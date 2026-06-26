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
- **视觉**：折线和下方渐变面积从左到右同步揭示
- **CSS**：SVG `clipPath` 同时裁切折线和面积，或给 line/area 套同一个 reveal mask
- **要点**：线和渐变必须同步推进；不要先画完线再单独淡入面积

#### 12.5 Counter Card 统计卡片
- **视觉**：数字从 0 滚动到目标值的统计卡片
- **实现**：JS `requestAnimationFrame` + ease-out cubic easing
- **场景**：Dashboard KPI、数据面板

#### 12.6 Horizontal Bar Reveal 横向条形展开
- **视觉**：条形从左侧基线依次向右展开，短暂停住后再重播
- **场景**：Top N 排名、长名称分类、商品/城市/国家对比
- **CSS**：`transform: scaleX(.05 → 1)` + `transform-origin: left` + 每条递增 `animation-delay`
- **要点**：横向条形比柱状图更适合长标签；数值标签等条形完成 70% 后再出现

#### 12.7 Scrubber Line 拖动播放头
- **视觉**：折线先描绘，末端播放头沿时间轴移动，垂直参考线跟随定位
- **场景**：视频/动画时间线、历史回放、监控曲线拖动取值
- **实现**：SVG path 用 `pathLength="100"` 归一化，`stroke-dashoffset: 100 → 0` 与播放头 `animateMotion keyPoints="0;1;1"` 使用同一 `keyTimes`
- **要点**：播放头颜色可以略亮，但线条主体保持克制；拖动时只更新读数，不重放整条线

#### 12.8 Radial Bars 径向条形
- **视觉**：多条进度环按半径叠成同心圆，依次描绘到目标比例
- **场景**：多个比例的紧凑对比、多项目完成度、多渠道达成率
- **CSS**：SVG circle + `pathLength="100"` 归一化长度 + 多个 `stroke-dashoffset` 目标值 + 分层 `animation-delay`
- **要点**：最多 3-4 条环；用灰阶深浅区分层级，不要做成彩虹圆环

#### 12.9 Scatter Pop 散点弹入
- **视觉**：坐标轴先出现，点按轻微 stagger 缩放弹入，悬停时显示局部信息
- **场景**：两个连续变量相关性、用户分群、价格 vs 销量、身高 vs 体重
- **CSS**：点 `transform: scale(0 → 1)` + `opacity`，可配合 `transition-delay`
- **要点**：散点动效要短，重点是让分布成形；避免每个点弹得太夸张

#### 12.10 Density Curve 密度曲线
- **视觉**：平滑曲线和半透明面积从左到右同步揭示，用于对比分布
- **场景**：连续变量分布、实验组/对照组、评分分布、价格区间密度
- **CSS**：同一个 SVG `clipPath` 同步裁切曲线和面积
- **要点**：适合替代过细的直方图；对比曲线不宜超过 2-3 条

#### 12.11 Pie Slice Reveal 饼图扇区展开
- **视觉**：扇区按顺序从中心角度展开，最后整体轻微 settle
- **场景**：少量分类占比、市场份额、预算分配
- **实现**：SVG path 按角度生成 arc，或用 `conic-gradient` + mask 做静态比例
- **要点**：仅在 <=5 个分类时使用；分类更多时改用条形图或堆叠条形

#### 12.12 Radar Sweep 雷达图描绘
- **视觉**：网格先淡入，多边形从中心扩展到各维度得分
- **场景**：能力评分、球员属性、产品维度、综合画像
- **CSS/JS**：SVG polygon points 插值 + 网格线 `opacity` 入场
- **要点**：维度控制在 5-7 个；数值不是精确比较时才用，精确比较优先条形图
