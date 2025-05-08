# 获取传感器温度，湿度，光照度
THISensorApplication
#### 实验目的
•	监测传感器的温度，湿度，光照
•	使用定时器周期性监测数据
#### 实验过程
•	启动应用，接收或手动刷新传感器推送的数据
•	改变环境的温度，湿度，光照，查看手机端数据变化


#### 核心类说明
| 类路径                                        | 描述                              |
| ------------------------------------------ | ------------------------------- |
| `owon/sdk/util/DeviceMessagesManager.java` | 设备操作类，封装灯光、电机、传感器等设备的控制与查询方法    |
| `owon/sdk/util/SocketMessageListener.java` | 数据回调类，包含登录结果、设备操作结果、设备状态获取等回调方法 |

###### 设备数据回调方法
类名： SocketMessageListener.java
方法： getMessage
| 字段名         | 类型    | 描述                 |
| ----------- | ----- | ------------------ |
| `commandID` | int   | 数据回调码（对应回调类型常量）    |
| `bean`      | class | 数据返回基类，需强转为对应设备的子类 |


### 功能接口
#### 获取温湿度

**方法**  
`getDeviceState`

**返回值**  
`bean` 转换子类 `z_SensorTempHumBean`

| 属性 | 类型 | 描述     |
|------|------|----------|
| temp | int  | 温度数值 |
| hum  | int  | 湿度数值 |

---

#### 获取光照

**方法**  
`getDeviceState`

**返回值**  
`bean` 转换子类 `z_SensorIlluminationBean`

| 属性        | 类型 | 描述       |
|-------------|------|------------|
| illumination | int  | 光照数值   |


#### 数据回调码
回调方法： getMessage
| 属性                                    | 描述           |
| ------------------------------------- | ------------ |
| `Constants.UpdateEPList`              | 获取网关列表       |
| `Constants.ZigBeeGetEPList`           | 获取设备列表       |
| `Constants.SmartLightSetupSwitchgear` | 设置灯光结果       |
| `Constants.UpdateSwitchgear`          | 查询或控制灯后的状态回调 |
| `Constants.UpdateLight`               | 物理控制灯后的状态回调  |
| `Constants.THI_UPDATE`                | 温湿度传感器数据回调   |
| `Constants.ILLUM_UPDATE`              | 光照传感器数据回调    |
| `Constants.MotionSensorUpdate`        | 人体传感器查询状态回调  |
| `Constants.MotionSensor`              | 人体传感触发数据回调   |
| `Constants.WarningSensor`             | 烟雾监测数据回调     |

#### 设备类型
| 属性                                            | 描述        |
| --------------------------------------------- | --------- |
| `Constants.LIGHT_601`                         | 灯，只有开关    |
| `Constants.LIGHT_EXTEND_LO_COLOR_TEMP_GOODVB` | 可调节亮度和色温灯 |
| `DeviceTypeCode.TH_SENSOR`                    | 温湿度传感器    |
| `DeviceTypeCode.LX_SENSOR`                    | 光照传感器     |
| `DeviceTypeCode.SMOKE_SENSOR_ZONE`            | 烟雾报警器     |
| `DeviceTypeCode.MOTION_SENSOR_ZONE`           | 人体传感器     |
| `DeviceTypeCode.AC_SENSOR`                    | 红外转发器     |
| `DeviceTypeCode.WARN_SENSOR`                  | 声光报警器     |
| `DeviceTypeCode.WARN_MOTOR`                   | 窗帘电机      |
| `DeviceTypeCode.DOOR_SENSOR`                  | 门磁感应器     |



