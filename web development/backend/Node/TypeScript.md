node uses an engine called `V8` that is used in the browser to turn javascript code into machine code.

`V8` is written by C++ 

![[node and  v8.png]]

# Typescript

in order to use typescript with node you simply need to `init` a typescript config file using:

```bash
~ ts --init
```

then you could normally `npm init` to add a json config file, then to use typescript with node you need the following `types`:

```bash
~ npm i --D @types/node
~ npm i --D @types/express
```

then in order to use the `import` es6 feature we go into the typescript config file and add:

![[ts.config for node.png]]

because node can not execute ts files, we need to compile our ts files into js files using the `tsc` in our terminal, however that will create our js files next to our  so we need to manage the output and input of our files to a better folder structure, in the ts.config file:

![[ts output.png]]

# Configuration 

while using node with typescript you would want to use the module `nodenext` or `node16` because they transform both from old javascript code and new one, it is generally advised by the typescript [documentation](https://www.typescriptlang.org/docs/handbook/modules/reference.html#commonjs) to use these options instead of `commonjs`

 
# ts-node

you can omit the compiling step by installing a  package called `ts-node` which will do that for you, and it will have a command that transform typescript code into javascript code 

if you install it locally in your project you need to use the script option and pass in the command and the file name ex: `ts-node app.ts`

# deployment

when deploying the app its better to not use `ts-node` and use the regular build using :

```json
"build": "tsc && node build/server.js"
```

this will compile the code then run it

**note** that you need to have complied it at least once so that the command on the right doesn't raise error that the folder doesn't exist

# watching your app

you could either use `nodemon with ts-node` or use [`tsx`](https://stackoverflow.com/a/70933036) and giving it the proper configuration:

```json
"dev": "tsx watch src/index.ts"
```

to prevent the terminal from clearing you can add option like:

```json
"dev": "tsx watch --clear-scren=false src/index.ts"
```

alternatively you can use the node version 18 `--watch` method:

```json
"dev": "tsx --watch src/index.ts"
```