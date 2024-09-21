# deploying via Vite

1. copy your github repository name and add `/` in the beginning and end and put it inside the vite.config:
![[viteConfig.png]]
2. build the app using:
`pnpm build` / `npm run build`
4. adding the dist folder into our github repository, using:
`git add dist -f`
5. we then commit our changes with the command:
`git commit -m "adding dist"`
6. we push our dist folder into our repository in a subtree called gh-pages
`git subtree push --prefix dist origin gh-pages`

this also work when we update something, we simply repeat the process

> deploying fails (!rejected)

if you can't push your build to gh-pages, you can simply delete the branch (gh-pages) and re push it, if there were some errors, with this [code](https://stackoverflow.com/a/52105454):

```Bash
git push origin --delete gh-pages
git subtree push --prefix dist origin gh-pages
```

