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
