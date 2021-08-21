
# AI ( Basic Neural Network )

- [What is neural network](#neuralnetwork)
- [Neurons](#neurons)
- [Layers](#layers)
- [Weights](#weights)
- [Bias](#bias)
- [Activation Function](#activation)
- [Training](#training)
- [Prediction](#prediction)
- [Sigmoid function](#sigmoid)
- [Demo](#demo)


### What is neural network? <a name="neuralnetwork"></a>
  
  Neural Network ဆိုတာ AI ဦး နှောက်အတွက်အဓိက အလုပ်လုပ်ပေးတဲ့ neurons တွေ ချိတ်ဆက်လုပ်ဆောင်တဲ့ network

--------

### Neurons <a name="neurons"></a>
Neurons တွေဆိုတာ random ကိန်းဂဏန်းတွေပဲဖြစ်ပါတယ် အထူးသဖြင့် input data ကလာတဲ့ ဂဏန်းတွေပဲဖြစ်ပါတယ်။ 
ဓါတ်ပုံကိုခွဲခြမ်းစိတ်ဖြာတဲ့ (Image classification) neural network တစ်ခုတည်ဆောက်မယ်ဆိုရင် 28x28 pexels ရှိတဲ့ဓါတ်ပုံက 784 အကွက်ရှိတယ်ဆိုပါစို့ 784 ကွက်လုံးက သူ့နံပါတ်နဲ့သူရှိတယ်။ 
အဲဒီ pixel အကွက်တွေဟာ ဓါတ်ပုံတစ်ခုက pixel တွေဖြစ်တဲ့အတွက်သူ့မှာ RGB color နဲ့ opacity နဲ့တွက်ထားတဲ့ ကိန်းဂဏန်းတစ်ခုရှိတယ် သူကို့ neuron တွေအဖြစ်မှတ်ရလွယ်အောင် sigmoid function အကူအညီနဲ့ 0 နဲ့ 1 ကြားပဲ result ရအောင် လုပ်ကြပါတယ်။

ဥပမာ 

```
[
0.0032332332,
0.8973939748,
0.8746737373,
0.0099939909
]
```

--------

### Layers <a name="layers"></a>

Neural network layers တွေ အဓိက ၃ ပိုင်းရှိတယ်
- input layer
- hidden layers 
- output layer

input layer နဲ့ hidden Layers ထဲမှာ neurons အတိအကျ size ဘယ်လောက်ပါရမယ်မျိုး မရှိပါ network ကြီးလျှင်ကြီးသလောက် neurons တွေများပါမယ် output layer ကတော့ neuron တစ်ခုတည်းပဲရှိပါတယ်

input layer ဆိုတာ ကိုယ်ကထည့်လိုက်တဲ့ data , train လိုတဲ့ data neurons အစုတွေပါတဲ့ အတန်းဖြစ်ပါတယ်

hidden layers ဆိုတာ input layer ကထည့်လိုက်တဲ့ data တွေကို weight နဲ့ တွက်ချက်ပြီး အလုပ်လုပ်စေတဲ့ layers ဖြစ်ပါတယ် [ bias နဲ့ activation function ထည့်ရန်ကျန်နေပါသေးသည်]

output layer ဆိုတာ hidden layers ကရလာတဲ့ result neuron ဖြစ်ပြီး ပုံမှန်အားဖြင့် တစ်ခုတည်း ပါပြီး တစ်ခုတည်းသို့ ဦးတည်ပြီး သွားတဲ့ပုံစံမျိုးရှိပါတယ်
result ကိုခန့်မှန်းတာ ဖြစ်တဲ့အတွက် output တစ်ခုတည်းရှိရမယ်ဆိုတဲ့သဘောမျိုးပါ 

<img src="https://www.tibco.com/sites/tibco/files/media_entity/2021-05/neutral-network-diagram.svg">

--------

### Weights <a name="weights"></a>

Weight ဆိုတာ layers တွေတစ်ခုနဲ့တစ်ခု ချိတ်ဆက်တဲ့ကြားထဲက channels တွေမှာ random generate ထုတ်ထားတဲ့ ဂဏန်းတွေပဲဖြစ်ပါတယ်။ 
random weight ကို input layer ကလာတဲ့ neuron တွေနဲ့ မြှောက်ပြီး ပေါင်းပေးရပါတယ်။ 

<img src="https://user-images.githubusercontent.com/33022876/130192354-f3d7f58a-0ef5-48ac-bb44-5318c2420e9d.jpg">

--------

### Traning <a name="training"></a>

ပထမပိုင်း layers တွေကတွက်ချက်လို့ထွက်လာတဲ့ result သည် အလွဲလိုက်ဖြစ်ပြီး အမှားနဲ့အမှန် random လျှောက်ကျနေမှာပဲဖြစ်ပါတယ်။အဲဒါကိုမှန်အောင်
တဖြည်းဖြည်းလေ့ကျင့်ပေးတဲ့ process ကို training process လို့ခေါ်ပါတယ်

ဥပမာ ကလေးတစ်ယောက် ကိုစာသင်ပေးသလိုပေါ့ စစချင်း ဘယ်ဟာက A ဘယ်ဟာက B ဆိုတာသူသိမှာမဟုတ်ဘူး ကိုယ်က ဒါက A ဒါက B ဆိုတာ train ပေးတဲ့သဘောပါ
training process က ၁ နာရီကြာကောင်းကြာမယ် တစ်ရက်ကြာကောင်းကြာမယ်

--------

### Prediction <a name="prediction"></a>
Prediction က အပေါ်က training မလုပ်ပဲ အဆင့်ကျော်လို့မရပါ ဘာမှမသင်ပဲနဲ့ မေးသလိုဖြစ်သွားမှာပဲဖြစ်ပါတယ် အဲဒီတော့ training process ပြီးပြီဆို သူ့ကို ခန့်မှန်းခိုင်းတာက prediction လုပ်တာပဲဖြစ်ပါတယ်

ဥပမာ A ကိုပြပြီး ဒါကဘာလဲဆိုတာမေးတဲ့သဘောမျိုးပါ 

---------

### Sigmoid function <a name="sigmoid"></a>

Neuron ကိန်းဂဏန်းတွေကို 0 နဲ့ 1 ကြားက value ဖြစ်အောင်ပြောင်းပေးတဲ့ function

---------

### Demo ( javascript ) <a name="demo"></a>

```javascript

const X_MAX = 400;
const Y_MAX = 400;

// Generate random numbers between min and max
const random = (high, low) => Math.random() * (high - low) + low;

// Generate numbers array
const numb   = n => [...Array(n)].map((_, index) => index + 1);

// Team to label points
const team   = (point) => point.x > point.y ? 1 : -1;


// Generate {x,y} object based on the number paramters
const generatePoints = (num) =>{
    return numb(num).map(()=>{
       return {x:random(0,X_MAX),y:random(0,Y_MAX)}
    })
}

// Random input data
const randomPoints = generatePoints(100);

// Random Weights - only single object
const randomWeights = () => {
  return {
     x: random(-1,1),
     y: random(-1,1)
  }
}

/* ------------
// Fomula 
// Guess First Step */

const guess = (weights, point) => {
  const sum = 
        point.x * weights.x + 
        point.y * weights.y
  const team = sum >= 0 ? 1 : -1
  return team
}


// Training function 
// Correct result based on error
const train = (weights, point, team) => {
   const guessResult = guess(weights, point) // 1
   const error = team - guessResult 
   const learningRate = 0.3
   return {
     x: weights.x + point.x * error * learningRate,
     y: weights.y + point.y * error * learningRate,
   }
}


const trainWeights = () =>{
   
    const examples = generatePoints(10000).map(point => ({
    point,
    team: team(point)
  }))

  let currentWeights = randomWeights();
  for (const example of examples) {
    currentWeights = train(currentWeights, example.point, example.team)
    //await sleep(25)
    //yield currentWeights
  }
  return currentWeights
}

// svg circles
let html = `<svg width="${X_MAX}" height="${Y_MAX}">
    ${randomPoints.map(point => 
      `<circle 
         cx="${point.x}"
         cy="${point.y}"
         r="3"
         fill="${guess(trainWeights(),point) === -1 ? 'green': 'blue'}" />`
    ).join(""}
    <line x1="0" x2="${X_MAX}" y1="0" y2="${Y_MAX}" stroke="purple" />
  </svg>`;

// Append svg points
let points = document.querySelector("#points");
if(!points){

   let new_points = document.createElement('div');
   new_points.id = 'points';
   new_points.innerHTML = html;
   document.body.append(new_points);

}else{
  points.innerHTML = html;
}

```
