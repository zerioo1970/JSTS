# JSTS

为 React 19 开发做准备的 JavaScript / TypeScript 学习资料。

## 学习计划

[React 19 开发所需的 JavaScript + TypeScript 学习计划](./React19-JS-TS-%E5%AD%A6%E4%B9%A0%E8%AE%A1%E5%88%92.md)

| 阶段 | 天数 | 内容 |
| --- | --- | --- |
| 0 | Day 1–2 | 环境、模块系统、心智模型 |
| 1 | Day 3–14 | JavaScript 核心 |
| 2 | Day 15–19 | TypeScript 够用版 |
| 3 | Day 20–21 | 工程化、调试、Git |
| 4 | Day 22 起 | React 19（全程用 TS 写），TS 进阶穿插其中 |

**21 天打完 JS + TS + 工程化基础，第 22 天起进入 React 19（约 6 周）。** 每天 2 小时。

计划按「从常用到很少用」排序，每个概念点带频率标记（★★★ 每天用 / ☆ 认得就行），含 C# / WebForm 对照速查表和进度记录表。

## 每日教程

按天展开的详细教程，可直接照着做。

| Day | 教程 | 主题 |
| --- | --- | --- |
| 1 | [Day 1 — 工具链](./Day%201%20%E2%80%94%20%E5%B7%A5%E5%85%B7%E9%93%BE.md) | Node.js · npm / package.json · Vite · VS Code · DevTools |
| 2 | [Day 2 — 模块系统 + 心智模型](./Day%202%20%E2%80%94%20%E6%A8%A1%E5%9D%97%E7%B3%BB%E7%BB%9F%20%2B%20%E5%BF%83%E6%99%BA%E6%A8%A1%E5%9E%8B.md) | `import` / `export` · 循环依赖 · 单线程事件循环 · 编译期 vs 运行期 · `UI = f(state)` |
| 3 | [Day 3 — 变量、原始类型、引用相等](./Day%203%20%E2%80%94%20%E5%8F%98%E9%87%8F%E3%80%81%E5%8E%9F%E5%A7%8B%E7%B1%BB%E5%9E%8B%E3%80%81%E5%BC%95%E7%94%A8%E7%9B%B8%E7%AD%89.md) | `const` / `let` · **金额精度与整数分方案** · `bigint` 主键陷阱 · `null` vs `undefined` · **`Object.is` 与不可变更新的成因** |
| 4 | [Day 4 — 字符串、运算符、真值假值](./Day%204%20%E2%80%94%20%E5%AD%97%E7%AC%A6%E4%B8%B2%E3%80%81%E8%BF%90%E7%AE%97%E7%AC%A6%E3%80%81%E7%9C%9F%E5%80%BC%E5%81%87%E5%80%BC.md) | 模板字符串 · 中文排序 · **`&&` 渲染出 `0` 的两条成因** · **`??` vs `\|\|`** · `?.` · 依赖数组为何要放原始值 |

> 教程中的所有数值输出均经 Node.js 24 实测核对。

## 说明

- 面向有 20 年 C# ASP.NET WebForm + SQL Server 经验、JS / TS 零基础的读者，全程带 .NET 侧对照
- 版本基准：React 19.2 · TypeScript 7.0 · Node.js 24 LTS · Vite 8（2026 年 7 月）
