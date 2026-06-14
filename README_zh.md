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
  <a href="#动效类别">动效类别</a> •
  <a href="https://joepui.github.io/motion-ref-skill/">在线预览</a> •
  <a href="README.md">English</a>
</p>

---

[Claude Code](https://docs.anthropic.com/en/docs/claude-code) 技能 — 用大白话描述你想要的动画效果，从 73 种动效中匹配最合适的，输出可直接使用的方案。

两种输出模式（自动判断）：
- **代码模式** — CSS/JS 动画参数，直接用于前端开发
- **视频模式** — 英文运动提示词，直接用于 Sora / Runway / 可灵等 AI 视频工具

## 安装

```bash
git clone https://github.com/joepUI/motion-ref-skill.git ~/.claude/skills/motion-ref-skill
```

安装后重启 Claude Code 即可使用。

## 使用

```
/motion-ref 按钮点击后弹一下
/motion-ref 数字从 0 跳到目标值
/motion-ref 输入错误时输入框抖一下
/motion-ref 图标像被一笔一笔画出来
/motion-ref 光沿着按钮边框跑一圈
/motion-ref 背景加一层流动的噪波纹理
/motion-ref 产品图从模糊变清晰出现
/motion-ref 点击后像水波纹一样扩散开
/motion-ref 页面切换用碎片飞散的效果
/motion-ref 做一个粒子上升的背景动画
```

也可以直接用自然语言描述，技能会自动激活。

## 动效类别

| 类别 | 数量 | 包含 |
|------|------|------|
| 移动系 | 5 | Move, SymMove, RepeatMove, WiggleMove, DelayMove |
| 旋转系 | 5 | Rotate, SymRotate, RepeatRotate, WiggleRotate, SolidRotation |
| 缩放系 | 5 | Scale, SymScale, RepeatScale, WiggleScale, Dot |
| 裁剪系 | 5 | TrimLine, TrimCircle, RepeatTrim, TrimPie, FlowingLine |
| 模糊·光效系 | 8 | Blur, Opacity, FieldOfDepth, MotionBlur, CrossBlur, RadialBlur, Glow, Flare |
| 偏移·轨道系 | 6 | Orbit, Offset, Vegas, Loop, Tiler, PolarCoordinates |
| 变形系 | 5 | ShapeTransform, RepeatTransform, LineWeight, Shade, Reshape |
| 时间操作系 | 4 | Easing, Rhythm, Integar, TimeDisplace |
| 扭曲系 | 3 | Bend, WaveWarp, Twirl |
| 扩散系 | 3 | Scatter, Median, Mosaic |
| 分形系 | 6 | FractalNoise, TurbulentDisplace, RoughEdge, NoiseAlpha, WigglePath, Lightning |
| 特殊效果 | 18 | Particle, Shatter, MaskWipe, CardDance, Wave, Grid, Text 等 |

## 在线预览

浏览全部 73 种动效的 GIF 预览：**https://joepui.github.io/motion-ref-skill/**

## License

MIT
