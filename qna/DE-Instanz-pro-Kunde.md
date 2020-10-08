## Question
Muss ich die fiskaltrust.Middleware für jeden Standort (Outlet) in einer eigenen CashBox im Portal anlegen?

## Metadata tags
lang-de, market-de, middleware, PosCreator, PosDealer

## Answer
Ja unbedingt. Es ist für eine rechtskonforme Verwendung notwendig, dass **jeder Standort** bei **jeder rechtlichen Einheit** zumindest eine eigene Instanz der fiskaltrust.Middleware verwendet und **die jeweils für diesen Standort konfigurierte Instanz beim richtigen Kunden nur ein mal** eingesetzt wird. Es können jedoch mehrere Kassen (Terminals) an diesem Standort diese Instanz verwenden. Um den Rollout für viele Kunden mit grundsätzlch gleicher Konfiguration zu vereinfachen, können Vorlagen (Templates) im fiskaltrust.Portal angelegt werden, die als Basis dienen.
https://docs.fiskaltrust.cloud/doc/productdescription-de-doc/for-posdealers/02-pre-sales/automatisierter-rollout.html 
