Mit diesem Nodeskript k�nnen die Buzzer vom Playstaiton2 Spiel "Buzz!" f�r das NerdBeef verwendet werden.

Um die USB Buzzer unter Windows verwenden zu k�nnen sind folgende Schritte notwendig:
1. Buzzer anschlie�en ;-)
2. Den Ger�temanager aufrufen.
3. Mit rechte Maustaste auf den USB-Hub klicken und im Kontextmen� �Treibersoftware aktualisieren�� ausw�hlen.
4. Den Punkt �Auf dem Computer nach Treibersoftware suchen� starten.
5. Den Punkt �Aus einer Liste von Ger�tetreibern auf dem Computer ausw�hlen� starten.
6. Aus der Liste den Eintrag USB-Eingabeger�t (HID) markieren.
7. Mit dem Button Weiter die Installation abschliessen.

Folgende �nderungen sind in der "buzzerps2.js" Datei notwendig:
	var ip = "192.168.1.55:1111" => hier die IP Adresse des Servers eintragen.
	var HIDDEV = "\\\\?\\hid#vid_054c&pid_0002#8&3c95396&1&0000#{4d1e55b2-f16f-11cf-88cb-001111000030}" => hier die ID des Buzzer eintragen.

An das passende HID - Device (also die Buzzer) kommt man wie folgt:
	1. In der Konsole "node node_modules\node-hid\src\show-devices.js" aufrufen (bei Linux / OSX entsprechende "/" statt "\" verwenden)
	2. Von dem entsprechenden Device (Bei mir hie� es "Logitech Buzz(tm) Controller V1") die Variable "path" kopieren und in HIDDEV einf�gen.

Dann in einer Konsole die Node-Module installieren und das Programm starten:
	npm i node-hid bit-mask node-bitarray bitwise socket.io-client
	node buzzerps2.js