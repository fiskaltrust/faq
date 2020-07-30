## Question

Unsere Cloud-Kasse arbeitet lediglich mit Eingabegeräten/Terminals, die keine Offlinefunktionalität bieten und nur bei (Internet-)Verbindung zum Rechenzentrum Vorgänge aufzeichnen können. Die Aufzeichnungen erfolgen ausschließlich auf den Servern im Rechenzentrum (Cloud). Damit ist das Rechenzentrum lt. BSI das "Operational Environment". Kann ich in meinem Rechenzentrum eine eigene TSE betreiben?

## Metadata tags

lang-de, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

Die fiskaltrust Lösung kann bei Bedarf unter bestimmten Rahmenbedingungen auch im eigenen Rechenzentrum des Kassenherstellers (PosCreator) betrieben werden.

### Voraussetzungen

- Der Kunde installiert und wartet das gemeinsam geplante Gewerk eigenständig

### Detailinformationen

| Leistungen Kunde                                             |                        | Leistungen fiskaltrust                                       |                           | Kosten                        |
| ------------------------------------------------------------ | ---------------------- | ------------------------------------------------------------ | ------------------------- | ----------------------------- |
| **Bereitstellung & Betrieb gewarteter  Kubernetes Cluster gem. ft. Anforderungen/sizing** im Rechenzentrum *(Eigenleistung oder wahlweise  Beauftragung an Dritte)* |                        |                                                              |                           | unbekannt                     |
| Der Cluster muss exklusiv zur Verfügung stehen (kein shared Cluster), da fiskaltrust Monitoring und Management der PODs übernimmt |                        |                                                              |                           |                               |
| SLA des Clusters mindestens 99,9% monatlich                  |                        |                                                              |                           |                               |
| Redundante Internetverbindung mit statischer Public IP       |                        |                                                              |                           |                               |
| Persistenter Speicher (SSD based)                            |                        |                                                              |                           |                               |
| Rechenzentrum  Name:                                         | *(bitte bekanntgeben)* |                                                              |                           |                               |
|                                                              |                        |                                                              |                           |                               |
| **Briefing  für sizing-Berechnung Kubernetes Cluster**       |                        | **Sizing Berechnung Kubernetes Cluster**                     |                           | keine                         |
| Anzahl  Cashboxen:                                           | *(bitte bekanntgeben)* | total PODs                                                   | *(wird von ft ermittelt)* |                               |
| Max. Anzahl Receipts/Tag/Cashbox:                            | *(bitte bekanntgeben)* | Number Application Nodes                                     | *(wird von ft ermittelt)* |                               |
|                                                              |                        | RAM/Applikation Node                                         | *(wird von ft ermittelt)* |                               |
|                                                              |                        | vCPU/Applikation Node                                        | *(wird von ft ermittelt)* |                               |
|                                                              |                        | Persistant Storage Amount HighIOPS                           | *(wird von ft ermittelt)* |                               |
|                                                              |                        | (DB,  Store and BUS) in GB                                   | *(wird von ft ermittelt)* |                               |
|                                                              |                        | POD  Storage Amount in GB                                    | *(wird von ft ermittelt)* |                               |
|                                                              |                        |                                                              |                           |                               |
|                                                              |                        | **Onboarding/Installation**                                  |                           | einmalige Kosten              |
|                                                              |                        | Übernahme des  Basissystems                                  |                           |                               |
|                                                              |                        | Einrichtung der  Managementverbindung                        |                           |                               |
|                                                              |                        | Einbindung der  fiskaltrust.Portal Verbindung                |                           |                               |
|                                                              |                        | Provisionierung der Basis PODs                               |                           |                               |
|                                                              |                        | Tests und Freigabe                                           |                           |                               |
|                                                              |                        |                                                              |                           |                               |
|                                                              |                        | **Management / SLA 99,0% Jährlich für von ft gelieferte Container basierend auf Azure Arc** |                           | monatliche Kosten             |
|                                                              |                        | Übertragung von Logs und Telemetrie                                                   |                           |                               |
|                                                              |                        | Beheben von Deployment issues                                |                           |                               |
|                                                              |                        | Support                                                      |                           |                               |
|                                                              |                        | Telefon Hotline Mo-Fr  09:00h-15:00h                         |                           |                               |
|                                                              |                        | Störungsmeldung online per Formular                          |                           |                               |
|                                                              |                        | Reaktionszeit: 4h                                            |                           |                               |
|                                                              |                        | Störungsbehebung: best effort, innerhalb 24h - nicht garantiert |                           |                               |
|                                                              |                        |                                                              |                           |                               |
|                                                              |                        | **Bereitgestellte Produkte**                                 |                           | monatliche Kosten pro Cashbox |
|                                                              |                        | Custom Produkt-Bundle mit TSE as a Service  & Archiv         |                           |                               |

Für weitere Informationen oder ein individuelles Angebot wenden sie sich bitte an den fiskaltrust.Support (info@fiskaltrust.de).
