<!-- 隐式触发：图表/流程图/Logo/数据可视化/落地页/信息图/图标 -->
# 数据可视化 / Logo / 流程图 参考

## 数据可视化

- **Edward Tufte 原则**：最大化数据墨水比，最小化 chartjunk
- 网格线淡化（#E5E5E5 或更浅）
- 颜色 ≤ 5 色（超过用 pattern）
- 数字直接标在图上（少用 legend）
- Y 轴从 0 开始（柱状图）
- **必避**：3D 效果 / 彩虹色 / 饼图 > 5 块 / 双 Y 轴 / Y 轴截断 / emoji 阴影渐变
- **工具**：D3.js / ECharts / Recharts / Visx / Observable Plot / Vega-Lite
- **资源**：Information is Beautiful Awards / FlowingData / Observable

## Logo / 品牌

- 黑白单色 + 彩色两版本
- 横版 + 竖版 + 字符标三版本
- 最小可识别尺寸测试（16×16 favicon）
- **必避**：渐变（除非品牌需要）/ 复杂插画（缩小看不清）/ 多色（> 3 色）/ 字体过细
- **工具**：Figma / Illustrator / Inkscape / Ideogram / Recraft
- **资源**：LogoArchive（5000+）/ Brand New / LogoMoose

## 流程图 / 架构图

- **方向一致**（LR / TD 二选一）
- 节点 ≤ 12 个（多了就分层）
- 颜色编码：输入 / 处理 / 输出 三色
- **必避**：节点过多（> 20）/ 箭头方向混乱 / 交叉线 / 滥用 3D 节点
- **工具**：mermaid（推荐）/ Graphviz / PlantUML / D2 / Excalidraw

## 仪表盘 / Dashboard

- **F 型阅读**：左上 = 核心 KPI，右下 = 详情
- 信息密度高但层级清晰
- 数字字号最大
- 图表用色 ≤ 3 色
- 时间范围 / 筛选器顶部固定
- **必避**：3D 饼图 / 彩虹色 / Y 轴不从 0 开始 / 表格列宽不固定 / 色盲不友好
- **工具**：shadcn/ui + Recharts / ECharts / D3.js / Tremor / Metabase

## 落地页 / Landing

- Hero 区：标题 + 副标题 + CTA + 截图（不绝对居中）
- 单一 CTA 主色
- 区块之间留白 ≥ 80px
- 社会证明：客户 Logo + 数据 + 评价
- **必避**：废话标题（"Empower your business"）/ 假数据 / CTA > 3 个 / 表单 > 5 个 / 弹窗骚扰
- **工具**：shadcn/ui + Next.js / Astro / Framer / Tailwind UI

## 通用载体自检

- [ ] 数据墨水比 > 50%（图表）
- [ ] 色盲友好
- [ ] Y 轴从 0 开始
- [ ] 图说 + 数据来源
- [ ] 节点 ≤ 12（流程图）
- [ ] Hero 1 个 CTA（落地页）
