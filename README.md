# simple-JS-sample
---
# 淺顯易懂的 keyword this
## (A) summary
#### (A-1) 優先順序
0. <例外> arrow Function 
1. new構造函數
2. apply、call或bind
3. obj調用
4. 普通調用（非obj 調用）

---
## (B) 概念
- 誰"調用"它，this就指向誰 (arrow Function 除外)
---
## (C) this的四種綁定規則：
#### (C-1) new構造函數
```js
// a-用new 調用
function User(name) {
    this.name = name;
    console.log(this)  //User {name: "Amy"}
}
var obj = new User('Amy');
---------
// b-不用new 調用
function User(name) {
    this.name = name;
    console.log(this)  //Window
}
User('Amy')
```
#### ① 無return ＝>自動return 新對象
```js
function User(){
    this.name = "amy";  // this绑定到obj上
    console.log(this)  //User{name: "amy"} 
}

User(); //this是window

var obj = new User();  //新對象(obj＝甲)綁定到此函數(User)的this上
console.log(obj) //User{name: "amy"}
obj.name; //"amy"
```
#### ② 有return值 ＝> this指向乙
```js
function User(){
    this.name = "amy";
    return {name:"Bob"}; // return 乙對象{name:"Bob"}
}

var obj = new User(); 
console.log(obj) //{name:"Bob"}
obj.name;   //Bob
```
#### (C-2) apply、call或bind
```js
fn.call(obj, 'arg1', 'arg2');
fn.apply(obj, ['arg1', 'arg2']);
fn.bind(obj, 'arg1', 'arg2')();
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

//① call
User.call(obj, 'Amy', 10);
//② apply
User.apply(obj, ['Amy', 10]);
//③
var u1 = User.bind(obj, 'Amy', 10)
var u2 = new u1();
```
