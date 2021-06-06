void kom2 () {
  if (rfidCard == "7 74 8 217" && Status2 == 0) {
    Status2 = 1;
    lcd.setCursor(0, 0);
    lcd.print("Komputer 2 ON");
    lcd.setCursor(1, 1);
    lcd.print("Welcome Fadil");
    digitalWrite(6, HIGH);
    digitalWrite(7, HIGH);
    delay(2000);
    lcd.clear();
    rfid.halt();
  }

  else if (rfidCard == "7 74 8 217" && Status2 == 1) {
    lcd.setCursor(0, 0);
    lcd.print("Komputer 2 ON");
    lcd.setCursor(1, 1);
    lcd.print("Tempelkan lagi");
    digitalWrite(6, HIGH);
    digitalWrite(7, HIGH);
    delay(500);
    digitalWrite(7, LOW);
    delay(500);
    digitalWrite(7, HIGH);
    delay(500);
    digitalWrite(7, LOW);
    delay(500);
    digitalWrite(7, HIGH);
    delay(500);
    digitalWrite(7, LOW);
    delay(500);
    digitalWrite(7, HIGH);
    delay(500);
    digitalWrite(7, LOW);
    lcd.clear();
    rfid.halt();
    int selesai2 = 1;
    while (rfid.isCard()) {
      if (rfid.readCardSerial()) {
        rfidCard = String(rfid.serNum[0]) + " " + String(rfid.serNum[1]) + " " + String(rfid.serNum[2]) + " " + String(rfid.serNum[3]);
        Serial.println(rfidCard);
        if (rfidCard == "7 74 8 217" && selesai2 == 1) {
          Status2 = 0;
          lcd.setCursor(0, 0);
          lcd.print("Komputer 2 OFF");
          lcd.setCursor(1, 1);
          lcd.print("Bye Fadil");
          digitalWrite(6, LOW);
          digitalWrite(7, LOW);
          delay(500);
          lcd.clear();
        }
        rfid.halt();
      }
    }
  }

}
