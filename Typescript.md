# Typescript

Typescript ဆိုတာ javascript ကို error တွေနည်းစေဖို့ရေးထားတဲ့ language တစ်မျိုးဖြစ်ပါတယ် သူ့ရေးပုံရေးနည်းက javascript အတိုင်းပါပဲ
ဒါပေမယ့် statically-typed language တွေဖြစ်တဲ့ Java, C++ တို့ရဲ့ type သဘောကို javascript မှာထည့်သုံးတဲ့သဘောပါ 
.ts extension နဲ့ရေးရပါတယ် 


### Installation

```
npm install -g typescript
``` 

**Init config file ပြုလုပ်မယ်ဆို**

```
tsc --init
```

## Type အမျိုးအစားများ

- boolean
- string
- number
- any
- array
- object
- interface
- type [custom name]


## Type declare ပုံများ  

```javascript

let a: string                       = 'Hello';
let b: boolean                      = true;
let c: number                       = 1234;
let d: any                          = 'world';
let e: object                       = {hello:'world'};
let f: {var1?:string, var2:number}  = {var1:'optional', var2:123};
let g: (string)[]                   = ['test'];
let h: (any)[]                      = [hello,123456];
let i: (number)[]                   = [123456];

```
