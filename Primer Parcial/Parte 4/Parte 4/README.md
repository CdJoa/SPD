## Primer Parcial Parte 4
![Tinkercad](./img/ArduinoTinkercad.jpg)


## Alumno
- Carnelos Duarte Joaquin Alejo


## Proyecto: Primer Parcial
![Tinkercad](./img/arduino-parcial-parte-3.png)


## Descripción
Ahora prendemos o apagamos el sistema segun el estado del slice, para girar el motor ahora usamos la fotorresistencia.

## Función principal
  Vamos directamente al loop el cual condiciona el acceso al sistema, tambien dejamos el mismo sistema a la vista

  Con un vistazo a estas dos funciones tenemos un panorama general del tinkercad.

 void loop() {
  
  slice = digitalRead(SLICE);//leemos el estado del slice
  
  if (slice == HIGH) {// en estado high accedemos al sistema
    sistema();
  } else{//caso contraro ("slice==low") apagamos todo
    digitalWrite(ledApagado, HIGH);
  	detenerMotor();
  	apagarDisplay();}
     }

void sistema() {
  
  digitalWrite(ledApagado, LOW);
	
  int lecturaSensor = analogRead(SENSOR_TEMP);
  temperatura = map(lecturaSensor, 20, 358, -40, 125);
  
  
  //ahora cambiamos entre numeros primos y numeros normales solo con la temperatura
   if (temperatura < 50 ) {
    modoPrimos();
  } else if (temperatura >= 50) {
    modoNormal();  
  }
  
  // ahora para acceder al giro del motor vamos a usar fotorresistencia
  int lecturaLuz = analogRead(FOTORESISTENCIA);
  if (lecturaLuz <1000)
  {
    girar();
  }
  else
  {detenerMotor();}

}

## :robot: Link al proyecto
- [proyecto](https://www.tinkercad.com/things/4mCJDIUYaWG?sharecode=MtPjHtsRDwiAordha0mapk6xsOL8XhZDuvLDA79TueE)
