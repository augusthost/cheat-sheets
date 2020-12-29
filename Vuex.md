
# Vuex

1. [Vuex ကို instant လုပ်မယ်](#vuex)
2. [Store ကို App Root ထဲထည့်ရမယ်](#addstore)
3. [Component ကနေ Store ကို access လုပ်မယ်](#accessstore)
4. Component ကနေ Mutations အတွက် commit လုပ်မယ်
5. Component ကနေ Actions အတွက် dispatch လုပ်မယ်
6. Component ကနေ State data ကို Getters နဲ့လှမ်းယူမယ်

# 1 Vuex ကို instant လုပ်မယ် <a name="vuex"></a>

```javascript

const store = new Vuex.Store({
    state: {
      /* data ကြေငြာရန် */
    },
    mutations: {
      /* 
      parameter 2 ခုဖြတ်မယ် (state,payload)
      state ကအပေါ်က data ဖြစ်ပြီး
      payload က component တွေကပစ်လာတဲ့ data
 
      mutation နဲ့ပစ်ရင် synchronous ဖြစ်တယ်
      */
    },
    actions: {
     /* 
      parameter 2 ခုဖြတ်မယ် (state,payload)
      state ကအပေါ်က data ဖြစ်ပြီး
      payload က component တွေကပစ်လာတဲ့ data
      
      action နဲ့ပစ်ရင် asynchronous ဖြစ်ပြီး data တွေ sync ဖြစ်မနေဘူး ဒါပေမယ့် တချိန်တည်းမှာပဲ multiple mutation လှမ််းပစ်လို့ရတယ်
      */
    },
    getters: {
      /* 
      parameter 2 ခုဖြတ်မယ် (state,payload)
      state ကအပေါ်က data ဖြစ်ပြီး
      payload က component တွေကပစ်လာတဲ့ argument or filter
      */
    }
})

export default store;

```


# 2 Store ကို App Root ထဲထည့်ရမယ် <a name="addstore"></a>

main.js အောက်က Vue Object ထဲထည့်မယ်

```javascript

new Vue({
  store, // <=== ဒီနေရာမှာထည့်မယ်
  render: h => h(App),
}).$mount('#app')

```
    
# 3 Component ကနေ Store ကို access လုပ်မယ် <a name="accessstore"></a>
    
store ကို access လုပ်မယ်ဆို `this.$store.` နဲ့ခေါ်ရပါမယ်

ဥပမာ

```
this.$store.getters.products;
this.$store.state.products; /* state ဒီတစ်ကြောင်းလိုမျိုးတိုက်ရိုက် access မလုပ်သင့်ပါ getters,mutations,actions ကနေပဲ access လုပ်သင့်ပါတယ် */ 
```
    
    
