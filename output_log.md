```
load:0x40080404,len:3904
entry 0x40080640
I (31) boot: ESP-IDF v5.3.1 2nd stage bootloader
I (31) boot: compile time Nov  1 2024 17:48:52
I (31) boot: Multicore bootloader
I (35) boot: chip revision: v1.0
I (39) boot.esp32: SPI Speed      : 40MHz
I (44) boot.esp32: SPI Mode       : DIO
I (48) boot.esp32: SPI Flash Size : 2MB
I (53) boot: Enabling RNG early entropy source...
I (58) boot: Partition Table:
I (62) boot: ## Label            Usage          Type ST Offset   Length
I (69) boot:  0 nvs              WiFi data        01 02 00009000 00006000
I (76) boot:  1 phy_init         RF data          01 01 0000f000 00001000
I (84) boot:  2 factory          factory app      00 00 00010000 00100000
I (91) boot: End of partition table
I (96) esp_image: segment 0: paddr=00010020 vaddr=3f400020 size=1f534h (128308) map
I (148) esp_image: segment 1: paddr=0002f55c vaddr=3ffb0000 size=00abch (  2748) load
I (149) esp_image: segment 2: paddr=00030020 vaddr=400d0020 size=82e68h (536168) map
I (337) esp_image: segment 3: paddr=000b2e90 vaddr=3ffb0abc size=03414h ( 13332) load
I (343) esp_image: segment 4: paddr=000b62ac vaddr=40080000 size=1734ch ( 95052) load
I (392) boot: Loaded app from partition at offset 0x10000
I (392) boot: Disabling RNG early entropy source...
I (404) cpu_start: Multicore app
I (412) cpu_start: Pro cpu start user code
I (413) cpu_start: cpu freq: 160000000 Hz
I (413) app_init: Application information:
I (415) app_init: Project name:     ESP32_ESP-IDF_WiFi-STA
I (422) app_init: App version:      1
I (426) app_init: Compile time:     Nov  1 2024 17:46:45
I (432) app_init: ELF file SHA256:  6a4f56dae...
I (437) app_init: ESP-IDF:          v5.3.1
I (442) efuse_init: Min chip rev:     v0.0
I (447) efuse_init: Max chip rev:     v3.99
I (452) efuse_init: Chip rev:         v1.0
I (457) heap_init: Initializing. RAM available for dynamic allocation:
I (464) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
I (470) heap_init: At 3FFB8100 len 00027F00 (159 KiB): DRAM
I (476) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
I (482) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I (489) heap_init: At 4009734C len 00008CB4 (35 KiB): IRAM
I (497) spi_flash: detected chip: generic
I (500) spi_flash: flash io: dio
W (504) spi_flash: Detected size(4096k) larger than the size in the binary image header(2048k). Using the size in the binary image header.
I (518) main_task: Started on CPU0
I (528) main_task: Calling app_main()
I (558) wifi station: ESP_WIFI_MODE_STA
I (568) wifi:wifi driver task: 3ffc0158, prio:23, stack:6656, core=0
I (578) wifi:wifi firmware version: ccaebfa
I (578) wifi:wifi certification version: v7.0
I (578) wifi:config NVS flash: enabled
I (578) wifi:config nano formating: disabled
I (588) wifi:Init data frame dynamic rx buffer num: 32
I (588) wifi:Init static rx mgmt buffer num: 5
I (598) wifi:Init management short buffer num: 32
I (598) wifi:Init dynamic tx buffer num: 32
I (608) wifi:Init static rx buffer size: 1600
I (608) wifi:Init static rx buffer num: 10
I (608) wifi:Init dynamic rx buffer num: 32
I (618) wifi_init: rx ba win: 6
I (618) wifi_init: accept mbox: 6
I (618) wifi_init: tcpip mbox: 32
I (628) wifi_init: udp mbox: 6
I (628) wifi_init: tcp mbox: 6
I (638) wifi_init: tcp tx win: 5760
I (638) wifi_init: tcp rx win: 5760
I (638) wifi_init: tcp mss: 1440
I (648) wifi_init: WiFi IRAM OP enabled
I (648) wifi_init: WiFi RX IRAM OP enabled
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (598) wifi:Init management short buffer num: 32
I (598) wifi:Init dynamic tx buffer num: 32
I (608) wifi:Init static rx buffer size: 1600
I (608) wifi:Init static rx buffer num: 10
I (608) wifi:Init dynamic rx buffer num: 32
I (618) wifi_init: rx ba win: 6
I (618) wifi_init: accept mbox: 6
I (618) wifi_init: tcpip mbox: 32
I (628) wifi_init: udp mbox: 6
I (628) wifi_init: tcp mbox: 6
I (638) wifi_init: tcp tx win: 5760
I (638) wifi_init: tcp rx win: 5760
I (638) wifi_init: tcp mss: 1440
I (648) wifi_init: WiFi IRAM OP enabled
I (648) wifi_init: WiFi RX IRAM OP enabled
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (868) wifi:enable tsf
I (598) wifi:Init dynamic tx buffer num: 32
I (608) wifi:Init static rx buffer size: 1600
I (608) wifi:Init static rx buffer num: 10
I (608) wifi:Init dynamic rx buffer num: 32
I (618) wifi_init: rx ba win: 6
I (618) wifi_init: accept mbox: 6
I (618) wifi_init: tcpip mbox: 32
I (628) wifi_init: udp mbox: 6
I (628) wifi_init: tcp mbox: 6
I (638) wifi_init: tcp tx win: 5760
I (638) wifi_init: tcp rx win: 5760
I (638) wifi_init: tcp mss: 1440
I (648) wifi_init: WiFi IRAM OP enabled
I (648) wifi_init: WiFi RX IRAM OP enabled
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (608) wifi:Init static rx buffer num: 10
I (608) wifi:Init dynamic rx buffer num: 32
I (618) wifi_init: rx ba win: 6
I (618) wifi_init: accept mbox: 6
I (618) wifi_init: tcpip mbox: 32
I (628) wifi_init: udp mbox: 6
I (628) wifi_init: tcp mbox: 6
I (638) wifi_init: tcp tx win: 5760
I (638) wifi_init: tcp rx win: 5760
I (638) wifi_init: tcp mss: 1440
I (648) wifi_init: WiFi IRAM OP enabled
I (648) wifi_init: WiFi RX IRAM OP enabled
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (618) wifi_init: tcpip mbox: 32
I (628) wifi_init: udp mbox: 6
I (628) wifi_init: tcp mbox: 6
I (638) wifi_init: tcp tx win: 5760
I (638) wifi_init: tcp rx win: 5760
I (638) wifi_init: tcp mss: 1440
I (648) wifi_init: WiFi IRAM OP enabled
I (648) wifi_init: WiFi RX IRAM OP enabled
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (638) wifi_init: tcp rx win: 5760
I (638) wifi_init: tcp mss: 1440
I (648) wifi_init: WiFi IRAM OP enabled
I (648) wifi_init: WiFi RX IRAM OP enabled
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (648) wifi_init: WiFi IRAM OP enabled
I (648) wifi_init: WiFi RX IRAM OP enabled
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (868) wifi:enable tsf
I (878) wifi station: wifi_init_sta finished.
I (768) phy_init: phy_version 4830,54550f7,Jun 20 2024,14:22:08
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (868) wifi:enable tsf
I (878) wifi station: wifi_init_sta finished.
I (3288) wifi station: retry to connect to the AP
W (838) phy_init: saving new calibration data because of checksum failure, mode(0)
I (868) wifi:mode : sta (58:bf:25:8c:13:d4)
I (868) wifi:enable tsf
I (878) wifi station: wifi_init_sta finished.
I (3288) wifi station: retry to connect to the AP
I (3288) wifi station: connect to the AP fail
I (868) wifi:enable tsf
I (878) wifi station: wifi_init_sta finished.
I (3288) wifi station: retry to connect to the AP
I (3288) wifi station: connect to the AP fail
I (3288) wifi station: retry to connect to the AP
I (3288) wifi station: connect to the AP fail
I (5708) wifi station: retry to connect to the AP
I (5708) wifi station: connect to the AP fail
I (8118) wifi station: retry to connect to the AP
I (3288) wifi station: connect to the AP fail
I (5708) wifi station: retry to connect to the AP
I (5708) wifi station: connect to the AP fail
I (8118) wifi station: retry to connect to the AP
I (5708) wifi station: retry to connect to the AP
I (5708) wifi station: connect to the AP fail
I (8118) wifi station: retry to connect to the AP
I (8118) wifi station: connect to the AP fail
I (10528) wifi station: retry to connect to the AP
I (8118) wifi station: retry to connect to the AP
I (8118) wifi station: connect to the AP fail
I (10528) wifi station: retry to connect to the AP
I (10538) wifi station: connect to the AP fail
I (8118) wifi station: connect to the AP fail
I (10528) wifi station: retry to connect to the AP
I (10538) wifi station: connect to the AP fail
I (10528) wifi station: retry to connect to the AP
I (10538) wifi station: connect to the AP fail
I (10538) wifi station: connect to the AP fail
I (12948) wifi station: retry to connect to the AP
I (12948) wifi station: connect to the AP fail
I (15358) wifi station: connect to the AP fail
I (15358) wifi station: Failed to connect to SSID:anc, password:123456789
I (15358) wifi station: connect to the AP fail
I (15358) wifi station: Failed to connect to SSID:anc, password:123456789
I (15358) wifi station: Failed to connect to SSID:anc, password:123456789
I (15358) main_task: Returned from app_main()
```

