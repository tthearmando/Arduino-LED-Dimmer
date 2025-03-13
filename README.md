# Arduino-LED-Dimmer

![Imagen del proyecto](ruta/a/tu/imagen.jpg) 

## Descripción
Este proyecto muestra cómo controlar la intensidad de un LED utilizando un potenciómetro y un Arduino Uno. Al girar el potenciómetro, el brillo del LED cambia de manera suave gracias a la modulación por ancho de pulso (PWM). Es un proyecto ideal para principiantes que quieran aprender sobre entradas analógicas, salidas PWM y programación básica en Arduino.

Grabé un video para mis redes sociales donde explico el montaje y funcionamiento. ¡Puedes verlo aquí!  
📹 [Enlace al video](https://www.tiktok.com/@tuusuario/video/xxxxxxxxx) <!-- Cambia por el enlace real de tu video -->

## Materiales necesarios
- Arduino Uno (o compatible)
- Potenciómetro (10kΩ recomendado)
- LED
- Protoboard
- Cables jumper
- Computadora con el IDE de Arduino instalado

## Conexiones
1. **Potenciómetro**:
   - Un extremo a 5V.
   - El otro extremo a GND.
   - El pin central (salida) a la entrada analógica A0 del Arduino.
2. **LED**:
   - Ánodo (patita larga) a un pin PWM (por ejemplo, pin 9) del Arduino.
   - Cátodo (patita corta) a GND.

Puedes ver el esquema de conexión en la siguiente imagen:  


<img src="https://raw.githubusercontent.com/tthearmando/Arduino-LED-Dimmer/main/Esquematico-led-dimmer.jpg" alt="Esquema del circuito" width="730"/>

## Código
El código lee el valor del potenciómetro (0-1023) y lo mapea a un rango de 0-255 para controlar el brillo del LED mediante PWM. Aquí está el código:

```cpp
int potPin = A1;    // Pin donde está conectado el potenciómetro
int ledPin = 9;     // Pin PWM donde está conectado el LED
int potValue = 0;   // Variable para almacenar el valor del potenciómetro
int brightness = 0; // Variable para el brillo del LED

void setup() {
  pinMode(ledPin, OUTPUT); // Configura el pin del LED como salida
}

void loop() {
  potValue = analogRead(potPin);              // Lee el valor del potenciómetro (0-1023)
  brightness = map(potValue, 0, 1023, 0, 255); // Mapea el valor a 0-255 para PWM
  analogWrite(ledPin, brightness);            // Ajusta el brillo del LED
  delay(10);                                  // Pequeña pausa para estabilidad
}
