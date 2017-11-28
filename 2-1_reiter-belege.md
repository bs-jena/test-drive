# Die Anwendung "JustOn Connector for DATEV" in Salesforce nutzen {#introduction}

## Aufruf der Anwendung {#aufruf-der-anwendung}

Loggen Sie sich nach der Installation in Salesforce ein und wählen Sie „DATEVconnect“ im Dropdown-Menü rechts oben:

![](/images/03_open-app.png)

Sie sehen nun eine Anwendung mit drei Reitern: “Belege“, „Datenübertragungen“ und „Einstellungen“.

**Wichtiger Hinweis:** Bitte prüfen Sie als ersten Schritt im Reiter “Einstellungen” die Sachkontenlänge. Die Sachkontenlänge muss mit der Sachkontolänge in den Anwendungen in DATEV Unternehmen online übereinstimmen und ist wichtig für die Validierung einiger Felder in den Datenstrukturen Beleg und Belegposition. Wie Sie die Sachkontenlänge einstellen können Sie im Abschnitt [Sachkontenlänge](2-3_einstellungen.md#sachkontenlaenge) nachlesen. Bei Fragen wenden Sie sich bitte an Ihren Steuerberater.


## Funktionsübersicht {#funktionen}
  
Folgende Haupt-Funktionen stehen Ihnen in „JustOn Connector for DATEV“ zur Verfügung:

1.	Aus angebundenen Salesforce-Anwendungen nach „JustOn Connector for DATEV“ transferierte [**Belege (Belegdaten und Belegbilder) prüfen**](#reiter-belege) (im Reiter "Belege")
2.	[**Belege (Belegdaten und Belegbilder) an DATEV übertragen**](2-2_reiter-datenuebertragung-neu.md#reiter-datenuebertragung) (im Reiter "Datenübertragung")
2.	[**Informationen (u.a. Status und Übertragungsprotokoll) zur Datenübertragung einsehen**](2-2_reiter-datenuebertragung-weiteres.md#status-aktualisieren) (im Reiter "Datenübertragung") 

	
![](/images/04_functions.png)


## Reiter „Belege“: Daten vor einer Übertragung an DATEV prüfen {#reiter-belege}

Im Reiter „Belege“ können Sie aus anderen Salesforce-Anwendungen übertragene Belege prüfen. 

Falls Sie den Beleg so nicht an DATEV übertragen möchten können Sie den Beleg auch löschen ([siehe Abschnitt "Beleg löschen"](#beleg-loeschen)).


### Datenstruktur eines Belegs {#datenstruktur-beleg}

Ein Beleg besteht aus übergreifenden Informationen, Belegpositionen und Belegbildern.

![](/images/05_data-structure.png)

| **Komponenten eines Belegs** | **Beschreibung** |
| --- | --- | 
| **Beleg**	| Daten zu einem Beleg. Ein Beleg kann von folgender Beleg-Art sein: <ul><li>Eingangsrechnung,</li><li>Ausgangsrechnung oder</li><li>Kasse</li></ul> |
| **Belegposition**| Ein Beleg hat mindestens eine Belegposition | 
| **Belegbild** | Salesforce-Anhang |


Die Ausgestaltung der Belegfelder (in Beleg und Belegposition) ist je nach Beleg-Art (Eingangsrechnungen, Ausgangsrechnungen oder Kassendaten) unterschiedlich.


### Belegpositionen eines Belegs {#beleg-belegpositionen}
Zu jedem Beleg sind ein oder mehrere Belegpositionen möglich. Jede Belegposition wird als Buchungsvorschlag an DATEV übertragen. Verschiedene Belegpositionen können sinnvoll sein, wenn z.B. Beträge mit verschiedenen Steuersätzen vorliegen oder wenn unterschiedliche Warengruppen oder Kostenstellen ausgewiesen werden sollen. Alle Belegpositionen müssen zur selben Rechnung (=Beleg) gehören.

Ob Sie die Belegpositionen eines Beleges bereits vollständig an DATEV übertragen haben sehen Sie daran, dass 
* in der Tabelle "Belegpositionen" in der Detailansicht des Beleges alle Belegpositionen eine Datenübertragung zugeordnet haben und 
* alle diese Datenübertragungen an DATEV erfolgreich waren

### Belegbilder zu einem Beleg {#beleg-belegbilder}
Belegbilder hängen als Anhang an einem Beleg. 

Anhänge an Belegen werden an DATEV übertragen, wenn Sie vom Dateityp
```
bmp, gif, jpeg, jpg, png, tif, tiff, csv, doc, docx, dta, msg, ods, odt, pdf, rtf, txt, xls, xlsx, xml, eml
```

sind. Andernfalls werden sie für die Übertragung nicht berücksichtigt.

Für die Übertragung nach DATEV darf ein einzelner Anhang nicht größer als 4 MB sein (andernfalls erhalten Sie eine Fehlermeldung bei der Vorbereitung einer Datenübertragung an DATEV).

Gibt es Belegpositionen mit verschiedenen Buchungsmonaten, so werden die Belegbilder im Buchungsmonat der ersten Belegposition des Belegs, die an DATEV übertragen wird, mit übertragen. 


**Besondere Hinweise für erfolgreiche Übertragungen von Belegbildern an DATEV:**
*	Dateianhänge werden als binary erwartet
*	Base64 encoding wird nicht unterstützt
*	Dateinamen mit Sonderzeichen im Unicode-decomposed-Format werden nicht unterstützt

### Notizen {#notizen}
Notizen sind Salesforce-spezifisch und werden nicht an DATEV übertragen.

Für Kommentare zu Belegen, die an DATEV übertragen werden sollen, nutzen Sie bitte das Feld „Nachricht“ in der Belegposition.


### Mehrere Buchungsmonate in einem Beleg {#beleg-mehrere-buchungsperioden}
In einem Beleg können Belegpositionen mit verschiedenen Buchungsmonaten (z.B. eine für Januar, eine für Februar) enthalten sein. An DATEV können Daten nur pro Buchungsmonat und Beleg-Art übertragen werden. Hat also ein Beleg Belegpositionen mit verschiedenen Buchungsmonaten, so müssen Sie diese in jeweils eigenen Datenübertragungen an DATEV übertragen.

Alle Belegbilder eines Belegs werden mit der ersten an DATEV übertragenen Belegposition an DATEV übertragen.

### Löschen eines Belegs {#beleg-loeschen}
Falls Sie bei der Prüfung des Belegs feststellen, dass der Beleg fehlerhaft ist, so können Sie ihn, solange er nicht mit einer Datenübertragung verknüpft ist, löschen.

**Hinweis:** Sie können einen Beleg auch löschen, wenn er mit einer Datenübertragung verknüpft ist und die Datenübertragung - erfolgreich oder nicht erfolgreich - abgeschlossen ist. Die Daten des Belegs hängen dann als XML plus Belegbilder an der Datenübertragung, die sie nicht mehr löschen können, wenn sie erfolgreich war. 

### Manuelle Anlage von Belegdaten {#beleg-manuelles-anlegen}
Das manuelle Anlegen von Belegdaten ist nur für Demozwecke gedacht. Bitte beachten Sie, dass, sobald Sie Daten eines bestehenden Belegs verändern oder sobald Sie einen Beleg manuell anlegen, keine GoBD-Konformität besteht.

**Erläuterung:** Bei manuell angelegten Belegen können Sie z.B. Belegbilder hinzufügen oder löschen und Belegpositionen hinzufügen oder löschen (bevor Sie den Beleg einer Datenübertragung zugeordnet haben) und die Änderungen werden nicht vom System protokolliert. 

### Kann ich in JustOn Connector for DATEV sehen, ob Daten aus einem Vorsystem stammen? {#unterscheidung-vorsystem}

Ja, Sie können im Feld "Aus Drittsystem" des Belegs in „JustOn Connector for DATEV“ sehen, ob Daten aus einem Vorsystem stammen oder manuell in "JustOn Connector for DATEV" erstellt wurden. Voraussetzung dafür ist, dass Sie das Feld bei den ursprünglich ausgelieferten Einstellungen belassen haben (Feld nicht editierbar) und das Vorsystem, das Daten nach "JustOn Connector for DATEV" überträgt, das Feld korrekt befüllt. 

**Hinweis:** In DATEV Unternehmen online sehen Sie keinen Unterschied zwischen aus "JustOn Connector for DATEV" manuell angelegten und aus Vorsystemen übertragenen Daten. Diesen können Sie nur am Beleg in "JustOn Connector for DATEV" sehen oder einem Vergleich der Daten im Vorsystem mit Daten in DATEV Unternehmen online entnehmen.
