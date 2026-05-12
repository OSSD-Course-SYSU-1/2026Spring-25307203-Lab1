\# ScanKit 扫码示例应用 - 新增功能说明文档

> 基于基础工程 v1.0.0 扩展的新功能



\---



功能一：扫描历史记录

1.1 功能概述

自动保存用户扫描过的所有条码，支持历史记录查看、搜索、删除。即使离线也能查看之前的扫描结果。



1.2 用户场景

\- 用户需要回顾之前扫描过的商品信息

\- 需要多次查看同一个二维码内容

\- 离线环境下查看已保存的扫描记录



1.3 实现方案

新增文件

| 文件 | 路径 | 说明 |

|------|------|------|

| `HistoryService.ets` | `pages/history/model/` | 历史记录数据服务 |

| `HistoryPage.ets` | `pages/history/` | 历史记录列表页 |

| `HistoryItem.ets` | `pages/history/view/` | 历史记录项组件 |



数据结构

```typescript

interface ScanHistory {

&#x20; id: string;           // 唯一标识

&#x20; content: string;      // 扫描内容

&#x20; type: string;         // 条码类型（QR\_CODE/EAN13等）

&#x20; timestamp: number;    // 扫描时间戳

&#x20; imagePath?: string;   // 截图路径（可选）

}



数据存储

\-使用 @ohos.data.preferences 持久化存储

\-最多保存 200 条记录

\-支持按时间倒序排列



1.4 UI 设计

┌─────────────────────────────────────┐

│  ← 历史记录             清空  搜索   │

├─────────────────────────────────────┤

│  📱 2024-01-15 14:30                │

│  https://example.com/product/12345  │

│  \[二维码]                     ⋮     │

├─────────────────────────────────────┤

│  📦 2024-01-15 10:15                │

│  6901234567890                      │

│  \[EAN-13]                     ⋮     │

├─────────────────────────────────────┤

│  ...                                │

└─────────────────────────────────────┘



1.5 交互说明

操作	               响应

点击记录	    跳转结果页，重新展示内容

长按记录	    弹出删除/分享菜单

点击清空	    二次确认后清空所有记录

搜索框输入	    实时过滤匹配内容



1.6 代码集成点

修改 ResultPage.ets，在展示结果时调用 HistoryService.saveRecord()：

// 扫描成功后自动保存

onScanResult(result: ScanResult) {

&#x20; this.resultText = result.originalValue;

&#x20; this.resultType = result.scanType;

&#x20; // 新增：保存到历史记录

&#x20; HistoryService.saveRecord({

&#x20;   content: result.originalValue,

&#x20;   type: result.scanType,

&#x20;   timestamp: Date.now()

&#x20; });

}



功能二：批量生成条码

2.1 功能概述

支持一次性输入多行文本，批量生成对应的条码图片，适合需要批量生成二维码/条形码的场景（如：活动门票、商品标签等）。



2.2 用户场景

\-活动主办方需要生成多个参会者二维码

\-商家需要批量生成商品条码标签

\-考试/证件需要批量生成身份二维码



2.3 实现方案

新增文件

文件	                                             路径	                                             说明

BatchGeneratePage.ets	pages/generateBarcode/	批量生成页面

BatchResultPage.ets	           pages/generateBarcode/	批量结果展示页



核心功能

\-支持文本列表导入（手动输入或从文件导入）

\-支持预览生成的条码列表

\-支持批量保存到相册

\-支持打包导出为 ZIP 文件



输入方式

方式	              说明

文本域输入	   每行一个内容，最多100行

文件导入	   支持 .txt 或 .csv 文件

剪贴板导入   从剪贴板粘贴批量数据



2.4 UI 设计

┌─────────────────────────────────────┐

│  ← 批量生成条码                      │

├─────────────────────────────────────┤

│  \[文本输入模式]  \[文件导入模式]       │

├─────────────────────────────────────┤

│  ┌─────────────────────────────┐    │

│  │ product\_001                  │    │

│  │ product\_002                  │    │

│  │ product\_003                  │    │

│  │ ...                          │    │

│  └─────────────────────────────┘    │

│          （最多100行）               │

├─────────────────────────────────────┤

│  条码类型：\[二维码 ▼]               │

│  尺寸：\[中 ▼]                       │

├─────────────────────────────────────┤

│  \[预览]          \[生成并保存]       │

└─────────────────────────────────────┘



2.5 性能优化

\-使用 Worker 线程处理批量生成任务

\-进度条显示生成进度

\-支持中断取消



功能三：分享扫描结果

3.1 功能概述

扫描结果支持多种方式的分享，包括文本、链接、图片（条码截图）等，便于用户将结果发送给他人或保存到其他应用。



3.2 用户场景

\-扫描到网址后直接分享给好友

\-扫描到联系方式后保存到通讯录

\-扫描到 Wi-Fi 密码后分享给他人



3.3 实现方案

新增文件

文件	                                  路径	               说明

ShareService.ets	common/	    分享服务封装



支持的分享类型

结果类型	   分享方式	           示例

URL	              系统分享	           分享链接到微信/浏览器

纯文本	   系统分享	           复制/发送文本

联系方式	   保存到联系人	一键添加联系人

Wi-Fi 配置	   生成配置码	分享 Wi-Fi 密码二维码

条码截图	   图片分享	           分享或保存截图



3.4 UI 设计

在 ResultPage.ets 底部增加分享按钮：

┌─────────────────────────────────────┐

│  📷 扫描结果                         │

├─────────────────────────────────────┤

│  类型：QR Code                       │

│  内容：https://example.com/page/123  │

├─────────────────────────────────────┤

│  \[复制]  \[分享]  \[保存到相册]  \[更多] │

└─────────────────────────────────────┘



点击\[分享]后弹出分享面板：

┌─────────────────────────────────────┐

│  分享到                              │

├─────────────────────────────────────┤

│  📱 微信    💬 QQ    🔗 复制链接     │

│  📧 邮件    📝 备忘录  🌐 浏览器打开  │

└─────────────────────────────────────┘



3.5 代码实现示例

// ShareService.ets

import share from '@ohos.share';



export class ShareService {

&#x20; // 分享文本

&#x20; static shareText(text: string) {

&#x20;   share.share({

&#x20;     dataType: share.ShareDataType.TEXT,

&#x20;     data: text

&#x20;   });

&#x20; }

&#x20; 

&#x20; // 分享链接

&#x20; static shareUrl(url: string) {

&#x20;   share.share({

&#x20;     dataType: share.ShareDataType.TEXT,

&#x20;     data: url,

&#x20;     title: '分享链接'

&#x20;   });

&#x20; }

&#x20; 

&#x20; // 分享图片

&#x20; static async shareImage(pixelMap: image.PixelMap) {

&#x20;   const uri = await this.saveToTemp(pixelMap);

&#x20;   share.share({

&#x20;     dataType: share.ShareDataType.URI,

&#x20;     data: uri

&#x20;   });

&#x20; }

}



功能四：暗黑模式适配

4.1 功能概述

为应用添加暗黑主题支持，跟随系统深色模式自动切换，也可以手动设置。提升夜间使用时视觉舒适度。



4.2 用户场景

\-夜间使用手机时，深色界面更护眼

\-用户偏好使用深色主题

\-节省 OLED 屏幕电量



4.3 实现方案

资源文件配置

在 resources/ 下添加暗黑模式资源：

resources/

├── base/                    # 默认（浅色）

│   └── element/color.json   # 浅色颜色定义

├── dark/                    # 暗黑模式（新增）

│   ├── element/color.json   # 暗黑颜色定义

│   └── media/               # 暗黑模式图标（可选）

├── zh\_CN/

└── en\_US/



颜色定义对比

用途	           浅色模式	暗黑模式

背景色	#FFFFFF	#1A1A1A

卡片背景	#F5F5F5	#2C2C2C

主要文字	#000000	#FFFFFF

次要文字	#666666	#999999

分割线	#EEEEEE	#3A3A3A

主题色	#0A59F7	#0A59F7（保持）



UI 组件适配

所有页面组件使用资源颜色而非硬编码：

// 正确方式

.backgroundColor($r('app.color.background'))



// 错误方式（需修改）

.backgroundColor('#FFFFFF')



4.4 配置方式

// 设置页面增加主题切换选项

@State themeMode: 'auto' | 'light' | 'dark' = 'auto';



// 监听系统暗黑模式变化

let colorMode = this.getUIContext().getHostContext().config.colorMode;



功能五：扫描记录导出 Excel

5.1 功能概述

将扫描历史记录批量导出为 Excel 文件，方便用户进行数据分析、备份或上报。



5.2 用户场景

\-库存盘点时导出扫码记录

\-统计分析扫描数据

\-数据备份和迁移

\-上报扫码结果给管理系统



5.3 实现方案

新增文件

文件	                                  路径	                         说明

ExportService.ets	common/	Excel   导出服务

ExportPage.ets	           pages/history/	   导出配置页



导出格式

Excel 文件包含以下列：

列名	           说明	                      示例

序号	           自动编号	           1

扫描内容	条码原始内容	https://example.com

条码类型	类型名称	           QR\_CODE

扫描时间	完整时间戳 	2024-01-15 14:30:25

扫描来源	扫码/相册	           相机扫描



依赖库

{

&#x20; "dependencies": {

&#x20;   "@ohos/xlsx": "^1.0.0"  // Excel 生成库

&#x20; }

}



5.4 UI 设计

在历史记录页面增加导出入口：

┌─────────────────────────────────────┐

│  ← 历史记录             导出   ⋮    │

├─────────────────────────────────────┤

│  导出设置                            │

│  ┌─────────────────────────────┐    │

│  │ 📅 时间范围：\[最近7天 ▼]     │    │

│  │ 📁 导出格式：\[Excel ▼]       │    │

│  │ 📂 保存位置：\[下载目录 ▼]     │    │

│  └─────────────────────────────┘    │

│                                      │

│  \[导出当前]    \[导出全部]    \[取消]  │

└─────────────────────────────────────┘



5.5 导出流程

用户点击导出

&#x20;   │

&#x20;   ▼

选择导出范围（全部/选中/时间范围）

&#x20;   │

&#x20;   ▼

读取历史记录数据

&#x20;   │

&#x20;   ▼

生成 Excel 文件（Worker 线程）

&#x20;   │

&#x20;   ▼

显示进度条

&#x20;   │

&#x20;   ▼

保存到文件管理器

&#x20;   │

&#x20;   ▼

提示导出成功，可选择分享



5.6 Excel 生成示例

// ExportService.ets

import xlsx from '@ohos/xlsx';



export class ExportService {

&#x20; static async exportToExcel(records: ScanHistory\[]): Promise<string> {

&#x20;   // 构建工作表数据

&#x20;   const data = \[

&#x20;     \['序号', '扫描内容', '条码类型', '扫描时间', '扫描来源'],

&#x20;     ...records.map((item, index) => \[

&#x20;       index + 1,

&#x20;       item.content,

&#x20;       item.type,

&#x20;       new Date(item.timestamp).toLocaleString(),

&#x20;       item.source || '相机扫描'

&#x20;     ])

&#x20;   ];

&#x20;   

&#x20;   // 创建工作簿和工作表

&#x20;   const wb = xlsx.utils.book\_new();

&#x20;   const ws = xlsx.utils.aoa\_to\_sheet(data);

&#x20;   xlsx.utils.book\_append\_sheet(wb, ws, '扫描记录');

&#x20;   

&#x20;   // 写入文件

&#x20;   const fileName = `scan\_records\_${Date.now()}.xlsx`;

&#x20;   const filePath = `${appContext.filesDir}/${fileName}`;

&#x20;   xlsx.writeFile(wb, filePath);

&#x20;   

&#x20;   return filePath;

&#x20; }

}

