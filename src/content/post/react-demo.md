---
title: react-demo
description: react-note
publishDate: 2025-07-30
draft: true
tags:
  - study
ogImage: /social-card.avif
---
just for copy

front-course-Udemy

[html+css](https://www.bilibili.com/video/BV1A34y1e7wL/?spm_id_from=333.1387.search.video_card.click&vd_source=c56f6e876183507cbb1bfdd8fb305472)

[js](https://www.bilibili.com/video/BV1vA4y197C7?spm_id_from=333.788.videopod.episodes&vd_source=c56f6e876183507cbb1bfdd8fb305472&p=20) | [repo](https://github.com/jonasschmedtmann/complete-javascript-course)

[react](https://www.bilibili.com/video/BV11M4m1z72h/?spm_id_from=333.1387.homepage.video_card.click&vd_source=c56f6e876183507cbb1bfdd8fb305472)

---

速通一下react （仅有简单的html基础，js了解浅薄，css更不用说，基本不会用，之前只跟视频用过vue

tsx类似于jsx

```jsx
function App(){
    ...

    return (
        <>
        <h1> 
         ...  // 只能使用html和react组件
        </>
    )
}
```

且jsx标记中，我们只能用html元素和其余react组件，数据渲染表达式需要使用 `{}` 包括起来

React 的核心是构建**组件 (Components)**。你可以把组件想象成乐高积木，每个积木都有自己的功能和外观，你可以把它们组合起来，搭建出复杂的应用。

---

### 1. 组件 (Components)

在现代 React 中，我们主要使用**函数式组件 (Functional Components)**。

**什么是函数式组件？**
它就是一个普通的 JavaScript 函数，这个函数会**返回 JSX**。

**示例：**

```jsx
// 这是一个最简单的函数式组件
function WelcomeMessage() {
  return <h1>Hello, React!</h1>; // 返回 JSX
}

// 在另一个组件中使用 WelcomeMessage
function App() {
  return (
    <div>
      <WelcomeMessage /> {/* 使用 WelcomeMessage 组件 */}
      <p>This is my first React app.</p>
    </div>
  );
}
```

**关键点：**

* 组件的名称必须以**大写字母开头**（例如 `WelcomeMessage`，而不是 `welcomeMessage`）。这是 React 区分 HTML 标签和 React 组件的方式。
* 组件必须返回 JSX。

---

### 2. JSX (JavaScript XML)

**JSX 不是 HTML，它是一种 JavaScript 的语法扩展。** 它看起来很像 HTML，但实际上它允许你在 JavaScript 代码中编写类似 HTML 的结构。

**为什么用 JSX？**
因为它让 UI 的描述变得非常直观和声明式。

**JSX 里能放什么？**

1. **HTML 标签：** 你可以直接写 `<div>`, `<p>`, `<h1>`, `<button>` 等。

   ```jsx
   const element = <div>这是一个 div 标签。</div>;
   ```
2. **React 组件：** 就像上面 `App` 组件里那样，你可以把其他组件当作标签一样使用。

   ```jsx
   // 假设上面定义了 WelcomeMessage 组件
   const myApp = (
     <div>
       <WelcomeMessage /> {/* 在 JSX 中使用 React 组件 */}
     </div>
   );
   ```
3. **JavaScript 表达式：** 这是 JSX 强大之处！你可以在 JSX 中嵌入任何有效的 JavaScript 表达式，只需要用**花括号 `{}`** 包裹起来。

   * **变量：**
     ```jsx
     const name = '张三';
     const greeting = <p>你好，{name}！</p>; // 渲染 "你好，张三！"
     ```
   * **数字和字符串：**
     ```jsx
     const price = 99.99;
     const productInfo = <p>商品价格：${price}</p>;
     ```
   * **函数调用：**
     ```jsx
     function sum(a, b) {
       return a + b;
     }
     const result = <p>2 + 3 = {sum(2, 3)}</p>; // 渲染 "2 + 3 = 5"
     ```
   * **三元表达式 (用于条件渲染)：**
     ```jsx
     const isLoggedIn = true;
     const authStatus = (
       <p>{isLoggedIn ? '已登录' : '未登录'}</p> // 如果 isLoggedIn 为 true，渲染 "已登录"，否则渲染 "未登录"
     );
     ```

**注意：** JSX 中不能直接使用 `if/else` 语句，但可以使用三元表达式或逻辑与 (`&&`)。

---

### 3. Props (属性 / Props)

Props 是 **"properties"** 的缩写。它们是你在创建组件时，从**父组件向子组件传递数据**的方式。

**理解 Props：**
你可以把 Props 想象成 HTML 标签的属性，或者 JavaScript 函数的参数。它们是子组件接收到的配置信息。

**如何传递 Props？**
在父组件的 JSX 中，将数据作为属性传递给子组件：

```jsx
// 父组件 App.jsx
function App() {
  return (
    <div>
      {/* 传递 name 和 age 作为 props 给 GreetUser 组件 */}
      <GreetUser name="小明" age={30} />
      <GreetUser name="小红" age={25} />
    </div>
  );
}
```

**如何接收 Props？**
在子组件的函数定义中，将 `props` 作为第一个参数接收。你可以通过 `props.属性名` 来访问这些数据，或者使用**解构赋值**让代码更简洁。

```jsx
// 子组件 GreetUser.jsx
// 方式一：使用 props 对象
function GreetUser(props) {
  return (
    <p>你好，{props.name}！你今年 {props.age} 岁了。</p>
  );
}

// 方式二：使用解构赋值 (更推荐)
function GreetUser({ name, age }) { // 直接解构出 name 和 age 属性
  return (
    <p>你好，{name}！你今年 {age} 岁了。</p>
  );
}
```

**Props 的重要特性：**

* **只读 (Read-Only)：** 子组件接收到的 Props 是只读的，它不能修改 Props 的值。如果子组件需要改变某些数据，那应该使用它自己的“状态”（State）。
* **单向数据流：** 数据总是从父组件流向子组件。

---

### 4. State (状态 / State)

State 是组件**内部**管理的数据。当 State 发生变化时，React 会重新渲染（更新）组件，从而更新 UI。

**理解 State：**

* Props 是组件从外部接收的数据，是不可变的。
* State 是组件自己维护的数据，是可以改变的，并且改变会触发组件的重新渲染。
* 你可以把 State 想象成组件的“记忆”或者“内部数据存储器”。

**如何在函数式组件中使用 State？**
使用 `useState` 这个 React Hook。

```jsx
import React, { useState } from 'react'; // ① 导入 useState Hook

function Counter() {
  // ② 使用 useState 定义一个状态变量 `count` 和一个更新它的函数 `setCount`
  // `0` 是 `count` 的初始值
  const [count, setCount] = useState(0);

  // ③ 定义一个函数来更新状态
  const increment = () => {
    setCount(count + 1); // 调用 setCount 函数来更新 count 的值
  };

  const decrement = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <p>当前计数：{count}</p> {/* ④ 在 JSX 中使用状态变量 */}
      <button onClick={increment}>增加</button> {/* ⑤ 绑定事件处理函数 */}
      <button onClick={decrement}>减少</button>
    </div>
  );
}

// 在 App 组件中使用 Counter 组件
function App() {
  return (
    <div>
      <h1>我的计数器应用</h1>
      <Counter />
      <Counter /> {/* 你可以多次使用同一个组件，它们各自有独立的 state */}
    </div>
  );
}
```

**`useState` 的返回值：**
`useState` 返回一个数组，通常我们会使用数组解构来获取这两个值：

1. **当前的状态值：** 上面例子中的 `count`。
2. **更新状态的函数：** 上面例子中的 `setCount`。当你调用这个函数并传入新值时，React 会更新状态，并重新渲染组件。

**为什么叫 `useState` 而不是 `userStatus`？**
“userStatus” 可能指的是用户登录状态，那它就是一个具体的 `state` 变量名。`useState` 是 React 提供的一个**通用函数**，用来帮助你管理任何类型的“状态”（state）。

---

### 5. 事件处理 (Event Handling)

在 React 中，事件处理（如点击按钮、输入文字等）与 HTML 类似，但有一些小区别：

* **命名：** React 事件名使用 **驼峰命名法 (camelCase)**，而不是小写。例如：`onClick` 而不是 `onclick`。
* **函数：** 你需要传入一个 JavaScript 函数作为事件处理器的值，而不是一个字符串。

```jsx
function MyButton() {
  const handleClick = () => {
    alert('按钮被点击了！');
  };

  return (
    <button onClick={handleClick}>点击我</button> {/* 传入一个函数 */}
  );
}
```

---

### 6. 条件渲染 (Conditional Rendering)

根据条件显示或隐藏组件或元素。最常用的方法是：

1. **三元表达式 (`condition ? expr1 : expr2`)：**

   ```jsx
   function Greeting({ isLoggedIn }) {
     return (
       <div>
         {isLoggedIn ? (
           <p>欢迎回来！</p>
         ) : (
           <p>请登录。</p>
         )}
       </div>
     );
   }
   ```
2. **逻辑与运算符 (`&&`)：** 当你只想在条件为真时渲染某些内容，否则什么也不渲染时。

   ```jsx
   function WarningSign({ showWarning }) {
     return (
       <div>
         {showWarning && <p style={{ color: 'red' }}>警告：这里有问题！</p>}
       </div>
     );
   }
   ```

   * **原理：** 在 JavaScript 中，`true && expression` 的结果是 `expression`，而 `false && expression` 的结果是 `false`。在 JSX 中，`false`、`null`、`undefined` 都不会被渲染。

---

### 7. 列表渲染 (List Rendering)

当你有一组数据（通常是数组），并希望为数组中的每个项渲染一个组件或元素时，使用 JavaScript 的 `map()` 方法。

**核心：`map()` 方法和 `key` 属性。**

```jsx
function ShoppingList() {
  const items = [
    { id: 1, name: '苹果' },
    { id: 2, name: '香蕉' },
    { id: 3, name: '橙子' },
  ];

  return (
    <ul>
      {items.map(item => (
        // 每个列表项都需要一个唯一的 `key` 属性
        // `key` 帮助 React 识别哪些项发生了变化、被添加或被删除，提高性能
        <li key={item.id}>
          {item.name}
        </li>
      ))}
    </ul>
  );
}
```

**`key` 属性的重要性：**

* `key` 必须是**唯一**的。通常使用数据项的 ID，如果没有 ID，可以使用数组索引，但当列表项顺序可能变化或增删时，不推荐使用索引作为 `key`。
* `key` 只是 React 内部用来优化渲染的提示，它不会作为 props 传递给组件，也不会在 DOM 中显示。

---

### 总结一下：

* **组件：** UI 的基本构建块，是返回 JSX 的 JavaScript 函数。
* **JSX：** 在 JavaScript 中编写类似 HTML 的结构，支持嵌入 JS 表达式。
* **Props：** 从父组件向子组件**传递数据**（只读）。
* **State (`useState`)：** 组件**内部管理**的可变数据，改变时会触发组件重新渲染。
* **事件处理：** 通过 `onClick` 等属性绑定 JS 函数。
* **条件渲染：** 根据条件显示/隐藏元素，常用三元表达式或逻辑与。
* **列表渲染：** 使用 `map()` 遍历数据并为每个项渲染元素，务必添加**唯一的 `key` 属性**。

---

好的，非常理解！我们重新聚焦在 **组件 (Components)** 和 **Hooks** 这两个核心概念上，并进行更深入的理论和实践剖析。这次我确保从您已有的“最基础”理解出发，逐步深入。

---

### 一、组件 (Components) 的深入理解

您已经知道组件是构建 UI 的基本单位，现在我们来深入了解它的哲学、种类、数据流以及如何更好地组织它们。

#### 1. 组件的本质与哲学

* **声明式编程 (Declarative Programming)：** React 的核心思想。你告诉 React 你想要什么状态的 UI，而不是告诉它一步一步如何去操作 DOM（那是命令式编程）。React 会负责将你的声明转换为实际的 DOM 操作。
  * **比喻：** 声明式就像你点菜，只告诉服务员“我要一份红烧肉”，而不用告诉厨师“先切肉、再烧水、再放调料……”。
* **组件化 (Componentization)：** 将复杂的用户界面拆分成独立、可复用的部分。
  * **独立性：** 每个组件应该只关注自己的功能，并尽量少地依赖其他组件的内部实现。
  * **可复用性：** 设计良好的组件可以在不同的地方、不同的场景下重复使用。
  * **可维护性：** 独立的小组件更容易理解、测试和修改。
* **单一职责原则 (Single Responsibility Principle)：** 一个组件应该只做一件事，并且把这件事做好。例如，一个按钮组件只负责按钮的显示和点击事件，而不应该负责处理复杂的表单提交逻辑。

#### 2. 函数式组件 vs. 类组件 (简要了解)

* **函数式组件 (Functional Components)：**
  * **特点：** 普通的 JavaScript 函数，接收 `props` 作为参数，返回 JSX。
  * **优势：** 更简洁、更易读、更易于测试。随着 Hooks 的出现，函数式组件已经成为主流，它也能拥有状态和生命周期等能力。
  * **现代 React 开发的首选。**
* **类组件 (Class Components)：**
  * **特点：** ES6 的类，继承自 `React.Component`，必须有一个 `render()` 方法返回 JSX。
  * **历史作用：** 曾经是唯一拥有 `state` 和生命周期方法的组件类型。
  * **劣势：** 语法相对繁琐，`this` 指向问题，难以复用逻辑。
  * **目前：** 除非维护老项目，新项目基本不推荐使用。

#### 3. Props 的深入理解

您已了解 Props 是从父组件向子组件传递数据的。

* **单向数据流 (Unidirectional Data Flow)：** 这是 React 的核心原则之一。数据总是从父组件流向子组件，子组件不能直接修改接收到的 Props。
  * **Why？** 这种明确的数据流使得应用的状态变化可预测、易于调试。
* **Props 的只读性 (Read-Only)：** 这是至关重要的。如果你在子组件中尝试修改 `props.name = '新名字'`，React 会报错或者行为异常。
  * **Why？** 确保父组件对子组件的控制权，避免子组件“偷偷”改变父组件的数据，造成不可预期的行为。
* **`children` Prop：** 一个特殊的 Prop。
  * **作用：** 允许你将一个或多个 JSX 元素作为子节点直接传递给组件。这对于构建可组合的组件（如布局组件、卡片组件）非常有用。
  * **示例：**
    ```jsx
    // Card.jsx (子组件)
    function Card({ title, children }) { // children 作为 props 接收
      return (
        <div style={{ border: '1px solid gray', padding: '10px', margin: '10px' }}>
          <h2>{title}</h2>
          <div className="card-content">
            {children} {/* 在这里渲染传递进来的子内容 */}
          </div>
        </div>
      );
    }

    // App.jsx (父组件)
    function App() {
      return (
        <div>
          <Card title="我的标题">
            {/* 这里的 P 标签就是 Card 组件的 children prop */}
            <p>这是卡片内部的任意内容。</p>
            <button>点击我</button>
          </Card>
          <Card title="另一个卡片">
            <ul>
              <li>列表项1</li>
              <li>列表项2</li>
            </ul>
          </Card>
        </div>
      );
    }
    ```
* **Prop Drilling (Props 逐层传递问题)：**
  * **问题描述：** 当一个组件需要的数据，是由其祖先组件提供的，但中间隔了很多层组件，这些中间组件本身并不需要这些数据，却不得不将数据一层层地通过 Props 传递下去。这会导致代码变得臃肿、难以维护。
  * **解决方案：** `Context API` (后面 Hooks 部分会详细介绍) 或状态管理库 (如 Redux)。

#### 4. 组件的重新渲染 (Re-rendering)

* **触发条件：** 一个组件会在以下情况重新渲染：
  1. **其自身的 `state` 改变。**
  2. **其父组件重新渲染时 (即使其自身的 `props` 没有变化)。**
  3. **其 `props` 改变时。**
  4. **强制更新 (不推荐)。**
* **重要性：** 理解何时会重新渲染是性能优化的关键。避免不必要的重新渲染可以显著提升应用性能。

---

### 二、Hooks 的深入理解

Hooks 是 React 16.8 引入的革命性功能，它让函数式组件也能拥有状态 (State) 和生命周期 (Lifecycle) 等能力，同时解决了类组件的一些痛点。

#### 1. Hooks 的核心理念

* **为什么需要 Hooks？**
  * **告别 `class` 带来的困扰：** 解决了 `this` 指向问题，以及 `class` 语法相对冗余的问题。
  * **逻辑复用：** 解决了类组件中 HOC (高阶组件) 和 Render Props 模式带来的“嵌套地狱”和代码结构复杂问题。Hooks 允许你将组件之间的可复用状态逻辑提取出来，形成独立的“自定义 Hook”。
  * **清晰的逻辑分离：** `useEffect` 让你将关注点分离的代码写在一起（例如，数据获取和清理），而不是像类组件那样分散在不同的生命周期方法中。
* **Hooks 的规则 (Rules of Hooks)：** 这是使用 Hooks 的强制性规则，非常重要！
  1. **只能在 React 函数式组件的顶层调用 Hook。** 不要再循环、条件语句或嵌套函数中调用 Hook。
     * **Why？** React 依赖于 Hook 的调用顺序来正确地关联 `state` 和 `effect`。条件调用会破坏这个顺序。
  2. **只能在 React 函数式组件或自定义 Hook 中调用 Hook。** 不要再普通的 JavaScript 函数中调用它们。
     * **Why？** Hook 依赖于 React 内部的机制，这些机制只在组件上下文中可用。

#### 2. `useState` 的深入理解

您已了解 `useState` 用来给函数式组件添加状态。

* **状态的异步更新与批处理 (Asynchronous Updates & Batching)：**
  * `setCount` 或任何 `setSomething` 函数的调用是**异步**的。这意味着在你调用 `setCount` 后，`count` 的值不会立即改变，它会在下一次组件渲染时才更新。
  * React 会将多个状态更新请求进行**批处理**，然后一次性进行重新渲染。这可以提高性能，避免不必要的多次渲染。
    ```jsx
    // 假设初始 count = 0
    function MyComponent() {
      const [count, setCount] = useState(0);

      const handleClick = () => {
        setCount(count + 1); // 此时 count 仍然是 0
        setCount(count + 1); // 此时 count 仍然是 0，结果 count 最终会是 1 (因为两次都基于 0 + 1)
        // React 会将这两个更新批处理，最终 count 会变成 1。
        console.log(count); // 仍然是旧值 0
      };

      return <button onClick={handleClick}>{count}</button>;
    }
    ```
* **函数式更新 (Functional Updates)：** 当新状态依赖于前一个状态时，推荐向 `setSomething` 传递一个函数，而不是直接传递值。
  * **作用：** 这个函数会接收上一个状态值作为参数，并返回新的状态值。这可以确保你在更新时总是使用最新的状态，避免闭包陷阱或竞态条件。
    ```jsx
    // 正确的递增方式
    setCount(prevCount => prevCount + 1); // 推荐
    setCount(prevCount => prevCount + 1); // 第二次调用会基于第一次更新后的值

    // 使用函数式更新，最终 count 会是 2
    ```
* **不可变性 (Immutability) 在 State 中的重要性：**
  * **核心：** 当状态是对象或数组时，**绝不能直接修改原始对象或数组**。你必须创建一个新的副本，然后在新副本上进行修改。
  * **Why？** React 的 `Diffing` 算法通过比较引用来判断状态是否发生变化。如果你直接修改了原对象/数组，引用不变，React 可能认为状态没有变化，从而不触发重新渲染。
  * **正确操作：**
    * **数组：** 使用 `map()`, `filter()`, `concat()`, `slice()`, 或展开运算符 `[...originalArray, newItem]`。
    * **对象：** 使用展开运算符 `{...originalObject, newProperty: newValue}`。
  * **示例：**
    ```jsx
    function ListEditor() {
      const [items, setItems] = useState(['Apple', 'Banana']);

      const addItem = () => {
        // 错误：直接修改原数组
        // items.push('Orange');
        // setItems(items); // ❌ 这样可能不会触发更新，或者行为异常

        // 正确：创建一个新数组
        setItems(prevItems => [...prevItems, 'Orange']);
      };

      const updateFirstItem = () => {
        // 正确：创建一个新数组，其中包含更新后的第一个元素
        setItems(prevItems => [
          'New ' + prevItems[0],
          ...prevItems.slice(1)
        ]);
        // 或者更通用的做法 (如果需要按ID更新复杂对象数组)
        // setItems(prevItems => prevItems.map(item => item.id === someId ? { ...item, name: 'Updated Name' } : item));
      };

      return (
        <div>
          <ul>
            {items.map((item, index) => <li key={index}>{item}</li>)}
          </ul>
          <button onClick={addItem}>Add Orange</button>
          <button onClick={updateFirstItem}>Update First Item</button>
        </div>
      );
    }
    ```

#### 3. `useEffect` 的深入理解

您已了解 `useEffect` 用于处理副作用。

* **副作用 (Side Effects)：** 指那些不在 React 渲染流程中发生的操作，但又依赖于 React 组件生命周期的行为，例如：

  * 数据获取 (AJAX 请求)
  * 订阅外部数据源 (WebSocket, 事件监听)
  * 手动修改 DOM
  * 设置计时器 (setTimeout, setInterval)
  * 记录日志
* **依赖项数组 (Dependency Array `[]`)：** 这是 `useEffect` 最关键的部分，它控制着 `effect` 何时重新运行。

  * **空数组 `[]`：** `effect` 只在组件**挂载 (Mount)** 后运行一次，并在组件**卸载 (Unmount)** 前执行清理函数（如果返回了清理函数）。这模仿了类组件的 `componentDidMount` 和 `componentWillUnmount`。
    ```jsx
    useEffect(() => {
      console.log('组件第一次渲染后执行，只执行一次。');
      const timer = setInterval(() => console.log('计时器'), 1000);
      return () => {
        // 清理函数：在组件卸载前或下次 effect 运行前执行
        console.log('组件卸载或 effect 重新执行前清理计时器。');
        clearInterval(timer);
      };
    }, []); // 空数组
    ```
  * **有依赖项的数组 `[dep1, dep2]`：** `effect` 会在组件挂载后运行一次，并在**任何一个依赖项发生变化**时重新运行。这模仿了 `componentDidUpdate`。
    ```jsx
    useEffect(() => {
      console.log('用户名或主题变化了，重新加载数据或更新UI。');
      // 假设这里会发起一个网络请求，依赖于 username 和 theme
      // fetchData(username, theme);
    }, [username, theme]); // 当 username 或 theme 变化时执行
    ```
  * **没有依赖项数组 (不推荐，除非你知道自己在做什么)：** `effect` 会在每次组件重新渲染后都运行。这可能导致无限循环或性能问题。
* **清理函数 (Cleanup Function)：** `useEffect` 的一个重要特性是它可以返回一个函数，这个函数会在以下两种情况被执行：

  1. 组件卸载之前。
  2. 下一次 `effect` 运行之前（清理上一次的 `effect`）。

  * **作用：** 防止内存泄漏，确保副作用被正确地清理（例如，取消订阅、清除计时器）。
* **`useEffect` 的执行时机：** `useEffect` 中的函数是在浏览器完成**渲染后**才异步执行的。这意味着它不会阻塞 UI 的绘制。

  * **`useLayoutEffect`：** 少数情况下，如果你需要在 DOM 更新后、浏览器绘制之前**同步**执行一些副作用（例如测量 DOM 元素尺寸以进行布局调整），可以使用 `useLayoutEffect`。但它会阻塞浏览器绘制，所以要谨慎使用。

#### 4. `useContext` (解决 Prop Drilling)

* **作用：** 提供一种跨组件层级共享数据的方式，而无需手动通过 Props 逐层传递。
* **概念：**
  * `Context` 对象：通过 `React.createContext()` 创建。
  * `Provider` (提供者)：一个组件，将 `Context` 的值提供给其所有后代组件。
  * `Consumer` (消费者)：一个组件，可以访问 `Context` 提供的值。
* **使用 `useContext` Hook：** 在函数式组件中消费 `Context` 的更简洁方式。
  * **示例：**
    ```jsx
    // 1. 创建 Context (通常在一个单独的文件中)
    const ThemeContext = React.createContext('light'); // 默认值 'light'

    // 2. 提供 Context 值 (在父组件中)
    function App() {
      const [theme, setTheme] = useState('light'); // 假设主题可以切换

      const toggleTheme = () => {
        setTheme(prevTheme => prevTheme === 'light' ? 'dark' : 'light');
      };

      return (
        <ThemeContext.Provider value={theme}> {/* 提供 'theme' 值 */}
          <button onClick={toggleTheme}>切换主题</button>
          <Toolbar />
        </ThemeContext.Provider>
      );
    }

    // 3. 消费 Context 值 (在任意深度的子孙组件中)
    function Toolbar() {
      return (
        <div>
          <ThemedButton />
        </div>
      );
    }

    function ThemedButton() {
      const theme = React.useContext(ThemeContext); // 使用 useContext 消费 Context 值
      return (
        <button style={{ background: theme === 'dark' ? 'black' : 'white', color: theme === 'dark' ? 'white' : 'black' }}>
          我是一个主题按钮 ({theme})
        </button>
      );
    }
    ```
* **何时使用：** 当多个组件需要访问相同的数据（如主题、认证信息、语言设置）时，`useContext` 是一个很好的选择。它避免了 Props 逐层传递的麻烦。

#### 5. `useReducer` (管理复杂状态逻辑)

* **作用：** `useReducer` 是 `useState` 的替代方案，用于管理更复杂的状态逻辑，特别是当状态更新依赖于前一个状态，或涉及多个子状态时。
* **概念：** 类似于 Redux 的简化版，但只作用于单个组件内部。
  * `reducer` 函数：一个纯函数，接收当前 `state` 和一个 `action` 对象，返回一个新的 `state`。
  * `initialState`：状态的初始值。
  * `dispatch` 函数：用于触发状态更新的函数，它接收一个 `action` 对象。
* **何时使用：**
  * 状态逻辑复杂，包含多个相互关联的子值。
  * 下一个状态依赖于上一个状态。
  * 需要对状态更新进行更精细的控制或调试。
* **示例：**
  ```jsx
  const initialState = { count: 0, loading: false };

  function reducer(state, action) {
    switch (action.type) {
      case 'increment':
        return { ...state, count: state.count + 1 };
      case 'decrement':
        return { ...state, count: state.count - 1 };
      case 'set_loading':
        return { ...state, loading: action.payload };
      default:
        throw new Error('未知 action 类型');
    }
  }

  function ComplexCounter() {
    const [state, dispatch] = React.useReducer(reducer, initialState);

    const fetchData = () => {
      dispatch({ type: 'set_loading', payload: true });
      // 模拟异步数据获取
      setTimeout(() => {
        dispatch({ type: 'increment' });
        dispatch({ type: 'set_loading', payload: false });
      }, 1000);
    };

    return (
      <div>
        <p>Count: {state.count}</p>
        <p>Loading: {state.loading ? 'Yes' : 'No'}</p>
        <button onClick={() => dispatch({ type: 'increment' })}>增加</button>
        <button onClick={() => dispatch({ type: 'decrement' })}>减少</button>
        <button onClick={fetchData} disabled={state.loading}>
          {state.loading ? '加载中...' : '异步增加'}
        </button>
      </div>
    );
  }
  ```

#### 6. `useRef` (直接访问 DOM 或持久化值)

* **作用：** 创建一个可变的 `ref` 对象，其 `.current` 属性可以存储任何可变值，并且在组件的整个生命周期中保持不变，即使组件重新渲染也不会丢失。
* **何时使用：**
  1. **直接操作 DOM 元素：** 例如获取输入框的焦点、播放/暂停视频、测量元素尺寸等。
  2. **在多次渲染之间持久化一个值：** 这个值不会触发组件重新渲染（不像 `useState`）。例如，存储计时器的 ID、保存上一次渲染的值。
* **与 `useState` 的区别：**
  * `useRef` 改变 `.current` **不会**触发组件重新渲染。
  * `useState` 改变状态**会**触发组件重新渲染。
* **示例：**
  ```jsx
  function TextInputWithFocusButton() {
    const inputRef = React.useRef(null);
    const timerIdRef = React.useRef(null); // 用于保存计时器ID，不触发渲染

    const focusInput = () => {
      inputRef.current.focus(); // 直接操作 DOM 元素
    };

    const startTimer = () => {
      if (!timerIdRef.current) {
        timerIdRef.current = setInterval(() => {
          console.log('Timer running...');
        }, 1000);
      }
    };

    const stopTimer = () => {
      if (timerIdRef.current) {
        clearInterval(timerIdRef.current);
        timerIdRef.current = null;
      }
    };

    // 清理计时器，防止内存泄漏
    React.useEffect(() => {
      return () => {
        if (timerIdRef.current) {
          clearInterval(timerIdRef.current);
        }
      };
    }, []);

    return (
      <div>
        <input ref={inputRef} type="text" />
        <button onClick={focusInput}>聚焦输入框</button>
        <button onClick={startTimer}>开始计时器</button>
        <button onClick={stopTimer}>停止计时器</button>
      </div>
    );
  }
  ```

#### 7. `useCallback` 和 `useMemo` (性能优化 Hooks)

这两个 Hooks 都用于**记忆化 (Memoization)**，以避免不必要的计算或函数重新创建，从而优化性能。

* **`useCallback`：记忆化函数**
  * **作用：** 缓存一个函数定义。它返回一个记忆化的回调函数，只有当其**依赖项**发生变化时，才会重新创建该函数。
  * **何时使用：** 当你将函数作为 Props 传递给经过 `React.memo` 优化的子组件时。如果父组件重新渲染导致函数引用改变，即使子组件的 Props 看起来没变，`React.memo` 也会失效。`useCallback` 解决了这个问题。
  * **示例：**
    ```jsx
    // MemoizedChild.jsx
    const MemoizedChild = React.memo(({ onClick }) => {
      console.log('MemoizedChild 渲染');
      return <button onClick={onClick}>点击我 (子组件)</button>;
    });

    // ParentComponent.jsx
    function ParentComponent() {
      const [count, setCount] = React.useState(0);

      // 如果没有 useCallback，每次 ParentComponent 渲染，handleClick 都会是新的函数引用
      // 导致 MemoizedChild 即使 props 没变也会重新渲染。
      const handleClick = React.useCallback(() => {
        console.log('按钮被点击了！');
      }, []); // 空数组表示这个函数只在组件挂载时创建一次，永远不变

      return (
        <div>
          <p>父组件计数: {count}</p>
          <button onClick={() => setCount(count + 1)}>增加父组件计数</button>
          <MemoizedChild onClick={handleClick} />
        </div>
      );
    }
    ```
* **`useMemo`：记忆化值 (计算结果)**
  * **作用：** 缓存一个计算结果。它返回一个记忆化的值，只有当其**依赖项**发生变化时，才会重新计算该值。
  * **何时使用：** 当某个计算成本很高（例如，大数据量的过滤、排序或复杂数学运算），并且这个计算结果在多次渲染之间可以复用时。
  * **示例：**
    ```jsx
    function ExpensiveCalculation() {
      const [count, setCount] = React.useState(0);
      const [text, setText] = React.useState('');

      // 模拟一个昂贵的计算
      const expensiveValue = React.useMemo(() => {
        console.log('正在执行昂贵的计算...');
        // 假设这里有一个非常耗时的计算，依赖于 count
        let result = 0;
        for (let i = 0; i < 100000000; i++) {
          result += i;
        }
        return result + count;
      }, [count]); // 只有当 count 变化时，才会重新执行上面的计算

      return (
        <div>
          <input value={text} onChange={e => setText(e.target.value)} placeholder="输入文本，不会触发昂贵计算" />
          <button onClick={() => setCount(count + 1)}>增加计数: {count}</button>
          <p>昂贵的计算结果: {expensiveValue}</p>
        </div>
      );
    }
    ```
* **`React.memo` (用于函数式组件的性能优化)：**
  * **作用：** 一个高阶组件 (HOC)，如果函数式组件的 `props` 没有变化，则跳过该组件的重新渲染。
  * **注意：** 它进行的是**浅比较**。如果 `props` 包含引用类型（函数、对象、数组），即使它们内容相同但引用变了，`React.memo` 也会导致重新渲染。这就是为什么 `useCallback` 和 `useMemo` 经常需要与 `React.memo` 配合使用。

#### 8. 自定义 Hooks (Custom Hooks)

* **作用：** 提取和复用组件之间的状态逻辑。它们是 React Hooks 模式中最强大的功能之一。
* **本质：** 一个普通的 JavaScript 函数，但它**内部会调用一个或多个其他的 Hook**（如 `useState`, `useEffect`, `useContext` 等）。
* **命名约定：** 自定义 Hook 的名称总是以 `use` 开头（例如 `useToggle`, `useFetchData`）。这是 Hook 规则的一部分。
* **何时使用：** 当你在多个组件中发现相同的状态管理或副作用逻辑时，可以将它们提取到一个自定义 Hook 中。
* **优势：**
  * **逻辑复用：** 避免代码重复。
  * **关注点分离：** 将复杂的状态逻辑与 UI 渲染逻辑分离。
  * **可读性：** 使组件代码更简洁、更易于理解。
* **示例：**
  ```jsx
  // useToggle.js (自定义 Hook 文件)
  import { useState, useCallback } from 'react';

  function useToggle(initialState = false) {
    const [state, setState] = useState(initialState);

    // 使用 useCallback 确保 toggle 函数的引用稳定
    const toggle = useCallback(() => setState(prev => !prev), []);

    return [state, toggle]; // 返回状态和更新函数
  }

  export default useToggle;

  // MyComponent.jsx (使用自定义 Hook)
  import React from 'react';
  import useToggle from './useToggle'; // 导入自定义 Hook

  function MyComponent() {
    const [isOn, toggle] = useToggle(false); // 使用自定义 Hook

    return (
      <div>
        <p>当前状态: {isOn ? '开' : '关'}</p>
        <button onClick={toggle}>切换</button>
      </div>
    );
  }

  function AnotherComponent() {
    const [isVisible, toggleVisibility] = useToggle(true); // 另一个组件也可以复用这个逻辑

    return (
      <div>
        {isVisible && <p>我现在可见！</p>}
        <button onClick={toggleVisibility}>切换可见性</button>
      </div>
    );
  }
  ```

---
