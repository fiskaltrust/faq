## Question

Was passiert wenn eine TSE ausfällt?

## Question

Kann man bei Ausfall oder Nichterreichbarkeit einer TSE (z.B. bei einer Cloud-Lösung oder einer zentralen TSE im eigenen Rechenzentrum) auf eine zweite TSE zugreifen?

## Metadata tags

lang-de, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

Bei einem Ausfall der TSE darf mit der Kasse weiter gearbeitet werden.

Die fiskaltrust.Middleware (ft.MW) signalisiert die Nichterreichbarkeit der TSE über den Service-Status `ftState = 0x4445000000000002`. Siehe dazu: [docs.fiskaltrust](https://docs.fiskaltrust.cloud/docs/poscreators/middleware-doc/germany/reference-tables/ftstate).

Die lokale ft.MW speichert dennoch in der lokalen Datenbank die erhaltenen Requests und kann somit alle Funktionen – insbesondere DSFinV-K-Export, PosArchiv, AKO, usw. weiter lückenlos und sicher zur Verfügung stellen.

Nach Nr. 1.3 des AEAO zu § 146a muss ein elektronisches Aufzeichnungssystem oder eine Gruppe elektronischer Aufzeichnungssysteme bei störungsfreier Verwendung genau einer zertifizierten technischen Sicherheitseinrichtung zugeordnet sein. Im Falle einer Störung darf also auf eine zweite TSE zugegriffen werden.

Nach Wiederherstellung der Kommunikation mit der TSE ist das Senden eines Nullbeleges durch die Kasse an die ft.MW erforderlich. Mit diesem Nullbeleg versucht die Middleware den ordnungsgemäßen Betrieb mit der TSE wieder herzustellen. Wir empfehlen, diesen Nullbeleg durch einen Benutzereingriff zu veranlassen, da hierdurch der laufende Betrieb der Kasse möglichst wenig beeinflusst wird. Falls die Kommunikation mit der ft.MW weiterhin nicht möglich ist (erneut `ftState = 0x4445000000000002`), dann muss der Vorgang, ein Nullbeleg zu senden, wiederholt werden, bis die Kommunikation mit der TSE wieder ordnungsgemäß erfolgt.
