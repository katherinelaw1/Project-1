---
layout: post
title: Popcorn Hacks
description: Popcorn Hacks for lessons.
type: issues
comments: True
---

# JavaScript Classes and Methods - Interactive Popcorns 
In this notebook, you will learn about classes and methods in JavaScript. During the lesson, use these to enhance your understanding of clases and methods
### 
- **Objectivs**: Do something - Change Later
- **How**:


<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Popcorn Hack</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      overflow: auto; /* Enable scrolling */
      font-family: Arial, sans-serif;
      background: #ffffff; /* Popcorn vibe! */
    }

    #startButton {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      padding: 10px 20px;
      font-size: 18px;
      background: #ffffff;
      color: #000;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
    }

    #startButton:hover {
      background: #e8a400;
    }

    .kernel {
      position: absolute;
      width: 20px;
      height: 20px;
      background: #fff;
      border-radius: 50%;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
      animation: pop 1.5s ease-in-out forwards;
    }

    @keyframes pop {
      0% {
        transform: scale(0.5) translateY(0);
        opacity: 1;
      }
      50% {
        transform: scale(1.2) translateY(-150px);
      }
      100% {
        transform: scale(1) translateY(300px);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <button id="startButton">Start Popping!</button>

  <script>
    function createKernel() {
      // Create a new popcorn kernel
      const kernel = document.createElement("div");
      kernel.classList.add("kernel");

      // Randomize its position
      kernel.style.left = Math.random() * window.innerWidth + "px";
      kernel.style.top = Math.random() * (window.innerHeight / 2) + "px";

      // Add the kernel to the body
      document.body.appendChild(kernel);

      // Remove the kernel after animation ends
      setTimeout(() => kernel.remove(), 1500);
    }

    function startPopping() {
      let popCount = 0;
      const interval = setInterval(() => {
        createKernel(); // Create a popcorn kernel
        popCount++;
        if (popCount > 30) clearInterval(interval); // Stop after 30 kernels
      }, 200);
    }

    // Attach the event to the button
    document.getElementById("startButton").addEventListener("click", startPopping);
  </script>
</body>
</html>
