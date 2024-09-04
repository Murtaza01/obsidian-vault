swiper is the best library for sliders in javascript, it support react and is easily configurable

# using it with react

you need to import two components from the `swiper/react` which comes built in the `swiper` library when you download it, and also import the css :

```js
import { Swiper, SwiperSlide } from "swiper/react";
import "swiper/css";
```

then simply use the components

```jsx
 <Swiper>
      <SwiperSlide>Slide 1</SwiperSlide>
      <SwiperSlide>Slide 2</SwiperSlide>
      <SwiperSlide>Slide 3</SwiperSlide>
      <SwiperSlide>Slide 4</SwiperSlide>
</Swiper>
```

the `Swiper` component take all the configuration so you should put all of the animation there, you should see the documentation for the full list:

```jsx
<Swiper spaceBetween={50} slidesPerView={3} loop={true}... >
...
</Swiper>
```

if you would like to use an effect you should import the css and its module, and add the needed properties to the `Swiper` component :

```jsx
import { EffectFade } from "swiper/modules";
import "swiper/css/effect-fade";

<Swiper effect={"fade"} fadeEffect={{crossFade: true,}} modules={[EffectFade]}>
...
</Swiper>
```