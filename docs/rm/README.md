<!-- # 欢迎 -->

<!-- > [!WARNING]
> The source language of the document is Chinese, and the entire site adopts Google Translate, which will be automatically translated according to the system language. You can also switch the language manually through the menu in the upper right corner.

> [!TIP]
> If you have any questions, please give me feedback in time

* 文档内容基于以下环境
* 固件：RRF
* 硬件：FLY系列主板

* Klipper相关文档请移至 [Mellow Klipper docs](https://mellow.klipper.cn) -->
  1. 通常RRF固件只需要：主板+wifi模块即可使用，无需额外的上位机
  2. RRF固件主要使用wifi将打印文件写入到主板的sd卡中，所以使用RRF固件时sd卡必须保持插在主板上
## 1. 主板固件介绍
 **RRF固件主要分为单机模式/上位机模式**
  1. **单机模式:**   这种模式是我们最常用的使用模式。通常使用esp-wifi模块进行控制。我们需要下载类似 firmware-stm32f4-**wifi**-3.5.0-rc.1+102.bin 带有**WIFI**字符名字的固件
  2. **上位机模式:** 需要配合树莓派/Fly-pi,使用SPI接口和主板连接进行通信。我们需要下载类似 firmware-stm32f4-**SBC**-3.5.0-rc.1+102.bin 带有**SBC**字符名字的固件

## 2. 主板SD卡目录
  1. **firmware**文件夹：主要储存**esp-wifi模块固件**
  2. **gcodes**文件夹：储存**打印文件**目录
  3. **macros**文件夹：储存**宏命令**(就是一个文件存很多行命令，你只执行这一个命令，文件里的所有命令都会执行)
  4. **menu**文件夹：主要**12864**等屏幕**操作界面**
  5. **sys**文件夹：主要储存**机器配置**
  6. **www**文件夹：主要储存**网络控制界面**