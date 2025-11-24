



int numero = 0;
int digitos = 0;
int d1, d2, d3, d4;
int fama = 0, punto = 0;
int intentos = 0;
boolean terminado = false;
boolean mostrarResultado = false;

int cantJugadores = 0;
int turno = 1;

//VIRUS POR JUGADOR
int virus1 = int(random(1, 21));
int virus2 = int(random(1, 21));
int virus3 = int(random(1, 21));
int virus4 = int(random(1, 21));


//  ESPACIOS SERVIDORES
int espacio1 = 0;
int espacio2 = 0;
int espacio3 = 0;
int espacio4 = 0;
int espacio5 = 0;
int espacio6 = 0;

//PÉTALOS
int petalo1 = 0;
int petalo2 = 0;
int petalo3 = 0;
int petalo4 = 0;
int petalo5 = 0;
int petalo6 = 0;
int petalo7 = 0;
int petalo8 = 0;
int petalo9 = 0;

//  POSICIONES
float px1, px2, px3, px4, px5, px6, px7, px8, px9;
float py1, py2, py3, py4, py5, py6, py7, py8, py9;

//VECINOS
int v0_1 = 1, v0_2 = 8;
int v1_1 = 0, v1_2 = 2;
int v2_1 = 1, v2_2 = 3;
int v3_1 = 2, v3_2 = 4;
int v4_1 = 3, v4_2 = 5;
int v5_1 = 4, v5_2 = 6;
int v6_1 = 5, v6_2 = 7;
int v7_1 = 6, v7_2 = 8;
int v8_1 = 7, v8_2 = 0;
int vecino1, vecino2;



boolean lanzando = false;
int dado = 0;

int estado = 0;
int ganador = 0;

PImage fondo;

int turnopetalo = 1;
boolean juegoTerminado = false;

boolean esperandoSegundo = false;
int primerPetalo = -1;

//multirusa
int estadomulti = 0;
int multiplicando = 0;
int resultado = 0;
int multiplicador = 0;
int resultadoRusa = 0;
//taylor de los taylor
String estado2 = "angulo";

String textoEntrada = "";
float angulo = 0;
int n = 0;

float piCalculado;
float senoResultado;
float cosenoResultado;
//calve de numeritos
int num = 0;
boolean ingresoTerminado = false;
int clave = -1;

// SETUP
void setup() {
  fullScreen();
  textAlign(CENTER, CENTER);
  textSize(40);

  float cx = width/2;
  float cy = height/2;
  float r = height * 0.30;

  // Calcular posiciones  px[]
  {
  float ang;

  ang = TWO_PI * 0/9 - HALF_PI;
  px1 = cx + cos(ang)*r;
  py1 = cy + sin(ang)*r;
  ang = TWO_PI * 1/9 - HALF_PI;
  px2 = cx + cos(ang)*r;
  py2 = cy + sin(ang)*r;
  ang = TWO_PI * 2/9 - HALF_PI;
  px3 = cx + cos(ang)*r;
  py3 = cy + sin(ang)*r;
  ang = TWO_PI * 3/9 - HALF_PI;
  px4 = cx + cos(ang)*r;
  py4 = cy + sin(ang)*r;
  ang = TWO_PI * 4/9 - HALF_PI;
  px5 = cx + cos(ang)*r;
  py5 = cy + sin(ang)*r;
  ang = TWO_PI * 5/9 - HALF_PI;
  px6 = cx + cos(ang)*r;
  py6 = cy + sin(ang)*r;
  ang = TWO_PI * 6/9 - HALF_PI;
  px7 = cx + cos(ang)*r;
  py7 = cy + sin(ang)*r;
  ang = TWO_PI * 7/9 - HALF_PI;
  px8 = cx + cos(ang)*r;
  py8 = cy + sin(ang)*r;
  ang = TWO_PI * 8/9 - HALF_PI;
  px9 = cx + cos(ang)*r;
  py9 = cy + sin(ang)*r;
}
}



void draw() {
  background(0);

  if (estado == 0) menu();
  if (estado == 1) elegir();
  if (estado == 2) micelanea();
  if (estado == 3) pantallaSeleccion();
  regresar();
  if (estado == 4) pantallaJuego();
  if (estado == 5) {
    pantallaGanador();
    regresar();
  }
  if (estado == 6) {
    puntofama();
    regresar();
  }
  if (estado == 7) {
    margarita();
    regresar();
  }
  if (estado == 9) problemasmates();
  if (estado == 10 || estado == 11 || estado == 12) multirusa();
  regresar();
  if (estado==13) {
    taylor();
    regresar();
  }
  if (estado==14) {
    clave();
    regresar();
  }
  if (estado==15) {
    reglas();
    regresar();
  }
  if (estado==16) {
    reglas2();
  }
  if (estado==17) {
    reglas3();
  }
 if(estado==18){
   reglas4();
 }
}




// VIRUS Y SERVIDORES
int getVirus(int j) {
  if (j==1) return virus1;
  if (j==2) return virus2;
  if (j==3) return virus3;
  return virus4;
}

void setVirus(int j, int v) {
  if (j==1) {
    virus1=v;
  } else {
    if (j==2) {
      virus2=v;
    } else {
      if (j==3) {
        virus3=v;
      } else {
        virus4=v;
      }
    }
  }
}

int getEsp(int s) {
  if (s==1) return espacio1;
  if (s==2) return espacio2;
  if (s==3) return espacio3;
  if (s==4) return espacio4;
  if (s==5) return espacio5;
  return espacio6;
}

void setEsp(int s, int v) {
  if (s==1) {
    espacio1=v;
  } else {
    if (s==2) {
      espacio2=v;
    } else {
      if (s==3) {
        espacio3=v;
      } else {
        if (s==4) {
          espacio4=v;
        } else {
          if (s==5) {
            espacio5=v;
          } else {
            espacio6=v;
          }
        }
      }
    }
  }
}


//  PETALOS
int getPetalo(int i) {
  if (i==0) return petalo1;
  if (i==1) return petalo2;
  if (i==2) return petalo3;
  if (i==3) return petalo4;
  if (i==4) return petalo5;
  if (i==5) return petalo6;
  if (i==6) return petalo7;
  if (i==7) return petalo8;
  return petalo9;
}

void setPetalo(int i, int v) {
  if (i==0) {
    petalo1=v;
  } else {
    if (i==1) {
      petalo2=v;
    } else {
      if (i==2) {
        petalo3=v;
      } else {
        if (i==3) {
          petalo4=v;
        } else {
          if (i==4) {
            petalo5=v;
          } else {
            if (i==5) {
              petalo6=v;
            } else {
              if (i==6) {
                petalo7=v;
              } else {
                if (i==7) {
                  petalo8=v;
                } else {
                  petalo9=v;
                }
              }
            }
          }
        }
      }
    }
  }
}

float getPx(int i) {
  if (i==0) return px1;
  if (i==1) return px2;
  if (i==2) return px3;
  if (i==3) return px4;
  if (i==4) return px5;
  if (i==5) return px6;
  if (i==6) return px7;
  if (i==7) return px8;
  return px9;
}

float getPy(int i) {
  if (i==0) return py1;
  if (i==1) return py2;
  if (i==2) return py3;
  if (i==3) return py4;
  if (i==4) return py5;
  if (i==5) return py6;
  if (i==6) return py7;
  if (i==7) return py8;
  return py9;
}


// MENÚS
void menu() {
  background(255);
  fondo = loadImage("menurealidad.jpg");
  image(fondo, 0, 0, width, height);
}

void elegir() {
  fondo = loadImage("peca.jpg");
  image(fondo, 0, 0, width, height);
}

void micelanea() {
  background(#DFF218);
  fondo = loadImage("metro.jpg");
  image(fondo, 0, 0, width, height);
}

void pantallaSeleccion() {
  fill(255);
  text("Selecciona cantidad de jugadores", width/2, height/4);

  for (int i = 1; i <= 4; i++) {
    float x = width/5 * i;
    float y = height/2;
    rectMode(CENTER);
    fill(100);
    rect(x, y, 200, 100);
    fill(255);
    text(i, x, y);
  }
}

void regresar() {
  fill(#E5793A);
  text("back", width/1.1, height/1.1);
}

void problemasmates() {
  background(#DFF218);
  fondo = loadImage("mura.jpg");
  image(fondo, 0, 0, width, height);
}

void multirusa() {
  background(240);
  fill(0);
  textSize(22);

  // ESTADO 10 → escribir multiplicador
  if (estado == 10) {
    text("Ingrese el multiplicador (solo números):", 200, 80);
    text(multiplicador, 40, 130);
  }

  // ESTADO 11 → escribir multiplicando
  if (estado == 11) {
    text("Ingrese el multiplicando:", 200, 80);
    text(multiplicando, 200, 130);
  }

  // ESTADO 12 → mostrar tabla y resultado
  if (estado == 12) {

    text("Multiplicación rusa: " + multiplicador + " x " + multiplicando, 200, 80);

    int m1 = multiplicador;
    int m2 = multiplicando;
    int suma = 0;
    int y = 130;

    while (m1 > 0) {

      if (m1 % 2 != 0) {
        suma += m2;
        text(m1 + "  |  " + m2 + "  <-- se suma", 200, y);
      }
      m1 /= 2;
      m2 *= 2;
      y += 30;
    }

    resultadoRusa = suma;

    text("Resultado = " + resultadoRusa, 200, y + 40);
  }
}

void taylor() {
  background(20);
  fill(255);

  if (estado2.equals("angulo")) {
    text("Ingrese el ANGULO en grados:", 300, 150);
    text(textoEntrada, 200, 250);
  }

  if (estado2.equals("iteraciones")) {
    text("Ingrese NUMERO DE ITERACIONES:", 300, 150);
    text(textoEntrada, 50, 250);
  }

  if (estado2.equals("resultado")) {
    text("Ángulo (rad): " + nf(angulo, 1, 10), 300, 150);
    text("Iteraciones: " + n, 300, 210);

    fill(0, 255, 0);
    text("SENO(x) = " + nf(senoResultado, 1, 10), 300, 300);
    fill(100, 200, 255);
    text("COSENO(x) = " + nf(cosenoResultado, 1, 10), 300, 380);

    fill(255);
    text("Presione ENTER para reiniciar.", 300, 500);
  }
}

void clave() {
  background(30);

  fill(255);
  text("CLAVE DE UN NÚMERO", 300, 60);

  textSize(26);
  fill(200);

  text("Escribe un número (ENTER para continuar):", 300, 130);

  // Mostrar el número que el usuario va formando
  textSize(40);
  fill(0, 255, 200);
  text(num, 50, 200);

  if (ingresoTerminado) {
    fill(255);
    textSize(30);
    text("Tu número clave es: " + clave, 300, 200);

    textSize(22);
    fill(180);
    text("Presiona R para reiniciar", 300, 330);
  }
}

void reglas() {
  background(#DFF218);
  fondo = loadImage("reglas.jpg");
  image(fondo, 0, 0, width, height);
}

void reglas2() {
  background(#DFF218);
  fondo = loadImage("reglas2.jpg");
  image(fondo, 0, 0, width, height);
}

void reglas3() {
  background(#DFF218);
  fondo = loadImage("reglas3.jpg");
  image(fondo, 0, 0, width, height);
}

void reglas4() {
  background(#DFF218);
  fondo = loadImage("reglas4.jpg");
  image(fondo, 0, 0, width, height);
}
//  JUEGO VIRUS
void pantallaJuego() {
  fill(255);
  text("Turno del jugador " + turno, width/2, 60);
  text("Virus actuales: " + getVirus(turno), width/2, 120);

  mostrarServidores();

  fill(150);
  rectMode(CENTER);
  rect(width/2, height - 150, 250, 120);
  fill(0);
  text("Lanzar Dado", width/2, height - 150);

  if (dado != 0) {
    fill(255);
    textSize(80);
    text("DADO: " + dado, width/2, height/2);
    textSize(40);
  }
}

void lanzarDado() {
  if (cantJugadores <= 0) {
    println("Aviso: cantJugadores no seleccionado. Elige jugadores primero.");
    return;
  }
  if (estado == 5) return;
  dado = int(random(1, 7));

  if (turno < 1 || turno > cantJugadores) {
    turno = 1;
  }

  int v = getVirus(turno);
  v = v - 1;
  setVirus(turno, v);

  if (dado >= 1 && dado <= 5) {
    int e = getEsp(dado);
    e = e + 1;
    setEsp(dado, e);

    int limite = dado;

    if (e > limite) {
      setVirus(turno, getVirus(turno) + (limite + 1));

      setEsp(dado, 0);

      siguienteTurno();
      return;
    }
  }

  if (getVirus(turno) <= 0) {
    ganador = turno;
    estado = 5;
    reiniciarServidores();
    return;
  }
}

void siguienteTurno() {
  turno++;
  if (turno > cantJugadores) turno = 1;
  dado = 0;
}

void mostrarServidores() {
  rectMode(CORNER);
  textSize(28);

  for (int i = 1; i <= 5; i++) {
    int x = 80;
    int y = 200 + (i - 1) * 90;

    int limite = i;

    if (getEsp(i) > limite-1) fill(200, 50, 50);
    else fill(0, 100, 200);

    rect(x, y, 300, 70);

    fill(255);
    text("Servidor " + i, x + 60, y + 25);
    text("Virus: " + getEsp(i), x + 60, y + 55);
  }

  int x = 80;
  int y = 200 + 5 * 90;

  fill(0, 150, 100);
  rect(x, y, 300, 70);

  fill(255);
  text("Servidor 6", x + 60, y + 25);
  text("Virus: ilimitado", x + 160, y + 55);
}


// cuando ganas
void pantallaGanador() {
  fill(255, 200, 0);
  textSize(70);
  text("¡GANADOR JUGADOR " + ganador + "!", width/2, height/2);
}


// margarita juego de los juego del juego cv que siemrpe se daña erad hola rocio estoy enojado porque siemrpe me da errores erda lco hola chao mare 2 1 no se aaaaaaAaaaaaaAAAAAaaaa
void margarita() {
  background(30);

  fill(255);
  text("Juego de la Margarita", width/2 - 15, 60);

  for (int i=0; i<9; i++) {
    int val = getPetalo(i);

    if (val==0) fill(255, 255, 0);
    if (val==1) fill(0, 150, 255);
    if (val==2) fill(255, 80, 80);

    ellipse(getPx(i), getPy(i), 120, 120);

    fill(0);
    text(i+1, getPx(i)-10, getPy(i)+10);
  }

  if (!juegoTerminado) {
    fill(255);
    text("Turno del jugador: " + turnopetalo, 200, height - 100);

    if (esperandoSegundo) {
      text("Haz clic en un pétalo contiguo — o ENTER para terminar turno", 550, height - 50);
    } else {
      text("Haz click en un pétalo disponible", 200, height - 50);
    }
  } else {
    fill(0, 255, 0);
    int g;
    if (turnopetalo%2==0) {
      g = 1;
    } else {
      g =2 ;
    }
    text("GANADOR: Jugador " + g, width/2 - 150, height - 50);
  }
}

int detectarPetalo(int mx, int my) {
  for (int i=0; i<9; i++) {
    if (dist(mx, my, getPx(i), getPy(i)) < 60) return i;
  }
  return -1;
}

void cambiarTurno() {
  if (turnopetalo==1) turnopetalo=2;
  else turnopetalo=1;
}

void revisarFin() {
  int usados=0;
  for (int i=0; i<9; i++) {
    if (getPetalo(i)!=0) usados++;
  }
  if (usados==9) juegoTerminado=true;
}


// ---------------------- MOUSE -----------------------
void mousePressed() {

  // ---------- MARGARITA ----------
  if (estado==7) {

    int elegido = detectarPetalo(mouseX, mouseY);

    if (elegido != -1 && !juegoTerminado) {

      if (!esperandoSegundo) {

        if (getPetalo(elegido) != 0) return;

        setPetalo(elegido, turnopetalo);
        primerPetalo = elegido;
        obtenerVecinos(elegido);

        int v1 = vecino1;
        int v2 = vecino2;

        boolean hayVecinos = (getPetalo(v1) == 0 || getPetalo(v2) == 0);

        if (hayVecinos) {
          esperandoSegundo = true;
        } else {
          cambiarTurno();
          revisarFin();
        }
        return;
      }

      int v1 = vecino1;
      int v2 = vecino2;

      if ((elegido == v1 || elegido == v2) && getPetalo(elegido) == 0) {
        setPetalo(elegido, turnopetalo);
        esperandoSegundo = false;
        cambiarTurno();
        revisarFin();
      }
    }
  }

  if (estado==2) {
    if (mouseX > width/1.3 - 250 && mouseX < width/1.3 +250 &&
      mouseY > height/1.3 - 60 && mouseY < height/1.3 +60) {
      estado=17;
    }
  }
  if (estado==17) {
    if (mouseX > width/8.3 - 100 && mouseX < width/8.3 + 100 &&
      mouseY > height/1.044 - 250 && mouseY < height/1.044 + 250) {
      petalo1=petalo2=petalo3=petalo4=petalo5=petalo6=petalo7=petalo8=petalo9=0;
      esperandoSegundo = false;
      primerPetalo=-1;
      turnopetalo=1;
      juegoTerminado=false;

      estado=7;
    }
  }
  if (estado==17) {
    if ( mouseX > width/1.2 - 250 && mouseX < width/1.2 + 250 &&
      mouseY > height/1.044 - 25 && mouseY < height/1.044 + 25) {
      estado=2;
    }
  }

  if (estado==2||estado==3||estado==5||estado==6||estado==9||estado==10||estado==7||estado==11||estado==12||estado==13||estado==14||estado==15||estado==4) {
    if (mouseX > width/1.1 - 40 && mouseX < width/1.1 +40 &&
      mouseY > height/1.1 - 40 && mouseY < height/1.1 +40) {                          //boton de regresar
      estado = 1;
    }
  }
  if (estado==2) {
    if (mouseX > width/1.3 - 250 && mouseX < width/1.3 + 250 &&                    //boton de los virus
      mouseY > height/4 - 60 && mouseY < height/4 + 60) {
      estado=15;
    }
  }
  if (estado==9) {
    if (mouseX > width/1.2 - 250 && mouseX < width/1.2 +250 &&
      mouseY > height/2 - 60 && mouseY < height/2 +60) {
      estado=14;
    }
  }
  if (estado == 9) {
    if (mouseX > width/1.2 - 250 && mouseX < width/1.2 +250 &&
      mouseY > height/1.3 - 60 && mouseY < height/1.3 +60) {
      estado=13;
    }
  }
  if (estado==9) {
    if ( mouseX > width/1.2 - 250 && mouseX < width/1.2 + 250 &&
      mouseY > height/4 - 60 && mouseY < height/4 + 60) {                    //multiplicacion rusa
      estado = 10;
    }
  }


  if (estado==1) {
    if (mouseX > width/1.2 - 250 && mouseX < width/1.2 +250 &&
      mouseY > height/1.9 - 60 && mouseY < height/1.9 + 60) {
      estado=9;
    }
  }

  if (estado==0) {
    if (mouseX > width/2 - 100 && mouseX < width/2 +100 &&
      mouseY > height/1.7 - 100 && mouseY < height/1.7 +100) {
      estado=1;
    }
    return;
  }

  if (estado==1) {
    if (mouseX > width/1.2 - 250 && mouseX < width/1.2 + 250 &&
      mouseY > height/3.9 - 60 && mouseY < height/3.9 + 60) {
      estado = 2;
    }
    return;
  }

  if (estado==2) {
    if (mouseX > width/1.3 - 100 && mouseX < width/1.3 +100 &&
      mouseY > height/2- 100 && mouseY < height/2 + 100) {
      estado=16;
    }
  }
  if (estado==16) {
    if (mouseX > width/8.3 - 100 && mouseX < width/8.3 + 100 &&
      mouseY > height/1.044 - 250 && mouseY < height/1.044 + 250) {

      generarClave();
      terminado=false;
      mostrarResultado=false;
      intentos=0;
      numero=0;
      digitos=0;
      estado=6;
    }
  }
  if (estado==16) {
    if ( mouseX > width/1.2 - 250 && mouseX < width/1.2 + 250 &&
      mouseY > height/1.044 - 25 && mouseY < height/1.044 + 25) {
      estado = 2;
    }
  }

  if (estado==2) {
    if (mouseX > width/1.3 - 100 && mouseX < width/1.3 +100 &&
      mouseY > height/4 - 50 && mouseY < height/4 +50) {
      estado=15;
    }
    return;
  }
  if (estado==15) {
    if (mouseX > width/8.3 - 100 && mouseX < width/8.3 + 100 &&
      mouseY > height/1.044 - 250 && mouseY < height/1.044 + 250) {
      estado= 3;
    }
  }
  if (estado==15) {
    if ( mouseX > width/1.2 - 250 && mouseX < width/1.2 + 250 &&
      mouseY > height/1.044 - 25 && mouseY < height/1.044 + 25) {
      estado=2;
    }
  }

  if (estado==3) {
    for (int i=1; i<=4; i++) {
      float x = width/5 * i;
      float y = height/2;

      if (mouseX>x-100 && mouseX<x+100 &&
        mouseY>y-50 && mouseY<y+50) {
        cantJugadores=i;
        resetVirus();
        reiniciarServidores();
        turno = 1;
        dado = 0;

        estado = 4;
      }
    }
    return;
  }

  if (estado==4) {
    if (mouseY > height-210 && mouseY < height-90) {
      lanzarDado();
    }
  }
}


// ---------------------- PUNTO FAMA ----------------------
void puntofama() {
  background(20);

  fill(255);
  text("Ingresa una contraseña de 4 dígitos distintos:", 500, 120);

  fill(255);
  rect(80, 160, width-160, 80, 20);

  fill(0);
  text(numero, 120, 215);

  if (mostrarResultado) {
    fill(255);
    text("Famas:  "+fama, 80, 330);
    text("Puntos: "+punto, 80, 390);
    text("Intentos: "+intentos, 90, 450);
  }

  if (terminado) {
    fill(0, 200, 0);
    text("¡Felicidades! Adivinaste en "+intentos+" intentos", 80, 520);

    String nivel="";
    if (intentos<=3) {
      nivel="MUY INSEGURO";
    } else {
      if (intentos<=6) {
        nivel="DEBIL";
      } else {
        if (intentos<=10) {
          nivel="MODERADO";
        } else {
          if (intentos<=20) {
            nivel="SEGURO";
          } else {
            nivel="MUY SEGURO";
          }
        }
      }
    }

    fill(0, 200, 200);
    text("Nivel de seguridad: "+nivel, 80, 580);
  }
}


// TECLADO
void keyPressed() {

  // ---- Primero: si estamos en puntofama (estado 6) manejamos la entrada de ese número ----
  if (estado == 6) {
    if (terminado) return;

    if (key == BACKSPACE) {
      if (digitos>0) {
        numero/=10;
        digitos--;
      }
    }

    if (key>='0' && key<='9') {
      if (digitos < 4) {
        int valor = key - '0';
        numero = numero*10 + valor;
        digitos++;
      }
    }

    if (key == ENTER || key == RETURN) {
      if (digitos==4) verificar();
    }

    return; // si estamos en estado 6 ya procesamos y salimos
  }

  // ---- Margaríta: terminar segundo con ENTER ----
  if (estado==7 && esperandoSegundo) {
    if (key==ENTER || key==RETURN) {
      esperandoSegundo=false;
      cambiarTurno();
      revisarFin();
    }
  }

  // ---- MULTIPLICACIÓN RUSA: estados 10 (multiplicador), 11 (multiplicando), 12 (mostrar) ----
  if (estado == 10) {
    // Digitos para multiplicador
    if (key >= '0' && key <= '9') {
      multiplicador = multiplicador * 10 + (key - '0');
      return;
    }
    if (key == BACKSPACE) {
      multiplicador /= 10;
      return;
    }
    if (key == ENTER || key == RETURN) {
      if (multiplicador > 0) {
        estado = 11;
      }
      return;
    }
  } else {
    if (estado == 11) {
      // Digitos para multiplicando
      if (key >= '0' && key <= '9') {
        multiplicando = multiplicando * 10 + (key - '0');
        return;
      }
      if (key == BACKSPACE) {
        multiplicando /= 10;
        return;
      }
      if (key == ENTER || key == RETURN) {
        if (multiplicando > 0) {
          estado = 12;
        }
        return;
      }
    }
  }
  // ---- TAYLOR (estado 13): construir textoEntrada (número con decimal o signo), ENTER -> procesarEntrada() ----
  if (estado == 13) {
    if (key == ENTER || key == RETURN) {
      procesarEntrada();
      return;
    }

    // permitir dígitos
    if (key >= '0' && key <= '9') {
      textoEntrada += key;
      return;
    }

    // permitir un punto decimal (una sola vez)
    if (key == '.' && !textoEntrada.contains(".")) {
      textoEntrada += key;
      return;
    }

    // permitir signo negativo solo al principio
    if (key == '-' && textoEntrada.equals("0")) {
      textoEntrada += key;
      return;
    }

    return;
  }

  // ---- CLAVE (estado 14) manejo (ya estaba bien) ----
  if (estado==14) {
    if (ingresoTerminado) {
      if (key == 'r' || key == 'R') {
        num = 0;
        clave = -1;
        ingresoTerminado = false;
      }
      return;
    }

    // Permitir '-' solo si num es 0
    if (key == '-' && num == 0) {
      num = -1;
      return;
    }

    // Si presiona un dígito
    if (key >= '0' && key <= '9') {
      int valor = key - '0';

      if (num >= 0) {
        // Positivo: construir normalmente
        num = num * 10 + valor;
      } else {
        // Negativo: mantener el signo
        num = num * 10 - valor;
      }
      return;
    }

    // Borrar con BACKSPACE
    if (key == BACKSPACE) {
      if (num < 0) {
        num = num / 10;

        // evitar "-0"
        if (num == 0) num = 0;
      } else {
        num = num / 10;
      }
      return;
    }

    // Si presiona ENTER -> calcular clave
    if (key == ENTER || key == RETURN) {
      calcularClave();
      if (estado == 13 && (key == ENTER || key == RETURN)) {
        procesarEntrada();
      }
      return;
    }
  }

  // Si llegamos aquí, no era un input específico de campos, simplemente salir
}


// ----------------- VERIFICAR CONTRASEÑA --------------------
void generarClave() {
  d1 = int(random(10));
  do {
    d2 = int(random(10));
  } while (d2==d1);
  do {
    d3 = int(random(10));
  } while (d3==d1 || d3==d2);
  do {
    d4 = int(random(10));
  } while (d4==d1 || d4==d2 || d4==d3 || d4==0);
}

void verificar() {
  int n = numero;

  int i1 = n % 10;
  int i2 = (n / 10) % 10;
  int i3 = (n / 100) % 10;
  int i4 = (n / 1000);

  if (i1==i2 || i1==i3 || i1==i4 ||
    i2==i3 || i2==i4 || i3==i4) {

    numero=0;
    digitos=0;
    mostrarResultado=false;
    return;
  }

  fama=0;
  punto=0;

  if (i1==d1) fama++;
  if (i2==d2) fama++;
  if (i3==d3) fama++;
  if (i4==d4) fama++;

  if (i1==d2||i1==d3||i1==d4) punto++;
  if (i2==d1||i2==d3||i2==d4) punto++;
  if (i3==d1||i3==d2||i3==d4) punto++;
  if (i4==d1||i4==d2||i4==d3) punto++;

  intentos++;
  mostrarResultado=true;

  if (fama==4) terminado=true;

  numero=0;
  digitos=0;
}

void reiniciarServidores() {
  espacio1 = 0;
  espacio2 = 0;
  espacio3 = 0;
  espacio4 = 0;
  espacio5 = 0;
  espacio6 = 0;
}

void resetVirus() {
  virus1 = int(random(1, 21));
  virus2 = int(random(1, 21));
  virus3 = int(random(1, 21));
  virus4 = int(random(1, 21));
}

void obtenerVecinos(int i) {
  if (i == 0) {
    vecino1 = v0_1;
    vecino2 = v0_2;
  }
  if (i == 1) {
    vecino1 = v1_1;
    vecino2 = v1_2;
  }
  if (i == 2) {
    vecino1 = v2_1;
    vecino2 = v2_2;
  }
  if (i == 3) {
    vecino1 = v3_1;
    vecino2 = v3_2;
  }
  if (i == 4) {
    vecino1 = v4_1;
    vecino2 = v4_2;
  }
  if (i == 5) {
    vecino1 = v5_1;
    vecino2 = v5_2;
  }
  if (i == 6) {
    vecino1 = v6_1;
    vecino2 = v6_2;
  }
  if (i == 7) {
    vecino1 = v7_1;
    vecino2 = v7_2;
  }
  if (i == 8) {
    vecino1 = v8_1;
    vecino2 = v8_2;
  }
}

void calcularPi() {
  float pi = 0;
  float n2 = 2;

  for (int i = 0; i <= 100000000; i++) {
    pi += 4 / (n2 * (n2 + 1) * (n2 + 2)) - 4 / ((n2 + 2) * (n2 + 3) * (n2 + 4));
    n2 += 4;
  }

  pi += 3;
  piCalculado = pi;
}

void procesarEntrada() {

  if (estado2.equals("angulo")) {
    // Evitar entradas vacías o solo "-"
    if (textoEntrada.equals("") || textoEntrada.equals("-")) return;

    // DEBUG: imprimir valores antes de convertir
    println("DEBUG: textoEntrada='" + textoEntrada + "' piCalculado=" + piCalculado);

    // Comprobar si piCalculado es 0 y reemplazarlo por PI incorporado
    if (piCalculado == 0) {
      piCalculado = PI;
      println("DEBUG: piCalculado era 0, lo cambié a PI integrado = " + piCalculado);
    }

    // Convertir grados a radianes usando piCalculado
    angulo = float(textoEntrada);
    angulo = angulo * piCalculado / 180.0;

    // Limpiar entrada y pasar al siguiente estado
    textoEntrada = "";
    estado2 = "iteraciones";
    return;
  }

  if (estado2.equals("iteraciones")) {
    if (textoEntrada.equals("") || textoEntrada.equals("-")) return;

    n = int(float(textoEntrada));
    if (n < 1) return;

    calcularSeno();
    calcularCoseno();

    textoEntrada = "";
    estado2 = "resultado";
    return;
  }

  if (estado2.equals("resultado")) {
    textoEntrada = "";
    estado2 = "angulo";
  }
}



void calcularSeno() {
  float sum = 0;

  for (int i = 0; i <= n; i++) {
    float numerador = (i % 2 == 0) ? 1 : -1;

    float k = 2 * i + 1;

    float denominador = 1;
    for (float f = 1; f <= k; f++) denominador *= f;

    float x1 = 1;
    for (int p = 1; p <= k; p++) x1 *= angulo;

    float fraccion = numerador / denominador;
    sum += fraccion * x1;
  }

  senoResultado = sum;
}

void calcularCoseno() {
  float sum = 0;

  for (int i = 0; i <= n; i++) {
    float numerador = (i % 2 == 0) ? 1 : -1;

    float k = 2 * i;

    float denominador = 1;
    for (float f = 1; f <= k; f++) denominador *= f;

    float x1 = 1;
    for (int p = 1; p <= k; p++) x1 *= angulo;

    float fraccion = numerador / denominador;
    sum += fraccion * x1;
  }

  cosenoResultado = sum;
}

void calcularClave() {

  // Si es negativo → clave = -1
  if (num < 0) {
    clave = -1;
    ingresoTerminado = true;
    return;
  }

  int temp = num;
  int digito;
  int sum = 0;
  int mult = 2;

  while (temp > 0) {
    digito = temp % 10;
    sum = sum + digito * mult;
    mult = mult + 1;
    temp = temp / 10;
  }

  clave = sum % 10;
  ingresoTerminado = true;
}

float factorial(int x) {
  float f = 1;
  for (int i = 1; i <= x; i++) f *= i;
  return f;
}
