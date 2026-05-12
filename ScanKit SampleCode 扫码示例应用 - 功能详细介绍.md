0\. 工程目录

scankit-samplecode-clientdemo-arkts-master/

├── AppScope/                                    # 应用全局作用域

│   ├── app.json5                               #   应用全局配置（包名、版本号、图标、标签）

│   └── resources/base/

│       ├── element/string.json                 #   应用级字符串资源

│       ├── media/app\_icon.png                  #   应用图标

│       └── profile/configuration.json          #   配置文件

│

├── entry/                                       # 主模块（HAP 包）

│   ├── build-profile.json5                     #   模块构建配置

│   ├── oh-package.json5                        #   模块包依赖信息

│   ├── hvigorfile.ts                           #   Hvigor 构建脚本

│   ├── screenshots/                            #   应用截图目录

│   │   ├── defaultMutiScanEs/                  #     默认多码扫描截图

│   │   ├── defaultResultEs/                    #     默认结果页截图

│   │   ├── generateResultEs/                   #     生成码结果截图

│   │   ├── generateRideResultEs/               #     乘车码生成截图

│   │   ├── homePageEs/                         #     首页截图

│   │   ├── qrcode/                             #     二维码相关截图

│   │   └── scanSuccess/                        #     扫描成功截图

│   │

│   └── src/main/

│       ├── module.json5                        #   模块配置（Ability 声明、页面路由）

│       │

│       ├── ets/                                 # ===== ArkTS 源码 =====

│       │   ├── entryability/

│       │   │   └── EntryAbility.ets            #     应用入口 Ability

│       │   │

│       │   ├── common/                         #     公共组件与工具

│       │   │   ├── CommonComponents.ets        #       公共组件（加载动画等）

│       │   │   ├── CommonTipsDialog.ets        #       公共提示弹窗

│       │   │   ├── Logger.ts                   #       日志工具类

│       │   │   ├── PermissionsUtil.ets         #       权限管理工具

│       │   │   ├── StatusBar.ets               #       状态栏组件

│       │   │   └── Utils.ets                   #       通用工具函数

│       │   │

│       │   └── pages/                          # ===== 页面模块 =====

│       │       ├── Index.ets                   #       首页（功能入口）

│       │       │

│       │       ├── access/                     #       权限申请页面

│       │       │   ├── ScanAccess.ets          #         扫码权限页

│       │       │   └── ScanDetail.ets          #         扫描详情页

│       │       │

│       │       ├── customScan/                 #       自定义扫码（完整版）

│       │       │   ├── CustomPage.ets          #         自定义扫码主页面

│       │       │   ├── constants/              #         常量定义

│       │       │   │   ├── BreakpointConstants.ets   #     断点常量

│       │       │   │   └── CommonConstants.ets       #     通用常量

│       │       │   ├── model/                  #         数据模型层

│       │       │   │   ├── BreakpointType.ets        #     断点类型

│       │       │   │   ├── CommonEventManager.ets   #     事件管理

│       │       │   │   ├── DeviceService.ets         #     设备服务

│       │       │   │   ├── OpenPhoto.ets             #     打开相册

│       │       │   │   ├── PromptTone.ts             #     提示音

│       │       │   │   ├── ScanLayout.ets            #     扫码布局

│       │       │   │   ├── ScanService.ets           #     扫码服务

│       │       │   │   ├── UIContextSelf.ets         #     UI上下文

│       │       │   │   ├── WindowService.ets         #     窗口服务

│       │       │   │   └── XComponentService.ets     #     XComponent服务

│       │       │   ├── pages/                  #         子页面

│       │       │   │   └── ScanPage.ets        #           扫码页面

│       │       │   └── view/                   #         视图组件层

│       │       │       ├── CommonCodeLayout.ets      #     通用布局

│       │       │       ├── IconPress.ets              #     按压图标

│       │       │       ├── MaskLayer.ets              #     遮罩层

│       │       │       ├── PickerDialog.ets           #     选择器弹窗

│       │       │       ├── ScanBottom.ets             #     底部栏

│       │       │       ├── ScanLine.ets               #     扫描线

│       │       │       ├── ScanLoading.ets            #     加载动画

│       │       │       ├── ScanTitle.ets              #     标题栏

│       │       │       └── ScanXComponent.ets         #     相机预览组件

│       │       │

│       │       ├── customScanV2/                #       自定义扫码 V2（精简版）

│       │       │   ├── model/                  #         数据模型层

│       │       │   │   ├── ConfigStorage.ets          #     配置存储

│       │       │   │   ├── OpenPhoto.ets              #     打开相册

│       │       │   │   ├── ScanLayout.ets             #     扫码布局

│       │       │   │   ├── ScanService.ets            #     扫码服务

│       │       │   │   ├── WindowService.ets          #     窗口服务

│       │       │   │   └── XComponentService.ets      #     XComponent服务

│       │       │   ├── pages/                  #         子页面

│       │       │   │   └── ScanPage.ets        #           扫码页面

│       │       │   └── view/                   #         视图组件层

│       │       │       ├── CommonCodeLayout.ets      #     通用布局

│       │       │       ├── IconPress.ets              #     按压图标

│       │       │       ├── MaskLayer.ets              #     遮罩层

│       │       │       ├── PickerDialog.ets           #     选择器弹窗

│       │       │       ├── ScanBottom.ets             #     底部栏

│       │       │       ├── ScanLine.ets               #     扫描线

│       │       │       ├── ScanLoading.ets            #     加载动画

│       │       │       ├── ScanTitle.ets              #     标题栏

│       │       │       └── ScanXComponent.ets         #     相机预览组件

│       │       │

│       │       ├── defaultScan/                 #       默认扫码页面

│       │       │   └── DefaultScan.ets          #         默认扫码实现

│       │       │

│       │       ├── detectBarcode/               #       条码检测页面

│       │       │   ├── CommonCodeLayout.ets    #         通用布局

│       │       │   ├── DecodeBarcode.ets       #         条码解码

│       │       │   └── DecodeCameraYuv.ets     #         相机 YUV 数据处理

│       │       │

│       │       ├── generateBarcode/             #       条码生成页面

│       │       │   └── CreateBarcode.ets       #         创建条码（二维码/条形码）

│       │       │

│       │       └── resultPage/                  #       结果展示页面

│       │           └── ResultPage.ets          #         扫描结果页

│       │

│       └── resources/                           # ===== 应用资源 =====

│           ├── base/                            #   基础资源（默认语言）

│           │   ├── element/

│           │   │   ├── color.json               #     颜色资源

│           │   │   ├── float.json               #     尺寸资源

│           │   │   └── string.json              #     字符串资源

│           │   ├── media/                       #     图标资源

│           │   │   └── icon/                    #       应用图标

│           │   └── profile/

│           │       └── main\_pages.json          #     页面路由配置

│           ├── rawfile/                         #   原始资源文件

│           │   ├── access.jpg                   #     权限引导图

│           │   ├── accessEs.jpg                 #     权限引导图（西班牙语）

│           │   ├── di.ogg                       #     扫描提示音

│           │   ├── scan\_back.svg                #     返回按钮图标

│           │   ├── scan\_close.svg               #     关闭按钮图标

│           │   ├── scan\_line.png                #     扫描线图片

│           │   ├── scan\_photo.svg               #     相册按钮图标

│           │   ├── scan\_selected.svg            #     选中状态图标

│           │   ├── scan\_selected2.svg           #     选中状态图标2

│           │   └── scan\_shadow.png              #     扫描框阴影

│           ├── zh\_CN/                           #   中文资源

│           │   └── element/string.json          #     中文字符串

│           └── en\_US/                           #   英文资源

│               └── element/string.json          #     英文字符串

│

├── hvigor/                                       # Hvigor 构建配置

│   └── hvigor-config.json5                      #   构建配置

│

├── build-profile.json5                          # 项目级构建配置

├── oh-package.json5                             # 项目级包信息

├── hvigorfile.ts                                # Hvigor 根构建脚本

├── LICENSE                                      # 开源许可证

├── OAT                                          # OAT 检查文件

├── readme\_cn.md                                 # 中文说明文档

└── readme\_en.md                                 # 英文说明文档



目录职责说明

目录/文件	                                                       层级	           职责

AppScope/	                                            应用层	全局配置与资源

entry/	                                                       模块层	主功能模块

entry/ets/common/	                                 公共层	复用组件和工具类

entry/ets/pages/	                                 页面层	各功能页面入口

entry/ets/pages/customScan/	           业务层	完整版自定义扫码实现

entry/ets/pages/customScanV2/	业务层	精简版自定义扫码实现

entry/ets/pages/defaultScan/	           业务层	默认扫码实现

entry/ets/pages/detectBarcode/	业务层	条码检测功能

entry/ets/pages/generateBarcode/	业务层	条码生成功能

entry/ets/entryability/	                      入口层	应用生命周期

entry/resources/	                                 资源层	静态资源文件

screenshots/	                                            文档层	应用功能截图



1\. 应用概述

1.1 应用定位

这是一个基于华为 ScanKit 扫码 SDK 的鸿蒙原生示例应用（Sample Code），旨在演示如何在 HarmonyOS 应用中集成 ScanKit 实现各类扫码功能。



1.2 核心功能模块

模块	                      功能描述

默认扫码	           最简扫码实现，快速集成

自定义扫码	           完全自定义 UI 的扫码界面（完整版）

自定义扫码 V2	精简版自定义扫码实现

条码检测	           从图片中检测和识别条码

条码生成	           生成二维码、条形码等

多码扫描	           支持同时识别多个条码

结果页面	           展示扫描结果和详情



1.3 技术架构

\-开发框架：HarmonyOS ArkTS

\-扫码能力：华为 ScanKit SDK

\-相机控制：XComponent 自定义相机预览

\-架构模式：MVVM（Model-View-ViewModel）

\-权限管理：动态权限申请（相机、存储）



2\. 首页功能

2.1 功能入口

Index.ets 作为应用主页面，提供以下功能入口：

入口	                      说明

默认扫码	           跳转 DefaultScan 页面，使用系统默认扫码界面

自定义扫码	           跳转 CustomPage（customScan），完全自定义 UI

自定义扫码 V2	跳转 customScanV2，简化的自定义实现

条码检测	           跳转 decodeBarcode 页面，从相册选择图片识别条码

条码生成	           跳转 CreateBarcode 页面，生成二维码/条形码

多码扫描	           在自定义扫码中支持同时识别多个条码



2.2 页面路由

页面路由通过 main\_pages.json 注册：

{

&#x20; "src": \[

&#x20;   "pages/Index",

&#x20;   "pages/access/ScanAccess",

&#x20;   "pages/access/ScanDetail",

&#x20;   "pages/customScan/CustomPage",

&#x20;   "pages/customScan/pages/ScanPage",

&#x20;   "pages/customScanV2/pages/ScanPage",

&#x20;   "pages/defaultScan/DefaultScan",

&#x20;   "pages/detectBarcode/DecodeBarcode",

&#x20;   "pages/generateBarcode/CreateBarcode",

&#x20;   "pages/resultPage/ResultPage"

&#x20; ]

}



3\. 默认扫码（DefaultScan）

3.1 功能说明

\-最简扫码实现，使用 ScanKit 提供的默认扫码界面

\-适用于快速集成，无需自定义 UI

\-开发者只需调用 scan 接口，SDK 自动处理相机预览和识别



3.2 调用流程

1\.申请相机权限

2\.调用 ScanKit 扫码 API

3\.接收扫描结果

4\.跳转结果页展示



3.3 实现文件

DefaultScan.ets：默认扫码主逻辑



4\. 自定义扫码（CustomScan / CustomScanV2）

4.1 两种实现对比

特性	                      customScan（完整版）	          customScanV2（精简版）

UI 自定义程度	高，完全自定义	                                 高，完全自定义

代码复杂度 	较高	                                                        较低

功能完整度	           包含更多功能（提示音、多码等）	核心功能精简

适用场景	           需要深度定制的场景	                       需要快速自定义 UI 的



4.2 自定义 UI 组件

自定义扫码页面包含以下 UI 组件（位于 view/ 目录）：

组件	                                            功能

ScanTitle.ets	                      顶部标题栏（返回按钮、闪光灯、相册入口）

ScanLine.ets	                      扫描动画线（上下移动效果）

ScanBottom.ets	                      底部操作栏（提示文字等）

ScanLoading.ets	           加载动画（识别中状态）

MaskLayer.ets	                      遮罩层（扫描框外区域变暗）

IconPress.ets	                      可按压图标按钮组件

PickerDialog.ets	           相册选择器弹窗

CommonCodeLayout.ets	通用布局组件



4.3 相机预览

\-使用 XComponent 组件实现相机预览

\-ScanXComponent.ets：封装相机预览逻辑

\-支持实时预览帧处理，用于条码识别



4.4 扫描流程

用户打开扫码页面

&#x20;   │

&#x20;   ▼

申请相机权限（首次）

&#x20;   │

&#x20;   ▼

初始化 XComponent 相机预览

&#x20;   │

&#x20;   ▼

ScanKit 引擎初始化

&#x20;   │

&#x20;   ▼

实时识别预览帧中的条码

&#x20;   │

&#x20;   ├── 识别成功 ──► 震动/提示音 ──► 获取结果 ──► 跳转结果页

&#x20;   │

&#x20;   └── 识别失败 ──► 继续扫描



4.5 核心服务（model/）

服务	                                                       职责

ScanService.ets	                                 扫码核心服务，调用 ScanKit API

WindowService.ets	                      窗口管理（全屏、方向等）

XComponentService.ets	           相机预览管理

DeviceService.ets	                      设备信息与震动控制

OpenPhoto.ets	                                 从相册选择图片识别条码

CommonEventManager.ets	跨组件事件通信

PromptTone.ts	                                  提示音播放（扫描成功音效）



4.6 提示音功能

\-扫描成功时播放 di.ogg 提示音

\-支持自定义开启/关闭



5\. 条码检测（DetectBarcode）

5.1 功能说明

\-从相册选择包含条码的图片

\-使用 ScanKit 检测图片中的条码

\-支持同时识别图片中的多个条码



5.2 实现文件

文件	                                            职责

DecodeBarcode.ets	           条码解码主逻辑

DecodeCameraYuv.ets	相机 YUV 格式数据处理

CommonCodeLayout.ets	页面布局组件



5.3 识别流程

1\.点击"从相册选择"按钮

2\.调用系统相册选择器

3\.将选中图片传递给 ScanKit 检测

4\.解析检测结果

5\.跳转结果页展示



6\. 条码生成（GenerateBarcode）

6.1 功能说明

\-支持生成二维码和条形码

\-用户输入文本内容

\-选择条码类型和尺寸

\-实时生成并预览



6.2 支持的条码类型

类型	           说明

QR Code	二维码

Code 128	一维条形码

Code 39	一维条形码

EAN-13	商品条码

EAN-8	商品条码

UPC-A	商品条码

ITF	           交叉二五条码

Codabar	库德巴条码



6.3 实现文件

CreateBarcode.ets：条码生成主逻辑



6.4 生成流程

1\.用户输入文本内容

2\.选择条码类型

3\.设置条码尺寸（宽/高/纠错级别）

4\.调用 ScanKit 生成接口

5\.预览生成结果

6\.支持保存到相册



7\. 结果页面（ResultPage）

7.1 功能说明

\-展示扫码/检测到的条码结果

\-显示条码类型和原始数据

\-支持复制结果到剪贴板

\-支持打开结果中的 URL（如果是网址）



7.2 实现文件

ResultPage.ets：结果展示页面



7.3 数据传递

\-通过页面路由参数传递扫描结果

\-包含：条码内容（resultString）、条码类型（resultType）、原始数据等



8\. 权限管理

8.1 所需权限

权限	                                                        用途

ohos.permission.CAMERA	           相机权限，用于扫码预览

ohos.permission.READ\_MEDIA	读取相册权限，用于选择图片识别



8.2 权限申请流程

\-PermissionsUtil.ets：权限管理工具类

\-首次进入扫码页面时动态申请权限

\-权限被拒绝时引导用户到设置页开启

\-ScanAccess.ets：权限引导页面



8.3 权限状态管理

未授权 ──► 请求权限

&#x20;   │

&#x20;   ├── 同意 ──► 进入扫码页面

&#x20;   │

&#x20;   └── 拒绝 ──► 显示引导弹窗

&#x20;             │

&#x20;             └── 跳转设置页 / 再次申请



9\. 公共组件（common/）

9.1 组件列表

组件	                                             功能

CommonComponents.ets	公共 UI 组件（加载动画等）

CommonTipsDialog.ets	通用提示弹窗

StatusBar.ets	                      沉浸式状态栏适配



9.2 工具类

工具	                                 功能

Logger.ts	                      日志输出（支持分级：debug/info/warn/error）

Utils.ets	                      通用工具函数（日期、字符串、文件处理等）

PermissionsUtil.ets	权限申请封装



10\. 扫描模式分类

10.1 单码扫描

\-默认模式：每次只识别一个条码

\-识别成功后自动停止扫描



10.2 多码扫描

\-同一画面可同时识别多个条码

\-返回所有识别到的条码列表

\-用户可选择其中一个进行后续处理

\-适用于包含多个条码的商品、票据等场景



10.3 连续扫描

\-识别成功后不停止，继续扫描

\-适用于批量扫描场景



11\. XComponent 相机预览

11.1 技术实现

\-使用 XComponent 组件（type = 'surface'）渲染相机预览

\-通过 nodeId 与 Native 层通信

\-设置预览分辨率为 1920x1080



11.2 生命周期管理

aboutToAppear()

&#x20;   │

&#x20;   ├── 初始化 XComponent 控制器

&#x20;   │

&#x20;   ▼

onLoad() 回调

&#x20;   │

&#x20;   ├── 创建 Surface

&#x20;   ├── 启动相机预览

&#x20;   ├── 初始化 ScanKit 引擎

&#x20;   │

&#x20;   ▼

onUnload() 回调

&#x20;   │

&#x20;   ├── 释放相机资源

&#x20;   ├── 销毁 ScanKit 引擎

&#x20;   └── 释放 Surface



12\. 扫描视觉反馈

12.1 扫描线动画

\-ScanLine.ets 实现扫描框内的上下移动动画

\-使用 @State 控制位置偏移

\-通过 animateTo 实现平滑过渡



12.2 震动反馈

\-扫描成功时触发设备震动

\-通过 DeviceService.ets 调用 vibrator API



12.3 音效反馈

\-扫描成功时播放提示音

\-资源文件：di.ogg

\-通过 PromptTone.ts 管理



12.4 视觉遮罩

MaskLayer.ets 在扫描框外区域叠加半透明遮罩



突出扫描区域，提升用户体验



13\. 资源文件说明

13.1 图标资源（media/icon/）

图标	                                 用途

app\_icon.png	           应用图标

scan\_back.svg	           返回按钮

scan\_close.svg	           关闭按钮

scan\_photo.svg	           相册按钮

scan\_selected.svg	选中状态

scan\_selected2.svg	选中状态（备用）



13.2 图片资源（rawfile/）

文件	                                 用途

access.jpg	                      权限引导图

accessEs.jpg	           权限引导图（西班牙语）

scan\_line.png	           扫描线图片

scan\_shadow.png	扫描框阴影



13.3 音频资源（rawfile/）

文件	           用途

di.ogg	扫描成功提示音



14\. 多语言支持

14.1 支持语言

语言	                                 资源目录

简体中文	                      resources/zh\_CN/

英文	                                  resources/en\_US/

默认（英文后备）	resources/base/



14.2 字符串资源示例

Key	              中文	 英文

app\_name	   扫码示例	 Scan Sample

scan	              扫一扫	 Scan

generate	   生成条码	 Generate

album	   相册	 Album

torch	              闪光灯	 Torch



15\. 构建与运行

15.1 开发环境要求

组件	                                 版本要求

DevEco Studio	           5.0.0或更高

HarmonyOS SDK	API12或更高

测试设备	                      支持相机功能的鸿蒙设备



15.2 依赖配置

oh-package.json5 中声明对 ScanKit SDK 的依赖：

{

&#x20; "dependencies": {

&#x20;   "@hms/core-scan-kit": "^1.0.0"

&#x20; }

}



15.3 构建产物

构建后生成 HAP 文件：

\-SampleCode\_entry-default-unsigned.hap

\-路径：entry/build/default/outputs/default/



16\. 功能对比总结

功能模块	customScan	           customScanV2	           defaultScan	detectBarcode	   generateBarcode

自定义 UI	✅ 完整	                      ✅ 精简	                      ❌ 默认UI	           ✅ 有	              ✅ 有

相机预览	✅ XComponent	✅ XComponent	✅ SDK内置	❌	                         ❌

相册识别	✅	                                  ✅	                                 ✅	                      ✅	                         ❌

多码扫描	✅	                                  ❌	                                 ❌	                      ✅                           	   ❌

连续扫描	✅	                                  ❌	                                 ❌	                      ❌	                         ❌

扫描线动画	✅	                                  ✅	                                 ❌	                      ❌	                         ❌

提示音	✅	                                  ❌	                                 ❌	                      ❌	                         ❌

震动反馈	✅	                                  ✅	                                 ✅	                      ✅	                         ❌

条码生成	❌	                                  ❌	                                 ❌	                      ❌	                         ✅



17\. 核心 API 调用示例

17.1 初始化 ScanKit

import scan from '@hms.core.scan.scanKit';



// 初始化扫码引擎

scan.init(context);



17.2 开始扫描

// 配置扫码参数

let scanOptions: scan.ScanOptions = {

&#x20; scanType: scan.ScanType.ALL,

&#x20; multiMode: scan.MultiMode.SINGLE

};



// 开始扫描

scan.startScan(scanOptions, (result: scan.ScanResult) => {

&#x20; console.info('Scan result: ' + result.originalValue);

});



17.3 生成条码

import { createBarcode } from '@hms.core.scan.barcode';



let barcodeOptions: createBarcode.CreateOptions = {

&#x20; content: 'https://example.com',

&#x20; type: createBarcode.BarcodeFormat.QR\_CODE,

&#x20; width: 500,

&#x20; height: 500

};



createBarcode.create(barcodeOptions).then((pixelMap) => {

&#x20; // 显示生成的条码图片

});



18\. 注意事项

1\.相机权限：首次使用需要用户授权相机权限，需做好权限被拒绝的引导处理

2\.性能优化：相机预览帧率建议控制在 30fps 以内，避免过度消耗资源

3\.多码识别：多码模式会增加识别耗时，建议根据场景选择合适的模式

4\.XComponent 限制：自定义相机预览需要处理 XComponent 的生命周期，避免内存泄漏

5\.扫描区域：自定义扫描区域时，需要将识别区域与预览区域进行坐标转换

