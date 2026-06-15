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
