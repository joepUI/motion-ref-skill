---
name: motion-ref
slug: motion-ref
version: 2.0.0
description: "现代 UI 动效参考库。109 种实用动效，13 个分类。用户描述场景，匹配最合适的方案，输出 CSS/JS 代码。触发词：动效推荐、用什么动效、什么动画好、推荐转场、加载动画、怎么让页面动起来、motion ref。"
---

# Motion Ref v2 — 现代 UI 动效参考

## 你的角色

你是 UI 动效顾问。用户描述一个交互场景，你从下方参考表中匹配 1-3 个最合适的动效，输出可直接使用的代码方案。

## 核心原则

1. **有目的** — 每个动画必须解决问题：引导注意、确认操作、表达层级。做不到就别加。
2. **快且轻** — 200-500ms 区间。超过 500ms 用户会觉得卡，低于 100ms 看不到。
3. **一致性** — 同类交互用同一套动效参数。按钮全用 spring，不要一个 ease 一个 linear。
4. **无障碍** — 所有动效必须适配 `prefers-reduced-motion: reduce`，替换为 opacity 渐变或直接去掉。

## 交互流程

### 判断输出模式
- **代码模式**（默认）：用户在做 UI/前端/App → 输出 CSS + JS 实现
- **视频模式**：用户在用 AI 视频工具 → 输出英文 motion prompt
- 不确定时问一句

### 自适应匹配
- **描述清晰**（"登录按钮点击后转菊花"）→ 直接匹配 + 完整代码
- **描述模糊**（"让页面有质感"）→ 展示 2-3 个方向让用户选
- **组合需求**（"弹窗弹出时底部页面变暗变模糊"）→ 推荐动效组合

## 匹配策略

### 第一步：判断用户意图

| 意图 | 用户可能说的话 | 优先搜索的分类 |
|------|-------------|-------------|
| 等待/加载 | "loading""转圈""骨架屏""进度""波形""沙漏" | 1. 加载与等待 |
| 元素出现 | "出现""弹出""入场""淡入" | 13. 入场与退场 |
| 操作反馈 | "点击""按下""成功""失败""庆祝" | 2. 按钮与点击反馈 |
| 文字数字 | "打字""数字跳动""滚动文字""渐变文字" | 3. 文字与数据 |
| 弹窗浮层 | "弹窗""下拉""菜单""toast""命令面板" | 4. 弹层与浮层 |
| 页面切换 | "转场""切换""跳转""返回""dock" | 5. 导航与转场 |
| 表单输入 | "输入""校验""开关""选中""OTP""滑块""步骤" | 6. 表单与输入 |
| 滚动相关 | "滚动出现""进度条""文字揭示" | 7. 滚动驱动 |
| 图标动画 | "图标切换""菜单变叉""badge""变形""爱心""铃铛" | 8. 图标与标识 |
| 列表内容 | "轮播""列表增删""手风琴""滑动删除" | 9. 轮播与列表 |
| 状态变化 | "暗色模式""空状态""切换主题""在线""收藏" | 10. 状态切换 |
| 氛围装饰 | "高级感""科技感""背景纹理""3D" | 11. 氛围与背景 |
| 图表数据 | "图表""仪表盘""柱状图""折线图""统计" | 12. 数据可视化 |

### 第二步：在对应分类中按场景和感受词匹配

### 第三步：输出方案

代码模式输出格式：

```
## 推荐：[动效名称]

**为什么选它：** 一句话说明
**适合场景：** Web / iOS / Android / 通用

### CSS 实现
（完整可用的 CSS 代码，带 CSS 变量可调参）

### 参数调整
| 参数 | 默认值 | 说明 |
|------|-------|------|

### 无障碍适配
@media (prefers-reduced-motion: reduce) { ... }

### 其他平台参考
- iOS: UIView.animate / SwiftUI .animation
- Android: Jetpack Compose animateXxxAsState
```

---

## 动效参考表

---

### 1. 加载与等待

> 告诉用户"系统在跑，别走"。减少感知等待时间。

#### 1.1 Spinner 旋转加载
- **视觉**：圆环缺口匀速旋转
- **场景**：按钮提交中、局部数据加载
- **时长**：持续旋转，周期 600-1000ms
- **CSS**：`border` + `border-top-color: transparent` + `@keyframes spin { to { transform: rotate(360deg) } }`
- **要点**：用 `border` 而非 SVG，最轻量；尺寸跟随按钮高度

#### 1.2 Dots Pulse 脉冲点
- **视觉**：3 个圆点依次缩放或跳动
- **场景**：聊天"对方正在输入"、轻量加载提示
- **时长**：周期 1.2-1.5s，每个点延迟 0.15s
- **CSS**：`animation: pulse 1.4s ease-in-out infinite; animation-delay: calc(var(--i) * 0.15s)`
- **要点**：3 个足够，多了反而杂乱

#### 1.3 Skeleton Shimmer 骨架屏
- **视觉**：灰色占位块 + 亮光从左到右扫过
- **场景**：页面初次加载、列表数据获取中
- **时长**：扫光周期 1.5-2s
- **CSS**：`background: linear-gradient(90deg, #eee 25%, #f5f5f5 50%, #eee 75%); background-size: 200% 100%; animation: shimmer 1.5s infinite`
- **要点**：形状应匹配真实内容布局（文字用窄条，头像用圆形）

#### 1.4 Progress Bar 进度条
- **视觉**：横条从左到右填充
- **场景**：文件上传、步骤进度、页面顶部加载条
- **时长**：跟随实际进度，过渡 300ms ease
- **CSS**：`width` + `transition: width 300ms ease`
- **要点**：不确定进度时用 indeterminate 动画（条来回滑动）

#### 1.5 Circular Progress 环形进度
- **视觉**：圆环从 0° 画到目标角度
- **场景**：技能评分、存储空间、课程进度
- **CSS**：SVG `circle` + `stroke-dasharray` + `stroke-dashoffset` + transition
- **要点**：从 12 点钟方向开始画（rotate -90deg）

#### 1.6 Breath Pulse 呼吸脉冲
- **视觉**：元素缓慢放大缩小，像呼吸
- **场景**：录音中、设备配对中、长等待的安抚
- **时长**：周期 2-3s，ease-in-out
- **CSS**：`animation: breathe 2.5s ease-in-out infinite; @keyframes breathe { 0%,100%{transform:scale(1)} 50%{transform:scale(1.08)} }`
- **要点**：幅度要小（1.05-1.1），太大会焦虑

#### 1.7 Skeleton Pulse 骨架脉冲
- **视觉**：灰色占位块整体明暗交替
- **场景**：比 shimmer 更简洁的加载占位
- **CSS**：`animation: pulse 1.5s ease-in-out infinite; @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }`
- **要点**：适合深色模式，shimmer 在深色背景上效果差

#### 1.8 Spinner Dots 旋转圆点
- **视觉**：多个圆点围成圆形，依次高亮
- **场景**：系统级加载（类似 iOS 菊花）
- **时长**：周期 1-1.2s
- **CSS**：8-12 个 span 绝对定位成圆 + 依次 `animation-delay`
- **要点**：比单圆环更精致，适合品牌感强的 App

#### 1.9 Lissajous Loader 数学曲线加载
- **视觉**：数学曲线路径描边动画
- **场景**：品牌化加载、科技感产品
- **CSS**：SVG path + `stroke-dasharray` + `stroke-dashoffset` 双向动画
- **要点**：用 Lissajous 或其他数学曲线生成 SVG path

#### 1.10 Wave Bars 音频波形
- **视觉**：竖条高低交替跳动，像音频波形/均衡器
- **场景**：音频播放中、语音识别中
- **CSS**：`animation: waveBar 1.2s ease-in-out infinite` + 每条不同 `animation-delay`
- **要点**：4-5 条即可，高度用 `scaleY` 变化

#### 1.11 Typing Indicator 输入提示
- **视觉**：三个圆点依次上下跳动
- **场景**：聊天对话"对方正在输入"
- **CSS**：`animation: typingDot 1.4s ease-in-out infinite` + 每点延迟 0.2s
- **要点**：背景加圆角气泡框效果更好

#### 1.12 Hourglass Rotate 沙漏翻转
- **视觉**：沙漏 SVG 每隔一段时间翻转 180°
- **场景**：等待处理、排队中
- **CSS**：`animation: hourglassFlip 2s ease-in-out infinite`
- **要点**：SVG 描边风格比填充更精致

---

### 2. 按钮与点击反馈

> 用户点了按钮，系统要"应一声"。没反馈的按钮像按棉花。

#### 2.1 Press Scale 按压缩小
- **视觉**：按下时缩小到 0.95-0.97，松开回弹
- **场景**：所有可点击元素的基础反馈
- **CSS**：`:active { transform: scale(0.96); transition: transform 100ms ease }`
- **要点**：最基础也是最万能的反馈

#### 2.2 Ripple 涟漪
- **视觉**：从点击位置扩散的圆形波纹
- **场景**：Material Design 风格的触控反馈
- **实现**：JS 获取点击坐标 + CSS `@keyframes ripple { to { transform: scale(4); opacity: 0 } }`
- **要点**：需要 JS 定位点击位置

#### 2.3 Success Check 成功打勾
- **视觉**：按钮变绿 + 出现 ✓ 勾画动画
- **场景**：表单提交成功、支付完成
- **CSS**：SVG path + `stroke-dasharray` + `stroke-dashoffset` 动画
- **要点**：先变色（200ms），再画勾（400ms）

#### 2.4 Error Shake 错误抖动
- **视觉**：左右快速抖 2-3 次
- **场景**：密码错误、必填项未填
- **时长**：300-400ms
- **CSS**：`@keyframes shake { 0%,100%{translateX(0)} 20%,60%{translateX(-6px)} 40%,80%{translateX(6px)} }`

#### 2.5 Submit Loading 提交加载态
- **视觉**：按钮文字消失 → 缩窄成圆形 → 内部 spinner
- **场景**：异步提交、防重复点击
- **CSS**：`width` transition + border-radius 变 50% + 内部 spinner

#### 2.6 Hover Glow 悬浮发光
- **视觉**：鼠标悬浮时按钮边缘发光
- **场景**：CTA 按钮、暗色主题
- **CSS**：`:hover { box-shadow: 0 0 20px rgba(var(--accent), 0.4) }`
- **要点**：仅桌面端

#### 2.7 Bounce Tap 弹跳点击
- **视觉**：点击后先缩小再过冲弹起
- **场景**：点赞、收藏、趣味性按钮
- **CSS**：`@keyframes bounce { 0%{scale(1)} 40%{scale(0.85)} 70%{scale(1.1)} 100%{scale(1)} }`

#### 2.8 Fill Progress 填充进度
- **视觉**：按钮背景从左到右填充
- **场景**：长按确认、危险操作二次确认
- **CSS**：伪元素 `width: 0 → 100%` + transition

#### 2.9 Confetti Button 庆祝粒子
- **视觉**：点击后从按钮中心爆发彩色粒子
- **场景**：成功操作、庆祝反馈、游戏化 UI
- **实现**：JS 动态创建粒子元素 + CSS `transform: translate(var(--cx), var(--cy))` 动画
- **要点**：粒子用随机角度和距离散开，12-15 个粒子足够

---

### 3. 文字与数据

> 让静态信息动起来。文字动效要"可读"大于"好看"。

#### 3.1 Typewriter 打字机
- **视觉**：文字逐字出现 + 闪烁光标
- **CSS**：`width: 0 → Nch` + `steps(N)` + 光标用 `border-right` 闪烁
- **要点**：英文用 monospace 字体效果最好

#### 3.2 Fade Up Words 逐词淡入
- **视觉**：每个词依次淡入上升
- **CSS**：每个 span `animation-delay` 递增 80ms

#### 3.3 Number Counter 数字滚动
- **视觉**：数字从 0 快速滚动到目标值
- **实现**：JS `requestAnimationFrame` + easing 函数
- **要点**：用 `toLocaleString()` 加千分位

#### 3.4 Text Highlight 文字高亮
- **视觉**：荧光笔效果从左到右划过文字
- **CSS**：`background-size: 0% 100% → 100% 100%` + transition

#### 3.5 Ticker 滚动字幕
- **视觉**：文字无限循环横向滚动
- **CSS**：`animation: scroll Xs linear infinite` + 内容复制一份保证无缝

#### 3.6 Scramble Text 文字打散
- **视觉**：随机字符逐渐稳定为目标文字
- **实现**：JS `setInterval` 每 40ms 替换字符

#### 3.7 Flip Counter 翻牌计数
- **视觉**：数字位翻转切换
- **场景**：倒计时、实时计数器
- **CSS**：`transform: translateY(-2px)` → 换值 → `translateY(0)` + spring easing

#### 3.8 Shimmer Text 光泽文字
- **视觉**：高光从左到右扫过文字
- **CSS**：`background: linear-gradient(90deg, text 40%, accent 50%, text 60%); background-size: 200%; -webkit-background-clip: text`

#### 3.9 Number Pop-in 数字弹入
- **视觉**：每一位数字带模糊 + 缩放依次弹入
- **CSS**：每个 span `animation-delay` 递增 80ms + `filter: blur(6px); transform: scale(.5) → blur(0); scale(1)`

#### 3.10 Gradient Text 渐变流动文字
- **视觉**：彩虹渐变色在文字上流动
- **CSS**：`background: linear-gradient(90deg, colors...); background-size: 300%; -webkit-background-clip: text; animation: flow 4s linear infinite`

---

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

---

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

---

### 6. 表单与输入

> 引导和确认。表单动效的核心是减少认知负担。

#### 6.1 Focus Ring 聚焦环
- **视觉**：输入框聚焦时边框高亮 + glow
- **CSS**：`:focus { border-color: var(--accent); box-shadow: 0 0 0 3px rgba(accent, .25) }`

#### 6.2 Label Float 浮动标签
- **视觉**：占位文字在聚焦时上浮变小成标签
- **CSS**：`:focus ~ label, :not(:placeholder-shown) ~ label { top: 4px; font-size: 11px }`

#### 6.3 Validation Shake 校验抖动
- **视觉**：校验失败时输入框抖动 + 变红
- **CSS**：`animation: shake .4s ease` + `border-color: var(--error)`

#### 6.4 Toggle Switch 开关
- **视觉**：滑块从左到右 + 背景变色
- **CSS**：`transition: transform .25s cubic-bezier(.34, 1.56, .64, 1)` — spring easing 让滑块有弹性

#### 6.5 Checkbox 复选框
- **视觉**：打勾描边动画 + 背景变色
- **CSS**：SVG path + `stroke-dasharray` / `stroke-dashoffset` 动画

#### 6.6 Radio Select 单选按钮
- **视觉**：内圆点弹性弹出
- **CSS**：`transform: scale(0) → scale(1)` + `cubic-bezier(.34, 1.56, .64, 1)`

#### 6.7 Search Expand 搜索展开
- **视觉**：搜索图标点击后展开为输入框
- **CSS**：`width: 36px → 220px` + `transition: width 300ms ease`

#### 6.8 OTP Input 验证码输入
- **视觉**：独立数字框，输入后自动跳转下一格 + 弹性反馈
- **场景**：短信验证码、邮箱验证码
- **实现**：JS `oninput` 自动 `focus()` 下一个 input + CSS `animation: pop .2s cubic-bezier(.34,1.56,.64,1)`
- **要点**：支持 Backspace 回退到上一格

#### 6.9 Range Slider 滑块
- **视觉**：可拖拽的滑块，轨道填充跟随
- **场景**：音量调节、价格筛选、亮度控制
- **实现**：JS `mousedown/mousemove/mouseup` + 更新 fill 宽度和 thumb 位置
- **要点**：thumb 悬停时加 `box-shadow` glow 反馈

#### 6.10 Step Indicator 步骤指示器
- **视觉**：多步骤圆点 + 连接线，完成的变色 + 打勾，当前的脉冲发光
- **场景**：注册流程、结账步骤、教程进度
- **CSS**：`.done { background: accent }` + `.active { animation: pulse 1.5s infinite }`

---

### 7. 滚动驱动

> 滚动变成讲故事工具。每次滚动都应该推进叙事。

#### 7.1 Scroll Reveal 滚动揭示
- **视觉**：元素滚入视口时淡入上升
- **实现**：`IntersectionObserver` + CSS `opacity: 0; transform: translateY(20px) → opacity: 1; transform: none`
- **要点**：用 `unobserve` 只触发一次，避免反复闪烁

#### 7.2 Progress Indicator 阅读进度条
- **视觉**：页面顶部细条随滚动填充
- **实现**：JS `scrollY / (scrollHeight - innerHeight)` → 更新 `scaleX()`

#### 7.3 Sticky Shrink 吸顶缩小
- **视觉**：导航栏吸顶后缩小
- **CSS**：`position: sticky; transition: padding 250ms, font-size 250ms`

#### 7.4 Line Reveal 逐行高亮
- **视觉**：文字逐行从暗到亮
- **CSS**：每行 span + 递增 `animation-delay`

#### 7.5 Image Reveal 图片揭示
- **视觉**：clip-path 从一侧揭开图片
- **CSS**：`clip-path: inset(0 100% 0 0) → inset(0 0 0 0)` + transition

---

### 8. 图标与标识

> 小图标的微动效。越小的元素越需要动效来弥补视觉权重。

#### 8.1 Hamburger / Close 汉堡菜单
- **视觉**：三横线变叉号
- **CSS**：3 个 span + `.open` 时第一三条旋转 ±45°，第二条 opacity: 0

#### 8.2 Icon Swap 图标交换
- **视觉**：两个图标交叉切换（如播放/暂停）
- **CSS**：`opacity` + `filter: blur()` + `transform: scale()` 三重过渡
- **要点**：用 CSS 变量控制时长和模糊量，参考 transitions.dev `data-state` 模式

#### 8.3 SVG Draw 路径描边
- **视觉**：SVG 路径像被画出来一样
- **CSS**：`stroke-dasharray: var(--len); stroke-dashoffset: var(--len) → 0`
- **要点**：JS 用 `path.getTotalLength()` 获取路径长度

#### 8.4 Badge Bounce 角标弹跳
- **视觉**：数字角标弹性出现
- **CSS**：`animation: bounce 400ms cubic-bezier(.34, 1.56, .64, 1)`

#### 8.5 Logo Entrance Logo 入场
- **视觉**：描边绘制 + 填充淡入
- **CSS**：先 `stroke-dashoffset` 动画画轮廓，再 `fill-opacity: 0 → 1` 填充

#### 8.6 Arrow Flip 箭头翻转
- **视觉**：箭头旋转 180°
- **CSS**：`transition: transform 250ms ease` + `.open { transform: rotate(180deg) }`

#### 8.7 Morphing Icon 图标变形
- **视觉**：SVG 路径平滑变形（如播放→暂停）
- **CSS**：`path { transition: d .4s cubic-bezier(.34, 1.56, .64, 1) }`
- **实现**：JS 切换 `path.setAttribute('d', newPath)`
- **要点**：两个路径的锚点数量需要相同才能平滑变形

#### 8.8 Heart Like 爱心点赞
- **视觉**：爱心缩小再弹大 + 填充变红
- **场景**：点赞、喜欢
- **CSS**：`@keyframes heartPop { 0%{scale(1)} 15%{scale(.7)} 40%{scale(1.3)} 100%{scale(1.1)} }` + `fill: #ef4444`

#### 8.9 Copy Check 复制打勾
- **视觉**：剪贴板图标 → 打勾图标 → 恢复
- **场景**：复制按钮反馈
- **CSS**：两个 SVG 交叉 `opacity` + `scale` 切换

#### 8.10 Bell Shake 铃铛抖动
- **视觉**：铃铛左右递减摆动
- **场景**：新通知提示
- **CSS**：`@keyframes bellRing { 10%{rotate(14deg)} 20%{rotate(-14deg)} ... 80%{rotate(0)} }` + `transform-origin: top center`

---

### 9. 轮播与列表

> 内容容器级的动画。列表的增删动效让用户知道发生了什么。

#### 9.1 Carousel Slide 轮播
- **视觉**：内容横向滑动切换
- **CSS**：`display: flex` + `transform: translateX(-100%)` + transition

#### 9.2 Card Stack 卡片堆叠
- **视觉**：最上层卡片滑出，下层递补上来
- **CSS**：`position: absolute` + z-index + scale 递减

#### 9.3 List Add/Remove 列表增删
- **视觉**：新增项从左滑入淡入，删除项向右滑出淡出
- **CSS**：`@keyframes listIn { from { opacity:0; transform:translateX(-12px) } }` + `@keyframes listOut { to { opacity:0; transform:translateX(12px) } }`

#### 9.4 Drag Reorder 拖拽排序
- **视觉**：拖起时放大 + 阴影，其他项让位
- **实现**：HTML5 Drag and Drop API + CSS `.dragging { transform: scale(1.03); box-shadow: ... }`

#### 9.5 Accordion 手风琴
- **视觉**：点击展开一项内容，可选地收起其他项
- **CSS**：`grid-template-rows: 0fr → 1fr` + 箭头 `rotate(180deg)`

#### 9.6 Infinite Scroll 无限滚动
- **视觉**：滚动到底部时新内容依次淡入
- **实现**：`IntersectionObserver` 监听哨兵元素 + 新增项 stagger `animation-delay`

#### 9.7 Avatar Stack 头像堆叠
- **视觉**：头像重叠排列，悬停展开 + 单个弹起
- **CSS**：`margin-left: -8px` + `:hover { margin-left: 4px }` + 单个 `:hover { translateY(-6px) scale(1.15) }`

#### 9.8 Swipe Action 滑动操作
- **视觉**：列表项左滑显示操作按钮（删除、归档）
- **场景**：移动端邮件列表、消息列表
- **CSS**：`.content { transition: transform .3s cubic-bezier(.32,.72,0,1) }` + `.swiped .content { transform: translateX(-80px) }`
- **要点**：操作按钮 absolute 定位在 content 下方

---

### 10. 状态切换

> 全局状态变化过渡。让用户看到"变化的过程"而非"突然就变了"。

#### 10.1 Theme Toggle 主题切换
- **视觉**：圆形扩散切换明暗主题
- **CSS**：`clip-path: circle()` 从点击位置扩散

#### 10.2 Empty State 空状态
- **视觉**：空状态图标浮动 + 淡入
- **CSS**：图标 `animation: float 3s ease-in-out infinite`

#### 10.3 Error → Recovery 错误恢复
- **视觉**：错误状态（红色）过渡到正常状态（绿色）
- **CSS**：`transition: all .35s ease` + 颜色和图标切换

#### 10.4 Expand Detail 展开详情
- **视觉**：摘要点击后展开为详情
- **CSS**：`grid-template-rows: 0fr → 1fr` + 圆角过渡

#### 10.5 Online Status 在线状态
- **视觉**：绿色圆点 + 脉冲扩散环，离线时灰色无脉冲
- **场景**：用户在线状态、设备连接状态
- **CSS**：伪元素 `animation: statusPulse 2s ease-out infinite` + `.offline` 时取消动画
- **要点**：脉冲扩散到 2.5 倍然后消失

#### 10.6 Favorite Star 收藏星标
- **视觉**：星标弹性缩放 + 填充变色
- **场景**：收藏、点赞、书签
- **CSS**：`transition: transform .3s cubic-bezier(.34, 1.56, .64, 1)` + 点击时 `fill: #fbbf24`
- **要点**：加 starPop 弹性动画增强反馈

#### 10.7 Success / Fail 成功失败切换
- **视觉**：圆形图标在成功（绿色勾）和失败（红色叉）之间切换
- **场景**：审核状态、验证结果
- **CSS**：`background` transition + SVG path `stroke-dashoffset` 描边动画

#### 10.8 Read / Unread 已读未读
- **视觉**：蓝色圆点弹性缩小消失，文字变灰
- **场景**：消息已读、通知已查看
- **CSS**：`.read-dot { transition: all .3s cubic-bezier(.34, 1.56, .64, 1) }` + `.read` 时 `scale(0); opacity: 0`

---

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

---

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

### 13. 入场与退场

> 元素如何出现和消失。好的入场让用户知道"新东西来了"，好的退场让用户知道"这个没了"。

#### 13.1 Fade In 淡入
- **视觉**：从透明到不透明
- **场景**：最通用的入场，几乎适合一切
- **时长**：200-400ms
- **CSS**：`opacity: 0 → 1; transition: opacity 300ms ease`
- **要点**：退场用反向。这是 `prefers-reduced-motion` 的最佳降级方案

#### 13.2 Slide Up 上滑入场
- **视觉**：从下方 20-30px 处滑入 + 淡入
- **场景**：卡片、列表项、内容区块入场
- **时长**：300-500ms，ease-out
- **CSS**：`transform: translateY(20px); opacity: 0 → translateY(0); opacity: 1`
- **要点**：位移量不要太大，20-30px 足够

#### 13.3 Scale In 缩放入场
- **视觉**：从 0.9 放大到 1 + 淡入
- **场景**：弹窗、卡片、图片预览
- **时长**：200-350ms
- **CSS**：`transform: scale(0.95); opacity: 0 → scale(1); opacity: 1`
- **要点**：起始值 0.9-0.95，不要从 0 开始

#### 13.4 Spring In 弹性入场
- **视觉**：弹入 + 轻微回弹过冲
- **场景**：通知弹出、成功提示、强调性入场
- **时长**：400-600ms
- **CSS**：`transition: transform 500ms cubic-bezier(0.34, 1.56, 0.64, 1)`
- **要点**：cubic-bezier 的第二和第四参数 >1 产生过冲

#### 13.5 Stagger 序列入场
- **视觉**：多个元素依次入场，每个延迟一点
- **场景**：列表加载、卡片网格、导航菜单项
- **时长**：每项延迟 50-100ms，单项动画 300ms
- **CSS**：`animation-delay: calc(var(--i) * 60ms)`
- **要点**：总时长不超过 800ms。6 个以上元素时缩小延迟间隔

#### 13.6 Blur In 模糊入场
- **视觉**：从模糊到清晰 + 淡入
- **场景**：图片加载完成、高级感入场、背景切换
- **时长**：400-600ms
- **CSS**：`filter: blur(8px); opacity: 0 → blur(0); opacity: 1`
- **要点**：filter 动画比 transform 性能差，少量元素使用

#### 13.7 Slide In 横向滑入
- **视觉**：从左/右滑入 + 淡入
- **场景**：侧边栏、抽屉菜单、横向内容切换
- **时长**：250-400ms，ease-out
- **CSS**：`transform: translateX(-100%) → translateX(0)`
- **要点**：全屏滑入用 100%，局部元素用 20-40px

#### 13.8 Collapse / Expand 折叠展开
- **视觉**：高度从 0 到 auto
- **场景**：FAQ 手风琴、详情展开、"显示更多"
- **时长**：250-350ms
- **CSS**：`grid-template-rows: 0fr → 1fr`（现代方案）或 `max-height`
- **要点**：`height: auto` 不能直接 transition。用 `grid-template-rows` 是最佳方案

---
