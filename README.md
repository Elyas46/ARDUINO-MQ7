#include <LiquidCrystal.h>
LiquidCrystal lcd(13,12,11,10,9,8);
int GAS_SENSOR=3;
int RED_LED=4;
int GREEN_LED=5;

void setup() {
pinMode(GAS_SENSOR, INPUT_PULLUP);
pinMode(RED_LED, OUTPUT);
pinMode(GREEN_LED, OUTPUT);
lcd.begin(20,4);
lcd.setCursor(0,0);
lcd.print("SISTEM PENDETEKSI");
lcd.setCursor(0,1);
lcd.print("ALCOHOL");
lcd.setCursor(0,2);
lcd.print("TELEKOMUNIKASI PNJ");
delay(1000);
}

void loop() {
int GAS_SENSOR_READ = digitalRead(GAS_SENSOR);
if (GAS_SENSOR_READ == HIGH)
  {
    lcd.clear();
    lcd.setCursor(0, 3);
    lcd.print("ALCOHOL DETECTED ");
    digitalWrite(RED_LED, LOW);
    digitalWrite(GREEN_LED, HIGH);
    delay(50);
  }
else 
  {
    lcd.clear();
    lcd.setCursor(0, 3);
    lcd.print("ALCOHOL NOT DETECTED ");
    digitalWrite(GREEN_LED, LOW);
    digitalWrite(RED_LED, HIGH);
    delay(50);
}
}
