---
layout: base
title: Snake
permalink: /snake/
---

<style>
    body{
    }
    .wrap{
        margin-left: auto;
        margin-right: auto;
    }

    canvas{
        display: none;
        border-style: solid;
        border-width: 10px;
        border-color: #FFFFFF;
    }
    canvas:focus{
        outline: none;
    }

    /* All screens style */
    #gameover p, #setting p, #menu p{
        font-size: 20px;
    }

    #gameover a, #setting a, #menu a{
        font-size: 30px;
        display: block;
    }

    #gameover a:hover, #setting a:hover, #menu a:hover{
        cursor: pointer;
    }

    #gameover a:hover::before, #setting a:hover::before, #menu a:hover::before{
        content: ">";
        margin-right: 10px;
    }

    #menu{
        display: block;
    }

    #gameover{
        display: none;
    }

    #setting{
        display: none;
    }

    #setting input{
        display:none;
    }

    #setting label{
        cursor: pointer;
    }

    #setting input:checked + label{
        background-color: #FFF;
        color: #000;
    }
</style>

<h2>Snake</h2>
<div class="container">
    <header class="pb-3 mb-4 border-bottom border-primary text-dark">
        <p class="fs-4">Score: <span id="score_value">0</span></p>
    </header>
    <div class="container bg-secondary" style="text-align:center;">
        <!-- Main Menu -->
        <div id="menu" class="py-4 text-light">
            <p>Welcome to Snake, press <span style="background-color: #42f5d4; color: #000000">space</span> to begin</p>
            <a id="new_game" class="link-alert">new game</a>
            <a id="setting_menu" class="link-alert">settings</a>
        </div>
        <!-- Game Over -->
        <div id="gameover" class="py-4 text-light">
            <p>Game Over, press <span style="background-color: #42f5d4; color: #000000">space</span> to try again</p>
            <a id="new_game1" class="link-alert">new game</a>
            <a id="setting_menu1" class="link-alert">settings</a>
        </div>
        <!-- Play Screen -->
        <canvas id="snake" class="wrap" width="640" height="640" tabindex="1"></canvas>
        <!-- Settings Screen -->
        <div id="setting" class="py-4 text-light">
            <p>Settings Screen, press <span style="background-color: #42f5d4; color: #000000">space</span> to go back to playing</p>
            <a id="new_game2" class="link-alert">new game</a>
            <br>
            <p>Speed:
                <input id="speed1" type="radio" name="speed" value="120" checked/>
                <label for="speed1">Slow</label>
                <input id="speed2" type="radio" name="speed" value="75"/>
                <label for="speed2">Normal</label>
                <input id="speed3" type="radio" name="speed" value="35"/>
                <label for="speed3">Fast</label>
            </p>
            <p>Wall:
                <input id="wallon" type="radio" name="wall" value="1" checked/>
                <label for="wallon">On</label>
                <input id="walloff" type="radio" name="wall" value="0"/>
                <label for="walloff">Off</label>
            </p>
        </div>
    </div>
</div>

<script>
(function(){
    /* Attributes of Game */
    /////////////////////////////////////////////////////////////
    // Canvas & Context
    const canvas = document.getElementById("snake");
    const ctx = canvas.getContext("2d");

    // Image Preload (sprites)
    const snakeHeadImage = new Image();
    const snakeBodyImage = new Image();
    const foodImage = new Image();

snakeHeadImage.src = '/Project-1/images/IMG_6720.jpeg'; // Your snake head image URL
    snakeBodyImage.src = 'https://image.petmd.com/files/inline-images/fluffy-dogs-bichon-frise.jpg?VersionId=uarSEQhS4ouBaCba1kOhiUzVr21LaXUq'; // Your snake body image URL
    foodImage.src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Cat_November_2010-1a.jpg/800px-Cat_November_2010-1a.jpg'; // Your food image URL
    

    // HTML Game IDs
    const SCREEN_SNAKE = 0;
    const screen_snake = document.getElementById("snake");
    const ele_score = document.getElementById("score_value");
    const speed_setting = document.getElementsByName("speed");
    const wall_setting = document.getElementsByName("wall");
    
    // HTML Screen IDs (div)
    const SCREEN_MENU = -1, SCREEN_GAME_OVER=1, SCREEN_SETTING=2;
    const screen_menu = document.getElementById("menu");
    const screen_game_over = document.getElementById("gameover");
    const screen_setting = document.getElementById("setting");

    // Game Control
    const BLOCK = 40; // size of block rendering
    let SCREEN = SCREEN_MENU;
    let snake;
    let snake_dir;
    let snake_next_dir;
    let snake_speed;
    let food = {x: 0, y: 0};
    let score;
    let wall;

    /* Display Control */
    /////////////////////////////////////////////////////////////
    let showScreen = function(screen_opt){
        SCREEN = screen_opt;
        switch(screen_opt){
            case SCREEN_SNAKE:
                screen_snake.style.display = "block";
                screen_menu.style.display = "none";
                screen_setting.style.display = "none";
                screen_game_over.style.display = "none";
                break;
            case SCREEN_GAME_OVER:
                screen_snake.style.display = "block";
                screen_menu.style.display = "none";
                screen_setting.style.display = "none";
                screen_game_over.style.display = "block";
                break;
            case SCREEN_SETTING:
                screen_snake.style.display = "none";
                screen_menu.style.display = "none";
                screen_setting.style.display = "block";
                screen_game_over.style.display = "none";
                break;
        }
    }

    /* Actions and Events  */
    /////////////////////////////////////////////////////////////
    window.onload = function() {
        // HTML Elements (Buttons)
        const button_new_game = document.getElementById("new_game");
        const button_new_game1 = document.getElementById("new_game1");
        const button_new_game2 = document.getElementById("new_game2");
        const button_setting_menu = document.getElementById("setting_menu");
        const button_setting_menu1 = document.getElementById("setting_menu1");

        // Event Listeners for Buttons
        button_new_game.onclick = function() { newGame(); };
        button_new_game1.onclick = function() { newGame(); };
        button_new_game2.onclick = function() { newGame(); };
        button_setting_menu.onclick = function() { showScreen(SCREEN_SETTING); };
        button_setting_menu1.onclick = function() { showScreen(SCREEN_SETTING); };

        // speed
        setSnakeSpeed(150);
        for (let i = 0; i < speed_setting.length; i++) {
            speed_setting[i].addEventListener("click", function() {
                for (let i = 0; i < speed_setting.length; i++) {
                    if (speed_setting[i].checked) {
                        setSnakeSpeed(speed_setting[i].value);
                    }
                }
            });
        }

        // wall setting
        setWall(1);
        for (let i = 0; i < wall_setting.length; i++) {
            wall_setting[i].addEventListener("click", function() {
                for (let i = 0; i < wall_setting.length; i++) {
                    if (wall_setting[i].checked) {
                        setWall(wall_setting[i].value);
                    }
                }
            });
        }

        // activate window events
        window.addEventListener("keydown", function(evt) {
            if (evt.code === "Space" && SCREEN !== SCREEN_SNAKE)
                newGame();
        }, true);
    };


    /* Snake is on the Go (Driver Function)  */
    /////////////////////////////////////////////////////////////
    let mainLoop = function(){
        let _x = snake[0].x;
        let _y = snake[0].y;
        snake_dir = snake_next_dir; // read async event key

        // Direction 0 - Up, 1 - Right, 2 - Down, 3 - Left
        switch(snake_dir){
            case 0: _y--; break;
            case 1: _x++; break;
            case 2: _y++; break;
            case 3: _x--; break;
        }
        snake.pop(); // tail is removed
        snake.unshift({x: _x, y: _y}); // head is new in new position/orientation

        // Wall Checker
        if(wall === 1){
            // Wall on, Game over test
            if (snake[0].x < 0 || snake[0].x === canvas.width / BLOCK || snake[0].y < 0 || snake[0].y === canvas.height / BLOCK){
                showScreen(SCREEN_GAME_OVER);
                return;
            }
        }else{
            // Wall Off, Circle around
            for(let i = 0, x = snake.length; i < x; i++){
                if(snake[i].x < 0){
                    snake[i].x = snake[i].x + (canvas.width / BLOCK);
                }
                if(snake[i].x === canvas.width / BLOCK){
                    snake[i].x = snake[i].x - (canvas.width / BLOCK);
                }
                if(snake[i].y < 0){
                    snake[i].y = snake[i].y + (canvas.height / BLOCK);
                }
                if(snake[i].y === canvas.height / BLOCK){
                    snake[i].y = snake[i].y - (canvas.height / BLOCK);
                }
            }
        }

        // Snake vs Snake checker
        for(let i = 1; i < snake.length; i++){
            if (snake[0].x === snake[i].x && snake[0].y === snake[i].y){
                showScreen(SCREEN_GAME_OVER);
                return;
            }
        }

        // Snake eats food checker
        if(checkBlock(snake[0].x, snake[0].y, food.x, food.y)){
            snake[snake.length] = {x: snake[0].x, y: snake[0].y};
            altScore(++score);
            addFood();
        }

        // Repaint canvas
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        
        // Paint snake (head and body)
        for(let i = 0; i < snake.length; i++){
            if(i === 0){
                ctx.drawImage(snakeHeadImage, snake[i].x * BLOCK, snake[i].y * BLOCK, BLOCK, BLOCK); // Head
            } else {
                ctx.drawImage(snakeBodyImage, snake[i].x * BLOCK, snake[i].y * BLOCK, BLOCK, BLOCK); // Body
            }
        }

        // Paint food
        ctx.drawImage(foodImage, food.x * BLOCK, food.y * BLOCK, BLOCK, BLOCK);

        // Recursive call after speed delay
        setTimeout(mainLoop, snake_speed);
    }

    /* New Game setup */
    /////////////////////////////////////////////////////////////
    let newGame = function(){
        showScreen(SCREEN_SNAKE);
        screen_snake.focus();

        score = 0;
        altScore(score);

        snake = [];
        snake.push({x: 0, y: 15});
        snake_next_dir = 1;

        addFood();

        canvas.onkeydown = function(evt) {
            changeDir(evt.keyCode);
        }
        mainLoop();
    }

    /* Key Inputs and Actions */
    /////////////////////////////////////////////////////////////
    let changeDir = function(key){
        switch(key) {
            case 37: // left arrow
                if (snake_dir !== 1) snake_next_dir = 3; // not right
                break;
            case 38: // up arrow
                if (snake_dir !== 2) snake_next_dir = 0; // not down
                break;
            case 39: // right arrow
                if (snake_dir !== 3) snake_next_dir = 1; // not left
                break;
            case 40: // down arrow
                if (snake_dir !== 0) snake_next_dir = 2; // not up
                break;
        }
    }

    /* Random food placement */
    /////////////////////////////////////////////////////////////
    let addFood = function(){
        food.x = Math.floor(Math.random() * (canvas.width / BLOCK));
        food.y = Math.floor(Math.random() * (canvas.height / BLOCK));

        for(let i = 0; i < snake.length; i++){
            if(checkBlock(food.x, food.y, snake[i].x, snake[i].y)){
                addFood();
            }
        }
    }

    /* Collision Detection */
    /////////////////////////////////////////////////////////////
    let checkBlock = function(x, y, _x, _y){
        return (x === _x && y === _y);
    }

    /* Update Score */
    /////////////////////////////////////////////////////////////
    let altScore = function(score_val){
        ele_score.innerHTML = String(score_val);
    }

    /////////////////////////////////////////////////////////////
    let setSnakeSpeed = function(speed_value){
        snake_speed = speed_value;
    }

    let setWall = function(wall_value){
        wall = wall_value;
        if(wall === 0){screen_snake.style.borderColor = "#e856cb";}
        if(wall === 1){screen_snake.style.borderColor = "#e856cb";}
    }
})();
</script>
