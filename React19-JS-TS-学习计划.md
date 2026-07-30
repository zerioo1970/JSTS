# React 19 开发所需的 JavaScript + TypeScript 学习计划

> **适用对象**：有 20 年 C# ASP.NET WebForm + SQL Server 开发经验，JS / TS 零基础
> **投入**：每天 2 小时
> **总量**：28 天 × 2 小时 = 56 小时（按工作日算约 6 周，天天学约 4 周）
> **目标**：覆盖 React 19 日常开发用得到的全部 JS / TS 内容，之后可直接进入 React 学习
> **版本基准**：React 19.2 / TypeScript 7.0（2026 年 7 月）

---

## 目录

- [一、计划总览](#一计划总览)
- [二、每天 2 小时怎么用](#二每天-2-小时怎么用)
- [三、频率标记说明](#三频率标记说明)
- [阶段 0：环境与模块（Day 1–2）](#阶段-0环境与模块day-12)
- [阶段 1：JavaScript 核心（Day 3–14）](#阶段-1javascript-核心day-314)
- [阶段 2：TypeScript（Day 15–24）](#阶段-2typescriptday-1524)
- [阶段 3：工程化（Day 25–28）](#阶段-3工程化day-2528)
- [附录 A：Day 29 起的 React 19 顺序](#附录-aday-29-起的-react-19-顺序预告)
- [附录 B：可以永远不学的清单](#附录-b可以永远不学的清单)
- [附录 C：C# / WebForm 对照速查表](#附录-cc--webform-对照速查表)
- [附录 D：进度记录表](#附录-d进度记录表)

---

## 一、计划总览

| 阶段 | 天数 | 内容 | 交付物 |
| --- | --- | --- | --- |
| 0 | Day 1–2 | 环境、模块系统、心智模型 | 能跑起来的 Vite 空项目 |
| 1 | Day 3–14 | JavaScript 核心（12 天） | 纯 JS 写的"待办清单 + 天气查询"控制台程序 |
| 2 | Day 15–24 | TypeScript（10 天） | 把阶段 1 的代码全部改写成 `.ts`，零 `any` |
| 3 | Day 25–28 | 工程化、调试、代码规范 | 配好 ESLint / Prettier / 路径别名的项目模板 |
| — | Day 29+ | 正式进入 React 19 | — |

---

## 二、每天 2 小时怎么用

| 时长 | 做什么 |
| --- | --- |
| 25 分钟 | 读当天概念（看文档 / 教程，不抄代码） |
| 75 分钟 | **手敲**练习。不许复制粘贴，不许让 AI 代写 |
| 20 分钟 | 复盘：把当天概念用自己的话写一句总结，记下没懂的点 |

### 三条铁律

1. **每个概念必须在浏览器控制台里亲手跑一遍**，看到输出才算学会。看视频不算。
2. **不懂就先记下、继续往下走**，不要卡在一个点上超过 20 分钟。很多概念要到 React 阶段才会「啊原来是这个意思」。
3. **阶段 1 只写 `.js`，不碰类型**。先建立运行时直觉，类型是第二层。

---

## 三、频率标记说明

| 标记 | 含义 |
| --- | --- |
| ★★★ | 每天都写，必须闭着眼能写出来 |
| ★★ | 每周都会遇到，要熟 |
| ★ | 偶尔遇到，知道怎么查 |
| ☆ | 读别人代码时要认得出来，自己基本不写 |
| ✕ | 禁用 |

---

# 阶段 0：环境与模块（Day 1–2）

## Day 1 — 工具链

- [ ] **Node.js** ★★★：装 LTS 版本。它是什么（JS 的运行时，类比 .NET Runtime），为什么前端开发要装它
- [ ] **npm** ★★★
  - `package.json` 的结构
  - `dependencies` vs `devDependencies`（类比 NuGet 的运行时依赖 vs 开发依赖）
  - 语义化版本 `^1.2.3` / `~1.2.3` / 精确版本 的区别
  - `package-lock.json` 的作用（为什么必须提交到 Git）
  - `node_modules`（为什么绝不提交）
  - `npm install` / `npm run` / `npx`
- [ ] **Vite** ★★★：`npm create vite@latest` 建项目、`npm run dev` / `npm run build`、什么是 HMR 热更新
- [ ] **VS Code** ★★★：装 ESLint、Prettier 扩展；`Ctrl+P` 快速打开文件、`F12` 跳转定义
- [ ] **浏览器 DevTools** ★★★：Console 面板执行代码、Sources 打断点单步、Network 看请求

## Day 2 — 模块系统 + 心智模型

### ESM 模块 ★★★（每个文件第一行都是它）

- [ ] `export` 命名导出 / `export default` 默认导出
- [ ] `import { a, b } from './x.js'` / `import X from './x.js'`
- [ ] `import { a as b }` 重命名、`import * as ns`
- [ ] 相对路径 `./` `../` vs 包名 `react`
- [ ] **和 C# 的根本差别**：没有 `namespace`，没有 dll，没有 `using`。文件路径就是模块标识，一个文件就是一个模块，模块内的东西默认私有
- [ ] 循环依赖是什么、为什么要避免
- [ ] ☆ `import()` 动态导入（React 懒加载会用到）
- [ ] ☆ CommonJS `require`（老代码里会见到，自己别写）

### JS 运行模型 ★★★（理解就好，不用背）

- [ ] 解释执行 / JIT，没有独立的编译步骤
- [ ] **单线程 + 事件循环**：一个线程跑所有代码，异步靠排队。所以没有锁、没有 `lock`、没有线程安全问题，但也不能有阻塞操作
- [ ] 编译期（TS 检查、打包）vs 运行期（浏览器执行）

### React 的核心思想 ★★★（先建立，后面反复回味）

- [ ] `UI = f(state)`。你永远不「改界面」，只改数据，界面自己重算
- [ ] 和 WebForm 的对比：没有回发（PostBack）、没有 ViewState、没有服务器控件、没有 `Page_Load`

---

# 阶段 1：JavaScript 核心（Day 3–14）

## Day 3 — 变量、原始类型

### `let` / `const` ★★★

- [ ] 一律用 `const`，需要重新赋值才用 `let`
- [ ] **`var` 永远不用**（作用域规则有历史缺陷）
- [ ] 块级作用域 `{}`
- [ ] `const` 只锁住「绑定」，不锁住内容：`const arr = []; arr.push(1)` 是合法的（类比 C# `readonly` 字段）
- [ ] ☆ TDZ（暂时性死区）—— 只需知道「变量声明前不能用」

### 7 种原始类型 ★★★

- [ ] `string` `number` `boolean` `null` `undefined` `symbol` `bigint`

### `number` 只有一种 ★★★

- [ ] 没有 `int` / `long` / `double` / `decimal`，全是 64 位浮点
- [ ] `0.1 + 0.2 !== 0.3` —— **涉及金额务必用整数分或专门库**（做业务系统的关键点）
- [ ] `NaN`、`Infinity`、`Number.isNaN()`、`Number.isInteger()`
- [ ] 字符串转数字：`Number('1')` / `parseInt('1px')` / `parseFloat` / 一元 `+'1'`
- [ ] `toFixed(2)`（**返回字符串**，不是数字）

### `null` vs `undefined` ★★★

- [ ] `undefined` = 从没赋值 / 没这个属性 / 函数没返回
- [ ] `null` = 明确表示「空」，通常来自后端数据或你主动赋值
- [ ] 实务约定：自己写代码尽量只用 `undefined`，`null` 交给 API 数据

### 其他

- [ ] **`typeof`** ★★★ 及其经典坑：`typeof null === 'object'`
- [ ] **值传递 vs 引用传递** ★★★：原始类型传副本；对象 / 数组 / 函数传引用。**这是 React 的地基** —— React 靠「引用变没变」决定是否重新渲染
- [ ] ☆ 自动装箱：为什么 `'abc'.toUpperCase()` 能对一个原始值调方法

## Day 4 — 字符串、运算符、真值假值

### 字符串 ★★★

- [ ] 模板字符串：`` `你好 ${name}，共 ${a + b} 元` ``、天然支持多行
- [ ] 常用方法：`length` `includes` `startsWith` `endsWith` `slice` `split` `join` `trim` `replace` `replaceAll` `toUpperCase` `toLowerCase` `padStart` `at(-1)` `indexOf`
- [ ] 字符串不可变：所有方法都返回新字符串，原串不变（同 C#）

### 运算符与真值假值 ★★★

- [ ] **`===` 与 `==`**：**一律用 `===`**，`==` 会做隐式类型转换（`'' == 0` 是 `true`）
- [ ] **假值（falsy）全表** —— 背下来，只有这 6 个（外加 `document.all`）
      `false` · `0` · `-0` · `''`（空串） · `null` · `undefined` · `NaN`
      **注意 `'0'`、`'false'`、`[]`、`{}` 都是真值**（`[]` 是真值，和直觉相反）
- [ ] **`&&` `||` 的返回值不是布尔**：短路求值，`a && b` 返回的是 `a` 或 `b` 本身
      **React 头号 bug**：`{count && <div/>}` 当 `count === 0` 时页面上会真的显示一个 `0`。正确写法 `{count > 0 && <div/>}`
- [ ] **`??` 空值合并**：只在左侧为 `null` / `undefined` 时取右侧
      **和 `||` 的关键区别**：`0 || 10` 得 `10`（错），`0 ?? 10` 得 `0`（对）。默认值场景一律用 `??`
- [ ] **`?.` 可选链**：`user?.address?.city`、`arr?.[0]`、`fn?.()`
- [ ] **三元运算符** `条件 ? a : b` —— JSX 里条件渲染的主力（JSX 中不能写 `if`）
- [ ] ★★ `??=` `||=` `&&=`
- [ ] ★★ `!!x` 转成真布尔值
- [ ] ★ `in`、`instanceof`、`delete`
- [ ] ☆ `void`、逗号运算符、位运算 `& | ^ << >>`

## Day 5 — 函数（上）

### 三种写法 ★★★

- [ ] `function f() {}` 函数声明（会提升）
- [ ] `const f = function() {}` 函数表达式
- [ ] `const f = () => {}` **箭头函数（React 里的默认选择）**

### 箭头函数细节 ★★★

- [ ] 单表达式可省 `return` 和 `{}`：`(x) => x * 2`
- [ ] **返回对象字面量必须加括号**：`() => ({ id: 1 })`，否则 `{}` 被当成函数体
- [ ] 单参数可省括号（团队通常仍要求写括号）

### 参数 ★★★

- [ ] 默认参数：`function f(a = 1) {}`
- [ ] 剩余参数：`function f(...args) {}`
- [ ] **参数解构 + 默认值**：`function Card({ title, size = 'md' }) {}` —— React 组件接收 props 的标准写法，必须写熟
- [ ] JS 没有方法重载，没有 `ref` / `out` 参数，没有命名参数（用对象参数模拟）

### 函数是一等公民 ★★★

- [ ] 可以赋值给变量、作为参数传递、作为返回值
- [ ] **回调函数**：`arr.map(fn)`、`onClick={fn}`
- [ ] **高阶函数**：接收或返回函数的函数
- [ ] 类比 C# 的 `Func<>` / `Action<>` / lambda，但 JS 里更随意
- [ ] **纯函数**：同样输入必有同样输出、不修改外部状态。**React 组件必须是纯函数**，这是硬要求

## Day 6 — 函数（下）：闭包

> **今天只学一个概念，但它是整个 React Hooks 的地基，值得花满 2 小时。**

### 闭包 ★★★

- [ ] 定义：函数记住了它被创建时所在的作用域
- [ ] 手写练习：计数器工厂 `makeCounter()`、私有变量、防抖 `debounce`
- [ ] 类比 C# lambda 捕获局部变量，但 JS 里用得频繁得多
- [ ] **在 React 里的意义**：`useState` 返回的 `count` 是这一次渲染被「冻结」的值。每次渲染产生全新的一套变量和函数
- [ ] **stale closure（过期闭包）**：`useEffect` 里读到旧值 —— React 新手第二号 bug。今天先建立概念，React 阶段会反复遇到

### `this` ★（React 函数组件里几乎用不到，但要知道）

- [ ] 普通函数的 `this` 取决于**怎么调用**，不是在哪定义
- [ ] 箭头函数没有自己的 `this`，继承外层
- [ ] 这曾是 React class 组件的巨大痛点（满屏 `.bind(this)`），函数组件已彻底绕开

### 其他

- [ ] ★ 立即执行、递归
- [ ] ☆ `call` / `apply` / `bind`、`arguments`、函数提升

## Day 7 — 对象

### 创建与访问 ★★★

- [ ] 字面量 `{ a: 1, b: 2 }`
- [ ] 属性简写：`{ name, age }` 等价于 `{ name: name, age: age }`
- [ ] 计算属性名：`{ [key]: value }`（动态字段名，表单处理常用）
- [ ] `.` 访问 vs `[]` 访问（字段名是变量时用 `[]`）
- [ ] 方法简写：`{ greet() {} }`

### 解构 ★★★

- [ ] 基础：`const { a, b } = obj`
- [ ] 重命名：`const { a: x } = obj`
- [ ] 默认值：`const { a = 1 } = obj`
- [ ] 嵌套：`const { user: { name } } = data`
- [ ] 剩余：`const { id, ...rest } = obj`

### 展开运算符 `...` ★★★

- [ ] 合并 / 覆盖：`{ ...defaults, ...overrides }`（**后面的覆盖前面的**）
- [ ] 复制：`{ ...obj }`
- [ ] **这就是 React 状态更新的主力手段**

### 浅拷贝 vs 深拷贝 ★★★

- [ ] `{...obj}` 只拷一层，嵌套对象仍是同一个引用
- [ ] `structuredClone(obj)` 深拷贝（现代浏览器原生支持）
- [ ] 为什么不要用 `JSON.parse(JSON.stringify(x))`（丢 `Date`、`undefined`、函数）

### 不可变更新对象 ★★★（React 必背）

- [ ] 改一个字段：`{ ...user, name: '张三' }`
- [ ] 改嵌套字段：`{ ...user, address: { ...user.address, city: '上海' } }`
- [ ] 为什么不能 `user.name = '张三'`

### 其他

- [ ] ★★ `Object.keys` / `values` / `entries` / `assign` / `fromEntries` / `freeze`
- [ ] ★★★ `JSON.stringify(obj, null, 2)` / `JSON.parse(str)`、哪些值不可序列化
- [ ] ★ 可选属性、`delete`、属性遍历顺序
- [ ] ☆ getter / setter、`Object.defineProperty`

## Day 8 — 数组（一）：读与变换

> 数组是 React 里最核心的一块，安排两天。

- [ ] **基础** ★★★：字面量、索引、`length`、`at(-1)` 取最后一个、`Array.isArray()`
- [ ] **`map`** ★★★ —— **React 渲染列表 100% 靠它**
  - `items.map(item => <li key={item.id}>{item.name}</li>)`
  - 返回新数组，长度不变；回调的第二个参数是索引
- [ ] **`filter`** ★★★：筛选，返回新数组
- [ ] **`find` / `findIndex`** ★★★：找第一个匹配项 / 它的下标
- [ ] **`some` / `every`** ★★★：有没有任一 / 是否全部满足
- [ ] **`reduce`** ★★：求和、分组、转对象。初学者最难的一个，值得多练 3 个例子
- [ ] **`sort`** ★★ —— **两个大坑**
  - 默认按**字符串**排序：`[10, 9, 1].sort()` 得 `[1, 10, 9]`。数字必须传比较函数 `(a, b) => a - b`
  - **`sort` 会原地修改原数组**，React 里必须 `[...arr].sort(...)` 或 `arr.toSorted(...)`
- [ ] **`includes` / `indexOf` / `join` / `flat` / `flatMap` / `reverse`** ★★
- [ ] **`slice`（不改原）vs `splice`（改原）** ★★ —— 名字像、行为完全不同，务必区分
- [ ] **`forEach`** ★★：只做副作用时用；要产出新数组用 `map`；不能 `break`（要提前退出用 `for...of`）
- [ ] **`Array.from`** ★：`Array.from({ length: 5 }, (_, i) => i)`
- [ ] **数组解构** ★★★：`const [a, b] = arr`、跳过 `const [, second] = arr`、剩余 `const [head, ...tail] = arr`
  - **`useState` 返回的就是数组，靠解构接收**：`const [count, setCount] = useState(0)`

## Day 9 — 数组（二）：不可变更新五式

> React 必背。今天全部手写一遍。

| 操作 | 写法 |
| --- | --- |
| 增（尾部） | `[...arr, newItem]` |
| 增（头部） | `[newItem, ...arr]` |
| 删 | `arr.filter(x => x.id !== id)` |
| 改 | `arr.map(x => x.id === id ? { ...x, done: true } : x)` |
| 插入到 i | `[...arr.slice(0, i), newItem, ...arr.slice(i)]` |
| 排序 | `[...arr].sort(cmp)` 或 `arr.toSorted(cmp)` |

- [ ] **禁用的原地修改方法** ★★★：`push` `pop` `shift` `unshift` `splice` `sort` `reverse`
      在 React 状态上用了，**界面不会刷新**
- [ ] **ES2023 不可变新方法** ★★：`toSorted` `toReversed` `toSpliced` `with(i, v)` —— 现代环境可直接用，比展开写法清爽
- [ ] **`key` 的概念** ★★★：为什么列表每项要唯一 `key`、为什么**不要用数组下标当 key**（列表增删排序时会错乱）
- [ ] **`Set`** ★★：去重、`has` 判存在（比 `includes` 快）
- [ ] **`Map`** ★★：任意类型做键、保持插入顺序、`size`；什么时候该用它们而不是对象 / 数组
- [ ] ★ `for...of` vs `for...in`（**`for...in` 遍历的是键名，用在数组上是错的**）、可迭代协议、`entries()`

## Day 10 — 异步（一）：Promise 与 async/await

- [ ] **同步 vs 异步** ★★★：单线程为什么不会卡死
- [ ] **事件循环（直觉级）** ★★：调用栈 → 微任务队列（Promise）→ 宏任务队列（setTimeout）。做一个「打印顺序」练习题就够
- [ ] **回调地狱 → Promise** ☆：了解历史，看得懂老代码

### `Promise` ★★★

- [ ] 三种状态：pending / fulfilled / rejected
- [ ] `.then()` / `.catch()` / `.finally()`
- [ ] `Promise.resolve()` / `Promise.reject()`
- [ ] ★ 手动 `new Promise((resolve, reject) => {})`（封装老 API 时用）

### `async` / `await` ★★★（日常主力）

- [ ] `async` 函数总是返回 Promise
- [ ] `await` 只能在 `async` 函数里用（顶层 ESM 可以）
- [ ] 和 C# `async/await` 的相同点：写法几乎一样
- [ ] **和 C# 的不同点**：没有 `Task` / `Task<T>` 的区分，没有 `ConfigureAwait`，没有线程池，没有真并行，没有 `async void` 的坑

### 错误处理 ★★★

- [ ] `try` / `catch` / `finally`
- [ ] `throw new Error('msg')`、`Error` 对象的 `message` / `stack` / `cause`
- [ ] ★ 自定义 Error 子类
- [ ] **未捕获的 Promise rejection** 是个常见事故源

### 并发 ★★

- [ ] `Promise.all`（一个失败全失败）
- [ ] `Promise.allSettled`（都等完，各自报告成败）
- [ ] ★ `Promise.race` / `Promise.any`
- [ ] 串行 `await` 循环 vs 并行 `Promise.all(arr.map(...))` 的性能差别

### 定时器 ★★

- [ ] `setTimeout` / `setInterval` / `clearTimeout` / `clearInterval`；写一个 `sleep(ms)` 工具函数

## Day 11 — 异步（二）：fetch 与真实数据

### `fetch` ★★★

- [ ] GET：`const res = await fetch(url)`
- [ ] **`response.ok` 必须手动检查** —— `fetch` 在 404 / 500 时**不会** reject！只有网络层失败才 reject。这是最常被忽略的一点
- [ ] `await res.json()` / `res.text()` / `res.status`
- [ ] POST：`{ method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(data) }`
- [ ] HTTP 状态码常识：200 / 201 / 204 / 400 / 401 / 403 / 404 / 409 / 500
- [ ] 查询参数：`URLSearchParams`

### 其他

- [ ] **`AbortController`** ★★：取消请求。React 的 `useEffect` 清理函数里会用
- [ ] **竞态条件（race condition）** ★★：快速切换筛选条件时，先发的请求后返回，导致显示旧数据。概念先建立，React 阶段用 TanStack Query 解决
- [ ] **CORS 跨域** ★★：概念、为什么本地开发要配 Vite proxy（做企业内部系统一定会撞上）

### 实战

- [ ] 调一个公开 API（如天气或 GitHub API），做完整的「加载中 / 成功 / 失败」三态处理

## Day 12 — 类、原型（认得出就行）

> React 里几乎不写 `class`，但库的源码和错误处理会用到。

### `class` 语法 ★

- [ ] `constructor`、实例字段、方法、`static`、`get` / `set`
- [ ] `#privateField` 私有字段
- [ ] `extends` / `super`、`instanceof`
- [ ] 与 C# 的差别：没有 `interface` 实现声明（TS 才有）、没有属性自动实现、没有重载、没有真正的抽象类（TS 有）

### 其他

- [ ] **原型链** ☆：只需读懂「对象通过 `__proto__` 向上查找属性」，**不要手写 prototype 继承**
- [ ] **`Error` 继承** ★：自定义业务异常类
- [ ] **为什么 React 抛弃了 class 组件** ★★：`this` 绑定麻烦、逻辑无法复用（HOC / render props 的复杂度）、生命周期方法把相关逻辑拆散。Hooks 用闭包解决了这些
- [ ] ☆ `Object.create`、`new` 到底做了什么、`Symbol.iterator`

## Day 13 — 浏览器 API 与 DOM（够用即止）

- [ ] **DOM 是什么** ★★：文档的树形对象模型。**React 替你操作它，你只在极少数情况直接碰**

### 事件模型 ★★★（React 事件基于它）

- [ ] 事件对象、`e.target` vs `e.currentTarget`
- [ ] **冒泡**与捕获
- [ ] `e.preventDefault()`（阻止表单默认提交 —— React 表单必用）
- [ ] `e.stopPropagation()`
- [ ] ★ React 的合成事件与原生事件的关系

### 存储与 URL

- [ ] **`localStorage` / `sessionStorage`** ★★：只能存字符串，配合 `JSON.stringify`；容量限制；同步阻塞
- [ ] **`URL` / `URLSearchParams`** ★★
- [ ] **`window.location` / `history`** ★

### 什么时候才允许直接摸 DOM ★★

- [ ] 合法场景：`useRef` + `focus()`、滚动到某处、集成第三方非 React 库（图表、地图）、测量元素尺寸
- [ ] **非法场景**：用 `document.getElementById` 去修改 React 渲染出来的节点内容。会和 React 打架，且下次渲染就被冲掉

### 其他

- [ ] ★ `FormData`、文件上传、`Blob` / 下载文件、`IntersectionObserver`、`ResizeObserver`
- [ ] ☆ Cookie 操作、`postMessage`、WebSocket、Canvas

## Day 14 — 收口 + 杂项 + 阶段项目

### 日期时间 ★★

- [ ] 原生 `Date` 的坑（月份从 0 开始、解析行为不一致、时区处理糟糕）
- [ ] **实务结论：装 `date-fns`**（轻量、按需引入）
- [ ] `Temporal` 新 API 已开始在浏览器落地，但工作项目里还早，先了解名字

### 格式化与数学

- [ ] **`Intl.NumberFormat`** ★★（金额、千分位）、**`Intl.DateTimeFormat`** ★★ —— 做业务系统天天要用
- [ ] **`Math`** ★★：`round` `floor` `ceil` `max` `min` `abs` `random`
- [ ] **正则表达式基础** ★：`test` / `match` / `replace` / 字符类 / `\d \w \s` / 量词 / 分组。表单校验会用到，不用深挖

### 认得就行 ☆

- [ ] `Symbol`、`generator` / `yield`、`Proxy` / `Reflect`（知道 MobX、Vue 用它做响应式）、标签模板（styled-components 用它）、`WeakMap`、`globalThis`

### 永远不用 ✕

- [ ] `eval`、`with`、`document.write`、`var`、`==`、`arguments`、jQuery

### 阶段 1 项目（占今天大部分时间，可顺延 1–2 天）

- [ ] 一个纯 JS 的待办清单模块：增删改查 + 筛选 + 排序，**全部用不可变更新**
- [ ] 一个天气查询模块：`fetch` + 三态处理 + 错误处理 + `AbortController`
- [ ] 不做界面，全部在控制台里 `console.log` 验证

---

# 阶段 2：TypeScript（Day 15–24）

> C# 底子在这里会让你飞起来 —— TypeScript 和 C# 是同一个人（Anders Hejlsberg）主持设计的。

## Day 15 — TS 是什么 + 基础标注

### 心智模型 ★★★

- [ ] TS **只在编译期存在，运行时被完全擦除**。没有反射、拿不到 `typeof T`、泛型里不能 `new T()`
- [ ] TS 是「极其聪明的 Lint」，不改变任何运行时行为
- [ ] **推论**：外部数据（API 返回、`localStorage`）的类型标注是**你的承诺，不是保证**。后端改字段，TS 不会报错，运行时照样炸

### 工具链 ★★

- [ ] `tsc --noEmit` 做类型检查
- [ ] **Vite 只转译不检查类型！** 必须把 `tsc --noEmit` 单独放进 `npm scripts` 和 CI，否则类型错误会静默溜进生产
- [ ] TypeScript 7 编译器已用 Go 重写，检查速度快约 10 倍，类型语义与 5.x / 6.x 完全一致，所以任何教程都不过时
- [ ] **`tsconfig.json` 最少必要项**：`strict: true`（**必开，不要商量**）、`target` `module` `jsx` `paths`

### 基础标注 ★★★

- [ ] `const n: number = 1`、`let s: string`
- [ ] 数组 `string[]` / `Array<string>`
- [ ] **元组** `[string, number]` —— `useState` 的返回值就是元组
- [ ] 函数：`function f(a: string, b?: number): boolean {}`
- [ ] 对象字面量类型 `{ id: number; name: string }`
- [ ] **优先依赖类型推断，不要过度标注**（`const n = 1` 不用写 `: number`）
- [ ] 什么时候必须手写：函数参数、导出的 API、空数组 `const a: User[] = []`

## Day 16 — 特殊类型 + type vs interface

- [ ] **`any`** ✕：**等于关掉 TS**。团队应开 `no-explicit-any` 规则禁止
- [ ] **`unknown`** ★★★：`any` 的安全替代。用之前必须先收窄
- [ ] **`never`** ★★：不可能的类型；用于穷尽性检查
- [ ] **`void`** ★★：函数无返回值
- [ ] **`null` / `undefined`** ★★★：`strictNullChecks` 下必须显式处理，`string | undefined` 不能直接当 `string` 用

### `type` vs `interface` ★★★

- [ ] 对象形状两者都行
- [ ] **只有 `type` 能写联合类型、元组、映射类型**
- [ ] `interface` 支持声明合并（扩展第三方库类型时用）
- [ ] `interface extends` vs `type &` 交叉
- [ ] 实务约定：**统一用 `type`，需要被外部扩展时用 `interface`**（或者反过来，关键是团队一致）

### 其他

- [ ] **`readonly`** ★★：`readonly string[]`、`Readonly<T>`
- [ ] **`as const`** ★★★：把字面量锁成最窄类型；自定义 Hook 返回元组时必用

## Day 17 — 联合类型与类型收窄（一）

> 这是 C# 里没有的东西，也是 TS 最有价值的部分。安排两天，全部时间投在这。

- [ ] **联合类型** ★★★：`string | number`、`'a' | 'b' | 'c'`
- [ ] **字面量联合替代 `enum`** ★★★
  - `type Status = 'idle' | 'loading' | 'success' | 'error'`
  - 为什么它比 `enum` 好：零运行时代码、可直接与字符串比较、和 JSON 无缝对接
- [ ] **交叉类型** ★★：`A & B`

### 类型收窄（narrowing）★★★ —— TS 最聪明的地方

- [ ] `typeof x === 'string'`
- [ ] `Array.isArray(x)`
- [ ] `x instanceof Date`
- [ ] `'key' in obj`
- [ ] 真值检查 `if (x)`（**注意 `0` 和 `''` 的假值陷阱，用 `if (x !== undefined)` 更准确**）
- [ ] `x === 'literal'` 字面量比较
- [ ] 提前 `return` / `throw` 让后续代码自动收窄
- [ ] 可选链后的收窄
- [ ] **实战**：处理 `catch (e: unknown)`（TS 里 catch 参数就是 `unknown`）

## Day 18 — 联合类型与类型收窄（二）：可辨识联合

### 可辨识联合（discriminated union）★★★ —— 工作里最有用的一招

```ts
type 请求状态<T> =
  | { 阶段: 'idle' }
  | { 阶段: 'loading' }
  | { 阶段: 'success'; 数据: T }
  | { 阶段: 'error'; 错误: string };
```

- [ ] 靠一个公共的字面量字段（这里是 `阶段`）自动收窄
- [ ] **它彻底消灭了「数据有了但还在 loading」这类不可能状态**
- [ ] React 里管理请求状态、`useReducer` 的 action、表单校验结果，全用这个模式

### 穷尽性检查 ★★

```ts
default: {
  const _exhaustive: never = s;
  throw new Error('未处理的状态');
}
```

- [ ] 以后新增一个状态，编译期立刻报错提醒你补分支

### 断言相关

- [ ] **类型谓词** ★★：`function isUser(x: unknown): x is User {}`
- [ ] **断言函数** ★：`function assertIsUser(x: unknown): asserts x is User {}`
- [ ] **类型断言 `as`** ★★：能用收窄就别用 `as`；`as unknown as T` 是投降信号，禁用
- [ ] **非空断言 `!`** ★★：`ref.current!` —— 谨慎，它等于对编译器说「相信我」

### 结构化类型（structural typing）★★★ —— 和 C# 最大的认知差异

- [ ] C# 是名义类型：必须显式 `: IFoo` 才算实现接口
- [ ] TS 是结构类型：**形状对得上就算兼容**，不需要任何继承声明
- [ ] **多余属性检查**：对象**字面量**直接赋值时会额外检查多余属性，但通过变量赋值不会 —— 这个不对称行为要知道
- [ ] ☆ branded types 模拟名义类型：`type UserId = string & { __brand: 'UserId' }`

## Day 19 — 泛型

- [ ] **泛型函数** ★★：`function first<T>(arr: T[]): T | undefined {}`
- [ ] **约束** ★★：`<T extends { id: number }>`
- [ ] **默认类型参数** ★★：`<T = string>`
- [ ] **`keyof`** ★★：`keyof User` 得到 `'id' | 'name'`
- [ ] **索引访问类型** ★★：`User['name']`
- [ ] **类型位置的 `typeof`** ★★：`typeof someObject` —— 从值反推类型，很常用
- [ ] **多个类型参数与推断** ★★：`function pick<T, K extends keyof T>(obj: T, keys: K[]): Pick<T, K>`
- [ ] **泛型接口 / 泛型类型别名** ★★
- [ ] **泛型 React 组件** ★（写通用 `<Table<User>>`、`<Select<T>>` 时用）
- [ ] **与 C# 泛型的差别**：**没有运行时具化**，不能 `new T()`，没有 `where T : new()`，但有 `extends` 约束和强大的类型推断

## Day 20 — 工具类型（日常高频）

- [ ] **对象改造** ★★★：`Partial<T>` `Required<T>` `Readonly<T>` `Pick<T, K>` `Omit<T, K>`
  - `Omit` 是扩展原生组件属性时的主力
- [ ] **构造映射** ★★★：`Record<K, V>`
  - `Record<Status, string>` 做状态到中文文案的映射表，业务系统里天天用
- [ ] **联合运算** ★★：`Exclude<T, U>` `Extract<T, U>` `NonNullable<T>`
- [ ] **从函数取类型** ★★：`ReturnType<typeof f>` `Parameters<typeof f>` `Awaited<T>`
  - `ReturnType<typeof useMyHook>` 复用自定义 Hook 的返回类型
- [ ] **`satisfies`** ★★：既校验又保留精确的推断类型 —— 配置对象的最佳写法
- [ ] **实战**：给一个后端接口写完整的类型定义（DTO、分页包装、枚举字段）

## Day 21 — React + TS（一）：组件与事件

### 组件 props ★★★

```ts
type ButtonProps = {
  label: string;
  onClick: () => void;
  size?: 'sm' | 'lg';
};

function Button({ label, onClick, size = 'sm' }: ButtonProps) { /* ... */ }
```

- [ ] **`children`** ★★★：`children: React.ReactNode`（最宽松、最常用）；`ReactNode` / `ReactElement` / `JSX.Element` 的区别
- [ ] **不要用 `React.FC`** ★★：现在的主流建议是直接标注 props 参数

### 事件类型 ★★★（记住这几个就够 90% 场景）

| 场景 | 类型 |
| --- | --- |
| 输入框 | `React.ChangeEvent<HTMLInputElement>` |
| 点击 | `React.MouseEvent<HTMLButtonElement>` |
| 表单提交 | `React.FormEvent<HTMLFormElement>` |
| 键盘 | `React.KeyboardEvent` |

- [ ] 内联写法可让 TS 自动推断，无需标注：`onChange={(e) => ...}`

### 扩展原生元素属性 ★★

- [ ] `React.ComponentProps<'button'>`
- [ ] `type Props = Omit<React.ComponentProps<'input'>, 'size'> & { label: string }`
- [ ] **`React.CSSProperties`** ★★

## Day 22 — React + TS（二）：Hooks 的类型

- [ ] **`useState`** ★★★
  - 能推断就别标注：`useState(0)`
  - 需要标注的场景：`useState<User | null>(null)`、`useState<string[]>([])`
- [ ] **`Dispatch<SetStateAction<T>>`** ★★：把 setter 往下传时的类型
- [ ] **`useRef`** ★★★
  - DOM 引用：`useRef<HTMLInputElement>(null)`
  - 可变值容器：`useRef<number>(0)`
  - 两者类型行为不同（`RefObject` vs `MutableRefObject`）
- [ ] **React 19：`ref` 就是普通 prop** ★★★ —— **不再需要 `forwardRef`**。老教程里满屏 `forwardRef`，可以直接跳过
- [ ] **`useReducer`** ★★：action 用**可辨识联合**建模（Day 18 的知识在这里变现）
- [ ] **`useContext`** ★★：`createContext<T | undefined>(undefined)` + 自定义 Hook 里做非空检查
- [ ] **自定义 Hook 返回值** ★★：返回对象（推荐）或 `as const` 元组
- [ ] **`useMemo` / `useCallback`** ★★：类型基本自动推断；**React Compiler 时代大部分场景不再需要手写**
- [ ] ★ 泛型组件与 `key`
- [ ] **实战**：把一个用 JS 写的组件完整改写成 TS，做到零 `any`

## Day 23 — 模块、声明文件、第三方库

- [ ] **`import type` / `export type`** ★★：只导入类型，打包时被完全移除
- [ ] **`@types/xxx`** ★★：为什么有些库要额外装 `@types/`，为什么现在多数库自带类型
- [ ] **`.d.ts` 声明文件是什么** ★★
- [ ] **`declare module 'xxx'`** ★：给没有类型的老库补一个最小声明
- [ ] **`declare global`** ★：扩展 `Window` 接口
- [ ] **环境变量类型** ★★：Vite 的 `import.meta.env` + `ImportMetaEnv` 接口扩展
- [ ] **路径别名** ★★：`@/components/Button` —— 需要**同时**配 `tsconfig.json` 的 `paths` 和 Vite 的 `resolve.alias`（只配一个会出现「能编译但运行报错」或反之）

### 运行时校验 ★★★ —— 重要观念

- [ ] TS 保护不了外部数据。API 返回的东西必须用 **Zod** 之类的库在运行时校验
- [ ] Zod 能从 schema 自动推导出 TS 类型（`z.infer`），一处定义两处受益
- [ ] 这是「类型安全」从编译期延伸到运行时的关键一步，做企业系统必须做
- [ ] ☆ 三斜线指令、`skipLibCheck`、Module Resolution 各种模式

## Day 24 — 高级类型（读得懂即可，不必会写）

> 这些是库作者的工具。**你日常不会写，但会在报错信息和库的类型定义里看到**，看不懂会很痛苦。

- [ ] **条件类型** ★：`T extends U ? X : Y`
- [ ] **`infer`** ★：从类型里「提取」出一部分
- [ ] **映射类型** ★：`{ [K in keyof T]: T[K] }`、`as` 键重映射、`+/-readonly`、`+/-?` 修饰符
- [ ] **模板字面量类型** ★：`` type Handler = `on${Capitalize<string>}` ``
- [ ] ☆ **递归类型**：`DeepPartial<T>`
- [ ] ☆ 联合类型的分发（distributive）行为
- [ ] **函数重载** ★：`function f(a: string): string; function f(a: number): number;`
- [ ] **类相关（TS 里用得比 C# 少得多）** ★
  - `implements`、`abstract`、`private/protected/public`、参数属性 `constructor(private x: string)`
  - **提醒**：TS 的 `private` 只是编译期的，运行时能访问到。真私有要用 JS 的 `#`
- [ ] **`enum`** ★：了解它，也了解**为什么现在推荐用字面量联合或 `as const` 对象替代**（`enum` 会生成运行时代码，`const enum` 有兼容问题，团队规范通常禁用）
- [ ] ☆ **`namespace`**：历史产物，模块化时代不要用
- [ ] ☆ **装饰器**：Angular / NestJS 用得多，React 基本不用
- [ ] ☆ mixin、`this` 类型

---

# 阶段 3：工程化（Day 25–28）

## Day 25 — 代码规范

- [ ] **ESLint**（flat config 时代，`eslint.config.js`）★★★
  - `typescript-eslint`
  - `eslint-plugin-react-hooks`（**能自动抓出 Hooks 依赖问题，价值极高**）
  - 关键规则：`no-explicit-any`、`exhaustive-deps`、`no-unused-vars`
- [ ] **Prettier** ★★★：交给它管格式，团队不再争论缩进；VS Code 配保存时自动格式化
- [ ] **两者分工**：Prettier 管「长相」，ESLint 管「对错」

## Day 26 — 调试与错误定位

- [ ] **VS Code / Chrome 断点调试** ★★★：条件断点、监视表达式、调用栈
- [ ] **Source Map** ★★：为什么生产环境报错行号是乱的、怎么恢复
- [ ] **React DevTools** ★★★：组件树、props / state 检查、Profiler 看渲染性能
- [ ] **读 TS 报错信息的技巧** ★★★：TS 的报错很长，学会**从最后一行往前读**、找 `Type 'X' is not assignable to type 'Y'` 的核心那句

### 常见错误速查

- [ ] `Cannot read properties of undefined`
- [ ] `x is not a function`
- [ ] `Objects are not valid as a React child`
- [ ] Hooks 顺序错误（`Rendered fewer hooks than expected`）

## Day 27 — 项目结构与依赖

- [ ] **目录组织** ★★：按功能（feature）而非按类型（components / utils）分目录 —— 项目大了差别巨大
- [ ] **npm scripts** ★★：`dev` `build` `lint` `typecheck` `preview`
- [ ] **`.env` 环境变量** ★★：Vite 的 `VITE_` 前缀规则、**为什么前端环境变量里绝不能放密钥**（会被打包进 JS 明文暴露）
- [ ] **依赖管理** ★★：`npm outdated` / `npm audit`、什么时候该升级、锁文件冲突怎么办
- [ ] **Git 基础** ★★（工作必需）：`clone` `branch` `add` `commit` `push`、`.gitignore`（`node_modules` 必须忽略）、Pull Request 流程

## Day 28 — 总复盘 + 模板沉淀

- [ ] 建一个自己的**项目起手模板**：Vite + React 19 + TS strict + ESLint + Prettier + 路径别名 + `typecheck` 脚本
- [ ] 把 28 天里所有「没懂的点」清单拿出来，逐条回看。此时至少一半会自动解开
- [ ] 写一份自己的备忘单（cheat sheet）：不可变更新五式、常用工具类型、常用事件类型

---

# 附录 A：Day 29 起的 React 19 顺序（预告）

只列顺序，细节到时再展开：

1. JSX 规则（`className`、`htmlFor`、`{}` 表达式、Fragment、条件渲染的三种写法）
2. 组件、props、组合（composition）
3. `useState` + 事件处理 + 受控组件
4. 列表渲染与 `key`
5. **派生状态**：能算出来的东西不要存进 state（新手最大的架构错误）
6. 状态提升、单向数据流
7. `useEffect` + 清理函数，以及**「你可能并不需要 Effect」**（这一课能省掉未来 80% 的 bug）
8. `useRef`、`useContext`、`useReducer`
9. 自定义 Hook
10. `useMemo` / `useCallback` 与 React Compiler
11. 错误边界、`Suspense`
12. **React 19 新特性**：`use()`、Actions / `useActionState` / `useFormStatus` / `useOptimistic`、`ref` 作为 prop、原生 document metadata 支持
13. 数据请求：**TanStack Query**（别自己用 `useEffect` + `fetch` 硬写）
14. 路由：**React Router**
15. 表单：**React Hook Form + Zod**
16. 样式：Tailwind CSS 或 CSS Modules
17. 组件库：Ant Design（企业后台）或 shadcn/ui
18. 最后再考虑：Next.js / Server Components

### React 阶段的三个「不要」

- 不要学 class 组件和生命周期方法（`componentDidMount` 那一套）
- 不要碰 Redux（`useState` + Context + TanStack Query 够了）
- 不要一开始就上 Next.js 和 Server Components

---

# 附录 B：可以永远不学的清单

看到这些内容的教程，直接关掉 —— 说明它已过时至少五年：

`var` · `==` · jQuery · `prototype` 手写继承 · IIFE · CommonJS `require` · Webpack / Babel 手工配置 · class 组件与 `componentDidMount` · `forwardRef`（React 19 已不需要） · 高阶组件 HOC · render props · Redux 的 `connect` / `mapStateToProps` · `PropTypes` · Bower / Grunt / Gulp · `moment.js` · `document.write` · `eval` · TS 的 `namespace` 与 `const enum`

---

# 附录 C：C# / WebForm 对照速查表

| C# / WebForm | JS / TS | 注意 |
| --- | --- | --- |
| `readonly` 字段 | `const` | `const` 只锁绑定，对象内容仍可改 |
| `int` / `long` / `decimal` | 只有 `number` | 金额要小心浮点误差 |
| `null` | `null` **和** `undefined` 两个 | 判空用 `??` 和 `?.` |
| `??` `?.` | `??` `?.` | 完全一样，可直接迁移 |
| LINQ `Select` / `Where` / `Any` / `All` | `map` / `filter` / `some` / `every` | 无延迟执行，立即返回新数组 |
| `Func<>` / `Action<>` / lambda | 箭头函数 | JS 里函数传递更随意 |
| `namespace` + `using` + dll | ESM `import` / `export` | 文件路径即模块标识 |
| `interface` 必须显式实现 | 结构化类型，形状对就兼容 | **最大的认知差异** |
| `enum` | 字面量联合 `'a' \| 'b'` | TS 的 `enum` 现在不推荐 |
| `async` / `await` / `Task<T>` | `async` / `await` / `Promise<T>` | 无线程池、无真并行、无 `ConfigureAwait` |
| 泛型可 `new T()`、可反射 | 类型运行时被擦除 | 不能 `new T()`，没有反射 |
| `Label1.Text = "x"` | **禁止**。改 state，UI 自己重算 | `UI = f(state)` |
| PostBack / ViewState / `Page_Load` | 不存在 | 整个模型不同 |
| 服务器控件 + DataBind | 组件 + props + `map` | — |
| `try/catch` | `try/catch` | JS 的 catch 参数是 `unknown` |
| 存储过程返回 DataTable | API 返回 JSON + Zod 校验 | 类型标注不等于运行时保证 |

---

# 附录 D：进度记录表

每天学完填一行。「卡住的点」栏很重要，阶段末统一回看。

| Day | 日期 | 主题 | 完成度 | 卡住的点 |
| --- | --- | --- | --- | --- |
| 1 | | 工具链 | | |
| 2 | | 模块 + 心智模型 | | |
| 3 | | 变量、原始类型 | | |
| 4 | | 字符串、运算符、假值 | | |
| 5 | | 函数（上） | | |
| 6 | | 闭包 | | |
| 7 | | 对象 | | |
| 8 | | 数组（一） | | |
| 9 | | 数组（二）不可变更新 | | |
| 10 | | Promise / async | | |
| 11 | | fetch | | |
| 12 | | 类、原型 | | |
| 13 | | 浏览器 API / DOM | | |
| 14 | | 杂项 + 阶段项目 | | |
| 15 | | TS 基础标注 | | |
| 16 | | 特殊类型 / type vs interface | | |
| 17 | | 联合与收窄（一） | | |
| 18 | | 可辨识联合 | | |
| 19 | | 泛型 | | |
| 20 | | 工具类型 | | |
| 21 | | React + TS：组件与事件 | | |
| 22 | | React + TS：Hooks 类型 | | |
| 23 | | 模块、声明文件、Zod | | |
| 24 | | 高级类型 | | |
| 25 | | ESLint / Prettier | | |
| 26 | | 调试 | | |
| 27 | | 项目结构、依赖、Git | | |
| 28 | | 总复盘 + 模板 | | |

---

## 参考来源

- [React 官方版本页](https://react.dev/versions)
- [React 官方文档](https://react.dev/learn)
- [TypeScript 官方博客](https://devblogs.microsoft.com/typescript/)
- [MDN JavaScript 指南](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript)

> 上述来源的内容已经过改写与归纳，以符合许可要求。
