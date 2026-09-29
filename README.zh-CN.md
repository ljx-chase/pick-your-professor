<div align="center">

# Pick your professor

<p>
<a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License"/></a>
<img src="https://img.shields.io/badge/version-v1.0.0-blue?style=flat-square" alt="Version"/>
<a href="https://github.com/ljx-chase/pick-your-professor/stargazers"><img src="https://img.shields.io/github/stars/ljx-chase/pick-your-professor?style=flat-square&color=yellow" alt="Stars"/></a>
</p>

<strong>Language</strong>: <a href="README.md">English</a> | <a href="README.zh-CN.md">中文</a>

</div>

> **问 AI 自己研究方向上的问题，回答是对的，却读不下去。** 这个 skill 让你设定回答的写法密度：Feynman、Griffiths 或 Landau，并在整个会话中保持下去。

## 快速开始

把下面这段粘贴给你的 agent，无论用的是哪一个：

```text
Install the pick-your-professor skill from
https://github.com/ljx-chase/pick-your-professor, following the installation
section of the repo's AGENTS.md.
```

也可以手动安装：

- **Claude Code：** `npx skills add ljx-chase/pick-your-professor -g`，或把内层的 `pick-your-professor/` 文件夹复制到 `~/.claude/skills/`。
- **Claude 网页版、桌面版、Cowork、ChatGPT：** 从 [Releases](https://github.com/ljx-chase/pick-your-professor/releases) 下载 `pick-your-professor.zip`，作为 skill 上传。
- **Codex 及其他 agent：** 见 [AGENTS.md](AGENTS.md)。

然后说一句“Feynman 风格”，再提问。

## 为什么需要它

在自己领域的边缘问一个问题，回答往往是专家密度：一段话里十几个没解释的术语。你没办法只说“同样的答案，写成我能看懂的样子”，而不顺带要求从头学一遍这个领域。

**之前**，默认密度：

> 你的参数很可能不可辨识：Jacobian 接近秩亏，Fisher 信息矩阵病态，协方差沿退化方向发散。需要重新参数化，或补充能打破简并的数据。

**之后**，Feynman：

> 你的模型有两个旋钮，但数据只能看到它们的某种组合。比如曲线只依赖乘积 a·b：把 a 翻倍、b 减半，画出来的曲线一模一样，所以拟合可以沿着一整条取值线滑动，而与数据的吻合程度不变。拟合程序把这种滑动报告成每个旋钮各自巨大的不确定度，尽管乘积本身可能精确到百分之几。解决办法：把乘积当作一个参数来拟合，或者在两个旋钮对曲线影响不同的范围里补测数据。这里假设误差棒来自最优值附近拟合误差上升得有多陡，大多数拟合程序报告的正是这个。

内容相同，解决办法相同，前提相同。不同的只是默认你已经认识多少术语。

真正起控制作用的是**未解释术语预算**：允许多少个领域术语在出现的地方不加解释。“写简单点”只是愿望；术语预算是可以执行、也可以检查的规则。

## 三种写法

- **Feynman**：零个未解释术语。先给图像，类比要说明在哪里失效，公式放在后面。
- **Griffiths**：每个术语首次出现时定义，之后自由使用。教科书顺序：动机、定义、推导、算一个例子。
- **Landau**：紧凑，默认你熟悉这个领域。先给结论，推导只给梗概。

这是密度，不是深度。每种写法都保留前提、数量级和注意事项，改变的只是术语负担和顺序。也可以用普通说法：`先讲图像`、`教科书`、`紧凑`。

这不是入门工具。它改变的是回答怎么写，而不是按什么顺序教什么。如果你想被一步步带进一个还不熟悉的领域，请看 [research-field-onboarding](https://github.com/ljx-chase/research-field-onboarding)，它有自己的讲解方式，用来控制教学顺序。

## 什么时候触发，什么时候不触发

只有明确要求（“Feynman 风格”“先讲物理图像”“讲人话”）或明确抱怨（“太专业了”“看不懂”“术语太多”）才会触发。

话题难、回答写得密、你说自己是新手，都**不会**触发。它从不主动推荐自己。一个自作主张认为你看不懂的风格 skill，比没有更糟。

## 规则

- 只有明确的要求或抱怨才设定写法。
- 写法在整个会话中保持，换话题、问短问题都不失效，直到你改它。
- 写法从不删减内容；如果预算会逼它丢掉一个前提，就多写几句。
- 收到抱怨时，把同一个问题降一档重新回答，而不是把原答案写得更长。
- 从不询问你的背景，从不开启教学流程。
- 切换写法只用一句话确认，不重复解释。
- 代码、日志和报错原样引用。

## 更新记录

### v1.0.0

- 首个版本。三种写法由未解释术语预算定义，只由明确要求或抱怨设定，在会话中持续有效。
- 规则沿用了 [research-field-onboarding](https://github.com/ljx-chase/research-field-onboarding) 的经验：规则一律写成祈使句，因为条件式的规则在那边的测试中被跳过；明确写出“清晰不等于浅薄”，因为最常见的失败是一个读起来顺畅、却悄悄丢掉注意事项的回答。
- 附带评测集（`references/evals.md`）：三个负例、五个正例、一个多语言用例。

## 参与贡献

见 [CONTRIBUTING.md](CONTRIBUTING.md)。特别欢迎负例：skill 不该触发却触发了的情况。

## 反馈

这个 skill 刚发布，主要由作者本人在物理及相近领域测试。最有价值的贡献，是告诉我们它在其他领域哪里出了问题：漏掉没解释的术语、Feynman 写法里消失的注意事项、没人要求却被设定的写法。[提交 issue](https://github.com/ljx-chase/pick-your-professor/issues)。

## 引用

```bibtex
@misc{pick_your_professor_2026,
  title        = {Pick your professor: a cross-agent skill for setting the
                  density of research answers},
  author       = {Li, Junxiang and Zhou, Ziyan},
  year         = {2026},
  howpublished = {\url{https://github.com/ljx-chase/pick-your-professor}},
  note         = {GitHub repository}
}
```

## 许可

MIT License. Copyright (c) 2026 LI Junxiang and Ziyan Zhou (Anna).
