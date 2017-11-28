### Status der Datenübertragung aktualisieren {#status-aktualisieren}

In der Detailansicht zu einer Datenübertragung können Sie den Salesforce Status und den DATEV Status prüfen. <b>Die Status werden nicht automatisch aktualisiert, </b> eine Datenübertragung bleibt ohne Ihr Zutun immer im zuletzt aktiv abgerufenen Status. 

<b>Bitte aktualisieren Sie den Status manuell</b> über den Button „Datenübertragung aktualisieren“ und in der Folgeansicht über „Bestätigen“. 

**Hinweis:** Der Status der Datenübertragung wird nur dann dauerhaft in der DATEV-Anwendung in Salesforce aktualisiert, wenn der Button „Bestätigen“ im Fenster „Status aktualisieren“ angeklickt wird. Andernfalls wird der aktuellste Status nur angezeigt, nicht aber in die Datenübertragung der Salesforce-Anwendung übernommen. 

Nach Klick auf den Button “Status aktualisieren” wird der Status der Datenübertragung bei DATEV abgerufen. Zusätzlich werden DATEV-Protokollinformationen zur Datenübertragung abgerufen und angezeigt. Dort ist z.B. der genaue Zeitpunkt der Übertragung enthalten, die Reihenfolge der übertragenen Daten und welche Dateien übertragen wurden. 

**Hinweis:** Status und Protokollinformationen stehen nur temporär, ca. zwei Monate zur Verfügung! Danach werden die Informationen bei DATEV gelöscht und der Status und das Protokoll können nicht mehr von der Salesforce-Anwendung bei DATEV abgerufen werden (Versuch führt zu einem HTTP-Error 404). Der Status und das Protokoll können auch dann nicht mehr abgerufen werden, wenn der Steuerberater oder Sie das Protokoll zu einer Datenübertragung in DATEV Unternehmen online löschen.

Der zuletzt von Ihnen abgerufene DATEV-Status der Übertragung und gegebenenfalls die letzte Fehlermeldungen werden dauerhaft in Salesforce an der Datenübertragung gespeichert.

Folgende Status sind möglich:

| **Salesforce-Status** | **DATEV-Status** | **Bedeutung** |
| --- | --- | --- |
| Neu | Status offen | Eine Datenübertragung wurde neu angelegt. |
| In Vorbereitung<br/>Vorbereitet zur Übertragung<br/>In Übertragung | Status offen| Daten in Verarbeitung in "JustOn Connector for DATEV" bei Salesforce.<br/>Bitte aktualisieren Sie den Status. |
| Transferiert | Status offen<br/> In Arbeit | Daten in Verarbeitung bei DATEV (in DATEV Unternehmen online).<br/>Bitte aktualisieren Sie den Status. | 
| Transferiert | Fertig | Die Datenübertragung und Verarbeitung bei DATEV (in DATEV Unternehmen online) war erfolgreich. |
| Transferiert| Abgebrochen<br/>Zu Prüfen | Die Verarbeitung in den Anwendungen in DATEV Unternehmen online war fehlerhaft. <br/><br/>Prüfen Sie die Fehlermeldungen. Falls bei einer fehlerhaften Datenübertragung bereits einzelne Belege erfolgreich verarbeitet wurden, klären Sie bitte mit Ihrem Steuerberater das weitere Vorgehen. |
| Transferiert| Erfolgreich storniert | Die Stornierung der Verarbeitung in DATEV Unternehmen online durch den Anwender war erfolgreich. Die Belege und die verarbeiteten Daten in den Anwendungen in DATEV Unternehmen online wurden entfernt. |
| Transferiert| Storniert mit Fehler | Die Stornierung der Verarbeitung in DATEV Unternehmen online durch den Anwender war nicht erfolgreich. Die Belege und die verarbeiteten Daten in den Anwendungen in DATEV Unternehmen online konnten nicht entfernt werden. |


### Protokollinformationen zur Übertragung anzeigen {#protokollinformationen}

Über den Button “Status aktualisieren” werden u.a. DATEV-Protokollinformationen zur Datenübertragung abgerufen und angezeigt. 

Es können maximal 1.000 Zeilen Protokolleinträge zu einer Übertragung angezeigt werden.

Weitere Informationen siehe [Status aktualisieren](#status-aktualisieren)


### Validierung und Fehlermeldungen bei der Übertragung {#validierungen}
Beim Transfer von Belegen aus anderen Salesforce-Anwendungen in "JustOn Connector for DATEV" in Salesforce werden die Daten validiert, um formal sicherzustellen, dass die Daten in den Anwendungen von „DATEV Unternehmen online“ verarbeitet werden können.

Trotzdem kann es bei der Datenübertragung und der Verarbeitung der Belege in den Anwendungen von DATEV Unternehmen online zu Fehlern kommen. Prüfen Sie deshalb bitte den Salesforce Status und den DATEV Status. 
 
In manchen Fehlersituationen benötigen Sie Ihren Steuerberater für die Behebung der Fehlersituation. Bitte nehmen Sie in diesem Fall Kontakt mit Ihrem Steuerberater auf. 
 
Sind bereits einzelne Belege der Datenübertragung erfolgreich verarbeitet worden, klären Sie bitte mit Ihrem Steuerberater das weitere Vorgehen.
 
Je nach Fehlersituation ist ein Löschen der Datenübertragung und der betroffenen Belege in "JustOn Connector for DATEV" notwendig. Korrigieren Sie die Belege in Ihrer Salesforce-Anwendung und importieren Sie die korrigierten Belege in "JustOn Connector for DATEV". Führen Sie anschließend die Datenübertragung zu DATEV durch.
 
Weitere Informationen zu möglichen Fehlermeldungen finden Sie auch hier: https://www.datev.de/dnlexom/client/app/index.html#/document/1046334


### Entfernen der Voreinstellungen für Datenübertragungen {#voreinstellungen-entfernen}

Bei Anlegen einer neuen Datenübertragung werden Sie zu einigen Angaben nicht mehr gefragt, falls Sie diese für neue Datenübertragungen gespeichert haben. Sie können diese Daten, also Angaben zu
* Bevorzugtem Mandant (Beraternummer und Mandantennummer) und
* Bevorzugtem Ordner

im Reiter „Einstellungen“ ändern oder entfernen (siehe Beschreibung [Reiter "Einstellungen"](2-3_einstellungen.md#reiter-einstellungen). Wenn Sie Ihre Angaben entfernt haben werden Sie Ihnen bei Anlegen einer neuen Datenübertragung erneut zur Auswahl angeboten.


### Neuübertragung einer Datenübertragung {#neu-uebertragen}

War eine Datenübertragung z.B. auf Grund eines Übertragungsfehlers nicht erfolgreich, so können Sie Daten neu übertragen. Rufen Sie dazu die Detailseite der Datenübertragung auf und klicken Sie auf den Button "Datenübertragung neu starten".


### Welche Belegdaten werden an DATEV übertragen? Was kommt bei DATEV in welchen Feldern an? {#was-bei-datev-ankommt}

Aus Ihrer JustOn Connector for DATEV vorgelagerten Salesforce Anwendung transferieren Sie Belege, d. h. Belegdaten und Belegbilder, an „JustOn Connector for DATEV“. „JustOn Connector for DATEV“ bereitet die Belegdaten für die Verarbeitung in den Anwendungen in DATEV Unternehmen online auf und überträgt diese Daten zusammen mit den Belegbildern an DATEV. 

In den Anwendungen in DATEV Unternehmen online stehen die Belege Ihrem Steuerberater zur Weiterverarbeitung in der Finanzbuchführung zur Verfügung. Er nutzt dafür ein DATEV Rechnungswesen Programm. 

Sie übertragen die Daten zuerst nach DATEV Unternehmen online, dort stehen alle Daten so wie in JustOn Connector for DATEV zur Verfügung. 

Von DATEV Unternehmen online übernimmt der Steuerberater die Daten in sein DATEV Rechnungswesen-Programm.

Im Folgenden wird beschrieben welche Daten aus "JustOn Connector for DATEV" in welche Felder im DATEV Rechnungswesen Programm übertragen werden.

| **Rechnungseingangs-/Rechnungsausgangsdaten** | **Feldbezeichnung im DATEV Rechnungswesen Programm** | 
| --- | --- |
| Vorzeichen des Betrags | Betragsangaben Soll/Haben | 
| Datum | Datum |
| Betrag | Umsatz |
| BU | BU (bzw. BU Konto) |
| Belegtext | Buchungstext oder Zusatzinformation 2 |
| Konto | Konto |
| KOST1 | KOST1 |
| KOST2 | KOST2 |
| KOST-Menge | KOST-Menge |
| Geschäftspartner-Name | Buchungstext (zusammen mit Ort) oder Zusatzinformation 2 |
| Geschäftspartner-Ort | Buchungstext (zusammen mit Name) oder Zusatzinformation 2 |
| Geschäftspartner-Konto | Gegenkonto |
| Rechnungs-Nr. | Belegfeld 1 |
| Fällig ohne Skonto | Belegfeld 2 |
| Steuer in %  | Zusatzinformation |
| USt-IdNr. | USt-IdNr. |
| Kurs | Kurs |
| Währung | WKZ |
| Kundennummer | Zusatzinformation |
| Zahlungsbedingungs-Nr. | Belegfeld 2 |
| Nachricht | Zusatzinformation mit Eintrag D_Nachricht |

| **Kassendaten** | **Feldbezeichnung im DATEV Rechnungswesen Programm** | 
| --- | --- |
| Vorzeichen des Betrags | Betragsangaben Soll/Haben |
| Datum | Datum |
| Betrag | Umsatz |
| Skonto-Betrag 1 | Skonto |
| BU | BU (bzw. BU Konto) |
| KOST-Menge | KOST-Menge |
| KOST1 | KOST1 |
| KOST2 | KOST2 |
| Steuer in % | Zusatzinformation |
| Nachricht | Zusatzinformation mit dem Eintrag D_Nachricht |
| Währung | WKZ |
| Rechnungsnummer | Belegfeld 1 |
| Belegtext | Buchungstext |
| Konto | Konto |

