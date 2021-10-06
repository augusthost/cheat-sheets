# NLP ဆိုတာ

မိခင်ဘာသာစကားသုံး ကွန်ပျူတာစနစ်ဆိုသည်မှာ ကွန်ပျူတာနှင့် လူသားတို့ဆက်သွယ်နိုင်ရန် မိခင်ဘာသာစကားအား ကွန်ပျူတာ၌ အသုံးပြုခြင်း ဖြစ်သည်။ မိခင်ဘာသာစကားသုံး ကွန်ပျူတာစနစ်သည် တီထွင်ဖန်တီးထားသော အသိဉာဏ်ဆိုင်ရာ ပညာရပ် ၏ အစိတ်အပိုင်းတစ်ခုလည်း ဖြစ်သည်။ ( wiki မှ ကူးထား :D )

NLP ရဲ့အဓိက ၆ ပိုင်း
1. segmentation
2. tokenizing
3. stemming
4. lemmatization
5. speech tagging
6. name entities tagging

## Segmentation

စာတစ်ကြောင်းစီ ဖြတ်ပေးတာ English မှာဆို full stop နဲ့ဖြတ်တာ မြန်မာမှာဆို ပုဒ်ကလေး ပုဒ်မ နဲ့ဖြတ်တာမျိုး

## tokenizing

သူက စာလုံးတစ်လုံးစီ ဖြတ်တောက်တာ ဥပမာ `this` `is` `an` `example` `of` `tokenizing` ဖြတ်တာမျိုးပါ 

## stemming

အရှေ့က စာလုံးတူတာတွေ အနောက်ကစာလုံးတူတာတွေရဲ့ အဓိကဘုံတူတဲ့စာလုံးမျိုးကိုယူတာ 

ဥပမာ trouble, troubling, troubles ရှိတယ်ဆိုပါစို့ အဓိကဘုံတူတာကိုဖြတ်ယူရမယ်ဆို troubl ဖြစ်ပါတယ်

ဥပမာ miss, missing, misses ရှိတယ်ဆိုပါစို့ အဓိကဘုံတူတာကိုဖြတ်ယူရမယ်ဆို miss ဖြစ်ပါတယ်

## lemmatization

သူကတော့ stemming နဲ့ဆင်သလိုလိုနဲ့ကွဲပါတယ် သူကတော့ stemming ကလို troubl ဆိုတဲ့အဓိပါယ်မရှိတဲ့စာလုံးမျိုးထုတ်ပေးမှာမဟုတ်ဘူး
သူအဓိကယူတာက base form ပါ word ကလည်းအဓိပါယ်လည်းရှိရပါမယ် 

ဥပမာ am, is, are ရှိတယ်ဆိုပါစို့ သူ့ base form က be ဖြစ်ပါတယ်

ဥပမာ go, went, gone ရှိတယ်ဆိုပါစို့ သူ့ base form က go ဖြစ်ပါတယ်

## speech tagging
သူကတော့ tokenized လုပ်ထားတဲ့စာလုံးတွေကို verb လား verb to be လား preposition လား စသဖြင့် အမျိုးအစားတွဲပေးတာဖြစ်ပါတယ်။
ဥပမာ I go to school ဆို I/PRP go/VBP to/PRT school/NN တို့ဖြစ်သွားမှာပါ 

ဒီနေရာမှာ

PRP - pronoun

VBP - verb

PRT - preposition

NN  - noun

တို့ပဲဖြစ်ပါတယ်

https://parts-of-speech.info/ မှာ စမ်းကြည့်လို့ရပါတယ် 

## name entities tagging

သူကတော့ နာမည် တွေလိပ်စာနာမည်တွေ ကိုရွေးထုတ်တဲ့အပိုင်းဖြစ်ပါတယ်

ဥပမာ U Thant , who served as Secretary-General of the United Nations from 1961 to 1971 ဆိုရင် 

U Thant, United Nations စတာ တွေကိုရွေးထုတ်သွားမှာပဲဖြစ်ပါတယ်။ 

