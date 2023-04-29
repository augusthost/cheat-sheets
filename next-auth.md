# Next JS Auth

Next auth ဆိုတာ OAuth providers ပေါင်းမြောက်များစွာကို ထည့်ရေးထားတဲ့ library တစ်ခုပါ
Google Facebook Apple Github တွေနဲ့ လွယ်လွယ်ကူကူဝင်လို့ရပါတယ်။ 

အခုအောက်က cheat sheet ကတော့ next auth သုံးပြီး သာမန် credential login နဲ့ဆိုဘယ်လိုသွားမလဲဆိုတာပါပဲ 


<img width="584" alt="Screen Shot 2023-04-28 at 11 08 27 PM" src="https://user-images.githubusercontent.com/33022876/235281395-1b8ccc6e-174c-4696-93c1-43392cb01425.png">


> မှတ်ချက် ။ ။ javascript အတွက်သာဖြစ်ပါတယ် typescript မပါပါ။

1. Installation
2. Create `[...nextauth].js` file
3. Add nextauth options
4. Add custom credential login form
5. Handle login form data
6. Wrap next app with SessionProvider
7. Redirect after login
8. Protect pages

-------

## 1. Installation
next auth ကို သုံးမယ်ဆို `npm i next-auth` နဲ့သွင်းလိုက်ပါ 

-------

## 2. Create `[...nextauth].js` file
pages/api/auth ဆိုတဲ့အောက်မှာ `[...nextauth].js` file လုပ်လိုက်ပါ

-------

## 3. Add nextauth options
`[...nextauth].js` file ထဲမှာ next auth options တွေကိုအောက်က code အတိုင်းထည့်ပါ 

```javascript
import CredentialsProvider from "next-auth/providers/credentials";
import NextAuth from 'next-auth';

export const authOptions = {
  session: {
      strategy: "jwt"
  },
  providers: [
      CredentialsProvider({
          name: "Email and Password",
          credentials: {
             username: { label: "Username", type: "text", placeholder: "jsmith" },
      		 password: { label: "Password", type: "password" }
          },
          async authorize(credentials, req) {
              // fetch API or query DB here
              // const res = await fetchAPI(credentials);
              if(res.status !== 200){
                throw new Error('Wrong credential')
              }
              return res;
          }
      })
  ]
}

export default NextAuth(authOptions)
```
ဒီနည်းကတော့ default ပါလာပြီးသား credential login form လေးနဲ့လုပ်တာပါ

-------

## 4. Add custom credential login form

အပေါ် step 3 ကအတိုင်းမဟုတ်ပဲ မိမိကိုယ်တိုင်ဆွဲထားတဲ့ login form သုံးချင်တယ်ဆို အောက်ကအတိုင်း pages ဆိုတဲ့ object ကိုဖြည့်ရပါမယ်

> မှတ်ချက် ။ ။ credentials ဆိုတဲ့ object ထဲကဟာတွေ ကိုကျတော့ဖျက်ပစ်ရမှာပဲဖြစ်ပါတယ်

```
  name: "Email and Password",
  credentials: {}
  ...
  pages: {
      signIn: "/auth/login"
  }
```

-------

## 5. Handle login form data
login form input data တွေကို အဆင်ပြေသလိုဖမ်းလို့ရပါတယ် ရလာတဲ့ credential data တွေကို ဒီအောက်ကအတိုင်း auth ကိုပစ်ရမှာပဲဖြစ်ပါတယ်။

```javascript

  const res = await signIn("credentials", {
    email: emailValue,
    password: passValue,
    redirect: false,
  });  
  
``` 
-------

Login Form တစ်ခုလုံးအပြည့် code 

```javascript
import { signIn } from "next-auth/react";
import Router from "next/router";
import { useRef, useState } from "react";


const LoginForm = () => {

  const email = useRef(null)
  const password = useRef(null)
  const [error,setError] = useState('')

  const handleClick = async () =>{
    const emailValue = email.current.value;
    const passValue = password.current.value;
    if(!emailValue || !passValue){
      return;
    }
  
  const res = await signIn("credentials", {
    email: emailValue,
    password: passValue,
    redirect: false,
  });  
  
  
  if(res.status === 200){
    Router.replace("/dashboard")
  }

  setError(res.error)
  setTimeout(()=>{
    setError('')
  },2000)
}

    return (
        
        <div id="loginForm" className="p-8">
            <form>
            {error ? <div className="my-3 p-2 bg-red-50 text-red-500 rounded">{error}</div> : ''}
            <div className="mb-6">
              <label htmlFor="email" className="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Your email</label>
              <input ref={email} type="email" id="email" className="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="name@flowbite.com" required />
            </div>
            <div className="mb-6">
              <label htmlFor="password" className="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Your password</label>
              <input ref={password} type="password" id="password" className="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" required />
            </div>
            <div className="flex items-start mb-6">
              <div className="flex items-center h-5">
                <input id="remember" type="checkbox" value="" className="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-blue-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-600 dark:ring-offset-gray-800 dark:focus:ring-offset-gray-800" required />
              </div>
              <label htmlFor="remember" className="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300">Remember me</label>
            </div>
            <button onClick={handleClick} type="button" className="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Submit</button>
          </form>
        </div>

    )
}

export default LoginForm;
```

-------

## 6. Wrap next app with SessionProvider

တခြား react library တွေလိုမျိုးပဲ Next _app.js ထဲမှာ SessionProvider နဲ့ wrap လုပ်မှသာ ကျန်တာအလုပ်လုပ်မှာပဲဖြစ်ပါတယ်

> ဒီ step ကိုမမေ့ပါနှင့် 

```javascript

import '@/styles/globals.css'
import { SessionProvider } from "next-auth/react";


export default function App({ Component, pageProps }) {
  return (
    <SessionProvider session={pageProps.session}>
      <Component {...pageProps} />
    </SessionProvider>
  );
}

```

-------

### 7. Redirect after login
Login လုပ်ပီးရင် redirect လုပ်ချင်ရင်တော့ `Router.replace()` ကိုသုံးပြီး redirect လုပ်လို့ရပါတယ် 

```javascript

const res = await signIn("credentials", {
    email: emailValue,
    password: passValue,
    redirect: false,
  });  
  
  
  if(res.status === 200){
    Router.replace("/dashboard")
  }

```

-------

## 8. Protect pages
မိမိပိတ်ချင်တဲ့ Page ကို useSession method နဲ့ protect လုပ်လို့ရပါတယ်

```javascript

import { signOut, useSession } from "next-auth/react";
import Router from "next/router";
import { useEffect } from "react";

const Dashboard = () =>{
    const {status,data} = useSession()

    useEffect(() => {
        if (status === "unauthenticated"){
            Router.replace("/auth/login")
        }
    }, [status]);

    if(status === 'authenticated'){
        return (
            <div className="container max-w-[600px] w-full p-4 shadow-lg rounded-md bg-white my-20 mx-auto">
                <button onClick={()=>signOut()}>Logout</button>
                <p>This is my protected page</p>
            </div>
        )
    }

    return (
        <>
        Loading...
        </>
    )
}

export default Dashboard;

```
