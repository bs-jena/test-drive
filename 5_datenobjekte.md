# Datenobjekte in Salesforce {#datenobjekte}  
Die Anwendung JustOn Connector for DATEV fügt Ihrer Salesforce-Umgebung einige neue Datenobjekte hinzu. Diese Objekte ermöglichen die Speicherung des Belegs, die Übertragung der Daten an DATEV und die Prüfung über den Verlauf der Übertragung.
Die technischen Benennungen der Objekte sind auf englisch und etwas anders als in der Oberfläche angezeigt.
 

## Accounting Document (= Beleg) {#accounting-document}
Ein Datensatz der Klasse Accounting Document repräsentiert eine Ein- oder Ausgangsrechnung oder einen Kassenbeleg. 

Die Datenstruktur ist dabei wie folgt:
Ein Accounting Document enthält
* Belegdaten wie das Datum des Belegs, die Rechnungsnummer und die Währung und für Ein- und Ausgangsrechnungen auch Geschäftspartnerdaten (Name, Ort, Kundennummer und Bankdaten).
* Anhänge am Accounting Document, die das Belegbild repräsentieren (siehe [Beschreibung zu Reiter "Belege" - Belegbilder](2-1_reiter-belege.md#beleg-belegbilder))
* Mindestens ein Accounting Detail (= Belegposition)

* Wurde bereits eine Datenübertragung für eine oder mehrere Buchungspositionen des Belegs gemacht, so ist der letzte Accounting Job (Datenübertragung) mit dem Beleg verknüpft.


Einige Felder haben dabei eine spezielle Bedeutung:

| **Feldname** | **Mögliche Werte** | **Beschreibung** |
| --- | --- | --- |
| **Datensatztyp** | <ul><li>accountsPayableLedger</li><li>accountsReceivableLedger</li><li>cashLedger</li></ul> | Art des Belegs (Eingangsrechnung, Ausgangsrechnung, Kasse). Über den Typ werden Felder und Feldausprägungen, Validierungen und die Erzeugung der Datenstruktur für die Übertragung an DATEV bestimmt. <br/><br/>Der Name des Feldes ist nicht änderbar, weil es sich um einen Recordtype handelt, mit dem die manuelle Anlage von Belegen typspezifisch abgebildet wird.|
| **Accounting Job** | ID und Link auf Datenübertragung | Verknüpfung mit der Datenübertragung, falls für eine oder mehrere Belegpositionen des Belegs bereits eine Datenübertragung angelegt wurde (damit ist keine Aussage über den Status der Datenübertragung getroffen!) |
| **Currency Code** | Alle auswählbaren Werte |	Das Währungskürzel muss immer gesetzt sein. Wenn die Salesforce Organisation, innerhalb der Sie "JustOn Connector for DATEV" nutzen Mehrwährungsfähigkeit aktiviert hat, so muss dieses Feld denselben Wert enthalten wie der CurrencyIsoCode in Salesforce. |
| **Document Amount** | Wird berechnet aus den Beträgen der Accounting Details | Gesamtsumme des Accounting Documents |  
| **Locked** | true oder false | Gibt an, ob der Beleg geändert werden kann oder nicht. Dieses Feld ist true wenn der Beleg aus einem Vorsystem transfveriert wurde oder manuell angelegte Belege (Achtung, nur zu Dummy-Zwecken erlaubt!) mit einer Datenübertragung verknüpft sind und gerade an DATEV übertragen werden oder erfolgreich übertragen wurden. |
| **From Third Party** | true oder false |  Gibt an, ob der Beleg aus einem Vorsystem an JustOn Connector for DATEV transferiert wurde. |

Die Anhänge am Beleg repräsentieren das Belegbild. Sie werden mit der ersten Belegposition des Belegs an DATEV übertragen. Für die Übertragung an DATEV sollten Anhänge nicht größer als 4 MB sein und bestimmten Datentypen entsprechen (siehe XY).

Es gibt zahlreiche Validierungsregeln für Accounting Documents (Belege). Diese stellen sicher, dass die Daten den Anforderungen der DATEV an die Datenübertragung entsprechen.


## Accounting Detail (= Beleposition) {#accounting-detail}
Ein Beleg hat mindestens eine, kann aber auch mehrere Belegpositionen haben. Diese werden in verschiedenen Accounting Details abgebildet.

Accounting Details werden über ein Accounting Document gruppiert. Alle Accounting Details eines Accounting Document müssen deshalb vom selben Typ (Beleg-Art) sein. Jedes Accounting Detail (Belegposition) muss genau einem Accounting Document (Beleg) und kann genau einem Accounting Job (Datenübertragung) zugeordnet sein.

Hat ein Accounting Document Accounting Details mit verschiedenen Buchungsdatums, die zu verschiedenen Buchungsmonaten gehören, so können die Accounting Details nur in mehrern Accounting Jobs (Datenübertragungen) übertragen werden - einer pro Buchungsmonat.

Einige Felder haben eine spezielle Bedeutung:

| **Feldname** | **Mögliche Werte** | **Beschreibung** |
| --- | --- | --- |
| **Accounting Document** | ID und Link auf Accounting Document | Das Accounting Document, zu dem das Accounting Detail (Belegposition) gehört | 
| **Accounting Job** | ID und Link auf Datenübertragung | Verknüpfung mit der Datenübertragung, falls für die Belegposition bereits eine Datenübertragung angelegt wurde (damit ist keine Aussage über den Status der Datenübertragung getroffen!) |
| **Datensatztyp** | <ul><li>accountsPayableLedger</li><li>accountsReceivableLedger</li><li>cashLedger</li></ul> | Art des Belegs (Eingangsrechnung, Ausgangsrechnung, Kasse). Über den Typ werden Felder und Feldausprägungen, Validierungen und die Erzeugung der Datenstruktur für die Übertragung an DATEV bestimmt. <br/><br/>**Dieses Feld wird aus Accounting Document übernommen.**|
| **Accounting Period** | Datum vom Typ YYYY-mm | Monat, in dem die Belegposition gebucht werden soll |
| **Accounting Year** | Datum vom Typ YYYY | Das Wirtschaftsjahr, in dem die Belegposition gebucht werden soll |
| **Belegdatum** | Datum vom Typ dd.mm.YYYY| Belegdatum des Accounting Documents <br/><br/>**Dieses Feld wird aus Accounting Document übernommen.** |
| **Date** | Datum vom Typ dd.mm.YYYY | Datum zu dem das Accounting Detail angelegt wurde |
| **Buchungsdatum** | Datum vom Typ dd.mm.YYYY| Buchungsdatum des Accounting Details |

**Hinweis:** Wird ein Accounting Document (Beleg) gelöscht, so werden auch alle zugehörigen Accounting Details (Belegpositionen) gelöscht. Ein Accounting Detail kann nicht auf ein anderes Accounting Document umgeschlüsselt werden.

Viele Felder des Accounting Documents (Belegs) gelten auch für die zugeordneten Accounting Details (Belegpositionen). Damit sie nicht mehrfach angegeben werden müssen sind sie dem Accounting Document (Beleg) zugeordnet. 

Es gibt zahlreiche Validierungsregeln für Accounting Details (Belegpositionen). Diese stellen sicher, dass die Daten den Anforderungen der DATEV an die Datenübertragung entsprechen.

## Accounting Job (= Datenübertragung) {#accounting-job}

Accounting Job ist die Klasse für die Datenübertragung an DATEV. 

Einige Felder haben eine spezielle Bedeutung:

| **Feldname** | **Mögliche Werte** | **Beschreibung** |
| --- | --- | --- |
| **ID der Datenübertragung** | Technische ID | **Wert aus dem DATEV-Rechenzentrum**: Gibt die technische ID der Übertragunng im DATEV-Rechenzentrum an. |
| **Name des Rechnungsordners / Kassenname** | TEXT(255) | **Wert aus dem DATEV-Rechenzentrum**: Gibt den Namen des Ordners / der Kasse aus Unternehmen online an, an den die Belegpositionen übertragen wurden. | | 
| **Beraternummer** | 4-7 stellige Zahl | **Wert aus dem DATEV-Rechenzentrum**: Nummer Ihres Steuerberaters  | 
| **Mandantennummer** | 1-5 stellige Zahl | **Wert aus dem DATEV-Rechenzentrum**: Ihre Mandantennummer | 
| **Unternehmensname** | TEXT | **Wert aus dem DATEV-Rechenzentrum**: Der Name Ihres Unternehmens so wie er in DATEV Unternehmen online hinterlegt ist | 
| **Salesforce Status**| <ul><li>Neu</li><li>In Vorbereitung</li><li>Vorbereitet zur Übertragung</li><li>In Übertragung</li><li>Transferiert</li></ul> | Der Status der Datenübertragung in Salesforce. |
| **DATEV Status** | <ul><li>Status offen</li><li>In Arbeit</li><li>Fertig</li><li>Abgebrochen</li><li>Zu Prüfen</li><li>Erfolgreich storniert</li><li>Storniert mit Fehler</li><li>Unknown</li></ul> | Gibt den Status der Datenübertragung bei DATEV an. Der Status kann nur manuell vom Nutzer über den Button "Status aktualisieren" aktualisiert werden. Daten+bertragungen können nur vom Nutzer gelöscht werden, wenn sie im Status "Open" sind. |
| **Belegposition** | ID und Link auf Accounting Detail | Verknüpfung mit den der Datenübertragung zugeordneten Belegpositionen. |

Um eine Daten an DATEV zu übertragen muss sich ein Salesforce-Nutzer über "JustOn Connector for DATEV" aktiv bei DATEV einloggen und Zugriff von "JustOn Connector for DATEV" auf DATEV freigeben. 

Weil diese Authentisierung nötig ist und nur über die Oberfläche gemacht werden kann können sie Datenübertragungen nur über die Salesforce-Benutzeroberfläche tätigen. Es ist nur möglich Belege über eine API-Schnittstelle zu übertragen, es ist nicht möglich Datenübertragungen über eine API-Schnittstelle anzulegen.

Jede Datenübertragung hat Belegpositionen und Anhänge assoziiert. Die Belegpositionen sind Referenzen auf die Objekte, die auch über Belege aufrufubar sind. Die Anhänge sind Kopien der Belegbilder aus Belegen und Metadaten (XML-Files) der Belege, so wie sie an DATEV übertragen wurden.

Haben Sie Belege gelöscht, die Belegpositionen enthielten, die zu dieser Datenübertragung zugeorndet sind (geht nur, wenn die Datenübertragung auf DATEV-Seite abgeschlossen ist oder im Salesforce-Status neu, also vor dem Start einer Übertragung), so können Sie in der XML-Datei im Anhang weiterhin sehen, welche Belegpositionen an DATEV übertragen wurden.