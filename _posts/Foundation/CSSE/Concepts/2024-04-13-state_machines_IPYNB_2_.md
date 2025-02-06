---
toc: True
comments: True
layout: post
title: Finite State Programming
description: In a game, the player can only be in a finite number of states. The player can move from one state to another based on the player's actions. This is the essence of finite state programming.
courses: {'csse': {'week': 20}}
type: ccc
---

## State Machines 

State machines, also known as finite state machines (FSMs) or finite state automata (FSAs), are mathematical models of computation used in computer science, linguistics, and related fields. They are abstract machines that can be in exactly one of a finite number of states at any given time.

### States

In the context of a game, a state could represent the status or condition of a game character at a given time. For example, `state.animation` could represent the current animation state of a character, such as 'idle', 'walk', 'run', or 'jump'. Similarly, `state.collision` could represent the current collision state of a character, such as 'floor', 'wall', or 'jumpPlatform'.

### Transitions

Transitions are the rules or conditions that dictate when and how a state machine can move from one state to another. In a game, a transition could be triggered by a user action (like pressing a key), a timer, or a change in game conditions (like a collision with another object).

### Actions

Actions are the behaviors associated with a particular state. When a state machine enters a state, it might perform an action associated with that state. For example, if a character enters the 'walk' state, the action might be to start the walking animation.

In the context of a game, state machines can be used to manage game logic, character behaviors, animations, and more. They provide a structured way to handle the complex, dynamic conditions that can arise in a game.

## The role of states in game logic 
Based on various factors, some synchronous and some asynchronous, the game states will change. JavaScript objects have been created to track these specific states. Finite state game logic is used to process these states as the game loop proceeds.

Here is an example of collision finite state logic. This logic handles collisions between the player and other game objects.

```javascript
switch (this.state.collision) {
    // 1. Player is on a jump platform
    case "jumpPlatform":
        // Player is on top of the jump platform
        // ... code
        break;
    // 2. Player is on or touching a wall 
    case "wall":
        // Player is on top of the wall
        // ... code
        break;
    // 3. Player is in default state
    case "floor":
        // Player is on the floor
        // ... code
        break;
}
```

Here is an example of animation finite state logic. This logic sets the sprite animation frame based on the player's current state.

```javascript
switch (this.state.animation) {
    case 'idle':
        this.setSpriteAnimation(this.playerData.idle[this.state.direction]);
        break;
    case 'walk':
        this.setSpriteAnimation(this.playerData.walk[this.state.direction]);
        break;
    case 'run':
        this.setSpriteAnimation(this.playerData.run[this.state.direction]);
        break;
    case 'jump':
        this.setSpriteAnimation(this.playerData.jump[this.state.direction]);
        break;
    default:
        console.error(`Invalid state: ${this.state.animation}`);
}
```

### Finite state change
The code below shows how objects can be changed to create a different state in the game. Be sure to review PlayerBase.js for the actual finite state game logic.


```python
%%js

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
        collision: 'floor',
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

    toStringStates() {
        var msg = "Animation: " + this.state.animation;
        msg += ", Collision: " + this.state.collision;
        msg += ", Direction: " + this.state.direction;
        msg += ",";
        return msg;
    }

    toStringAction() {
        var msg = "Movement: ";
        for (const [key, value] of Object.entries(this.state.movement)) {
            msg += key + ": " + value + ", ";
        }
        return msg;
    }

    toString() {
        return this.toStringStates() + "\n" + this.toStringAction();
    }   
}

// Create a new PlayerBase object
var player = new PlayerBase();
element.append(player.toString()); // 'element.append' only works in Jupyter. Use 'console.log()' in a web environment.

// Spacing for the next output
element.append('<br><br>');

// Change the collision state of the player
player.state.animation = 'jump';
player.state.collision = 'jumpPlatform';
player.state.direction = 'left';
player.state.movement = {up: false, down: false, left: true, right: true, falling: false};
element.append(player.toString());
```


    <IPython.core.display.Javascript object>

