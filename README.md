# Zombie-Shooter-stage-1
var bg, bgImg;
var hammer, hammerImg;
var dirt1, mole2, dirtImg1, moleImg2;
var dirt3, mole4, dirtImg3, moleImg4;
var dirt5, mole6, dirtImg5, moleImg6;
var dirt7, mole8, dirtImg7, moleImg8;

var reappearDelay = 4000; // 4 seconds in milliseconds

function preload() {
  moleImg1 = loadImage("no_mole_dirt.png");
  moleImg2 = loadAnimation("Mole_dirt.png", "Mole_blink_dirt.png");
  hammerImg = loadImage("assets/hammer.png");
  bgImg = loadImage("assets/background.png");
  dirtImg3 = loadImage("no_mole_dirt.png");
  moleImg4 = loadAnimation("Mole_dirt.png", "Mole_blink_dirt.png");
  dirtImg5 = loadImage("no_mole_dirt.png");
  moleImg6 = loadAnimation("Mole_dirt.png", "Mole_blink_dirt.png");
  dirtImg7 = loadImage("no_mole_dirt.png");
  moleImg8 = loadAnimation("Mole_dirt.png", "Mole_blink_dirt.png");
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  bg = createSprite(500, 300, 1200, 600);
  bg.addImage(bgImg);
  bg.scale = 0.7;
  hammer = createSprite(600, 300, 50, 50);
  hammer.addImage(hammerImg);
  hammer.scale = 0.4;
  hammer.debug = true;
  hammer.setCollider("rectangle", -200, -30, 200, 210);

  dirt1 = createSprite(200, 300, 50, 50);
  dirt1.addImage(dirtImg1);
  dirt1.scale = 0.3;

  mole2 = createSprite(200, 270, 50, 50);
  mole2.addAnimation("coming_mole", moleImg2);
  mole2.scale = 0.3;
  mole2.visible = true;
  dirt1.visible = false;

  dirt3 = createSprite(400, 480, 50, 50);
  dirt3.addImage(dirtImg3);
  dirt3.scale = 0.3;

  mole4 = createSprite(400, 450, 50, 50);
  mole4.addAnimation("running_mole", moleImg4);
  mole4.scale = 0.3;
  mole4.visible = true;
  dirt3.visible = false;

  dirt5 = createSprite(500, 300, 50, 50);
  dirt5.addImage(dirtImg5);
  dirt5.scale = 0.3;

  mole6 = createSprite(500, 270, 50, 50);
  mole6.addAnimation("happy_mole", moleImg6);
  mole6.scale = 0.3;
  mole6.visible = true;
  dirt5.visible = false;

  dirt7 = createSprite(700, 200, 50, 50);
  dirt7.addImage(dirtImg7);
  dirt7.scale = 0.3;

  mole8 = createSprite(700, 170, 50, 50);
  mole8.addAnimation("birthday_mole", moleImg8);
  mole8.scale = 0.3;
  mole8.visible = true;
  dirt7.visible = false;

  hammer.depth = dirt1.depth;
  hammer.depth = hammer.depth + 1;

  hammer.depth = dirt3.depth;
  hammer.depth = hammer.depth + 1;

  hammer.depth = dirt5.depth;
  hammer.depth = hammer.depth + 1;

  hammer.depth = dirt7.depth;
  hammer.depth = hammer.depth + 1;
}

function draw() {
  background(0);
  hammer.x = mouseX;
  hammer.y = mouseY;
  if (hammer.isTouching(mole2)) {
    mole2.visible = false;
    dirt1.visible = true;
    moleReappear(mole2, dirt1);
  }
  if (hammer.isTouching(mole4)) {
    mole4.visible = false;
    dirt3.visible = true;
    moleReappear(mole4, dirt3);
  }
  if (hammer.isTouching(mole6)) {
    mole6.visible = false;
    dirt5.visible = true;
    moleReappear(mole6, dirt5);
  }
  if (hammer.isTouching(mole8)) {
    mole8.visible = false;
    dirt7.visible = true;
    moleReappear(mole8, dirt7);
  }

  drawSprites();
}

function moleReappear(mole, dirt) {
  setTimeout(function () {
    mole.visible = true;
    dirt.visible = false;
  }, reappearDelay);
}