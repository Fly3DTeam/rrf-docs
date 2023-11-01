## 1. 下载固件
 1. **[下载主板固件(点击跳转)](https://github.com/gloomyandy/RepRapFirmware/releases "点击跳转")**

   ![](../../images/rm/firmware.png ":size=100%")
    根据自己的wifi模块以及主板芯片型号下载对应的固件,如果不清楚型号咨询客服或者技术人员
 2. **[下载网页界面(点击跳转)](https://github.com/Duet3D/DuetWebControl/releases)**

    ![](../../images/rm/www.png ":size=100%")

## 2. 生成机器配置
 1. **[网页配置界面(点击跳转)](https://teamgloomy.github.io/Configurator)**
   ![](../../images/rm/web_config1.png ":size=100%")
   **右上角可以选择语言**
   然后点击**下一步**
### General 设置
 1. **选择主板型号**

   ![](../../images/rm/web_config2.png ":size=100%")
 
 2. **机器结构设置**

     **Cartesian: I3/UM/MB**
  
     **CoreXY : Vzbot/BLV/Voron**

   ![](../../images/rm/web_config3.png ":size=100%")

 3. **打印尺寸设置**

   ![](../../images/rm/web_config4.png ":size=100%")

 4. **归位速度设置**

   ![](../../images/rm/web_config5.png ":size=100%")

### I/O Mapping 设置
 
   
   1. **电机/限位设置**

      此设置主要设置那个轴使用哪个端口为限位

      只要Endstop Pin可以选择的端口，都可以作为限位使用
     ![](../../images/rm/web_config6.png ":size=50%") 

     以xstop为例解释

      **stop:** 限位信号接收到 **高** 电平信号 **触发** 

      **stop(active-low):** 限位信号接收到 **低** 电平信号 **触发**

      **stop(pull-up):** 限位信号内部**上拉**接收到**高**电平信号 **触发** 

      **stop(active-low，pull-up):** 限位信号内部 **上拉** 接收到 **低** 电平信 **触发**       

     ![](../../images/rm/web_config6.1.png ":size=50%") 
   2. **风扇设置**
      
      比如我们需要2个可控风扇，1个给喉管散热，1个给模型散热，点击+号按钮增加可控风扇数量。

      具体哪个风扇分配给喉管/模型，在TOOL界面配置

      ![](../../images/rm/web_config7.png ":size=50%")
   3. **加热端口设置**

      此设置我们主要设置加热端口数量，以及每个加热口对应的温度检测口
      
      **Index:** 序列号一般0为热床

      **Type:** 加热口类型:热床，喷嘴，腔温

      **Output:** 指定主板哪个加热端口为 热床，喷嘴，腔温开关控制器

   	**Sensor:** 指定对应主板加热端口的热敏传感器端口(比如热床热敏端口我们可以配置成喷嘴的，喷嘴配置成热床的，你只需要插到对应的端口即可)
      
      
      ![](../../images/rm/web_config8.png ":size=50%")

   4. **调平探针设置**

      如果机器没有调平，可以忽略这里设置

      **Input Pin:**调平信号输入端口(如果是bltouch，将probe插入此端口)

      **PWM Control Channel:** 这个是控制BLTOCH探针伸缩使用的仅bltouch传感器才需要配置

      ![](../../images/rm/web_config9.png ":size=50%")


### Motors 设置
 1. **X Y Z E设置**
   
   这里我们主要设置每个轴的电机方向，驱动类型，脉冲值，电机电流(电机电流设置仅TMC系列驱动有效)

   **Direction:** 电机转动方向

   **Driver:** 电机驱动类型TMC2209等等

   **Microstepping :** 细分

   **Steps per mm:** 脉冲，移动1mm发送多少脉冲，一般20齿同步轮设置80脉冲

   **Max. Speed Change (mm/s):** 每秒速度最大变化量

   **Max. Speed (mm/s):** 最大速度

   **Acceleration (mm/s²):** 最大加速度

   **Motor Current (mA):** 电机电流设置，仅TMC系列驱动支持，4988等驱动此选项无效

   ![](../../images/rm/web_config10.png ":size=100%")

 2. **空闲电流设置**
   
   当打印机电机停止转动多久以后，为了省电，又想保持电机锁住，启用此模式，减少电机电流。开启节能模式(仅TMC系列驱动支持)

   **Idle Current Percentage:** 节能模式下电流比例，比如X轴电流设置1A,Idle Current Percentage:30%，到了时间以后系统就会自动降低X轴电流到300ma。

   **Idle Timeout:** 超时时间

   ![](../../images/rm/web_config11.png ":size=100%")
### Endstop 设置
 1. **限位设置**
      	
      **Endstop Type:** 限位类型。光电/机械限位均为Switch。使用TMC的无限位模式需要额外的配置，参考单独的文档。如果要使用Z限位的z-probe需要配置I/O Mapping下Z-Probe下的Input Pin

      **Endstop Location at:** 设置归位点。此设置会影响你打印出来模型镜像等问题，请仔细确认。

      配置方法如下

      **正面面对你的机器** 看一下机器喷头归位位置，参考下图四个角的位置进行配置

   ![](../../images/rm/web_config12.1.png ":size=60%")

   ![](../../images/rm/web_config12.png ":size=100%")

 2. **Z调平传感器设置**

   如果机器没有调平模块，忽略此设置

   **Probe X/Y Offset:** 设置XY偏移

   **Probe Type:** 传感器类型。**switch:** 接近开关，PL08,klicky,TAP等等
    **Blouch:** bltouch,3dtouch
   ![](../../images/rm/web_config13.png ":size=100%")

###  Heaters 设置
 1. **加热方式设置**
   **一般默认无需修改**
   ![](../../images/rm/web_config14.png ":size=100%")

 2. **温度/最大功率/热敏类型设置**
   
   **Temp. Limit** 最大安全温度，加热器超过此温度将会报警，并关闭加热

   **PWM Limit** 最大功率设置，如果你的热床或者加热棒功率太大，可以设置为50，降低一半功率

   ![](../../images/rm/web_config15.png ":size=100%")
 3. **热敏类型设置**
 
 普通NTC100K我们保持默认无需修改
 
 如果需要修改请按图片操作

 ![](../../images/rm/web_config15.1.png ":size=100%")

### Fan 设置
   
   风扇设置我们通常只需要设置以下参数

   **speed** 开机后转速 0为不转 100为满速运行。

   **Thermostatic Control** 受温度控制，比如喉管风扇，喷嘴达到45度时风扇自动开启

   **Monitored Heaters** 绑定受温度控制风扇的传感器。根据I/O Mapping下Heaters下的Index。一般H0为风扇，H1为喷嘴。意思是温度风扇是根据热床温度自动开启还是根据喷嘴温度自动开启。

   ![](../../images/rm/web_config16.png ":size=100%")

### TOOL 设置

   **Select the First Tool on Start-Up** 一般都要勾选。防止网页设置喷嘴温度不起作用

![](../../images/rm/web_config17.png ":size=100%")

如果我们有多个喷嘴可以点击+进行增加
![](../../images/rm/web_config18.png ":size=100%")

### Compensation 设置

   此界面设置调平范围，由于大多数xy偏移不为0所以可能测不了全部平台范围，进行设置避免测到平台以外的位置

   ![](../../images/rm/web_config19.png ":size=100%")

### Display 设置

**12864 Display** 需要手动配置，具体配置参考单独的文档

如果你有串口屏可以启用下面配置

![](../../images/rm/web_config20.png ":size=100%")

### Network 设置

如果你只有 **Network Settings - ESP32** 一个选项，保持默认不需要修改

如果你的这个界面同时包含 **Network Settings - ESP8266** 。根据自己的wifi模块进行启用。

![](../../images/rm/web_config21.png ":size=100%")

### Finish 设置

 1. **Extra Files**
   由于部分地区网络问题，一般我们取消勾选，不获取最新固件地址

   ![](../../images/rm/web_config22.png ":size=100%")

 2. **点击Finish**

   ![](../../images/rm/web_config23.png ":size=100%")

 3. **下载配置文件**

   ![](../../images/rm/web_config24.png ":size=100%")

## 3. 解压/重命名文件

根据以上操作我们一共下载了4份文件：
(由于wifi模块/主板型号的不同，可能个别文件名字有差异)
![](../../images/rm/file_open.png ":size=100%")

 1. **解压缩文件**

  将**DuetWebControl-SD.zip** **config.zip** 解压缩

 2. **重命名文件**

   **DuetWiFiServer_32.bin** -> **DuetWiFiServer.bin**

   **firmware-stm32xxx-wifi-xxx.bin** -> **firmware.bin**

   **DuetWebControl-SD**文件夹重命名 -> **www**


## 4. 将固件放入SD卡
 1. 先在sd卡根目录下创建**firmware** **menu** **gcodes** **macros**文件夹

 ![](../../images/rm/sd_file1.png ":size=60%")

 2. 将DuetWiFiServer.bin放入到SD卡的firmware文件夹下

 ![](../../images/rm/sd_file2.png ":size=50%")

 3. 将**config.zip** 解压缩出来的config文件夹内的**sys**文件夹复制到sd卡根目录

 将www文件夹复制到sd卡根目录

 将firmware.bin复制到sd卡根目录

 完整SD卡内容如下图所示：

  ![](../../images/rm/sd_file3.png ":size=100%")




## 5.配置wifi

 1. **[下载串口调试助手(点击跳转)]( https://drive.google.com/file/d/1P6rPPH3vVmkVSEnUujaWWcw3sapksa7M/view?usp=drive_link)**

 2. 链接主板

 将SD卡插入主板，主板连接到电脑。大概10s左右，电脑设备管理器会多出一个usb串口

   ![](../../images/rm/usb_port.png ":size=50%")
 
 3. 打开串口调试助手

![](../../images/rm/serial1.png ":size=50%")


![](../../images/rm/serial2.png ":size=50%")

 输入M997 S1并按回车发送。给wifi模块烧录固件

![](../../images/rm/WIFI1.png ":size=50%")


 输入M552 S0 并按回车发送。关闭wifi连接

![](../../images/rm/WIFI2.png ":size=50%")

 输入M587 S"wifi账户" P"密码"并按回车发送。设置wifi账户密码。
 区分大小写，不支持5Gwifi

![](../../images/rm/WIFI3.png ":size=50%")

 输入M552 S1 并按回车发送。开启wifi连接
开启后正常情况下会反馈一个IP

![](../../images/rm/WIFI4.png ":size=50%")

4.浏览器打开IP

![](../../images/rm/PRINT.png ":size=100%")

## 6.完成基础配置
 接下来我们将主板装入机器进行调试
