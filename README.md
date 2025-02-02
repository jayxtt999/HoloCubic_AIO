# HoloCubic_AIO (All in one for HoloCubic)

* 原作者的项目链接 https://github.com/peng-zhihui/HoloCubic
* 本项目的地址 https://github.com/ClimbSnail/HoloCubic_AIO （最新版本）
* 或者 https://gitee.com/ClimbSnailQ/HoloCubic_AIO

# 自行使用开发板和元器件复刻HoloCubic_AIO
## 项目使用元器件
 - 开发板 doit-esp32-devkit-v1
 - mpu6050 模块
 - 1.3寸 TFT显示屏 OLED 液晶屏 st7735
 - 3位 WS2812 RGB LED 
 - 分光棱镜
 - sd卡 && 卡套
 
 ## 接线
### esp32-devkit-v1   <==>   st7735

23 ------------------ MOSI
 
18 ------------------ SCLK

25 ------------------ DC

26 ------------------ DC

5V------------------ VCC

GND------------------ GND


### esp32-devkit-v1   <==>   mpu6050

33 ------------------ SCL
 
32 ------------------ SDA

5V------------------ VCC

GND------------------ GND

### esp32-devkit-v1   <==>   sd

12 ------------------ MOSO

GND ------------------ GND

14 ------------------ SCK

5V ------------------ Vdd

GND ------------------ GND

13------------------ MOSI

15 ------------------ CS


###  esp32-devkit-v1   <==>   3位 WS2812 RGB LED

5V------------------ VCC

GND------------------ GND

17------------------ PIN

![image](https://github.com/jayxtt999/HoloCubic_AIO/blob/5038fa83bc50ca2284d45edfec70dda82df658dd/Image/esp32_1_3_mou6050_bb.jpg)


### 关于SD卡
参考 `https://blog.csdn.net/finedayforu/article/details/108727110?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165012432016782246459753%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165012432016782246459753&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-3-108727110.142^v9^control,157^v4^control&utm_term=esp32+SD%E5%8D%A1&spm=1018.2226.3001.4187`

![image](https://github.com/jayxtt999/HoloCubic_AIO/blob/5038fa83bc50ca2284d45edfec70dda82df658dd/Image/20220416234234.png)


### esp32divkitv1 引脚图

![image](https://github.com/jayxtt999/HoloCubic_AIO/blob/5038fa83bc50ca2284d45edfec70dda82df658dd/Image/202107191728226.png)



##代码改动
### 修改了原版本中的mpu引脚
`src\driver\imu.cpp` 中 `IMU_I2C_SDA` 和 `IMU_I2C_SCL` 的定义
### 修改了ST7789 中第5配置项的定义
`lib\TFT_eSPI\TFT_Drivers\ST7789_Rotation.h`  `case 5: #ifdef CGRAM_OFFSET..`
###  修改了RGB灯珠数量，因为我用的元器件有3颗灯珠
`src\driver\rgb_led.h` 中 `RGB_LED_NUM` , `src\driver\rgb_led.cpp` 中  `Pixel &Pixel::setRGB , Pixel &Pixel::setHVS `对 `rgb_buffers`数组的配置 



## 展示
![image](https://github.com/jayxtt999/HoloCubic_AIO/blob/b48e7157415dbd9ed0d1d3231f726cc77a5bf76f/Image/20220417000026.jpg)

## 其它
参考`https://github.com/ClimbSnail/HoloCubic_AIO` 项目作者的说明即可，感谢大佬们的无私奉献



