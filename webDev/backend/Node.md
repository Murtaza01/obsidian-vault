# import 

in order to use the import function, we simply add this line of code in our package.json file:

```json
{
"type": "module",
}
```

usually under the `main` , you have to put the two quotation instead of the one and the  coma at the end



a good way to use import, is to first write xxx for the name, then actually import it from the module, see the example:

```javascript
import xxx from 'sillyName'
//then when we try to change the xxx to something it will give us suggestions
```

# writing in a new line in `fs`

to write in a new line using the `fs` module, we use the writeFile with the flag of a which stands for append, look the code below:

```javascript
fs.writeFile('url.txt',`\n ${theUrl}`,{'flag':'a'},(err)=>{
  if (err){
    throw err
  }
  console.log('it works')
})
```

using the \n to move to a new line, and out text is a variable


# `__dirname` doesn't work with import

when using  import  `__dirname` won't work and you have to do some extra [steps](https://stackoverflow.com/a/62892482) to make this happen:

```javascript
import { fileURLToPath } from 'url';
import { dirname } from 'path';

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);
```

>`__dirname`

will get the exact directory you are working with, this combined with `path.join` will make your path dynamic 

```js
path.join(__dirname, "data", "results.json");
// this will look like this ./data/results.json but in different cases this './' will change
```


# getting the exact path of a file

we can't use a local path to a file using express, because when we upload it somewhere it no longer recognize that path, so we have to it dynamically, using `path` and `url` from node built-in modules, so no need for installing them.

in order to link a file to our path we need a couple of steps

```javascript
//we need to import the path module and get the dirname function, which will give us directory of the path we put
import { dirname } from "path";

// we need to import url and get the fileurltopath which will convert the url of a path
import { fileURLToPath } from "url";

// converting and getting the actuall path so we can use it when rending or sending a file
const __dirname = dirname(fileURLToPath(import.meta.url));
```


