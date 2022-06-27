# Typescript

Typescript ဆိုတာ javascript ကို error တွေနည်းစေဖို့ရေးထားတဲ့ language တစ်မျိုးဖြစ်ပါတယ် သူ့ရေးပုံရေးနည်းက javascript အတိုင်းပါပဲ
ဒါပေမယ့် statically-typed language တွေဖြစ်တဲ့ Java, C++ တို့ရဲ့ type သဘောကို javascript မှာထည့်သုံးတဲ့သဘောပါ 
.ts extension နဲ့ရေးရပါတယ် 

သာမာန်အားဖြင့် .ts သည် javascript မဟုတ်တဲ့အတွက် browser .ts ကိုမသိနိုင်ပါ 
browser ကိုသိစေချင်ရင်တော့ vite လိုမျိုး tool သုံးပြီးတော့ browser ထဲမှာထည့် run လို့ရပါတယ် ဒါပေမယ့်လည်း browser တကယ်သိတာမဟုတ်ပဲ vite က hotreload လုပ်တဲ့အချိန်မှာ .js အဖြစ် transpile လုပ်ပေးတဲ့သဘောပဲဖြစ်ပါတယ်။ )


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

## Generic Types

Generic Types ဆိုတာလက်ရှိ type တွေကို parameterized လုပ်တာပဲဖြစ်ပါတယ် 
String or Object တစ်ခုမှာ Type တွေများရင် any လိုပေးပြီး ကျနော်တို့ကြိုက်တဲ့ type ကို assign ပေးလို့ရပါတယ် 
ဒါပေမယ့် ဒါက .js သုံးတာနဲ့ဘာမှမထူးတော့ပါဘူး ပြီးတော့ type information တွေကျနော်တို့ကြည့်လို့မရတော့ပါဘူး၊
အဲဒါကို Generic Types နဲ့ parameterized လုပ်လို့ရပါတယ် 

ဥပမာ

```javascript

const getUser = (name: string, age: any) => {
  return {name,age};
}
// ဒီလို generic type ပြောင်းလို့ရပါတယ် ဒါဆို type information လည်းမဆုံးရှုံးတော့ပါဘူး 
const getFullName = <T>(name:string, age:T) => {
  return {name,age};
}

```


