---
layout: post
title:  "Lluvia Random - Hello World p5-js"
date:   2018-04-29

categories: RandomCode

tags:
  - p5
  - WEB
  - Javascript
---


## Simple Lluvia Random en el navegador con p5js

> ### Ver el código en Acción [aqui.](https://forcesk.github.io/p5js-Repo/RandomRain/)

```js
var spot =
{
  x: 50,
  y: 50
}

var col =
{
  r: 255,
  g: 0,
  b: 0,
}
var black = 20;

function setup()
{
	createCanvas(windowWidth, windowHeight);
	background(black);
}

function draw()
{
	col.r = random(0,255);
	col.b = random(0,190);
	spot.x = random(0, width);
	spot.y = random(0, height);
		noStroke();

	fill(col.r,col.g,col.b,100);
	ellipse(spot.x,spot.y,24,24);

}

function mousePressed()
{
	black = black-10;
	background(black);
}

```
> [Link al Repositorio completo.](https://github.com/forcesk/p5js-Repo/tree/gh-pages/RandomRain)

### Links de interés
> [Link al video de Shiffman donde se explica el código](https://www.youtube.com/watch?v=nfmV2kuQKwA&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=10)
