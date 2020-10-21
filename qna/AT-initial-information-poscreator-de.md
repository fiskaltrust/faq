## Question

Was ist die wichtigste Erstinformation für KassenHersteller (PosCreator) in AT

## Metadata tags

lang-de, market-at, middleware, portal-sandbox, architecture, cashbox management, portal, PosCreator, Consultant

## Answer

Erstinformationen und diverse FAQ zur Anbindung der fiskaltrust.Middleware sowie zur Anmeldung und Konfiguration in [https://portal.fiskaltrust.at](https://portal.fiskaltrust.at/).

**Allgemeines, Geschäftsmodell**

- Die fiskaltrust.Sicherheitseinrichtung (Middleware) ist eine kostenlose und standardisierte technische Umsetzung der Fiskalisierung (Signatur, QR-Code, Datenerfassungsprotokoll, …) für AT, DE und FR
- Das optionale Sorglos-Paket kostet dem Endkunden EUR 360,- pro Jahr bei lokale Anwendung sowie EUR 288,- pro Jahr für die Cloud-Anwendung
  - Produktübersicht: https://www.fiskaltrust.at/entgeltblatt
  - Für diese Produkte gibt es Großmengen-Preise für KassenHändler.
  - Die fiskaltrust.Sicherheitseinrichtung kann vom Kunden jedoch auch kostenlos verwendet werden!
  - Eine etwaig notwendige lokale Hardware wie z.B. Chip-Karte mit Leser ist nicht kostenlos inbegriffen.
  - Alle Produkte sind über https://portal.fiskaltrust.at/shop erhältlich

**Entwickler-Dokumentation**

- Die aktuelle Dokumentation zu unserer POS-Schnittstelle finden Sie für unter [https://docs.fiskaltrust.cloud](https://docs.fiskaltrust.cloud/).
- Die Kommunikation zwischen Kassensoftware und der Middleware funktioniert so, dass die Belegdaten aus der Kassensoftware an das iPos-Interface gesendet, dort verarbeitet (Summenzähler, Datenerfassungsprotokoll, QR-Code, …) und danach die ursprünglichen Belegdaten mit dem Response der Middleware auf den (jetzt RKSV konformen) Beleg gedruckt werden.
- In der Dokumentation ist auch ein github-repository mit Beispielen, wie unsere Sicherheitseinrichtung von der Kasse angesprochen wird, für verschiedene Programmiersprachen verfügbar. Test-Installationen können bei in [https://portal-sandbox.fiskaltrust.at](https://portal-sandbox.fiskaltrust.at/) kostenfrei generiert werden.
- Es stehen auch Nuget Packages zum Download bereit.

Diverse Tutorials sind als Videos unter https://youtube.com/c/fiskaltrust verfügbar. 

**Registrierung** 

- Für unsere Partnerschaft ist die kostenfreie Registrierung sowie der Abschluss der Rolle als KassenHersteller unter [https://portal.fiskaltrust.at](https://portal.fiskaltrust.at/) erforderlich.

**FAQ - AT** 

- Rechtsgrundlagen und Links zu den relevanten Gesetzen: https://www.fiskaltrust.at/rechtsgrundlagen
- Infos gibt es für registrierte Partner auch unter https://portal.fiskaltrust.at/ - „Download“ und „Fragen und Antworten“

* https://www.fiskaltrust.at/faq/
* https://www.fiskaltrust.at/checklist/

Kontakt: [info@fiskaltrust.at](mailto:info@fiskaltrust.at) 

.