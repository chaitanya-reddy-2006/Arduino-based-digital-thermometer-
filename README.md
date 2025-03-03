# Arduino-based-digital-thermometer-
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

#define LM35_PIN A0  // LM35 output connected to A0

LiquidCrystal_I2C lcd(0x27, 16, 2);  // I2C address 0x27 (change if needed)

void setup() {
    lcd.begin(16, 2);
    lcd.backlight();
    lcd.print("Digital Thermo");
    delay(2000);
    lcd.clear();
}

void loop() {
    int sensorValue = analogRead(LM35_PIN);
    float temperature = sensorValue * 0.488;  // Convert to Celsius

    lcd.setCursor(0, 0);
    lcd.print("Temp: ");
    lcd.print(temperature);
    lcd.print(" C");

    delay(1000);
}
