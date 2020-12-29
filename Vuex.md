
# Vuex

1. [Vuex ကို instant လုပ်မယ်](#vuex)
2. [Store ကို App Root ထဲထည့်ရမယ်](#addstore)
3. [Component ကနေ Store ကို access လုပ်မယ်](#accessstore)
4. [Component ကနေ Mutations အတွက် commit လုပ်မယ်](#mutations)
5. [Component ကနေ Actions အတွက် dispatch လုပ်မယ်](#actions)
6. [Component ကနေ State data ကို Getters နဲ့လှမ်းယူမယ်](#getters)
7. [အရမ်းကြီးလာတဲ့ Store ကို Module ခွဲမယ်](#modules)

### Best Practices

 - Fetch Data အကုန် actions ထဲကနေခေါ်ပါ async ရတာရယ် multiple mutations ပစ်လို့ရတာရယ် ကြောင့်ပါ။ 
 - အစဥ်လိုက် Store ကိုသုံးနည်းကတော့ Actions -> Mutations -> State ဖြစ်ပါတယ်။ Getters ကတော့ data ယူတာတစ်ခုတည်းပါ။ 
 - `this.$store.state.products` ဆိုပြီး state data တွေကိုတိုက်ရိုက် access မလုပ်သင့်ပါ getters,mutations,actions ကနေပဲ access လုပ်သင့်ပါတယ် */ 

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
      payload က component တွေကပစ်လာတဲ့ argument သို့ data ဖြစ်ပါတယ်။
 
      mutation နဲ့ပစ်ရင် synchronous ဖြစ်တယ်
      */
    },
    actions: {
     /* 
      parameter 2 ခုဖြတ်မယ် (ctx,payload)
      ctx ကတော့ context data ဖြစ်ပါတယ်
      payload က component တွေကပစ်လာတဲ့ argument သို့ data ဖြစ်ပါတယ်။
      
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

```javascript
this.$store.getters.products;
```

# 4 Component ကနေ Mutations အတွက် commit လုပ်မယ် <a name="mutation"></a>
    
