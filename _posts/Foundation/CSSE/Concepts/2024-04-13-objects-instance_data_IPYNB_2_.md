---
toc: True
comments: True
layout: post
title: Objects, Instance Data
description: Objects in JavaScript are a fundamental data type. Each Game Object, in the game, is a collections of instance data and methods. JavaScript Objects are used to store the states of a Game Objects.
courses: {'csse': {'week': 19}}
type: ccc
---

## Properties and Methods

- **Properties**: These are the values associated with a JavaScript object. A JavaScript object is a collection of unordered properties. Properties can usually be changed, added, and deleted.

- **Methods**: These are actions that can be performed on objects. A method is a property that contains a function definition.

For example, consider an object representing a player in a game:

```javascript
let player = {
    name: "John",
    health: 100,
    level: 1,
    fullName: function() {
        return this.name + " the Brave";
    },
    attack: function() {
        console.log(this.name + " attacks!");
    }
};

In this example, name, health, and level are properties, while fullName and attack are methods.

## How to Access Properties and Methods

Properties and methods of an object can be accessed using ***dot notation*** or ***bracket notation***.

### Dot notation

```javascript
// Property
objectName.propertyName 
// Method
objectName.methodName()
```

### Bracket notation

```javascript
// Property
objectName["propertyName"]
// Method
objectName["methodName"]()
```

### Example using person object

```javascript
// To access the firstName property of the person object
// Dot Notation Property
person.firstName
// Bracket Notation Property
person["firstName"]
// Dot Notation Method
person.fullName()
// Bracket Notation Method
person["fullName"]()
```

### Object Summary
Understanding objects is crucial for understanding JavaScript, and they are used extensively in all the code we will be looking at.

## Transition to Class-Based Structures
As we advance, we will transition from using object literals to class-based structures, which provide a more organized and scalable way to define objects, similar to Java. A class-based data structure will help us write more organized and maintainable code, especially as we develop more complex game features.

A class in JavaScript is defined using the **class keyword**. 
- **Properties** are defined within the constructor
- **Methods** are defined as functions within the class.

### class PlayerBase
Using a classic Java-like **class** definition, we can encapsulate JavaScript objects. The **player object** created below contains properties and methods for a player in our Platformer game. The `this.state` data structure is used to hold many of the player's properties as it interacts in the game.

This is the code that creates an object:

```javascript
let player = new PlayerBase();
```

### Setting data

Property data can be set and accessed using dot notation:

```javascript
player.state.collision = 'wall';  // string type
player.state.movement = {up: false, down: false, left: true, right: false, falling: false}; // object type
```

## PlayerBase sample

In the PlayerBase code cell below, we highlight some features of managing **player** properties.




```javascript
%%javascript

class PlayerBase {
    /**
     * Initial environment of the player.
     * @property {string} collision - Name of the current object the player is interacting with (e.g., 'floor', 'wall', 'platform').
     * @property {Array} collisions -  An array that holds a collection of player collisions.
     * @property {string} animation - Name of the current animation state of the player (e.g., 'idle', 'walk', 'run', 'jump').
     * @property {string} direction - The direction the player is facing (e.g., 'left', 'right').
     * @property {Object} movement - The directions in which the player can move.
     * @property {boolean} movement.up - Whether the player can move up.
     * @property {boolean} movement.down - Whether the player can move down.
     * @property {boolean} movement.left - Whether the player can move left.
     * @property {boolean} movement.right - Whether the player can move right.
     * @property {boolean} movement.falling - Whether the player is falling.
     * @property {boolean} isDying - Whether the player is dying.
     */

    // This object represents the initial state of the player when the game starts.
    initEnvironmentState = {
        // environment
        collision: 'none',
        collisions: [],
        // player
        animation: 'idle',
        direction: 'right',
        movement: {up: false, down: false, left: true, right: true, falling: false},
        isDying: false,
    };

    /** GameObject: Constructor for Player object
     */
    constructor() {      
        this.state = {...this.initEnvironmentState}; // Player and environment states 
    }


    /**
     * Adds a collision to the history and updates the current collision.
     * @param {string} collision - The new collision to add.
     */
    addCollision(collision) {
        this.state.collisions.push(collision);
        this.state.collision = collision;
    }

    /**
     * Pops the last collision from the history and updates the current collision.
     * If the collision stack is empty, the current collision is set to 'none'.
     */
    popCollision() {
        this.state.collisions.pop();
        this.state.collision = this.state.collisions[this.state.collisions.length - 1] || 'none';
    }

    /**
     * Returns a formatted HTML string representing the player's state.
     * Primary purpose is to display the state in a Jupyter notebook.
     * @returns {string} - The formatted state HTML string.
     */
        toHTML() {
            let collisions = (this.state.collisions.length > 0) ? this.state.collisions.slice().reverse().map((collision, index) => `  ${collision}`).join(', ')  : 'none';
            return `
            <div>
                <strong>Collision Stack:</strong> ${collisions}
                <br>
                <strong>Player State:</strong>
                <ul>
                    <li>Collision: ${this.state.collision}</li>
                    <li>Animation: ${this.state.animation}</li>
                    <li>Direction: ${this.state.direction}</li>
                    <li>Movement:
                        <ul>
                            <li>Up: ${this.state.movement.up}</li>
                            <li>Down: ${this.state.movement.down}</li>
                            <li>Left: ${this.state.movement.left}</li>
                            <li>Right: ${this.state.movement.right}</li>
                            <li>Falling: ${this.state.movement.falling}</li>
                        </ul>
                    </li>
                    <li>Is Dying: ${this.state.isDying}</li>
                </ul>
            </div>
            `;
        }
    
}

// Example usage
const player = new PlayerBase();

// Initial state
// Jupyter JavaScript magic element is used to display the output, versus normal DOM
element.append("Initial instance data for a player:");
element.append(player.toHTML());

// Simulate Wall collision
player.addCollision('wall');
player.state.movement = {up: false, down: false, left: true, right: false, falling: false};
element.append("Wall collision simulation:");
element.append(player.toHTML());

// Simulate JumpPlatform collision
player.addCollision('jumpPlatform');
player.state.movement = {up: false, down: false, left: true, right: true, falling: false};
element.append("JumpPlatform collision simulation:");
element.append(player.toHTML());

// Pop back to the previous collision
player.popCollision();
element.append("Pop back to the previous collision (back 1):");
element.append(player.toHTML());

// Pop back again to the previous collision
player.popCollision();
element.append("Pop back to the previous collision (back 2):");
element.append(player.toHTML());
```


    <IPython.core.display.Javascript object>

