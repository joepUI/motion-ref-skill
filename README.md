<h1 align="center">motion-ref</h1>

<p align="center">
  <strong>Describe what you want. Get the right motion effect.</strong>
</p>

<p align="center">
  <a href="https://github.com/joepUI/motion-ref-skill/stargazers"><img src="https://img.shields.io/github/stars/joepUI/motion-ref-skill?style=flat&color=yellow" alt="Stars"></a>
  <a href="https://github.com/joepUI/motion-ref-skill/commits/main"><img src="https://img.shields.io/github/last-commit/joepUI/motion-ref-skill?style=flat" alt="Last Commit"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/joepUI/motion-ref-skill?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="#install">Install</a> •
  <a href="#usage">Usage</a> •
  <a href="#effect-categories">Categories</a> •
  <a href="https://joepui.github.io/motion-ref-skill/">Live Preview</a> •
  <a href="README_zh.md">中文文档</a>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that matches plain-language descriptions to motion effects. 73 effects across 12 categories — describe the feeling, get the technique.

Two output modes (auto-detected):
- **Code** — CSS / JS animation parameters for frontend development
- **Video** — English motion prompts for Sora / Runway / Kling

## Install

```bash
git clone https://github.com/joepUI/motion-ref-skill.git ~/.claude/skills/motion-ref
```

Restart Claude Code after installing.

## Usage

```
/motion-ref bounce effect on button click
/motion-ref number counting up from zero
/motion-ref input field shake on error
/motion-ref icon drawing itself line by line
/motion-ref light tracing along a button border
/motion-ref flowing noise texture for background
/motion-ref product image appearing from blur to sharp
/motion-ref ripple expanding outward on click
/motion-ref page transition with shattering fragments
/motion-ref particles rising in the background
```

Or describe what you want in natural language — the skill activates automatically.

## Effect Categories

| Category | Count | Includes |
|----------|-------|----------|
| Movement | 5 | Move, SymMove, RepeatMove, WiggleMove, DelayMove |
| Rotation | 5 | Rotate, SymRotate, RepeatRotate, WiggleRotate, SolidRotation |
| Scale | 5 | Scale, SymScale, RepeatScale, WiggleScale, Dot |
| Trim | 5 | TrimLine, TrimCircle, RepeatTrim, TrimPie, FlowingLine |
| Blur & Light | 8 | Blur, Opacity, FieldOfDepth, MotionBlur, CrossBlur, RadialBlur, Glow, Flare |
| Offset & Orbit | 6 | Orbit, Offset, Vegas, Loop, Tiler, PolarCoordinates |
| Transform | 5 | ShapeTransform, RepeatTransform, LineWeight, Shade, Reshape |
| Time | 4 | Easing, Rhythm, Integar, TimeDisplace |
| Distortion | 3 | Bend, WaveWarp, Twirl |
| Diffusion | 3 | Scatter, Median, Mosaic |
| Fractal | 6 | FractalNoise, TurbulentDisplace, RoughEdge, NoiseAlpha, WigglePath, Lightning |
| Special FX | 18 | Particle, Shatter, MaskWipe, CardDance, Wave, Grid, Text, and more |

## Live Preview

Browse all 73 effects with GIF previews: **https://joepui.github.io/motion-ref-skill/**

## License

MIT
