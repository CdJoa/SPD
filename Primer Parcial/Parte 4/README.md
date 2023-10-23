## Primer Parcial Parte 4
![Tinkercad](./img/ArduinoTinkercad.jpg)


## Alumno
- Carnelos Duarte Joaquin Alejo


## Proyecto: Primer Parcial
![Tinkercad](./img/arduino-parcial-parte-4.png)


## Descripción
Ahora prendemos o apagamos el sistema segun el estado del slice, para girar el motor ahora usamos la fotorresistencia.

## Función principal
  Vamos directamente al loop el cual condiciona el acceso al sistema, tambien dejamos el mismo sistema a la vista

  Con un vistazo a estas dos funciones tenemos un panorama general del tinkercad.

  void loop() {
    int lecturaLuz = analogRead(FOTORESISTENCIA);
    if (lecturaLuz <1000) {
    // Serial.print("Luz: ");
    // Serial.println(lecturaLuz); para averiguar el limite de mi fotoresistencia use un print
      sistema();
    }
    else{
      digitalWrite(ledApagado, HIGH);
      detenerMotor();
      apagarDisplay();}
  }

  void sistema() {
    
    digitalWrite(ledApagado, LOW);
    
    int lecturaSensor = analogRead(SENSOR_TEMP);
    temperatura = map(lecturaSensor, 20, 358, -40, 125);
    
    slice = digitalRead(SLICE);

    girar();
    // El cambio de modos entre normales y primos solo se da si cambio la temperatura y apreto el boton, sino el contador seguira en el mismo modo
    //el sistema no prende a menos de que si o si se cumplan las condiciones de temperatura y slice
    if (temperatura < 50 && slice == HIGH) {
      modoPrimos();
    } else if (temperatura >= 50 && slice == LOW) {
      modoNormal();  
    }

  }

## :robot: Link al proyecto
- [proyecto](https://www.tinkercad.com/things/4mCJDIUYaWG?sharecode=MtPjHtsRDwiAordha0mapk6xsOL8XhZDuvLDA79TueE)
