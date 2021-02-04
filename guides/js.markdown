---
layout: page
title: JavaScript guidelines
---

Do not follow this guide
------------------------
If you are joining an existing project and team, chances are there are already style guides that your team follows.
Ask your Team Leader about them. Only if there aren't any, or you feel comfortable in suggesting changes,
ask them if they are willing to follow this guide.

Do not write JavaScript
-----------------------

The JavaScript that is safe to run in browsers is fairly limited. Even if you plan to only support modern browsers, 
they don't always support all the features.

Fortunately, there are tools like [Babel](https://babeljs.io/) that transform bleeding edge code to code that most 
browsers should be able to handle.  
If babel is not already in your project, you should take the time to set it up, 
maybe using [Webpack](https://webpack.js.org/). 

Beyond browsers, JavaScript may be used in other environments (e.g. [Node.js](https://nodejs.org/)) 
which may have fewer restrictions. In this case, it's up to you and your team to decide if Babel is needed.

Use "double quotes"
-------------------

As a general programmer, with C and Java background, the fact that 
JavaScript allows treats 'single quotes' and "double quotes" exactly the same is mind-boggling.

Some style guides suggest using single quotes. If you see one, check how old it is. 
In ancient times, some JavaScript was written directly in HTML attributes, like so:

```html
<!-- BAD CODE -->
<a onclick="open('sesamy')">Click me like one of your French girls</a>
```

Back then, it made sense to keep consistency: HTML attributes would use "double quotes", and JS strings 'single quotes'.

In modern times, that's not important, and in fact it's bad practice having JS inside HTML attributes. 
I find it more important to keep consistency with other mature programming languages. 
That's why I prefer "double quotes".

`const` vs `let` when constants are not constant
------------------------------------------------

Modern JS replaces the ancient `var` for declaring variables with `let` and `const`. 
I will assume anyone reading this knows the basics: With `let`, you can change the value, with `const`, you can't.

What is less obvious is that properties of objects that are declared with `const`

```javascript
const OBJ = {
    A: 'a'
};

// This is completely allowed
OBJ.A = 'b';

const ARR = [1, 2];

// No problem as far as JS designers are concerned
ARR.push('potatoes');
```

I think **this is a bad design decision, and I refuse to willingly take advantage of it**.

**Rule**: If absolutely nothing changes in the object or array, use `const`.  
**Rule**: If anything changes in the object or array over the course of the current block, use `let`.

Of course, you may find yourself working with people who think Ecma International (the organization that is in charge of JS standards) is made of untouchable gods that can never do anything wrong, just nod and pretend you don't think they're religious fanatics.
