<h1 align="center">motion-ref-skill</h1>

<p align="center">
  <strong>给你的产品加动效 — 不需要设计背景</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Agent-Skill-111111?style=flat-square" alt="Agent Skill">
  <img src="https://img.shields.io/badge/Claude%20Code-Supported-f59e0b?style=flat-square" alt="Claude Code">
  <img src="https://img.shields.io/badge/Codex-Supported-10a37f?style=flat-square" alt="Codex">
  <img src="https://img.shields.io/badge/OpenClaw-Supported-3b82f6?style=flat-square" alt="OpenClaw">
</p>

<p align="center">
  <a href="#安装">安装</a> •
  <a href="#使用">使用</a> •
  <a href="#动效分类">分类</a> •
  <a href="https://joepui.github.io/motion-ref-skill/">在线预览</a> •
  <a href="README.md">English</a>
</p>

---

AI agent 技能，帮你给产品加动效。119 种效果，13 个分类 — 描述产品场景就能推荐可落地的实现方案，不需要设计背景。

适配 Claude Code、Codex、OpenClaw 及任何支持 SKILL.md 的 agent。

## 安装

```bash
npx skills add https://github.com/joepUI/motion-ref-skill
```

或手动安装：

```bash
git clone https://github.com/joepUI/motion-ref-skill.git ~/.claude/skills/motion-ref-skill
```

安装后重启 agent 即可使用。

## 使用

描述你的产品场景，技能会推荐合适的动效并给出可直接使用的代码。

### 整体丰富产品动效

```
/motion-ref 我的网站感觉很静态，没有活力。
            帮我加一些动效让它看起来更专业。
```

技能会分析你的页面，推荐动效组合：内容区滚动渐现、卡片网格依次入场、按钮悬浮反馈、页面平滑转场等。

### 解决具体问题

```
/motion-ref 用户点了提交按钮后要等 3 秒，没有任何反馈，
            他们会反复点击。
```

```
/motion-ref 页面加载时先白屏再突然出现内容，
            看起来像坏了一样。
```

### 给功能加细节

```
/motion-ref 定价页有月付/年付的切换，
            切换时价格数字不要生硬跳变，要有过渡。
```

```
/motion-ref 落地页想要高级感，
            首屏加点什么效果。
```

### 获取推荐

```
/motion-ref SaaS 后台适合加哪些动效？
```

```
/motion-ref 我在做一个移动端聊天 App，
            有哪些动效可以考虑？
```

## 动效分类

| # | 分类 | 数量 | 代表效果 |
|---|------|------|---------|
| 1 | 加载与等待 | 14 | Spinner、骨架屏、波形跳动、玫瑰曲线、双纽线 |
| 2 | 按钮与点击反馈 | 9 | 按压缩小、涟漪、成功打勾、错误抖动、庆祝粒子 |
| 3 | 文字与数据 | 10 | 打字机、数字滚动、翻牌计数、光泽文字、渐变文字 |
| 4 | 弹层与浮层 | 10 | 弹窗、底部面板、Toast、Tooltip、抽屉、命令面板 |
| 5 | 导航与转场 | 7 | 页面推入、共享元素过渡、标签指示器、Dock 导航 |
| 6 | 表单与输入 | 10 | 聚焦环、浮动标签、开关、验证码输入、滑块、步骤指示器 |
| 7 | 滚动驱动 | 5 | 滚动揭示、阅读进度条、滚动文字揭示 |
| 8 | 图标与标识 | 10 | 汉堡菜单、SVG 描边、角标弹跳、爱心点赞、铃铛抖动、复制打勾 |
| 9 | 轮播与列表 | 8 | 轮播、卡片堆叠、拖拽排序、手风琴、头像堆叠、滑动操作 |
| 10 | 状态切换 | 7 | 主题切换、错误恢复、在线状态、收藏星标、已读未读 |
| 11 | 氛围与背景 | 8 | 渐变流动、粒子、磁性光标、3D 卡片悬浮、光线扫过、扫描线 |
| 12 | 数据可视化 | 12 | 柱状图升起、径向条形、散点图、密度曲线、饼图扇区、雷达图 |
| 13 | 入场与退场 | 8 | 淡入、上滑入场、弹性入场、序列入场、模糊入场、折叠展开 |

## 在线预览

浏览全部 119 种动效的在线演示：**https://joepui.github.io/motion-ref-skill/**

## License

MIT
