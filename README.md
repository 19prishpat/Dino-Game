# Dino Jump Game

## Overview

**Dino Jump Game** is a simple platformer game created using the p5.js library. The player controls a dinosaur character that jumps over obstacles and collects points while avoiding collisions. The game features dynamic difficulty scaling and includes a high score tracking system.

## Features

- **Play State**: The game starts in this state. The dinosaur jumps to avoid obstacles, and the score increases as the game progresses.
- **End State**: The game transitions to this state when the dinosaur collides with an obstacle. The player can restart the game from this state.
- **High Score Tracking**: The game keeps track of the highest score using local storage.

## Prerequisites

- **p5.js Library**: Ensure you have the p5.js library included in your project for the game to run.

## How to Use

1. **Setup**: Include the p5.js library in your HTML file.
2. **Run the Game**: Open the HTML file in a web browser to start playing.

## Code

Here is the complete JavaScript code for the **Dino Jump Game**:

```javascript
var PLAY = 1;
var END = 0;
var gameState = PLAY;

var trex, trex_running, trex_collided;
var ground, invisibleGround, groundImage;

var cloudsGroup, cloudImage;
var obstaclesGroup, obstacle1, obstacle2, obstacle3, obstacle4, obstacle5, obstacle6;

var score = 0;

var gameOver, restart;

localStorage["HighestScore"] = 0;

function preload() {
  trex_running = loadAnimation("trex1.png", "trex3.png", "trex4.png");
  trex_collided = loadAnimation("trex_collided.png");

  groundImage = loadImage("ground2.png");

  cloudImage = loadImage("cloud.png");

  obstacle1 = loadImage("obstacle1.png");
  obstacle2 = loadImage("obstacle2.png");
  obstacle3 = loadImage("obstacle3.png");
  obstacle4 = loadImage("obstacle4.png");
  obstacle5 = loadImage("obstacle5.png");
  obstacle6 = loadImage("obstacle6.png");

  gameOverImg = loadImage("gameOver.png");
  restartImg = loadImage("restart.png");
}

function setup() {
  createCanvas(600, 200);

  trex = createSprite(50, 180, 20, 50);
  trex.addAnimation("running", trex_running);
  trex.addAnimation("collided", trex_collided);
  trex.scale = 0.5;

  ground = createSprite(200, 180, 400, 20);
  ground.addImage("ground", groundImage);
  ground.x = ground.width / 2;
  ground.velocityX = -(6 + 3 * score / 100);

  gameOver = createSprite(300, 100);
  gameOver.addImage(gameOverImg);

  restart = createSprite(300, 140);
  restart.addImage(restartImg);

  gameOver.scale = 0.5;
  restart.scale = 0
