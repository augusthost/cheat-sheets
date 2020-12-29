# Context API

1. [React ကနေ createContext ယူပြီး အဲဒီနာမည်နဲ့ function ဆောက်မယ်၊ အဲဒီ function ကို variable တစ်ခုထဲထည့်ရပါမယ်။](#createcontext)
2. [နောက်ဆုံးရလာတဲ့ variable ကို <[နာမည်].provider> ဆိုပြီး wrapper component တစ်ခုဆောက်ပါ](#wrapper)
3. [အဲဒီ wrapper component ကို root component အနေနဲ့ထားပါ အဲဒါမှ context တွေဖြတ်ဆင်းလို့ရမှာပဲဖြစ်ပါတယ်](#root)
4. [child component ကနေ data လှမ်းယူမယ် ( နည်း ၂ နည်းရှိပါတယ် )](#consume)


# 1 React ကနေ createContext ယူပြီး အဲဒီနာမည်နဲ့ function ဆောက်မယ်၊ အဲဒီ function ကို variable တစ်ခုထဲထည့်ရပါမယ်။ <a name="createcontext"></a>

```javascript

import React,{createContext} from 'react';
export const AppContext = createContext();

```

# 2 နောက်ဆုံးရလာတဲ့ variable ကို <[နာမည်].provider> ဆိုပြီး wrapper component တစ်ခုဆောက်ပါ <a name="wrapper"></a>
wrapper ထဲကိုဖြတ်ဆင်းမယ့် data ရဲ့ prop name ကအမြဲ value ပဲဖြစ်ရပါမယ်။ 

```javascript

export const AppProvider = (props) => {

    const [products, setProducts] = useState([]);

    useEffect(() => {
      const fetchData = async () => {
        const e = await fetch(
          "https://example.com/products"
        );
        const res = await e.json();
        setHouses(res.entries);
      };
      fetchData();
    }, []);

    return (
        <AppContext.Provider value={[products,setProducts]}>
            {props.children}
        </AppContext.Provider>
    )
}

```

# 3 အဲဒီ wrapper component ကို root component အနေနဲ့ထားပါ အဲဒါမှ context တွေဖြတ်ဆင်းလို့ရမှာပဲဖြစ်ပါတယ် <a name="root"></a>

```javascript

import {AppProvider} from './context'

export default function Main() {
  return (
    <AppProvider>
      { /* Childern Components.. */}
    </AppProvider>
    
```

# 4 child component ကနေ data လှမ်းယူမယ် ( နည်း ၂ နည်းရှိပါတယ် ) <a name="consume"></a>

    - a. React ကနေ useContext ကိုယူပါ 1 က create လုပ်ခဲ့တဲ့ variable ကို useContext ထဲ pass လုပ်ပါ variable တစ်ခုထဲထည့်ပါ အဲဒီ variable သည် 2 ကဖြတ်ဆင်းလာတဲ့ data ပဲဖြစ်ပါတယ်။
    - b. data access လုပ်မယ့် နေရာနားမှာ 2 အတိုင်း <[နာမည်].consumer> ကို wrapper အနေနဲ့ထားပါ ပြီးတော့ အဲဒီ wrapper ထဲမှာ function အနေနဲ့ ခေါ်ပါ argument သည် 2 ကဖြတ်ဆင်းလာတဲ့ data ပဲဖြစ်ပါတယ်။
    
    
```javascript

import { AppContext } from './context'

const Products = () => {
  const [products,setProducts] = useContext(AppContext);
  return (
      <div>
      {/* Access Products Data Here */}
      </div>
  )
}

export default Products

```
