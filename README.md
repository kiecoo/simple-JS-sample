# simple JS sample
---
# keyword `this`＆ Vue

## (A) summary 
#### (A-1)  Priority

0. < 例外 > arrow Function  ( 沒 自己的this)

1. new 構造函數
2. apply、call、bind
3. obj 調用
4. 普通調用（ 非 obj 調用 ）

---

## (B) 概念

誰"調用"它，this 就指向誰  ( arrow Function 除外 )

---

## (C) this 四種綁定規則

#### (C-1) new 構造函數

```js

// a-用 new 調用

function User(name) {
    this.name = name;
    console.log(this)  // User {name: "Amy"}
}

var obj = new User('Amy');

---------

// b-不用 new 調用

function User(name) {
    this.name = name;
    console.log(this)  // Window
}

User('Amy')

```
#### 1 無 return ＝> 自動 return 新對象

```js

function User(){
    this.name = "amy";  // this 绑定到 obj 上
    console.log(this)  // User {name: "amy"} 
}

User();   //this 是 window

var obj = new User();  //新對象(obj＝甲)綁定到此函數(User)的this
console.log(obj) // User{name: "amy"}
obj.name; //"amy"

```

#### 2 有 return 值 ＝> this 指向 乙

```js

function User(){
    this.name = "amy";
    return {name:"Bob"}; // return 乙對象 {name:"Bob"}
}

var obj = new User(); 
console.log(obj) // { name:"Bob"}
obj.name;   //Bob

```
#### (C-2) apply、call、bind

```js

fn.call(obj, 'arg1', 'arg2'); // 1. call
fn.apply(obj, ['arg1', 'arg2']); // 2. apply
fn.bind(obj, 'arg1', 'arg2')(); // 3. bind

```

```js

function User(name, luckyNum) {
  this.name = name;
  this.luckyNum = luckyNum;
  console.log(this);
}

var obj = {
  name: 'Bob',
  luckyNum: 6
};

//  1. call
User.call(obj, 'Amy', 10);

//  2. apply
User.apply(obj, ['Amy', 10]);

//  3. bind
var u1 = User.bind(obj, 'Amy', 10)
var u2 = new u1();

```

---

## (D) List
1. [callback](https://developer.mozilla.org/zh-TW/docs/Glossary/Callback_function) （回呼函式）
2. [Promise](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Promise)
3. [Async/Await](https://zhuanlan.zhihu.com/p/72036724)
4. Prototype
5. [class](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Classes)
6. Prototype Chain
7. Module
8. [Deep Copy___blog](https://kanboo.github.io/2018/01/27/JS-ShallowCopy-DeepCopy/)
9. [RESTful](https://medium.com/itsems-frontend/api-%E6%98%AF%E4%BB%80%E9%BA%BC-restful-api-%E5%8F%88%E6%98%AF%E4%BB%80%E9%BA%BC-a001a85ab638)
10. [Fetch](https://developer.mozilla.org/zh-TW/docs/Web/API/Fetch_API/Using_Fetch)
11. 正則 [Regular Expression](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Regular_Expressions)
12. [arrFn](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/Arrow_functions) (沒有自己的[this](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/this)、[arguments](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/arguments)、[super](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/super)、new.target )
13. [setTimeout](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/setTimeout)、[setInterval](https://www.w3schools.com/jsref/met_win_setinterval.asp)

---

## Vue
- [v-bind](https://vuejs.org/v2/guide/class-and-style.html)
- [v-on](https://vuejs.org/v2/guide/events.html)
- [v-if](https://vuejs.org/v2/guide/conditional.html) . [v-for](https://vuejs.org/v2/guide/list.html)
- [v-model](https://vuejs.org/v2/guide/forms.html)
- [computed](https://vuejs.org/v2/guide/computed.html#Computed-Properties)([Setter](https://vuejs.org/v2/guide/computed.html#Computed-Setter))
- [Prop](https://vuejs.org/v2/guide/components-props.html) ([Prop Validation](https://vuejs.org/v2/guide/components-props.html#Prop-Validation). [$attrs](https://vuejs.org/v2/guide/components-props.html#Disabling-Attribute-Inheritance)). [Emit](https://vuejs.org/v2/guide/components-custom-events.html)（[.native](https://vuejs.org/v2/guide/components-custom-events.html#Binding-Native-Events-to-Components) & [.sync](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)）
- [Mixin](https://vuejs.org/v2/guide/mixins.html)
- [Slot](https://vuejs.org/v2/guide/components-slots.html) 
- [Vuex](https://vuex.vuejs.org/guide/) ( [State](https://vuex.vuejs.org/guide/state.html) / [Getters](https://vuex.vuejs.org/zh/guide/getters.html) / [Mutations](https://vuex.vuejs.org/zh/guide/mutations.html) / [Actions](https://vuex.vuejs.org/guide/actions.html) )（[namespace](https://vuex.vuejs.org/guide/modules.html#namespacing)）
- [Module](https://vuex.vuejs.org/guide/modules.html)
- [Vue Router](https://router.vuejs.org/) ( query / [params](https://router.vuejs.org/guide/essentials/navigation.html) . [Navigation Guards](https://router.vuejs.org/guide/advanced/navigation-guards.html).  [linkActiveClass](https://router.vuejs.org/api/#linkactiveclass).  [active-class](https://router.vuejs.org/api/#active-class))
- [Watch](https://vuejs.org/v2/api/#vm-watch)
- [slot](https://vuejs.org/v2/guide/components-slots.html)([v-slot](https://vuejs.org/v2/guide/components-slots.html) . [Scoped Slots](https://vuejs.org/v2/guide/components-slots.html#Named-Slots))
```
vm.$watch( expOrFn, callback, [options] )
```
- [Life Cycle](https://vuejs.org/v2/guide/instance.html#Instance-Lifecycle-Hooks) ( [Hook function](https://vuejs.org/v2/api/#Options-Lifecycle-Hooks) )
- [vue 3](https://v3.vuejs.org/guide/introduction.html) （ [composition api](https://composition-api.vuejs.org/#api-introduction) . [$attrs](https://v3.vuejs.org/guide/migration/attrs-includes-class-style.html#_3-x-behavior) . [conditional rendering](https://v3.vuejs.org/guide/conditional.html#conditional-rendering) . communicating Events . [Event Handling](https://v3.vuejs.org/guide/events.html) .  [Class and Style Bindings](https://v3.vuejs.org/guide/class-and-style.html) ）

- ES6 (in Vue): [Spread Operator](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Spread_syntax) . [Destructuring assignment](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) . [Class](https://github.com/ruanyf/es6tutorial/blob/04dddb2d7c34cbcd90a0bd1f027835bd744bf827/docs/class.md) ( [constructor](https://github.com/ruanyf/es6tutorial/blob/04dddb2d7c34cbcd90a0bd1f027835bd744bf827/docs/class.md#constructor-%E6%96%B9%E6%B3%95) , ...... ) . [Module](https://github.com/ruanyf/es6tutorial/blob/04dddb2d7c34cbcd90a0bd1f027835bd744bf827/docs/module.md) .Scope

```
//wrong
{a, b} = {a: 1, b: 2}

//correct
({a, b} = {a: 1, b: 2}) 

```
- UI
- [Axios](https://vuejs.org/v2/cookbook/using-axios-to-consume-apis.html) (in Vue)

## 資源
- [隨機圖產生器](https://picsum.photos/)（Fake Image Snippet Collection 外掛 in VScode :輸入 picsum 即可）

```
<img src="https://picsum.photos/80?random=1">
<img src="https://fakeimg.pl/350x200/ff0000/000">
```

# others
- [Scss](https://sass-lang.com/documentation/syntax#scss) ([Syntax](https://sass-lang.com/documentation/syntax#scss) ,  [mixin](https://sass-lang.com/documentation/at-rules/mixin) ,  [function](https://sass-lang.com/documentation/at-rules/function)  ,   [extend](https://sass-lang.com/documentation/at-rules/extend) ,   [variable](https://sass-lang.com/documentation/variables))
```
@mixin name(<arguments...>) { ... }

@include <name>(<arguments...>)
```
