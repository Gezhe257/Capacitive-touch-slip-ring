# 电容触摸滑环

## Capacitive-touch-slip-ring



基于STM32F1的电容式触摸滑环，通过定时器输出PWM和ADC同步采样测量电容。

本项目部分硬件和代码参考自https://github.com/AnalogDragon/TouchPad-Demo ，并在该项目基础上作了一定的修改。

板子上电后在蜂鸣器响之前处于校准状态，请不要触摸。

<img width="1323" height="927" alt="image" src="https://github.com/user-attachments/assets/a61eacde-a239-43cf-befc-39610f33f032" />



## 电容测量原理

<img width="710" height="308" alt="image" src="https://github.com/user-attachments/assets/506602e9-07fd-44a3-af45-5530f96ad77b" />

PWM输出一个1kHz，占空比50%的PWM波，高电平期间，通过一个1MΩ的电阻给电容充电，下降沿时，进行ADC采样，即可获得当前的电容值，当手指放在触摸板上，电容增大，根据 U = Q/C，电压变小，即判定当前触摸板发生了触摸。

触摸位置的判定是根据各个极板的触摸强度进行反正切计算后得到的，详情请参见代码。
