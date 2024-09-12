# รายละเอียดการทำงานของ ESP32 Wi-Fi Station Connection

ขณะที่ ESP32 เชื่อมต่อ Wi-Fi จะมีการทำงานเป็นเฟสย่อยๆ ทั้งหมด 4 เฟสด้วยกัน ได้แก่

1. Scan Phase
2. Auth Phase
3. Association Phase
4. Four-way Handshake Phase


โดยมีรายละเอียดคร่าวๆ ดังนี้

## 1. Scan Phase

s1.1: ใน state นี้  Wi-Fi driver จะเริ่มทำงาน และสแกนหา  Access point ที่เรา config ไว้ เป็นผลจากการเรียก `esp_wifi_connect()` 

s1.2: ถ้าสแกนไม่เจอ Access point จะเกิด Wi-Fi event ที่ชื่อ  `WIFI_EVENT_STA_DISCONNECTED`  Wi-Fi driver จะส่ง result code ออกมาเป็น `WIFI_EVENT_STA_DISCONNECTED`

## 2. Auth Phase

s2.1: เริ่มต้นขั้นตอนการตรวจสอบสิทธิ์ โดยกระบวนการจับเวลาก็จะเริ่มขึ้นด้วยเพื่อตรวจสอบเวลาที่ใช้ในการร้องขอ ถ้านานกว่าค่า time out ก็แสดงว่าร้องขอไม่สำเร็จ

s2.2: ถ้าเลยเวลาที่กำหนดแล้ว แต่ยังไม่มีการตอบรับการร้องขอ ก็จะเกิด Wi-Fi event ที่ชื่อ  `WIFI_EVENT_STA_DISCONNECTED` Wi-Fi driver จะส่ง result code ออกมาเป็น  `WIFI_REASON_AUTH_EXPIRE`

s2.3: ถ้ามีการตอบรับจาก Access point จะทำให้ Timer หยุดลงและสิ้นสุดกระบวนการ authen

s2.4: ถ้า Access point ไม่ยอมรับ auth response packet  จะทำให้เกิด Wi-Fi event ที่ชื่อ  `WIFI_EVENT_STA_DISCONNECTED` และ  Wi-Fi driver จะส่ง result code ออกมาเป็น `WIFI_REASON_AUTH_FAIL`

## 3. Association Phase

s3.1: ในขั้นนี้จะเริ่มต้นการร้องขอการเชื่อมต่อ (association request)  และ association timer จะเริ่มทำงาน

s3.2: ถ้าเลยกำหนดเวลาของ association timer แล้ว จะเกิด Wi-Fi event ที่ชื่อ `WIFI_EVENT_STA_DISCONNECTED`  Wi-Fi driver จะส่ง result code ออกมาเป็น `WIFI_REASON_ASSOC_EXPIRE`

s3.3: ในขั้นนี้ association timer จะหยุดทำงาน เมื่อได้รับ association response packet จาก Access point

s3.4: เป็นกรณีที่ Access point ปฏิเสธ association response packet  ทำให้เกิด Wi-Fi event ที่ชื่อ  `WIFI_EVENT_STA_DISCONNECTED`   Wi-Fi driver จะส่ง result code ออกมาเป็น `WIFI_REASON_AUTH_FAIL`.


## 4. Four-way Handshake Phase

s4.1: เมื่อเริ่มกระบวนการ handshake และ handshake timer เกิด time-out และไม่ได้รับ  1/4 EAPOL (EAPoL Protocol = Extensible Authentication Protocol over LAN) จะทำให้เกิด  Wi-Fi event ที่ชื่อ  `WIFI_EVENT_STA_DISCONNECTED` Wi-Fi driver จะส่ง result code ออกมาเป็น `WIFI_REASON_HANDSHAKE_TIMEOUT`

s4.2: ในจังหวะนี้จะได้รับ  1/4 EAPOL

s4.3: station ตอบกลับ 2/4 EAPOL

s4.4: ในจังหวะนี้ ถ้าไม่ได้รับ 3/4 EAPOL จะเกิด Wi-Fi event ` WIFI_EVENT_STA_DISCONNECTED`   Wi-Fi driver จะส่ง result code ออกมาเป็น `WIFI_REASON_HANDSHAKE_TIMEOUT`

s4.5: ในจังหวะนี้ได้รับ  3/4 EAPOL

s4.6: ในจังหวะนี้  station จะส่ง 4/4 EAPOL กลับมาให้

s4.7: เกิด Wi-Fi event  `WIFI_EVENT_STA_CONNECTED`

หลังจาก s4.7 จะสามารถใช้งาน Wi-Fi station ได้

## [>> ใบงานการทดลอง >> ](./Lab_Sheet_ESP32_ESP-IDF_WiFi-STA.md)