# ใบงานการเชื่อมต่อ ESP32 กับ WiFi ในโหมด Station (STA)
ในใบงานนี้ เราจะเรียนรู้การตั้งค่า ESP32 ในโหมด Station (STA) โดยใช้ ESP-IDF 
นักศึกษาจะได้ทำความรู้จักกับ API ที่จำเป็นสำหรับการเชื่อมต่อ W-Fi รายละเอียดเกี่ยวกับไดรเวอร์ Wi-Fi 
และตัวอย่างสำหรับการเขียนโปรแกรม ESP-IDF เพื่อเชื่อมต่อกับเครือข่ายไร้สาย

## APIs สำหรับการเชื่อมต่อ  ESP32 เข้ากับ Wi-Fi  โดยใช้ ESP-IDF
ฟังก์ชันสำคัญในการเชื่อมต่อ ESP32 กับ Wi-Fi จะอยู่ในไลรารี่  esp_wifi (ต้อง include esp_wifi.h) สามารถใช้ในการตั้งค่าและตรวจสอบการทำงานของเครือข่าย Wi-Fi ESP32 รวมถึงการกำหนดค่าทั้งโหมด Access point และ Wi-Fi station ของ ESP32 ในโหมดความปลอดภัยต่างๆ เช่น WPA, WEP ฯลฯ การตรวจสอบแพ็กเก็ต Wi-Fi และการสแกนจุดเชื่อมต่อที่อยู่ในระยะใกล้เคียง 

ใบงานนี้ เราจะเน้นที่วิธีเชื่อมต่อบอร์ด ESP32 กับจุดเข้าใช้งานโดยการกำหนดค่าในโหมดสถานีซึ่งเรียกอีกอย่างว่าโหมด STA

ขั้นตอนที่จำเป็น

### 1.  include header file

```c
#include "esp_wifi.h"
```

### 2. การตั้งค่า (Configuration)

เราต้องจัดารรพรัพยากรที่จำเป็นให้แก่ Wi-Fi driver โดยการส่งผ่านทาง โครงสร้างข้อมูล wifi_init_config_t โดยฟังก์ชัน

```c
esp_wifi_init(const wifi_init_config_t *config);

```
ถ้าต้องการความรวดเร็ว เราอาจจะกำหนดค่าเริ่มต้นให้แก่ wifi_init_config_t ตามค่าเริ่มต้นที่ framework เตรียมไว้ให้ ซึ่งสามารถทำได้โดยฟังก์ชันนี้

```c
wifi_init_config_t wifi_config = WIFI_INIT_CONFIG_DEFAULT();

```

###3. กำหนดโหมดการทำงาน

ESP-IDF Wi-Fi library อนุญาตให้เราใช้งาน Wi-Fi บน ESP32 ได้ในหลายโหมดด้วยกัน
โดยเราสามารถกำหนดโหมดได้ด้วยฟังก์ชัน `esp_wifi_set_mode()` โดยโครงสร้างข้อมูลสำหรับโหมดเป็น parameterของฟังก์ชัน

เราสามารถกำหนดโหมดของ ESP32 ได้ทั้งหมด 3 โหมด ได้แก่

a. WIFI_MODE_STA (for station mode)
b. WIFI_MODE_AP (for soft-AP mode)
c. WIFI_MODE_APSTA (for station + soft-AP mode)

รูปแบบคำสั่งการเลือกโหมด

```c
esp_wifi_set_mode(wifi_mode_t mode);
```

### 4. เริ่มต้น Wi-Fi


การเริ่มต้นการเชื่อมต่อ Wi-Fi ตามที่ตั้ง config และ mode ไว้แล้วนั้น เราสามารถเรียกใช้ตำสั่ง
 `esp_wifi_start()` ได้ทันที โดยมีรูปแบบของคำสั่งคือ 

```c
esp_wifi_start(void)

```

### 5. เชื่อมต่อ ESP32 เข้ากับ access point

หลังจากที่ Wi-Fi เริ่มทำงานแล้ว เราสามารถที่จะเชื่อมต่อเข้ากับ  access point โดยใช้คำสั่งต่อไปนี้

```c
esp_wifi_connect()

```

## [>> เฟสการทำงานของ ESP32 Wi-Fi >>](./Phase-of-WiFi-Connection.md)

