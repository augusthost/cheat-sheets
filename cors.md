# Cors Error

Cors ပြသနာမှာ request domain နဲ့ response domain ၂ ခုရှိတယ်

1. domain ၂ ခု က တူရမယ်
2. domain ၂ ခုစလုံး SSL https ဖြစ်ရမယ်
3. အကယ်လို့ SSL မရှိဘူးဆိုရင် ၂ ခုစလုံး SSL ဖြုတ်ရမယ်

4. အကယ်လို့ domain ၂ ခုမတူဘူးဆိုရင် server domain ကို cors ဖွင့်ပေးရမယ်


## 4 a. PHP နဲ့ cors ဖွင့်နည်း

```php

    header('Access-Control-Allow-Origin: *'); 
    header("Access-Control-Allow-Credentials: true");
    header('Access-Control-Allow-Methods: GET, PUT, POST, DELETE, OPTIONS');
    header('Access-Control-Allow-Headers: Origin, Content-Type, X-Auth-Token , Authorization');
    
```

## 4 b. .htaccess နဲ့ဖွင့်နည်း

domain အားလုံးအတွက်
```

<IfModule mod_headers.c>
    Header set Access-Control-Allow-Origin "*"
</IfModule>

```

ပစ်မယ့် domain တစ်ခု နှစ်ခုအတွက်ပဲ
```

<IfModule mod_headers.c>
    SetEnvIf Origin "http(s)?://(domainone.com|domaintwo.com$" AccessControlAllowOrigin=$0
    Header add Access-Control-Allow-Origin %{AccessControlAllowOrigin}e env=AccessControlAllowOrigin
    Header always set Access-Control-Allow-Methods: "GET,POST,OPTIONS,DELETE,PUT"
</IfModule>

```

## 4 c. nodejs ဖွင့်နည်း

cors library ကိုသွင်းရပါမယ်
```
npm i cors
```

ပြီးတော့ 

```javascript

const express = require('express');
const app = express();

const cors = require('cors');
app.use(cors())

```
