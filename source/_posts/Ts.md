---
title: Ts
date: 2024-12-08 14:06:57
categories:
  - Ts
tags:
  - Ts
---

### Ts 介绍

**TypeScript 是由微软开发的，基于 JavaScript（JS）的一个扩展语言，包含 JS 所有内容，并增加了静态类型检查、接口、泛型等特性.**

**Ts 支持静态类型检查,在代码运行前进行检查,减少运行异常的概率.同样的功能,Ts 的代码量大于 Js,但是代码结构更加清晰,更加便于维护.**

**Ts 编译:Ts 不能直接被浏览器运行,需要先编译为 Js,再交由浏览器解析执行.(vue,react 基于 webpack,vite 等配置进行 Ts 编译)**

<details class="lake-collapse"><summary id="uf812c35c"><span class="ne-text">1.命令行编译</span></summary><p id="u4edc343b" class="ne-p" style="text-indent: 2em"><span class="ne-text">安装ts,命令npm i typescript -g(全局安装) ,编译命令tsc &lt;ts文件&gt;解析编译出ts文件对应的js文件</span></p></details>
<details class="lake-collapse"><summary id="uf7a681eb"><span class="ne-text">2.自动化编译</span></summary><p id="u27e3738b" class="ne-p" style="text-indent: 2em"><span class="ne-text">同样先全局安装ts,输入命令tsc --init,生成tsconfig.json配置文件.</span></p><p id="u692d87af" class="ne-p" style="text-indent: 2em"><span class="ne-text">ts --watch监视全部ts文件,也可监视单个ts文件</span></p><p id="ufea8de56" class="ne-p"><span class="ne-text">	技巧:当出现错误时,不进行编译 tsc --noEmitOnError --watch(也可直接修改tsconfig.json的noEmitOnError 属性)</span></p></details>

对于变量,函数进行基本的类型声明

```typescript
let a: string;
let b: number;
let c: boolean;
a = "hello";
b = 1;
c = true;
function fn(x: number, y: number): number {
  return x + y;
}
fn(1, 2);
```

Ts 类型推断,Ts 会根据代码进行类型推断,面对复杂类型可能出错,尽量明确编写的类型声明

```typescript
let d= 99
d='123
```

### 基础类型总览

<details class="lake-collapse"><summary id="uaabb7dd7"><span class="ne-text">js中的数据类型</span></summary><p id="ua5bf1f19" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">① string </span></p><p id="ub8258016" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">② </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">number </span></p><p id="u306b5347" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">③ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">boolean </span></p><p id="ud79c25c0" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">④ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">null </span></p><p id="u17e78bca" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">⑤ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">undefined </span></p><p id="u0d936672" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">⑥ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">bigint </span></p><p id="ud4c5383f" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">⑦ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">symbol </span></p><p id="u6ecacdea" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">⑧ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">object </span></p><p id="u1b4cd798" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">备注：其中 object 包含： Array 、 Function 、 Date 、 Error 等.....</span></p></details>
<details class="lake-collapse"><summary id="u32dbb78f"><span class="ne-text">ts中的数据类型</span></summary><p id="u2ff6582f" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">1. 上述所有 JavaScript 类型 </span></p><p id="u590a9d1e" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">2. </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">六个新类型： </span></p><p id="u01c33d3a" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">① </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">any </span></p><p id="u76ff1110" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">② </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">unknown </span></p><p id="u56d902db" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">③ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">never </span></p><p id="u4585c27d" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">④ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">void </span></p><p id="u57ba264a" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">⑤ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">tuple </span></p><p id="ue42ab522" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">⑥ </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">enum </span></p><p id="ud2723297" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">3. </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">两个⽤于⾃定义类型的⽅式： </span></p><p id="u0254fc1f" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">① </span><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">type </span></p><p id="u2451c65d" class="ne-p"><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">② interface</span></p></details>

:::info
注意:<font style="color:rgb(38,38,38);">在 JavaScript 中的这些内置构造函数： Number 、 String 、 Boolean ，⽤于 </font>

<font style="color:rgb(38,38,38);">创建对应的包装对象， 在⽇常开发时</font><font style="color:rgb(173,26,43);">很少使⽤</font><font style="color:rgb(38,38,38);">，在 </font><font style="color:rgb(38,38,38);">TypeScript </font><font style="color:rgb(38,38,38);">中也是同理，所以 </font>

<font style="color:rgb(38,38,38);">在 </font><font style="color:rgb(38,38,38);">TypeScript </font><font style="color:rgb(38,38,38);">中进⾏类型声明时，通常都是⽤⼩写的 </font><font style="color:rgb(38,38,38);">number </font><font style="color:rgb(38,38,38);">、 </font><font style="color:rgb(38,38,38);">string </font><font style="color:rgb(38,38,38);">、 </font><font style="color:rgb(38,38,38);">bo </font>

<font style="color:rgb(38,38,38);">olean</font>

1. <font style="color:rgb(38,38,38);">原始类型 VS 包装对象  
   </font><font style="color:rgb(38,38,38);">原始类型：如 number 、 string 、 boolean ，在 JavaScript 中是简单数据  
   </font><font style="color:rgb(38,38,38);">类型，它们在内存中占⽤空间少，处理速度快。  
   </font><font style="color:rgb(38,38,38);">包装对象：如 Number 对象、 String 对象、 Boolean 对象，是复杂类型，在  
   </font><font style="color:rgb(38,38,38);">内存中占⽤更多空间，在⽇常开发时很少由开发⼈员⾃⼰创建包装对象。</font>
2. <font style="color:rgb(38,38,38);">⾃动装箱：JavaScript 在必要时会⾃动将原始类型包装成对象，以便调⽤⽅法或访  
   </font><font style="color:rgb(38,38,38);">问属性</font>

:::

```typescript
// 原始类型字符串
let str = "hello";
// 当访问str.length时，JavaScript引擎做了以下⼯作：
let size = (function () {
  // 1. ⾃动装箱：创建⼀个临时的String对象包装原始字符串
  let tempStringObject = new String(str);
  // 2. 访问String对象的length属性
  let lengthValue = tempStringObject.length;
  // 3. 销毁临时对象，返回⻓度值
  // （JavaScript引擎⾃动处理对象销毁，开发者⽆感知）
  return lengthValue;
})();
console.log(size); // 输出: 5
```

#### 基础类型

**any:**任意类型,<font style="color:rgb(38,38,38);">可以赋值给任意类型的变量(容易造成类型错误,比如将一个 any 类型的数据赋值给一个 string 类型的数据),不进行声明时 Ts 会判断为隐式 any.</font>

**<font style="color:rgb(38,38,38);">unknow:</font>**<font style="color:rgb(38,38,38);">可以理解为一个类型安全的 any,适⽤于：起初不确定数据的具体类型，要后期才能确定.使用时强制开发者进行类型判断,从而保证类型安全.(可以使用断言进行强制推断)</font>

:::info
**<font style="color:rgb(38,38,38);">tip(断言):</font>**

<font style="color:rgb(38,38,38);">第 1 种⽅式  
</font><font style="color:rgb(38,38,38);">x = a as string  
</font><font style="color:rgb(38,38,38);">第 2 种⽅式  
</font><font style="color:rgb(38,38,38);">x = <string>a</font>

:::

**never**:不是任何值,一般不主动使用(无意义),一般由 ts 进行类型推断,推断为"never".

```typescript
// 指定a的类型为string
let a: string;
// 给a设置⼀个值
a = "hello";
if (typeof a === "string") {
  console.log(a.toUpperCase());
} else {
  console.log(a); // TypeScript会推断出此处的a是never，因为没有任何⼀个值符合此处的
  逻辑;
}
```

**<font style="color:rgb(38,38,38);">void </font>**<font style="color:rgb(38,38,38);">：函数不返回任何值，调⽤者也不应依赖其返回值进⾏</font><font style="color:rgb(223,42,63);">任何操作</font><font style="color:rgb(38,38,38);">！</font>

```typescript
function logMessage(msg: string): void {
  console.log(msg);
}
logMessage("你好");
```

:::info
<font style="color:rgb(38,38,38);">注意：编码者没有编写 return 指定函数返回值，所以 logMessage 函数是没有</font><font style="color:rgb(223,42,63);">显式 </font>

<font style="color:rgb(223,42,63);">返回值</font><font style="color:rgb(38,38,38);">的，但会有⼀个</font><font style="color:rgb(223,42,63);">隐式返回值 </font><font style="color:rgb(38,38,38);">，是 </font><font style="color:rgb(38,38,38);">undefined </font><font style="color:rgb(38,38,38);">，虽然函数返回类型为 </font><font style="color:rgb(38,38,38);">void </font><font style="color:rgb(38,38,38);">，但 </font>

<font style="color:rgb(38,38,38);">也是可以接受 undefined 的，简单记： </font>**<font style="color:rgb(38,38,38);">undefined </font>**<font style="color:rgb(38,38,38);">是 </font>**<font style="color:rgb(38,38,38);">void </font>**<font style="color:rgb(38,38,38);">可以接受的⼀种“空”。</font>

:::

<details class="lake-collapse"><summary id="u3118a979"><strong><span class="ne-text" style="color: rgb(38,38,38); font-size: 16px">理解 void 与 undefined </span></strong></summary><p id="u5c954ab3" class="ne-p" style="text-indent: 2em"><span class="ne-text" style="color: rgb(88,90,90); font-size: 16px">void </span><span class="ne-text" style="color: rgb(88,90,90); font-size: 16px">是⼀个⼴泛的概念，⽤来表达“空”，⽽ </span><span class="ne-text" style="color: rgb(88,90,90); font-size: 16px">undefined </span><span class="ne-text" style="color: rgb(88,90,90); font-size: 16px">则是这种“空”的具体 </span></p><p id="ucba7d1dd" class="ne-p"><span class="ne-text" style="color: rgb(88,90,90); font-size: 16px">实现。 </span></p><p id="uff48e4eb" class="ne-p" style="text-indent: 2em"><span class="ne-text" style="color: rgb(88,90,90); font-size: 16px">因此可以说 undefined 是 void 能接受的⼀种“空”的状态。也可以理解为： void 包含 undefined ，但 void 所表达的语义超越了 undefined ， void 是⼀种意图上的约定，⽽不仅仅是特定值的限制。 </span></p></details>

**<font style="color:rgb(47,142,244);">object </font>**<font style="color:rgb(38,38,38);">（⼩写) ：</font>所有⾮原始类型，可存储：对象、函数、数组等，由于限制的范围⽐较宽泛，在实际开发中使⽤的相对较少。

<font style="color:rgb(223,42,63);">Object（⼤写）: </font><font style="color:rgb(38,38,38);">所有可以调⽤ </font>**<font style="color:rgb(223,42,63);">Object </font>**<font style="color:rgb(38,38,38);">⽅法的类型。(除了 undefined 和 null 的任何值.)</font>

#### <font style="color:rgb(38,38,38);">声明对象类型</font>

```typescript
// 限制person1对象必须有name属性，age为可选属性
let person1: { name: string; age?: number };
// 含义同上，也能⽤分号做分隔
let person2: { name: string; age?: number };
// 含义同上，也能⽤换⾏做分隔
let person3: {
  name: string;
  age?: number;
};
```

**索引签名**： 允许定义对象可以具有任意数量的属性，这些属性的键和类型是可变的,常⽤于：描述类型不确定的属性，（具有动态属性的对象）。

```typescript
// 限制person对象必须有name属性，可选age属性但值必须是数字，同时可以有任意数
量、任意类型的其他属性
let person: {
 name: string
 age?: number
 [key: string]: any
}
```

#### <font style="color:rgb(38,38,38);">声明函数类型</font>

```typescript
let count: (a: number, b: number) => number;
count = function (x, y) {
  return x + y;
};
```

:::info
<font style="color:rgb(38,38,38);">备注：TypeScript 中的 => 在函数类型声明时表示函数类型，描述其参数类型和返回类 型。 </font>

<font style="color:rgb(38,38,38);">JavaScript 中的 => 是⼀种定义函数的语法，是具体的函数实现。函数类型声明还可以使⽤：接⼝、⾃定义类型等⽅式</font>

:::

:::info
tip:<font style="color:rgb(38,38,38);">在函数定义时，限制函数返回值为 void ，那么函数的返回值就必须是空。使⽤类型声明限制函数返回值为 void 时，</font>**<font style="color:rgb(223,42,63);">TypeScript </font>**<font style="color:rgb(223,42,63);">并不会严格要求函数返回空。</font>

<font style="color:rgb(38,38,38);">是为了确保如下代码成⽴，我们知道 Array.prototype.push 的返回值是⼀个数字 Array.prototype.forEach ⽅法期望其回调的返回类型是 void 。</font>

:::

```typescript
const src = [1, 2, 3];
const dst = [0];
//若是src.forEach((el) => {dst.push(el)})返回值为void;若是简写形式则返回为number
src.forEach((el) => dst.push(el));
```

#### <font style="color:rgb(38,38,38);">声明数组类型</font>

```typescript
let arr1: string[];
let arr2: Array<string>; //泛型
arr1 = ["a", "b", "c"];
arr2 = ["hello", "world"];
```

**元组(tuple):**<font style="color:rgb(38,38,38);">tuple 是⼀种特殊的数组类型，可以存储固定数量的元素，并且每个元素的类型是已 </font>

<font style="color:rgb(38,38,38);">知的且可以不同。元组⽤于精确描述⼀组值的类型，? 表示可选元素。</font>

```typescript
// 第⼀个元素必须是 string 类型，第⼆个元素必须是 number 类型。
let arr1: [string, number];
// 第⼀个元素必须是 number 类型，第⼆个元素是可选的，如果存在，必须是 boolean 类型。
let arr2: [number, boolean?];
// 第⼀个元素必须是 number 类型，后⾯的元素可以是任意数量的 string 类型
let arr3: [number, ...string[]];
```

#### 枚举(enum)

**<font style="color:rgb(38,38,38);">枚举（ enum ）</font>**<font style="color:rgb(38,38,38);">:可以定义</font><font style="color:rgb(223,42,63);">⼀组命名常量</font><font style="color:rgb(38,38,38);">，它能增强代码的可读性，也让代码更好维护</font>

**<font style="color:rgb(38,38,38);">数字枚举:</font>**<font style="color:rgb(38,38,38);">数字枚举⼀种最常⻅的枚举类型，其成员的值会</font><font style="color:rgb(223,42,63);">⾃动递增</font><font style="color:rgb(38,38,38);">，且数字枚举还具备</font><font style="color:rgb(223,42,63);">反向映射</font><font style="color:rgb(38,38,38);">的 </font>

<font style="color:rgb(38,38,38);">特点,</font><font style="color:#DF2A3F;">也可以指定枚举成员的初始值，其后的成员值会⾃动递增</font><font style="color:rgb(38,38,38);">。</font>

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right,
}
console.log(Direction); // 打印Direction会看到如下内容
/* 
 {
 0:'Up', 
 1:'Down', 
 2:'Left', 
 3:'Right', 
 Up:0, 
 Down:1, 
 Left:2,
 Right:3
 } 
*/
// 反向映射
console.log(Direction.Up);
console.log(Direction[0]);
// 此⾏代码报错，枚举中的属性是只读的
Direction.Up = "shang";
```

**字符串枚举:**<font style="color:rgb(38,38,38);">枚举成员的值是字符串</font>

```typescript
enum Direction {
  Up = "up",
  Down = "down",
  Left = "left",
  Right = "right",
}
let dir: Direction = Direction.Up;
console.log(dir); // 输出: "up"
```

**常量枚举:**<font style="color:rgb(38,38,38);">官⽅描述：常量枚举是⼀种特殊枚举类型，它使⽤ </font><font style="color:rgb(38,38,38);">const </font><font style="color:rgb(38,38,38);">关键字定义，在编译时会被 </font>

<font style="color:rgb(223,42,63);">内联</font><font style="color:rgb(38,38,38);">，</font><font style="color:rgb(223,42,63);">避免</font><font style="color:rgb(38,38,38);">⽣成⼀些</font><font style="color:rgb(223,42,63);">额外</font><font style="color:rgb(38,38,38);">的代码。</font>

:::info
<font style="color:rgb(38,38,38);">何为</font><font style="color:rgb(223,42,63);">编译时内联</font><font style="color:rgb(38,38,38);">？ </font>

<font style="color:rgb(38,38,38);">所谓“内联”其实就是 TypeScript 在编译时，会将枚举成员引⽤替换为它们的实际值,⽽不是⽣成额外的枚举对象。这可以减少⽣成的 JavaScript 代码量，并提⾼运⾏时性能</font>

:::

```typescript
const enum Directions {
  Up,
  Down,
  Left,
  Right,
}
let x = Directions.Up;
```

#### type

**<font style="color:rgb(38,38,38);">type</font>**<font style="color:rgb(38,38,38);"> :可以为任意类型创建别名，让代码更简洁、可读性更强，同时能更⽅便地进⾏类型复⽤和扩展</font>

**<font style="color:rgb(38,38,38);">基本用法:</font>**<font style="color:rgb(38,38,38);">类型别名使⽤ type 关键字定义， type 后跟类型名称</font>

**<font style="color:rgb(38,38,38);">联合类型:</font>**<font style="color:rgb(38,38,38);">联合类型是⼀种⾼级类型，它表示⼀个值可以是⼏种不同类型之⼀。</font>

```typescript
type Status = number | string;
type Gender = "男" | "⼥";
```

**交叉类型**:<font style="color:rgb(38,38,38);">交叉类型（Intersection Types）允许将多个类型合并为⼀个类型。合并后的类型将拥 </font>

<font style="color:rgb(38,38,38);">有所有被合并类型的成员。交叉类型通常⽤于对象类型。 </font>

```typescript
//⾯积
type Area = {
  height: number; //⾼
  width: number; //宽
};
//地址
type Address = {
  num: number; //楼号
  cell: number; //单元号
  room: string; //房间号
};
// 定义类型House，且House是Area和Address组成的交叉类型
type House = Area & Address;
```

:::info
tip:<font style="color:rgb(38,38,38);">在函数定义时，限制函数返回值为 void ，那么函数的返回值就必须是空。使⽤类型声明限制函数返回值为 void 时，</font>**<font style="color:rgb(223,42,63);">TypeScript </font>**<font style="color:rgb(223,42,63);">并不会严格要求函数返回空。</font>

<font style="color:rgb(38,38,38);">是为了确保如下代码成⽴，我们知道 Array.prototype.push 的返回值是⼀个数字 Array.prototype.forEach ⽅法期望其回调的返回类型是 void 。</font>

:::

```typescript
const src = [1, 2, 3];
const dst = [0];
//若是src.forEach((el) => {dst.push(el)})返回值为void;若是简写形式则返回为number
src.forEach((el) => dst.push(el));
```

####

### 类

```typescript
class Person {
  // 属性声明
  name: string;
  age: number;
  // 构造器
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  // ⽅法
  speak() {
    console.log(`我叫：${this.name}，今年${this.age}岁`);
  }
}
// Person实例
const p1 = new Person("小明", 18);
```

```typescript
class Student extends Person {
  grade: string;
  // 构造器
  constructor(name: string, age: number, grade: string) {
    super(name, age);
    this.grade = grade;
  }
  // 备注本例中若Student类不需要额外的属性，Student的构造器可以省略
  // 重写从⽗类继承的⽅法
  override speak() {
    console.log(`我是学⽣，我叫：${this.name}，今年${this.age}岁，在读${this.grade}
年级`);
  }
  // ⼦类⾃⼰的⽅法
  study() {
    console.log(`${this.name}正在努⼒学习中......`);
  }
}
```

#### 属性修饰符

| **<font style="color:#117CEE;">修饰符</font>** | **<font style="color:#117CEE;">含义</font>** | **<font style="color:#117CEE;"> 是否可以被访问</font>**            |
| ---------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------ |
| public                                         | 公开的                                       | 可以被 <font style="color:#DF2A3F;">类内部,子类,类外部</font> 访问 |
| protected                                      | 受保护的                                     | 可以被 <font style="color:#DF2A3F;">类内部,子类</font> 访问        |
| private                                        | 私有的                                       | 可以被 <font style="color:#DF2A3F;">类内部</font> 访问             |
| readonly                                       | 只读                                         | 属性无法被修改,<font style="color:#DF2A3F;">只读</font>            |

```typescript
class Person {
  // name写了public修饰符，age没写修饰符，最终都是public修饰符
  public name: string;
  age: number;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  speak() {
    // 类的【内部】可以访问public修饰的name和age
    console.log(`我叫：${this.name}，今年${this.age}岁`);
  }
}
const p1 = new Person("张三", 18);
// 类的【外部】可以访问public修饰的属性
console.log(p1.name);
//子类也可访问到
class Student extends Person {
  constructor(name: string, age: number) {
    super(name, age);
  }
  study() {
    // 【⼦类中】可以访问⽗类中public修饰的：name属性、age属性
    console.log(`${this.age}岁的${this.name}正在努⼒学习`);
  }
}
```

```typescript
//完整写法
class Person {
  public name: string;
  public age: number;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
//简写形式
class Person {
  constructor(public name: string, public age: number) {}
}
```

```typescript
class Person {
  // name和age是受保护属性，不能在类外部访问，但可以在【类】与【⼦类】中访问
  constructor(protected name: string, protected age: number) {}
  // getDetails是受保护⽅法，不能在类外部访问，但可以在【类】与【⼦类】中访问
  protected getDetails(): string {
    // 类中能访问受保护的name和age属性
    return `我叫：${this.name}，年龄是：${this.age}`;
  }
  // introduce是公开⽅法，类、⼦类、类外部都能使⽤
  introduce() {
    // 类中能访问受保护的getDetails⽅法
    console.log(this.getDetails());
  }
}
const p1 = new Person("杨超越", 18);
// 可以在类外部访问introduce
p1.introduce();
// 以下代码均报错
// p1.getDetails()
// p1.name
// p1.age
class Student extends Person {
  constructor(name: string, age: number) {
    super(name, age);
  }
  study() {
    // ⼦类中可以访问introduce
    this.introduce();
    // ⼦类中可以访问name
    console.log(`${this.name}正在努⼒学习`);
  }
}
const s1 = new Student("tom", 17);
s1.introduce();
```

```typescript
class Person {
  constructor(
    public name: string,
    public age: number,
    // IDCard属性为私有的(private)属性，只能在【类内部】使⽤
    private IDCard: string
  ) {}
  private getPrivateInfo() {
    // 类内部可以访问私有的(private)属性 —— IDCard
    return `身份证号码为：${this.IDCard}`;
  }
  getInfo() {
    // 类内部可以访问受保护的(protected)属性 —— name和age
    return `我叫: ${this.name}, 今年刚满${this.age}岁`;
  }
  getFullInfo() {
    // 类内部可以访问公开的getInfo⽅法，也可以访问私有的getPrivateInfo⽅法
    return this.getInfo() + "，" + this.getPrivateInfo();
  }
}
const p1 = new Person("张三", 18, "110114198702034432");
console.log(p1.getFullInfo());
console.log(p1.getInfo());
// 以下代码均报错
// p1.IDCard
// p1.getPrivateInfo()
```

```typescript
class Car {
  constructor(
    public readonly vin: string, //⻋辆识别码，为只读属性
    public readonly year: number, //出⼚年份，为只读属性
    public color: string,
    public sound: string
  ) {}
  // 打印⻋辆信息
  displayInfo() {
    console.log(`
 识别码：${this.vin},
 出⼚年份：${this.year},
 颜⾊：${this.color},
 ⾳响：${this.sound}
 `);
  }
}
const car = new Car("1HGCM82633A123456", 2018, "⿊⾊", "Bose⾳响");
car.displayInfo();
```

#### 抽象类

**抽象类:**<font style="color:rgb(38,38,38);">抽象类是⼀种</font><font style="color:rgb(223,42,63);">⽆法被实例化</font><font style="color:rgb(38,38,38);">的类，专⻔⽤来定义类的</font><font style="color:rgb(223,42,63);">结构和⾏为</font><font style="color:rgb(38,38,38);">，类中可以写</font><font style="color:rgb(223,42,63);">抽象⽅法</font><font style="color:rgb(38,38,38);">，也可以写</font><font style="color:rgb(223,42,63);">具体实现</font><font style="color:rgb(38,38,38);">。抽象类主要⽤来为其派⽣类提供⼀个</font><font style="color:rgb(223,42,63);">基础结构</font><font style="color:rgb(38,38,38);">，要求其派⽣类</font><font style="color:rgb(223,42,63);">必须实现</font><font style="color:rgb(38,38,38);">其中的抽象法。 简记：抽象类</font><font style="color:rgb(223,42,63);">不能实例化</font><font style="color:rgb(38,38,38);">，其意义是</font><font style="color:rgb(223,42,63);">可以被继承</font><font style="color:rgb(38,38,38);">，抽象类⾥可以有</font><font style="color:rgb(223,42,63);">普通⽅法</font><font style="color:rgb(38,38,38);">、也可以有</font><font style="color:rgb(223,42,63);">抽象⽅法</font><font style="color:rgb(38,38,38);">。</font>

```typescript
abstract class Package {
  constructor(public weight: number) {}
  // 抽象⽅法：⽤来计算运费，不同类型包裹有不同的计算⽅式
  abstract calculate(): number;
  // 通⽤⽅法：打印包裹详情
  printPackage() {
    console.log(`包裹重量为: ${this.weight}kg，运费为: ${this.calculate()}元`);
  }
}
// 标准包裹
class StandardPackage extends Package {
  constructor(
    weight: number,
    public unitPrice: number // 每公⽄的固定费率
  ) {
    super(weight);
  }
  // 实现抽象⽅法：计算运费
  calculate(): number {
    return this.weight * this.unitPrice;
  }
}
// 创建标准包裹实例
const s1 = new StandardPackage(10, 5);
s1.printPackage();
```

:::info
<font style="color:rgb(38,38,38);">总结：何时使⽤</font><font style="color:rgb(223,42,63);">抽象类</font><font style="color:rgb(38,38,38);">？ </font>

<font style="color:rgb(38,38,38);">1. 定义 通用接口：为⼀组相关的类定义通⽤的⾏为（⽅法或属性）时。 </font>

<font style="color:rgb(38,38,38);">2. 提供 基础实现：在抽象类中提供某些⽅法或为其提供基础实现，这样派⽣类就可以继承这 </font>

<font style="color:rgb(38,38,38);">些实现。 </font>

<font style="color:rgb(38,38,38);">3. 确保关键实现：强制派⽣类实现⼀些关键⾏为。 </font>

<font style="color:rgb(38,38,38);">4. 共享代码和逻辑：当多个类需要共享部分代码时，抽象类可以避免代码重复。 </font>

:::

#### 接口

**接口**:<font style="color:rgb(38,38,38);">interface 是⼀种</font><font style="color:rgb(223,42,63);">定义结构</font><font style="color:rgb(38,38,38);">的⽅式，主要作⽤是为：类、对象、函数等规定</font><font style="color:rgb(223,42,63);">⼀种契约</font><font style="color:rgb(38,38,38);">，这样可以确保代码的⼀致性和类型安全，但要注意 interface </font><font style="color:rgb(223,42,63);">只能</font><font style="color:rgb(38,38,38);">定义</font><font style="color:rgb(223,42,63);">格式</font><font style="color:rgb(38,38,38);">，</font><font style="color:rgb(223,42,63);">不能</font><font style="color:rgb(38,38,38);">包含</font><font style="color:rgb(223,42,63);">任何实现.</font>

```typescript
// PersonInterface接⼝，⽤与限制Person类的格式
interface PersonInterface {
  name: string;
  age: number;
  speak(n: number): void;
}
// 定义⼀个类 Person，实现 PersonInterface 接⼝
class Person implements PersonInterface {
  constructor(public name: string, public age: number) {}
  // 实现接⼝中的 speak ⽅法
  speak(n: number): void {
    for (let i = 0; i < n; i++) {
      // 打印出包含名字和年龄的问候语句
      console.log(`你好，我叫${this.name}，我的年龄是${this.age}`);
    }
  }
}
// 创建⼀个 Person 类的实例 p1，传⼊名字 'tom' 和年龄 18
const p1 = new Person("tom", 18);
p1.speak(3);
```

```typescript
interface UserInterface {
  name: string;
  readonly gender: string; // 只读属性
  age?: number; // 可选属性
  run: (n: number) => void;
}
const user: UserInterface = {
  name: "张三",
  gender: "男",
  age: 18,
  run(n) {
    console.log(`奔跑了${n}⽶`);
  },
};
```

```typescript
interface CountInterface {
  (a: number, b: number): number;
}
const count: CountInterface = (x, y) => {
  return x + y;
};
```

**接口的继承:**<font style="color:rgb(38,38,38);">⼀个 interface 继承另⼀个 interface ，从⽽实现代码的复⽤</font>

```typescript
interface PersonInterface {
  name: string; // 姓名
  age: number; // 年龄
}
interface StudentInterface extends PersonInterface {
  grade: string; // 年级
}
const stu: StudentInterface = {
  name: "张三",
  age: 25,
  grade: "⾼三",
};
```

tip:当接口重复定义时,会自动合并

```typescript
// PersonInterface接⼝
interface PersonInterface {
  // 属性声明
  name: string;
  age: number;
}
// 给PersonInterface接⼝添加新属性
interface PersonInterface {
  // ⽅法声明
  speak(): void;
}
// Person类实现PersonInterface
class Person implements PersonInterface {
  name: string;
  age: number;
  // 构造器
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  // ⽅法
  speak() {
    console.log("你好！我是⽼师:", this.name);
  }
}
```

:::info
总结：何时使⽤接⼝？

1. 定义对象的格式： 描述数据模型、API 响应格式、配置对象........等等，是开发中⽤的最多  
   的场景。
2. 类的契约：规定⼀个类需要实现哪些属性和⽅法。
3. 扩展已有接⼝：⼀般⽤于扩展第三⽅库的类型， 这种特性在⼤型项⽬中可能会⽤到。

:::

#### <font style="color:rgb(38,38,38);">interface 和 type</font>

:::info
<font style="color:rgb(38,38,38);">相同点： interface 和 type 都可以⽤于定义</font><font style="color:rgb(223,42,63);">对象结构</font><font style="color:rgb(38,38,38);">，在定义对象结构时两者可以互换。 </font>

<font style="color:rgb(38,38,38);">不同点： </font>

<font style="color:rgb(38,38,38);">1️⃣</font><font style="color:rgb(38,38,38);"> </font><font style="color:rgb(38,38,38);">interface </font><font style="color:rgb(38,38,38);">：更专注于定义</font><font style="color:rgb(223,42,63);">对象</font><font style="color:rgb(38,38,38);">和</font><font style="color:rgb(223,42,63);">类</font><font style="color:rgb(38,38,38);">的结构，⽀持</font><font style="color:rgb(223,42,63);">继承</font><font style="color:rgb(38,38,38);">、</font><font style="color:rgb(223,42,63);">合并</font><font style="color:rgb(38,38,38);">。 </font>

<font style="color:rgb(38,38,38);">2️⃣</font><font style="color:rgb(38,38,38);"> type ：可以定义</font><font style="color:rgb(223,42,63);">类型别名、联合类型</font><font style="color:rgb(38,38,38);">、</font><font style="color:rgb(223,42,63);">交叉类型</font><font style="color:rgb(38,38,38);">，但不⽀持继承和⾃动合并。 </font>

:::

#### <font style="color:rgb(38,38,38);">interface 和抽象类</font>

:::info
<font style="color:rgb(38,38,38);">相同点：都能定义⼀个</font><font style="color:rgb(223,42,63);">类的格式</font><font style="color:rgb(38,38,38);">（定义类应遵循的契约） </font>

<font style="color:rgb(38,38,38);">不相同： </font>

<font style="color:rgb(38,38,38);">1️⃣</font><font style="color:rgb(38,38,38);"> 接⼝：</font><font style="color:rgb(223,42,63);">只能</font><font style="color:rgb(38,38,38);">描述</font><font style="color:rgb(223,42,63);">结构</font><font style="color:rgb(38,38,38);">，</font><font style="color:rgb(223,42,63);">不能</font><font style="color:rgb(38,38,38);">有任何</font><font style="color:rgb(223,42,63);">实现代码</font><font style="color:rgb(38,38,38);">，⼀个类可以实现</font><font style="color:rgb(223,42,63);">多个</font><font style="color:rgb(38,38,38);">接⼝。 </font>

<font style="color:rgb(38,38,38);">2️⃣</font><font style="color:rgb(38,38,38);"> 抽象类：既可以包含</font><font style="color:rgb(223,42,63);">抽象⽅法</font><font style="color:rgb(38,38,38);">，也可以包含</font><font style="color:rgb(223,42,63);">具体⽅法</font><font style="color:rgb(38,38,38);">， ⼀个类只能继承</font><font style="color:rgb(223,42,63);">⼀个</font><font style="color:rgb(38,38,38);">抽象类。</font>

:::

### <font style="color:rgb(38,38,38);">泛型</font>

**泛型:**<font style="color:rgb(38,38,38);">泛型允许我们在定义函数、类或接⼝时，使⽤类型参数来表示</font><font style="color:rgb(223,42,63);">未指定的类型</font><font style="color:rgb(38,38,38);">，这些参数在具体</font><font style="color:rgb(223,42,63);">使⽤时</font><font style="color:rgb(38,38,38);">，才被指定</font><font style="color:rgb(223,42,63);">具体的类型</font><font style="color:rgb(38,38,38);">，泛型能让同⼀段代码适⽤于多种类型，同时仍然保持类型的安全性。</font>

```typescript
function logData<T>(data: T): T {
  console.log(data);
  return data;
}
logData<number>(100);
logData<string>("hello");
//也可以多个泛型
function logData<T, U>(data1: T, data2: U): T | U {
  console.log(data1, data2);
  return Date.now() % 2 ? data1 : data2;
}
```

```typescript
interface PersonInterface<T> {
  name: string;
  age: number;
  extraInfo: T;
}
let p1: PersonInterface<string>;
let p2: PersonInterface<number>;
p1 = { name: "张三", age: 18, extraInfo: "⼀个好⼈" };
p2 = { name: "李四", age: 18, extraInfo: 250 };
```

```typescript
interface LengthInterface {
  length: number;
}
// 约束规则是：传⼊的类型T必须具有 length 属性
function logPerson<T extends LengthInterface>(data: T): void {
  console.log(data.length);
}
logPerson<string>("hello");
// 报错：因为number不具备length属性
// logPerson<number>(100)
```

```typescript
class Person<T> {
 constructor(
 public name: string,
 public age: number,
 public extraInfo: T
 ) { }
 speak() {
 console.log(`我叫${this.name}今年${this.age}岁了`)
 console.log(this.extraInfo)
 }
}
// 测试代码1
const p1 = new Person<number>("tom", 30, 250);
// 测试代码2
type JobInfo = {
 title: string;
 company: string;
}
const p2 = new Person<JobInfo>("tom", 30, { title: '研发总监', company: '发发发
科技公司' });
```

### 类型声明文件

:::info
<font style="color:rgb(38,38,38);">类型声明⽂件是 TypeScript 中的⼀种特殊⽂件，通常以 .d.ts 作为扩展名。它的主要作⽤ </font>

<font style="color:rgb(38,38,38);">是为现有的 </font><font style="color:rgb(223,42,63);">JavaScript 代码</font><font style="color:rgb(38,38,38);">提供</font><font style="color:rgb(223,42,63);">类型信息</font><font style="color:rgb(38,38,38);">，使得 TypeScript 能够在使⽤这些 JavaScript 库 </font>

<font style="color:rgb(38,38,38);">或模块时进⾏</font><font style="color:rgb(223,42,63);">类型检查和提示</font><font style="color:rgb(38,38,38);">。</font>

:::

### <font style="color:rgb(38,38,38);">Ts 装饰器</font>

#### <font style="color:rgb(38,38,38);">Ts 装饰器</font>简介

1. 装饰器本质是一种特殊的**函数**，它可以对：类、属性、方法、参数进行扩展，同时能让代码更简洁。
2. 装饰器自`2015`年在`ECMAScript-6`中被提出到现在，已将近 10 年。
3. 截止目前，装饰器依然是实验性特性 ，需要开发者手动调整配置，来开启装饰器支持。
4. 装饰器有 5 种：

1⃣ 类装饰器  
2⃣ 属性装饰器  
3⃣ 方法装饰器  
4⃣ 访问器装饰器  
5⃣ 参数装饰器

#### 类装饰器

```typescript
/* 
  Demo函数会在Person类定义时执行
  参数说明：
     target参数是被装饰的类，即：Person
*/
function Demo(target: Function) {
  console.log(target);
}

// 使用装饰器
@Demo
class Person {}
```

```typescript
// 使用装饰器重写toString方法 + 封闭其原型对象
function CustomString(target: Function) {
  // 向被装饰类的原型上添加自定义的 toString 方法
  target.prototype.toString = function () {
    return JSON.stringify(this);
  };
  // 封闭其原型对象，禁止随意操作其原型对象
  Object.seal(target.prototype);
}

// 使用 CustomString 装饰器
@CustomString
class Person {
  constructor(public name: string, public age: number) {}
  speak() {
    console.log("你好呀！");
  }
}

/* 测试代码如下 */
let p1 = new Person("张三", 18);
// 输出：{"name":"张三","age":18}
console.log(p1.toString());
// 禁止随意操作其原型对象
interface Person {
  a: any;
}
// Person.prototype.a = 100 // 此行会报错：Cannot add property a, object is not extensible
// console.log(p1.a)
```

**类装饰器的返回值**

:::info
<font style="color:rgb(51, 51, 51);">类装饰器有返回值：若类装饰器返回一个新的类，那这个新类将</font>**<font style="color:rgb(51, 51, 51);">替换</font>**<font style="color:rgb(51, 51, 51);">掉被装饰的类。</font>

<font style="color:rgb(51, 51, 51);">类装饰器无返回值：若类装饰器无返回值或返回</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">undefined</font>`<font style="color:rgb(51, 51, 51);">，那被装饰的类</font>**<font style="color:rgb(51, 51, 51);">不会</font>**<font style="color:rgb(51, 51, 51);">被替换。</font>

:::

**<font style="color:rgb(51, 51, 51);">关于构造类型</font>**

<font style="color:rgb(119, 119, 119);">在 TypeScript 中，</font>`<font style="color:rgb(119, 119, 119);background-color:rgb(243, 244, 244);">Function</font>`<font style="color:rgb(119, 119, 119);"> 类型所表示的范围十分广泛，包括：普通函数、箭头函数、方法等等。但并非</font>`<font style="color:rgb(119, 119, 119);background-color:rgb(243, 244, 244);">Function</font>`<font style="color:rgb(119, 119, 119);"> 类型的函数都可以被 </font>`<font style="color:rgb(119, 119, 119);background-color:rgb(243, 244, 244);">new</font>`<font style="color:rgb(119, 119, 119);"> 关键字实例化，例如箭头函数是不能被实例化的，那么 TypeScript 中概如何声明一个构造类型呢？有以下两种方式：</font>

```typescript
/*
  ○ new     表示：该类型是可以用new操作符调用。
  ○ ...args 表示：构造器可以接受【任意数量】的参数。
  ○ any[]   表示：构造器可以接受【任意类型】的参数。
  ○ {}      表示：返回类型是对象(非null、非undefined的对象)。
*/

// 定义Constructor类型，其含义是构造类型
type Constructor = new (...args: any[]) => {};

function test(fn: Constructor) {}
class Person {}
test(Person);
```

```typescript
// 定义一个构造类型，且包含一个静态属性 wife
type Constructor = {
  new (...args: any[]): {}; // 构造签名
  wife: string; // wife属性
};

function test(fn: Constructor) {}
class Person {
  static wife = "asd";
}
test(Person);
```

```typescript
// User接口
interface User {
  getTime(): Date;
  log(): void;
}

// 自定义类型Class
type Constructor = new (...args: any[]) => {};

// 创建一个装饰器，为类添加日志功能和创建时间
function LogTime<T extends Constructor>(target: T) {
  return class extends target {
    createdTime: Date;
    constructor(...args: any[]) {
      super(...args);
      this.createdTime = new Date(); // 记录对象创建时间
    }
    getTime() {
      return `该对象创建时间为：${this.createdTime}`;
    }
  };
}

@LogTime
class User {
  constructor(public name: string, public age: number) {}
  speak() {
    console.log(`${this.name}说：你好啊！`);
  }
}

const user1 = new User("张三", 13);
user1.speak();
console.log(user1.getTime());
```

#### 装饰器工厂

**<font style="color:rgb(51, 51, 51);">装饰器工厂是一个返回装饰器函数的函数，可以为装饰器添加参数，可以更灵活地控制装饰器的行为。</font>**

**<font style="color:rgb(51, 51, 51);">需求：</font>**<font style="color:rgb(51, 51, 51);">定义一个</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">LogInfo</font>`<font style="color:rgb(51, 51, 51);">类装饰器工厂，实现</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">Person</font>`<font style="color:rgb(51, 51, 51);">实例可以调用到</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">introduce</font>`<font style="color:rgb(51, 51, 51);">方法，且</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">introduce</font>`<font style="color:rgb(51, 51, 51);">中输出内容的次数，由</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">LogInfo</font>`<font style="color:rgb(51, 51, 51);">接收的参数决定。</font>

```typescript
interface Person {
  introduce: () => void;
}

// 定义一个装饰器工厂 LogInfo，它接受一个参数 n，返回一个类装饰器
function LogInfo(n: number) {
  // 装饰器函数，target 是被装饰的类
  return function (target: Function) {
    target.prototype.introduce = function () {
      for (let i = 0; i < n; i++) {
        console.log(`我的名字：${this.name}，我的年龄：${this.age}`);
      }
    };
  };
}

@LogInfo(5)
class Person {
  constructor(public name: string, public age: number) {}
  speak() {
    console.log("你好呀！");
  }
}

let p1 = new Person("张三", 18);
// console.log(p1) // 打印的p1是：_classThis，转换的JS版本比较旧时，会出现，不必纠结
p1.speak();
p1.introduce();
```

:::info
<font style="color:rgb(51, 51, 51);">装饰器可以组合使用，执行顺序为：先【由上到下】的执行所有的装饰器工厂，依次获取到装饰器，然后再【由下到上】执行所有的装饰器。</font>

:::

```typescript
//装饰器
function test1(target: Function) {
  console.log("test1");
}
//装饰器工厂
function test2() {
  console.log("test2工厂");
  return function (target: Function) {
    console.log("test2");
  };
}
//装饰器工厂
function test3() {
  console.log("test3工厂");
  return function (target: Function) {
    console.log("test3");
  };
}
//装饰器
function test4(target: Function) {
  console.log("test4");
}

@test1
@test2()
@test3()
@test4
class Person {}

/*
  控制台打印：
    test2工厂
    test3工厂
    test4
    test3
    test2
    test1
*/
```

#### 属性装饰器

```typescript
/* 
  参数说明：
    ○ target: 对于静态属性来说值是类，对于实例属性来说值是类的原型对象。
    ○ propertyKey: 属性名。
*/
function Demo(target: object, propertyKey: string) {
  console.log(target, propertyKey);
}

class Person {
  @Demo name: string;
  @Demo age: number;
  @Demo static school: string;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

const p1 = new Person("张三", 18);
```

<font style="color:rgb(119, 119, 119);">如下代码中：当构造器中的</font>`<font style="color:rgb(119, 119, 119);background-color:rgb(243, 244, 244);">this.age = age</font>`<font style="color:rgb(119, 119, 119);">试图在实例上赋值时，实际上是调用了原型上</font>`<font style="color:rgb(119, 119, 119);background-color:rgb(243, 244, 244);">age</font>`<font style="color:rgb(119, 119, 119);">属性的</font>`<font style="color:rgb(119, 119, 119);background-color:rgb(243, 244, 244);">set</font>`<font style="color:rgb(119, 119, 119);">方法。</font>

```typescript
class Person {
  name: string;
  age: number;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

let value = 99;
// 使用defineProperty给Person原型添加age属性，并配置对应的get与set
Object.defineProperty(Person.prototype, "age", {
  get() {
    return value;
  },
  set(val) {
    value = val;
  },
});
//与js同理,实例对象上无age属性,沿原型链逐级查找,在原型对象查找到age,进行修改,则不会在实例对象上创建age属性
//若先创建示例对象,在调用Object.defineProperty方法去添加属性,则示例对象的age为给定的值,原型上的age为原拟定的value

const p1 = new Person("张三", 18);
console.log(p1.age); //18
console.log(Person.prototype.age); //18
```

<font style="color:rgb(51, 51, 51);">需求：定义一个</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">State</font>`<font style="color:rgb(51, 51, 51);">属性装饰器，来监视属性的修改。</font>

```typescript
// 声明一个装饰器函数 State，用于捕获数据的修改
function State(target: object, propertyKey: string) {
  // 存储属性的内部值
  let key = `__${propertyKey}`;

  // 使用 Object.defineProperty 替换类的原始属性
  // 重新定义属性，使其使用自定义的 getter 和 setter
  Object.defineProperty(target, propertyKey, {
    get() {
      return this[key];
    },
    set(newVal: string) {
      console.log(`${propertyKey}的最新值为：${newVal}`);
      //将变化的值存在实例本身,以免发生多个实例对象捕获无法区分的错误
      this[key] = newVal;
    },
    //可枚举性
    enumerable: true,
    //可配置性
    configurable: true,
  });
}

class Person {
  name: string;
  //使用State装饰器
  @State age: number;
  school = "atguigu";
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

const p1 = new Person("张三", 18);
const p2 = new Person("李四", 30);

p1.age = 80;
p2.age = 90;

console.log("------------------");
console.log(p1.age); //80
console.log(p2.age); //90
```

#### 方法装饰器

```typescript
/* 
  参数说明：
    ○ target: 对于静态方法来说值是类，对于实例方法来说值是原型对象。
    ○ propertyKey:方法的名称。
    ○ descriptor: 方法的描述对象，其中value属性是被装饰的方法。
*/
function Demo(
  target: object,
  propertyKey: string,
  descriptor: PropertyDescriptor
) {
  console.log(target);
  console.log(propertyKey);
  console.log(descriptor);
}

class Person {
  constructor(public name: string, public age: number) {}
  // Demo装饰实例方法
  @Demo speak() {
    console.log(`你好，我的名字：${this.name}，我的年龄：${this.age}`);
  }
  // Demo装饰静态方法
  @Demo static isAdult(age: number) {
    return age >= 18;
  }
}

const p1 = new Person("张三", 18);
p1.speak();
```

需求：

1. 定义一个`Logger`方法装饰器，用于在方法执行前和执行后，均追加一些额外逻辑。
2. 定义一个`Validate`方法装饰器，用于验证数据。

```typescript
function Logger(
  target: object,
  propertyKey: string,
  descriptor: PropertyDescriptor
) {
  // 保存原始方法
  const original = descriptor.value;
  // 替换原始方法
  descriptor.value = function (...args: any[]) {
    console.log(`${propertyKey}开始执行......`);
    //不能直接调用original,否则会丢失this,使用call函数,修改this指向
    const result = original.call(this, ...args);
    console.log(`${propertyKey}执行完毕......`);
    return result;
  };
}

function Validate(maxValue: number) {
  return function (
    target: object,
    propertyKey: string,
    descriptor: PropertyDescriptor
  ) {
    // 保存原始方法
    const original = descriptor.value;
    // 替换原始方法
    descriptor.value = function (...args: any[]) {
      // 自定义的验证逻辑
      if (args[0] > maxValue) {
        throw new Error("年龄非法！");
      }
      // 如果所有参数都符合要求，则调用原始方法
      //call和apply都能修改this,call需要一个一个传参数,apply一次性传入数组
      return original.apply(this, args);
    };
  };
}

class Person {
  constructor(public name: string, public age: number) {}
  @Logger speak() {
    console.log(`你好，我的名字：${this.name}，我的年龄：${this.age}`);
  }
  @Validate(120)
  static isAdult(age: number) {
    return age >= 18;
  }
}

const p1 = new Person("张三", 18);
p1.speak();
console.log(Person.isAdult(100));
```

#### 访问器装饰器

```typescript
/* 
  参数说明：
    ○ target: 
        1. 对于实例访问器来说值是【所属类的原型对象】。
        2. 对于静态访问器来说值是【所属类】。
    ○ propertyKey:访问器的名称。
    ○ descriptor: 描述对象。
*/
function Demo(
  target: object,
  propertyKey: string,
  descriptor: PropertyDescriptor
) {
  console.log(target);
  console.log(propertyKey);
  console.log(descriptor);
}

class Person {
  @Demo
  get address() {
    return "北京宏福科技园";
  }
  @Demo
  static get country() {
    return "中国";
  }
}
```

<font style="color:rgb(51, 51, 51);">需求：对</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">Weather</font>`<font style="color:rgb(51, 51, 51);">类的</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">temp</font>`<font style="color:rgb(51, 51, 51);">属性的</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">set</font>`<font style="color:rgb(51, 51, 51);">访问器进行限制，设置的最低温度</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">-50</font>`<font style="color:rgb(51, 51, 51);">，最高温度</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">50</font>`<font style="color:rgb(51, 51, 51);"></font>

```typescript
function RangeValidate(min: number, max: number) {
  return function (
    target: object,
    propertyKey: string,
    descriptor: PropertyDescriptor
  ) {
    // 保存原始的 setter 方法，以便在后续调用中使用
    const originalSetter = descriptor.set;

    // 重写 setter 方法，加入范围验证逻辑
    descriptor.set = function (value: number) {
      // 检查设置的值是否在指定的最小值和最大值之间
      if (value < min || value > max) {
        // 如果值不在范围内，抛出错误
        throw new Error(`${propertyKey}的值应该在 ${min} 到 ${max}之间！`);
      }

      // 如果值在范围内，且原始 setter 方法存在，则调用原始 setter 方法
      if (originalSetter) {
        originalSetter.call(this, value);
      }
    };
  };
}

class Weather {
  private _temp: number;
  constructor(_temp: number) {
    this._temp = _temp;
  }
  // 设置温度范围在 -50 到 50 之间
  @RangeValidate(-50, 50)
  set temp(value) {
    this._temp = value;
  }
  get temp() {
    return this._temp;
  }
}

const w1 = new Weather(25);
console.log(w1);
w1.temp = 67;
console.log(w1);
```

#### 参数装饰器

```typescript
/* 
  参数说明：
    ○ target:
      1.如果修饰的是【实例方法】的参数，target 是类的【原型对象】。
      2.如果修饰的是【静态方法】的参数，target 是【类】。
    ○ propertyKey：参数所在的方法的名称。
    ○ parameterIndex: 参数在函数参数列表中的索引，从 0 开始。
*/
function Demo(target: object, propertyKey: string, parameterIndex: number) {
  console.log(target);
  console.log(propertyKey);
  console.log(parameterIndex);
}

// 类定义
class Person {
  constructor(public name: string) {}
  speak(@Demo message1: any, message2: any) {
    console.log(`${this.name}想对说：${message1}，${message2}`);
  }
}
```

<font style="color:rgb(51, 51, 51);">需求：定义方法装饰器</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">Validate</font>`<font style="color:rgb(51, 51, 51);">，同时搭配参数装饰器</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">NotNumber</font>`<font style="color:rgb(51, 51, 51);">，来对</font>`<font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">speak</font>`<font style="color:rgb(51, 51, 51);">方法的参数类型进行限制。</font>

```typescript
function NotNumber(target: any, propertyKey: string, parameterIndex: number) {
  // 初始化或获取当前方法的参数索引列表
  let notNumberArr: number[] = target[`__notNumber_${propertyKey}`] || [];
  // 将当前参数索引添加到列表中
  notNumberArr.push(parameterIndex);
  // 将列表存储回目标对象
  target[`__notNumber_${propertyKey}`] = notNumberArr;
}

// 方法装饰器定义
function Validate(
  target: any,
  propertyKey: string,
  descriptor: PropertyDescriptor
) {
  const method = descriptor.value;
  descriptor.value = function (...args: any[]) {
    // 获取被标记为不能为空的参数索引列表
    const notNumberArr: number[] = target[`__notNumber_${propertyKey}`] || [];
    // 检查参数是否为 null 或 undefined
    for (const index of notNumberArr) {
      if (typeof args[index] === "number") {
        throw new Error(
          `方法 ${propertyKey} 中索引为 ${index} 的参数不能是数字！`
        );
      }
    }
    // 调用原始方法
    return method.apply(this, args);
  };

  return descriptor;
}

// 类定义
class Student {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  @Validate
  speak(@NotNumber message1: any, mesage2: any) {
    console.log(`${this.name}想对说：${message1}，${mesage2}`);
  }
}

// 使用
const s1 = new Student("张三");
s1.speak(100, 200);
```
