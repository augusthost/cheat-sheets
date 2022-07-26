# React Router Dom v6


1. Router installation
2. Router configuration
3. Link inside components
4. Exact prop

## Router Installation
`npm install react-router-dom@latest` လို့ terminal မှာ run ပြီးသွင်းနိုင်ပါတယ်

## Router configuration

ပုံမှန်အားဖြင့် အောက်ကအတိုင်း App.js ထဲမှာ router ကိုထည့်ကြပါတယ် 

```jsx

// React Router Dom က import လုပ်တာ 
import { BrowserRouter, Route, Routes } from 'react-router-dom'


return (
    <>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Home />}></Route>;
          <Route path="/about" element={<About />}></Route>
        </Routes>
      </BrowserRouter>
	</>
)

```

အပေါ်ကနည်းအတိုင်းကို v6 react-router-dom ကတော့ ဒါကိုဒီလိုပြဿနာရှာတာမျိုးရှိတတ်ပါတယ် 

```
Error: useHref() may be used only in the context of a <Router> component
```

ဒါကိုဖြေရှင်းနည်းကတော့ `<BrowserRouter>` ကို App.js ကနေထုတ်ပြီး ‌app level အထက်ကိုပို့ရပါမယ် 
အပြင်ဆုံး `main.js` ဆီကိုအောက်ပါအတိုင်းထည့်ထားရမှာပဲဖြစ်ပါတယ် 

```jsx
// React Router Dom က import လုပ်တာ 
import { BrowserRouter } from 'react-router-dom'

ReactDOM.render(
  <React.StrictMode>
    <AppProvider>
      <BrowserRouter> <!-- ဒီကိုပြန်ရွှေ့ရပါတယ် -->
        <App />
      </BrowserRouter>
    </AppProvider>
  </React.StrictMode>,
  document.getElementById('root')
)
```


## Link inside components

Link နှိပ်ပြီး route တစ်ခုပြီးတစ်ခုသွားအောင်လုပ်မယ်ဆို ခါတိုင်း html ရဲ့ a tag နဲ့မဟုတ်တော့ပါဘူး Link ကိုသုံးရပါတယ် 

ဥပမာ

```
import { Link } from 'react-router-dom'

return (
  
   <Link to="/about">
       About
   </Link>

)

```
