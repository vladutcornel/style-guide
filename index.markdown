---
layout: home
---

After 15 years working with different coding and programming languages, and following different coding style guidelines,
I have developed my own style, that may contradict or complement other guidelines you may have read. 
[More about me here](/about) 

General rules
=============

Use these regardless of the language or framework.

1\. Don't always follow this guide
----------------------------------
If you are joining an existing project and team, chances are there are already style guides that your team follows.
Ask your Team Leader about them. Only if there aren't any, or you feel comfortable in suggesting changes, 
ask them if they are willing to follow this guide.

Even with new projects, there may be official guidelines for the language or frameworks you will be using. Try to follow those as much as it makes sense.


2\. Code for fellow developers
------------------------------
The code you write will **always** be read by someone else. People change over time, so that someone else may be you from the future.

Give that someone else as few reasons to cuss you as possible. 

The fact you are reading a style guide is a step in the right direction.


3\. General programming
-----------------------
Try to avoid constructs that are specific to other languages, unless there is a very good reason to do it.

4\. Code Comments
-----------------
I still think comments are important in code. 

I heard the argument that code should speak for itself, thus comments aren't needed. The reasoning is fair, in my opinion, but I disagree with the conclusion. There needs to be a middle ground between providing too much information and none at all. 

Here are my suggestions:

1. **Comment at the beginning of the file**  
If the file represents a single class, function, module, or component, provide some usage examples.  
If not, give some details on what the file does.
2. **Doc-Comment before each class or function**  
Doc-Comments are a special kind of comment, first introduced for Java ([Javadoc](https://en.wikipedia.org/wiki/Javadoc)) for generating API documentation. They were adopted by other languages.  
Even if you don't have an API Generator running, some IDEs use it to provide nice auto-complete.
3. **Describe the algorithm inside a longer block of code**  
Instead of writing a comment before each line (which qualifies as too much information), describe the algorithm before you implement it. Remember to change the description when you update the algorithm.


5\. Use Git
-----------
There is no competition anymore. Git is now the industry standard for code versioning. 

Look at [Cornel's Git Style Guide](/guides/git).

6\. Common debates
------------------

Here are some common codding debates, and how I settle them:

### Tabs vs. Spaces
**Answer**: Spaces inserted with the TAB key.

Most serious code editors do this already: You just press the TAB key, and they insert 4 spaces (or how many you define, but it should be 4)

### Indentation
**Answer**: 4 spaces.

Having only 2 spaces is too flat for me. More than 4 is too much.
The only case where I would use 2 spaces is in an YAML file, when defining arrays.

```yaml
parent:
  - line1: "Note only 2 spaces before -"
    line2: "BTW, This is an object in the array"
    line3: "Now we have 4 spaces because we are in the same object"
  - This is a string
```

### First brace
Should the first brace be on the same line, or the next line?

Chances are the community for the programming language already decided this, so you should follow it.
  
Generally, I prefer to have it on the same line because when I have the text cursor on the last brace , my IDEs show a dotted line straight into the statement it belongs to. Having the first brace on a separate line just means I would have to look one line up, which is not a huge inconvenience.  
I allow my IDE to refactor the code based on the defaults for the language, and I don't give much thought to it.

### Best IDE
The best IDE/Editor is the one you know how to use. You should learn the ins and outs of your editor. 

If you are just starting out, and don't know which one to chose, play with all of them, and see which one feels best.  
**Do not use an IDE just because it's hip.**.

Also, the language, sometimes even the framework you use may limit your options. While many editors can provide nice syntax highlighting, you may need a proper IDE (Integrated Development Environment) to write code faster, cleaner, and with fewer problems.

Personally, I like the IDEs provided by [JetBrains](https://www.jetbrains.com/), but if I were on a tighter budget, I would probably go for [NetBeans](https://netbeans.org/) or [VSCode](https://code.visualstudio.com/) (VSCode is closer to an editor than an IDE, but with 3rd party extensions, it can act almost like an IDE.