## Question
Gibt es Hinweise zur Anlage der Stammdaten?

## Question

Welche häufigen Fehler gibt es bei der Eingabe der FinanzOnline-Zugangsdaten?

## Question

Was sind die häufigsten Fragen zu Bestellung und Lieferung über den fiskaltrust.Shop?

## Question

Wie kann ich Probleme beim Login ins fiskaltrust.Portal lösen?

## Question

Welche Technische Probleme können auftreten, die ich selbst lösen kann?

## Question

Was muss ich tun wenn sich die Adresse meiner Firma ändert?

## Question

Was muss ich tun wenn sich die Steuernummer meiner Firma ändert?

## Question

Was muss ich tun wenn sich der Firmenname ändert?

## Question

Was muss ich tun wenn sich die UID Nummer meiner Firma ändert?

## Question

In welchen Fällen benötige ich einen oder mehrere fiskaltrust-Accounts?

## Metadata tags
lang-de, market-at, middleware, portal, consulting, documentation, security, PosCreator, PosDealer, PosOperator, Consultant

## Answer

### Gibt es Hinweise zur Anlage der Stammdaten?

#### Was ist ein Suffix?

Ein Titel welcher hinter dem Nachnamen angefügt wird (Bsp. MBA, MSc, MA usw)

#### Was ist eine GLN – Global Location Number?

Die GLN kann als Ordnungsbegriff zur Personalisierung einer Signaturerstellungseinheit (SEE) verwendet werden.Wir empfehlen hierzu jedoch, wenn vorhanden, die UID zu verwenden. In diesem Fall muss die GLN nicht ausgefüllt werden.GLN-Suche:

- www.gepir.at/de/home
- https://firmen.wko.at
- In FinanzOnline/Eingaben/Registrierkassen

#### Was kann ich bei einem Fehler beim Datacheck der Firmenbuchnummer machen?

- Die FN ist für fiskaltrust derzeit irrelevant und muss daher nicht ausgefüllt werden.
- Ist die Nummer im korrekten Format? Bsp. 123456x
- Abfrage beim Firmenbuch eventuell derzeit nicht möglich.

#### Was kann ich bei einem Fehler beim Datacheck der UID-Nummer machen?

Meist stimmt der Firmenname in den Stammdaten (oberstes Feld) nicht mit dem beim Finanzamt zu dieser UID-Nummer hinterlegten Namen überein.In der Fehlermeldung steht der korrekte Name, dieser muss im Feld „Firmenname“ eingetragen, die Eingabe gespeichert, und ein neuer Datacheck gemacht werden. Die Zahl in ( ) zeigt die Anzahl der nicht korrekten Zeichen an. Hierbei kann es sich auch um Leerzeichen handeln.Der Hinweis unter dem Eingabefeld ist zu beachten.

### Welche häufigen Fehler gibt es bei der Eingabe der FinanzOnline-Zugangsdaten?

**Es gibt unterschiedliche Fehlermeldungen bei der Eingabe Portal|“Firm“|AT FinanzOnline Meldungen:**

„Der Benutzer ist kein Webuser“

Finanzonline gemäß dieser Anleitung angelegt werden. [161108-BMF_Handbuch_Registrierkassen.pdf](https://www.fiskaltrust.at/wp-content/uploads/2015/08/161108-BMF_Handbuch_Registrierkassen.pdf) (ab Seite 54).

#### Unsere Kurzanleitung:

Finanzonline -> Eingaben -> Registrierkassen -> Anlegen eines Benutzers für Registrierkassen Webservice.
Benutzer und PIN sind frei wählbar.
Die Teilnehmer ID ist immer dieselbe für dieses Unternehmen und wird, nach erfolgreicher Eingabe, direkt am Bildschirm angezeigt.

„Ungültige Zugangskennungen“

Falsche Zugangsdaten, kontrollieren und ggf. erneut versuchen

„Der Benutzer ist gesperrt“

Achtung! Nach 3 misslungenen Anmeldeversuchen in FinanzOnline wird der FinanzOnline-Benutzer gesperrt und muss über https://finanzonline.at |Admin|Benutzer einzeln wieder entsperrt werden.

### Was sind die häufigsten Fragen zu Bestellung und Lieferung über den fiskaltrust.Shop?

#### Wieso fehlen manche Artikel (Sorglospakete) im Shop?

Erst nach Vertrags-Unterzeichnung der Zuordnung als Registrierkassenbetreiber in Portal|Übersicht|Schieberegler bei Registrierkassenbetreiber auf „ON“ hat man Einblick in alle Produkte im Shop.

#### Wann erhalte ich mein Sorglos Produkt? Wann wird dieses aktiviert?

Das Paket ist automatisch für sie im Portal aktiv, sobald Sie die Bestellung bezahlt haben.

#### Wann wird meine Bestellung geliefert?

Im Portal|Shop|Lieferscheine kann selbst kontrolliert werden ob und wann die Ware bereits versendet wurde.
Die Trackingnummer im Lieferschein kann man auf GLS Tracking nachverfolgen.
Achtung: es passiert immer wieder dass fälschlicherweise Bestellungen in der Sandbox getätigt werden, hier ist eine Kontrolle im Portal erforderlich.

### Wie kann ich Probleme beim Login ins fiskaltrust.Portal lösen?

#### „Sie haben nicht die Berechtigung um sich in diesem Bereich anzumelden“

- Variante 1. Dieser Kontakt (Mailadresse) wurde als Mitarbeiter einer Firma eingeladen und hat nicht die notwendigen Berechtigungen erhalten um sich anmelden zu können.
  Sein Hauptkontakt muss ihm die Berechtigungen erteilen.
- Variante 2. Sie haben sich selbst registriert allerdings bei der Anmeldung die Seite mit den Firmendaten übersprungen, in diesem Fall wird ein Kontakt angelegt aber keine dazu passende Firma.
  Kontaktieren Sie bitte unseren Support.

#### Ihr Login ist gesperrt

Der Login im Portal ist so lange gesperrt, bis die Mailadresse bestätigt wurde. Hierzu erhalten Sie ein Mail mit einem Link welchem Sie folgen müssen. Sollten Sie dieses Mail versehentlich gelöscht haben, kontaktieren Sie bitte unseren Support.

#### Ich kann mich nicht anmelden / Der Benutzer ist nicht bekannt

Kontrollieren Sie bitte, dass Sie die korrekte Mailadresse (Benutzername) zur Anmeldung verwenden. Benutzer welche bisher nur in der fiskaltrust-Sandbox registriert waren, sind beispielsweise nicht automatisch berechtigt sich im Echtportal anzumelden.

### Welche Technische Probleme können auftreten, die ich selbst lösen kann?

Viele Informationen und technische Hilfestellungen finden Sie in unserer [Entwickler-Dokumentation](https://docs.fiskaltrust.cloud) oder in der Wissensdatenbank im [fiskaltrust.Portal](https://portal.fiskaltrust.at).

Hier ein Auszug:

[Cashbox erstellen](https://portal.fiskaltrust.at/KBArticle/Search?search=KBA-01094-Q1P4Y1)
[REST FAQ](https://portal.fiskaltrust.at/KBArticle/Show/KBA-01093-P0P0B9)
[Portal Anmeldung](https://portal.fiskaltrust.at/public/FindKBArticles/KBA-01095-V0N7F4)
[Ausfall der Kasse, der Sicherheitseinrichtung
](https://portal.fiskaltrust.at/KBArticle/Show/KBA-01102-S2M4P5)[Firewall-Einstellungen // Ausfall der Internetverbindung, der Sicherheitseinrichtung](https://portal.fiskaltrust.at/KBArticle/Search?search=dns#faq-KBA-01107-X6R2P6)
[Windows XP](https://portal.fiskaltrust.at/KBArticle/Show/KBA-01023-T1N7B1)
[Dienst startet nicht](https://portal.fiskaltrust.at/KBArticle/Show/KBA-01109-T8C1G6)
[Dienst mit SQL Server (EF)](https://portal.fiskaltrust.at/KBArticle/Show/KBA-01111-Y4L1G6)
[Smartcard und Leser Probleme](https://portal.fiskaltrust.at/KBArticle/Search?search=KBA-01116-N8Y7S7)

Sollten Sie Ihr Problem nicht in der Wissensdatenbank finden, so senden Sie bitte ein Mail mit einer möglichst genauen Beschreibung des Problems an [info@fiskaltrust.at](mailto:info@fiskaltrust.at) unsere Techniker werden sich so rasch wie möglich melden !

Bitte haben Sie Verständnis, das spezifische PC Probleme, die auf einzelnen Geräten in speziellen Konfigurationen auftreten derzeit von uns nur eingeschränkt bzw. entgeltlich behandelt werden können.

### Was muss ich tun wenn sich die Adresse meiner Firma ändert?

Die Adresse sollte im https://portal.fiskaltrust.at in Ihren Stammdaten aktualisiert werden.

### Was muss ich tun wenn sich die Steuernummer meiner Firma ändert?

Wenn Ihr Signaturzertifikat auf Ihre Steuernummer personalisiert wurde, muss ein neues erworben werden.

Wenn Ihr Signaturzertifikat auf Ihre UID Nummer personalisiert wurde, so können Sie dies weiterhin nutzen.

### Was muss ich tun wenn sich der Firmenname ändert?

Der Firmenname sollte im portal.fiskaltrust.at in Ihren Stammdaten aktualisiert werden.

### Was muss ich tun wenn sich die UID Nummer meiner Firma ändert?

Wenn ein fiskaltrust.Produkt auf die UID-Nummer personalisiert wurde, muss man bei einer Änderung ein neues Paket/Pakete erwerben. 

Falls sich das Unternehmen geändert hat, ist ein neuer Account für die neue Firma anzulegen. Hier wird in die Stammdaten die neue UID Nummer eingetragen und ein neues Produkt erworben. 

Bitte beachten Sie, dass Sie mit einem neuen Startbeleg die Kasse aktivieren sowie die gesetzlich vorgeschrieben Meldungen und Belegprüfungen durchführen. Die nicht mehr benötigten Produkte können anschließend gekündigt werden.

### In welchen Fällen benötige ich einen oder mehrere fiskaltrust-Accounts?

#### Wann sollte ich einen zweiten fiskaltrust Account anlegen?

*Dies ist nur erforderlich wenn sich aufgrund einer betrieblichen Veränderung die UID-Nummer des Unternehmens ändert.*

#### Benötige ich für unterschiedliche Kassensysteme zwei unterschiedliche Accounts?

*Nein, um sich im bestehenden Account mit einem neuen Händler zu verbinden können Sie diesen im Menü „Kassenbetreiber“ suchen.*

#### Benötige ich für unterschiedliche Standorte zwei unterschiedliche Accounts?

*Nein, für zwei Standorte des selben Unternehmens nutzen Sie bitte einen Account.*

**Profitipp:**

Bei mehreren Accounts für **ein** Unternehmen kann es aufgrund der Namensgleichheit der Registrierkassen zu Komplikationen kommen.
