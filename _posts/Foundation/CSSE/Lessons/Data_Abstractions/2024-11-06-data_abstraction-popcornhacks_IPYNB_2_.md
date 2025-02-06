---
comments: True
layout: post
title: Data Abstraction Hacks
description: An intro to data abstraction
permalink: /csse/javascript/fundamentals/data-abstraction-hacks
type: ccc
author: Veera Kalakota, Santhosh Karthik, Akhil Kulkarni
---

# Popcorn Hack #1
Create a child class of the class **Appliance**, and call it's name() function


```python
%%js 
    class Appliance {
        constructor(name) {
            this.name = name;
        }
        name() {
            return "I am a " + this.constructor.name + " and my model is " + this.name;
        }
    }
    // Below this name the class and cause it to inherit from the Appliance class
    class XXXX{
        constructor(name) {
            super(name);
    }
        
    }
```


    <IPython.core.display.Javascript object>


### Popcorn Hack #2
Create child classes of the product class with items, and add parameters depending on what it is. An example is provided of a bagel.


```python
%%js
    class Product{
        constructor(price,size,taxRate) {
            this.price = price;
            this.size = size;
            this.taxRate = taxRate;
        }   
        getPrice() {
            return this.price + this.taxRate * this.price;
        }
        product(){
            const className = this.constructor.name.toLowerCase();
            return "You are ordering a " + className + " with a price of " + this.getPrice() + " dollars, a size of " + this.size;
        }
    }
    class Bagel extends Product{
        constructor(price, size, taxRate, flavor) {
            super(price, size, taxRate);
            this.flavor = flavor;
        }
        getPrice(){
            return super.getPrice() * this.size;
        }
        product(){
            return super.product() + " and a flavor of " + this.flavor;
        }
    }
var sesameBagel = new Bagel(1.5, 2, 0.07, "sesame");
console.log(sesameBagel.product());
```


    <IPython.core.display.Javascript object>



```python

```
