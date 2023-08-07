# Humanoid robot


Hand + Arm
Head
Body
Leg + Foot

## Target

1. A fully autonomous humanoid robot

2. 支撑骨架而不是外包围，方便以后扩展和支持皮肤触觉传感器。并且外漏布线方便调试。

3. 仿真快速验证，然后建造，降低成本。


## Think

1. 生物关节很多是弱连接的，骨接触面是一个滑动面，通过滑动面周围结缔组织链接，这使得很多关节有具有三维运动的特征。例如踢毽子的动作，推不止能前后弯曲，还有左右的摆动。机械关节如何实现这种效果？

2. 生物关节之间的结缔组织还具有减震效果，机械关节如何做到？


## Create Step

1. A Hand

2. Hands + Arms


3. Body


4. Foots + legs

## Precondition

建模 -> FreeCAD
仿真 -> CoppeliaSim
电路 -> KiCAD + 输电、模电
制造 -> 沃龙打印机

解剖结构 -> 艾氏解剖
电机 -> 
控制板 -> Esp32
机器人控制 -> ROS2
AI -> PyTouch (深度学习，强化学习。。。。) Nvidia 学习卡
