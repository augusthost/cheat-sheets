# PHP Design Patterns

#### ဒီ Note တွေကတော့ Laravel Founder - Jeffrey Way ရဲ့ PHP Design Patterns series ကိုကြည့်ပြီး ကောက်နုတ်ထားတဲ့ Cheat Sheet Note ပါ။

## Interface 

Interface ဆိုတာ term လိုမျိုးပဲ class တစ်ခုမှာ ဒီ methods တွေအဓိကပါဝင်မယ်လို့ကြေငြာထားတဲ့သဘော အကယ်၍ instantiate လုပ်တဲ့ class မှာ method တစ်ခုပါမလာရင် error ပြမယ်။

**ဘယ်လိုနေရာတွေမှာ သုံးသလဲ?**

Interface ကို တူညီတဲ့ methods တွေပါတဲ့ class တွေကိုဘုံထုတ်တဲ့ အခါသုံးပါတယ် method နာမည်တွေ ကိုပဲ ကြေငြာပေးရပါတယ် method codes တွေမလိုပါ။ 

မှတ်ချက်။  ။ Interface က implements သို့မဟုတ် Dependency Inject လုပ်လို့ရပါတယ်။


## Adapter Class

Adapter Class ဆိုတာ methods တွေမတူတဲ့ Class ၂ ခုကိုကြားခံပေါင်းစပ်ပေးတဲ့ class တစ်ခု Adapter class ရဲ့ construct method မှာ class ကို inject လုပ်ပေးရပါတယ်။ 
( Adapter Class က interface တွေကို implement လုပ်တာဖြစ်ပါတယ်။ ) 

```php
interface CarServiceInterface{

    public function drive();

    public function stop();

  }

  // call 1
  class BMW implements CarServiceInterface{
     public function drive(){
       echo 'Driving BMW';
     }
     public function stop(){
      echo 'Stop BMW';
    }
  }

  // call 2
  class CarAdapter implements CarServiceInterface{
    protected $carService;
    public function __construct(CarServiceInterface $carService){
      $this->carService = $carService;
    }
    public function drive(){
      echo $this->carService->drive();
    }
   public function stop(){
     echo $this->carService->stop();
   }
  }

  class Lamboginny implements CarServiceInterface{
    public function drive(){
      echo 'Driving Lamboginny';
    }
    public function stop(){
     echo 'Stop Lamboginny';
   }
  }

  (new CarAdapter(new Lamboginny))->drive();
```

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

လက်ရှိ Abstract class ထဲမှာခေါ်သုံးထားတဲ့ ဘုံ methods တွေထဲက တစ်ခုကို dynamic ဖြစ်ချင်တယ်ဆိုရင် Abstract method ကိုသုံးလို့ရပါတယ်။ ဒီအောက်က ဥပမာ
မှာ play ဆိုတဲ့ method ကို abstract method အနေနဲ့ ခေါ်သုံးထားပါတယ်။ 

```php

abstract class Common{

  public function run(){
     $this->download();
     $this->play();
  }

  public function upload(){
     // upload codes
  }

  public function download(){
      // download codes
  } 

  protected abstract function play();

}

class Audio extends Common{
   public function listen(){
      // listen 
   } 
   public function play(){
      echo 'playing audio';
   } 
}

class Movie extends Common{
   public function watch(){
      // watch 
   } 
   public function play(){
      echo 'playing video';
   } 
}

(new Movie)->run(); 

// Should echo playing video

```

-----------------

Repository

Repository ဆိုတာ Database wrapper API လို့ပြောလို့ရတယ်
ဥပမာ database ကို mysql db ကနေ mongodb ပြောင်းချင်တာမျိုးဆို
mongodb repository ကို ကောက်စွပ်လိုက်ရုံနဲ့ mongodb အတွက် ready ဖြစ်ပြီးသား ပြီးတော့ 
API တွေခေါ်သုံးလို့ရမယ် (ဥပမာ Mongodb::class->connect())
Laravel မှာ eloquent နဲ့ collections API တွေရှိပြီးသားမို့ repository ကိုသိပ်အသုံးမပြုစေချင်။

------------------

Services

Controller က business logics တွေက
အကြောင်းရေများလာရင် ရှုပ်ထွေးကုန်တယ် အဲဒီတော့ service class တွေခွဲပြီး
အကြောင်းရေနည်းအောင်လုပ်တဲ့အချိန်မှာ Services ကိုသုံးတယ် 

------------------

Trait

Trait က inherit လုပ်တာနဲ့ ဆင်တယ်
ဒါပေမယ့် inherit မှာ single class ကိုပဲချိတ်ဆက်လို့ရတယ်
Trait မှာကျတော့ Class အကုန်လုံးနဲ့ share လို့ရတယ်။ 

-------------------


