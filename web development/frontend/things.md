# top level await
you can add await at the top level of your javascript file, instead of 
using a function

# import a directory

if we have a folder which contains all the header components

header
	header.js
	headerItems.js
	headerLogo.js

we will have to import things like this:

```js
import header from "../header/header.js"
```

that would be redundant, a better way is to have an index which will redirect all our imports

```js
export * from './header'
export {default} from './header'

```

in the first line we are exporting everyhing that inside the folder to be avaible in the index file, which would be the name of the folder, so our imports would look something like this

import {headerItems} from "./header"

# curl to request

we can use curl to do request to the server from the bash command:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-d '{"query": "{ hello }"}' \
http://localhost:4000/graphql
```

