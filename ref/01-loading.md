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

#### 1.9 Rose Two 双瓣玫瑰曲线
- **视觉**：r=a·cos(2θ) 玫瑰曲线，粒子拖尾沿路径运动 + 呼吸脉冲 + 旋转
- **场景**：品牌化加载、科技感产品、数学/数据类应用
- **JS**：SVG + requestAnimationFrame，粒子沿曲线分布，透明度衰减形成拖尾
- **要点**：粒子数 50-80，拖尾比例 0.3，呼吸周期 4-5s

#### 1.10 Rose Three 三瓣玫瑰曲线
- **视觉**：r=a·cos(3θ) 三瓣结构，旋转 + 呼吸
- **场景**：同 Rose Two，三瓣更具辨识度
- **JS**：同 Rose Two，k 参数改为 3
- **要点**：k 值决定花瓣数，奇数 k 产生 k 瓣，偶数 k 产生 2k 瓣

#### 1.11 Lemniscate 伯努利双纽线
- **视觉**：无限符号(∞)形状，粒子拖尾 + 呼吸缩放
- **场景**：无限循环概念、持续处理中
- **JS**：x = a·cos(t)/(1+sin²t)，y = a·sin(t)·cos(t)/(1+sin²t)
- **要点**：不需要旋转，双纽线自身形态已经足够动态

#### 1.12 Four-Petal Spiral 四瓣内旋轮线
- **视觉**：R=4,r=1,d=3 的内旋轮线，四瓣花形 + 旋转 + 呼吸
- **场景**：复杂运算加载、高端品牌
- **JS**：x=(R-r)·cos(t)+d·cos((R-r)/r·t)，hypotrochoid 公式
- **要点**：R 值决定花瓣数，d 值影响花瓣大小

#### 1.13 Wave Bars 音频波形
- **视觉**：竖条高低交替跳动，像音频波形/均衡器
- **场景**：音频播放中、语音识别中
- **CSS**：`animation: waveBar 1.2s ease-in-out infinite` + 每条不同 `animation-delay`
- **要点**：4-5 条即可，高度用 `scaleY` 变化

#### 1.14 Typing Indicator 输入提示
- **视觉**：三个圆点依次上下跳动
- **场景**：聊天对话"对方正在输入"
- **CSS**：`animation: typingDot 1.4s ease-in-out infinite` + 每点延迟 0.2s
- **要点**：背景加圆角气泡框效果更好

#### 1.15 Hourglass Rotate 沙漏翻转
- **视觉**：沙漏 SVG 每隔一段时间翻转 180°
- **场景**：等待处理、排队中
- **CSS**：`animation: hourglassFlip 2s ease-in-out infinite`
- **要点**：SVG 描边风格比填充更精致
