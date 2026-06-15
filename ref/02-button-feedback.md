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
