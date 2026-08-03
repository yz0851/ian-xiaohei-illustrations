# Product Lab 输入与交接合同

## 核心边界

Product Lab 负责“需要几张、放哪里、解决什么问题、使用什么比例、哪些文案和事实不能错”。

本 Skill 负责“如何用合适的视觉模式、构图、场景和提示词把它表达好”。

## 分层读取

不要一次读取整个仓库或全部原始资料。

### 第一层：页面和图片框架

优先读取：

```text
workflow-state.json
content/image-production-plan.md
content/layout-design-brief.md
content/page-copy.md
```

先确认产品身份、图片槽位、目标比例、基本职责、页面主叙事和批准文案。

### 第二层：事实边界

再读取：

```text
facts/verified-facts.md
content/public-display-convention.md
facts/conflicts-and-decisions.md
facts/pending-items.md
```

确认可公开参数、禁止宣传、冲突决定和阻塞项。

### 第三层：按单张图片读取来源

只在设计具体图片时读取相关内容：

```text
sources/source-manifest.json
sources/image-observations.md
相关产品照片
相关 PDF 页面
相关 CAD / 3D 图
工厂或应用参考
publish/product-media-manifest.json
```

例如，设计液冷图只读取液冷事实；设计产品主图只检查真实产品图是否可见，不用文字重新描述整台产品。

## 用户图片要求与页面槽位匹配

用户没有直接指定页面槽位时，先按语义匹配 Product Lab 中最合适的现有槽位。

| 用户表达 | 默认匹配槽位 |
|---|---|
| 产品主图 | Hero Product Identity |
| 参数图 | Hero Core Specifications |
| 场景图 / 应用图 | Applications Poster |
| Hero场景图 | Hero Applications |
| 拓扑图 / 系统图 | Overview System Diagram |
| Hero拓扑图 | Hero Topology |
| 工厂图 / OEM图 | Project Configuration / OEM Poster |
| 液冷图 / 户外图 | Outdoor and Thermal Operation |
| PCS架构图 | Cluster-Level Power Conversion |

如果当前产品没有完全对应的槽位，选择职责最接近的槽位并说明原因；不得为了方便全部映射为 Hero。

输出提示词前，必须列出：

```text
用户要求：
匹配槽位：
目标比例 / 尺寸：
比例来源：
对应批准文案：
```

## 比例和尺寸优先级

### 设计新图片

1. 用户当前明确指定；
2. 已批准 `content/image-production-plan.md` 中该槽位的目标比例；
3. 已批准 `content/layout-design-brief.md` 中该区块的页面比例；
4. 页面组件默认比例；
5. `publish/product-media-manifest.json` 中历史媒体实际尺寸。

### 替换或局部修改现有图片

1. 用户当前明确指定；
2. 现有媒体实际尺寸；
3. 图片计划中的目标比例；
4. Layout比例。

### 比例冲突

当目标设计比例与历史媒体实际尺寸不同，必须显式输出：

```text
设计目标比例：
历史媒体比例：
本次任务类型：新设计 / 替换现有图
最终采用：
```

不得静默选择，也不得因为用户一次要求多张图而把所有图片统一为同一比例。

## 图片文案读取合同

每张图匹配槽位后，按以下顺序提取图片文字：

1. `image-production-plan.md` 中该图片的 `Image text`；
2. `page-copy.md` 对应区块的批准标题；
3. 对应 Eyebrow、Subtitle 或 Intro；
4. 批准的设备 Label、参数和短语；
5. 从批准文案中压缩出的短 Label。

不得自行发明新的营销主张。

只有以下情况才默认无新增文字：

- 图片计划明确写 `Image text: None`；
- 用户明确要求无文字；
- 页面职责明确要求纯产品展示。

场景图通常应有一个主标题或场景 Label；拓扑图通常应有一个简短系统标题和设备节点 Label；工厂图通常应有一个能力标题或短副标题。最终仍以 Product Lab 批准文案为准。

## 产品参考图可用性

### A. 当前对话中有可见真实产品图

直接使用：

```text
参考图1中的真实产品……
提取图1产品……
为图1中的真实产品创建……
```

不需要逐项描述产品部件。

### B. 仓库中有可直接读取的真实产品图

先读取实际图片并编号，再在提示词中引用。

### C. 仓库只有文件名、Manifest、本地路径或上传记录

不得假装已经看到了真实图片。必须说明：

```text
当前仓库只记录了图片文件信息，未提供可直接读取的产品图像。
使用下面提示词时，请将已确认的真实产品图片上传为参考图1。
```

不得用门板、把手、铰链、散热口、接口等长篇文字代替缺失的产品图。

## 产品外观最小约束

默认只写一条简洁约束：

```text
参考图1中的真实产品制作，保持图1产品外观、比例和质感不变，不重新设计产品。
```

只有以下条件同时满足时，才增加具体结构描述：

- 结构在参考图中清楚可见；
- 对当前图片职责重要，或模型此前在此处生成错误；
- 描述不会诱导模型补画不存在的部件。

如果参考图没有展示侧面、背面或内部，应选择参考图支持的视角，不得猜测或用竞品图补全。

## 信息优先级

发生冲突时：

1. 用户当前对话中的最新明确决定；
2. `verified-facts.md`；
3. `public-display-convention.md`；
4. 已批准页面文案；
5. 已批准 Layout；
6. 已批准图片计划；
7. `conflicts-and-decisions.md`；
8. 用户批准的真实产品参考；
9. 原始资料；
10. 网上参考。

低优先级内容不得覆盖高优先级决定。

## 固定字段

不得自行修改：

- 图片数量；
- 页面位置和 Block ID；
- 目标比例与尺寸；
- 基本职责；
- 已批准参数和文字；
- 必须保留与禁止项；
- 文件名、Alt 和派生来源；
- Technical Specifications 的媒体决定；
- Hero数量和比例，以当前 Product Lab 批准计划为准；
- OG与Datasheet缩略图的派生关系。

## 可设计字段

可以自主设计：

- 视觉模式；
- 构图与镜头；
- 产品位置；
- 场景与背景；
- 光线；
- 标签和工程线条；
- 信息层级；
- 反重复策略；
- 完整提示词。

## 行业与设计参考

产品主图、场景图、拓扑图、工厂图、功能图和新构图方向默认必须研究相关行业与设计案例。

可以不搜索的情况：

- 用户要求严格复刻现有图；
- 用户已经提供明确设计参考；
- 仅修改少量文字、尺寸或检查提示词。

搜索只参考：

- 构图和留白；
- 产品与画面的比例；
- 标题与参数层级；
- 场景视角和摄影距离；
- 拓扑节点和箭头组织；
- 字体、色彩和整体商业感。

不得用网上参考证明或补充 KUNETIC 的外观、结构、参数、认证、客户、工厂规模、产能或真实项目。

输出时简要列出 2–4 个参考方向及其借鉴点。如果搜索工具不可用，必须明确说明。

## 保存边界

默认只在对话中输出。用户明确要求时，可以写入：

```text
content/visual-prompt-pack.md
```

不得覆盖 `image-production-plan.md`，不得推进 workflow 状态，不得上传媒体或发布产品。
