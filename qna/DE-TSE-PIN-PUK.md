## Question

Wie kann ich die PIN für die TSE angeben?

## Question

Wie kann ich die PIN für eine neue TSE setzen?

## Question

Wie kann ich die unterschiedliche PINs pro TSE vergeben?

## Question

Kann ich die PUK für die TSE vergeben oder angeben?

## Metadata tags

lang-de, market-de, portal, security, PosCreator, PosDealer

## Answer

Für die Cryptovision, Swissbit und Diebold Nixdorf Hardware TSEs können mit Hilfe des ft.Portals diverse PINs durch den Nutzer gesetzt oder angegeben werden. Dies geschieht durch die Konfiguration der entsprechenden SCU (TSE Signatur-Erstellungs-Einheit / Signature Creation Unit) im ft.Portal. Die PUK kann nicht explizit durch den Nutzer im ft.Portal angegeben oder gesetzt werden. 

#### PINs bei Inbetriebnahme einer neuen TSE vergeben

Bei einer neuen, noch nicht initialisierten TSE können optional vor Inbetriebnahme der TSE PINs für die TSE expizit in der SCU Konfiguration gesetzt werden (zum Beispiel mit dem Parameter `AdminPIN` kann die admin PIN gesetzt werden). Werden PINs nicht explizit über Parameter gesetzt, so verwendet das System gleichbleibende Default-PINs. Werden PINs durch die Konfiguration vor der ersten Inbetriebnahme explizit gesetzt, so müssen für alle weiteren SCUs die auf diese TSE in Zukunft zugreifen wollen die gleichen PINs in der SCU Konfiguration angegeben werden.  

#### PINs einer TSE ändern

Mit dem fiskaltrust System ist es zur Zeit nicht möglich die PINs einer bereits in Betrieb genommenen TSE zu ändern. Es ist lediglich möglich PINs für die erste Inbetriebnahme der TSE zu setzen.

#### PINs für eine bereits in Betrieb genommene TSE angeben

Wurde die TSE bereits in Betrieb genommen, so müssen die bei der Inbetriebnahme explizit gesetzten PINs bei jeder weiteren SCU Konfiguration angegeben werden, die auf diese TSE zugreifen möchte. 

Wurde die TSE ohne explizit gesetzte PINs durch die fiskaltrust.Middelware in Betrieb genommen - es wurden also Default-PINs verwendet - so müssen keine weiteren Angaben zu den PINs in den darauf folgenden SCU Konfigurationen zu dieser TSE vorgenommen werden. 

Wurde die TSE durch ein Fremdsystem zum ersten Mal in Betrieb genommen, so müssen die dabei verwendeten PINs in der SCU Konfiguration für diese TSE mit hilfe des ft.Portals angegeben werden.

Im folgenden finden Sie Angaben darüber, welche PINs pro TSE genau mit Hilfe der SCU Konfiguration gesetzt oder angegeben werden können:

- [Cryptovision TSE Interoperabilität](https://docs.fiskaltrust.cloud/docs/product-description/germany/products-and-services/caas/features/basics/tse/cryptovision) <br/>
- [Swissbit TSE Interoperabilität ](https://docs.fiskaltrust.cloud/docs/product-description/germany/products-and-services/caas/features/basics/tse/swissbit) <br/>
- [Diebold Nixdorf TSE Interoperabilität ](https://docs.fiskaltrust.cloud/docs/product-description/germany/products-and-services/caas/features/basics/tse/diebold-nixdorf) <br/>
