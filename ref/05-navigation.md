### 5. 导航与转场

> 页面之间的切换动画。告诉用户"你从哪来，到了哪"。

#### 5.1 Page Slide 页面推入
- **视觉**：新页面从右滑入，旧页面向左退出
- **CSS**：`transform: translateX(100%) → translateX(0)`
- **要点**：后退时方向反转

#### 5.2 Fade Switch 淡入淡出切换
- **视觉**：旧内容淡出 → 新内容淡入
- **场景**：Tab 内容切换、同级页面切换

#### 5.3 Shared Element 共享元素过渡
- **视觉**：元素从列表位置无缝过渡到详情页位置
- **CSS**：`view-transition-name` + View Transitions API

#### 5.4 Tab Slide 标签指示器
- **视觉**：底部指示条跟随选中 Tab 滑动
- **CSS**：`transition: left 250ms ease, width 250ms ease`

#### 5.5 Sidebar Push 侧栏推入
- **视觉**：侧栏展开，同时推动主内容
- **CSS**：`transform: translateX(-100%) → translateX(0)` + 主内容 `margin-left` transition

#### 5.6 View Transition 视图过渡
- **视觉**：圆形扩散切换视图
- **CSS**：`clip-path: circle()` + View Transitions API

#### 5.7 Dock Nav 底部导航
- **视觉**：悬停图标放大，相邻图标联动
- **场景**：macOS Dock 风格导航
- **CSS**：`:hover { transform: scale(1.5) translateY(-6px) }` + `:has(+ .item:hover) { scale(1.25) }`
- **要点**：CSS `:has()` 选择器实现相邻联动
