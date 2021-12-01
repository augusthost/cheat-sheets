# Tailwind Nextjs

1. [Install tailwind via npm](#installtailwind)
2. [root folder မှာပဲ tailwind config file တစ်ခုလုပ်မယ်](#rootfolder)
3. [အဲဒီ config ထဲကိုအောက်က code တွေထည့်မယ်](#tailwindconfig)
4. [tailwind ချိတ်သုံးနည်း](#connecttailwind)


## 1 install tailwind via npm <a name="installtailwind"></a>

```sh
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
```

## 2 root folder မှာပဲ tailwind config file တစ်ခုလုပ်မယ် <a name="rootfolder"></a>

tailwind.config.js ဆိုတဲ့နာမည်နဲ့ file တစ်ခုလုပ်မယ် 

## 3  အဲဒီ config ထဲကိုအောက်က code တွေထည့်မယ် <a name="tailwindconfig"></a>

```javascript
 module.exports = {
   purge: [],
   purge: ['./pages/**/*.{js,ts,jsx,tsx}', './components/**/*.{js,ts,jsx,tsx}'],
    darkMode: false, // or 'media' or 'class'
    theme: {
      extend: {},
    },
    variants: {
      extend: {},
    },
    plugins: [],
  }
```

## 4 tailwind ချိတ်သုံးနည်း <a name="connecttailwind"></a>

styles/globals.css file ကိုဖွင့်ပြီး အောက်က tailwind css ကိုပေါင်းထည့်ပါ

```css
/* ./styles/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

tailwind စသုံးလို့ရပါပြီ
