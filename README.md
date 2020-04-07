![](https://github.com/iQIYIVR/QIYUVR/blob/master/images/dev-logo.png)
![](https://img.shields.io/badge/QIYU-VR-green) ![](https://img.shields.io/badge/QIYUVR-Unity-orange) 
![](https://img.shields.io/badge/QIYUVR-UNREAL-green) ![](https://img.shields.io/badge/QIYUVR-APPSTORE-blue)  
 欢迎来到爱奇艺奇遇VR开发者支持！  
 Welcome to the QIYUVR DEV!  
#
# 奇遇2Pro UnitySDK开发文档
 ##### 版本：0327 2020.3.27  [SDK下载](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/2p_sdk_0327.unitypackage)
 ```
 安装提示：下载文件包后，加载入Unity即可。
 ```
 
```
1.模块介绍与工程配置  
2.API接口  
3.手柄手势模型简介  
4.手柄资源规范  
```

### 1.模块介绍和工程配置 
 
**1.1 主入口模块**  
###### 首先，将下图所示prefab拖入场景。  
<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic1.png" width="300"> 

###### QVRMain是SDK各主要模块的入口集合，主要包括EventCamera，InputModule（手柄模块），SvrCamera（相机渲染模块）等，如下图。 

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic2.png" width="200">  

###### 可参考Assets/Sample/Scenes/SampleScene和Assets/Sample/Scenes/OtherScene  
 
**1.2 系统弹窗转3D显示模块**   
###### 此模块根据应用需要选择是否拖入场景中，路径如下。 

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic3.png" width="300"> 

###### 其中包含一个单独的canvas，里面是用于显示texture的image； 
###### canvas需要引入EventCamera，并可以根据应用调节大小，距离和scale，如下图所示。  

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic4.png" width="600"> 

###### 可参考Assets/Sample/Scenes/SampleScene  

**1.3 VR键盘模块**   
###### 此模块根据应用需要选择是否拖入场景的canvas中，并根据应用调节大小，距离和scale，默认是隐藏状态。如下两图。  

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic5.png" width="300"> 

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic6.png" width="800"> 

###### 可参考Assets/Sample/Scenes/KeyboardScene 

**1.4 工程配置** 
###### 建议使用unity 2018.4及以上版本，Platform选择Android，如图。 

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic7.png" width="400">  

###### Orientation选择landscape Left，如图。 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic8.png) 

###### Other Setting参考设置如下两图。 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic9-1.png) 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic9-2.png) 

### 2.主要API接口 

**2.1 camera相关属性和方法**     
*QVRCameraMain.cs：*   
  > Head //获取头部transform  
  > LeftEyeCamera //左camera  
  > RightEyeCamera //右camera  
  > Initialized //已初始化  
  > IsRunning //运行中  
  > RecenterTracking //重置 
  > LockCamera //锁屏  
  > IsLockCamera //是否已锁屏  
  > EnableLog //开关log  
  > 调用方式示例：QVRCameraMain.Instance.Head; 

*SvrManager.cs：*  
> Settings  
> 包括trackPosition（是否追踪位置），headHeight（head高度），headDepth（head深度），eyeAntiAliasing（抗锯齿），cpuPerfLevel，gpuPerfLevel等。  
> 调用方式示例：SvrManager.Instance.settings.trackPosition = false;  
> 可参考Assets/Sample/Scenes/SampleScene 

**2.2 手柄按键和数据的接口**   
 cQVRInput      
> `bool Get(Button buttonMask, Controller controllerMask = Controller.Default)`   
> 获取按钮事件(不松手一直触发)，默认是带射线的主手柄（以下相同）  

> `float GetPressTime(Button buttonMask, Controller controllerMask = Controller.Default)`      
> 获取按压时间  

> `bool GetDown(Button buttonMask, Controller controllerMask = Controller.Default)`   
> 获取按钮按下事件  

> `bool GetUp(Button buttonMask, Controller controllerMask = Controller.Default)`   
> 获取按钮抬起事件  

> `float Get(Axis1D axis, Controller controllerMask = Controller.Default)`  
> 获取一维数据（trigger力度） 

> `Vector2 Get(Axis2D axis, Controller controllerMask = Controller.Default)`  
> 获取二维数据（触摸板坐标） 

> `bool GetTouch(Axis2D axis, Controller controllerMask = Controller.Default)`  
> 获取按键触摸状态 

> `Vector3 GetLocalPosition(Controller controllerMask = Controller.Default)`  
> 控制器位置 

> `Quaternion GetLocalRotation(Controller controllerMask = Controller.Default)`  
> 控制器旋转 

> `Vector3 GetPositionVelocity(Controller controllerMask = Controller.Default)`  
> 控制器线速度 

> `Vector3 GetPositionAcc(Controller controllerMask = Controller.Default)`  
> 控制器线加速度 

> `Vector3 GetOrientationVelocity(Controller controllerMask = Controller.Default)`  
> 控制器角速度 

> `Vector3 GetOrientationAcc(Controller controllerMask = Controller.Default)`  
> 控制器角加速度 

> `int GetBatteryPercentRemaining(Controller controllerMask = Controller.Default)`  
> 获取电量 

> `bool IsConnected(Controller controllerMask = Controller.Default)`  
> 控制器是否连接 

> `string GetVersion(Controller controllerMask = Controller.Default)`  
> 获取版本号 

> `SwipeType GetSwipe(Controller controllerMask = Controller.Default)`  
> 获取滑动手势 

> `void StartVibration(float amplitude, float duration, Controller controllerMask = Controller.Default)`  
> 震动手柄（强度，时长，手柄编号） 

> `Handedness GetDominentHand()`  
> 获取主手柄 

> `void SetDominentHand(Handedness val)`  
> 设置主手柄 

调用方式示例：  
> `QVRInput.IsConnected(QVRInput.Controller.LTouch)`   
> `QVRControllerInstanceManager.cs：`   
> `ControllerInstanceType CurrCtrllerInstanceType`  
> 获取和设置手柄显示还是手势显示 

> `Qiyi.Event.Controller：`  
> 包括CONNECTION_CHANGE等事件通知。  
 
调用方法示例：  
> `Event.AddListener(Event.Controller.CONNECTION_CHANGE, OnConnectionChange);`  
> `可参考Assets/Sample/Scenes/SampleScene` 

**2.3 系统服务模块接口** 

*QvrSdkService.cs：* 

> `string GetSn()`//获取设备SN  

> `string GetSystemVersion()` //获取设备系统版本  

> *string GetModel() //获取设备型号*  

> *string GetMacAddress() //获取Mac地址*  

> *void SetVolume(int volume) //设置音量，取值(0~15)*  

> *int GetVolume() //获取音量值（0~15）*  

> *string GetProperty(string key, string defaultValue) //获取属性*  

> *void SetProperty(string key, string value) //设置属性*  

> *void SetBrightness(int brightness) //设置亮度，取值(0~255)*  

> *int GetBrigthness() //获取亮度值（0~255）*  

> *void SetColorTemperature(int colorTemperature) //设置色温，取值(0~255)* 

> *int GetColorTemperature() //获取色温（0~255）*  

> *StorageInfo GetSdInfo() //获取存储容量信息*  

> *void OpenWifi() //打开wifi*  

> *void CloseWifi() //关闭wifi*  

> *bool IsWifiEnabled() //wifi是否打开*  

> *void Reboot() //重启* 

> *void Shutdown() //关机*  

> *void KeepScreenOn() //亮屏*  

> *void KeepScreenOff() //灭屏*  

> *void StartApp(string packageName, string data = null) //开启应用(应用包名, 传递参数)*  

> *void GetAppList(Action<List<LauncherInfo>> action) //获取应用列表* 
 
> *bool Is24Format() //是否是24小时制*  

> *void RegisterBattery(Action<ProtocolBatteryState> action) //注册电量广播*  
 
> *void UnregisterBattery() //取消电量广播*  

> *void RegisterWifi(Action<ProtocolWifiState> action) //注册wifi广播*  
 
> *void UnregisterWifi() //取消wifi广播*  

> *void RegisterAppInstall(Action<AppInstallState> action) //注册全局安装/卸载/覆盖安装广播*  
 
> *void UnregisterAppInstall() //取消全局安装/卸载/覆盖安装广播*  

> *void InstallApp(string apkPath, Action<AppInstallState> action = null) //安装应用*  
 
> *void UninstallApp(string packageName, Action<AppInstallState> action = null) //卸载应用*  
 
> *void ClearMemory(Action<ProtocolMemory> action) //清理缓存*  
 
可参考Assets/Sample/Scenes/SDKServiceDemo  

**2.4 VR键盘模块接口** 

*void SetInputField (IVrInputField inputField) //设置键盘所关联的输入框，以将输入内容显示在输入框中* 

*bool IsActive () //键盘是否在场景中显示* 

*void SetActive (bool active) //调出或隐藏键盘*

*bool IsDone () //输入是否完成*

*bool WasCanceled () //输入是否被取消* 

*void FinishInput (FinishAction action)//结束输入并隐藏键盘* 

*void ProcessKeyDown (KeyCode code, char c, EventModifiers modifiers)*   
处理键盘按键输入的内容(按键的KeyCode, 按键的字符, 按键的修饰按键)  

*bool IsCapsLock () //是否处于大写锁定状态* 

*void ClearInput () //清除输入的内容*  

*SupportedInputMethod GetCurrentInputMethod () //获取当前的输入法*  

*void InputSequence (string input) //输入一个字符串*  

*OnEndInputEvent OnEndInput; //点击“完成”按钮时回调*  

*nityEvent OnShow; //当键盘ui从隐藏到被显示的时候回调*  

*UnityEvent OnHide; //键盘被隐藏时回调* 

（注意：输入框UI上需要添加VrInputField.cs作为component）  
可参考Assets/Sample/Scenes/KeyboardScene 

**3.手柄手势模型简介** 

左右手柄和左右手模型prefab在如图所示路径。 

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic10.png" width="300"> 

运行时QVRControllerLoader会自动加载模型，如下图。 

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic11.png" width="700"> 

模型资源可根据规则进行替换，如下所示。 

<img src="https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic12.png" width="500"> 



### HTC VIVE WAVE SDK 
    爱奇艺奇遇VR（2S不包含6DOF手柄/2P)现支持WaveSDK.请使用以下链接进行下载Unity或Unreal版本.  
    https://developer.vive.com/resources/knowledgebase/download-vive-wave-sdk-3-1-4-unity/
  
### SDK文档
    SDK说明文档请参阅以下链接内容,如果设备兼容问题请在Issues栏提问，我们将协助您解决问题。
    https://hub.vive.com/storage/docs/zh-cn/
    
