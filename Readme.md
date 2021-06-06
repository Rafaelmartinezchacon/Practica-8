
# PRÁCTICA 8: Bucle de comuniación UART2

## CÓDIGO

```
#include <Arduino.h>
#define RXD2 16
#define TXD2 17
void setup()
{
Serial.begin(115200);
Serial2.begin(9600, SERIAL_8N1, RXD2, TXD2);
Serial.println("Serial Txd is on pin: "+String(TX));
Serial.println("Serial Rxd is on pin: "+String(RX));
}
void loop()
{
while (Serial2.available())
{
Serial.print(char(Serial2.read()));
}
while (Serial.available())
{
Serial2.print(char(Serial.read()));
}
}
```
# Funcionamiento

Primero de todo definimos RXD2 y TXD2.

```
#include <Arduino.h>
#define RXD2 16
#define TXD2 17
```

En el `void setup()` incializamos una comunicación en serie con una velocidad de 115200 bauds. Utilizamos el **Serial port 2** y establecemos la velocidad a 9600 bauds.Seguidamente estableceremos el protocolo con `SERIAL_8N1` donde los ultimos dos parametros son los pines RX y TX. Por ultimo , imprimimos por pantalla los pines que estan en el serial Txd y serial Rxd.

```
void setup()
{
Serial.begin(115200);
Serial2.begin(9600, SERIAL_8N1, RXD2, TXD2);
Serial.println("Serial Txd is on pin: "+String(TX));
Serial.println("Serial Rxd is on pin: "+String(RX));
}
```
En el `void loop()` haremos un while que compruebe si el Serial2 esta disponible. En el caso de que este disponible, deberia hacer un print de lo que lee, que lo envié al otro puerto y lo que llegue a este puerto(Serial) que lo envie al monitor. En el segundo While haremos lo mismo que en el primero pero a diferencia del otro, este comprobara si el Serial esta disponible. 

```
void loop()
{
while (Serial2.available())
{
Serial.print(char(Serial2.read()));
}
while (Serial.available())
{
Serial2.print(char(Serial.read()));
}
}
```

# Salida por el terminal

La salida que veriamos seria esta:


Serial Txd is on pin: 1
Serial Rxd is on pin: 3
...

A partir de estos mensajes, puedes escribir los que tu desees.







