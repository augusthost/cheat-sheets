# Content
- [Codes](#codes)
- [Console](#console)
- [Variables](#variables)
- [Types](#types)
- [Operator](#opertor)
- [querySelector](#queryselector)
- [querySelectorAll](#queryselectorall)
- [condition](#condition)
- [loop](#loop)
- [createElement](#createelement)
- [classList](#classlist)
- [attribute](#attribute)
- [addEventListener](#addeventlistener)
- [fetch](#fetch)
- [Form](#form)
- [Ajax](#ajax)
- [Anonymous Function](#anonFunction)
- [Object CRUD](#object)
- [Array CRUD](#array)
- [Play with Array data](#playwitharray)
- [Array vs Object](#arrayvsobj)

---------
# Codes <a name="codes">
javascript default function တွေ object တွေဟာ lowercase letter အသေးနဲ့ပြီး နောက်ဆက်စာလုံးတွေကို Uppercase letter နဲ့စတယ်
e.g
querySelector
setTimeout
ToLowerCase

---------

# Console <a name="console">
Console ဆိုတာ javascript ဘယ်နေရာမှာမှားနေတယ် သို့မဟုတ် data တွေကိုအစမ်းကြည့်ချင်တယ်ဆို log လုပ်ပြီးဖမ်းတဲ့သဘော

* console.log ဆိုတာ log ဖမ်းတာ
* console.table ဆိုတာ array data တွေ object data တွေ ကြည့်ရလွယ်အောင် table လိုမျိုးလုပ်ပေးတာ
* console.warn ဆိုတာ အ၀ါရောင်လေးနဲ့ warning စာလိုမျိုးပြပေးတာ
* console.error ဆိုတာ အနီရောင်လေးနဲ့ error စာလိုမျိုးပြပေးတာ

---------

# Variables <a name="variables">
var,const,let သုံးမျိုးရှိတယ်။

* var ဆိုတာ variable ပါ ES5 ထိပဲအသုံးများတယ် နောက်ပိုင်း ES6/7/8/9 တို့ဆိုရင် const နဲ့ let ပဲသုံးတော့တယ်။
* const ဆိုတာ အသေ တစ်ခေါက်ပဲ assign လုပ်လို့ရတယ်
* let ဆိုတာ ခဏ ခဏ assign လုပ်လို့ရတယ်


-------
# Types <a name="types">

(code မှန်သမျှ type ရှိတယ်)

### Types အမျိုးအစားများ <a name="types">

* String ဆိုတာ စာကြောင်း စာလုံး၊ String တွေမှာ အမြဲတမ်း မျက်တောင်အဖွင့်အပိတ်ပါတယ်။ (e.g "Mg Mg") ** မျက်တောင်အဖွင့်အပိတ်မပါရင် variable ဖြစ်သွားမယ် **
* Boolean ဆိုတာ အမှားနဲ့အမှန် ၂ ခုပဲ (e.g true and flase)
* Integer ဆိုတာ ဂဏန်း မျက်တောင်အဖွင့်အပိတ်**မပါ**ပါ (e.g 0,1,2,3,4 ) 
* Array ဆိုတာ data အစုလိုက်ထည့်သည့်နေရာ (e.g **['a','b','c']** )
* Object ဆိုတာ array လိုပဲ data အမျိုးအစားအမျိုးမျိုးထည့်လိုရတယ် ဒါပေမယ့် တွန့်ကွင်းနဲ့ရေးရတယ် (e.g **{'a':['1','2'],'b':['3'], 'c':'test'}** )
* Null ဆိုတာ ဘာမှမရှိဘူး blank ဆိုတဲ့ သဘော error မပြဘူး
* Undefined ဆိုတာ ဘာမှမကြေငြာထားဘူး error ပြမယ်

** variable တွေ code တွေရဲ့ type ကို typeof နဲ့ လှမ်းကြည့်လို့ရတယ် ဥပမာ ( e.g typeof testing ) **

-------

# opertor <a name="opertor">

#### သတိ = operator များသည် Integer တစ်မျိုးတည်းသာ အလုပ်လုပ်သည် String တို့ကို ပေါင်းနုတ်မြှောက်စား လုပ်လို့မရပါ။

* `+` အပေါင်း
* `-` အနတ်
* `*` အမြှောက်
* `/` အစား
* `%` အကြွင်းပြတ်စားတာ

`1++` ဆို 1 ကို ထပ်ထပ်ပေါင်းထည့်တာ for loop ထဲမှာအများဆုံးသုံးတယ်

```javascript
for(i=0; i<10; i++){
console.log(i);
}
```

`1--` ဆို 1 ကို ထပ်ထပ်နုတ်လိုက်တာ

------
# querySelector <a name="queryselector">

document.querySelector ဆိုတာ document ထဲမှာ ကိုယ်လိုချင်တဲ့ element ကိုလှမ်းယူတာ

element ေတွဆိုယူတာ ၃ မျိုးရှိတယ်
1. tags (div,body,span,p,table)
2. class နာမည်
3. id နာမည်

e.g
```javascript

// 1
const name = document.querySelector("div");

// 2
const name = document.querySelector(".name");

// 3
const name = document.querySelector("#name");

```

------


# querySelectorAll <a name="queryselectorall">

document.querySelectorAll ဆိုတာ document ထဲမှာ ကိုယ်လိုချင်တဲ့ element **များ** ကိုလှမ်းယူတာ

element ေတွဆိုယူတာ ၃ မျိုးရှိတယ်
1. tags (div,body,span,p,table)
2. class နာမည်
3. id နာမည်

e.g
```javascript

// 1
const nameArray = document.querySelectorAll("div");

// 2
const nameArray = document.querySelectorAll(".name");

// 3
const nameArray = document.querySelectorAll("#name");

```

ရလာတဲ့ nameArray ကို forEach လုပ်ဖို့လိုအပ် ဒါမှသာ တစ်ခုချင်းစီကို ယူလို့ရတယ်

------

# Condition <a name="condition">
 
 အကယ်၍ ဆိုတဲ့ အခြေအနေ ကိုစစ်တာ
 
 e.g
 ```javascript
  const a = 'test';
  const b = 'test';
 
  // မှန်တယ် ဆိုတဲ့ အခြေအနေ
 
  if( a == b ){
      // do something
  }
  
  // မှားတယ် ဆိုတဲ့ အခြေအနေ
 
  if( a != b ){
      // do something
  }
 
 ```
 `===` နဲ့ `!==` ဆို အရမ်းတိကျတယ် type ပါစစ်တယ် ( security ပိုအားသာတယ် )
 
 `==` နဲ့ `!=` ဆို အရမ်းတိကျတယ် type ပါစစ်တယ်
 
 ----------
# Loop <a name="loop">

Loop လုပ်တယ်ဆိုတာ array data တွေကို တစ်ခုချင်းစီလည်ပြီး တိုက်စစ်တာ/ပေါင်းထည့်တာ/ဖြုတ်တာ မျိုး

Loop လုပ်မယ်ဆိုကတည်းက လည်မည့် data သည် array ဖြစ်ရပါမယ်

ဥပမာ **arrayData** ဆိုတဲ့ variable ထဲကို array data ['1','2','3','4','5','6','7','8'] ထည့်ထားတယ်ဆိုပါစို့

နံပါတ် တစ်ခုချင်းစီ လည်ပြီးထုတ်ချင်တယ်ဆိုအောက်က loop နည်း 4 ခုနဲ့ လည်ပြီးထုတ်လို့ရပါတယ်


### forEach loop (နှေးတယ် ဒါပေမယ့်နားလည်လွယ်တယ် browser support ကောင်းတယ်)
```javascript
const arrayData = ['1','2','3','4','5','6','7','8'];
arrayData.forEach(each=>{
  console.log(each)
)
```

### for of loop (အရှင်ဆုံးနည်း modern browser တွေပဲရသေးတယ်)
```javascript
const arrayData = ['1','2','3','4','5','6','7','8'];
for( let each of arrayData){
  console.log(each)
}
```

### for loop  ( အမြန်ဆုံးနည်း ဒါပေမယ့်ရှုပ်တယ် )
```javascript
const arrayData = ['1','2','3','4','5','6','7','8'];
for(let i=0; arrayData.length < i ; i++)
{
    const each = arrayData[i]
    console.log(each)
}
```

### while loop (မြန်တယ် ဒါပေမယ့် အသုံးနည်းတယ် ရှုပ်တယ်)
```javascript
const arrayData = ['1','2','3','4','5','6','7','8'];
let i = 0;
while (i < arrayData.length) {
   console.log(arrayData[i])
  i++;
}
```

> မှတ်ချက်။ ။ နောက်ပိုင်း developer တွေ loop အစား array.map, array.reduce, array.filter, array.sort တွေကိုပဲသုံးတယ်

 ----------

# createElement <a name="createelement">
document.createElement ဆိုတာ document ထဲမှာ html ကို javascript နဲ့လှမ်းထည့်တာ လှမ်းရေးတာမျိုး

e.g
```javascript

const myBtn = document.createElement("button");

// <button></button>

myBtn.classList.add("btn");
myBtn.classList.add("btn-success");

// <button class="btn btn-success"></button>


myBtn.innerText = "my button";

// <button class="btn btn-primary">my button</button>

document.querySelector("body").innerHTML = myBtn.outerHTML;


```

# ClassList

ClassList ဆိုတာ element ထဲမှာရှိတဲ့ class အစုတွေကို
ဖြုတ်တာ ပေါင်းထည့်တာ စစ်တာတွေလုပ်လို့ရတယ် 

    1. element.classList.add('className') ဆိုတာပေါင်းထည့်တာ
    2. element.classList.remove('className') ဆိုဖြုတ်တာ
    3. element.classList.contains('className') ဆိုတာ class ပါမပါ စစ်တာ true or false စစ်တာ

```javascript
const Btn = document.querySelector(".blue");

Btn.addEventListener("click",e=>{
  
     // အကယ်၍ btn မှာ red ဆိုတဲ့ class ရှိတယ်ဆို ဖြုတ်ပစ်ပါ
     if(Btn.classList.contains("red")){
          Btn.classList.remove("red");
     }else{
       
       // အကယ်၍ btn မှာ red ဆိုတဲ့ class မရှိဘူးဆိုရင် ထည့်ပါ
          Btn.classList.add("red");
     }
})
```


# Array CRUD <a name="array">
<img style="max-width:300px" src="https://i.ibb.co/KFQymqm/Screen-Shot-2019-09-28-at-4-08-54-PM.png">

**Array.filter** // ယူမယ့် criteria နဲ့ Array ထဲကိုလှမ်းပြီး စစ်ထုတ်ယူတာ၊ Array အကုန်ပြန်မလာပါ လိုအပ်တာပဲ ပြန်လာတယ်။

**Array.map**   // Array အကုန်ပြန်လာတယ် ဒါပေမယ့် each တစ်ခုချင်းစီကို ကိုယ်ပြင်ချင်တာပြင်လို့ရတယ်။

--------

# fetch <a name="fetch">
 * GET  // လှမ်းယူ
 * PUT  // edit လုပ်ပြီး update လုပ်တာ  <== data လိုတယ်
 * POST  // လှမ်း ပေါင်းထည့်တာ          <== data လိုတယ်
 * DELETE // လှမ်း ဖြုတ်တာ delete လုပ်တာ  <== Id လိုတယ်
 
 ### GET ဥပမာ
 ```javascript
   fetch(url)
   
   // အမြဲတမ်းပါတယ်
   .then(e=>e.json())
   .then(res=>console.log(res))
 
 ```
 
 ပြန်လာတဲ့ data က json ဆို `.then(e=>e.json())`
 ပြန်လာတဲ့ data က text ဆို `.then(e=>e.text())`
 ပြောင်းပေးရမယ်

 ------
 
 ### POST ဥပမာ
 ```javascript
 
   const data = { mydata:"my testing data" }
 
   fetch(url,{
     method:"post"    // GET, POST, PUT, DELETE, etc.
     headers:{
        "Content-type":"application/json"
     },
     body: JSON.stringify(data)
   })
   
   // အမြဲတမ်းပါတယ်
   .then(e=>e.json())
   .then(res=>console.log(res))
 
 ```
 
 ----------
 
# Form <a name="form">
Javascript နဲ့ form submit လုပ်ရင် `e.preventDefault();` ထည့်ပေးရမယ်
သူက စာမျက်နှာ refresh မဖြစ်အောင်ပိတ်ပေးတဲ့သဘော

 ----------

# Ajax <a name="ajax">
<img src="https://i.ibb.co/wdC8qgZ/ajax.png">
 
 -----------
 
 # Array Vs Object <a name="arrayvsobj"></a>
 
 1 - Array ကို [] square bracket နဲ့ ရေးတယ်
 2 - Object ကို {} curly bracket နဲ့ ရေးတယ်
 
 3 - Array data ကိုခေါ်မယ်ဆို index number နဲ့ခေါ်မယ် 
 4 - Object data ကိုခေါ်မယ်ဆို key နဲ့ခေါ်မယ်
 5 - Array ဆို [] square , Object ဆို . dot 
 
 6 - Array ကို loop ပတ်တယ်ဆို for .. of 
 
 ```javascript
 
 for(let val of Array){
  console.log(val)
 }
 
 ```
 7 - Object ကို loop ပတ်မယ်ဆို for .. in 
 
  ```javascript
  
 for(let key in Array){
  console.log(`${key} : ${Array[key]}`)
 }
 
 ```
 


