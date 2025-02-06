---
layout: post
title: Variables Popcorn Hax
description: Exercises to do mid-lesson, when instructed. Designed to be fairly easy and help you apply a basic understanding of variables you should already have from the lesson.
type: collab
comments: False
categories: ['CSSE JavaScript Fundamentals']
permalink: /csse/lessons/variables/popcornHax
---

<h1>Popcorn Hax</h1>

To access printed results using console.log, follow this simple set of steps.
1: Access the "Help" button near the top of your screen (next to to "Terminal" and "Window). It looks something like this on macOS:<br>
<img width="844" alt="image" src="https://github.com/user-attachments/assets/18465a9b-e7e3-4f9d-8653-3ede47e2dfc6" />
<br>
After clicking help, the drop-down menu should have a "Toggle Developer Tools" option. Click it, and navigate to the console menu.
Then, look for a little O with a line through it. Click this to clear the console.

<h2>Lesson 1, Exercise 1:</h2><br>
Define a variable "charHealth" as an integer value of 100. Then, run a command to print the value and type of charHealth.



```python
%%js
//On this line, define charHealth. 
let charHealth = 1

//Run the command to print charHealth's value here.
console.log(charHealth)

//Run the command to check the type of variable here.
console.log(typeof charHealth)
```


    <IPython.core.display.Javascript object>


<h2>Exercise 2:</h2><br>
Define two variables: "charHealth" and "damage". Then, combine the two to update charHealth. Make sure they are the same type of variable - otherwise, you will not be able to combine them.


```python
%%js
//Define variables up here. Make sure they are both number values.
let charHealth = 200
let damage = 20
//Update charHealth after the player has taken damage. The character should lose health relative to damage taken. Print your results.
charHealth -= damage
console.log(charHealth);
```


    <IPython.core.display.Javascript object>


<h2>Exercise 3:</h2><br>
Create two parts of a message, and store each part as a separate variable. Combine these variables into a new one, finalMessage, and print its results.


```python
%%js
//Define variables and combine them here
let messagePart1 = "hello"
let messagePart2 = "Friend"
let finalMessage = messagePart1 + messagePart2
//Print results here.
console.log(finalMessage); //Insert variable
```


    <IPython.core.display.Javascript object>


<b1>
Make sure to end each line with a semicolon (;). 
<br>Part 2: Using this if conditional, see if you can get the console to output "You have successfully manipulated these strings! Good Job!" If you don't get the desired result, try again.
</b1>


```python
%%js
let m1 = "Hello, ";
let m2 = "world!"; //Edit this 

if (m1 + m2 == "Hello, world!"){
    console.log("You have successfully manipulated these strings! Good Job!");
} else {
    console.log("Failed to match strings. Try again.");
}
console.log(m1 + m2); //Should say "Hello, world!"
```


    <IPython.core.display.Javascript object>


Try defining a score variable and a string that displays the player's score. A very basic version of this has been set up for you here, using Math.random() to get a random number.


```python
%%js 
let gambling = Math.round(100 * Math.random()) //Random integer from 0 to 100. Math.round just takes the decimal produced by Math.random and rounds it for you (crazy I know).
let gamblingTalk = `You won ${gambling}`//Use graves and ${} to make gamblingTalk contain the random number, along with a message.

console.log(gamblingTalk); //Print gamblingTalk.
```


    <IPython.core.display.Javascript object>


Lastly, here's a quick way to learn the difference between =, ==, and ===.


```python
%%js
let m1 = "1"; //Note the data types present in these two variables. This is a string.
let m2 = 1; //This is a number.
console.log(m1==m2);
//Use a loose equality and see what the computer thinks about m1 and m2.
console.log(m1===m2);
//Use a strict equality and see what the computer says. Why are your results different?
```


    <IPython.core.display.Javascript object>


<h2>Exercise 4:</h2><br>
Here, a Math.random function creates a number from 0 to 1. Using the conditional set up for you and your knowledge of booleans, create a system that checks if the number created is greater than 0.7.


```python
%%js
let isGreaterThan = false; //What should this be defined as by default?
let randomNum = Math.random(); //Makes a random number.
if (randomNum > 0.7) { //Put something in the parentheses to check if the random number is over 0.7.
    isGreaterThan = true;
} 
console.log(isGreaterThan); //Output the value of isGreaterThan

//Run this a few times, and see if you get a mix of true and false outputs.
```


    <IPython.core.display.Javascript object>


<h2>Exercise 5:</h2><br>
- Fix this code to correctly output the type of data message1 is.
- In code, undefined and null are not used intentionally very often. This exercise is an example on why it is useful: since message1 is not defined, you can check this with console.log(). If this results in an undefined output, you can go change the variable to be correctly defined.


```python
%%js
//This is a very open-ended exercise. What type of variable to you want message1 to be? Depending on your answer, 
// you will define message1 differently, likely with a different name (like score or isAlive).
let epicName = "hello"; //Change this, go nuts.
console.log(epicName); //Output the variable.
console.log(typeof epicName); //Output its type.
```


    <IPython.core.display.Javascript object>


<h2>Exercise 6:</h2><br>
Create a bigInt with a value of your choosing. Check to make sure it's a big enough number. The highest number in JS is 9007199254740990, and can be referenced with the property Number.MAX_SAFE_INTEGER.


```python
%%js
let bigNumber = 999999999999999999n //Pick a big number. End it with n to make sure it's a bigInt type of variable.
let x = Number.MAX_SAFE_INTEGER;
console.log(bigNumber>x); //Check to make sure your number is big enough (so, bigger than x). You're looking for a "true" output.
console.log(bigNumber); //Big number go brrrrr
```


    <IPython.core.display.Javascript object>


<h2>Exercise 7:</h2><br>
- Create a "player" object with as many properties as you can think of. A minimum of 5 properties and at least 3 different types of variables must be used to complete this exercise.
- After this, print 2 of those variables. One has already been done for you, and the other started. Lastly, change the player's health and print it again.


```python
%%js
//A few variables are included for you already, fill the rest in on your own.
let player = {
    name: "Katherine", //Replace with your name/gamertag.
    health: 25 //commas between every term, except the last one.
    score: 100
    weapon: gun



};
//Reference your parts here. Add one final console.log() and just print player. See what happens.
console.log(Katherine);



//Change and reference player's health
player.health = ;
console.log(player.health); //new health 
```


    <IPython.core.display.Javascript object>


<h2>Exercise 8:</h2><br>
Create a "user" object with a password variable as a symbol. Other than that, customize the object similarly to the previous exercise (Minimum of 5 variables, minimum of 3 types). There's a nifty little bonus at the bottom of this exercise which shows the power of symbols.


```python
%%js 
const password = Symbol(); //Defines the password symbol. It's okay to leave his empty, as you will assign the symbol a value in the object.
const backupPassword = Symbol(); 
let user ={
    [password]: "1234" //Assign the symbol a value here. 
    [backupPassword]: "1234" //Assign your backup password a value. Make this the same as your default password.
    username: "katherine123" //Fill in the rest of the object's properties. Replace this username with your own.

}
//Referencing symbols looks like this:
console.log(user[password]);
//This outputs the value of "password" you assigned earlier.
```


    <IPython.core.display.Javascript object>


<h2>Lesson 2, Exercise 1:</h2>
<b1>
btw, classes are thing that you will learn later. I'm not explaining them now jus roll with it
</b1>

Imagine this: you have a brand-spankin' shiny new game that you made, and you want to keep track of how many players you have. Using context clues and my helpful comments, fill in the blanks.

Next, try and see if you can make the player number increase.


```python
%%js 
class Player {
    static totalPlayers = 0 //Hmm I wonder what the constant, "global" variable could be in this context (pick from either totalPlayers or name)

    constructor(name) {
        this.name = name // I wonder what name could be
        this.id = ++Player.totalPlayers
    }

    static getTotalPlayers() { // this is the thing that will give you the number of players
        return Player.totalPlayers
    }
}
const player1 = new Player("RedIsSus")
const player2 = new Player("Jimmy")
// I wonder if making new players would increase the player count

console.log(Player.getTotalPlayer) // you want to print the *function* that will give you the player numbers.
```


    <IPython.core.display.Javascript object>


<h2>Exercise Dos</h2>


```python
%%js
class Car {
    constructor(color, model) {
        this.color = color;    // Instance variable
        this.model = model; //Set up another instanced variable
    }
}

const car1 = new Car("Red ", "2006 Nissan Murano");
const car2 = new Car("Blue ", "2019 Toyota Corolla");

console.log(car1.color + car1.model);  // Prints car colors and models. Make sure to reference the instanced variable here.
console.log(car2.color + car2.model);  

car1.color = "Yellow ";    // Only changes car1.
console.log(car1.color + car1.model);  // Logs changes.
console.log(car2.color + car2.model);  // No change from earlier.
```
