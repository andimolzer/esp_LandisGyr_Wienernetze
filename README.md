# smartmeter->reader()
um den Landis&amp;Gyr E450 Smartmeter der Wiener-Netze mit einem ESP8266 auszulesen und die Daten an einen MQTT-Broker zu übergeben.  

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

Hat man die Kundenschnittstelle am Smartmeter frei geschalten (https://www.wienernetze.at/smart-meter-portale), benoetigt man nur noch den Key.  

Nach dem Flashen und dem ersten Start, erstellt der ESP ein neues WLAN.
mit dem WLAN verbinden und unter der URL http://192.168.4.1 sein WLAN konfigurieren.  
Sollte sich der ESP nicht mit dem WLAN verbinden koennen, sollte er nach einer gewissen Zeit wieder unter http://192.168.4.1 erreichbar sein.  

Nach einen erneuten Neustart des ESP einfach die von deinem Router vergebene IP-Adresse aufrufen um die Konfiguration ab zu schliessen.  

![setup](https://avatars2.githubusercontent.com/u/53957681?s=460&u=68dab87193fe05690a01e1cf6226a8069ca4ec75&v=4)





