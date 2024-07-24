is a way to translate your website, it has many feature and is very convenient way of translation.

we start by downloading the three packages

~ i18next  
~ react-i18next
~ i18next-browser-languagedetector

the first two packages will work with our react app, the third is a way to detect and add our language to the localStorage.

we start by making a file and importing our packages:

```js
import i18n from "i18next";
import { initReactI18next } from "react-i18next";
import LangDetector from "i18next-browser-languagedetector";
```

then we use them in the `i18n` function with the method `use`:

```js
export default i18n
  .use(LanguageDetector)
  .use(initReactI18next).init({})
```

# init()

this  method is a function that takes an object that will have our options for our translation:

```js
export default i18n
  .use(LanguageDetector)
  .use(initReactI18next).init({
  debug: true,
  fallbackLang: "en",
  resources: {
      en: {
        translation: {
        'greeting':'hello'
        },
      },
      ar: {
        translation: {
        'greeting':'مرحبا'
        },
      },
    },
  })
```

the debug will show error messages, the `fallbackLang` will default if there were no key, and the resources will be our translation, we need to add a translation object and the `ar/en`, each object inside the translation object will be accessed via the key in this case its a string because usually we deal with `json` files

# useTranslation

we use this hook to access our translation, it returns two objects, we destruct the `t` function that will get our translation from the `transltion` object above:

```jsx
import { useTranslation } from "react-i18next";

function App(){
const {t} = useTranslation()
t('greeting') // hello
}
```

# changing the language

we can easily do that via the `i18n` fucntion that we destruct from the `useTranslation` hook:

```jsx
import { useTranslation } from "react-i18next";

function App(){
const {i18n} = useTranslation()

i18n.changeLanguage('ar') // we pass the lang name
}
```

this should be inside a function that will trigger whenever we click a button for example.