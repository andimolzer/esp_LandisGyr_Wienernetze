# smartmeter->reader()
um den Landis&amp;Gyr E450 Smartmeter der Wiener-Netze mit einem ESP8266 auszulesen.  

## Vorraussetzungen  
1x TTL IR(Infrarot) Lesekopf [ich verwende diesen](https://bayha-electronics.de/produkt/bausatz-ttl-irinfrarot-lese-schreibkopf/)  
1x NodeMcu oder aehnliches mit mehr als 1 MiB Speicher falls einmal OTA verwendet werden sollte  
4x Jumperkabel  

wer es kompakter will, [kann auch diesen](https://bayha-electronics.de/produkt/tasmota-wifi-lesekopf/) verwenden.  
Nachteil -> schwieriger zu flashen und zu wenig Speicher für OTA  

Beim Flashen mit USB-Kabel darf der TTL-Lesekopf nicht angeschlossen sein.  

## Anschluss  
|ESP  |TTL  |  
|-----|-----|  
|RX   |TX   |  
|TX   |RX   |  
|3.3V |VCC  |  
|GND  |GND  |  


