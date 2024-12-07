# Pr-ctica-ESP32-con-DHT11-y-Lcd

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
## Librerías

1. **DHT sensor library for ESPx**
2. **LiquidCrystal I2C**

## Conexión
![](https://github.com/Victor-Cabanas-99/Pr-ctica-ESP32-con-DHT11-y-Lcd/blob/main/3.PNG?raw=true)
