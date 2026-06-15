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
