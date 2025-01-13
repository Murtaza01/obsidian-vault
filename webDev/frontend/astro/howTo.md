## add js to your components

```astro
<Heading clinet:load />
```

## get current route

using the components scripts:

```astro
---
const currentPath = new URL(Astro.request.url).pathname
---
```

using js:

```javascript
const currentPath = window.location.pathname
```

