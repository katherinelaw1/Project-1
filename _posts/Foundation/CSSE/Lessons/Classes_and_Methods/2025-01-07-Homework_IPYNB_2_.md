---
layout: post
title: Homework
description: Homework for classes and methods lessons.
type: issues
comments: True
---

## Homework 

# JavaScript Classes and Methods - Interactive Homework
In this notebook, you will learn about classes and methods in JavaScript. After the lesson, complete the tasks by editing the code cells.

### What are Classes and Methods?
- **Class**: A blueprint for creating objects with properties and methods.
- **Method**: A function inside a class that defines an object's behavior.



## Example: Class for food

Below is an example of a JavaScript class for creating different foods. The class has:
1. A **constructor** to initialize properties (brand and model).
2. Two **methods** (`displayInfo` and `start`) to define behaviors.



```python
%%js
// Example: A Class for Cars
class Car {
  constructor(brand, model) {
    this.brand = brand; // Property
    this.model = model; // Property
  }

  displayInfo() {
    console.log(`This car is a ${this.brand} ${this.model}.`);
  }

  start() {
    console.log(`${this.brand} ${this.model} is starting...`);
  }
}

// Create an instance of the class
const myCar = new Car("Tesla", "Model S");
myCar.displayInfo();
myCar.start();

```


    <IPython.core.display.Javascript object>

