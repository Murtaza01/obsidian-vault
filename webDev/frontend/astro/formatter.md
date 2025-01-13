For formatting using nvim we can should install 
the following packages:

```zsh
pnpm i --save-dev prettier prettier-plugin-astro
```

Or we can install them globally and then use the prettier file
to export the fomatting:

```JavaScript
// .prettierrc.mjs
export default {
  plugins: ['prettier-plugin-astro'],
}
```

This will be make sure there is formatting in our project.
