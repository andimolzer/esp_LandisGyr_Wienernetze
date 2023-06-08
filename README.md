# smartmeter->reader()
um den Landis&amp;Gyr E450 Smartmeter der Wiener-Netze mit einem ESP8266 auszulesen und die Daten an einen MQTT-Broker zu übergeben.  
(sollte es jemand mit einem anderen Zaehler versuchen und Erfolg haben, dann lasst es mich bitte wissen :))

## Vorraussetzungen  
1x TTL IR(Infrarot) Lesekopf, [ich verwende diesen](https://bayha-electronics.de/produkt/bausatz-ttl-irinfrarot-lese-schreibkopf/)  
1x NodeMcu oder aehnliches mit mehr als 1 MiB Speicher falls einmal OTA verwendet werden sollte  

wer es kompakter will, [kann auch diesen](https://bayha-electronics.de/produkt/tasmota-wifi-lesekopf/) verwenden.  
Nachteil -> umstaendlich zu flashen und zu wenig Speicher für OTA  

Beim Flashen mit USB-Kabel darf der TTL-Lesekopf nicht angeschlossen sein.  

## Anschluss  
|ESP  |TTL  |  
|-----|-----|  
|RX   |TX   |  
|TX   |RX   |  
|3.3V |VCC  |  
|GND  |GND  |  

Hat man die Kundenschnittstelle am Smartmeter frei geschalten (https://www.wienernetze.at/smart-meter-portale), benoetigt man nur noch den dabei hinterlegten Key.  
(es ist nicht erforderlich einen PIN mit der Taschenlampe rein zu blinseln wie bei manch anderen Zaehlern)  

Nach dem Flashen und dem ersten Start, erstellt der ESP ein neues WLAN (ESPxxxxx).  
Mit dem WLAN verbinden und unter http://192.168.4.1 sein eigenes WLAN konfigurieren.  
Sollte sich der ESP nicht mit dem WLAN verbinden koennen, erstellt er nach einer gewissen Zeit wieder einen AP und ist wieder unter http://192.168.4.1 erreichbar.    

Nach einen erneuten Neustart des ESP einfach die von deinem Router vergebene IP-Adresse aufrufen um die Konfiguration ab zu schliessen.  

![setup](https://github.com/andimolzer/esp_LandisGyr_Wienernetze/blob/main/setup.PNG)  

Ueber die URL http://xxx.xxx.xxx.xxx:8080/webota koennen eventuelle Updates geflasht werden.  
![OTA](https://github.com/andimolzer/esp_LandisGyr_Wienernetze/blob/main/ota.png)  

Im Endeffekt sieht das z.B.: im MQTT-Adapter von IOBroker dann so aus   
  
![IOBROKER](https://github.com/andimolzer/esp_LandisGyr_Wienernetze/blob/main/iobroker.PNG)  
(1_7_0= aktueller Stromverbr., 1_8_0= aktueller Zaehlerstand, 2_7_0= aktuelle Einspeisung, 2_8_0= Einspeisung Zaehlerstand)  
  
  woraus man sich dann z.b. mit Grafana soetwas basteln kann  
  
![grafana](https://github.com/andimolzer/esp_LandisGyr_Wienernetze/blob/main/grafana.PNG)  
