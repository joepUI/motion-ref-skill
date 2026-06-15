### 12. 数据可视化

> 图表与数据展示动效。让数据"讲故事"而非只是展示数字。

#### 12.1 Bar Chart Rise 柱状图升起
- **视觉**：柱状从底部依次生长到目标高度
- **CSS**：`height: 0 → var(--h)` + 每列递增 `animation-delay`
- **要点**：用 CSS 变量 `--h` 控制每列高度

#### 12.2 Donut Chart 环形图
- **视觉**：环形弧线依次描绘
- **CSS**：SVG circle + `stroke-dasharray` + `stroke-dashoffset` 动画
- **要点**：多段弧用不同颜色和 dashoffset 起始值

#### 12.3 Gauge Meter 仪表盘
- **视觉**：半圆弧 + 指针旋转到目标值
- **实现**：SVG 半圆弧 path + `stroke-dashoffset` + 指针 `transform: rotate(deg)` 同步
- **要点**：指针用 `transform-origin: center bottom`，旋转范围 -90° 到 90°

#### 12.4 Sparkline Draw 迷你折线图
- **视觉**：折线图路径描边绘制 + 面积渐显
- **CSS**：SVG path + `stroke-dasharray/dashoffset` + 面积用 `opacity: 0 → 0.3` 延迟淡入

#### 12.5 Counter Card 统计卡片
- **视觉**：数字从 0 滚动到目标值的统计卡片
- **实现**：JS `requestAnimationFrame` + ease-out cubic easing
- **场景**：Dashboard KPI、数据面板
