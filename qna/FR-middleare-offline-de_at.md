## Question
Wie reagiere ich auf den Offline-Modus?

## Metadata tags
lang-de, lang-at, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Wenn der Beleg nicht vom fiskaltrust.SecurityMechanism signiert werden kann, muss das POS-System **mode dégradé** auf den Beleg drucken.

Wenn der fiskaltrust.Middleware die Belege wieder signieren kann, müssen alle diese nicht-signierten Belege (manuell oder automatisch) eingegeben, an den fiskaltrust.SecurityMechanism gesendet und erneut als reguläre Belege gedruckt werden. Dann müssen die nicht-signierten und die signierten Belege zusammen archiviert werden.

Es empfiehlt sich, im technischen Protokoll eine Nachricht mit folgendem Inhalt zu senden:

```JSON
{
  "code": 70,
  "description": "Start of degraded mode",
  "moment": "2020-03-22T06:10:52.6395741Z"
}
```

Damit wird der Beginn des Offline-Modus dokumentiert. Wenn die normale Funktion wieder hergestellt ist, sollte die folgende Nachricht an das technische Protokoll gesendet werden, um dies ebenfalls zu dokumentieren.
```JSON
{
  "code": 120,
  "description": "End of degraded mode",
  "moment": "2020-03-22T09:23:22.6015741Z"
}
```
