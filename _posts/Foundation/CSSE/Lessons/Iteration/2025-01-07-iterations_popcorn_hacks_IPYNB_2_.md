---
comments: True
layout: post
title: Iteration Popcorn Hacks
description: Iterations Popcorn Hacks
permalink: /csse/javascript/fundamentals/iteration/Popcorn_Hacks
categories: ['CSSE JavaScript Fundamentals']
author: Andrew Ge, Ishan Shrivastava, Pratheep Natarajan, and Ruhaan Bansal
---

# Popcorn Hacks on Iterations in JavaScript

##### Instructions:
##### Complete the exercises below in JavaScript.
##### You can run and test your code in a JavaScript environment.

### Exercise 1: Counting with a For Loop
##### Write a JavaScript for loop that prints all numbers from 1 to 10.

##### Example:
##### Output:
##### 1
##### 2
##### 3
##### ...
##### 9 
##### 10 

### Exercise 2: Sum of Numbers
##### Write a function in JavaScript to calculate the sum of all numbers from 1 to n using a loop.

##### Example:
##### Input: 5
##### Output: 15 (because 1 + 2 + 3 + 4 + 5 = 15)


### Exercise 3: Looping through Arrays
##### Write a JavaScript program to iterate through an array of names and print each name.


```javascript
%%javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
```


    <IPython.core.display.Javascript object>



```python
%%js 
for (let i = 1; i <= 5; i++) {
    let zeroes = "";
    for (let j = 1; j <= i; j++) {
        zeroes += "0";
    }
    console.log(zeroes);
}
```


    <IPython.core.display.Javascript object>



```python
%%js 
function isPrime(num) {
    if (num <= 1) return false;
    for (let i = 2; i <= Math.sqrt(num); i++) {
        if (num % i === 0) return false;
    }
    return true;
}

for (let i = 1; i <= 50; i++) {
    if (isPrime(i)) {
        console.log(i);
    }
}
```


    <IPython.core.display.Javascript object>



```python
%%js 
const names = ["Yuna", "Katherine", "Namira", "Yasna"];
for (let i = 0; i < names.length; i++) {
    console.log(names[i]);
}
```


    <IPython.core.display.Javascript object>



```python
%%js
const colors = ['red','blue','yellow','green','black'];

//color = i
for (let color of colors) { //checks each element in the list
    console.log(color); //prints each color
}
```


    <IPython.core.display.Javascript object>

