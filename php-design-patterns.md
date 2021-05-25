# PHP Design Pattern

#### ဒီ Note တွေကတော့ Laravel Founder - Jeffery Way ရဲ့ PHP Design Patterns series ကိုကြည့်ပြီး ကောက်နုတ်ထားတဲ့ Cheat Sheet Note ပါ။

## Interface 

Interface ဆိုတာ term လိုမျိုးပဲ class တစ်ခုမှာ ဒီ methods တွေအဓိကပါဝင်မယ်လို့ကြေငြာထားတဲ့သဘော အကယ်၍ instantiate လုပ်တဲ့ class မှာ method တစ်ခုပါမလာရင် error ပြမယ်။

**ဘယ်လိုနေရာတွေမှာ သုံးသလဲ?**

Interface ကို တူညီတဲ့ methods တွေပါတဲ့ class တွေကိုဘုံထုတ်တဲ့ အခါသုံးပါတယ် method နာမည်တွေ ကိုပဲ ကြေငြာပေးရပါတယ် method codes တွေမလိုပါ။ 

မှတ်ချက်။  ။ Interface က implements သို့မဟုတ် Dependency Inject လုပ်လို့ရပါတယ်။

```php
interface CarServiceInterface{
  
  public method drive()
  
  public method stop()
 
}

// call 1
class BMW implements CarServiceInterface{
    
}

// call 2
class Lamboginny{

  protected $carService; 
  public function __construct(CarServiceInterface $carService){
    $this->carService = $carService;
  }

}
```

## Adapter Class

Adapter Class ဆိုတာ methods တွေမတူတဲ့ Class ၂ ခုကိုကြားခံပေါင်းစပ်ပေးတဲ့ class တစ်ခု Adapter class ရဲ့ construct method မှာ class ကို inject လုပ်ပေးရပါတယ်။ 
( Adapter Class က interface တွေကို implement လုပ်တာဖြစ်ပါတယ်။ ) 

## The template method pattern 

#### Abstract Class
Interface လိုမျိုးပဲ methods တွေကိုဘုံထုတ်တဲ့အခါသုံးပါတယ် ဒါပေမယ့် inherit class ပုံစံဖြစ်တဲ့အတွက် implements လုပ်တာမျိုးမဟုတ်ပဲ extends လုပ်ရတာဖြစ်ပါတယ်။ ပြီးတော့ interface လိုမျိုး method နာမည်ချည်းမဟုတ်ပဲ codes တွေပါထည့်ရေးရပါတယ်။

```php

abstract class Common{

  public function upload(){
     // upload codes
  }

  public function download(){
      // download codes
  } 

}

class Audio extends Common{
   public function listen(){
      // listen 
   } 
}

class Movie extends Common{
   public function watch(){
      // watch 
   } 
}


```

#### Abstract Method


