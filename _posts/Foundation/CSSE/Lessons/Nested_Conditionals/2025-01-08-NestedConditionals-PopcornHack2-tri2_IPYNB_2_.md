---
layout: post
title: Nested Conditionals, Popcorn Hack Two
description: Second popcorn hack for nested conditionals
type: issues
comments: True
---

### Popcorn Hack 2

This code uses boolean to check if a person has the unlimited amusement food card. If they do, then they are allowed to buy any food that they want for free. Add code for another type of food and take into account whether or not the food is in stock.


```python
%%html
<!-- HTML output div -->
<div id="message"></div>
<script>
    function runWhenDOMLoaded() {
        let foodCard = true;
        let money = 1;
        let foodChoice = "cotton candy";
        //You probably want to add some boolean variables here to check if the food is in stock or not... 
        //Make sure to add another food! Get creative!

        const messageElement = document.getElementById("message");

        function displayMessage(message) {
            console.log(message); // Log to console
            messageElement.textContent = message; // Display on the webpage
        }

        if (foodCard === true) {
            if (foodChoice === "popcorn") {//Checks the food choice
                    displayMessage("Yum! The popcorn is tasty!");
            } else if (foodChoice === "cotton candy") {
                    displayMessage("Yum! The cotton candy is tasty!");
            }//Use the previous code as examples to help make another food! 
            // Also, make sure to add more nested conditionals inside the if statements above to check if the food is in stock
        } else {
            if (foodChoice === "popcorn") {
                if (money >= 8) { // checks if you have enough money to buy
                    //Add another if statement to check if the food is in stock!
                    displayMessage("Yay! You can buy the popcorn!");
                } else {
                    displayMessage("Oh... you can't buy the popcorn.");
                }
            } else if (foodChoice === "cotton candy") {
                if (money >= 5) {
                    //Add another if statement to check if the food is in stock!
                    displayMessage("Yay! You can buy the cotton candy!");
                } else {
                    displayMessage("Oh... you can't buy the cotton candy.");
                }//Add the other food and make sure to check if it is in stock!
            }
        }
    }

    // Ensure the function runs only after the page loads
    if (document.readyState === "loading") {
        document.addEventListener("DOMContentLoaded", runWhenDOMLoaded);
    } else {
        runWhenDOMLoaded();
    }
</script>

```


<!-- HTML output div -->
<div id="message"></div>
<script>
    function runWhenDOMLoaded() {
        let foodCard = true;
        let money = 1;
        let foodChoice = "cotton candy";
        //You probably want to add some boolean variables here to check if the food is in stock or not... 
        //Make sure to add another food! Get creative!

        const messageElement = document.getElementById("message");

        function displayMessage(message) {
            console.log(message); // Log to console
            messageElement.textContent = message; // Display on the webpage
        }

        if (foodCard === true) {
            if (foodChoice === "popcorn") {//Checks the food choice
                    displayMessage("Yum! The popcorn is tasty!");
            } else if (foodChoice === "cotton candy") {
                    displayMessage("Yum! The cotton candy is tasty!");
            }//Use the previous code as examples to help make another food! 
            // Also, make sure to add more nested conditionals inside the if statements above to check if the food is in stock
        } else {
            if (foodChoice === "popcorn") {
                if (money >= 8) { // checks if you have enough money to buy
                    //Add another if statement to check if the food is in stock!
                    displayMessage("Yay! You can buy the popcorn!");
                } else {
                    displayMessage("Oh... you can't buy the popcorn.");
                }
            } else if (foodChoice === "cotton candy") {
                if (money >= 5) {
                    //Add another if statement to check if the food is in stock!
                    displayMessage("Yay! You can buy the cotton candy!");
                } else {
                    displayMessage("Oh... you can't buy the cotton candy.");
                }//Add the other food and make sure to check if it is in stock!
            }
        }
    }

    // Ensure the function runs only after the page loads
    if (document.readyState === "loading") {
        document.addEventListener("DOMContentLoaded", runWhenDOMLoaded);
    } else {
        runWhenDOMLoaded();
    }
</script>


