
animate on scroll is a simple javascript library.

# using it in react

you can do that using the following code:

```js
import Aos from "aos";
import "aos/dist/aos.css";

Aos.init();

function App()...
```

you can put the init in a `useEffect` with the `Aos.refersh`

then you should wrap the element you want to have animation with `data-aos`:

```jsx
fucntion App(){
return <h1 data-aos="fade-up">Hi</h1>
}
```







