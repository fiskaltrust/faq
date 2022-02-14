## Question
Ich bekomme die fiskaltrust.Middleware bei einem Kunden nicht zum Laufen. Welche technischen Ursachen kann das haben?

## Metadata tags
lang-de, market-de, middleware, PosCreator, PosDealer

## Answer

### Die Middleware (der Launcher) kann nicht aus dem Portal heruntergeladen werden
* Rebuild Configuration Button klicken im Portal, danach herunterladen
* Einen anderen Browser zum Download verwenden
* Einen anderen Computer zum Download verwenden
	
### Der Online Launcher kann die Pakete beim Starten nicht herunterladen
* Eine andere Internetverbindung verwenden
* Bei restriktiven Firewalls kann der Upload in das fiskaltrust.Portal blockiert werden. Hier hilft es auf dem Gerät, auf dem der fiskaltrust.Service und als der Benutzer der den Dienst startet (wegen Proxy Problemen) die Verbindung zur fiskaltrust.Cloud zu prüfen. Geben sie folgendes in den Browser ein:
* Helipad:             https://helipad.fiskaltrust.cloud/api/version (für den Upload der Daten)
* Packages:           https://packages.fiskaltrust.cloud/api/version (für den Download der Pakete beim ersten Start)
Wenn die Verbindung erfolgreich ist, erhalten Sie jeweils ein JSON mit Versionsinformationen angezeigt.

### Der Dienst startet nicht richtig
* Unser Service benötigt .net Framework (am besten 4.8) und eine Microsoft C++ Runtime als Voraussetzung, genaueres hier /fiskaltrust/productdescription-de-doc/blob/master/product-service-description/compliance-as-a-service/produkte/lokal-installierte-middleware.md
* Eine bestimmte Instanz eines fiskaltrust.Dienstes (eine Cashbox mit einer CashboxId und einem Accesstoken) kann auf einem Gerät nur einmal laufen. Sonst würde versucht werden, die gleichen Endpunkte mehrmals zu verwenden. Mehrere unterschiedliche Cashboxen können bei richtiger Konfiguration auf einem Gerät gleichzeitig laufen.
* Wurde der Dienst mit Administrator Rechten gestartet? Der Benutzer, unter dem der Dienst ausgeführt wird muss Administrator Rechte besitzen.
* Zur Fehlersuche kann es sehr hilfreich sein, den fiskaltrust.Service mit ```test.cmd``` direkt aufzurufen (Achtung nur ENTWEDER mit test.cmd aufrufen, ODER als Windows Dienst im Hintergrund starten, eine Instanz darf nicht 2 Mal auf einem Gerät gestartet werden UND AUCH NICHT AUF VERSCHIEDENEN GERÄTEN). Wenn man die ```test.cmd``` editiert, kann man auch den Parameter -verbosity=debug und -logfile="C:\t\fiskaltrust.log" anhängen um mehr Informationen angezeigt zu bekommen. Siehe auch die FAQ _Debugging_. https://docs.fiskaltrust.cloud/doc/faq/qna/DE-debugging.html?q=debugging


### Nach dem Neustart des Geräts startet der Dienst nicht selbständig. Wird er manuell gestartet, funktioniert der Dinest einwandrei.
* Den Windows Dienst auf die Startart „Automatisch (verzögerter Start)“ setzen. Damit wird sichergestellt, dass benötigte Dienste beim Aufruf schon bereit sind.


### Es kommt keine Signatur zurück (überhaupt nicht, von Anfang an nicht)
* Ist in der Konfiguration der TSE/Signaturerstellungseinheit der richtige Laufwerksbuchstabe, COM Port eingetragen?
* Wird die TSE richtig erkannt, sehe ich den Laufwerksbuchstaben im Explorer, den COM Port im Gerätemanager?

### Die fiskaltrust.Middleware liefert plötzlich zu einem Request keine ftSignaturType im Response zurück.
* Senden sie einen [zero-receipt](https://docs.fiskaltrust.cloud/doc/interface-doc/doc/appendix-de-kassensichv/reference-tables/type-of-receipt-ftreceiptcase.html#type-of-receipt-ftreceiptcase) als Request. Beim Senden eines [zero-receipt](https://docs.fiskaltrust.cloud/doc/interface-doc/doc/appendix-de-kassensichv/reference-tables/type-of-receipt-ftreceiptcase.html#type-of-receipt-ftreceiptcase) wird von der fiskaltrust.Middleware versucht, die Verbindung zur TSE wiederherzustellen. 
* Ist eine verwendete Hardware-TSE (versehentlich) vom Gerät getrennt worden?
* Ist keine Internetverbindung zur Kommunikation mit einer Cloud-TSE vorhanden?
* Ist eine erforderliche Konfiguration eines Laufwerksbuchstabes oder COM Port noch korrekt?
* Wurde am System etwas geändert, Updates eingespielt, neue Hardware angeschlossen, alte Hardware entfernt?


### Es kommt keine Signatur zurück (nach längerem Betrieb)
* War der Computer im Energiesparmodus? Eventuell hilft ein Ausschalten der Energiesparmodi.

### Die Kasse meldet, dass die fiskaltrust.Middleware nicht erreichbar ist, wie kann ich das prüfen?
* Ist der Endpunkt der Middleware erreichbar? Man erhält eine Antwort im Browser, wenn man in den Browser den Endpunkt eingibt (Bei GRPC kommen nur “Sonderzeichen”, erhält man diese, so kann man aber zumindest davon ausgehen, dass der fiskaltrust.Service gestartet wurde und auf Eingaben wartet).
z.B. (je nach konfiguriertem Endpunkt bei der Queue)
* REST:      http://localhost:1200/ftrest 
* WCF SOAP:  http://localhost:1200/fiskaltrust
* GRPC:      http://localhost:10103/ 
Siehe auch die FAQ Debugging.

### Die Belege werden korrekt signiert, im fiskaltrust.Portal sind die Belege aber auch nach einiger Zeit noch nicht sichtbar.
* Bei restriktiven Firewalls kann der Upload in unser Portal blockiert werden. Prüfen Sie die Verbindung zur fiskaltrust.Cloud auf dem Gerät als der Benutzer, der den Service ausführt. Um Proxy-Probleme auszuschließen empfiehlt es sich, immer den Benutzer des Services für Tests zu verwenden.  Geben Sie folgendes in die Adresszeile des Browsers ein:
* Helipad:             https://helipad.fiskaltrust.cloud/api/version (für den Upload der Daten)
* Packages:           https://packages.fiskaltrust.cloud/api/version (für den Download der Pakete beim ersten Start)
Sie erhalten jeweils eine JSON-Struktur mit Versionsinformationen angezeigt, falls die Verbindung fehlerfrei ist.
* Wenn im fiskaltrust.Service die interne Kommunikation mit GRPC erfolgt (der Endpunkt der TSE/Signaturerstellungseinheit ein GRPC Endpunkt ist), dann kann ein verwendeter Proxy zu Problemen führen. Dies kann durch setzen der Environement-Variable ```no_grpc_proxy``` auf localhost (wenn localhost verwendet wird) umgangen werden https://github.com/grpc/grpc/blob/master/doc/environment_variables.md 


### Meine fiskaly TSE scheint nicht zu funktionieren, wie kann ich die Verbindung zu fiskaly prüfen?	
* Kann man die Adresse kassensichv.io über einen ping erreichen (in einer Eingabeaufforderung ping kassensichv.io eingeben, hier sollte eine Antwort kommen)?
* Fehlermeldungen in der Firewall (lokal am Gerät, oder im Netzwerk)?

### Ich habe alles versucht, was kann noch eine Ursache eines Problems sein?
* Lokaler Virenscanner | Dieser kann den Zugriff auf vom fiskaltrust.Service benötigte Dateien sperren. z.B. im Ordner C:\Programdata\fiskaltrust
* Lokale Firewall | Der fiskaltrust.Service kommuniziert auch intern auf einem Computer über Netzwerkports (außer bei net.pipe)
* Windows Updates installiert | Dies kann selten zu Änderungen der erkannten Geräte führen.
* Registry Cleaner | Könnten Änderungen am Startverhalten des fiskaltrust.Service vorschlagen.
