# React 19 开发所需的 JavaScript + TypeScript 学习计划

> **适用对象**：有 20 年 C# ASP.NET WebForm + SQL Server 开发经验，JS / TS 零基础
> **投入**：每天 2 小时
> **总量**：**21 天 × 2 小时 = 42 小时**打完 JS + TS + 工程化基础，**第 22 天起进入 React 19**（约 6 周）
> **目标**：覆盖 React 19 日常开发用得到的全部 JS / TS 内容
> **版本基准**：React 19.2 / TypeScript 7.0（2026 年 7 月）

---

## 目录

- [一、计划总览](#一计划总览)
- [二、每天 2 小时怎么用](#二每天-2-小时怎么用)
- [三、频率标记说明](#三频率标记说明)
- [阶段 0：环境与模块（Day 1–2）](#阶段-0环境与模块day-12)
- [阶段 1：JavaScript 核心（Day 3–14）](#阶段-1javascript-核心day-314)
- [阶段 2：TypeScript 够用版（Day 15–19）](#阶段-2typescript-够用版day-1519)
- [阶段 3：工程化（Day 20–21）](#阶段-3工程化day-2021)
- [阶段 4：React 19 + TS 进阶穿插（Day 22 起）](#阶段-4react-19--ts-进阶穿插day-22-起)
- [附录 A：可以永远不学的清单](#附录-a可以永远不学的清单)
- [附录 B：C# / WebForm 对照速查表](#附录-bc--webform-对照速查表)
- [附录 C：进度记录表](#附录-c进度记录表)

---

## 一、计划总览

| 阶段 | 天数 | 内容 | 交付物 |
| --- | --- | --- | --- |
| 0 | Day 1–2 | 环境、模块系统、心智模型 | 能跑起来的 Vite 空项目 |
| 1 | Day 3–14 | JavaScript 核心（12 天） | 纯 JS 写的「待办清单 + 天气查询」控制台程序 |
| 2 | Day 15–19 | **TypeScript 够用版**（5 天） | 把阶段 1 的代码全部改写成 `.ts`，零 `any` |
| 3 | Day 20–21 | 工程化、调试、代码规范、Git | 配好 ESLint / Prettier / 路径别名的项目模板 |
| 4 | **Day 22 起** | **React 19**，全程用 TS 写；**TS 进阶穿插其中** | 一个完整的增删改查页面 |

### 为什么 TS 只前置 5 天

TS 拆成两批：

- **够用版（Day 15–19，前置）**：基础标注、`type` vs `interface`、联合与收窄、可辨识联合、结构化类型、泛型基础。这些是读懂任何 TS 代码的下限
- **进阶（穿插在阶段 4）**：工具类型、Hooks 的类型细节、泛型组件、`ComponentProps` 透传类型、Zod 运行时校验、高级类型。**这些在真正需要时才学，学了立刻就用得上**

这样安排的原因：一次性学完 10 天 TS，前 5 天有用、后 5 天没有落地场景，学完就忘。同时**从第一行 React 代码起就写 TS**，避免把 props、事件、Hooks 的写法学两遍。

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

## Day 3 — 变量、原始类型、引用相等

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
- [ ] `0.1 + 0.2 !== 0.3` —— **涉及金额务必用整数分或专门库**
      你 20 年 SQL Server `decimal(18,2)` 的习惯在 JS 里**没有对应物**，做报表 / 金额计算时这是头号风险
- [ ] `NaN`、`Infinity`、`Number.isNaN()`、`Number.isInteger()`
- [ ] 字符串转数字：`Number('1')` / `parseInt('1px')` / `parseFloat` / 一元 `+'1'`
- [ ] `toFixed(2)`（**返回字符串**，不是数字）

### `null` vs `undefined` ★★★

- [ ] `undefined` = 从没赋值 / 没这个属性 / 函数没返回
- [ ] `null` = 明确表示「空」，通常来自后端数据或你主动赋值
- [ ] 实务约定：自己写代码尽量只用 `undefined`，`null` 交给 API 数据

### 值语义 vs 引用语义 ★★★ —— 这是 React 不可变性的成因

- [ ] 原始类型传副本；对象 / 数组 / 函数传**引用**
- [ ] **关键机制：React 用 `Object.is` 比较新旧 state 的「引用」来决定是否重新渲染**
- [ ] **推论**：你改了对象内部但引用没变，React 认为什么都没发生，界面不刷新

```js
const a = { n: 1 }
const b = a
b.n = 2
console.log(a.n)              // 2  —— 同一个对象
console.log(Object.is(a, b))  // true —— React 会认为「没变化」

const c = { ...a, n: 3 }
console.log(Object.is(a, c))  // false —— React 才会重渲染
```

> 记住这一条，Day 7 和 Day 9 的所有「不可变更新」写法你都能自己推出来，不用背。

- [ ] **`typeof`** ★★★ 及其经典坑：`typeof null === 'object'`
- [ ] ☆ 自动装箱：为什么 `'abc'.toUpperCase()` 能对一个原始值调方法

## Day 4 — 字符串、运算符、真值假值

### 字符串 ★★★

- [ ] **模板字符串**：`` `你好 ${name}，共 ${a + b} 元` ``、天然支持多行
      JSX 里拼接动态 `className`、拼接 URL 几乎全靠它，比 `+` 拼接更常用
- [ ] 常用方法：`length` `includes` `startsWith` `endsWith` `slice` `split` `join` `trim` `replace` `replaceAll` `toUpperCase` `toLowerCase` `padStart` `at(-1)` `indexOf`
- [ ] 字符串不可变：所有方法都返回新字符串，原串不变（同 C#）

### 严格相等 ★★★

- [ ] **一律用 `===`**，`==` 会做隐式类型转换（`'' == 0` 是 `true`）
- [ ] **`Object.is` 与 `===` 基本等价**（只在 `NaN`、`±0` 上有差别）
- [ ] **为什么这条对 React 极其重要**：`useEffect` 的依赖数组用 `Object.is` **逐项比较引用**

```js
useEffect(() => { /* ... */ }, [{ id: 1 }])  // 每次渲染都是新对象 → 每次都触发，等于没写依赖
useEffect(() => { /* ... */ }, [user.id])    // 原始值比较 → 正确
```

> 规则：**依赖数组里尽量只放原始值**（string / number / boolean），别放对象和数组。

### 真值假值（falsy）★★★

- [ ] **实务上记住这 6 个假值**：`false` · `0` · `''`（空串） · `null` · `undefined` · `NaN`
      （另有三个边角情况：`-0`、`0n`、`document.all`）
- [ ] **注意 `'0'`、`'false'`、`' '`（空格）、`[]`、`{}` 都是真值**
- [ ] **`[]` 是真值** —— 所以 `if (列表)` 对空数组永远为真，必须写 `列表.length > 0`

### `&&` 短路渲染的坑 ★★★ —— React 新手头号 bug

这个坑是**两条独立规则叠加**造成的，理解机制就不用死记：

1. **`&&` 返回的是操作数本身，不是布尔值** —— `0 && <span/>` 的结果是 `0`，不是 `false`
2. **React 会渲染 `0`，但会忽略 `false` / `null` / `undefined`**

```jsx
{count && <span>{count}</span>}        // count 为 0 时，页面上真的出现一个 "0"
{items.length && <List />}             // 空数组时同样渲染出 "0"

{count > 0 && <span>{count}</span>}    // 对
{items.length > 0 && <List />}         // 对
```

- [ ] **规则：`&&` 左边必须是真正的布尔表达式**（`x > 0`、`arr.length > 0`、`Boolean(x)`），不能是数字或字符串

### `??` 空值合并 —— 和 `&&` 的坑同一类 ★★★

- [ ] `a ?? b`：**只**在 `a` 为 `null` / `undefined` 时取 `b`

```js
const 页大小 = props.pageSize || 20    // 传 0 会变成 20 —— 错
const 页大小 = props.pageSize ?? 20    // 传 0 就是 0 —— 对

const 备注 = props.remark || '无'      // 用户故意清空（''）会被覆盖成「无」—— 错
const 备注 = props.remark ?? '无'      // 对
```

- [ ] **规则：取默认值一律用 `??`，不要用 `||`**

### 其他运算符

- [ ] **`?.` 可选链** ★★★：`user?.address?.city`、`arr?.[0]`、`fn?.()`
- [ ] **三元运算符** ★★★ `条件 ? a : b` —— JSX 里条件渲染的主力（JSX 中不能写 `if`）
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

- [ ] **默认参数**：`function f(a = 1) {}` —— 给组件 props 设默认值时常用
- [ ] **参数解构 + 默认值**：`function Card({ title, size = 'md' }) {}`
      React 组件接收 props 的标准写法，必须写熟
- [ ] JS 没有方法重载，没有 `ref` / `out` 参数，没有命名参数（用对象参数模拟）

### 剩余参数与 `{...rest}` 属性透传 ★★★

- [ ] **剩余参数**：`function sum(...args) {}` —— 收集不定个数的参数
- [ ] **参数里的剩余解构 + 透传**：封装可复用组件的核心手法

```jsx
// 自己关心的 prop 单独取出，其余原样透传给底层原生元素
function Input({ label, ...rest }) {
  return (
    <label>
      {label}
      <input {...rest} />   {/* placeholder、disabled、maxLength、onBlur… 全部自动支持 */}
    </label>
  )
}

// 调用方可以像用原生 input 一样用它
<Input label="客户名称" placeholder="请输入" maxLength={50} disabled />
```

- [ ] **为什么这条对企业后台特别关键**：要封一套统一样式的 `Input` / `Button` / `Select`，靠的就是它。否则你得把原生元素的几十个属性一个个手工转发
- [ ] 它的类型写法（`ComponentProps<'input'>` + `Omit`，透传时保留原生属性的类型提示）在**阶段 4 第 6 周**接上

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
- [ ] **和 C# 的关键差别 —— 你已有的直觉会在这里帮倒忙**
  - C# 里闭包捕获的是**变量**（变量后来变了，闭包看到的也变）
  - React 里每次渲染会产生**全新一套变量**，闭包捕获的是**「那一次渲染的快照」**
- [ ] **在 React 里的意义**：`useState` 返回的 `count` 是这一次渲染被「冻结」的值
- [ ] **stale closure（过期闭包）**：`useEffect` / `setTimeout` 里读到旧值 —— React 新手第二号 bug。今天先建立概念，React 阶段会反复遇到

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
- [ ] **属性简写**：`{ name, age }` 等价于 `{ name: name, age: age }`
      直接影响自定义 Hook 返回值的可读性：`return { data, loading, error }`
- [ ] **计算属性名**：`{ [key]: value }` —— 动态字段名，表单统一处理时必用

```js
// 一个 onChange 处理所有输入框
const handleChange = (e) => {
  setForm({ ...form, [e.target.name]: e.target.value })
}
```

- [ ] `.` 访问 vs `[]` 访问（字段名是变量时用 `[]`）
- [ ] 方法简写：`{ greet() {} }`

### 解构 ★★★

- [ ] 基础：`const { a, b } = obj`
- [ ] 重命名：`const { a: x } = obj`
- [ ] 默认值：`const { a = 1 } = obj`
- [ ] 嵌套：`const { user: { name } } = data`
- [ ] **剩余 + 透传**：`const { id, ...rest } = obj` —— 和 Day 5 的 `{...rest}` 是同一个手法，用于「排除某几个字段，其余原样传下去」

### 展开运算符 `...` ★★★

- [ ] 合并 / 覆盖：`{ ...defaults, ...overrides }`（**后面的覆盖前面的**）
- [ ] 复制：`{ ...obj }`
- [ ] **这就是 React 状态更新的主力手段**

### 浅拷贝 ≠ 深拷贝 ★★★ —— 嵌套更新必须逐层展开

`{...obj}` **只拷一层**。真实业务数据全是嵌套的，这里是所有人翻车的地方：

```js
// 错：address 还是同一个引用，Object.is 判定「没变」，React 不刷新
const bad = { ...user }
bad.address.city = '上海'

// 对：从根到被改字段的每一层都要新建
const good = { ...user, address: { ...user.address, city: '上海' } }
```

- [ ] `structuredClone(obj)` 深拷贝（现代浏览器原生支持）
- [ ] 为什么不要用 `JSON.parse(JSON.stringify(x))`（丢 `Date`、`undefined`、函数）
- [ ] **嵌套超过三层就该考虑拆分 state**，而不是写三层展开

### 不可变更新对象 ★★★（React 必背）

- [ ] 改一个字段：`{ ...user, name: '张三' }`
- [ ] 改嵌套字段：`{ ...user, address: { ...user.address, city: '上海' } }`
- [ ] 删一个字段：`const { 密码, ...其余 } = user`
- [ ] 为什么不能 `user.name = '张三'` —— 回看 Day 3 的 `Object.is`

### 其他

- [ ] **`Object.keys` / `values` / `entries`** ★★：遍历对象数据渲染列表时配合 `.map()` 使用

```jsx
{Object.entries(统计).map(([键, 值]) => <tr key={键}><td>{键}</td><td>{值}</td></tr>)}
```

- [ ] ★★ `Object.assign` / `fromEntries` / `freeze`
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
- [ ] **`sort`** ★★ —— **两个大坑，几乎所有教程都不提**
  - 默认按**字符串**排序：`[10, 9, 1].sort()` 得 `[1, 10, 9]`。数字必须传比较函数 `(a, b) => a - b`
  - **`sort` 会原地修改原数组**，React 里必须 `[...arr].sort(...)` 或 `arr.toSorted(...)`
- [ ] **`includes` / `indexOf` / `join` / `flat` / `flatMap` / `reverse`** ★★
- [ ] **`slice`（不改原）vs `splice`（改原）** ★★ —— 名字像、行为完全不同，务必区分
- [ ] **`forEach`** ★★：只做副作用时用；要产出新数组用 `map`；不能 `break`（要提前退出用 `for...of`）
- [ ] **`Array.from`** ★：`Array.from({ length: 5 }, (_, i) => i)`
- [ ] **数组解构** ★★★：`const [a, b] = arr`、跳过 `const [, second] = arr`、剩余 `const [head, ...tail] = arr`
  - **`useState` 返回的就是数组，靠解构接收**：`const [count, setCount] = useState(0)`

## Day 9 — 数组（二）：不可变更新五式

> React 必背。今天全部手写一遍。所有写法的依据都是 Day 3 的 `Object.is` 引用比较。

| 操作 | 写法 |
| --- | --- |
| 增（尾部） | `[...arr, newItem]` |
| 增（头部） | `[newItem, ...arr]` |
| 删 | `arr.filter(x => x.id !== id)` |
| 改 | `arr.map(x => x.id === id ? { ...x, done: true } : x)` |
| 插入到 i | `[...arr.slice(0, i), newItem, ...arr.slice(i)]` |
| 排序 | `[...arr].sort(cmp)` 或 `arr.toSorted(cmp)` |

### 禁用的原地修改方法 ★★★

**在 React 状态上用了这些，界面不会刷新** —— 因为引用没变：

`push` · `pop` · `shift` · `unshift` · `splice` · `sort` · `reverse`

```js
// 错：引用没变，Object.is 判定「没变化」
rows.push(newRow)
setRows(rows)

// 对：新数组，新引用
setRows([...rows, newRow])
```

- [ ] **企业系统最高频的操作 —— 改表格某一行**

```js
setRows(rows.map(r => r.id === id ? { ...r, 状态: '已审核' } : r))
```

### 其他

- [ ] **ES2023 不可变新方法** ★★：`toSorted` `toReversed` `toSpliced` `with(i, v)` —— 现代环境可直接用，比展开写法清爽
- [ ] **`key` 的规则** ★★★
  - 为什么列表每项要唯一 `key`：React 靠它判断「哪一项是哪一项」
  - **不要用数组下标当 key**。用 `index` 时，删除中间一项后**输入框里的值会串到别的行上**
  - 「表格 + 可编辑单元格」的场景必然撞上这个坑，用数据库主键当 key
- [ ] **`Set`** ★★：去重、`has` 判存在（比 `includes` 快）
- [ ] **`Map`** ★★：任意类型做键、保持插入顺序、`size`
- [ ] ★ `for...of` vs `for...in`（**`for...in` 遍历的是键名，用在数组上是错的**）、可迭代协议

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

- [ ] `try` / `catch` / `finally` 配合 `async/await`
- [ ] `throw new Error('msg')`、`Error` 对象的 `message` / `stack` / `cause`
- [ ] ★ 自定义 Error 子类
- [ ] **未捕获的 Promise rejection** 是个常见事故源
- [ ] ⚠️ **注意：try/catch 抓不住 HTTP 错误状态** —— 明天 Day 11 专门讲

### 并发 ★★

- [ ] `Promise.all`（一个失败全失败）
- [ ] `Promise.allSettled`（都等完，各自报告成败）
- [ ] ★ `Promise.race` / `Promise.any`
- [ ] 串行 `await` 循环 vs 并行 `Promise.all(arr.map(...))` 的性能差别

### 定时器 ★★

- [ ] `setTimeout` / `setInterval` / `clearTimeout` / `clearInterval`；写一个 `sleep(ms)` 工具函数

## Day 11 — 异步（二）：fetch 与真实数据

### ⚠️ `fetch` 在 404 / 500 时不会 reject ★★★ —— 本计划最重要的一个坑

**你的 WebForm 直觉在这里会主动害你。** `SqlCommand` 出错会抛 `SqlException`，你的 `try/catch` 一定抓得到。
**`fetch` 遇到 500 是「成功地拿到了一个 500 响应」，一声不响。**

`try/catch` 只能抓住**网络层**失败（断网、DNS 失败、CORS 被拒），抓不住 HTTP 错误状态：

```js
// 错：接口挂了你不知道
async function 取数据() {
  const res = await fetch(url)         // 500 也顺利通过，不抛异常
  const data = await res.json()        // 服务器返回 HTML 错误页 → 这里才炸
  return data                          // 报错信息是 Unexpected token '<' in JSON
}                                      // 你会以为是解析问题，其实是接口挂了
```

```js
// 对：必须手动检查
async function 取数据() {
  const res = await fetch(url)
  if (!res.ok) {                       // ← 这一行不写，接口挂了你不知道
    throw new Error(`请求失败：${res.status}`)
  }
  return await res.json()
}
```

- [ ] **`res.ok`（等价于 status 在 200–299）必须每次检查**，这是硬规矩
- [ ] 记住那个误导性报错：`Unexpected token '<' in JSON` **≠ 解析问题，= 接口返回了 HTML 错误页**

### `fetch` 其余用法 ★★★

- [ ] GET：`const res = await fetch(url)`
- [ ] `await res.json()` / `res.text()` / `res.status`
- [ ] POST：`{ method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(data) }`
- [ ] HTTP 状态码常识：200 / 201 / 204 / 400 / 401 / 403 / 404 / 409 / 500
- [ ] 查询参数：`URLSearchParams`

### 其他

- [ ] **`AbortController`** ★★：取消请求。React 的 `useEffect` 清理函数里会用
- [ ] **竞态条件（race condition）** ★★：快速切换筛选条件时，先发的请求后返回，导致显示旧数据。概念先建立，React 阶段用 TanStack Query 解决
- [ ] **CORS 跨域** ★★：概念、为什么本地开发要配 Vite proxy（做企业内部系统一定会撞上）

### 实战

- [ ] 调一个公开 API（如天气或 GitHub API），做完整的「加载中 / 成功 / 失败」三态处理，**含 `res.ok` 检查**

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
- [ ] **非法场景**：用 `document.getElementById` 去修改 React 渲染出来的节点内容
      这是 WebForm `Label1.Text = "x"` 习惯的直接迁移，**会和 React 打架，且下次渲染就被冲掉**

### 其他

- [ ] ★ `FormData`、文件上传、`Blob` / 下载文件、`IntersectionObserver`、`ResizeObserver`
- [ ] ☆ Cookie 操作、`postMessage`、WebSocket、Canvas

## Day 14 — 收口 + 杂项 + 阶段项目

### 日期时间 ★★

- [ ] 原生 `Date` 的坑（月份从 0 开始、解析行为不一致、时区处理糟糕）
- [ ] **实务结论：装 `date-fns`**（轻量、按需引入）
- [ ] `Temporal` 新 API 已开始在浏览器落地，但工作项目里还早，先了解名字

### 格式化与数学

- [ ] **`Intl.NumberFormat`** ★★：千分位、金额、百分比
      前端没有 `String.Format("{0:N2}")`，这就是替代品，报表页面天天用
- [ ] **`Intl.DateTimeFormat`** ★★
- [ ] **`Math`** ★★：`round` `floor` `ceil` `max` `min` `abs` `random`
- [ ] **正则表达式基础** ★：`test` / `match` / `replace` / 字符类 / `\d \w \s` / 量词 / 分组
      企业内部系统**必然**做表单校验，所以这个不能跳过，但不用深挖

### 认得就行 ☆

- [ ] `Symbol`、`generator` / `yield`、`Proxy` / `Reflect`（知道 MobX、Vue 用它做响应式）、标签模板（styled-components 用它）、`WeakMap`、`globalThis`

### 永远不用 ✕

- [ ] `eval`、`with`、`document.write`、`var`、`==`、`arguments`、jQuery

### 阶段 1 项目（占今天大部分时间，可顺延 1–2 天）

- [ ] 一个纯 JS 的待办清单模块：增删改查 + 筛选 + 排序，**全部用不可变更新**
- [ ] 一个天气查询模块：`fetch` + `res.ok` 检查 + 三态处理 + `AbortController`
- [ ] 不做界面，全部在控制台里 `console.log` 验证

---

# 阶段 2：TypeScript 够用版（Day 15–19）

> C# 底子在这里会让你飞起来 —— TypeScript 和 C# 是同一个人（Anders Hejlsberg）主持设计的。
> **这 5 天只学「读懂并写出任何 TS 业务代码」的下限。**工具类型、泛型组件、Zod、高级类型全部推迟到阶段 4 穿插。

## Day 15 — TS 是什么 + 基础标注

### 心智模型 ★★★

- [ ] TS **只在编译期存在，运行时被完全擦除**。没有反射、拿不到 `typeof T`、泛型里不能 `new T()`
      —— 你 C# 里靠反射做的事情，在 TS 里全都要换思路
- [ ] TS 是「极其聪明的 Lint」，不改变任何运行时行为
- [ ] **推论**：外部数据（API 返回、`localStorage`）的类型标注是**你的承诺，不是保证**。后端改字段，TS 不会报错，运行时照样炸（阶段 4 用 Zod 解决）

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

## Day 17 — 联合类型与类型收窄

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
- [ ] 真值检查 `if (x)`（**注意 Day 4 的假值陷阱：`0` 和 `''` 会被判为假，用 `if (x !== undefined)` 更准确**）
- [ ] `x === 'literal'` 字面量比较
- [ ] 提前 `return` / `throw` 让后续代码自动收窄
- [ ] 可选链后的收窄
- [ ] **实战**：处理 `catch (e: unknown)`（TS 里 catch 参数就是 `unknown`）

## Day 18 — 可辨识联合 + 结构化类型

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

- [ ] C# 是**名义类型**：必须显式 `: IFoo` 才算实现接口
- [ ] TS 是**结构类型**：**形状对得上就算兼容**，不需要任何继承声明
- [ ] **多余属性检查**：对象**字面量**直接赋值时会额外检查多余属性，但通过变量赋值不会 —— 这个不对称行为要知道
- [ ] ☆ branded types 模拟名义类型：`type UserId = string & { __brand: 'UserId' }`

## Day 19 — 泛型基础

- [ ] **泛型函数** ★★：`function first<T>(arr: T[]): T | undefined {}`
- [ ] **约束** ★★：`<T extends { id: number }>`
- [ ] **默认类型参数** ★★：`<T = string>`
- [ ] **`keyof`** ★★：`keyof User` 得到 `'id' | 'name'`
- [ ] **索引访问类型** ★★：`User['name']`
- [ ] **类型位置的 `typeof`** ★★：`typeof someObject` —— 从值反推类型，很常用
- [ ] **泛型接口 / 泛型类型别名** ★★
- [ ] **与 C# 泛型的差别**：**没有运行时具化**，不能 `new T()`，没有 `where T : new()`，但有 `extends` 约束和强大的类型推断
- [ ] ⏭️ 泛型 React 组件、多类型参数推断（`Pick<T, K>` 那类写法）**推迟到阶段 4 第 6 周**

### 阶段 2 交付物

- [ ] 把 Day 14 的两个 JS 模块全部改写成 `.ts`，`tsc --noEmit` 零报错、零 `any`
- [ ] 请求状态用**可辨识联合**建模

---

# 阶段 3：工程化（Day 20–21）

## Day 20 — 代码规范 + 调试

### ESLint + Prettier ★★★

- [ ] **ESLint**（flat config 时代，`eslint.config.js`）
  - `typescript-eslint`
  - `eslint-plugin-react-hooks`（**能自动抓出 Hooks 依赖问题，价值极高**）
  - 关键规则：`no-explicit-any`、`exhaustive-deps`、`no-unused-vars`
- [ ] **Prettier**：交给它管格式，团队不再争论缩进；VS Code 配保存时自动格式化
- [ ] **两者分工**：Prettier 管「长相」，ESLint 管「对错」

### 调试与错误定位 ★★★

- [ ] **VS Code / Chrome 断点调试**：条件断点、监视表达式、调用栈
- [ ] **Source Map** ★★：为什么生产环境报错行号是乱的、怎么恢复
- [ ] **React DevTools**：组件树、props / state 检查、Profiler 看渲染性能
- [ ] **读 TS 报错信息的技巧**：TS 的报错很长，学会**从最后一行往前读**、找 `Type 'X' is not assignable to type 'Y'` 的核心那句

### 常见错误速查

- [ ] `Cannot read properties of undefined`
- [ ] `x is not a function`
- [ ] `Objects are not valid as a React child`
- [ ] `Unexpected token '<' in JSON` —— **不是解析问题，是接口返回了 HTML 错误页**（回看 Day 11）
- [ ] Hooks 顺序错误（`Rendered fewer hooks than expected`）

## Day 21 — 项目结构、依赖、Git + 模板沉淀

- [ ] **目录组织** ★★：按功能（feature）而非按类型（components / utils）分目录 —— 项目大了差别巨大
- [ ] **npm scripts** ★★：`dev` `build` `lint` `typecheck` `preview`
- [ ] **`.env` 环境变量** ★★：Vite 的 `VITE_` 前缀规则
      **前端环境变量里绝不能放密钥**（会被打包进 JS 明文暴露，任何人都能看）
- [ ] **依赖管理** ★★：`npm outdated` / `npm audit`、什么时候该升级、锁文件冲突怎么办
- [ ] **Git 基础** ★★（工作必需）：`clone` `branch` `add` `commit` `push`、`.gitignore`（`node_modules` 必须忽略）、Pull Request 流程

### 阶段 3 交付物

- [ ] 一个自己的**项目起手模板**：Vite + React 19 + TS strict + ESLint + Prettier + 路径别名 + `typecheck` 脚本
- [ ] 把 Day 1–19 所有「没懂的点」清单拿出来逐条回看。此时至少一半会自动解开
- [ ] 一份自己的备忘单：不可变更新五式、`??` vs `||`、`&&` 渲染规则、`res.ok` 检查

---

# 阶段 4：React 19 + TS 进阶穿插（Day 22 起）

## 类型使用纪律：前两周只用这 4 样

初次接触 JSX 时如果同时处理泛型组件、类型体操，噪音会过大。**前两周把 TS 压到最小：**

1. props 的 `type`（对象形状标注）
2. `useState<T>()`
3. 4 个事件类型（`ChangeEvent` / `MouseEvent` / `FormEvent` / `KeyboardEvent`）
4. `children: React.ReactNode`

**不碰**：泛型组件、`ComponentProps` 高级用法、工具类型组合、条件类型。
遇到搞不定的类型先写 `// TODO 类型` 标记继续往下，第 3 周统一回来处理。

## 六周路线 + TS 进阶穿插点

| 周 | React 内容 | 同期补的 TS |
| --- | --- | --- |
| **第 1 周** | JSX 规则（`className`、`htmlFor`、`{}` 表达式、Fragment、条件渲染三种写法）· 组件与 props · 组合（composition）· `useState` + 事件处理 + 受控组件 · 列表渲染与 `key` | 只用 props `type` + `useState<T>` |
| **第 2 周** | **派生状态**（能算出来的不要存 state，新手最大的架构错误）· 状态提升 · 单向数据流 · `useEffect` + 清理函数 · **「你可能并不需要 Effect」**（这一课能省掉未来 80% 的 bug） | 4 个事件类型 · `children: ReactNode` · `ReactNode` / `ReactElement` 的区别 · 不要用 `React.FC` |
| **第 3 周** | `useRef` · `useContext` · `useReducer` · 自定义 Hook | **TS 进阶 ①：Hooks 的类型**<br>`useRef<HTMLInputElement>(null)` vs `useRef<number>(0)`（`RefObject` vs `MutableRefObject`）· `Dispatch<SetStateAction<T>>` · `useReducer` 的 action 用**可辨识联合**（Day 18 变现）· `createContext<T \| undefined>(undefined)` + 自定义 Hook 做非空检查 · 自定义 Hook 返回值用对象或 `as const` 元组 · **React 19：`ref` 就是普通 prop，不再需要 `forwardRef`** |
| **第 4 周** | 数据请求：**TanStack Query**（别自己用 `useEffect` + `fetch` 硬写，它顺手解决 Day 11 的竞态条件）· 错误边界 · `Suspense` | **TS 进阶 ②：工具类型 + 运行时校验**<br>`Partial` / `Required` / `Readonly` / `Pick` / `Omit` / `Record` · `Exclude` / `Extract` / `NonNullable` · `ReturnType<typeof f>` / `Parameters` / `Awaited` · `satisfies` · **Zod**：从 schema 用 `z.infer` 推导类型，把类型安全从编译期延伸到运行时 |
| **第 5 周** | 路由：**React Router** · 表单：**React Hook Form + Zod** · 样式：Tailwind CSS 或 CSS Modules | **TS 进阶 ③：模块与声明文件**<br>`import type` / `export type` · `@types/xxx` 与 `.d.ts` 是什么 · `declare module` 给无类型老库补声明 · `declare global` 扩展 `Window` · `import.meta.env` + `ImportMetaEnv` · **路径别名要同时配 `tsconfig` 的 `paths` 和 Vite 的 `resolve.alias`**（只配一个会「能编译但运行报错」） |
| **第 6 周** | 组件库：Ant Design（企业后台）或 shadcn/ui · **React 19 新特性**：`use()` · Actions / `useActionState` / `useFormStatus` / `useOptimistic` · 原生 document metadata · `useMemo` / `useCallback` 与 React Compiler | **TS 进阶 ④：泛型组件与高级类型**<br>泛型 React 组件（通用 `Table<T>` / `Select<T>`）· `ComponentProps<'input'>` + `Omit` 做**属性透传的类型**（接上 Day 5 的 `{...rest}`）· `Pick<T, K extends keyof T>` 多参数推断 · **读得懂就行**：条件类型 · `infer` · 映射类型 · 模板字面量类型 · 函数重载 · 为什么不用 `enum` / `namespace` |

### 阶段 4 的三个「不要」

- 不要学 class 组件和生命周期方法（`componentDidMount` 那一套）
- 不要碰 Redux（`useState` + Context + TanStack Query 够了）
- 不要一开始就上 Next.js 和 Server Components，等这 6 周走完再说

### 阶段 4 交付物

- [ ] 一个完整的增删改查页面：列表 + 筛选 + 排序 + 分页 + 新增/编辑表单 + 校验 + 删除确认
- [ ] 数据走真实 API，含加载 / 空数据 / 错误三态
- [ ] `tsc --noEmit` 零报错、零 `any`、ESLint 零 warning

---

# 附录 A：可以永远不学的清单

看到这些内容的教程，直接关掉 —— 说明它已过时至少五年：

`var` · `==` · jQuery · `prototype` 手写继承 · IIFE · CommonJS `require` · Webpack / Babel 手工配置 · class 组件与 `componentDidMount` · `forwardRef`（React 19 已不需要） · 高阶组件 HOC · render props · Redux 的 `connect` / `mapStateToProps` · `PropTypes` · Bower / Grunt / Gulp · `moment.js` · `document.write` · `eval` · TS 的 `namespace` 与 `const enum`

---

# 附录 B：C# / WebForm 对照速查表

| C# / WebForm | JS / TS | 注意 |
| --- | --- | --- |
| `readonly` 字段 | `const` | `const` 只锁绑定，对象内容仍可改 |
| `int` / `long` / `decimal` | 只有 `number` | 金额要小心浮点误差，没有 `decimal` |
| `null` | `null` **和** `undefined` 两个 | 判空用 `??` 和 `?.` |
| `??` `?.` | `??` `?.` | 完全一样，可直接迁移 |
| `\|\|` 取默认值 | 必须换成 `??` | `0 \|\| 20` 得 20，是 bug |
| LINQ `Select` / `Where` / `Any` / `All` | `map` / `filter` / `some` / `every` | 无延迟执行，立即返回新数组 |
| `Func<>` / `Action<>` / lambda | 箭头函数 | JS 里函数传递更随意 |
| lambda 捕获**变量** | 闭包捕获**那次渲染的快照** | stale closure 的全部成因 |
| `namespace` + `using` + dll | ESM `import` / `export` | 文件路径即模块标识 |
| `interface` 必须显式实现 | 结构化类型，形状对就兼容 | **最大的认知差异** |
| `enum` | 字面量联合 `'a' \| 'b'` | TS 的 `enum` 现在不推荐 |
| `async` / `await` / `Task<T>` | `async` / `await` / `Promise<T>` | 无线程池、无真并行、无 `ConfigureAwait` |
| `SqlException` 一定抛出 | **`fetch` 遇 500 不抛异常** | 必须手动 `if (!res.ok) throw` |
| 泛型可 `new T()`、可反射 | 类型运行时被擦除 | 不能 `new T()`，没有反射 |
| `Label1.Text = "x"` | **禁止**。改 state，UI 自己重算 | `UI = f(state)` |
| PostBack / ViewState / `Page_Load` | 不存在 | 整个模型不同 |
| 服务器控件 + DataBind | 组件 + props + `map` | — |
| `try/catch` | `try/catch` | JS 的 catch 参数是 `unknown` |
| 存储过程返回 DataTable | API 返回 JSON + Zod 校验 | 类型标注不等于运行时保证 |
| `String.Format("{0:N2}")` | `Intl.NumberFormat` | 报表金额格式化 |

---

# 附录 C：进度记录表

每天学完填一行。「卡住的点」栏很重要，阶段末统一回看。

| Day | 日期 | 主题 | 完成度 | 卡住的点 |
| --- | --- | --- | --- | --- |
| 1 | | 工具链 | | |
| 2 | | 模块 + 心智模型 | | |
| 3 | | 变量、原始类型、引用相等 | | |
| 4 | | 字符串、`===`、假值、`&&`、`??` | | |
| 5 | | 函数（上）、`{...rest}` 透传 | | |
| 6 | | 闭包 | | |
| 7 | | 对象、浅拷贝、嵌套更新 | | |
| 8 | | 数组（一） | | |
| 9 | | 数组（二）不可变更新、`key` | | |
| 10 | | Promise / async | | |
| 11 | | fetch、`res.ok` | | |
| 12 | | 类、原型 | | |
| 13 | | 浏览器 API / DOM | | |
| 14 | | 杂项 + 阶段 1 项目 | | |
| 15 | | TS 心智模型 + 基础标注 | | |
| 16 | | 特殊类型 / type vs interface | | |
| 17 | | 联合与收窄 | | |
| 18 | | 可辨识联合 + 结构化类型 | | |
| 19 | | 泛型基础 + 阶段 2 交付物 | | |
| 20 | | ESLint / Prettier / 调试 | | |
| 21 | | 项目结构、Git、起手模板 | | |

### React 阶段（Day 22 起，按周记录）

| 周 | 起止日期 | React 内容 | TS 进阶 | 卡住的点 |
| --- | --- | --- | --- | --- |
| 1 | | JSX、组件、props、useState、列表 | 基础标注 | |
| 2 | | 派生状态、状态提升、useEffect | 事件类型、children | |
| 3 | | useRef / useContext / useReducer / 自定义 Hook | ① Hooks 类型 | |
| 4 | | TanStack Query、错误边界、Suspense | ② 工具类型 + Zod | |
| 5 | | React Router、表单、样式 | ③ 模块与声明文件 | |
| 6 | | 组件库、React 19 新特性、Compiler | ④ 泛型组件 + 高级类型 | |

---

## 参考来源

- [React 官方版本页](https://react.dev/versions)
- [React 官方文档](https://react.dev/learn)
- [TypeScript 官方博客](https://devblogs.microsoft.com/typescript/)
- [MDN JavaScript 指南](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript)

> 上述来源的内容已经过改写与归纳，以符合许可要求。
