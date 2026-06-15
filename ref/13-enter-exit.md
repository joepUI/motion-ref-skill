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
