---
toc: True
comments: True
layout: post
title: Single Responsibility Principle
description: This post will introduce you to Single Responsibility Principle (SRP) and how to apply it in your code.
courses: {'csse': {'week': 21}}
type: ccc
---

## Designing with Single Responsibility Principle (SRP)
The Single Responsibility Principle is a programming concept that states that a class or method should have only one reason to change. This means that a class or method should only have one job or responsibility. This principle is part of the SOLID principles of Object-Oriented Programming (OOP).

- Class design.  SRP helps to keep the code more maintainable and understandable. When classes have more than one responsibility, they can become complex and can be harder to understand, maintain, and change. By ensuring that each class has only one responsibility, we can keep our code clean, organized, and easier to work with.

- Method design.  In game development, it's crucial to keep code as simple and clear as possible using SRP. Games often involve complex systems interacting with each other, and having clear, single-purpose methods can make it easier to understand how these systems work together. It also makes it easier to isolate and fix bugs, as each method is responsible for one thing.

- The importance of single purpose classes and methods in game development

  - Easier debugging and testing. When each class and method has a single responsibility, it's easier to write tests for them and to debug them when things go wrong. You can focus on testing one specific functionality at a time, and if a test fails, you know exactly where to look for the problem.

  - More readable and maintainable code. Code that follows the SRP is generally more readable and easier to maintain. Each class and method does one thing, so it's easier to understand what each part of the code is supposed to do. This makes it easier for other developers to understand your code, and it makes it easier for you to understand and update your code in the future.

## The role of SRP in game Design 
Code complexity without Single Responsibility Principle (SRP) can quickly become unreadable and changes can become daunting.  Code with SRP more clearly illustrates code flow and order of operations.

In this example, we will follow OOP design and SRP principles by tracking the update process in the game.

### GameEnv Update
Here is an example of SRP design pattern showing gameObject.update() method that is called within the GameLoop, the GameEnv update() is called from the GameControl gameLoop(). 

This gameObject.update() method call, using SRP principle, is distinct from the gameObject.serialize() method and the gameObject.draw() method. Read the descriptions of the static update() method calls...

- gameObject.update(). Updates to game object state(s).
- gameObject.serialize(). Prepares game object updates for multiplayer sharing.
- gameObject.draw(). Renders the game object on the screen, canvas element.

```javascript
static update() {
    // Update game state, including all game objects
    // if statement prevents game from updating upon player death
    if (GameEnv.player === null || GameEnv.player.state.isDying === false) {
        for (const gameObject of GameEnv.gameObjects) {
            gameObject.update();  
            gameObject.serialize(); 
            gameObject.draw(); 
        } 
    }
}
```

### Player Update
Here is an example of managing player updates. This is the update() method required by the GameLoop for class PlayerBase.  Using the SRP design pattern, each portion of update is split into a unique method...

- updateAnimation().  Prepares the animation frame for the Player
- updateMovement().  Handles the x and y changes of the Player
- super.update().  Calls the update method of the parent class, Character

```javascript
update() {
    // player methods
    this.updateAnimation();
    this.updateMovement();

    // parent actions are performed after child specific actions
    super.update();
}
```

### Character Update
Here is the super update method defined in class Character a direct descendent of class GameObject. PlayerBase is a Character direct descendent. This follow SRP design in Character handles moving characters like a player or a goomba, which require updates according to gravity and frames for animation.  

- updateY(). Handles y axis updates, primarily related to gravity simulation.
- updateFrameX().  Handles sprite frame updates, changing frame on each update cycle to simulate movement (animation)
- collisionChecks(). Handles collisions checks, producing a data structure of collision events.

```javascript
update() {
    // Update the y position of the character based on gravity
    this.updateY();
    // Update animation frameX of the object
    this.updateFrameX(); 
    // Check for collisions, defined in GameObject which calls the collisionAction method
    this.collisionChecks();
}
```

### Player Collision Action (GameObject override)
Here is an example of managing collision actions using SRP.  A key consideration in this SRP design, is the use of the PlayerBase class object data and state machines to manage the flow of control through SRP. 

- handleCollisionStart().  Watches for and sets up collision events for the Player.
- handleCollisionEnd().  Tears down collisions no longer active for the Player.
- setActiveCollision().  Sets the finite state name for the active collision.
- handlePlayerReaction().  Updates the object data structure to represent the Player's reaction to the collision

```javascript
collisionAction() {
    this.handleCollisionStart();
    this.handleCollisionEnd();
    this.setActiveCollision();
    this.handlePlayerReaction();
}
```




