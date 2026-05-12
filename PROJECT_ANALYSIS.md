\# ScanKit SampleCode 扫码示例应用 - 工程分析文档



\## 1. 工程基本信息

| 项目 | 信息 |

|------|------|

| 项目名称 | scankit-samplecode-clientdemo-arkts |

| 应用名称 | Scan Sample / 扫码示例 |

| 开发框架 | HarmonyOS ArkTS |

| SDK 版本 | API 12+ |

| 构建工具 | Hvigor |

| 核心 SDK | 华为 ScanKit 扫码SDK |

| 开源协议 | Apache License 2.0 |



\## 2. 完整工程目录结构

scankit-samplecode-clientdemo-arkts-master/

├── AppScope/ # 应用全局作用域

│ ├── app.json5 # 应用配置（包名、版本、图标）

│ └── resources/base/

│ ├── element/string.json # 应用名称

│ ├── media/app\_icon.png # 应用图标

│ └── profile/configuration.json # 配置文件

│

├── entry/ # 主模块

│ ├── build-profile.json5 # 模块构建配置

│ ├── oh-package.json5 # 依赖配置

│ ├── hvigorfile.ts # 构建脚本

│ ├── screenshots/ # 功能截图目录

│ │ ├── defaultMutiScanEs/ # 多码扫描截图

│ │ ├── defaultResultEs/ # 结果页截图

│ │ ├── generateResultEs/ # 生成码结果截图

│ │ ├── generateRideResultEs/ # 乘车码截图

│ │ ├── homePageEs/ # 首页截图

│ │ ├── qrcode/ # 二维码截图

│ │ └── scanSuccess/ # 扫描成功截图

│ │

│ └── src/main/

│ ├── module.json5 # 模块配置

│ │

│ ├── ets/ # ArkTS 源码

│ │ ├── entryability/

│ │ │ └── EntryAbility.ets # 应用入口

│ │ │

│ │ ├── common/ # 公共模块

│ │ │ ├── CommonComponents.ets # 公共组件（加载动画）

│ │ │ ├── CommonTipsDialog.ets # 提示弹窗

│ │ │ ├── Logger.ts # 日志工具

│ │ │ ├── PermissionsUtil.ets # 权限管理

│ │ │ ├── StatusBar.ets # 状态栏

│ │ │ └── Utils.ets # 通用工具

│ │ │

│ │ └── pages/ # 功能页面

│ │ ├── Index.ets # 首页（功能入口）

│ │ │

│ │ ├── access/ # 权限页面

│ │ │ ├── ScanAccess.ets # 权限申请页

│ │ │ └── ScanDetail.ets # 扫描详情

│ │ │

│ │ ├── customScan/ # 自定义扫码（完整版）

│ │ │ ├── CustomPage.ets # 主页面

│ │ │ ├── constants/ # 常量

│ │ │ ├── model/ # 数据模型（11个服务类）

│ │ │ ├── pages/ScanPage.ets # 扫码页

│ │ │ └── view/ # UI组件（9个）

│ │ │

│ │ ├── customScanV2/ # 自定义扫码（精简版）

│ │ │ ├── model/ # 数据模型（6个服务类）

│ │ │ ├── pages/ScanPage.ets # 扫码页

│ │ │ └── view/ # UI组件（9个）

│ │ │

│ │ ├── defaultScan/ # 默认扫码

│ │ │ └── DefaultScan.ets # 默认扫码实现

│ │ │

│ │ ├── detectBarcode/ # 条码检测

│ │ │ ├── CommonCodeLayout.ets # 布局

│ │ │ ├── DecodeBarcode.ets # 解码

│ │ │ └── DecodeCameraYuv.ets # YUV处理

│ │ │

│ │ ├── generateBarcode/ # 条码生成

│ │ │ └── CreateBarcode.ets # 生成器

│ │ │

│ │ └── resultPage/ # 结果页

│ │ └── ResultPage.ets # 结果展示

│ │

│ └── resources/ # 资源文件

│ ├── base/ # 基础资源

│ │ ├── element/（color.json, float.json, string.json）

│ │ ├── media/icon/ # 图标

│ │ └── profile/main\_pages.json # 路由配置

│ ├── rawfile/ # 原始文件

│ │ ├── access.jpg # 权限引导图

│ │ ├── accessEs.jpg # 西语引导图

│ │ ├── di.ogg # 提示音

│ │ ├── scan\_\*.svg/png # UI素材（9个）

│ │ └── ...

│ ├── zh\_CN/ # 中文资源

│ └── en\_US/ # 英文资源

│

├── hvigor/ # 构建配置

│ └── hvigor-config.json5

│

├── build-profile.json5 # 项目构建配置

├── oh-package.json5 # 项目依赖

├── hvigorfile.ts # 根构建脚本

├── LICENSE # Apache 2.0

├── OAT # OAT检查

├── readme\_cn.md # 中文说明

└── readme\_en.md # 英文说明



\## 3. 代码文件统计

| 模块 | 文件数 | 说明 |

|------|--------|------|

| entryability | 1 | 应用入口 |

| common | 6 | 公共组件和工具 |

| pages/Index | 1 | 首页 |

| pages/access | 2 | 权限页面 |

| pages/customScan | 23 | 完整版自定义扫码 |

| pages/customScanV2 | 18 | 精简版自定义扫码 |

| pages/defaultScan | 1 | 默认扫码 |

| pages/detectBarcode | 3 | 条码检测 |

| pages/generateBarcode | 1 | 条码生成 |

| pages/resultPage | 1 | 结果页 |

| \*\*总计\*\* | \*\*57\*\* | \*\*ArkTS/TS 源文件\*\* |



\## 4. 核心服务类说明（model/）

\### 4.1 customScan/model/（11个）

| 服务 | 职责 |

|------|------|

| `BreakpointType.ets` | 断点类型定义 |

| `CommonEventManager.ets` | 跨组件事件通信 |

| `DeviceService.ets` | 震动、设备信息 |

| `OpenPhoto.ets` | 相册选择与识别 |

| `PromptTone.ts` | 提示音播放 |

| `ScanLayout.ets` | 扫描区域布局计算 |

| `ScanService.ets` | 扫码核心逻辑 |

| `UIContextSelf.ets` | UI上下文管理 |

| `WindowService.ets` | 窗口/全屏管理 |

| `XComponentService.ets` | 相机预览控制 |



\### 4.2 customScanV2/model/（6个，精简版）



| 服务 | 职责 |

|------|------|

| `ConfigStorage.ets` | 配置存储 |

| `OpenPhoto.ets` | 相册选择 |

| `ScanLayout.ets` | 布局计算 |

| `ScanService.ets` | 扫码逻辑 |

| `WindowService.ets` | 窗口管理 |

| `XComponentService.ets` | 相机控制 |



\## 5. UI 组件说明（view/）

| 组件 | 功能 |

|------|------|

| `CommonCodeLayout.ets` | 通用布局容器 |

| `IconPress.ets` | 可按压图标按钮 |

| `MaskLayer.ets` | 扫描框外遮罩 |

| `PickerDialog.ets` | 相册选择弹窗 |

| `ScanBottom.ets` | 底部操作栏 |

| `ScanLine.ets` | 扫描动画线 |

| `ScanLoading.ets` | 加载动画 |

| `ScanTitle.ets` | 顶部标题栏 |

| `ScanXComponent.ets` | 相机预览组件 |



\## 6. 功能模块关系图

┌─────────────────┐

│ Index.ets │

│ （首页） │

└────────┬────────┘

│

┌────────────────────┼────────────────────┐

│ │ │

▼ ▼ ▼

┌───────────────┐ ┌───────────────┐ ┌───────────────┐

│ DefaultScan │ │ CustomScan │ │ CustomScanV2 │

│ （默认扫码） │ │（完整自定义） │ │（精简自定义） │

└───────────────┘ └───────────────┘ └───────────────┘

│ │ │

└────────────────────┼────────────────────┘

│

┌────────────────────┼────────────────────┐

│ │ │

▼ ▼ ▼

┌───────────────┐ ┌───────────────┐ ┌───────────────┐

│DetectBarcode │ │GenerateBarcode│ │ ResultPage │

│ （条码检测） │ │ （条码生成） │ │ （结果页） │

└───────────────┘ └───────────────┘ └───────────────┘



\## 7. 依赖关系

```json

{

&#x20; "dependencies": {

&#x20;   "@hms/core-scan-kit": "^1.0.0",      // 华为扫码SDK

&#x20;   "@ohos/hypium": "1.0.6",             // 测试框架

&#x20;   "@ohos/hamock": "1.0.0"              // Mock框架

&#x20; }

}



8\. 路由配置（main\_pages.json）

\[

&#x20; "pages/Index",

&#x20; "pages/access/ScanAccess",

&#x20; "pages/access/ScanDetail",

&#x20; "pages/customScan/CustomPage",

&#x20; "pages/customScan/pages/ScanPage",

&#x20; "pages/customScanV2/pages/ScanPage",

&#x20; "pages/defaultScan/DefaultScan",

&#x20; "pages/detectBarcode/DecodeBarcode",

&#x20; "pages/generateBarcode/CreateBarcode",

&#x20; "pages/resultPage/ResultPage"

]



9\. 构建输出

产物	                      路径	                                                                     大小

unsigned.hap	entry/build/default/outputs/default/	  \~1.5 MB



10\. 技术栈总结

技术	                                                       用途

ArkTS	                                            开发语言

XComponent	                                 相机预览渲染

ScanKit	                                            扫码能力

Hvigor	                                            构建工具

@State/@Prop/@Link	           状态管理

router	                                             页面路由

@ohos.file.photoAccessHelper	相册访问

@ohos.vibrator	                                  震动反馈

@ohos.multimedia.audio	            音频播放

