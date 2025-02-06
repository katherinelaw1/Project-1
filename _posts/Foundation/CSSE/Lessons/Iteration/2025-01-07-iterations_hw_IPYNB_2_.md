---
comments: True
layout: post
title: Iteration Homework
description: Iterations HW
permalink: /csse/javascript/fundamentals/iteration/hw
categories: ['CSSE JavaScript Fundamentals']
author: Andrew Ge, Ishan Shrivastava, Pratheep Natarajan, and Ruhaan Bansal
---

### Exercise 1: Multiplication Table
##### Write a JavaScript program to print the multiplication table for a given number.

##### Example:
##### Input: 3
##### Output:
##### 3 x 1 = 3
##### 3 x 2 = 6
##### ...
##### 3 x 10 = 30


```python
%%js
function multiplicationTable(number) {
    for (let i = 1; i <= 10; i++) {
        console.log(`${number} x ${i} = ${number * i}`);
    }
}
multiplicationTable(3);
```


    <IPython.core.display.Javascript object>


### Exercise 2: Nested Loops
##### Write a JavaScript program using nested loops to generate the following pattern:

##### Output:
##### 0
##### 00
##### 000
##### 0000
##### 00000


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


### Challenge Exercise: Prime Numbers
##### Write a JavaScript program to print all prime numbers between 1 and 50.


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


# End of Homework
