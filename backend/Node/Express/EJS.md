in order to use `ejs` in our express app, we first need to install it, import it, and use it with our express engine, here is an example

```javascript
import ejs from 'ejs'
app.set('view engine','ejs')
```

# if statement 

for if statement we need  the following syntax in order to not get any error:


```javascript
<% if(true){ %>
   <h1>foo</h1>
 <% } else{ %>  
   <h1>bar</h1>
<% } %>
```

the end of the if needs to be paired with the else statement

# ejs tags

there is multiple ejs tags, showing below:

![[ejs tags.png]]

# locals

there is some cases when we want to display a variable that we want to be after a submit or a post request, because ejs works by first trying the code, and it won't check for our variable, see the example below:

![[locals.png]]

this won't work, because numberOfLetters is not yet defined since its waiting the post request *(the form)*, so to solve this we need to give the variable locals:

```javascript
if (locals.numberOfLetters){..}
```

# partials

when you render partials in your `ejs` page, by default it would look in the **views** folder,  for your partials, so it would look like this:

```javascript
<%- include('partials/header.ejs') %>
```