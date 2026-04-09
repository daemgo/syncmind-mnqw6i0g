# 输出规则

## JSON 写入规则

写入路径：`docs/customer/sales-guide.json`

### 写入策略

- **首次写入**：创建完整 JSON
- **迭代写入**：只覆盖有变化的字段
- **始终更新**：metadata.generatedAt（首次）/ metadata.updatedAt（迭代）、metadata.version
- **UTF-8 编码**，JSON 缩进 2 个空格

### interviewGuide 同步规则

`interviewGuide.fromRequirements` 从 `requirements.json` 的 `current.pendingQuestions[]` 筛选：
- 只取 status=pending 或 partially-answered 的问题
- 保留 questionId、stage、question、priority、status 字段
- 按 stage 分组：screening → deep-dive → closing
- requirements.json 不存在时输出空数组

`tracking` 基于 requirements.json 的全部 pendingQuestions 计算（含已回答的），反映问题整体覆盖进度。

### humanizer-zh 处理清单

| 字段路径 | 处理重点 |
|----------|---------|
| timing.entryStrategy | 具体可执行，不泛泛 |
| competitors[].counterStrategy | 像有经验的销售在教新人 |
| nextActions[].action | 具体到可执行 |
