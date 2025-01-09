> [!info] WiFi - Arduino Reference  
> The Arduino programming language Reference, organized into Functions, Variable and Constant, and Structure keywords.  
> [https://www.arduino.cc/reference/en/libraries/wifi/](https://www.arduino.cc/reference/en/libraries/wifi/)  

[WiFi.RSSI()](https://www.arduino.cc/en/Reference/WiFiRSSI) - уровень сигнала точки доступа !

WiFi реализован синхронно, его обработчик должен постоянно вызываться во время работы программы не реже, чем каждые 20 мс (если WiFi используется в программе). Обработка WiFi происходит в следующих местах:  
Автоматически в конце каждой итерации loop()  
Внутри любого delay()  
Внутри функции yield()  
Если у вас есть участки программы, которые долго выполняются, то нужно разместить вызовы yield() до и после тяжёлых блоков кода. Также в чужих скетчах можно встретить delay(0), по сути это и есть yield().  
По тем же причинам не рекомендуется использовать задержку delayMicroseconds() более чем на 20’000 мкс.