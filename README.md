# simple JS   sample
---

# keyword `this`＆ Vue


## (A) summary 
#### (A-1)  Priority

0. < 例外 > arrow Function  ( 沒自己的 this)

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
1. callback （回呼函式）
2. Promise
3. Async/Await
4. Prototype
5. class
6. Prototype Chain
7. Module
8. Deep Copy___blog
9. RESTful
10. Fetch
11. 正則 Regular Expression
12. arrFn (沒有自己的this、arguments、super、new.target )
13. setTimeout、setInterval
---

## Vue
- v-bind
- v-on
- v-if . v-for
- v-model
- computed(Setter)
- Prop(Prop Validation. $attrs). Emit（.native & .sync）
- Mixin
- Slot
- Vuex ( State/ Getters / Mutations/ Actions )（namespace）
- Module
- Vue Router ( query / params . Navigation Guards.  linkActiveClass.  active-class.passing-props)
- Watch
- slot(v-slot . Scoped Slots)
```
vm.$watch( expOrFn, callback, [options] )
```
- Life Cycle ( Hook function )
- vue 3（ composition api. $attrs . conditional rendering] . communicating Events . Event Handling .  Class and Style Bindings ）

- ES6 (in Vue): Spread Operator . Destructuring assignment . Class( constructor , ...... ) . Module .Scope

```
//wrong
{a, b} = {a: 1, b: 2}

//correct
({a, b} = {a: 1, b: 2}) 

```
- UI
- Axios(in Vue)

## 資源
- 隨機圖產生器（Fake Image Snippet Collection 外掛 in VScode :輸入 picsum 即可）

```
<img src="https://picsum.photos/80?random=1">
<img src="https://fakeimg.pl/350x200/ff0000/000">
```

# others
- Scss(Syntax ,  mixin ,  function  ,   extend ,   variable)
```
@mixin name(<arguments...>) { ... }

@include <name>(<arguments...>)
```
