# project-akhir
//AKSES KOMPUTER MENGGUNAKAN RFID

#include <SPI.h>
#include <RFID.h>
#define SS_PIN 10
#define RST_PIN 9
#include <Wire.h>
#include <LCD.h>
#include <LiquidCrystal_I2C.h>

int com1 = 4;
int com2 = 5;
int com3 = 6;
int com4 = 7;
int Status1 = 0;
int Status2 = 0;

LiquidCrystal_I2C  lcd(0x27, 2, 1, 0, 4, 5, 6, 7);
RFID rfid(SS_PIN, RST_PIN);
String rfidCard;
void setup() {
  Serial.begin(9600);
  Serial.println("Starting the RFID Reader...");
  SPI.begin();
  rfid.init();
  pinMode(4, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  {
    lcd.begin (16, 2); // LCD 16x2
    lcd.setBacklightPin(3, POSITIVE);
    lcd.setBacklight(HIGH);
    lcd.print("LAB KOMPUTER");
  }
}


void loop() {
  if (rfid.isCard()) {
    if (rfid.readCardSerial()) {
      rfidCard = String(rfid.serNum[0]) + " " + String(rfid.serNum[1]) + " " + String(rfid.serNum[2]) + " " + String(rfid.serNum[3]);
      Serial.println(rfidCard);

      kom1 ();
      kom2 ();

    }
  }
}
