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
