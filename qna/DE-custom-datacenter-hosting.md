## Question

Unsere Cloud-Kasse arbeitet lediglich mit Eingabegeräten/Terminals, die keine Offlinefunktionalität bieten und nur bei (Internet-)Verbindung zum Rechenzentrum Vorgänge aufzeichnen können. Die Aufzeichnungen erfolgen ausschließlich auf den Servern im Rechenzentrum (Cloud). Damit ist das Rechenzentrum lt. BSI das "Operational Environment". Kann ich in meinem Rechenzentrum eine eigene TSE betreiben?

## Metadata tags

lang-de, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

Die fiskaltrust Lösung kann bei Bedarf unter bestimmten Rahmenbedingungen auch im eigenen Rechenzentrum des KassenHerstellers (PosCreator) betrieben werden.

### Voraussetzungen

- Der Kunde installiert und wartet das gemeinsam geplante Gewerk eigenständig
- Internetverbindung
- SQL Datenbank (MSSQL oder MySQL) für die Speicherung der Middlewaredaten

### Detailinformationen

| Leistungen Kunde                                             |                        | Leistungen fiskaltrust                                       |                           | Kosten                        |
| ------------------------------------------------------------ | ---------------------- | ------------------------------------------------------------ | ------------------------- | ----------------------------- |
| **Bereitstellung & Betrieb gewarteter  Kubernetes Cluster gem. ft. Anforderungen/sizing** im Rechenzentrum *(Eigenleistung oder wahlweise  Beauftragung an Dritte)* |                        |                                                              |                           | unbekannt                     |
| Rechenzentrum  Name:                                         | *(bitte bekanntgeben)* |                                                              |                           |                               |
|                                                              |                        |                                                              |                           |                               |
| **Briefing  für Sizing-Berechnung Kubernetes Cluster**  |                        | **Sizing Berechnung Kubernetes Cluster**                     |                           | keine                         |
| Anzahl Cashboxen:                                           | *(bitte bekanntgeben)* | total Backend PODs                                                   | *(wird von ft ermittelt)* |                               |
| Max. Anzahl Receipts/Tag/Cashbox:                            | *(bitte bekanntgeben)* | Datenbankspeicher                                     | *(wird von ft ermittelt)* |                               |
|                                                              |                        | |                               ||
|                                                              |                        | **Onboarding/Consulting**                                  |                           | einmalige Kosten              |
|                                                              |                        | Interview - Anforderungsanalyse                                  |                           |                               |
|                                                              |                        | Onboarding-Workshop                       |                           |                               |
|                                                              |                        | Umsetzungs-Support              |                           |                               |
|                                                              |                        | Abschlusstermin, Projektabschluss                               |                           |                               |
|                                                              |                        | |                                                              |                           |
|                                                              |                        | |                                                              |                           |
|                                                              |                        | **fiskaltrust Produkte**                                 |                           | monatliche Kosten pro Cashbox |
|                                                              |                        | Standard Produkt-Bundle mit TSE as a Service & Archiv         |                           |                               |

Für weitere Informationen oder ein individuelles Angebot wenden sie sich bitte an den fiskaltrust <a href="mailto:info@fiskaltrust.de">Support Team</a>.
