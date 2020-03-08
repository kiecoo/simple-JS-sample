# simple-JS-sample
---
# 淺顯易懂的 keyword this
## (A) summery
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
#### ① 無return ＝>自動return 新對象
```
function User(){
    this.name = "amy";  // this绑定到obj上
    console.log(this)
}

User(); //this是windows 

var obj = new User(); //User{name: "amy"}  //新對象(obj＝甲)綁定到此函數(User)的this上
console.log(obj) //User{name: "amy"}
obj.name; //"amy"
```
