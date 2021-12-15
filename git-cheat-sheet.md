# Git Cheat Seet ( Only for master branch )

# Creat new repository
github Repository တစ်ခုလုပ်မယ်ဆို github menu ရဲ့ညာဘက်ကအပေါင်းမှာနှိပ်ပြီးလုပ်လို့ရတယ်

----------

# clone repo
ကိုယ့်စက်မှာ repo ကိုဆွဲချမယ်ဆို 

```
git clone https://github.com/account/repo.git
```

https://github.com/account/repo.git ဆိုတဲ့နေရာက ကိုယ့်ရဲ့ repo link ဖြစ်ရပါမယ်

----------


# pull from master

လိုင်းပေါ်က data တွေကို ကိုယ့်ရဲ့ local ဆီဆွဲချမယ်ဆို pull နဲ့ဆွဲပါတယ်

```
git pull origin master
```

----------


# push to master

ကိုယ့်ရဲ့ local က data တွေကိုလိုင်းပေါ်ပြန်တင်ချင်တယ်ဆို push နဲ့တင်ပါတယ်။

```
git push origin master
```

> တံခါးကို push တွန်းတယ် pull ဆွဲတယ်ဆိုတာနဲ့အလွယ်မှတ်ထားလို့ရပါတယ်။ push ဆို လိုင်းပေါ်တွန်းတင်တယ် pull ဆိုလိုင်းပေါ်ကဆွဲချတယ်။ 


----------

# push မတင်ခင် လုပ်ရမယ့် ၃ ချက်

1. ကိုယ့်ရဲ့ changes တွေကို add နဲ့ထည့်ပါ
2. ကိုယ်ဘာ change လိုက်လဲဆိုတာကို commit အနေနဲ့ message တစ်ခုရေးပေးပါ
3. နောက်ဆုံး commit လုပ်ပြီးရင် git status နဲ့စစ်ပါ

## 1. ကိုယ့်ရဲ့ changes တွေကို add နဲ့ထည့်ပါ

```
 git add .
```

ဆိုတဲ့ command နဲ့ ကိုယ် change ထားတာတွေအကုန်လုံးကိုထည့်လို့ရပါတယ်။

```
 git add index.html
```

ဆိုတဲ့ command ဆိုရင်တော့ `index.html` တစ်ဖိုင်တည်းထည့်တာဖြစ်ပါတယ်။

## 2. ကိုယ်ဘာ change လိုက်လဲဆိုတာကို commit အနေနဲ့ message တစ်ခုရေးပေးပါ

```
git commit -m "My Message"
```

"My message" ဆိုတဲ့နေရာမှာ ကိုယ် change လိုက်တဲ့အဓိကအကြောင်းအရင်းကိုရေးရပါမယ်။ 

ဥပမာ `git commit -m "added git cheat sheet"`

## 3. နောက်ဆုံး commit လုပ်ပြီးရင် git status နဲ့စစ်ပါ

လိုင်းပေါ်မတင်ခင်မှာ git status တစ်ချက်ပြန်စစ်ပေးပါ။

> working tree clean ဆိုတဲ့စာသားပေါ်နေမှတင်လို့ရပါတယ်။ 

အဲဒီလို git status နဲ့မစစ်ပဲတင်တယ်ဆို error တွေရှိတတ်ပါတယ်

working tree clean ဆိုတဲ့စာသားမျိုးပေါ်နေပြီဆို git push origin master လုပ်လို့ရပါပြီ။ 

------------------

## Ubuntu server ပေါ်တွင် Git credential သိမ်းနည်း

root မှာ ~/.netrc file တစ်ခု လုပ်ပါ

အထဲမှာအောက်ကအတိုင်းထည့်ပါ

```
machine github.com
login YOUR_GITHUB_USERNAME
password YOUR_GITHUB_PASSWORD
```

သတိ - file permission အသေအချာပေးပါ
chmod 600 ~/.netrc
