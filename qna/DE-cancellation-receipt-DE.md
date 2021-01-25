## Question
Wie ist die das Storno von Vorgängen und Positionen im iPOS abzubilden?

## Question
Wie werden Belege storniert?

## Metadata tags
lang-de, market-de, middleware, PosCreator, PosDealer

## Answer

### Storno von Vorgängen und Positionen
- Storno von Vorgängen
    - Nachträgliche Vorgangsstornierung (DSFinV-K 4.2.2) 
        - Der Stornobeleg ist ein separater Beleg, der durch BON_STORNO = „1“ zu kennzeichnen ist. Die Vorzeichen von MENGE, BRUTTO, NETTO sowie UST sind umzukehren. 
        Zur eindeutige Identifizierung ist cbPreviousReceiptReferenze entsprechend zu verwenden.           
        - Der neu zu erstellende Stornobeleg ist mit dem ReceiptCaseFlag „reverse/voided receipt“, 0x0000000000040000 zu kennzeichnen. 
        - Dadurch wird der Beleg im DSFinV-K mit BON_STORNO = „1“ gekennzeichnet.
        - Die Aussage in DSFinV-K S. 80, dass BON_STORNO nicht verwendet werden darf, wenn eine negative Rückbuchung des Vorgangs erfolgt ist dahingehend korrekt, da sich dies auf den ursprünglichen zu stornierenden Beleg bezieht.
    - Sofortige Vorgangsstornierung (DSFinV-K 4.2.1) 
        - Die sofortige Vorgangsstornierung erfolgt ausschließlich wie die „Nachträgliche Vorgangs-Stornierung“.
        - Da fiskaltrust keine „alte“ Kassen unterstützt, die noch nicht mit einer TSE verbunden sind, wird die sofortige Vorgangsstornierung durch nachträgliches Markieren des Belegs mit dem Storno-Flag „BON_STORNO“ durch das ft.Interface NICHT unterstützt.
        - Der Vorgangstyp „AVBelegstorno “ kann daher ebenso nicht verwendet werden.
    - Storno von Positionen (DSFinV-K 4.2.3) 
        - Ebenso wie bei der Vorgangsstornierung ist ein zusätzlicher Positionsdatensatz zu erstellen Die Vorzeichen von MENGE, BRUTTO, NETTO sowie UST sind umzukehren.
        - Die Stornierung von Positionen durch nachträgliches Markieren der Position mit dem Storno-Flag „P_STORNO“ darf nicht verwendet werden.

### DSFinV-K
#### Darstellung besonderer Vorgänge
##### 4.2.1 Sofortige Vorgangsstornierungen
Eine sofortige Vorgangsstornierung kommt nur bei Systemen in Betracht, die nicht mit einer TSE verbunden sind (z.B. Kassen, die mit Übergangsregelung bis 31.12.2022 ein-gesetzt werden können), wenn ein Kassenbeleg erzeugt wurde, das Geschäft aber unmittelbar nicht zustande kommt (z. B. weil der Kunde das Geld vergessen hat). Aus-schließlich in diesen Fallkonstellationen kann ein Sofortstorno vorgenommen werden.
Die Darstellung kann auf zwei Arten erfolgen:
* BON_STORNO wird auf „1“ gesetzt, ansonsten bleibt der Datensatz unverändert (insbesondere wird kein zweiter Datensatz erzeugt; nur in diesen Fällen darf der Vorgangstyp „AVBelegstorno“ genutzt werden), oder
* Vorgehensweise wie nachfolgend zu „Nachträgliche Vorgangs-Stornierung“ dargestellt.
##### 4.2.2 Nachträgliche Vorgangs-Stornierungen
Für die nachträgliche Stornierung eines Vorgangs gelten besondere Vorschriften:
* Der Ursprungsbeleg bleibt unverändert.
* Der Stornobeleg ist ein separater Beleg, der durch BON_STORNO = „1“ zu kennzeichnen ist. Der Vorgangstyp ist in diesem Fall (analog zu dem Ursprungsbeleg) mit „Beleg“ anzugeben. Die Vorzeichen sind umzukehren.
Um einen Bezug zum ursprünglichen Vorgang zu ermöglichen, sind spezielle Referenz-Felder zur eindeutigen Identifizierung in der DSFinV-K enthalten.
Aus umsatzsteuerlicher Sicht gehört eine Stornorechnung zum Bereich der Rechnungskorrekturen. Ebenso wie für Rechnungen gelten auch für Rechnungskorrekturen die gesetzlichen Pflichtangaben nach § 14 Abs. 4 UStG.

##### 4.2.3 Stornierung von Positionen
Vorzunehmende Stornierungen auf Positionsebene finden im Bereich der Bonpos statt.
Dabei ist entweder in der ursprünglichen Position P_STORNO auf „1“ zu setzen (ohne eine zweite Datenzeile zu erstellen) oder ein zusätzlicher Positionsdatensatz zu erstellen, bei dem MENGE, BRUTTO, NETTO sowie UST mit negativen Vorzeichen dargestellt werden. In diesem Fall darf P_STORNO nicht auf „1“ gesetzt werden.
Sobald die Transaktion in der TSE signiert ist, darf das Feld P_STORNO nicht mehr verwendet werden.

##### 4.2.5 Vorgänge mit Negativpositionen
Kommen in einem Bon Positionen mit negativem Vorzeichen durch z. B. Warenrücknahmen, Rabatte oder Positionsstornos vor, so erfolgt eine Darstellung wie bei einem normalen Verkauf. Lediglich das Vorzeichen für das Feld MENGE ändert sich (und damit automatisch das Vorzeichen von POS_BRUTTO, POS_NETTO und POS_UST in der Datei Bonpos_UST, vgl. 3.1.1.1).

##### Anhang B BON_TYP (Vorgangstyp)
Es werden folgende Vorgangstypen (Bontypen) unterschieden:
…
* AVBelegstorno
AVBelegstorno
Der Vorgangstyp „AVBelegstorno“ kennzeichnet alle Vorgänge, die vollständig storniert werden. Die Verwendung ist nur innerhalb eines Kassenabschlusses zulässig. Der Einsatz von AVBelegstorno ist kassensystemabhängig und für die Kassensysteme gedacht, die anstatt einer Gegenbuchung nur ein Storno-Kennzeichen am Originalbeleg verwenden.
Der AVBelegstorno zeigt eine vollständige Stornierung des Originalbelegs an, so dass sämtliche Beträge nicht mehr im Kassenabschluss berücksichtigt werden.
Hinweis: Mit dem AVBelegstorno ist nicht die negative Darstellung eines Beleges gemeint. Hierfür muss weiterhin der Vorgangstyp „Beleg“ mit umgekehrten Vorzeichen und ohne Storno-Kennzeichen genutzt werden. Zu beachten ist in diesen Fällen, dass eine Referenz auf den ursprünglichen Vorgang erfolgen muss.
Achtung! Sobald eine TSE an einer Kasse eingesetzt wird, ist es technisch nicht mehr möglich, den Vorgangstyp „AVBelegstorno“ korrekt zu verwenden, da jeder Beleg schon vor dem Setzen des Storno-Kennzeichens bereits durch die TSE signiert wurde. Insofern ist ein nachträgliches „Nullen“ eines Beleges nicht mehr möglich.

#### Kapitel: Einzelaufzeichnungsmodul
##### 11. Datei “Bonkopf” (transactions.csv)
###### BON_STORNO
Feldtyp: Zeichen
Feldlänge: 1
Kurzbeschreibung: Die Aktivierung (Wert: „1“) dieses Feldes kennzeichnet die Stornierung eines einzelnen Beleges. Eine Angabe ist zwingend erforderlich („0“ oder „1“). BON_STORNO darf nur auf „1“ gesetzt werden, wenn ein kompletter Vorgang sofort und ohne Gegenbuchung „aufgehoben“ wird, nicht aber, wenn eine negative Rückbuchung des Vorgangs erfolgt. Vgl. hierzu Ausführungen zu Tz. 4.2.1 und 4.2.2.

###### P_STORNO
Feldtyp: Zeichen
Feldlänge: 1
Kurzbeschreibung: Positionsstorno-Kennzeichnung. Bei Aktivierung des Feldes (Wert = „1“) handelt es sich um eine (sofort während der Erfassung) stornierte Position.

#### Anhang I Definition “Art” und “Daten” des Vorgangs; QR-Code
##### 1. Definition der Datenstrukturen zur Übergabe an das Sicherheitsmo-dul
…
###### Kassenbeleg
processType: Kassenbeleg-V1
processData: `<Vorgangstyp>^<Brutto-Steuerumsätze>^<Zahlungen>`
Trennzeichen: ^ (Unicode U+005E)
`<Vorgangstyp>`:
Der Vorgangstyp laut DSFinV-K kann folgende Werte annehmen:

* AVBelegstorno

