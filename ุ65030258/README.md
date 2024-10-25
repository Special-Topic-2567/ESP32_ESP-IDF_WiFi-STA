# ส่งงาน
## 65030258 สิทธา กล้าพานิช

https://github.com/SitthaKlaphanich/ESP32_ESP-IDF-WiFi-STA.git

### เชื่อมต่อไม่สำเร็จ
```
I (30) boot: ESP-IDF v5.3.1 2nd stage bootloader
I (30) boot: compile time Oct 25 2024 15:09:37
I (30) boot: Multicore bootloader
I (35) boot: chip revision: v1.0
I (38) boot.esp32: SPI Speed      : 40MHz
I (43) boot.esp32: SPI Mode       : DIO
I (47) boot.esp32: SPI Flash Size : 2MB
I (52) boot: Enabling RNG early entropy source...
I (57) boot: Partition Table:
I (61) boot: ## Label            Usage          Type ST Offset   Length
I (68) boot:  0 nvs              WiFi data        01 02 00009000 00006000
I (76) boot:  1 phy_init         RF data          01 01 0000f000 00001000
I (83) boot:  2 factory          factory app      00 00 00010000 00100000
I (91) boot: End of partition table
I (95) esp_image: segment 0: paddr=00010020 vaddr=3f400020 size=1e930h (125232) map
I (146) esp_image: segment 1: paddr=0002e958 vaddr=3ffb0000 size=016c0h (  5824) load
I (149) esp_image: segment 2: paddr=00030020 vaddr=400d0020 size=786c8h (493256) map
I (321) esp_image: segment 3: paddr=000a86f0 vaddr=3ffb16c0 size=02800h ( 10240) load
I (325) esp_image: segment 4: paddr=000aaef8 vaddr=40080000 size=172f4h ( 94964) load
I (376) boot: Loaded app from partition at offset 0x10000
I (376) boot: Disabling RNG early entropy source...
I (388) cpu_start: Multicore app
I (396) cpu_start: Pro cpu start user code
I (396) cpu_start: cpu freq: 160000000 Hz
I (396) app_init: Application information:
I (399) app_init: Project name:     ESP32_ESP-IDF_WiFi-STA
I (405) app_init: App version:      9706e70-dirty
I (411) app_init: Compile time:     Oct 25 2024 15:08:46
I (417) app_init: ELF file SHA256:  fb939ecfc...
I (422) app_init: ESP-IDF:          v5.3.1
I (427) efuse_init: Min chip rev:     v0.0
I (431) efuse_init: Max chip rev:     v3.99
I (436) efuse_init: Chip rev:         v1.0
I (441) heap_init: Initializing. RAM available for dynamic allocation:
I (449) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
I (454) heap_init: At 3FFB8090 len 00027F70 (159 KiB): DRAM
I (461) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
I (467) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I (474) heap_init: At 400972F4 len 00008D0C (35 KiB): IRAM
I (481) spi_flash: detected chip: generic
I (484) spi_flash: flash io: dio
W (488) spi_flash: Detected size(4096k) larger than the size in the binary image header(2048k). Using the size in the binary image header.
I (502) main_task: Started on CPU0
I (512) main_task: Calling app_main()
I (532) wifi station: ESP_WIFI_MODE_STA
I (542) wifi:wifi driver task: 3ffc0024, prio:23, stack:6656, core=0
I (552) wifi:wifi firmware version: ccaebfa
I (552) wifi:wifi certification version: v7.0
I (552) wifi:config NVS flash: enabled
I (552) wifi:config nano formating: disabled
I (552) wifi:Init data frame dynamic rx buffer num: 32
I (562) wifi:Init static rx mgmt buffer num: 5
I (562) wifi:Init management short buffer num: 32
I (572) wifi:Init dynamic tx buffer num: 32
I (572) wifi:Init static rx buffer size: 1600
I (582) wifi:Init static rx buffer num: 10
I (582) wifi:Init dynamic rx buffer num: 32
I (582) wifi_init: rx ba win: 6
I (592) wifi_init: accept mbox: 6
I (592) wifi_init: tcpip mbox: 32
I (602) wifi_init: udp mbox: 6
I (602) wifi_init: tcp mbox: 6
I (602) wifi_init: tcp tx win: 5760
I (612) wifi_init: tcp rx win: 5760
I (612) wifi_init: tcp mss: 1440
I (612) wifi_init: WiFi IRAM OP enabled
I (622) wifi_init: WiFi RX IRAM OP enabled
I (632) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
I (712) wifi:mode : sta (58:bf:25:8c:14:64)
I (712) wifi:enable tsf
I (712) wifi station: wifi_init_sta finished.
I (3132) wifi station: retry to connect to the AP
I (3132) wifi station: connect to the AP fail
I (5542) wifi station: retry to connect to the AP
I (5542) wifi station: connect to the AP fail
I (7962) wifi station: retry to connect to the AP
I (7962) wifi station: connect to the AP fail
I (10372) wifi station: retry to connect to the AP
I (10372) wifi station: connect to the AP fail
I (12782) wifi station: retry to connect to the AP
I (12782) wifi station: connect to the AP fail
I (15202) wifi station: connect to the AP fail
I (15202) wifi station: Failed to connect to SSID:AIS 4G Hi-Speed Home WiFi_769475, password:50769475
I (15202) main_task: Returned from app_main()
```

### เมื่อเชื่อมต่อ WiFi ที่กำหนด ไว้ไม่สำเร็จจะไม่โชว์ค่าสถานะการเชื่อมต่อต่างๆ ของเครือข่ายที่เชื่อมต่ออยู่ จะแสดง ชื่อ และ รหัสผ่าน ที่ไม่สามารถเชื่อมต่อได้

### เชื่อมต่อสำเร็จ
```
I (30) boot: ESP-IDF v5.3.1 2nd stage bootloader
I (30) boot: compile time Oct 25 2024 15:09:37
I (30) boot: Multicore bootloader
I (35) boot: chip revision: v1.0
I (38) boot.esp32: SPI Speed      : 40MHz
I (43) boot.esp32: SPI Mode       : DIO
I (48) boot.esp32: SPI Flash Size : 2MB
I (52) boot: Enabling RNG early entropy source...
I (57) boot: Partition Table:
I (61) boot: ## Label            Usage          Type ST Offset   Length
I (68) boot:  0 nvs              WiFi data        01 02 00009000 00006000
I (76) boot:  1 phy_init         RF data          01 01 0000f000 00001000
I (83) boot:  2 factory          factory app      00 00 00010000 00100000
I (91) boot: End of partition table
I (95) esp_image: segment 0: paddr=00010020 vaddr=3f400020 size=1e930h (125232) map
I (146) esp_image: segment 1: paddr=0002e958 vaddr=3ffb0000 size=016c0h (  5824) load
I (149) esp_image: segment 2: paddr=00030020 vaddr=400d0020 size=786dch (493276) map
I (321) esp_image: segment 3: paddr=000a8704 vaddr=3ffb16c0 size=02800h ( 10240) load
I (325) esp_image: segment 4: paddr=000aaf0c vaddr=40080000 size=172f4h ( 94964) load
I (376) boot: Loaded app from partition at offset 0x10000
I (376) boot: Disabling RNG early entropy source...
I (388) cpu_start: Multicore app
I (396) cpu_start: Pro cpu start user code
I (396) cpu_start: cpu freq: 160000000 Hz
I (396) app_init: Application information:
I (399) app_init: Project name:     ESP32_ESP-IDF_WiFi-STA
I (405) app_init: App version:      9706e70-dirty
I (411) app_init: Compile time:     Oct 25 2024 15:16:46
I (417) app_init: ELF file SHA256:  9713ca891...
I (422) app_init: ESP-IDF:          v5.3.1
I (427) efuse_init: Min chip rev:     v0.0
I (432) efuse_init: Max chip rev:     v3.99
I (436) efuse_init: Chip rev:         v1.0
I (442) heap_init: Initializing. RAM available for dynamic allocation:
I (449) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
I (455) heap_init: At 3FFB8090 len 00027F70 (159 KiB): DRAM
I (461) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
I (467) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I (474) heap_init: At 400972F4 len 00008D0C (35 KiB): IRAM
I (481) spi_flash: detected chip: generic
I (484) spi_flash: flash io: dio
W (488) spi_flash: Detected size(4096k) larger than the size in the binary image header(2048k). Using the size in the binary image header.
I (502) main_task: Started on CPU0
I (512) main_task: Calling app_main()
I (532) wifi station: ESP_WIFI_MODE_STA
I (542) wifi:wifi driver task: 3ffc0024, prio:23, stack:6656, core=0
I (552) wifi:wifi firmware version: ccaebfa
I (552) wifi:wifi certification version: v7.0
I (552) wifi:config NVS flash: enabled
I (552) wifi:config nano formating: disabled
I (552) wifi:Init data frame dynamic rx buffer num: 32
I (562) wifi:Init static rx mgmt buffer num: 5
I (562) wifi:Init management short buffer num: 32
I (572) wifi:Init dynamic tx buffer num: 32
I (572) wifi:Init static rx buffer size: 1600
I (582) wifi:Init static rx buffer num: 10
I (582) wifi:Init dynamic rx buffer num: 32
I (582) wifi_init: rx ba win: 6
I (592) wifi_init: accept mbox: 6
I (592) wifi_init: tcpip mbox: 32
I (602) wifi_init: udp mbox: 6
I (602) wifi_init: tcp mbox: 6
I (602) wifi_init: tcp tx win: 5760
I (612) wifi_init: tcp rx win: 5760
I (612) wifi_init: tcp mss: 1440
I (612) wifi_init: WiFi IRAM OP enabled
I (622) wifi_init: WiFi RX IRAM OP enabled
I (632) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
I (712) wifi:mode : sta (58:bf:25:8c:14:64)
I (712) wifi:enable tsf
I (712) wifi station: wifi_init_sta finished.
I (722) wifi:new:<5,0>, old:<1,0>, ap:<255,255>, sta:<5,0>, prof:1, snd_ch_cfg:0x0
I (722) wifi:state: init -> auth (0xb0)
I (732) wifi:state: auth -> assoc (0x0)
I (752) wifi:Association refused temporarily time 1000, comeback time 1100 (TUs)
I (1872) wifi:state: assoc -> assoc (0x0)
I (1882) wifi:state: assoc -> run (0x10)
I (1902) wifi:connected with Sittha, aid = 5, channel 5, BW20, bssid = 40:9b:cd:2d:b3:30
I (1902) wifi:security: WPA2-PSK, phy: bgn, rssi: -35
I (1902) wifi:pm start, type: 1

I (1902) wifi:dp: 1, bi: 102400, li: 3, scale listen interval from 307200 us to 307200 us
I (1972) wifi:AP's beacon interval = 102400 us, DTIM period = 1
I (2912) esp_netif_handlers: sta ip: 111.111.0.111, mask: 255.255.255.0, gw: 111.111.0.1
I (2912) wifi station: got ip:111.111.0.111
I (2912) wifi station: connected to ap SSID:Sittha password:12345678000
I (2922) main_task: Returned from app_main()
```
### เมื่อเชื่อมต่อ WiFi ที่กำหนด ไว้สำเร็จจะโชว์ค่าสถานะการเชื่อมต่อต่างๆ ของเครือข่ายที่เชื่อมต่ออยู่
