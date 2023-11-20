# From the beginnin


Define variables with
`var [DATA TYPE] = '[EXPRESSION]'`;
**but** use 
`let` to let future values to constantly update value
# Data Types
**Number** - number, including decimals. 
**String** - any grouping of characters on your keyboard, wrapped in single ' ' or double " "
**Boolean** - true or false
**Null** - intentional absence of a value
**Undefined** - absence of a value
# Math
`Math.random()` returns a value between `0` (inclusive) and `1` (exclusive).
`Math.floor` ensures only whole numbers (rounds down)
# Conditional Statements
## Comparison Operators
- Less than: `<`
- Greater than: `>`
- Less than or equal to: `<=`
- Greater than or equal to: `>=`
- Is equal to: `===`
- Is not equal to: `!==`
## Logical Operators
<mark class="hltr-yellow">_and_ operator (`&&`)</mark>
	both conditions must evaluate to true
	if one is `false`, the else will execute
<mark class="hltr-yellow">_or_ operator (`||`)</mark>
	only one condition must evaluate to true --> overall statement will evaluate to true
<mark class="hltr-yellow">_not_ operator, otherwise known as the _bang_ operator (`!`)</mark>
	negates the value, `true`to `false`

Something can evaluate to a truthy value even though it doesn't say true, just has to have a non-falsy value. (Used in a boolean or conditional context.)

Example: 
````js
let myVariable = 'I Exist!';

if (myVariable) {   
	console.log(myVariable)
} else {   
	console.log('The variable does not exist.')
}
````

### Truthy and Falsy Values
**Truthy Values**

**Falsy Values**
`0`
Empty strings like `""` or `''`
`null` which represent when there is no value at all
`undefined` which represent when a declared variable lacks a value
`NaN`, or Not a Number

````js
let username = '';
let defaultName = username || 'Stranger'; // if username is false, aka blank (it will be true if there is a username), Stranger is outputted
// || is OR 

console.log(defaultName); // Prints: Stranger
````

## Else if Statements
can be used to check additional conditions 
`if (time < 10) {

  greeting = 'Good morning 🌄';
} else if (time < 20) {
  greeting = 'Good day 🌁';
} else {
  greeting = 'Good evening 🌉';

}`
## Ternary Operators
simplifies if... else statements
````js
isNightTime ? console.log('Turn on the lights!') 
: console.log('Turn off the lights!');
````
condition `isNightTime` provided before the `?`
expressions follow the `?`
separated by the `:`

can also be used for statements that evaluate to true and false

## Switch statements
instead of using `else if` statements (messy!)
````js
let groceryItem = 'papaya';
if (groceryItem === 'tomato') {  
	console.log('Tomatoes are $0.49');
} else if (groceryItem === 'papaya'){  
	console.log('Papayas are $1.29');
} else {  console.log('Invalid item');
}
````
you can use a switch statement that can check multiple conditions:
````js
let groceryItem = 'papaya';

switch (groceryItem) {  
	case 'tomato':    
		console.log('Tomatoes are $0.49');    
		break;  
	case 'lime':    
		console.log('Limes are $1.49');    
		break;  
	case 'papaya':    
		console.log('Papayas are $1.29');    
		break;  
	default:    
		console.log('Invalid item');    
		break;
}

// Prints 'Papayas are $1.29'
````


