void kom1 () {
  if (rfidCard == "71 36 4 217" && Status1 == 0) {
    Status1 = 1;
    lcd.setCursor(0, 0);
    lcd.print("Komputer 1 ON");
    lcd.setCursor(1, 1);
    lcd.print("Welcome Agung");
    digitalWrite(4, HIGH);
    digitalWrite(5, HIGH);
    delay(2000);
    lcd.clear();
    rfid.halt();
  }

  else if (rfidCard == "71 36 4 217" && Status1 == 1) {
    lcd.setCursor(0, 0);
    lcd.print("Komputer 1 ON");
    lcd.setCursor(1, 1);
    lcd.print("Tempelkan lagi");
    digitalWrite(4, HIGH);
    digitalWrite(5, HIGH);
    delay(500);
    digitalWrite(5, LOW);
    delay(500);
    digitalWrite(5, HIGH);
    delay(500);
    digitalWrite(5, LOW);
    delay(500);
    digitalWrite(5, HIGH);
    delay(500);
    digitalWrite(5, LOW);
    delay(500);
    digitalWrite(5, HIGH);
    delay(500);
    digitalWrite(5, LOW);
    lcd.clear();
    rfid.halt();
    int selesai1 = 1;
    while (rfid.isCard()) {
      if (rfid.readCardSerial()) {
        rfidCard = String(rfid.serNum[0]) + " " + String(rfid.serNum[1]) + " " + String(rfid.serNum[2]) + " " + String(rfid.serNum[3]);
        Serial.println(rfidCard);
        if (rfidCard == "71 36 4 217" && selesai1 == 1) {
          Status1 = 0;
          lcd.setCursor(0, 0);
          lcd.print("Komputer 1 OFF");
          lcd.setCursor(1, 1);
          lcd.print("Bye Agung");
          digitalWrite(4, LOW);
          digitalWrite(5, LOW);
          delay(500);
          lcd.clear();
        }
        rfid.halt();
      }
    }
  }

}
