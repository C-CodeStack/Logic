# JavaScript Logic 
Previously you learned about `variables` but your code always did the same thing no matter what the variables held. This time you are going to make your code perform different tasks depending on what a variable holds.

To illistrate this point lets imagine that you go to the DMV to get your drivers license. The first thing they will ask you is `How old are you?`. `If` you respond with `19` then you may take the exam. `If` you respond with `15` then you may not take the exam.

You want to execute this interaction within your code. You first need to ask the user a question and then save their answer.

```javascript
let money = prompt("How much money do you have?") // typeof -> string
money = parseInt(money) // typeof -> number
```

When you see the above code you are probably thinking, "what does money have to do with our DMV scenerio". You are right it is not exactly applicable. However, when you develope code it is rare to find that someone wrote your exact answer for you. More often you find that someone wrote code similar to your answer and you need to learn how to take it and adapt it to your needs. As such, I will usually develop a similar code that you will have to adapt to complete your tasks.

Now back to your code. In the above code the variable `money` is created. Then `prompt()` asks the user whatever is in the quotes and waits for a response. The users response will be saved(`assigned`) to `money` as a string. You need it to be a number so you use `parseInt(money)` to change it to a number and save it back into the `money` variable.

```javascript
let money = parseInt(prompt("How much money do you have?"))// this can be done in one line
```

## Task 1
1. declare a variable called `age`.
2. Ask the user `How old are you?`
3. Assign the answer to `age`

Don't forget to turn it from a `string` to a `number`.
#

Now that you have the users `age` you need to respond with `you may take the exam` or `you may not take the exam`. To determine which to respond with you need to use the `if` statement.

```javascript
if (condition) {
  //do something
}
```

In the `if` statement we need to get a `boolean` value or `true`, `false` inside the parenthesis. To do this you need to use `comparison operators`. These operators are `===`(equals), `!==`(not equals), `<`(less than), `>`(greater than), `<=`(less than or equal), `>=`(greater than or equal), `&&`(and), `||`(or). These examples will help define them.

```javascript
(1 === 2) // -> false
(1 !== 2) // -> true
(1 < 2) // -> true
(1 > 2) // -> false
(1 <= 2) // -> true
(1 >= 2) // -> false
(1 < 2 && 2 < 3) // -> true
(1 < 2 && 2 > 3) // -> false
(1 < 2 || 2 < 3) // -> true
(1 < 2 || 2 > 3) // -> true
(1 > 2 || 2 > 3) // -> false
```

Now that you know about the comparison operators you can do something like this.

```javascript
if (money > playstation_cost) {
  console.log("You can buy the Playstation!")
}
```

In the example above `money` and `playstation_cost` are variables that hold numbers

## Task 2
1. Create your own `if` statement using your variable `age` and `16`
2. If the users responds with an age `greater than or equal` to 16 then respond with `You may take the exam!`
#

You have covered the case where the user is greater than or equal to 16 but what if they are younger? You could do something like this

```javascript
if (money >= playstation_cost) {
  console.log("You can buy the Playstation!")
}

if (money <= playstation_cost) {
  console.log("You will not be getting the playstation.")
}
```

This is not a prefered method because in some situations you could get both `logs` running. Like if money was equal to playstation_cost. That would be really confusing to the user. So you have another tool called the `else` condition. The code in the `else` section runs only if the `if` condition is `false`.

```javascript
if (money >= playstation_cost) {
  console.log("You can buy the Playstation!")
}
else {
  console.log("You will not be getting the playstation.")
}
```

In the code above it is now impossible to run both `logs` because money >= playstation_cost is either `true` or `false`. If it is `true` the first log will run and if it is `false` the second log will run.

## Task 3
Add an `else` to your if statement. Respond with `You may not take the exam.`
#

If someone is 16 lets add the message `Your barely old enough. You can take the exam!`

So now you want 3 possible outcomes. Greater than 16 `You may take the exam`, equal to 16 `Your barely old enough. You can take the exam!`, anything else(`less than 16`) `You may not take the exam`. Since we only want one 1 of the 3 outcomes to be possible we need to use an `else if` statement.

```javascript
if (money > playstation_cost) {
  console.log("You can buy the Playstation!")
}
else if (money === playstation_cost) {
  console.log("You exactly enough to buy the Playstation!")
}
else {
  console.log("You will not be getting the playstation.")
}
```

## Task 4
Modify your `if else` statement to be an `if, else if, else` chain as described above. Your answer should look similar to the JS just above this.

1. Greater than 16 `You may take the exam`
2. If someone is 16 lets add the message `Your barely old enough. You can take the exam!`
3. anything else(`less than 16`) `You may not take the exam`
#

Lets say you want to get crazy and give a different log for every year approaching 16. That would look like this.

```javascript
//to keep things short we will not consider anything over 16
if (age === 16) {
  console.log("Your barely old enough. You can take the exam!")
}
else if (age === 15) {
  console.log("1 year away")
}
else if (age === 14) {
  console.log("2 years away")
}
else if (age === 13) {
  console.log("3 years away")
}
else if (age === 12) {
  console.log("4 years away")
}
else if (age === 11) {
  console.log("5 years away")
}
else if (age === 10) {
  console.log("6 years away")
}
else if (age === 9) {
  console.log("7 years away")
}
else {
  console.log("A really long time")
}
```

What a mess. You have a tool to clean this up called the `switch` statement. It can turn all that code into this.

```javascript
//assume playstation_cost = 200
//and we are not considering anything over 200
switch (money) {
  case 200:
    console.log("You can buy it!");
		break;
  case 199:
    console.log("$1 away");
		break;
  case 198:
    console.log("$2 away");
		break;
  case 197:
    console.log("$3 away");
		break;
  case 196:
    console.log("$4 away");
		break;
  case 195:
    console.log("$5 away");
		break;
  case 194:
    console.log("$6 away");
		break;
  case 193:
    console.log("$7 away");
		break;
  default://runs if nothing else runs and does not have to be at the bottem
		console.log("You need a job!");
		break;
}
```

If you forget the `break` the code will execute every `log` until it hits a `break`. So if you didn't put a break inside case 200 and money = 200 you would log `You can buy it!` and `$1 away`

## Task 5
Turn the long if, else if, else chain from 2 examples ago into a switch like the last example. Do not change the if, make a new switch under it.
#

## Task 6
Create another if, else if, else chain that meets the following conditions
1. asks the user for number of siblings
2. if siblings is greater than 3 respond with "wow big family"
3. if siblings is greater than 0 respond with "good size family"
4. if siblings is zero respond with "oh your an only child"
#

Your final code in the index.js should have the following.

1. Ask the user for their age
2. if, else if, else chain
3. switch
4. sibling if, else if, else chain
5. It should all execute without errors and show the appropriate logs in the console