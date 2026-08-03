# Prompt Examples

下面的指令可以直接复制到 Codex 中使用。

## 完整产品页提示词包

```text
Use $kunetic-product-visual-prompts

请读取：
yz0851/kunetic-product-lab
products/YYYY-M-D-{stable-product-id}/

根据已批准的事实、文案、Layout 和图片框架，
设计整套产品页配图并输出全部完整提示词。
不要生成图片，不要修改 Product Lab。
```

## 只输出 Shot List

```text
Use $kunetic-product-visual-prompts
读取指定产品目录，先只输出：
- Product Lab 硬约束摘要
- 整体视觉策略
- Shot List

暂时不要写完整提示词，不要生成图片。
```

## 重新设计某一张 Hero

```text
Use $kunetic-product-visual-prompts
读取指定产品目录和现有图片框架。
只重新设计 Hero 04 的视觉方案与完整提示词，
保持页面位置、比例、基本职责、事实和文件名不变。
```

## 真实应用场景图

```text
Use $kunetic-product-visual-prompts
读取指定产品目录，为 Applications 区块设计一张真实应用场景图。
场景摄影语言必须以“一张由iphone6s随意拍摄的真实照片……”开头，
但具体构图、人物、产品视角和环境由你根据页面内容设计。
只输出提示词。
```

## 系统架构图

```text
Use $kunetic-product-visual-prompts
读取指定产品目录，为系统集成区块设计一张工程可视化图。
严格核对 PV、Grid、Load、Generator、EV 和产品之间的真实连接关系，
区分标准配置、外部设备和 Optional，不得自行增加功能。
```

## 工厂与 OEM / ODM 图

```text
Use $kunetic-product-visual-prompts
读取指定产品目录，为 OEM / ODM 区块设计一张工厂能力图。
使用“一张由iphone6s随意拍摄的真实照片……”的普通手机现场风格，
配合已批准页面文案，不虚构工厂面积、产能、机器人产线或认证实验室。
```

## 检查现有提示词

```text
Use $kunetic-product-visual-prompts
读取指定产品目录，并检查下面这组产品图提示词是否：
- 符合 Product Lab 图片数量和职责
- 保持真实产品结构
- 没有参数或内部结构幻觉
- 构图不重复
- 字体与品牌色统一
- 真实场景符合 iPhone 6s 普通手机现场感

只输出问题、修改建议和修订后的提示词，不生成图片。
```
