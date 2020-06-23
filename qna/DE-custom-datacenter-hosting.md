## Question

Wir arbeiten lediglich mit Eingabegeräten /Terminals, die keine Offlinefunktionalität bieten und nur mit einer Verbindung zum Rechenzentrum Aufzeichnungen anstoßen können. Die Aufzeichnungen erfolgen ausschließlich auf den Servern im Rechenzentrum (Cloud). Damit ist das Rechenzentrum das Operational Environment. Muß ich in meinem Rechenzentrum eine TSE betreiben?

## Metadata tags

lang-en, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

Die fiskaltrust Lösung kann bei Bedarf unter bestimmten Rahmenbedingungen auch im eigenen Rechenzentrum betrieben werden.

### Voraussetzungen

- Vertragslaufzeit: 3 Jahre 
- Sie stellen einen dedizierten Kubernetes Cluster je Rechenzentrum bzw. beauftragen einen Dritten mit deren Bereitstellung
- fiskaltrust übernimmt & konfiguriert den bereitgestellten Cluster
- fiskaltrust übernimmt das Management des Clusters inkl. SLA
- fiskaltrust stellt individuelle Produktbundles pro Cashboxen zur Verfügung

### Detailinformationen

| Leistungen Kunde                                             |                        | Leistungen fisklatrust                                       |                           | Kosten                        |
| ------------------------------------------------------------ | ---------------------- | ------------------------------------------------------------ | ------------------------- | ----------------------------- |
| **gewarteter  Kubernetes Cluster** im Rechenzentrum *(Eigenleistung oder wahlweise  Beauftragung an Dritte)* |                        |                                                              |                           | unbekannt                     |
| Major Version: Update nach Absprache mit Serviceprovider (Breaking Changes) |                        |                                                              |                           |                               |
| Minor Version: Spätestens 60 Tage ab Release muss die Minor Version am Cluster zur Verfügung stehen |                        |                                                              |                           |                               |
| Patch Version: Spätestens 30 Tage ab Release muss die Minor Version am Cluster zur Verfügung stehen |                        |                                                              |                           |                               |
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
|                                                              |                        | Persistant  Storage Amount HighIOPS                          | *(wird von ft ermittelt)* |                               |
|                                                              |                        | (DB,  Store and BUS) in GB                                   | *(wird von ft ermittelt)* |                               |
|                                                              |                        | POD  Storage Amount in GB                                    | *(wird von ft ermittelt)* |                               |
|                                                              |                        |                                                              |                           |                               |
|                                                              |                        | **Onboarding/Installation**                                  |                           | einmalige Kosten              |
|                                                              |                        | Übernahme des  Basissystems                                  |                           |                               |
|                                                              |                        | Einrichtung der  Managementverbindung                        |                           |                               |
|                                                              |                        | Einbindung der  fiskaltrust.portal Verbindung                |                           |                               |
|                                                              |                        | Provisionierung der  Basis PODs                              |                           |                               |
|                                                              |                        | Tests und Freigabe                                           |                           |                               |
|                                                              |                        |                                                              |                           |                               |
|                                                              |                        | **Management / SLA 99,0% Jährlich**                          |                           | monatliche Kosten             |
|                                                              |                        | Monitoring                                                   |                           |                               |
|                                                              |                        | Einspielen von Patches                                       |                           |                               |
|                                                              |                        | Updates von Kubernetes  aktivieren (mind. vierteljährlich)   |                           |                               |
|                                                              |                        | Beheben von Deployment  issues                               |                           |                               |
|                                                              |                        | Support                                                      |                           |                               |
|                                                              |                        | Telefon Hotline Mo-Fr  09:00h-15:00h                         |                           |                               |
|                                                              |                        | Störungsmeldung online per  Formular                         |                           |                               |
|                                                              |                        | Reaktionszeit: 4h                                            |                           |                               |
|                                                              |                        | Störungsbehebung: best effort,  innerhalb 24h - nicht garantiert |                           |                               |
|                                                              |                        |                                                              |                           |                               |
|                                                              |                        | **Bereitgestellte Produkte**                                 |                           | monatliche Kosten pro Cashbox |
|                                                              |                        | Custom Produkt-Bundle mit TSE as a Service  & Archiv         |                           |                               |

Für weitere Informationen oder ein individuelles Angebot wenden sie sich bitte an den fiskaltrust.Support (info@fiskaltrust.de).