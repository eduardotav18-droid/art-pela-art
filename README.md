let particulas = [];

const num = 2000;

const noiseScale = 0.10;

function setup() {
  createCanvas(700, 400);
  for(let i = 0; i < num; i ++) {
particulas.push(createVector(random(width),random(height))); 
  }
  stroke("rgb(0 255 179)")
  
}

function draw() {
  background(0,10);
  for(let i = 0; i < num; i ++) {
    let p = particulas[i];
    point(p.x, p.y);
    let n = noise(p.x * noiseScale, p.y * noiseScale);
    //TAU significa 2 vezes o valor de pi no pj5
    let a = TAU * n;
    p.x += cos(a);
    p.y += sin(a);
    if(!onScreen(p)) {
      p.x = random(width);
      p.y = random(height);
    }
  }
}

//função do clique mudar a origem da particula
function mouseReleased(){
  noiseSeed(millis());
}

//fará eles irem para um lugar só da tela
function onScreen(v) {
  return v.x >= 0 && v.x <= width && v.y >= 0 && v.y <= height; 
}


function keyPressed() {
  if (key === 's') {
    // Parâmetros: nome do arquivo, duração (segundos)
    saveGif('minhaAnimacao2', 5);
  }
}
