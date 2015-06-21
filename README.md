
#The difference between let and var in JavaScript

As you may be aware, let is a new keyword in ECMAScript 6. While let works very much like var, there is one major difference. This article (a quick one) explains the difference between these two keywords in JavaScript.

## Scope
The difference lies in scope. The variables declared with var are scoped to the function block while those declared with let are scoped to the enclosing block (which may be smaller than the function block). Let's analyse this through an example.

```javascript
function simpleLoop(){
	/* i is visible here due to variable hoisting */
   for(var i=0;i<10;i++){
	  console.log(i);
	  /* of course i is available here */
   }
   /* i is available as well */
}
```

The above snippet shows a simple loop. The variable i, declared with var keyword, is hoisted and is available to the whole function. Now, let's change the snippet to use let instead of var.

```javascript
function simpleLoop(){
	/* i is not visible here. */
   for(let i=0;i<10;i++){
	  console.log(i);
	  /* i is scoped to this block */
   }
   /* i is not available here */
}
```

In the above example, the variable i is scoped to the for loop. It's visible inside the parentheses and the curly braces of the loop. If you try to access it before or after the loop, you will get ReferenceError.

The variables declared with var are scoped to the function block while those declared with let are scoped to the nearest enclosing block.

## The Let Block and Expression
The let keyword also allows you assign values to variables within a particular block scope without affecting other variables with the same name outside the block.

This is done as following :
```javascript
let (name = 'Sandeep', message = 'Good Morning!') {
  console.log(message+' '+name);
}
```
Here, the variables name and message are scoped to the particular block.

With let keyword you can also declare variables that are scoped to a single expression. The following snippet demonstrates this.

```javascript
let (x=5) console.log(x+5);
```

Do note that by declaring let blocks and expressions you aren't interfering with variables outside the blocks. Take a look at the following snippet:
```javascript
var x=12; //12
let(x=2) console.log(x); //2
console.log(x+2); //14
```
So, this was all about the difference between var and let. However, you should remember that these features are still experimental and the browser support is limited. To know exactly which browsers support let keyword see this [chart](http://kangax.github.io/compat-table/es6/).
