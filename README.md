- 👋 Hi, I’m @Charanmudhira
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Charanmudhira/Charanmudhira is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->//Pateek
//www.justdoelectronics.com
 
#include <TinyGPS.h>
#include <SoftwareSerial.h>
#include <Wire.h>
SoftwareSerial Gsm(9, 10);
 
char phone_no[] = "+919346124760";
 
TinyGPS gps;
int state;
String textMessage;
void setup() {
  Serial.begin(9600);
  Gsm.begin(9600);
  delay(2000);
  Serial.print("AT+CMGF=1\r");
  delay(100);
  Serial.print("AT+CNMI=2,2,0,0,0\r");
  delay(100);
  pinMode(5, INPUT);
}
 
void loop() {
  bool newData = false;
  unsigned long chars;
  unsigned short sentences, failed;
 
  for (unsigned long start = millis(); millis() - start < 1000;) {
    while (Serial.available()) {
      char c = Serial.read();
      Serial.print(c);
      if (gps.encode(c))
        newData = true;
    }
  }
 
  if (textMessage.indexOf("LOCAL") >= 0) {
    float flat, flon;
    unsigned long age;
    gps.f_get_position(&flat, &flon, &age);
    Gsm.print("AT+CMGF=1\r");
    delay(400);
    Gsm.print("AT+CMGS=\"");
    Gsm.print(phone_no);
    Gsm.println("\"");
    delay(3000);
    Gsm.print(flat == TinyGPS::GPS_INVALID_F_ANGLE ? 0.0 : flat, 6);
    Serial.print(",");
    Gsm.print(flon == TinyGPS::GPS_INVALID_F_ANGLE ? 0.0 : flon, 6);
    delay(200);
    Gsm.println((char)26);
    delay(200);
    Gsm.println();
    delay(10000);
  }
 
  Serial.println(failed);
  Serial.println("**GPS: check wiring **");
}                                                   if (state == 0) {
    float flat, flon;
    unsigned long age;
    gps.f_get_position(&flat, &flon, &age);
    Gsm.print("AT+CMGF=1\r");
    delay(400);
    Gsm.print("AT+CMGS=\"");
    Gsm.print(phone_no);
    Gsm.println("\"");
    delay(3000);
    Gsm.println("Alert I need help... ");
    //Prateek
    //www.justdoelectronics.com
    Gsm.print(flat == TinyGPS::GPS_INVALID_F_ANGLE ? 0.0 : flat, 6);
    Serial.print(",");
    Gsm.print(",");
    Gsm.print(flon == TinyGPS::GPS_INVALID_F_ANGLE ? 0.0 : flon, 6);
    delay(200);
    Gsm.println((char)26);
    delay(200);
    Gsm.println();
    Serial.print("Alert I need help... ");
    delay(10000);
 
  } else {
    delay(10);
  }
