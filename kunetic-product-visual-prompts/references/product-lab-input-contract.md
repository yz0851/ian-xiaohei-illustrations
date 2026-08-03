# Product Lab 输入与交接合同

## 核心边界

Product Lab 负责“需要几张、放哪里、解决什么问题、哪些事实不能错”。

本 Skill 负责“用什么视觉模式、构图和场景把它表达好”。

## 分层读取

不要一次读取整个仓库或全部原始资料。

### 第一层：先确认页面和图片框架

优先读取：

```text
workflow-state.json
content/image-production-plan.md
content/layout-design-brief.md
content/page-copy.md
```

先确认产品身份、图片总数、槽位、比例、基本职责和页面主叙事。

### 第二层：确认事实边界

再读取：

```text
facts/verified-facts.md
content/public-display-convention.md
facts/conflicts-and-decisions.md
facts/pending-items.md
```

确认可公开参数、禁止宣传、冲突决定和阻塞项。

### 第三层：按图片任务读取来源

只在设计具体图片时读取相关内容：

```text
sources/source-manifest.json
sources/image-observations.md
相关产品照片
相关 PDF 页面
相关 CAD / 3D 图
工厂或应用参考
```

例如，设计液冷图只读取液冷事实；设计正面主图只读取正面、侧面和 Logo 参考。

## 信息优先级

发生冲突时：

1. 用户当前对话中的最新明确决定；
2. `verified-facts.md`；
3. `public-display-convention.md`；
4. 已批准的页面文案；
5. 已批准的 Layout；
6. Product Lab 图片框架；
7. `conflicts-and-decisions.md`；
8. 用户批准的真实产品参考；
9. 原始资料；
10. 网上参考。

低优先级内容不得覆盖高优先级决定。

## 固定字段

不得自行修改：

- 图片数量；
- 页面位置和 Block ID；
- 比例与尺寸；
- 基本职责；
- 已批准参数和文字；
- 必须保留与禁止项；
- 文件名、Alt 和派生来源；
- Technical Specifications 无图；
- Hero 固定 6 张 1:1；
- OG 与 Datasheet 缩略图从批准 Hero 裁切。

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

## 网上参考

允许研究同行产品页、工业摄影、能源系统图、工厂视觉和设计案例。

只能参考构图、镜头、场景、光线、信息层级和表达方法；不得用于证明 KUNETIC 的结构、参数、认证、客户、工厂规模、产能或真实项目。

## 保存边界

默认只在对话中输出。用户明确要求时，可以写入：

```text
content/visual-prompt-pack.md
```

不得覆盖 `image-production-plan.md`，不得推进 workflow 状态，不得上传媒体或发布产品。
