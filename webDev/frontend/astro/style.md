# adding varaible from components scripts

```astro
---
const skillColor = 'blue';
---

<style define:vars={{skillColor}}>
h1{
    color:var(--skillColor);
}
</style>
```


