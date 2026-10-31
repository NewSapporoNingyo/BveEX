# BveEX 文档编写待办

状态核对日期：2026-10-31。

本清单依据 [AGENTS.md](AGENTS.md) 的文档规划、当前 `docs/` 正文和 `SamplePlugins/` 工程清单整理。`[x]` 表示对应主题已有正文；`[ ]` 表示待编写、待补齐或待验证。源码终审、示例编译与实机验证在第 4 节单独记录。

| 文档板块 | 规划篇数 | 已有正文 | 待编写 |
| --- | ---: | ---: | ---: |
| 用户手册 | 3 | 3 | 0 |
| 插件开发者文档 | 8 | 7 | 1 |
| 核心开发者文档 | 6 | 0 | 6 |
| 合计 | 17 | 10 | 7 |

## 1. 用户手册

### 1.1 安装与部署

文档：[docs/user-manual/installation.md](docs/user-manual/installation.md)。

- [x] 编写 BVE 版本、进程位数和运行环境要求。
- [x] 编写下载、文件部署、输入设备插件启用与安装结果检查步骤。
- [x] 说明安装目录、路径重定向、升级、多版本选择和旧版兼容模式。
- [x] 编写卸载步骤及安装期错误代码速查。

### 1.2 配置说明与插件加载

文档：[docs/user-manual/configuration.md](docs/user-manual/configuration.md)。

- [x] 汇总配置文件及入口、引导器配置的用途与加载时序。
- [x] 说明 `BveExPluginUsing` 清单的元素、属性、路径和 `Identifier` 规则。
- [x] 编写扩展、车辆插件、原生 ATS 插件及地图插件的部署与配置示例。
- [x] 编写 `BveExScriptPluginPackageManifest` 脚本包清单说明。
- [x] 说明诊断器目录、自动生成的状态文件及常见配置错误。

### 1.3 故障排除

文档：[docs/user-manual/troubleshooting.md](docs/user-manual/troubleshooting.md)。

- [x] 说明诊断信息的呈现位置、查看方法和故障排查流程。
- [x] 汇总启动、初始化、插件装载及车辆 ATS 兼容错误。
- [x] 说明版本信息与插件一览窗体、诊断器的使用方式。
- [x] 编写运行期故障定位、二分排除、常见问题及问题报告材料清单。

## 2. 插件开发者文档

### 2.1 插件开发快速入门

文档：[docs/plugin-development/getting-started.md](docs/plugin-development/getting-started.md)。

- [x] 说明插件类型、程序集与脚本载体、开发环境及 NuGet / 本地程序集引用配置。
- [x] 提供列车插件、地图插件的最小代码示例及插件元数据配置。
- [x] 编写编译、部署、清单挂载与加载结果检查步骤。
- [x] 编写断点调试、状态观察、错误输出及脚本插件入门内容。

### 2.2 插件生命周期与执行时机

文档：[docs/plugin-development/architecture-lifecycle.md](docs/plugin-development/architecture-lifecycle.md)。

- [x] 说明插件基类、核心入口属性、元数据及各类插件的生命周期跨度。
- [x] 绘制加载与初始化时序，列出各阶段的对象可用性。
- [x] 说明每帧 `Tick()` 调用链、执行顺序和 `elapsed` 计算方式。
- [x] 说明场景关闭、重载、`Dispose()` 调用及资源释放要求。
- [x] 编写跨插件通信、扩展获取方式与已知行为特性。

### 2.3 列车插件开发指南

文档：[docs/plugin-development/vehicle-plugins.md](docs/plugin-development/vehicle-plugins.md)。

- [x] 编写车辆清单、插件骨架与列车插件生命周期说明。
- [x] 说明 `INative`、车辆规格与状态、ATS 面板和音效数组、按键及运行事件。
- [x] 编写手柄干预、输入模拟及车辆位置、速度和物理参数操作示例。
- [x] 说明驾驶台面板对象及 `PanelController` 的使用范式。
- [x] 说明车门控制、`IConductorPatchFactory` 与自定义车掌逻辑。
- [x] 编写独立音频、右键菜单、控制窗体与跨插件通信示例。
- [x] 说明原生 ATS 混用、手柄串联及已知限制。

### 2.4 地图插件开发指南

文档：[docs/plugin-development/map-plugins.md](docs/plugin-development/map-plugins.md)。

- [x] 编写地图加载语句、插件清单、兼容头、插件骨架与生命周期说明。
- [x] 说明 `MapStatements` 内置语法、自定义语句、过滤与读取时机。
- [x] 编写闭塞分区、信号机及 `ISignalPatchFactory` 的使用示例。
- [x] 编写先行列车、他车控制、跨轨道切换与自定义渲染示例。
- [x] 说明车站、时刻表编辑及 `IDiagramUpdater` 界面同步。
- [x] 编写模型查找、动态贴图与自定义音效的使用示例。
- [x] 说明地图与列车插件协作及已知限制。

### 2.5 BveHacker 深入解析

文档：[docs/plugin-development/bve-hacker.md](docs/plugin-development/bve-hacker.md)。

- [x] 说明 `IBveHacker` 的获取方式、成员及窗体访问模型。
- [x] 说明 `ScenarioInfo`、`Scenario` 对象树与场景状态修改方式。
- [x] 说明场景生命周期事件的触发位置、订阅与退订规则。
- [x] 说明 `PreviewTick`、`PostTick` 与每帧执行时序。
- [x] 说明音频、辅助显示、输入、偏好设置及 `MapLoader` 访问方式。
- [x] 说明 `BveTypes` 包装器、底层反射、版本适配、已知缺陷及宿主行为验证边界。

### 2.6 AtsArrayExtender 专题

文档：[docs/plugin-development/extensions/ats-array-extender.md](docs/plugin-development/extensions/ats-array-extender.md)。

源码入口：`Extensions/BveEx.Extensions.AtsArrayExtender/`；示例入口：`SamplePlugins/VehiclePlugins/AtsPanelValueTest/`。

- [x] 创建专题文档，说明扩展的部署、加载及与 `INative` 的关系。
- [x] 逐项梳理数组扩容的目标、长度、补丁位置与生效时机。
- [x] 编写通过 `INative` 访问扩展后数组的完整插件示例。
- [x] 对照 `AtsPanelValueTest` 说明索引使用方式、数据流与边界行为。
- [x] 汇总资源与兼容限制，并补齐车辆指南和配置手册的交叉引用。

### 2.7 DXDynamicTexture 专题

文档：[docs/plugin-development/extensions/dynamic-texture.md](docs/plugin-development/extensions/dynamic-texture.md)。

源码入口：`Extensions/BveEx.Extensions.DXDynamicTexture/`；示例入口：`SamplePlugins/MapPlugins/DXDynamicTextureTest/`。

- [x] 创建专题文档，说明程序集依赖、扩展加载和命名空间。
- [x] 说明 `TextureManager` 的注册入口、模型与贴图匹配规则。
- [x] 说明 `TextureHandle` 的创建事件、贴图更新、刷新间隔与释放流程。
- [x] 说明 `GDIHelper` 绘图上下文及相关资源管理方式。
- [x] 说明 `TouchManager`、`TouchTextureHandle` 与鼠标交互事件。
- [x] 对照 `DXDynamicTextureTest` 提供完整绘制示例，补充渲染流程图及设备相关验证事项。

### 2.8 官方示例项目深度解析

目标文档：`docs/plugin-development/samples-walkthrough.md`。

当前 `SamplePlugins/` 包含 6 个列车示例工程、10 个地图示例工程。下列任务以该专题中的逐行解析为交付物。

- [ ] 建立全部 16 个示例的索引，列出工程路径、插件类型、依赖、入口类及部署方式。
- [ ] 逐行解析列车示例 `SimpleAts`。
- [ ] 逐行解析列车示例 `StateViewer`。
- [ ] 逐行解析列车示例 `PanelController`。
- [ ] 逐行解析列车示例 `AtsPanelValueTest`。
- [ ] 逐行解析列车示例 `ConductorPatchTest`。
- [ ] 逐行解析列车示例 `CooperatingWithMapPlugin`。
- [ ] 逐行解析地图示例 `SignalController`。
- [ ] 逐行解析地图示例 `PreTrainController`。
- [ ] 逐行解析地图示例 `TrainController`。
- [ ] 逐行解析地图示例 `TrainControllerEx.Automatic`。
- [ ] 逐行解析地图示例 `TrainControllerEx.Manual`。
- [ ] 逐行解析地图示例 `StationController`。
- [ ] 逐行解析地图示例 `MapStatementTest`。
- [ ] 逐行解析地图示例 `SoundFactoryTest`。
- [ ] 逐行解析地图示例 `DXDynamicTextureTest`。
- [ ] 逐行解析地图示例 `CooperatingWithVehiclePlugin`。
- [ ] 为各示例补充生命周期、关键 API、资源释放及对应指南的阅读链接。

## 3. 核心开发者文档

### 3.1 框架整体设计与分层架构

目标文档：`docs/core-development/architecture-overview.md`。

- [ ] 梳理 `BveEx.sln` 工程职责、引用关系和运行期依赖，绘制分层架构图。
- [ ] 说明入口、引导器、核心、`PluginHost` 与官方扩展之间的调用关系。
- [ ] 说明 `BveHacker`、`BveTypes`、`TypeWrapping` 及相关库的分工。
- [ ] 说明场景服务、扩展服务、诊断、启动画面和虚拟 ATS 的职责与生命周期。

### 3.2 启动链与 Hook 注入机制

目标文档：`docs/core-development/injection-mechanism.md`。

- [ ] 解析 `BveEx.Caller.InputDevice` 导出接口及 BVE 输入设备入口调用链。
- [ ] 解析 `BveEx.Launcher` 的核心定位、版本选择、程序集解析与旧版兼容分支。
- [ ] 跟踪核心初始化及 Harmony 补丁注册，绘制启动时序图与补丁位置表。
- [ ] 梳理场景加载、每帧回调和卸载阶段的补丁调用、异常路径与清理过程。

### 3.3 完整构建与打包指南

目标文档：`docs/core-development/build-guide.md`。

- [ ] 对照项目文件整理开发工具、目标框架、构建配置及平台目标。
- [ ] 核对 `LocalReferences`、各项目 `HintPath` 与 NuGet 依赖，给出本地程序集放置表。
- [ ] 解析 `DllExport.bat`、构建事件、输出目录及 `package.bat` 参数和产物布局。
- [ ] 说明旧版兼容组件等外部目录依赖，对照当前工程给出 `HowToBuild.md` 所述依赖的现行路径并记录可复现步骤。

### 3.4 插件宿主内部实现

目标文档：`docs/core-development/plugin-host-internals.md`。

- [ ] 解析 `PluginSourceSet` 的目录发现、XML 清单解析及路径解析规则。
- [ ] 解析程序集插件发现、构造、类型检查、元数据和标识符分配。
- [ ] 解析插件集合、扩展集合、原生 ATS 包、脚本包及加载错误汇总流程。
- [ ] 按实现说明程序集解析、共享状态、加载与隔离边界以及实例释放流程。

### 3.5 脚本引擎与运行时

目标文档：`docs/core-development/scripting-runtime.md`。

- [ ] 解析 `BveEx.Scripting` 与核心脚本插件适配层的职责及调用关系。
- [ ] 说明 C# / Roslyn 与 IronPython 2 的创建、编译、执行及结果获取流程。
- [ ] 对照脚本包清单与 `Globals` 说明引用、全局成员、生命周期和错误传播。
- [ ] 提供与当前运行时匹配的 C#、IronPython 2 完整脚本包示例及部署说明。

### 3.6 已知缺陷与架构限制

目标文档：`docs/core-development/known-issues.md`。

- [ ] 复核并汇总现有指南中的已知缺陷，为每项记录源码位置、触发条件、影响和规避方式。
- [ ] 对照 `PluginBase.Validate()`、`MapLoader.Stations`、`RandomFileList.SelectedFile` 等现有文档条目复查具体实现。
- [ ] 复核场景初始化订阅、`StructureSetLifeProlonger` 事件订阅及全局扩展跨场景事件绑定问题。
- [ ] 将源码可确定的限制与宿主实测事项分别标注，并建立各指南到缺陷条目的交叉引用。

## 4. 全局补充与验收

- [ ] 建立文档导航索引，串联用户、插件开发者、核心开发者三条阅读路径。
- [ ] 补齐当前 6 处指向待编写页面的本地链接，并在目标文档创建后复查链接和章节锚点。
- [ ] 将快速入门和生命周期文档中“14 个官方示例”的表述统一为当前 16 个工程，并同步示例索引。
- [ ] 建立公共 API 与文档的覆盖对照表，逐项核对 `BveEx.PluginHost`、`BveTypes` 和全部官方扩展。
- [ ] 补齐官方核心扩展的 API 索引，覆盖 `Native`、`MapStatements`、`SignalPatch`、`PreTrainPatch`、`TrainDrawPatch`、`ConductorPatch`、`SoundFactory`、`ContextMenuHacker`、`DiagramUpdater`、`StructureModelFinder`、`LoadErrorManager` 及 `IMatrixConverter`，关联已有讲解和待补主题。
- [ ] 逐篇复核类型、命名空间、成员签名、访问修饰符、事件时序及源码引用，统一源码链接格式。
- [ ] 将文档示例与官方工程逐项交叉对照，补齐完整示例的 `using`、引用和配置，并记录编译验证结果。
- [ ] 对照 XML Schema 与解析器核查全部配置示例、路径基准、默认值、优先级及错误分支。
- [ ] 检查 Mermaid 图的语法、渲染与源码时序一致性。
- [ ] 按 `AGENTS.md` 完成中文文案终审，清理否定式铺垫、免责套话、软化修饰和重复规则，统一代码符号与警告块格式。
- [ ] 在对应 BVE 5 / 6 环境验证安装、启用、插件加载、旧版兼容及动态贴图等操作，并记录宿主版本、位数和观察结果。
- [ ] 验证场景首次加载、重载、跳站、关闭与退出时的事件和资源释放行为，将宿主相关结果写回对应章节。
