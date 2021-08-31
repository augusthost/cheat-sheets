# Netlify Serverless Functions


### Netlify serverless functions

Netlify serverless functions ဆိုတာ server deployment အပိုင်းဘာမှ စဥ်းစားစရာမလိုပဲ netlify ကလုပ်ထားပြီးသား api functions ကိုပြောတာပါ

Function တစ်ခုမှာ event နဲ့ context တွေပါပါတယ် အသေးစိတ်ကို netlify functions docs မှာဖတ်နိုင်ပါတယ်

ဥပမာ function

```javascript

exports.handler = async function(event,context){
  // do some api logic here
}

``` 

----------

### request ကနေ api parameter ဘယ်လိုဖမ်းမလဲ

event ထဲက queryStringParameters နဲ့ ဖမ်းလို့ရပါတယ် 

ဥပမာ 

```javascript

exports.handler = async function(event,context){
     const user_id = event.queryStringParameters.user_id;
}

``` 
ဒီဥပမာမှာ user_id ဆိုတဲ့ parameter ဖမ်းပြထားပါတယ်။


### response ဘယ်လိုပြန်မလဲ

e.g
```javascript
 return {
        statusCode:code,
        body:JSON.stringify(data)
    }
```


### client side က ပစ်ရမယ့် URL 

```
/.netlify/functions/my-func.js
```

----------

### function ကိုဘယ်မှာရေးရသလဲ

functions တွေကို folder တစ်ခုထဲမှာ စုရေးလို့ရပါတယ်
ဒါပေမယ့် folder ကိုတော့ `netlify.toml` ဆိုတဲ့ config ထဲမှာပြန် point လုပ်ပေးရပါမယ်

----------

### netlify.toml ဆိုတာဘာလဲ

netlify.toml ဆိုတာ netlify configuration နဲ့ဆိုင်တဲ့ file ပါ root folder ထဲမှာရေးပေးရပါတယ်

ဥပမာ netlify.toml

```
[build]
functions = 'my-func'
publish = 'src'
```
ဒီနေရာမှာ `[build]` ဆိုတာ project data တွေကို netlify ပေါ်တင်ရင် build လုပ်ပေးတဲ့အချိန်ပါ 

#### functions
build လုပ်တုန်းမှာ netlify ကို functions တွေဟာ my-func ဆိုတဲ့ folder ထဲမှာရှိတယ်လို့ညွန်းပေးတဲ့သဘောပါ

#### publish
အောက်က publish ကတော့ build လုပ်တုန်းမှာ netlify ကို publish လွင့်တင်မယ့် code တွေဟာ src ဆိုတဲ့ folder ထဲမှာရှိတယ်လို့ညွန်းပေးတဲ့သဘောပါ


