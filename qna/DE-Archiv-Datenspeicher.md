## Question

Wo speichert fiskaltrust welche Daten?

## Question

Wo werden die Daten des POSArchiv und AKO revisionssicher gespeichert?

## Question

Wo befinden sich die archivierten DSFinV-K und TSE TAR-Files?

## Question

An welchem Speicherort werden die Daten durch fiskaltrust revisionsicher archiviert?

## Metadata tags

lang-de, market-de, data-archive, bundle-carefree, PosCreator, PosDealer, PosOperator, Consultant

## Answer

### ### Art der Daten

* Kundenbezogene Daten (= Name, Adresse, Kontaktdaten, UID-Nummer, Aufträge, usw. von KassenHerstellern, KassenHändlern, KassenBetreibern)
* Konfigurations- und Statusdaten (= TSE-Zertifikat, ClientId, Status der Queue, usw.)

### Massendaten (= ReceiptRequest, ReceiptResponse)

* Revisionsgesicherte kundenbezogene Massendaten (= .Tar-File, DSFinV-K-File, usw.)
* Allgemeine kundenbezogene Massendaten (= Kopie von allem, was in revisionsgesicherten Kundenbezogenen Massendaten manuell gespeichert wird, Rechnungen, Verträge, usw.)

### Standorte der Verarbeitung

* Azure-Region West-Europe (a104, a105)
* Azure-Region North-Europe 
* Azure-Region Germany-West-Central  (a110, a111)
* Azure-Region France-Central (a107, a108)
* Equinix-Datacenter Amsterdam (nl18) (https://www.equinix.com/locations/europe-colocation/netherlands-colocation/amsterdam-data-centers/)
* RRZ-Datacenter Raaba / Graz (at11) (https://www.rrz.co.at/)

### Standorte der Speicherung

* SQL Azure West-Europe -> Mirror ( Azure North-Europe, Azure Germany-West-Central, Azure France-Central)
* Dynamics365 EMEA Region (=crm4)
* Massendaten Azure West-Europe -> Mirror Azure North-Europe
* Kundenbezogene Massendaten Deutschland Azure Germany-West-Central

### Unterscheidung bei Verarbeitung

* Allgemeine Workloads werden in West-Europe verarbeitet.
* CPU-Intensive Workloads werden in North-Europe und Raaba / Graz (at11) verarbeitet.
* Kundenbezogene Daten werden ausschließlich in einer eigenen Dynamics365 - Instanz pro Land verwaltet.
* Alle Services mit der Endung "fiskaltrust.de" werden mit Azure Germany-West-Central (Microsoft Azure in Deutschland) verarbeitet.
* Kundenbezogene Massendaten für Konfigurationen, welche mit Services mit der Endung "fiskaltrust.de" erzeugt wurden, werden in Azure Germany-West-Central gespeichert.
