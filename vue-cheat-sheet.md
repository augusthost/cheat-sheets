# Vue CLI (Components Based)

 1. [Node.js install (npm auto ပါလာပြီးသား)](#node-install)
 2. [Vue CLI ကို install လုပ်မယ်](#cli-install)
 3. [Create new vue project](#create-vue) 
 4. [Serve/run vue project](#run-vue) 
 
 - [Vue](#vue) 
 - [Vue Router](#vue-router) 
 
 ## 1 Node.js installation <a name="node-install">

https://nodejs.org/en/ မှာ download ဆွဲပြီး install လုပ်မယ်

-----

 ## 2 Vue CLI installation <a name="cli-install">
node သွင်းပြီးရင် 

```sh
npm install vue -g
```
ဆိုတဲ့ command ကိုရိုက်မယ်

> Note 1 နဲ့ 2 ကို သွင်းပြီးလား မသွင်းရသေးဘူးလား စစ်ချင်ရင် 

```sh
node --version
```

```sh
vue --version
```

နဲ့စစ်လို့ရတယ်

------

## 3 Create new vue project <a name="create-vue">

Vue project အသစ်လုပ်မယ်ဆိုရင်

```sh
vue create (name)(ကြိုက်တာပေးလို့ရတယ်)
```

------

## 4 Serve/run vue project <a name="run-vue">

Vue app ကို စ run မယ်ဆိုရင်

```sh
npm run serve
```

> Note: သူ့ project folder ထဲရောက်နေမှရတယ်

-----

# Vue JS cheat sheet <a name="vue">

Vue ရေးမယ်ဆိုရင် new Vue() ဆိုတဲ့ class ကိုခေါ်ရမယ်

Vue Class ထဲကို Object ဖြတ်ပေးရတယ် အဲဒီ object တွေဟာ ကိုယ်ကြေငြာထားတဲ့ data တွေ

run မည့် data တွေကို {{ data }} လိုရေးပေးရတယ်

## HTML

> message ဆိုတဲ့ variable ကို html/template ထဲမှာသုံးချင်တယ်ဆို ပထမဆုံး data() function အောက်မှာကြေငြာပေးရပါမယ်

```html
<div id="app">
   {{message}} 
</div>
```

## Javascript
```javascript
const Obj = {

  // ဒါက document.querySelector လိုမျိုး
  el: '#app',
  
  // data အားလုံးထည့်တဲ့နေရာ
  data(){
     return{
         message: 'Hello Vue!'
     }
  },
  
  // page စ load တဲ့အချိန်လုပ်ချင်တာ ဒီမှာ လုပ်ရမယ်
  mounted(){
    
  },
  
  // javascript funtions အားလုံး ကို methods အောက်မှာရေးရတယ်
  methods:{
     clickme(){
       
     }
  }
  
  
};

// object ကို Vue class ထဲဖြတ်လိုက်တာ
var app = new Vue(Obj);
```

## Vue Router <a name="vue-router">
 
 ၁ − vue router သုံးမယ်ဆို အောက်က commend နဲ့ vue-router ကို install လုပ်ရမယ်

 
 ```sh
 npm i vue-router
 ```

၂ − router.js ကိုအောက်ကအတိုင်း ရေးရမယ်

```javascript

import Vue from 'vue';
import vueRouter from 'vue-router';
import Home from '@/components/home';  // component တွေကို import လုပ်
import Notfound from '@/components/notfound';  // component တွေကို import လုပ်
Vue.use(vueRouter); // vue router ကို Vue.use() နဲ့အသုံးချတယ်


const router = new vueRouter({
    routes:[
        {
            'path':'/',
            'name':'Home',
            'component':Home // component တွေကို ဒီမှာပြန်သုံး
        },
        {
            'path':'/*',
            'name':'Notfound',
            'component':Notfound
        }
    ]
})

export default router;

```

၃ − router.js  ဆိုတဲ့ router file ကို vue project နဲ့ ချိတ်ဆက်ပေးဖို့လိုတယ်

main.js ထဲမှာ ဒီလိုပုံစံလေးနဲ့ချိတ်ပေးရမယ်

```javascript

import router from './router' // router ကို import လုပ်တယ်

new Vue({
  router, // router ကို ဒီ object ထဲမှာဖြတ်ပြီးသောသုံးတယ်
  render: h => h(App),
}).$mount('#app')

```


၄ −  vue router ကို template ထဲမှာ သုံးမယ်ဆို 

`<router-view></router-view>` ဆိုတဲ့ tag နဲ့သုံးတယ်


၅ − vue route တွေကိုသွားဖို့အတွက် <a> tag အစား  
 
 `<router-link to="/about"></router-link>` ဆိုတဲ့ tag သုံးတယ်

> a tag မှာ href ကို router-link မှာ to နဲ့သုံးတယ်

----------
