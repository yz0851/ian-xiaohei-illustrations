# KUNETIC Product Visual Prompts

> 读取 KUNETIC Product Lab 的指定产品目录，把已批准的产品事实、页面文案、Layout 和图片框架，转化为一套可直接交给外部生图工具使用的产品页视觉方案与完整提示词。
>
> 产品真实性 | B2B 工业视觉 | iPhone 6s 真实场景 | 工程可视化 | 只输出提示词

---

## 这个仓库是什么

这是从 [Ian Xiaohei Illustrations](https://github.com/helloianneo/ian-xiaohei-illustrations) Fork 并改造的 Codex Skill。

它保留原版最有价值的工作逻辑：

```text
读取内容 → 提炼视觉重点 → 选择构图 → 输出 Shot List → 输出单张方案 → QA
```

但任务域改为 KUNETIC 产品详情页：

```text
读取指定 Product Lab 产品目录
→ 理解事实、文案、Layout 和图片框架
→ 设计整套产品页视觉
→ 输出完整生图提示词
```

本 Skill 不生成图片，不修改 Product Lab，不上传媒体，也不发布产品。

第一版只支持产品页，Blog 配图后续再扩展。

---

## Product Lab 与本 Skill 的分工

Product Lab 决定：

- 需要多少张图；
- 放在哪个页面区块；
- 比例和尺寸；
- 每张图解决什么问题；
- 必须表达的事实；
- 禁止内容、文件名和 Alt。

本 Skill 决定：

- 使用哪种视觉模式；
- 产品角度和镜头；
- 构图、场景和光线；
- 标签、工程线条和信息层级；
- 如何避免整组图片重复；
- 每张图的完整提示词。

---

## 它会产出什么

默认输出：

- 资料完整性与硬约束摘要；
- 整体视觉策略；
- 与 Product Lab 完全对应的 Shot List；
- 每张图片的完整生图提示词；
- 可选优化建议；
- QA 检查结果。

默认不输出：

- 最终图片；
- 图片编辑；
- Payload Media；
- Product Lab 内容修改；
- 发布操作；
- Blog 配图。

---

## 视觉模式

- 产品商业摄影；
- 真实应用场景；
- 工程系统可视化；
- 功能概念表达；
- 部署与尺度；
- 多场景应用拼贴；
- 工厂与 OEM / ODM 能力。

凡涉及真实项目、安装、仓库、运输、应用或工厂场景，提示词统一以：

```text
一张由iphone6s随意拍摄的真实照片……
```

作为摄影风格基础。

图片新增文字统一为极简无衬线字体、现代工业风，可使用藏蓝、KUNETIC 品牌蓝、品牌红、深灰和白色克制搭配。

---

## 安装

克隆 Fork：

```bash
git clone https://github.com/yz0851/ian-xiaohei-illustrations.git
cd ian-xiaohei-illustrations
```

复制新 Skill 到 Codex skills 目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R ./kunetic-product-visual-prompts "${CODEX_HOME:-$HOME/.codex}/skills/"
```

---

## 怎么用

### 完整产品页提示词包

```text
Use $kunetic-product-visual-prompts

请读取：
yz0851/kunetic-product-lab
products/YYYY-M-D-{stable-product-id}/

根据已批准的事实、文案、Layout 和图片框架，
设计整套产品页配图并输出全部完整提示词。
不要生成图片。
```

### 只做配图规划

```text
Use $kunetic-product-visual-prompts
读取指定产品目录，先只输出整体视觉策略和 Shot List，
不要写完整提示词，不要生成图片。
```

更多示例见 [examples/prompts.md](examples/prompts.md)。

---

## 工作流程

1. 用户明确指定 Product Lab 产品目录；
2. 分层读取状态、图片框架、Layout、文案和事实边界；
3. 按具体图片任务读取相关产品参考；
4. 形成与 Product Lab 对应的 Shot List；
5. 为每张图选择一个主要视觉模式；
6. 输出完整可复制提示词；
7. 按 QA 检查产品真实性、技术边界和反重复；
8. 停止，不调用图像模型。

---

## 目录结构

```text
.
├── README.md
├── LICENSE
├── NOTICE.md
├── examples/
│   └── prompts.md
├── kunetic-product-visual-prompts/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── product-lab-input-contract.md
│       ├── style-dna.md
│       ├── product-fidelity.md
│       ├── composition-patterns.md
│       ├── prompt-template.md
│       └── qa-checklist.md
└── ian-xiaohei-illustrations/
    └── ... upstream skill retained for reference
```

真正安装的是：

```text
kunetic-product-visual-prompts/
```

原版 Skill 文件保留在 Fork 中作为上游参考，不进入新 Skill 的默认读取路径。

---

## 来源与许可

本项目基于 Ian 的 [Ian Xiaohei Illustrations](https://github.com/helloianneo/ian-xiaohei-illustrations) 改造，保留了原版的 Skill 组织方式与“先理解内容再设计视觉”的工作流骨架。

原项目使用 MIT License。详见 [LICENSE](LICENSE) 和 [NOTICE.md](NOTICE.md)。
