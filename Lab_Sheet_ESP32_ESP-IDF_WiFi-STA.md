# ใบงานการทดลอง ESP32_ESP-IDF_WiFi-STA

## ขั้นตอนการทดลอง


1. สร้าง Espressif IDF project ใหม่ ชื่อ  ESP32_ESP-IDF_WiFi-STA 

2. แก้ไขไฟล์ main.c ให้เป็นดังนี้ โดยเชียนแต่ละส่วนให้ต่อเนื่องในไฟล์เดียวกัน

## ไฟล์ main.c

###  ส่วน  include
```c
/* WiFi station Example

   This example code is in the Public Domain (or CC0 licensed, at your option.)

   Unless required by applicable law or agreed to in writing, this
   software is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
   CONDITIONS OF ANY KIND, either express or implied.
*/
#include <string.h>
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "freertos/event_groups.h"
#include "esp_system.h"
#include "esp_wifi.h"
#include "esp_event.h"
#include "esp_log.h"
#include "nvs_flash.h"

#include "lwip/err.h"
#include "lwip/sys.h"
```

###  ส่วน การกำหนดตัวแปรและค่าคงที่

```c
/* The examples use WiFi configuration that you can set via project configuration menu

   If you'd rather not, just change the below entries to strings with
   the config you want - ie #define EXAMPLE_WIFI_SSID "mywifissid"
*/

#define EXAMPLE_ESP_WIFI_SSID      "_____Wifi_SSID___"
#define EXAMPLE_ESP_WIFI_PASS      "___Wifi_password_"
#define EXAMPLE_ESP_MAXIMUM_RETRY  5

/* FreeRTOS event group to signal when we are connected*/
static EventGroupHandle_t s_wifi_event_group;

/* The event group allows multiple bits for each event, but we only care about two events:
 * - we are connected to the AP with an IP
 * - we failed to connect after the maximum amount of retries */
#define WIFI_CONNECTED_BIT BIT0
#define WIFI_FAIL_BIT      BIT1

static const char *TAG = "wifi station";

```
### event_handler 

```c

static int s_retry_num = 0;

static void event_handler(void* arg, esp_event_base_t event_base,
                                int32_t event_id, void* event_data)
{
    if (event_base == WIFI_EVENT && event_id == WIFI_EVENT_STA_START) {
        esp_wifi_connect();
    } else if (event_base == WIFI_EVENT && event_id == WIFI_EVENT_STA_DISCONNECTED) {
        if (s_retry_num < EXAMPLE_ESP_MAXIMUM_RETRY) {
            esp_wifi_connect();
            s_retry_num++;
            ESP_LOGI(TAG, "retry to connect to the AP");
        } else {
            xEventGroupSetBits(s_wifi_event_group, WIFI_FAIL_BIT);
        }
        ESP_LOGI(TAG,"connect to the AP fail");
    } else if (event_base == IP_EVENT && event_id == IP_EVENT_STA_GOT_IP) {
        ip_event_got_ip_t* event = (ip_event_got_ip_t*) event_data;
        ESP_LOGI(TAG, "got ip:" IPSTR, IP2STR(&event->ip_info.ip));
        s_retry_num = 0;
        xEventGroupSetBits(s_wifi_event_group, WIFI_CONNECTED_BIT);
    }
}
```
### การตั้งค่าให้ wifi ทำงานในโหมด STA

```c
void wifi_init_sta(void)
{
    s_wifi_event_group = xEventGroupCreate();

    ESP_ERROR_CHECK(esp_netif_init());

    ESP_ERROR_CHECK(esp_event_loop_create_default());
    esp_netif_create_default_wifi_sta();

    wifi_init_config_t cfg = WIFI_INIT_CONFIG_DEFAULT();
    ESP_ERROR_CHECK(esp_wifi_init(&cfg));

    esp_event_handler_instance_t instance_any_id;
    esp_event_handler_instance_t instance_got_ip;
    ESP_ERROR_CHECK(esp_event_handler_instance_register(WIFI_EVENT,
                                                        ESP_EVENT_ANY_ID,
                                                        &event_handler,
                                                        NULL,
                                                        &instance_any_id));
    ESP_ERROR_CHECK(esp_event_handler_instance_register(IP_EVENT,
                                                        IP_EVENT_STA_GOT_IP,
                                                        &event_handler,
                                                        NULL,
                                                        &instance_got_ip));

    wifi_config_t wifi_config = {
        .sta = {
            .ssid = EXAMPLE_ESP_WIFI_SSID,
            .password = EXAMPLE_ESP_WIFI_PASS,
            /* Setting a password implies station will connect to all security modes including WEP/WPA.
             * However these modes are deprecated and not advisable to be used. Incase your Access point
             * doesn't support WPA2, these mode can be enabled by commenting below line */
	     .threshold.authmode = WIFI_AUTH_WPA2_PSK,
        },
    };
    ESP_ERROR_CHECK(esp_wifi_set_mode(WIFI_MODE_STA) );
    ESP_ERROR_CHECK(esp_wifi_set_config(WIFI_IF_STA, &wifi_config) );
    ESP_ERROR_CHECK(esp_wifi_start() );

    ESP_LOGI(TAG, "wifi_init_sta finished.");

    /* Waiting until either the connection is established (WIFI_CONNECTED_BIT) or connection failed for the maximum
     * number of re-tries (WIFI_FAIL_BIT). The bits are set by event_handler() (see above) */
    EventBits_t bits = xEventGroupWaitBits(s_wifi_event_group,
            WIFI_CONNECTED_BIT | WIFI_FAIL_BIT,
            pdFALSE,
            pdFALSE,
            portMAX_DELAY);

    /* xEventGroupWaitBits() returns the bits before the call returned, hence we can test which event actually
     * happened. */
    if (bits & WIFI_CONNECTED_BIT) {
        ESP_LOGI(TAG, "connected to ap SSID:%s password:%s",
                 EXAMPLE_ESP_WIFI_SSID, EXAMPLE_ESP_WIFI_PASS);
    } else if (bits & WIFI_FAIL_BIT) {
        ESP_LOGI(TAG, "Failed to connect to SSID:%s, password:%s",
                 EXAMPLE_ESP_WIFI_SSID, EXAMPLE_ESP_WIFI_PASS);
    } else {
        ESP_LOGE(TAG, "UNEXPECTED EVENT");
    }

    /* The event will not be processed after unregister */
    ESP_ERROR_CHECK(esp_event_handler_instance_unregister(IP_EVENT, IP_EVENT_STA_GOT_IP, instance_got_ip));
    ESP_ERROR_CHECK(esp_event_handler_instance_unregister(WIFI_EVENT, ESP_EVENT_ANY_ID, instance_any_id));
    vEventGroupDelete(s_wifi_event_group);
}
```
### app_main()

```c
void app_main(void)
{
    //Initialize NVS
    esp_err_t ret = nvs_flash_init();
    if (ret == ESP_ERR_NVS_NO_FREE_PAGES || ret == ESP_ERR_NVS_NEW_VERSION_FOUND) {
      ESP_ERROR_CHECK(nvs_flash_erase());
      ret = nvs_flash_init();
    }
    ESP_ERROR_CHECK(ret);

    ESP_LOGI(TAG, "ESP_WIFI_MODE_STA");
    wifi_init_sta();
}

```


3. แก้ไขบรรทัดต่อไปนี้ ให้เป็น SSID และ Password ของ Access point ที่ใช้

```c
#define EXAMPLE_ESP_WIFI_SSID      "_____Wifi_SSID___"
#define EXAMPLE_ESP_WIFI_PASS      "___Wifi_password_"

```

## ผลลัพน์


### 1. ทำที่มหาลัยโดยใช้ เราต์เตอร์ WiFi Ais ในการเชื่อมต่อ

![462547300_388964734182196_2887552636389704187_n](https://github.com/user-attachments/assets/7d09b430-32a9-44cb-aa84-0be848727d54)


![462566792_2803548789818647_6028728299940093707_n](https://github.com/user-attachments/assets/f355168d-154e-4171-bd64-364eebe59e15)


![462543680_2614029942319758_5667074555521716548_n](https://github.com/user-attachments/assets/fedef5c6-7efa-4ead-a9df-dbe8163e8600)

![462548358_476783948062264_5537232092815006658_n](https://github.com/user-attachments/assets/55a393fb-2e51-4f1b-a1e4-948c2223820f)

![462565823_1080823326828678_5546521908062438162_n](https://github.com/user-attachments/assets/643ead5e-3104-4655-8898-8d6aed405a4e)


![462638996_3947606245511629_4750825591737058650_n](https://github.com/user-attachments/assets/cf17d7f8-0b49-469a-ae88-81324ae30211)

![462578660_532362389685323_7591263226418920899_n](https://github.com/user-attachments/assets/55ba6171-57e5-40f2-abb4-411528538659)

![462569814_424143610514982_4912579447844577156_n](https://github.com/user-attachments/assets/90070a5f-adcf-4fc8-94f0-c0450c074f07)

![462572836_819342610164048_3669393909528594181_n](https://github.com/user-attachments/assets/5e09eba8-c705-4122-a7c8-1ca7aaa7fa39)


โปรแกรมที่ทำงานบน VS code ที่นำขึ้นบน git hub

https://github.com/AnchisaPhetnoi/ESP32__ESP-IDF_WiFi-STA.git

![image](https://github.com/user-attachments/assets/373747eb-9a6d-4fb8-a631-0e76859cd327)



### 2. ทำการเชื่อมกับอินเตอร์เน็ตโทรศัพน์มือถือ

![image](https://github.com/user-attachments/assets/3e3a1380-d1b9-4c4d-8f38-a6b4daa0cde4)



![image](https://github.com/user-attachments/assets/49fa6a6f-509f-4516-83a3-11ec5f8ebe1f)



![image](https://github.com/user-attachments/assets/cdfe3a5f-e478-4e09-835e-699e7f4bc0b7)



จะเห็นว่ามีการเชื่อม ต่อกับ อินเตอร์เน็ต และมีการแสดง ที่อยู่ ชื่อ รหัสขึ้นมา 



โปรแกรมที่ทำงานบน VS code ที่นำขึ้นบน git hub

https://github.com/AnchisaPhetnoi/ESP32_ESP-IDF__WiFi-STA.git



