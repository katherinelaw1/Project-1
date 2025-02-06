---
layout: post
title: Variables Homework
description: JavaScript variable homework exercises to apply your skills.
type: collab
comments: True
categories: ['CSSE JavaScript Fundamentals']
permalink: /csse/lessons/variables/homework
---

# Lesson 1 homework - Level 1

You are in charge of maintaining an illegal arcade. You bought shoddy arcade machines off of Temu and they sadly came with missing information. You need to help put back the missing information to allow your shady customers to lose all their money at your store.

Create a float variable to make the default score 0.00 so the grimy kids don't win when gambling.


```python
%%js
// Would you use Let or Const? Let
let score = 0.00
```


    <IPython.core.display.Javascript object>


Define a variable "playerLimit" that cannot be re-assigned and give it a value of 4. This will prevent the raggamuffins from ruining your game.


```python
%%js
const playerlimit = 4 //Const makes sure that the values do not change
```


    <IPython.core.display.Javascript object>


Create a string variable to store the players name. Those dirty children have to verify their victory somehow.


```python
%%js
let PlayerName = "katherine"; 
```


    <IPython.core.display.Javascript object>


Make a boolean to set gameFunction to false.


```python
%%js
let gameFunction = false;
```


    <IPython.core.display.Javascript object>


Now put it all together in this code cell to allow the children to gamble away all their parents money! The quick example may help you, it is for a superhero game the basement dwellers fixed.


```python
%%js
// 1. Hero Name (String)
let heroName = prompt("Your name here");

// 2. Points Scored (Number)
let points = 0.0;

// 3. Energy Levels (Number
let energyLevel = 100.0;

// 4. Mission Status (Boolean)
let missionComplete = false;

// Training Simulation
console.log(`Welcome, ${heroName}! Your training begins now.`);
console.log(`Starting energy level: ${energyLevel}`);
console.log(`Points: ${points}`);

// Task 1
energyLevel -= 5.5;
points += 10;
console.log("You completed a task!");
console.log(`Energy level: ${energyLevel}`);
console.log(`Points: ${points}`);

// Task 2
energyLevel -= 5.5;
points += 10;
console.log("You completed another task!");
console.log(`Energy level: ${energyLevel}`);
console.log(`Points: ${points}`);

// Completing the mission
missionComplete = true;
if (missionComplete) {
    console.log(`Mission Accomplished, ${heroName}!`);
    console.log(`Final score: ${points}`);
}
```


    <IPython.core.display.Javascript object>


Now, create something that on run, defines a playername, sets a game score, and decreases some amount from it. Make sure to use console.log to print the playername and the variable before and after the operation. Go forth, future basement dwellers.


```python
%%js
let playerName = "Katherine"; //tells us the name of the player
let gameScore= 100; // tells us the score

console.log(playerName); //prints name
console.log (gameScore); //prints score
gameScore -= 2; //subtracts two from score
console.log(gameScore); // prints the new score
```

## Lesson 1 homework - Level 2

This homework is harder than the last, to make sure you are efficient workers in the basement. You will now create code for a space invaders knockoff since we obviously can't afford to get the actual one. 
- Complete the code and READ THE COMMENTS. Don't leave any underscores and make some working code!


```python
%%js
//Replace Blanks and fill in information with code

// Put variables for spaceship and mission below
let spaceship = "Flying town"; // Name your spaceship! The red will show up in console once complete.
let initialFuel = 100; // Initial fuel value
let distanceTraveled = 0; // Set distance travelled
let fuelConsumptionRate = 2; // Fuel decrease rate per distance = 2


// 2. Mission variables assigning
let selectedFuel = 50; // Assign how much fuel is allocated for the mission
let missionStatus = ""; // Status of the mission
let fuelDrops = Math.floor(Math.random() * 3) + 1; 
// Random fuel drops (1 to 3) - the _ outside the parenthesis is the minimum fuel drop, so is that 1 or 3

// 3. Add random fuel during the mission
function collectFuel(currentFuel, distance) {
  let fuelCollected = Math.floor(Math.random() * 15) + 10; // Random fuel between 10 and 30 - remember from before
  console.log(`At distance ${distance}, a fuel drop was found! Collected ${fuelCollected} fuel.`);
  return currentFuel + fuelCollected; //Replace with the variable you defined above - fuelC_______
}

// 4. Mission logic - makes mission occur - dont worry about if else statement
if (selectedFuel > initialFuel) {
  missionStatus = "Mission failed. Not enough fuel!"; //If selected fuel is greater than initial fuel will it fail or be succsesfull
} else if (selectedFuel <= 0) {
  missionStatus = "Mission aborted. Fuel must be greater than zero."; //If selected fuel is greater than initial fuel will it fail or abort
} else {
  // Begining mission
  for (let i = 0; i < fuelDrops; i++) {
    // Calculates distance and updates remaining fuel
    distanceTraveled += selectedFuel / fuelConsumptionRate;
    initialFuel -= selectedFuel;

    // Check if there’s still enough fuel for the mission
    if (initialFuel <= 0) {
      missionStatus = `Mission failed! The spaceship ran out of fuel after traveling ${distanceTraveled} units.`; //If selected fuel is greater than initial fuel will it fail or be succsesfull
      break;
    }

    // Collect random fuel
    initialFuel = collectFuel(initialFuel, distanceTraveled); //
  }

  // Set end results of mission status
  if (initialFuel > 0) {
    missionStatus = `Mission successful! The spaceship ${spaceship} traveled ${distanceTraveled} units of distance. Remaining fuel: ${initialFuel}`; //If selected fuel is greater than initial fuel will it fail or be succsesfull
  }
}

// 5. Output the mission results - what can print stuff 
console.log(`name: ${spaceship}`);
console.log(`Fuel given: ${selectedFuel}`);
console.log(`distanceTraveled: ${distanceTraveled}`);
console.log(`Remaining fuel: ${initialFuel}`);
console.log(`missionStatus: ${missionStatus}`);
// Hint red underscores may just be whats in the {}'s - you can also change this to alter what it says
```


    <IPython.core.display.Javascript object>


- For you cheating basement dwellers, look away and go complete your code for minimal to no pay. 
- But for those of you who completed it, here is something to check your code with. Also make sure to run your own code and see it in console to ensure the gambling children can play the games.


```python
%%js

let spaceship = "Mort's Flying Monkey";
let initialFuel = 100; 
let distanceTraveled = 0; 
let fuelConsumptionRate = 2; 

let selectedFuel = 50; 
let missionStatus = ""; 
let fuelDrops = Math.floor(Math.random() * 3) + 1; 


function collectFuel(currentFuel, distance) {
  let fuelCollected = Math.floor(Math.random() * 20) + 10; 
  console.log(`At distance ${distance}, a fuel drop was found! Collected ${fuelCollected} fuel.`);
  return currentFuel + fuelCollected;
}

if (selectedFuel > initialFuel) {
  missionStatus = "Mission failed. Not enough fuel!";
} else if (selectedFuel <= 0) {
  missionStatus = "Mission aborted. Fuel must be greater than zero.";
} else {

  for (let i = 0; i < fuelDrops; i++) {
   
    distanceTraveled += selectedFuel / fuelConsumptionRate;
    initialFuel -= selectedFuel;

    
    if (initialFuel <= 0) {
      missionStatus = `Mission failed! The spaceship ran out of fuel after traveling ${distanceTraveled} units.`;
      break;
    }

    
    initialFuel = collectFuel(initialFuel, distanceTraveled);
  }

  
  if (initialFuel > 0) {
    missionStatus = `Mission successful! The spaceship ${spaceship} traveled ${distanceTraveled} units of distance. Remaining fuel: ${initialFuel}`;
  }
}

console.log(`Spaceship: ${spaceship}`);
console.log(`Fuel given: ${selectedFuel}`);
console.log(`Distance traveled: ${distanceTraveled}`);
console.log(`Remaining fuel: ${initialFuel}`);
console.log(`Mission Status: ${missionStatus}`);
```


    <IPython.core.display.Javascript object>


### Lesson 2: Level 1

You need to get the color of the cars from the frogger game. Use an instance variable called myCar to accomplish this. 


```python
%%js
class Car {
    constructor(color) {
      this.color = color;  // Put your instance varibale in the blank
    }
  
    getColor() {
      return this.color;
    }
  }
  
  const myCar = new Car("Pink"); // Choose any color
  console.log(myCar.getColor()); // Once run, you should see your color in the console
  
```

You need a static variable for player lives. Use the variable playerLives to set the number of lives to 3.


```python
%%js
class Health {
    static playerLives = 2;  // Make static variable and number for it

}
  console.log(Health.playerLives); 
```

### Lesson 2 - Level 2

Create a Book class with an instance variable title and a static variable bookCount that tracks how many books have been created. Add a method getBookInfo() to return the book's title and total number of books.


```python
%%js
class Book {
    static bookCount = 0;  // Static variable (maybe read above?)
  
    constructor(title) {
      this.title = title;  // Instance variable for title
      Book.bookcount++;  // Use the static variable and increment it
    }
  
    getBookInfo() {
      return `Book Title: ${this.title}, Total Books: ${Book.bookCount}`; // use the instance and static variables here
    }
  }
  
  const book1 = new Book("Mort's Guide to Making Students Fear You");
  const book2 = new Book("How to make slime"); // Name a book for yourself
  console.log(book1.getBookInfo()); // Output: Book Title: JavaScript Basics, Total Books: 2
  console.log(book2.getBookInfo()); // Output: Book Title: Advanced JavaScript, Total Books: 2
  
```


    <IPython.core.display.Javascript object>


Create an ArcadeGame class that:
- Has instance variables gameName and highScore.
- Has a static variable totalGames to track how many - arcade games have been created.
- Includes a method getGameInfo() to return the game name and high score.
- Includes a static method getTotalGames() to return the total number of arcade games created.


```python
class ArcadeGame {
    static totalGames = 0;  // Static variable to track total number of games
  
    constructor(gameName, highScore) {
      this.gameName = gameName;  // Instance variable - same thing in each blank
      this.highScore = highScore;  // Instance variable - same thing in each blank
      ArcadeGame.totalGames++;  // Increment static variable each time a new game is created
    }
  
    // Instance method to return the game name and high score
    getGameInfo() {
      return `${this.gameName}: High Score = ${this.highScore}`; //The instance variables from above maybe?
    }
  
    // Static method to get the total number of games
    static getTotalGames() {
      return ArcadeGame.totalGames;
    }
  }
  
  // Create instances of the ArcadeGame class
  const game1 = new ArcadeGame("High Jump", 5000); //Put any name for a game in the blank
  const game2 = new ArcadeGame("Low Jump", 7000);
  
  // Display game info
  console.log(game1.getGameInfo()); // Output: Your games High Score = 5000
  console.log(game2.getGameInfo()); // Output: Your games #2: High Score = 7000
  
  // Display total arcade games count
  console.log(ArcadeGame.getTotalGames()); // Output: 2
  
```
