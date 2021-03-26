## Question

An welchem Speicherort werden die Daten durch fiskaltrust (POS Archiv und AKO,  DSFinV-K und TSE TAR-Files) revisionsicher archiviert?

## Question

Welche personenbezogenen Daten werden resultierend aus dem Kassengesetz gespeichert ?

## Question

Werden die gespeicherten Daten pseudonymisiert oder anonymisiert und wer hat Zugriff auf die Verschlüsselung?

## Question

Welche Sicherheiten (Löschfristen) sind vorgesehen, um die Daten für den gesetzlich vorgeschriebenen Zeitraum zu speichern?

## Metadata tags

lang-de, market-de, data-archive, bundle-carefree, PosCreator, PosDealer, PosOperator, Consultant

## Answer

### Welche Daten werden verarbeitet

- Kundenbezogene Daten (= Name, Adresse, Kontaktdaten, UID-Nummer, Aufträge, usw. von KassenHerstellern, KassenHändlern, KassenBetreibern)
- Konfigurations- und Statusdaten (= TSE-Zertifikat, ClientId, Status der Queue, usw.)
- Massendaten (= ReceiptRequest, ReceiptResponse)
- Revisionsgesicherte kundenbezogene Massendaten (= .Tar-File, DSFinV-K-File, usw.)
- Allgemeine kundenbezogene Massendaten (= Kopie von allem, was in revisionsgesicherte Kundenbezogene Massendaten gespeichert wird, Rechnungen, Verträge, usw.)

Resultierend aus dem Gesetz müssen keine personenbezogenen Daten gespeichert werden. Der Kassenhersteller entscheidet, welche Daten bei der Registrierung im Portal und auf den Kassenbelegen (Massendaten) bekannt gegeben werden.

Wenn ein Kassenhersteller sich z.B. im Portal registriert, dann könnte er auch anonymisierte Daten verwenden. 
Bitte beachten Sie, dass Sie z.B. bei den Belegdaten keine Namen oder dergleichen aufdrucken, wenn Sie die Bekanntgabe von personenbezogenen Daten verhindern möchten. 
In der Praxis wird es wohl kaum zu verhindern sein, personenbezogene Daten zu verwenden, das Gesetz sieht hier jedoch keine Notwendigkeit vor. 

### Wo werden die Daten verarbeitet

* Azure-Region West-Europe (a104, a105)
* Azure-Region North-Europe 
* Azure-Region Germany-West-Central  (a110, a111)
* Azure-Region France-Central (a107, a108)
* Equinix-Datacenter Amsterdam (nl18) (https://www.equinix.com/locations/europe-colocation/netherlands-colocation/amsterdam-data-centers/)
* RRZ-Datacenter Raaba / Graz (at11) (https://www.rrz.co.at/)


### Wo werden die Daten gespeichert

- SQL Azure West-Europe -> Mirror (Azure North-Europe, Azure Germany-West-Central, Azure France-Central)
- Dynamics365 EMEA Region (=crm4)
- Massendaten Azure West-Europe -> Mirror Azure North-Europe
- Kundenbezogene Massendaten Deutschland Azure Germany-West-Central


- Allgemeine Workloads werden in West-Europe verarbeitet.
- CPU-Intensive Workloads werden in North-Europe und at11 verarbeitet.
- Kundenbezogene Daten werden ausschließlich in einer eigenen Dynamics365 - Instanz pro Land verwaltet.
  - Alle Services mit der Endung "fiskaltrust.de" werden mit Azure Germany-West-Central ([Microsoft Azure in neuen Cloudregionen in Deutschland verfügbar | Azure-Updates | Microsoft Azure](https://azure.microsoft.com/de-de/updates/microsoft-azure-available-from-new-cloud-regions-in-germany/)) verarbeitet.
  - Kundenbezogene Massendaten für Konfigurationen, welche mit Services mit der Endung "fiskaltrust.de" erzeugt wurden, werden in Azure Germany-West-Central gespeichert.

### Wie werden die Daten gespeichert

Die Daten werden gemäß den gesetzlichen Vorgaben in der Form gespeichert, in der sie an die Middleware geschickt werden.

### Wie lange werden die Daten aufbewahrt

Die Daten werden mindestens entsprechend der gesetzlichen Aufbewahrungsfristen aufbewahrt (dzt. mindestens 10 Jahre), bzw. die Speicherdauer verlängert sofern anderweitige Verfahren anhängig sind.