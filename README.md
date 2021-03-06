[![Version](https://img.shields.io/badge/Symcon-PHP--Modul-red.svg)](https://www.symcon.de/service/dokumentation/entwicklerbereich/sdk-tools/sdk-php/)
[![Version](https://img.shields.io/badge/Symcon%20Version-5.0-blue.svg)](https://www.symcon.de/produkt/)
[![Version](https://img.shields.io/badge/Modul%20Version-1.0.20180415-orange.svg)](https://github.com/Wilkware/SymconMHC)
[![Version](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-green.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

# MHC - Magic Home Controller
IP-Symcon Modul für die Ansteuerung von WiFi LED Controller der Firma _Magic Home_.

### Danksagung 

Dieses Modul basiert auf dem Modul von ...
* _Spoosie_ : Modul _KH\_LEDWiFiController_ (https://github.com/Spoosie/KH_LEDWiFiController) 

Vielen Dank für die hervorragende und tolle Arbeit! 

### Inhaltverzeichnis

1. [Funktionsumfang](#1-funktionsumfang)
2. [Voraussetzungen](#2-voraussetzungen)
3. [Software-Installation](#3-software-installation)
4. [Einrichten der Instanzen in IP-Symcon](#4-einrichten-der-instanzen-in-ip-symcon)
5. [Statusvariablen und Profile](#5-statusvariablen-und-profile)
6. [WebFront](#6-webfront)
7. [PHP-Befehlsreferenz](#7-php-befehlsreferenz)
8. [Changlog] (#8-changelog)

### 1. Funktionsumfang

Das Modul dient zur Ansteuerung von LED Strpes mittels eines WiFi LED Controllers des Herstellers Magic Home.
Das sind Controller vom Typ LD382 bzw. LD382A.


Wenn jemand noch weitere kennt, bitte einfach bei mir melden!

### 2. Voraussetzungen

- IP-Symcon Version 5.0 
- Funktioniert wahrscheinlich auch mit der Version 4.4 (nicht getestet).

### 3. Software-Installation

Über das Modul-Control folgende URL hinzufügen.  
`https://github.com/Wilkware/SymconMHC` oder `git://github.com/Wilkware/SymconMHC.git`

### 4. Einrichten der Instanzen in IP-Symcon

- Unter "Instanz hinzufügen" ist das 'Magic Home Controller'-Modul (Alias: LED Controller) unter dem Hersteller '(Sonstige)' aufgeführt.

__Konfigurationsseite__:

Die Konfiguration beinhaltet die Zuweisung der IP-Adresse und der Auswahl der Farbkanal-Reihenfolge (RGB-Pins).
Derzeit werden Stripes mit der Reihenfolge GRB (Gelb, Rot, Blau) und BRG (Blau, Rot, Gelb) unterstützt. 
Die Reihenfolge der Pins beginnt immer ausgehend vom GND-Pin (12V Pin).

Darüber hinaus kann noch ausgewählt werden, ob die Debug-Meldungen auch im Status Logging (Log Meldungen) ausgegeben werden sollen.

Name               | Beschreibung
------------------ | ---------------------------------
WiFi Controller IP | IP-Adresse des Controlers im lokalen WLAN (zb. 192.168.0.10)
RGB Pin Belegung   | Reihenfolge der Farb-Pins (GRB oder BRG), Standard ist GRB
Meldungen im Log   | Ausgabe von Debug-Meldungen im Log


### 5. Statusvariablen und Profile

Ident         | Name                | Typ       |  Profil                      | Beschreibung
------------- | ------------------- | --------- | ---------------------------- | -------------------------------------------------------
Brightness    | Helligkeit          | Integer   | ~Intensity.100               | Helligkeitswert von 0 bis 100%
Color         | Farbe               | Integer   | ~HexColor                    | Farbwert
Mode          | Modus               | Integer   | MHC.ModeGRB oder MHC.ModeBRG | Manueller Farbmodus oder vordefinierter Funktionsmodus
Power         | Aktiv               | Boolean   | ~Switch                      | An/Aus Schalter 
Speed         | Geschwindigkeit     | Integer   | ~Intensity.100               | Geschwindigkeitswert von 0 bis 100%

### 6. WebFront

Man kann die Statusvariaben direkt im WebFront verlinken.

### 7. PHP-Befehlsreferenz

`void MHC_SetBrightness(int $InstanzID, int $Brightness);`  
Setzt die Helligkeit auf $Brightness. Die Funktion liefert keinerlei Rückgabewert.

`void MHC_SetColor(int $InstanzID, int $Color);`  
Setzt den Farbwert auf $Color. Die Funktion liefert keinerlei Rückgabewert.

`void MHC_SetMode(int $InstanzID, int $Mode);`  
Setzt den Anzeigemodus auf auf $Mode. Die Funktion liefert keinerlei Rückgabewert.

`void MHC_Power(int $InstanzID, bool $Power);`  
Schaltet den Controler Ein(true) bzw Aus(false). Die Funktion liefert keinerlei Rückgabewert.

### 8. Changelog

Version 20180415
* _NEU_: Initialversion

### Entwickler
* Heiko Wilknitz ([@wilkware](https://github.com/wilkware))

### Spenden
Die Software ist für die nicht kommzerielle Nutzung kostenlos, Schenkungen als Unterstützung für den Entwickler bitte hier:  
<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=8816166" target="_blank"><img src="https://www.paypalobjects.com/de_DE/DE/i/btn/btn_donate_LG.gif" border="0" /></a>
