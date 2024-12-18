# 自行车主控板

## 前系统特征
### 板载资源
- ESP32-C3-WROOM-2U, xx32F103C8T6
- 太阳能Buck降压电路，可用MPPT驱动
- USB 5V输出升压电路(PS7516)
- USB充电电路(TP4056)
- 数字功放(NS4168)
- 2路NMOS(可连接车灯、报警器)
- IMU传感器(QMI8610,ICM-42688-P)
- 磁力计(QMC6308,QMC7983)
- 气压计(SPL06-001)
- 温湿度计(AHT20)

### 接口
- 8PIN SPI显示屏接口
- 扬声器接口
- I2S麦克风
- TF卡槽
- 3.7V锂电池接口
- 外置I2C接口(连接传感器和GPIO扩展芯片)
- 指纹传感器接口
- 后系统接口(UART)
- USB-C口(可充电,连接ESP32-C3模块)
- USB-A口(可放电,连接xx32芯片)
- 5V输出接口，用于连接USB公头
- 霍尔传感器接口x2(2个可以用于区分前进和后退)

### 待添加
- USB PD输出
- 外置电池组接口
- 转向角编码器接口
- 板载LoRa模块

## 评论
前系统有一些射频发射源，GNSS模块和天线打算放在后系统附近，通过增大距离来减少干扰。  
暂时不考虑刷卡解锁，先考虑支持指纹和蓝牙  
按键，刹车开关，副车灯，风扇等电路等放在与显示屏同一块PCB中，使用PCA9555/TCA9555 GPIO扩展芯片  
为了提高稳定性，IMU和磁力计PCB上各有两个的不同封装可以焊接，只焊一个也可以。

为了减少git仓库占用空间，我在`git commit`提交前在KiCad中清除所有填充域(快捷键Ctrl+B)，您可以在打开后重新填充(快捷键B)  
在KiCad的Python控制台中，切换到该repo根目录运行下例命令
````python
import build
build.all()
```
即可自动完成添加泪滴、重新填充、应用PCB背面信息字符串

## 版权和许可证
Copyright (C) 2024 徐瑞骏

本设计以CERN开放硬件许可证第二版强互惠授权(CERN Open Hardware Licence Version 2 - Strongly Reciprocal)，许可证文件位于`LICENSE.txt`

本设计不提供任何保证
