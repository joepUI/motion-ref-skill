<h1 align="center">motion-ref</h1>

<p align="center">
  <strong>描述你想要的效果，AI 帮你匹配动效方案</strong>
</p>

<p align="center">
  <a href="https://github.com/joepUI/motion-ref-skill/stargazers"><img src="https://img.shields.io/github/stars/joepUI/motion-ref-skill?style=flat&color=yellow" alt="Stars"></a>
  <a href="https://github.com/joepUI/motion-ref-skill/commits/main"><img src="https://img.shields.io/github/last-commit/joepUI/motion-ref-skill?style=flat" alt="Last Commit"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/joepUI/motion-ref-skill?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="#安装">安装</a> •
  <a href="#使用">使用</a> •
  <a href="#动效分类">分类</a> •
  <a href="https://joepui.github.io/motion-ref-skill/">在线预览</a> •
  <a href="README.md">English</a>
</p>

---

[Claude Code](https://docs.anthropic.com/en/docs/claude-code) 技能 — 现代 UI 动效参考库。109 种可直接使用的动画效果，13 个分类。用自然语言描述交互场景，匹配最合适的动效，输出 CSS/JS 代码。

## 安装

```bash
git clone https://github.com/joepUI/motion-ref-skill.git ~/.claude/skills/motion-ref-skill
```

安装后重启 Claude Code 即可使用。

## 使用

用自然语言描述一个交互场景。技能会从参考库中匹配最合适的动效，输出完整的、可直接使用的代码。

```
/motion-ref 我有一个数据面板页面，上面有几个统计卡片。
            希望它们逐个出现，而不是一下子全冒出来。
```

```
/motion-ref 用户提交表单后需要等 2-3 秒才有响应。
            提交按钮需要显示一个加载状态。
```

```
/motion-ref 我在做一个设置面板，是从右边滑出的抽屉。
            需要滑入动画和遮罩层。
```

```
/motion-ref 移动端的消息列表，
            我想做左滑删除的效果，类似 iOS 邮件那种。
```

```
/motion-ref 定价页有月付/年付的切换。
            切换时价格数字要有动画过渡，不要生硬地跳变。
```

```
/motion-ref 落地页的标题大字需要一种高级感。
            想加一个光泽扫过的效果。
```

```
/motion-ref 我在做一个多步骤结账流程。
            需要一个步骤指示器，能显示当前在第几步，
            切换步骤时有动画。
```

## 动效分类

| # | 分类 | 数量 | 代表效果 |
|---|------|------|---------|
| 1 | 加载与等待 | 12 | Spinner、骨架屏、波形跳动、输入提示、沙漏、Lissajous 曲线 |
| 2 | 按钮与点击反馈 | 9 | 按压缩小、涟漪、成功打勾、错误抖动、庆祝粒子 |
| 3 | 文字与数据 | 10 | 打字机、数字滚动、翻牌计数、光泽文字、渐变文字 |
| 4 | 弹层与浮层 | 10 | 弹窗、底部面板、Toast、Tooltip、抽屉、命令面板 |
| 5 | 导航与转场 | 7 | 页面推入、共享元素过渡、标签指示器、Dock 导航 |
| 6 | 表单与输入 | 10 | 聚焦环、浮动标签、开关、验证码输入、滑块、步骤指示器 |
| 7 | 滚动驱动 | 5 | 滚动揭示、阅读进度条、滚动文字揭示 |
| 8 | 图标与标识 | 10 | 汉堡菜单、SVG 描边、角标弹跳、爱心点赞、铃铛抖动、复制打勾 |
| 9 | 轮播与列表 | 8 | 轮播、卡片堆叠、拖拽排序、手风琴、头像堆叠、滑动操作 |
| 10 | 状态切换 | 8 | 主题切换、空状态、在线状态、收藏星标、已读未读 |
| 11 | 氛围与背景 | 7 | 渐变流动、粒子、磁性光标、3D 卡片悬浮、光线扫过 |
| 12 | 数据可视化 | 5 | 柱状图升起、环形图、仪表盘、折线描绘、统计卡片 |
| 13 | 入场与退场 | 8 | 淡入、上滑入场、弹性入场、序列入场、模糊入场、折叠展开 |

## 在线预览

浏览全部 109 种动效的在线演示：**https://joepui.github.io/motion-ref-skill/**

## License

MIT
