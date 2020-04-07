![](https://github.com/iQIYIVR/QIYUVR/blob/master/images/dev-logo.png)
![](https://img.shields.io/badge/QIYU-VR-green) ![](https://img.shields.io/badge/QIYUVR-Unity-orange) 
![](https://img.shields.io/badge/QIYUVR-UNREAL-green) ![](https://img.shields.io/badge/QIYUVR-APPSTORE-blue)  
 欢迎来到爱奇艺奇遇VR开发者支持！  
 Welcome to the QIYUVR DEV!  
#
### 奇遇2P SDK开发文档
*版本：0327 2020.3.27*  

1.主要模块介绍和工程配置  
2.主要api接口  
3.手柄手势模型简介  
4.手柄资源规范  

======================  
1.主要模块介绍和工程配置 


 
**1.1 主入口模块**  
首先，将下图所示prefab拖入场景。  

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic1.png)  

QVRMain是SDK各主要模块的入口集合，主要包括EventCamera，InputModule（手柄模块），SvrCamera（相机渲染模块）等，如下图。  

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic2.png)  

可参考Assets/Sample/Scenes/SampleScene和Assets/Sample/Scenes/OtherScene  


 
**1.2 系统弹窗转3D显示模块** 
此模块根据应用需要选择是否拖入场景中，路径如下。 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic3.png)  

其中包含一个单独的canvas，里面是用于显示texture的image； 
canvas需要引入EventCamera，并可以根据应用调节大小，距离和scale，如下图所示。  

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic4.png) 

可参考Assets/Sample/Scenes/SampleScene  

**1.3 VR键盘模块** 
此模块根据应用需要选择是否拖入场景的canvas中，并根据应用调节大小，距离和scale，默认是隐藏状态。如下两图。  
![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic5.png)  

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic6.png)  

可参考Assets/Sample/Scenes/KeyboardScene 

**1.4 工程配置** 
建议使用unity 2018.4及以上版本，Platform选择Android，如图。 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic7.png) 

Orientation选择landscape Left，如图。 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic8.png) 

Other Setting参考设置如下两图。 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic9-1.png) 

![](https://github.com/iQIYIVR/QIYUVR/blob/master/SDK/pic/pic9-2.png) 

**2.主要api接口**  
2.1 camera相关属性和方法   
*QVRCameraMain.cs：*   
  *Head //获取头部transform*  
  *LeftEyeCamera //左camera*  
  *RightEyeCamera //右camera*  
  *Initialized //已初始化*  
  *IsRunning //运行中*  
  *RecenterTracking //重置* 
  *LockCamera //锁屏*  
  *IsLockCamera //是否已锁屏*  
  *EnableLog //开关log*  
*调用方式示例：QVRCameraMain.Instance.Head;* 

*SvrManager.cs：*  
Settings //包括trackPosition（是否追踪位置），headHeight（head高度），headDepth（head深度），eyeAntiAliasing（抗锯齿），cpuPerfLevel，gpuPerfLevel等。  
调用方式示例：SvrManager.Instance.settings.trackPosition = false;  
可参考Assets/Sample/Scenes/SampleScene 

**2.2 手柄按键和数据的接口**   
QVRInput    
  
bool Get(Button buttonMask, Controller controllerMask = Controller.Default)  
获取按钮事件(不松手一直触发)，默认是带射线的主手柄（以下相同）  











### HTC VIVE WAVE SDK 
    爱奇艺奇遇VR（2S不包含6DOF手柄/2P)现支持WaveSDK.请使用以下链接进行下载Unity或Unreal版本.  
    https://developer.vive.com/resources/knowledgebase/download-vive-wave-sdk-3-1-4-unity/
  
### SDK文档
    SDK说明文档请参阅以下链接内容,如果设备兼容问题请在Issues栏提问，我们将协助您解决问题。
    https://hub.vive.com/storage/docs/zh-cn/
    
