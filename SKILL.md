---
name: motion-ref
slug: motion-ref
version: 2.1.0
description: "UI 动效参考库，帮你给产品加上合适的动画。不需要懂动效 — 描述你的产品场景（页面加载慢、用户点了没反应、想让页面高级一点），直接推荐方案 + 代码。触发词：页面没动画、交互没反馈、怎么加动效、让页面动起来、加载太慢怎么办、想让产品高级一点、motion ref。"
---

# Motion Ref — 产品动效方案库

## 你的角色

用户不懂动效，你来帮他们选。他们会描述产品场景（"提交按钮点了没反应""首页加载白屏""想让落地页高级一点"），你从下方参考表中匹配 1-3 个最合适的动效，输出可直接使用的代码。

不要默认用户懂动画术语。他们说"转一下"可能是 spinner 也可能是 3D 翻转，先确认场景再推荐。

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
- **场景清晰**（"用户下单后要等3秒"）→ 直接推荐 + 完整代码
- **场景模糊**（"让页面有质感"）→ 展示 2-3 个方向让用户选
- **组合需求**（"弹窗弹出时底部页面变暗变模糊"）→ 推荐动效组合

## 产品场景速查

用户描述产品问题，直接匹配方案：

### 等待与加载
| 产品场景 | 推荐方案 | 参考编号 |
|---------|---------|---------|
| 页面首次打开，数据没加载出来 | Skeleton Shimmer + Stagger 入场 | 1.3 + 13.5 |
| 按钮点了在等接口返回 | Submit Loading（按钮变菊花） | 2.5 |
| 后台处理要几秒 | Spinner 或 Breath Pulse | 1.1 / 1.6 |
| 文件上传/下载进度 | Progress Bar 或 Circular Progress | 1.4 / 1.5 |
| 聊天等对方回复 | Typing Indicator（三点跳动） | 1.11 |
| 语音识别中/音乐播放中 | Wave Bars（音频波形） | 1.10 |

### 操作反馈
| 产品场景 | 推荐方案 | 参考编号 |
|---------|---------|---------|
| 用户点按钮没反应感 | Press Scale（按压缩小） | 2.1 |
| 操作成功了想告诉用户 | Success Check（打勾）+ Toast | 2.3 + 4.5 |
| 重要操作成功想庆祝一下 | Confetti（粒子爆发）+ Success Check | 2.9 + 2.3 |
| 密码输错了/表单校验失败 | Error Shake + 输入框变红 | 2.4 + 6.3 |
| 危险操作需要二次确认 | Fill Progress（长按填充） | 2.8 |
| 复制成功了想告诉用户 | Copy Check（图标变勾） | 8.9 |

### 页面与内容
| 产品场景 | 推荐方案 | 参考编号 |
|---------|---------|---------|
| 页面内容平铺太死板 | Scroll Reveal（滚动渐现） | 7.1 |
| 列表/卡片一次加载多个 | Stagger（依次入场） | 13.5 |
| 长文章想显示阅读进度 | Progress Indicator（顶部进度条） | 7.2 |
| 页面之间跳转生硬 | Page Slide 或 Fade Switch | 5.1 / 5.2 |
| 数据面板数字想动起来 | Number Counter（数字滚动） | 3.3 |
| Dashboard 图表入场 | Bar Chart Rise + Counter Card | 12.1 + 12.5 |

### 弹窗与浮层
| 产品场景 | 推荐方案 | 参考编号 |
|---------|---------|---------|
| 需要一个确认弹窗 | Modal（缩放淡入） | 4.1 |
| 移动端底部操作菜单 | Bottom Sheet（底部滑入） | 4.2 |
| 点击出现选项菜单 | Dropdown 或 Context Menu | 4.3 / 4.7 |
| 操作结果轻提示 | Toast（顶部/底部滑入） | 4.5 |
| Cmd+K 搜索框 | Command Palette | 4.10 |

### 表单与输入
| 产品场景 | 推荐方案 | 参考编号 |
|---------|---------|---------|
| 输入框聚焦没感觉 | Focus Ring + Label Float | 6.1 + 6.2 |
| 开关/选项切换 | Toggle Switch（弹性滑动） | 6.4 |
| 验证码输入框 | OTP Input（自动跳格） | 6.8 |
| 注册/结账多步骤 | Step Indicator（步骤圆点） | 6.10 |

### 提升质感
| 产品场景 | 推荐方案 | 参考编号 |
|---------|---------|---------|
| 落地页想要高级感 | Gradient Flow + Light Sweep + Scroll Reveal | 11.1 + 11.6 + 7.1 |
| 暗色主题按钮想突出 | Hover Glow + Glow Pulse | 2.6 + 11.2 |
| 卡片悬浮想要交互感 | 3D Card Hover 或 Glow Trace | 11.7 / 11.5 |
| 品牌Logo入场 | Logo Entrance（描边+填充） | 8.5 |
| 背景想有动态感 | Gradient Flow 或 Particles | 11.1 / 11.3 |
| 有通知想引起注意 | Bell Shake + Badge Bounce | 8.10 + 8.4 |

## 匹配策略

当场景速查表没有覆盖到时，按以下步骤匹配：

### 第一步：从用户描述中提取意图

| 用户可能说的话 | 真实意图 | 搜索分类 |
|-------------|---------|---------|
| "加载慢""白屏""等待""转圈" | 缓解等待焦虑 | 1. 加载与等待 |
| "点了没反应""没反馈""不知道有没有成功" | 操作反馈缺失 | 2. 按钮与点击反馈 |
| "数字想动起来""文字太静了""倒计时" | 数据/文字动态化 | 3. 文字与数据 |
| "弹窗""菜单""提示""toast" | 浮层出入场 | 4. 弹层与浮层 |
| "页面跳转""切换""tab" | 页面转场 | 5. 导航与转场 |
| "输入框""表单""开关""步骤" | 表单交互 | 6. 表单与输入 |
| "滚动""往下拉""读到哪了" | 滚动交互 | 7. 滚动驱动 |
| "图标""菜单按钮""通知""小红点" | 图标微动效 | 8. 图标与标识 |
| "列表""轮播""拖拽""左滑删除" | 列表交互 | 9. 轮播与列表 |
| "暗色模式""状态变化""在线离线" | 状态切换 | 10. 状态切换 |
| "高级感""质感""科技感""背景" | 氛围提升 | 11. 氛围与背景 |
| "图表""仪表盘""数据展示" | 数据可视化 | 12. 数据可视化 |
| "出现""消失""入场""列表加载" | 元素出入场 | 13. 入场与退场 |

### 第二步：在对应分类中按场景匹配

### 第三步：输出方案

```
## 推荐：[动效名称]

**解决什么问题：** 一句话，用产品语言说明
**适合场景：** Web / iOS / Android / 通用

### 实现代码
（完整可用的 CSS + JS 代码）

### 可调参数
| 参数 | 默认值 | 改了会怎样 |
|------|-------|-----------|

### 无障碍适配
@media (prefers-reduced-motion: reduce) { ... }
```

---

## 动效参考表

匹配到分类后，读取对应的 ref/ 文件获取详细实现参考：

| 分类 | 文件 | 包含效果 |
|-----|------|---------|
| 1. 加载与等待 | `ref/01-loading.md` | Spinner、Dots Pulse、Skeleton、Progress Bar、Breath Pulse 等 12 个 |
| 2. 按钮与点击反馈 | `ref/02-button-feedback.md` | Press Scale、Ripple、Success Check、Error Shake、Confetti 等 9 个 |
| 3. 文字与数据 | `ref/03-text-data.md` | Typewriter、Number Counter、Flip Counter、Shimmer Text 等 10 个 |
| 4. 弹层与浮层 | `ref/04-overlay.md` | Modal、Bottom Sheet、Dropdown、Toast、Command Palette 等 10 个 |
| 5. 导航与转场 | `ref/05-navigation.md` | Page Slide、Shared Element、Tab Slide、Dock Nav 等 7 个 |
| 6. 表单与输入 | `ref/06-form-input.md` | Focus Ring、Toggle Switch、OTP Input、Range Slider 等 10 个 |
| 7. 滚动驱动 | `ref/07-scroll.md` | Scroll Reveal、Progress Indicator、Sticky Shrink 等 5 个 |
| 8. 图标与标识 | `ref/08-icon.md` | Hamburger、SVG Draw、Heart Like、Bell Shake 等 10 个 |
| 9. 轮播与列表 | `ref/09-carousel-list.md` | Carousel、Card Stack、Drag Reorder、Swipe Action 等 8 个 |
| 10. 状态切换 | `ref/10-state.md` | Theme Toggle、Error→Recovery、Online Status、Favorite Star 等 8 个 |
| 11. 氛围与背景 | `ref/11-ambient.md` | Gradient Flow、Particles、Glow Trace、3D Card Hover 等 7 个 |
| 12. 数据可视化 | `ref/12-data-viz.md` | Bar Chart、Donut Chart、Gauge Meter、Sparkline 等 5 个 |
| 13. 入场与退场 | `ref/13-enter-exit.md` | Fade In、Slide Up、Spring In、Stagger、Blur In 等 8 个 |

**指令：匹配到分类后，用 Read 工具读取对应 ref/ 文件，获取具体效果的视觉描述、CSS/JS 实现和要点，然后按输出格式回复用户。不要凭记忆编写动效参数，必须从 ref 文件中读取。**
