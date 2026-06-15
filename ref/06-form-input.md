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
