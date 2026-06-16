# Output Format

输出最终方案前读取本文件。不要把本文件当知识库读取入口；动效细节必须来自相关 `ref/*.md`。

## 代码模式

用户在做 UI、Web、App、前端页面或产品功能时，默认使用代码模式。

```markdown
## 推荐：[动效名称]

**解决什么问题：** 用产品语言说明，不写术语堆砌。
**适合场景：** Web / iOS / Android / 通用

### 实现代码
（优先使用 CSS；只有交互状态需要时再补充必要 JS）

### 可调参数
| 参数 | 默认值 | 改了会怎样 |
| --- | --- | --- |

### 无障碍适配
包含 `@media (prefers-reduced-motion: reduce) { ... }`
```

### 代码输出规则

- 代码必须能独立复制使用，除非用户要求接入现有项目文件。
- 动画参数必须来自相关 `ref/*.md`，不要凭记忆编。
- 组合动效最多推荐 3 个；每个动效说明为什么需要。
- 所有动画都要提供 `prefers-reduced-motion` 降级。
- 如果 JS 只是为了添加/移除状态类，保持最小实现。

## 视频模式

用户明确提到 AI 视频、motion prompt、镜头、生成视频、Sora、Runway、可灵、即梦等视频工具时，使用视频模式。

```markdown
## Motion Prompt

[English prompt describing subject, movement, timing, easing, camera, and mood.]

## 中文说明

解释这个 prompt 表达的动效节奏、镜头和使用场景。
```

### 视频 prompt 规则

- 用英文写 prompt，中文解释。
- 描述运动方式、时长感、节奏、镜头和材质。
- 不输出网页实现代码，除非用户同时要求网页实现。
