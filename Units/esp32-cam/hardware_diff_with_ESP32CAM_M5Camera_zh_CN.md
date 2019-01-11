# ESP32CAM 与 M5Camera 的硬件对比

**[English](https://github.com/m5stack/M5-Schematic/blob/master/Units/m5camera/hardware_diff_with_ESP32CAM_M5Camera.md)**

*注意：ESP32CAM过一段时间之后会下架。*

*M5Camera的固件地址：https://github.com/m5stack/m5stack-cam-psram*

## 管脚对比

**摄像头驱动芯片 OV2640 接口**

| *接口*             | *OV2640 引脚*| *Alternate ESP32 Pin Mapping* | *ESP32Cam*    | *M5Camera(A 版本)*  | *M5Camera(B 版本)*  |
| :-------------------  | :--------:| :-------------------------: | :--------:  | :------:  | :------:  |
| SCCB Clock            | SIOC      | IO23                        | IO23        |IO23       |IO23       |
| SCCB Data             | SIOD      | IO25                        | IO25        |**IO25**       |**IO22**       |
| System Clock          | XCLK      | IO27                        | IO27        |IO27       |IO27       |
| Vertical Sync         | VSYNC     | IO22                        | IO22        |**IO22**       |**IO25**       |
| Horizontal Reference  | HREF      | IO26                        | IO26        |IO26       |IO26       |
| Pixel Clock           | PCLK      | IO21                        | IO21        |IO21       |IO21       |
| Pixel Data Bit 0      | D2        | IO35                        | IO17        |IO32       |IO32       |
| Pixel Data Bit 1      | D3        | IO17                        | IO35        |IO35       |IO35       |
| Pixel Data Bit 2      | D4        | IO34                        | IO34        |IO34       |IO34       |
| Pixel Data Bit 3      | D5        | IO5                         | IO5         |IO5        |IO5        |
| Pixel Data Bit 4      | D6        | IO39                        | IO39        |IO39       |IO39       |
| Pixel Data Bit 5      | D7        | IO18                        | IO18        |IO18       |IO18       |
| Pixel Data Bit 6      | D8        | IO36                        | IO36        |IO36       |IO36       |
| Pixel Data Bit 7      | D9        | IO19                        | IO19        |IO19       |IO19       |
| Camera Reset          | RESET     | IO15                        | IO15        |IO15       |IO15       |
| Camera Power Down     | PWDN      | *see Note 1*                | *see Note 1* | *see Note 1* | *see Note 1* |
| Power Supply 3.3V     | 3V3       | 3V3                         | 3V3         | 3V3       | 3V3       |
| Ground                | GND       | GND                         | GND         | GND       | GND       |

**GROVE 接口**

| *Grove*         | *ESP32Cam*    | *M5Camera(A 版本)*  | *M5Camera(B 版本)*  |
| :-----------: | :--------:  | :------:  | :------:  |
| SCL           | IO13        | IO13      | IO13      |
| SDA           | IO4        | **IO12**      | **IO4**      |
| 5V            | 5V          | 5V        | 5V        |
| GND           | GND         | GND       | GND       |

**BME280 接口**

`Note: the pinmap of BME280 on the old version of M5Camera is SCL -> GPIO23, SDA -> GPIO22, and it's iic address is 0x76. Thanks the issues of [sige1](https://github.com/sige1)(issues#1)`

| *BME280*         | *ESP32Cam*    | *M5Camera(A 版本)*  | *M5Camera(B 版本)*  |
| :-----------: | :--------:  | :------:  | :------:  |
| SCL           | IO4         | IO23      | IO23      |
| SDA           | IO13        | IO22      | IO22      |


**MPU6050 接口**

| *MPU6050*         | *ESP32Cam*    | *M5Camera(A 版本)*  | *M5Camera(B 版本)*  |
| :-----------: | :--------:  | :------:  | :------:  |
| SCL           | IO4         | IO23      | IO23      |
| SDA           | IO13        | IO22      | IO22      |

**MIC(SPM1423) 接口**

| *MPU6050*     | *ESP32Cam*        | *M5Camera(A 版本)*  | *M5Camera(B 版本)*  |
| :-----------: | :------:  | :------:  | :------:  |
| SCL           | *see Note 2*      |IO2|IO2|
| SDA           | *see Note 2*      |IO4|IO4|

**MIC(SPQ2410) 接口**

| *MPU6050*            | *ESP32Cam*  | *M5Camera(A 版本)*  | *M5Camera(B 版本)*  |
| :-----------: | :------:  |:------:  | :------:  |
| SCL           | IO32      |*see Note 2*|*see Note 2*|

**LED 接口**

| *LED*         | *ESP32Cam*    | *M5Camera(A 版本)*  | *M5Camera(B 版本)*  |
| :-----------: | :--------:  | :------:  | :------:  |
| LED_Pin           | IO16        | IO14      | IO14      |

Notes:

1. **Camera Power Down 引脚** 没必要连接到 ESP32 的引脚。

2. **麦克风引脚** ESP32Cam 上的麦克风 IC 是 SPQ2410，连接到 GPIO32 引脚。M5Camera 上的麦克风 IC 是 SPM1423，连接到 GPIO2 和 GPIO4 引脚。

![Image text](https://github.com/m5stack/M5-Schematic/blob/master/Units/m5camera/m5camera_03.jpg)
