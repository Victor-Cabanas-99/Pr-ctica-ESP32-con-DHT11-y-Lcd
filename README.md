# Pr-ctica-ESP32-con-DHT11-y-Lcd
## INTRODUCCION 
### Descripcion 
La Esp32 es una tarjeta de adquisición de datos, paralo cual en esta practica ocuparemos un sensor (DTH11) con una pantalla LCD216 para adquirir datos de temperatura y humedad del entorno cada segundo y mostrarlar los datos en la panatlla, se usara un simulador llamado WOKWI.
## MATERIAL A UTILIZAR
- [WOKWI](https://wokwi.com/projects/new/esp32)
- TARJET ESP32
- SENSOR DHT11
- LCD 16X2 2IC
  
## INSTRUCCIONES
### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:
```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("DIPLOMADO V");
  lcd.setCursor(2, 1);
  lcd.print("Mecatronica");
  delay(2000);

  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("Victor Cabanas");
  lcd.setCursor(2, 1);
  lcd.print("Ing. Mecanica");
  delay(2000);

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(2, 0);
  lcd.print("Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(2000);
}
```

2. Instalar la libreria de **DHT sensor library for ESPx** y **LiquidCrystal I2C** como se muestra en la siguente imagen.

![]()

3. Hacer la conexion de **DHT11** con la **ESP32** como se muestra en la siguente imagen.

![]()

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT11**

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.
![]()

## Librerías

1. **DHT sensor library for ESPx**
2. **LiquidCrystal I2C**


