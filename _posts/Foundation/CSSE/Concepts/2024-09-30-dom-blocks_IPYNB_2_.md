---
comments: True
layout: post
title: DOM Updates
description: Learn about scaling and placing blocks.
permalink: /csse/javascript/fundamentals/dom/blocks/
categories: ['JavaScript Concepts']
courses: {'csse': {'week': 4}}
type: ccc
---

## Scale a Block

Scalling is an important Math operation that is used in Gaming.  This example is considering HD formats to construct a block.


```python
%%html 

<p>This example uses data types, operators, and functions to scale a block based on a user-defined width.</p>

<!-- Input definitions -->
<div>
  <label for="width">Enter Width (1280, 1920, 2560, 3840):</label>
  <input type="number" id="width" name="width" min="1280" max="3840" step="640" value="1280">
  <button onclick="submitScale()">Submit</button>
</div>

<!-- Document Object Model (DOM) output locations -->
<div id="output"></div>
<div id="error"></div>

<!-- Block display -->
<div id="block" style="width: 64px; height: 36px; background-color: red;"></div>

<script>

  // Function to validate and output the scale value
  function submitScale() {
    const BLOCK_SCALE_DIVISOR = 20;
    const ASPECT_RATIO = 9 / 16;
    let block = document.getElementById('block');
    let width = parseInt(document.getElementById('width').value);
    
    // Restrict sizes to common HD resolutions
    if (width === 1280 || width === 1920 || width === 2560 || width === 3840) {
      // Calculate height based on 16:9 aspect ratio
      let height = Math.round(width * ASPECT_RATIO);
      
      // Calculate block size as 1/20th of the scale dimensions
      let blockSize = Math.min(width, height) / BLOCK_SCALE_DIVISOR;
      
      // Set/clear error messages when the value is valid
      document.getElementById('error').innerHTML = "";
      // Output the scale value to the console
      document.getElementById('output').innerHTML = "Scale set to: " + width + " x " + height + " (Block size: " + blockSize + "px)";
      
      // Adjust the size of the block
      block.style.width = blockSize + "px";
      block.style.height = blockSize * ASPECT_RATIO + "px";
    } else {
      // Set/clear output messages when there is an error
      document.getElementById('output').innerHTML = "";
      // Output an error message to the console
      // Output an error message to the HTML page
      document.getElementById('error').innerHTML = "Invalid HD resolution: " + width;

      // Clear the block size
      block.style.width = "0px";
      block.style.height = "0px";
    }
    console.error("HD resolution:", block.style.width, "x", block.style.height);
  }
</script>
```



<p>This example uses data types, operators, and functions to scale a block based on a user-defined width.</p>

<!-- Input definitions -->
<div>
  <label for="width">Enter Width (1280, 1920, 2560, 3840):</label>
  <input type="number" id="width" name="width" min="1280" max="3840" step="640" value="1280">
  <button onclick="submitScale()">Submit</button>
</div>

<!-- Document Object Model (DOM) output locations -->
<div id="output"></div>
<div id="error"></div>

<!-- Block display -->
<div id="block" style="width: 64px; height: 36px; background-color: red;"></div>

<script>

  // Function to validate and output the scale value
  function submitScale() {
    const BLOCK_SCALE_DIVISOR = 20;
    const ASPECT_RATIO = 9 / 16;
    let block = document.getElementById('block');
    let width = parseInt(document.getElementById('width').value);

    // Restrict sizes to common HD resolutions
    if (width === 1280 || width === 1920 || width === 2560 || width === 3840) {
      // Calculate height based on 16:9 aspect ratio
      let height = Math.round(width * ASPECT_RATIO);

      // Calculate block size as 1/20th of the scale dimensions
      let blockSize = Math.min(width, height) / BLOCK_SCALE_DIVISOR;

      // Set/clear error messages when the value is valid
      document.getElementById('error').innerHTML = "";
      // Output the scale value to the console
      document.getElementById('output').innerHTML = "Scale set to: " + width + " x " + height + " (Block size: " + blockSize + "px)";

      // Adjust the size of the block
      block.style.width = blockSize + "px";
      block.style.height = blockSize * ASPECT_RATIO + "px";
    } else {
      // Set/clear output messages when there is an error
      document.getElementById('output').innerHTML = "";
      // Output an error message to the console
      // Output an error message to the HTML page
      document.getElementById('error').innerHTML = "Invalid HD resolution: " + width;

      // Clear the block size
      block.style.width = "0px";
      block.style.height = "0px";
    }
    console.error("HD resolution:", block.style.width, "x", block.style.height);
  }
</script>



### Popcorn Hack 1

Make a code cell that changes block into a square, versus HD resolution

## Placing a Block

Often in gaming you will want to position on element in relationship to another.


```python
%%html 

<p>This example uses data types, operators, and functions to scale a block based on a user-defined width.</p>

<!-- Input definitions -->
<div>
  <label for="widthCanvas">Enter Width (1280, 1920, 2560, 3840):</label>
  <input type="number" id="widthCanvas" name="widthCanvas" min="1280" max="3840" step="640" value="1280">
  <button onclick="submitScaleImg()">Submit</button>
</div>

<!-- Document Object Model (DOM) output locations -->
<div id="outputMsg"></div>
<div id="errorMsg"></div>

<!-- Canvas for background display -->
<canvas id="canvas"></canvas>

<script>
  // Function to validate and output the scale value
  function submitScaleImg() {
    const BLOCK_SCALE_DIVISOR = 20;
    const ASPECT_RATIO = 9 / 16;
    const SCALE_DOWN_FACTOR = 0.5;
    let canvas = document.getElementById('canvas');
    let c = canvas.getContext('2d');
    let width = parseInt(document.getElementById('widthCanvas').value);
    
    // Restrict sizes to common HD resolutions
    if (width === 1280 || width === 1920 || width === 2560 || width === 3840) {
      // Calculate height based on 16:9 aspect ratio
      let height = Math.round(width * ASPECT_RATIO);
      
      // Set the canvas dimensions
      canvas.width = width * SCALE_DOWN_FACTOR;
      canvas.height = height * SCALE_DOWN_FACTOR;
      
      // Calculate block size as 1/20th of the scale dimensions and scale down by 50%
      let blockSize = Math.min(width, height) / BLOCK_SCALE_DIVISOR;
      
      // Set/clear error messages when the value is valid
      document.getElementById('errorMsg').innerHTML = "";
      // Output the scale value to the console
      document.getElementById('outputMsg').innerHTML = "Scale set to: " + width + " x " + height + " (Block size: " + blockSize + "px)";
      
      // Load background image
      let imageBackground = new Image();
      imageBackground.src = 'https://samayass.github.io/samayaCSA/images/background.png';
      imageBackground.onload = function() {
        // Clear the canvas before drawing
        c.clearRect(0, 0, canvas.width, canvas.height);
        // Draw the background image on the canvas
        c.drawImage(imageBackground, 0, 0, canvas.width, canvas.height);
        
        // Draw the red block on the canvas
        c.fillStyle = 'red';
        c.fillRect((canvas.width - blockSize) / 2, (canvas.height - blockSize) / 2, blockSize, blockSize);
      };
    } else {
      // Set/clear output messages when there is an error
      document.getElementById('outputMsg').innerHTML = "";
      // Output an error message to the console
      console.error("Invalid HD resolution:", width);
      // Output an error message to the HTML page
      document.getElementById('errorMsg').innerHTML = "Invalid HD resolution: " + width;
      
      // Clear the canvas
      c.clearRect(0, 0, canvas.width, canvas.height);
    }
  }
</script>
```



<p>This example uses data types, operators, and functions to scale a block based on a user-defined width.</p>

<!-- Input definitions -->
<div>
  <label for="widthCanvas">Enter Width (1280, 1920, 2560, 3840):</label>
  <input type="number" id="widthCanvas" name="widthCanvas" min="1280" max="3840" step="640" value="1280">
  <button onclick="submitScaleImg()">Submit</button>
</div>

<!-- Document Object Model (DOM) output locations -->
<div id="outputMsg"></div>
<div id="errorMsg"></div>

<!-- Canvas for background display -->
<canvas id="canvas"></canvas>

<script>
  // Function to validate and output the scale value
  function submitScaleImg() {
    const BLOCK_SCALE_DIVISOR = 20;
    const ASPECT_RATIO = 9 / 16;
    const SCALE_DOWN_FACTOR = 0.5;
    let canvas = document.getElementById('canvas');
    let c = canvas.getContext('2d');
    let width = parseInt(document.getElementById('widthCanvas').value);

    // Restrict sizes to common HD resolutions
    if (width === 1280 || width === 1920 || width === 2560 || width === 3840) {
      // Calculate height based on 16:9 aspect ratio
      let height = Math.round(width * ASPECT_RATIO);

      // Set the canvas dimensions
      canvas.width = width * SCALE_DOWN_FACTOR;
      canvas.height = height * SCALE_DOWN_FACTOR;

      // Calculate block size as 1/20th of the scale dimensions and scale down by 50%
      let blockSize = Math.min(width, height) / BLOCK_SCALE_DIVISOR;

      // Set/clear error messages when the value is valid
      document.getElementById('errorMsg').innerHTML = "";
      // Output the scale value to the console
      document.getElementById('outputMsg').innerHTML = "Scale set to: " + width + " x " + height + " (Block size: " + blockSize + "px)";

      // Load background image
      let imageBackground = new Image();
      imageBackground.src = 'https://samayass.github.io/samayaCSA/images/background.png';
      imageBackground.onload = function() {
        // Clear the canvas before drawing
        c.clearRect(0, 0, canvas.width, canvas.height);
        // Draw the background image on the canvas
        c.drawImage(imageBackground, 0, 0, canvas.width, canvas.height);

        // Draw the red block on the canvas
        c.fillStyle = 'red';
        c.fillRect((canvas.width - blockSize) / 2, (canvas.height - blockSize) / 2, blockSize, blockSize);
      };
    } else {
      // Set/clear output messages when there is an error
      document.getElementById('outputMsg').innerHTML = "";
      // Output an error message to the console
      console.error("Invalid HD resolution:", width);
      // Output an error message to the HTML page
      document.getElementById('errorMsg').innerHTML = "Invalid HD resolution: " + width;

      // Clear the canvas
      c.clearRect(0, 0, canvas.width, canvas.height);
    }
  }
</script>



### Popcorn Hack 2

Try to place a square in every corner.

