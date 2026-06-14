<h1 align="center">motion-ref-skill</h1>

<p align="center">
  <strong>Describe what you want. Get production-ready animation code.</strong>
</p>

<p align="center">
  <a href="https://github.com/joepUI/motion-ref-skill/stargazers"><img src="https://img.shields.io/github/stars/joepUI/motion-ref-skill?style=flat&color=yellow" alt="Stars"></a>
  <a href="https://github.com/joepUI/motion-ref-skill/commits/main"><img src="https://img.shields.io/github/last-commit/joepUI/motion-ref-skill?style=flat" alt="Last Commit"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/joepUI/motion-ref-skill?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="#install">Install</a> •
  <a href="#usage">Usage</a> •
  <a href="#categories">Categories</a> •
  <a href="https://joepui.github.io/motion-ref-skill/">Live Preview</a> •
  <a href="README_zh.md">中文文档</a>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill for modern UI motion design. 105 production-ready animation effects across 13 categories — describe the interaction, get CSS/JS code you can ship.

## Install

```bash
git clone https://github.com/joepUI/motion-ref-skill.git ~/.claude/skills/motion-ref-skill
```

Restart Claude Code after installing.

## Usage

Describe an interaction scenario in natural language. The skill matches the best effect(s) from its reference library and outputs complete, production-ready code.

```
/motion-ref I have a dashboard page that loads several stat cards.
            I want them to appear one by one instead of all at once.
```

```
/motion-ref Users submit a form and wait 2-3 seconds for the server response.
            The submit button should show a loading state.
```

```
/motion-ref I'm building a settings panel as a side drawer.
            It needs to slide in from the right with a backdrop.
```

```
/motion-ref My mobile app has a message list.
            I want swipe-left-to-delete like iOS Mail.
```

```
/motion-ref I have a pricing toggle between Monthly and Annual.
            The prices should animate when switching, not just swap.
```

```
/motion-ref The landing page hero has a tagline.
            I want it to have a subtle shimmer effect for a premium feel.
```

```
/motion-ref I'm building a multi-step checkout flow.
            I need a progress indicator that shows which step
            the user is on and animates between steps.
```

## Categories

| # | Category | Count | Highlights |
|---|----------|-------|------------|
| 1 | Loading & Waiting | 9 | Spinner, Skeleton Shimmer, Circular Progress, Breath Pulse |
| 2 | Enter & Exit | 8 | Fade In, Slide Up, Spring In, Stagger, Blur In |
| 3 | Button & Click Feedback | 9 | Press Scale, Ripple, Success Check, Error Shake, Confetti |
| 4 | Overlay & Popup | 10 | Modal, Bottom Sheet, Toast, Tooltip, Drawer, Command Palette |
| 5 | Navigation & Transition | 8 | Page Slide, Shared Element, Tab Slide, Dock Nav |
| 6 | Form & Input | 10 | Focus Ring, Label Float, Toggle Switch, OTP Input, Range Slider, Step Indicator |
| 7 | Text & Data | 10 | Typewriter, Number Counter, Flip Counter, Shimmer Text, Gradient Text |
| 8 | Scroll-driven | 7 | Scroll Reveal, Parallax, Progress Indicator, Scroll Snap |
| 9 | Icon & Badge | 7 | Hamburger/Close, SVG Draw, Badge Bounce, Morphing Icon |
| 10 | Carousel & List | 8 | Carousel, Card Stack, Drag Reorder, Accordion, Avatar Stack, Swipe Action |
| 11 | State Change | 6 | Theme Toggle, Skeleton-to-Content, Error Recovery, Confetti Celebration |
| 12 | Atmosphere & Background | 8 | Gradient Flow, Particles, Magnetic Cursor, 3D Card Hover, Meteor Shower |
| 13 | Data Visualization | 5 | Bar Chart Rise, Donut Chart, Gauge Meter, Sparkline Draw, Counter Card |

## Live Preview

Browse all 105 effects with live demos: **https://joepui.github.io/motion-ref-skill/**

## License

MIT
