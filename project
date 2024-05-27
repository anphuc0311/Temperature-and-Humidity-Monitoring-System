#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);
int measurePin = A0;
int ledPower =3;

int samplingTime = 0;
int deltaTime = 40;
int sleepTime = 9680;

float voMeasured = 0;
float calcVoltage = 0;
float dustDensity = 0;

void setup(){
  lcd.init();
  lcd.backlight();
  Serial.begin(9600);
  pinMode(ledPower,OUTPUT);
}

void loop(){
  digitalWrite(ledPower,LOW);
  delayMicroseconds(samplingTime);

  voMeasured = analogRead(measurePin);

  delayMicroseconds(deltaTime);
  digitalWrite(ledPower,HIGH);
  delayMicroseconds(sleepTime);

  calcVoltage = voMeasured*(5.0/1024.0);
  dustDensity = 170*calcVoltage -0.1;
  if(dustDensity != -0.10){
    Serial.println(dustDensity);
    lcd.setCursor(0,0);
    lcd.print("Nhom 26:");
    lcd.setCursor(0,1);
    lcd.print(dustDensity);
    lcd.print("(mg/m3)");
  }
  delay(1000);
}
