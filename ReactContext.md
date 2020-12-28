# Context API

1. React ကနေ createContext ယူပြီး အဲဒီနာမည်နဲ့ function ဆောက်မယ်၊ အဲဒီ function ကို variable တစ်ခုထဲထည့်ရပါမယ်။
2. နောက်ဆုံးရလာတဲ့ variable ကို <[နာမည်].provider> ဆိုပြီး wrapper component တစ်ခုဆောက်ပါ
    - a. wrapper ထဲကိုဖြတ်ဆင်းမယ့် data ရဲ့ prop name ကအမြဲ value ပဲဖြစ်ရပါမယ်။ 
3. အဲဒီ wrapper component ကို root component အနေနဲ့ထားပါ အဲဒါမှ context တွေဖြတ်ဆင်းလို့ရမှာပဲဖြစ်ပါတယ်
4. child component ကနေ data လှမ်းယူမယ် ( နည်း ၂ နည်းရှိပါတယ် ) 
    - a. React ကနေ useContext ကိုယူပါ 1 က create လုပ်ခဲ့တဲ့ variable ကို useContext ထဲ pass လုပ်ပါ variable တစ်ခုထဲထည့်ပါ အဲဒီ variable သည် 2 ရဲ့ a ကဖြတ်ဆင်းလာတဲ့ data ပဲဖြစ်ပါတယ်။
    - b. data access လုပ်မယ့် နေရာနားမှာ 2 အတိုင်း <[နာမည်].consumer> ကို wrapper အနေနဲ့ထားပါ ပြီးတော့ အဲဒီ wrapper ထဲမှာ function အနေနဲ့ ခေါ်ပါ argument သည် 2 ရဲ့ a ကဖြတ်ဆင်းလာတဲ့ data ပဲဖြစ်ပါတယ်။
