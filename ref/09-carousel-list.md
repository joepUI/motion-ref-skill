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
