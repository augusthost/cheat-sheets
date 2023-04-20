# React Redux Toolkit

[demo](https://codesandbox.io/s/react-redux-toolkit-8hkes8?file=/src/App.tsx:0-910)

## Understanding Store, Reducer, Selector, Action and Dispatch

**store** - store ဆိုတာ global state တစ်ခုပါ အဲဒီထဲကို data တွေပစ်ထည့်ရမယ့် object ကြီးတစ်ခုလို့ပြောရပါမယ်

**action** - action ကတော့ ဘာလုပ်မယ်ဆိုတာကို command ပေးတဲ့အနေနဲ့ပို့တဲ့ စာတစ်စောင်ပဲ

**dispatch** - အပေါ်က action command ကိုအဓိကပို့ပေးမယ့် function တစ်မျိုး  

**reducer** - dispatch လုပ်ပြီးရောက်တာတဲ့ action command ကို reducer က data တစ်ခုချင်းစီ ထည့်တာ ဖြုတ်တာ ဖျက်တာတွေကို စီမံခန့်ခွဲပေးပါတယ် သူလည်း function ပဲ 

**selector** - selector ကတော့ data တွေကိုဆွဲထုတ်ဖို့အတွက်အဓိကသုံးပါတယ် dispatch နဲ့ဆန့်ကျင်ဘက်လို့ပြောလိုရပါတယ် 


> ဥပမာ post တစ်ခုဖျက်မယ်ဆို action ကနေလှမ်းပြောတယ် deletePost(index) , အဲဒါကို redux ရဲ့ dispatch က dispatch(deletePost(index)) ဆိုပြီးသယ်သွားပေးတယ် အဲဒါကိုတစ်ဘက်က reducer ကလက်ခံပြီး `addPerson: (state, action) => state.persons.splice(0,action)` အဲဒီလိုမျိုူး state ထဲက data ကိုလှမ်းဖျက်လိုက်တယ်။ နောက်ဆုံး modify လုပ်လိုက်တဲ့ state data ကိုပြန်ဆွဲပြီးပြမယ်ဆို selector နဲ့ဆွဲပါတယ်။ 

----


# Redux Toolkit

## 1. Folder Structure

- store
  - store.ts
  - features
    - personSlice.ts

## 2. Wrap with provider
အရင်ဆုံး react-redux က Provider ကိုယူပြီး <App /> ကို wrap လိုက်ပါ

```javascript
import { Provider } from "react-redux";
import { store } from "./store/store";

import App from "./App";

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById("root")
);

```

> ဒီနေရာမှာ error တက်ပါလိမ့်မယ် ဘာလို့လဲဆိုတော့ Provider မှာ store ဆိုတဲ့ props data ကဘာမှမရှိသေးလို့ 

## 3. Add Store

step 2 က store data မရှိတဲ့ error ကိုပြင်ဖို့

store ဆိုတဲ့ object ကို store/store.ts file ထဲမှာ configureStore ဆိုတဲ့ method နဲ့ create လုပ်လိုက်မယ်

> မှတ်ချက် ဒီမှာ personReducer တွေကိုပါတစ်ခါတည်းထည့်ထားလိုက်တယ် ဖြုတ်လိုက်ပေါင်းလိုက်ဆို ရှုပ်နေမှာစိုးလို့ အောက်မှာ personReducer ကိုသပ်သပ်ရှင်းထားပါတယ်

> ဒီမှာလဲ error တက်ပါလိမ့်မယ် ဘာလို့လဲဆိုတော့ features/personSlice ကို create မလုပ်ထားလို့ပါ 


```javascript
import { configureStore } from "@reduxjs/toolkit";
import personReducer from "./../store/features/personSlice";

export const store = configureStore({
  reducer: {
    person: personReducer
  }
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

## 4. Create personSlice 

step 3 မှာတက်ခဲ့တဲ့ error ကိုဖြေရှင်းဖို့ features/personSlice.ts ဆိုတဲ့ file တစ် file create လုပ်ရပါမယ် ပြီးတော့ အောက်က content ကိုထည့်ပါမယ် 

```javascript

import { createSlice, PayloadAction } from "@reduxjs/toolkit";

interface Person {
  persons: string[];
}

export const initialState: Person = {
  persons: []
};

const personSlice = createSlice({
  name: "person",
  initialState,
  reducers: {
    addPerson: (state, action: PayloadAction<string>) => {
      state.persons.push(action.payload);
    }
  }
});

export const { addPerson } = personSlice.actions;

export default personSlice.reducer;


```

ဒါက person တစ်ခုတည်းနဲ့ဆိုင်တဲ့ reducer လေးတစ်ခုလို့ပြောလို့ရပါတယ်။ 

ဒီ file တစ်ခုလုံးရဲ့ အဓိကသော့ချက်က `personSlice.actions` နဲ့ `personSlice.reducer` ဆိုတဲ့ ၂ ခုပါ

တစ်ဘက်ကို ကို actions နဲ့ reducer ပို့ပေးတာပဲဖြစ်ပါတယ် 
ဒီနေရာမှာ actions ကို destructure လုပ်ထားတော့ addPerson ဆိုတဲ့ method ပဲ ပို့ပေးတာဖြစ်ပါတယ် 

## 5. Use addPerson action

Reducer ကတော့ store နဲ့တွဲချိတ်တာဆိုတော့ step 3 (Add store) မှာကတည်းက ချိတ်ထားပြီးသား

ဒါပေမယ့် Action ကျတော့ကိုယ်တစ်ခုခု action လုပ်မှာဖြစ်တဲ့အတွက် form element တွေ button တွေမှာချိတ်ပြီး သုံးရမှာပဲဖြစ်ပါတယ်

အောက်က code ကိုကြည့်မယ်ဆို addPerson ဆိုတဲ့ action ကို step 4 က personSlice ကနေဆွဲထုတ်လာတယ် ဘယ်မှာပြန်သုံးတာလဲဆိုတော့ button ရဲ့ onClick မှာခေါ်သုံးထားတယ်


> မှတ်ချက် addPerson action ကိုဒီအတိုင်းခေါ်သုံးလို့မရဘူး dispatch() ဆိုတဲ့ function နဲ့ အုပ်လိုက်မှသာ အလုပ်လုပ်ပါတယ်။


```javascript

import "./styles.css";

import { RootState } from "./store/store";
import { useSelector, useDispatch } from "react-redux";
import { addPerson } from "./store/features/personSlice";
import { useState } from "react";
export default function App() {
  const persons = useSelector((state: RootState) => state.person.persons);
  const dispatch = useDispatch();

  const [personName, setPersonName] = useState("");

  const handleAddPerson = () => {
    dispatch(addPerson(personName));
  };

  return (
    <div className="App">
      <form className="testForm">
        <input type="text" onChange={(e) => setPersonName(e.target.value)} />
        <button type="button" onClick={handleAddPerson}>
          Add
        </button>
      </form>
      <div className="result">
        {persons &&
          persons.map((p, i) => {
            return <li key={i}>{p}</li>;
          })}
      </div>
    </div>
  );
}

```

## 6. Selector
selector က dispatch နဲ့ဆန့်ကျင်ဘက်လို့ပြောရမယ် အသွားလမ်းကိုပို့ပေးပြီး data တွေကို ပြန်ဆွဲထုတ်တဲ့ လမ်းမှာကျတော့ useSelector နဲ့ state data တွေကိုပြန်ဆွဲထုတ်လာတာပဲဖြစ်ပါတယ် step 5 က code ကိုပဲပြန်ကြည့်လို့ရပါတယ်။ 


---

[demo](https://codesandbox.io/s/react-redux-toolkit-8hkes8?file=/src/App.tsx:0-910)
