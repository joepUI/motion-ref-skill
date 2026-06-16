<h1 align="center">motion-ref-skill</h1>

<p align="center">
  <strong>Add motion to your product — no design background needed.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Agent-Skill-111111?style=flat-square" alt="Agent Skill">
  <img src="https://img.shields.io/badge/Claude%20Code-Supported-f59e0b?style=flat-square" alt="Claude Code">
  <img src="https://img.shields.io/badge/Codex-Supported-10a37f?style=flat-square" alt="Codex">
  <img src="https://img.shields.io/badge/OpenClaw-Supported-3b82f6?style=flat-square" alt="OpenClaw">
</p>

<p align="center">
  <a href="https://github.com/joepUI/motion-ref-skill/stargazers"><img src="https://img.shields.io/github/stars/joepUI/motion-ref-skill?style=flat-square&color=yellow" alt="Stars"></a>
  <a href="https://github.com/joepUI/motion-ref-skill/commits/main"><img src="https://img.shields.io/github/last-commit/joepUI/motion-ref-skill?style=flat-square" alt="Last Commit"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/joepUI/motion-ref-skill?style=flat-square" alt="License"></a>
</p>

<p align="center">
  <a href="#install">Install</a> •
  <a href="#usage">Usage</a> •
  <a href="#categories">Categories</a> •
  <a href="https://joepui.github.io/motion-ref-skill/">Live Preview</a> •
  <a href="README_zh.md">中文文档</a>
</p>

---

AI agent skill for UI motion design. 111 production-ready effects across 13 categories — describe your product scenario, get implementation guidance you can ship. No motion design knowledge required.

Works with Claude Code, Codex, OpenClaw, and any SKILL.md-compatible agent.

## Install

```bash
npx skills add https://github.com/joepUI/motion-ref-skill
```

Or install manually:

```bash
git clone https://github.com/joepUI/motion-ref-skill.git ~/.claude/skills/motion-ref-skill
```

Restart your agent after installing.

## Usage

Describe your product scenario. The skill recommends the right animation and gives you production-ready code.

### Enrich your whole site

```
/motion-ref My website feels static and lifeless.
            Help me add animations to make it feel polished.
```

The skill will analyze your pages and suggest a combination of effects: scroll reveals for content sections, stagger animations for card grids, hover feedback for buttons, smooth page transitions, etc.

### Fix a specific problem

```
/motion-ref Users click the submit button and nothing happens for 3 seconds.
            They keep clicking because there's no feedback.
```

```
/motion-ref The page loads with a white flash before content appears.
            It looks broken.
```

### Add polish to a feature

```
/motion-ref I have a pricing toggle between Monthly and Annual.
            The prices should animate when switching, not just swap.
```

```
/motion-ref My landing page needs to feel premium.
            Something subtle on the hero section.
```

### Get recommendations

```
/motion-ref What animations would work well for a SaaS dashboard?
```

```
/motion-ref I'm building a mobile chat app.
            What motion effects should I consider?
```

## Categories

| # | Category | Count | Highlights |
|---|----------|-------|------------|
| 1 | Loading & Waiting | 14 | Spinner, Skeleton Shimmer, Wave Bars, Typing Indicator, Rose Curve, Lemniscate |
| 2 | Button & Click Feedback | 9 | Press Scale, Ripple, Success Check, Error Shake, Confetti |
| 3 | Text & Data | 10 | Typewriter, Number Counter, Flip Counter, Shimmer Text, Gradient Text |
| 4 | Overlay & Popup | 10 | Modal, Bottom Sheet, Toast, Tooltip, Drawer, Command Palette |
| 5 | Navigation & Transition | 7 | Page Slide, Shared Element, Tab Slide, Dock Nav |
| 6 | Form & Input | 10 | Focus Ring, Label Float, Toggle Switch, OTP Input, Range Slider, Step Indicator |
| 7 | Scroll-driven | 5 | Scroll Reveal, Progress Indicator, Scroll Text Reveal |
| 8 | Icon & Badge | 10 | Hamburger/Close, SVG Draw, Badge Bounce, Heart Like, Bell Shake, Copy Check |
| 9 | Carousel & List | 8 | Carousel, Card Stack, Drag Reorder, Accordion, Avatar Stack, Swipe Action |
| 10 | State Change | 7 | Theme Toggle, Error Recovery, Online Status, Favorite Star, Read/Unread |
| 11 | Atmosphere & Background | 8 | Gradient Flow, Particles, Magnetic Cursor, 3D Card Hover, Light Sweep, Scan Line |
| 12 | Data Visualization | 5 | Bar Chart Rise, Donut Chart, Gauge Meter, Sparkline Draw, Counter Card |
| 13 | Enter & Exit | 8 | Fade In, Slide Up, Spring In, Stagger, Blur In, Collapse |

## Live Preview

Browse all 111 effects with live demos: **https://joepui.github.io/motion-ref-skill/**

## License

MIT
