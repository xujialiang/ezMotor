# ezMotor

智能小车系列-动力系统

项目使用麦克纳母轮。 支持小车向前、向后、向左、向右、向左前方、向右前方、向左后方、向右后方、向右旋转、向左旋转。

本库使用rpio，引脚使用物理引脚号。

本库在树莓派4B上进行测试。



本库使用 eztb6612 驱动轮子。

如果您使用其他型号的板子，可以替换为eztb6612。代码可参考eztb6612编写。



## 安装

```javascript
npm install ezmotor eztb6612 ezpwmforraspberry --save
```



## 测试轮子及IO口

在使用轮子时，可能我们插线的时候，无法确认IO口连接的是哪个轮子，我们可以做简单的测试。

```javascript
const MotorManager = require('./ezMotor.js');
const motorMgr = new MotorManager();
let motor = motorMgr.motorFactory(18, 22, ezPWM.PWMPin.PIN12);

motor.updateMotorSpeed(50); // 设定速度
motor.doForward();// 向前
motor.doForward();// 向后
```



## 使用

```javascript
const ezPWM = require('ezpwmforraspberry');
const MotorManager = require('ezmotor');
const motorMgr = new MotorManager();

// 通过上面的 测试轮子及IO口, 我们基本可以确定引脚对应的轮子。
// 由于使用rpio库，我们默认使用物理引脚号作为输入。
this.rightFront = motorMgr.motorFactory(18, 22, ezPWM.PWMPin.PIN12); //右前轮
this.leftFront = motorMgr.motorFactory(31, 29, ezPWM.PWMPin.PIN12);  //左前轮
this.rightBack = motorMgr.motorFactory(15, 16, ezPWM.PWMPin.PIN12);  //右后轮
this.leftBack = motorMgr.motorFactory(13, 11, ezPWM.PWMPin.PIN12);   //左后轮

// 设置前后左右轮子
motorMgr.setupMotors(this.leftFront, this.rightFront, this.leftBack, this.rightBack); 

motorMgr.doForward(); // 向前
motorMgr.doBackward();// 向后
motorMgr.doLeft();// 向左
motorMgr.doRight();// 向右
motorMgr.turnLeft();// 向左旋转
motorMgr.turnRight();// 向右旋转
motorMgr.doRightFront();// 向右前方
motorMgr.doLeftFront();// 向左前方
motorMgr.doRightBack();// 向右后方
motorMgr.doLeftBack();// 向左后方

```



有技术问题可微信我

![wechat](./vx.jpeg)

