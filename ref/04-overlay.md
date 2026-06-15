### 4. 弹层与浮层

> 弹窗和浮层是独立于页面的"新层"。入场要说明"我从哪来"，退场要说明"我回哪去"。

#### 4.1 Modal 弹窗
- **视觉**：scale(0.95) + opacity 0 → scale(1) + opacity 1，背景 overlay 同时淡入
- **场景**：确认对话框、信息编辑
- **CSS**：overlay + 弹窗 scale + fade
- **要点**：关闭动画要比打开快一点

#### 4.2 Bottom Sheet 底部面板
- **视觉**：从底部滑上来
- **场景**：移动端操作菜单、筛选面板
- **CSS**：`transform: translateY(100%) → translateY(0)`；easing 用 `cubic-bezier(.32,.72,0,1)`

#### 4.3 Dropdown 下拉菜单
- **视觉**：从触发元素向下展开 + 淡入
- **CSS**：`transform-origin: top; transform: scaleY(0.9) → scaleY(1)`
- **要点**：`transform-origin` 必须设对

#### 4.4 Popover 气泡弹出
- **视觉**：从锚点方向 scale + fade 弹出
- **CSS**：根据弹出方向设 `transform-origin`

#### 4.5 Toast 轻提示
- **视觉**：从顶部/底部滑入 + 淡入，停留后自动滑出
- **时长**：入场 300ms，停留 3-5s，退场 300ms

#### 4.6 Alert Slide 警告横幅
- **视觉**：从顶部推入，将内容下推
- **CSS**：`max-height: 0 → max-height: 60px` + opacity

#### 4.7 Context Menu 右键菜单
- **视觉**：从鼠标位置快速 scale + fade 弹出
- **时长**：100-150ms（要快）

#### 4.8 Tooltip 延迟提示
- **视觉**：悬停延迟显示，离开即隐
- **场景**：按钮解释、术语说明
- **CSS**：`:hover` + `transition-delay: 0.4s`（显示延迟），`:not(:hover)` 时 `transition-delay: 0s`（立即隐藏）
- **要点**：非对称延迟是关键 — 显示慢（防误触），隐藏快（不挡路）

#### 4.9 Drawer 抽屉面板
- **视觉**：从侧边滑入的面板
- **场景**：设置面板、筛选器、购物车
- **CSS**：`transform: translateX(100%) → translateX(0)`；easing 用 `cubic-bezier(.32,.72,0,1)`
- **要点**：通常右侧滑入，宽度不超过 80vw

#### 4.10 Command Palette 命令面板
- **视觉**：从顶部缩放 + 淡入的搜索框，带快捷键提示
- **场景**：Cmd+K 全局搜索、命令面板
- **CSS**：`transform: scale(.95) translateY(-8px) → scale(1) translateY(0)`
- **要点**：打开速度要快（200ms），自动聚焦搜索框
