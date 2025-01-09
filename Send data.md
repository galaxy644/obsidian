```C++
\#include <Arduino.h>
\#include <microDS18B20.h>
\#include <ESP8266WiFi.h>
\#include <ESP8266WiFiMulti.h>
\#include <ESP8266HTTPClient.h>
\#include <WiFiClient.h>
\#define DS_PIN 4 // пин для термометров
uint8_t s1_addr[] = {0x28, 0x61, 0x64, 0xA, 0x73, 0x6F, 0xE2, 0xE3}; //Ближний к МК
uint8_t s2_addr[] = {0x28, 0x61, 0x64, 0xA, 0x73, 0xD, 0x30, 0xC3};  //Дальний от МК
MicroDS18B20<DS_PIN, s1_addr> sensor1;  // Создаем термометр с адресацией
MicroDS18B20<DS_PIN, s2_addr> sensor2;  // Создаем термометр с адресацией

ESP8266WiFiMulti WiFiMulti;

void setup() {

  Serial.begin(115200);
  // Serial.setDebugOutput(true);

  Serial.println();
  Serial.println();
  Serial.println();

  for (uint8_t t = 4; t > 0; t--) {
    Serial.printf("[SETUP] WAIT %d...\n", t);
    Serial.flush();
    delay(1000);
  }

  WiFi.mode(WIFI_STA);
  //WiFiMulti.addAP("Kotimaa", "OgTu@Kil791mUr");
  WiFiMulti.addAP("Dyfnder", "Qd129MrZ18");
}

void loop() {
  // wait for WiFi connection
  if ((WiFiMulti.run() == WL_CONNECTED)) {

    WiFiClient client;
    HTTPClient http;
    sensor1.requestTemp();      // Запрашиваем преобразование температуры
    sensor2.requestTemp();
    delay(1000);
    Serial.print("[HTTP] begin...\n");
    //if (http.begin(client, ("http://test:test@grafana.kitrm.ru/data/?vr=30.30")) {  // HTTP
    String uurl("http://test:test@grafana.kitrm.ru/data/?vr=");
    uurl+=sensor1.getTemp();
    if (http.begin(client, uurl )) {  // HTTP
    
      Serial.print("[HTTP] GET...\n");
      // start connection and send HTTP header
      int httpCode = http.GET();

      // httpCode will be negative on error
      if (httpCode > 0) {
        // HTTP header has been send and Server response header has been handled
        Serial.printf("[HTTP] GET... code: %d\n", httpCode);

        // file found at server
        if (httpCode == HTTP_CODE_OK || httpCode == HTTP_CODE_MOVED_PERMANENTLY) {
          String payload = http.getString();
          Serial.println(payload);
        }
      } else {
        Serial.printf("[HTTP] GET... failed, error: %s\n", http.errorToString(httpCode).c_str());
      }

      http.end();
    } else {
      Serial.println("[HTTP] Unable to connect");
    }
    //Второй датчик пошел :)
    uurl=("http://test:test@grafana.kitrm.ru/data/?wr=");
    uurl+=sensor2.getTemp();  
  if (http.begin(client, uurl )) {  // HTTP
    
      Serial.print("[HTTP] GET...\n");
      // start connection and send HTTP header
      int httpCode = http.GET();

      // httpCode will be negative on error
      if (httpCode > 0) {
        // HTTP header has been send and Server response header has been handled
        Serial.printf("[HTTP] GET... code: %d\n", httpCode);

        // file found at server
        if (httpCode == HTTP_CODE_OK || httpCode == HTTP_CODE_MOVED_PERMANENTLY) {
          String payload = http.getString();
          Serial.println(payload);
        }
      } else {
        Serial.printf("[HTTP] GET... failed, error: %s\n", http.errorToString(httpCode).c_str());
      }

      http.end();
    } else {
      Serial.println("[HTTP] Unable to connect");
    }
  }

  delay(119000);
}
```