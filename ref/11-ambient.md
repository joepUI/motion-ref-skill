### 11. 氛围与背景

> 提升调性的装饰动效。注意性能，背景动效不能影响交互。

#### 11.1 Gradient Flow 渐变流动
- **视觉**：背景渐变色缓慢流动
- **CSS**：`background-size: 300% 300%; animation: flow 6s ease infinite`

#### 11.2 Glow Pulse 呼吸发光
- **视觉**：元素持续呼吸式发光
- **CSS**：`box-shadow` + `animation: glow 3s ease-in-out infinite`

#### 11.3 Particles 粒子
- **视觉**：粒子缓慢上升漂浮
- **实现**：Canvas 2D + `requestAnimationFrame`

#### 11.4 Magnetic Cursor 磁性光标
- **视觉**：元素被光标吸引跟随
- **实现**：JS `mousemove` → `transform: translate(dx, dy)`；dx/dy 为偏移 × 系数（0.1-0.2）

#### 11.5 Glow Trace 光标跟随高光
- **视觉**：鼠标移动时卡片表面出现跟随光晕
- **CSS**：`::before` + `radial-gradient` + CSS 变量 `--mx`, `--my` 跟随鼠标

#### 11.6 Light Sweep 光线扫过
- **视觉**：光线从左到右扫过表面
- **CSS**：伪元素 + `linear-gradient(110deg, transparent, rgba(255,255,255,.08), transparent)` + `animation: sweep 3s infinite`

#### 11.7 3D Card Hover 3D 卡片悬浮
- **视觉**：卡片根据鼠标位置 3D 倾斜
- **实现**：JS `mousemove` → `rotateY(x*20deg) rotateX(-y*20deg)`；父容器需 `perspective: 400px`
