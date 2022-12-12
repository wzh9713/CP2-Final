# CP2-Final
A PoseNet Game
// Copyright (c) 2019 ml5
//
// This software is released under the MIT License.
// https://opensource.org/licenses/MIT

/* ===
ml5 Example
PoseNet example using p5.js
=== */

let video;
let poseNet;
let poses = [];


//positions
var by1 = 0;
var bx1;
var by2 = 0;
var bx2;
var by3 = 0;
var bx3;

var type1;
var type2;
var type3;

var chance;

//speeds
var s = 1;
var s2 = 1;
var s3 = 1;

var gvt = 0.1;

//touch ground
var gg = 0;
var gg2 = 0;
var gg3 = 0;

var rt;
var rt2;
var rt3;

var img1;
var img2;
var img3;
var fish;
var stk;
var chk;
var ppr
var hny
var glc
var sm
var md
var lg

var stg = 0

var cnt = 0

//fish
var scrm1 = 0;
//beef
var scrm2 = 0;
//chkn
var scrm3 = 0;

var scrt1 = 0
var scrt2 = 0
var scrt3 = 0

var scrf1 = 0
var scrf2 = 0
var scrf3 = 0

var p = 0

var mkx
var mky

var mainmenu
var intro
var bttn
var intro1
var intro2
var intro3

var strt = 0

function score1() {
  if (type1 == 1) {
    scrm1 = scrm1 + 15;
  }
  if (type1 == 0) {
    scrm2 = scrm2 + 15;
  }
  if (type1 == 2) {
    scrm3 = scrm3 + 15;
  }
}

function score11() {
  if (type1 == 1) {
    scrt1 = scrt1 + 15;
  }
  if (type1 == 0) {
    scrt2 = scrt2 + 15;
  }
  if (type1 == 2) {
    scrt3 = scrt3 + 15;
  }
}

function score111() {
  if (type1 == 1) {
    scrf1 = scrf1 + 15;
  }
  if (type1 == 0) {
    scrf2 = scrf2 + 15;
  }
  if (type1 == 2) {
    scrf3 = scrf3 + 15;
  }
}

function score2() {
  if (type2 == 1) {
    scrm1 = scrm1 + 15;
  }
  if (type2 == 0) {
    scrm2 = scrm2 + 15;
  }
  if (type2 == 2) {
    scrm3 = scrm3 + 15;
  }
}

function score22() {
  if (type2 == 1) {
    scrt1 = scrt1 + 15;
  }
  if (type2 == 0) {
    scrt2 = scrt2 + 15;
  }
  if (type2 == 2) {
    scrt3 = scrt3 + 15;
  }
}

function score222() {
  if (type2 == 1) {
    scrf1 = scrf1 + 15;
  }
  if (type2 == 0) {
    scrf2 = scrf2 + 15;
  }
  if (type2 == 2) {
    scrf3 = scrf3 + 15;
  }
}

function score3() {
  if (type3 == 1) {
    scrm1 = scrm1 + 15;
  }
  if (type3 == 0) {
    scrm2 = scrm2 + 15;
  }
  if (type3 == 2) {
    scrm3 = scrm3 + 15;
  }
}

function score33() {
  if (type3 == 1) {
    scrt1 = scrt1 + 15;
  }
  if (type3 == 0) {
    scrt2 = scrt2 + 15;
  }
  if (type3 == 2) {
    scrt3 = scrt3 + 15;
  }
}

function score333() {
  if (type3 == 1) {
    scrf1 = scrf1 + 15;
  }
  if (type3 == 0) {
    scrf2 = scrf2 + 15;
  }
  if (type3 == 2) {
    scrf3 = scrf3 + 15;
  }
}


function puse(){
  if (scrm1 + scrm2 + scrm3 >= 195 && stg == 0){
    p = 1 
  }
  if (scrt1 + scrt2 + scrt3 >= 195 && stg == 1){
    p = 1
  }
  if (scrf1 + scrf2 + scrf3 >= 195 && stg == 2){
    p = 1
  }
}

function preload() {
  fish = loadImage("fish.png");
  stk = loadImage("steak.png");
  chk = loadImage("chiken.png");
  ppr = loadImage("peper.png")
  glc = loadImage("garlic.png")
  hny = loadImage("honey.png")
  sm = loadImage("s.png")
  md = loadImage("m.png")
  lg = loadImage("l.png")
  mainmenu = loadImage("FC.jpeg")
  intro = loadImage("SFYB.jpeg")
  bttn = loadImage("strt.png")
  intro3 = loadImage("intro3.png")
  intro2 = loadImage("intro2.png")
  intro1 = loadImage("intro1.png")
}


function setup() {
  createCanvas(640, 480);
  video = createCapture(VIDEO);
  video.size(width, height);
  bx1 = random(20, 620);
  bx2 = random(20, 620);
  bx3 = random(20, 620);
  type1 = Math.floor(Math.random() * 3);
  type2 = Math.floor(Math.random() * 3);
  type3 = Math.floor(Math.random() * 3);
  
  image(mainmenu, 0, 0, 640, 480)
  
  image(bttn, 265, 370, 110, 50)
  
  // Create a new poseNet method with a single detection
  poseNet = ml5.poseNet(video, modelReady);
  // This sets up an event that fills the global variable "poses"
  // with an array every time new poses are detected
  poseNet.on('pose', function(results) {
    poses = results;
  });
  // Hide the video element, and just show the canvas
  video.hide();
}

function modelReady() {
  select('#status').html('Model Loaded');
}

function mouseClicked(){
  if (strt < 2 && dist(mouseX, mouseY, 320, 395) <= 90){
    strt ++
  }
}

function draw() {
  let d3 = dist(mkx, mky, bx3 + 25, by3 - 25);
  let d2 = dist(mkx, mky, bx2 + 25, by2 - 25);
  let d1 = dist(mkx, mky, bx1 + 25, by1 - 25);

if (strt == 1){
  image(intro, 0, 0, 640, 480)
  image(bttn, 265, 370, 110, 50)
}
  
  if(strt == 2 && cnt <= 600){
    image(intro1, 0, 0, 640, 480)
    cnt ++
  }
  if(strt == 2 && cnt > 600){
    strt = 3
    cnt = 0
  }
  
  if (strt == 3){
  if (poses.length > 0 && poses[0].pose.nose.y > 0 && poses[0].pose.nose.y < height && poses[0].pose.nose.x > 0 && poses[0].pose.nose.x < width && poses[0].pose.score >= 0.2){
    mkx = poses[0].pose.nose.x
    mky = poses[0].pose.nose.y
    
  }
  

  image(video, 0, 0, width, height);

  
    puse();

  if (p == 1) {
    chance = 7;
    gg = 0;
    gg1 = 0;
    gg2 = 0;
  } else {
    chance = random(0, 1000);
  }

  if (p == 1 && stg <= 2) {
    cnt++;
if (stg == 0){
  image(intro2, 0, 0, 640, 480)
}  
    if (stg == 1){
  image(intro3, 0, 0, 640, 480)
}  
}

  if (cnt >= 600 && stg <= 2) {
    p = 0;
    stg++;
    cnt = 0;
  }

  //bars
  stroke(60);
  fill(200);
  rect(550, 220, 10, 195);
  rect(570, 220, 10, 195);
  rect(590, 220, 10, 195);

  noStroke();
  fill(202, 165, 127);
  rect(552, 415, 6, -scrm3);
  fill(102, 124, 150);
  rect(552, 415 - scrm3, 6, -scrm2);
  fill(161, 82, 80);
  rect(552, 415 - scrm3 - scrm2, 6, -scrm1);

  fill(181, 123, 31);
  rect(572, 415, 6, -scrt3);
  fill(239, 238, 236);
  rect(572, 415 - scrt3, 6, -scrt2);
  fill(185, 27, 25);
  rect(572, 415 - scrt3 - scrt2, 6, -scrt1);

  fill(83, 95, 197);
  rect(592, 415, 6, -scrf3);
  fill(255, 173, 65);
  rect(592, 415 - scrf3, 6, -scrf2);
  fill(246, 75, 5);
  rect(592, 415 - scrf3 - scrf2, 6, -scrf1);

  fill(300);
  //IMAGE3==========================================================

  if (chance >= 980 && gg3 == 0) {
    gg3 = 1;
  }

  //stage1
  if (stg == 0) {
    if (type3 == 0) {
      img3 = fish;
    }
    if (type3 == 1) {
      img3 = stk;
    }
    if (type3 == 2) {
      img3 = chk;
    }
    if (d3 <= 30 && gg3 == 1) {
      score3();
      bx3 = random(20, 620);
      type3 = Math.floor(Math.random() * 3);
      by3 = 0;
      s3 = 1;
      gg3 = 0;
    }
  }

  //stage2

  if (stg == 1) {
    if (type3 == 0) {
      img3 = glc;
    }
    if (type3 == 1) {
      img3 = ppr;
    }
    if (type3 == 2) {
      img3 = hny;
    }
    if (d3 <= 30 && gg3 == 1) {
      score33();
      bx3 = random(20, 620);
      type3 = Math.floor(Math.random() * 3);
      by3 = 0;
      s3 = 1;
      gg3 = 0;
    }
  }

  //stage3

  if (stg == 2) {
    if (type3 == 0) {
      img3 = md;
    }
    if (type3 == 1) {
      img3 = lg;
    }
    if (type3 == 2) {
      img3 = sm;
    }
    if (d3 <= 30 && gg3 == 1) {
      score333();
      bx3 = random(20, 620);
      type3 = Math.floor(Math.random() * 3);
      by3 = 0;
      s3 = 1;
      gg3 = 0;
    }
  }

  image(img3, bx3, by3 - 50, 50, 50);
  if (gg3 >= 1) {
    if (gg3 == 2) {
      s3 = s3 + gvt;
      by3 = by3 + s3;
      s3 *= -1;
    } else {
      s3 = s3 + gvt;
      by3 = by3 + s3;
    }

    if (by3 >= height && gg3 == 1) {
      gg3 = 2;
      s3 = random(2, 5);
    }
    if (gg3 == 2) {
      s3 *= -1;
    }

    if (by3 >= 2 * height && gg3 == 2) {
      bx3 = random(20, 620);
      type3 = Math.floor(Math.random() * 3);
      by3 = 0;
      s3 = 1;
      gg3 = 0;
    }
  }
  //================================================================

  //IMAGE2==========================================================

  if (chance <= 2 && gg2 == 0) {
    gg2 = 1;
  }

  //stage1
  if (stg == 0) {
    if (type2 == 0) {
      img2 = fish;
    }
    if (type2 == 1) {
      img2 = stk;
    }
    if (type2 == 2) {
      img2 = chk;
    }

    if (d2 <= 30 && gg2 == 1) {
      score2();
      bx2 = random(20, 620);
      type2 = Math.floor(Math.random() * 3);
      by2 = 0;
      s2 = 1;
      gg2 = 0;
    }
  }

  //stage2

  if (stg == 1) {
    if (type2 == 0) {
      img2 = glc;
    }
    if (type2 == 1) {
      img2 = ppr;
    }
    if (type2 == 2) {
      img2 = hny;
    }

    if (d2 <= 30 && gg2 == 1) {
      score22();
      bx2 = random(20, 620);
      type2 = Math.floor(Math.random() * 3);
      by2 = 0;
      s2 = 1;
      gg2 = 0;
    }
  }

  //stage3

  if (stg == 2) {
    if (type2 == 0) {
      img2 = md;
    }
    if (type2 == 1) {
      img2 = lg;
    }
    if (type2 == 2) {
      img2 = sm;
    }

    if (d2 <= 30 && gg2 == 1) {
      score222();
      bx2 = random(20, 620);
      type2 = Math.floor(Math.random() * 3);
      by2 = 0;
      s2 = 1;
      gg2 = 0;
    }
  }

  image(img2, bx2, by2 - 50, 50, 50);

  if (gg2 >= 1) {
    if (gg2 == 2) {
      s2 = s2 + gvt;
      by2 = by2 + s2;
      s2 *= -1;
    } else {
      s2 = s2 + gvt;
      by2 = by2 + s2;
    }

    if (by2 >= height && gg2 == 1) {
      gg2 = 2;
      s2 = random(2, 5);
    }
    if (gg2 == 2) {
      s2 *= -1;
    }

    if (by2 >= 2 * height && gg2 == 2) {
      bx2 = random(20, 620);
      type2 = Math.floor(Math.random() * 3);
      by2 = 0;
      s2 = 1;
      gg2 = 0;
    }
  }
  //================================================================

  //IMAGE1==========================================================
  if (chance <= 51 && chance >= 40 && gg == 0) {
    gg = 1;
  }
  //stages diff!!
  if (stg == 0) {
    if (type1 == 0) {
      img1 = fish;
    }
    if (type1 == 1) {
      img1 = stk;
    }
    if (type1 == 2) {
      img1 = chk;
    }
    if (d1 <= 30 && gg == 1) {
      score1();
      bx1 = random(20, 620);
      type1 = Math.floor(Math.random() * 3);
      by1 = 0;
      s = 1;
      gg = 0;
    }
  }

  //stage2

  if (stg == 1) {
    if (type1 == 0) {
      img1 = glc;
    }
    if (type1 == 1) {
      img1 = ppr;
    }
    if (type1 == 2) {
      img1 = hny;
    }
    if (d1 <= 30 && gg == 1) {
      score11();
      bx1 = random(20, 620);
      type1 = Math.floor(Math.random() * 3);
      by1 = 0;
      s = 1;
      gg = 0;
    }
  }
  //stage3

  if (stg == 2) {
    if (type1 == 0) {
      img1 = md;
    }
    if (type1 == 1) {
      img1 = lg;
    }
    if (type1 == 2) {
      img1 = sm;
    }
    if (d1 <= 30 && gg == 1) {
      score111();
      bx1 = random(20, 620);
      type1 = Math.floor(Math.random() * 3);
      by1 = 0;
      s = 1;
      gg = 0;
    }
  }

  image(img1, bx1, by1 - 50, 50, 50);

  if (gg >= 1) {
    if (gg == 2) {
      s = s + gvt;
      by1 = by1 + s;
      s *= -1;
    } else {
      s = s + gvt;
      by1 = by1 + s;
    }

    if (by1 >= height && gg == 1) {
      gg = 2;
      s = random(2, 5);
    }
    if (gg == 2) {
      s *= -1;
    }

    if (by1 >= 2 * height && gg == 2) {
      bx1 = random(20, 620);
      type1 = Math.floor(Math.random() * 3);
      by1 = 0;
      s = 1;
      gg = 0;
    }
  }

  //reset
  if (p == 1) {
    by1 = -30;
    by2 = -30;
    by3 = -30;
  }
}
  

  
  
  
  
  
  
  
  
  
  
  
  
  //  if (poses.length > 0 && poses[0].pose.nose.y > 0 && poses[0].pose.nose.y < height && poses[0].pose.nose.x > 0 && poses[0].pose.nose.x < width && poses[0].pose.score >= 0.2) {
//    if (poses[0].pose.nose.x > width/2){
//      background(255);
//      textSize(40)
//      text('STOP LOOKING AT ME!!!', 80, 250)
//      fill(0)
//    }
//    if (poses[0].pose.nose.x < width/2 && poses[0].pose.nose.x > 0){
//      background(0);
//      textSize(40)
//      text('STOP LOOKING AT ME!!!', 80, 250)
//      fill(255)
//    }
    
   
//  }
}
