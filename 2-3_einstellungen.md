## Reiter “Einstellungen”: Benutzerspezifische Einstellungen für die Datenübertragung {#reiter-einstellungen}

### Sachkontenlänge {#sachkontenlaenge}

In den Einstellungen hinterlegen Sie die Sachkontolänge. Die Sachkontenlänge kann einen Wert zwischen 4 und 8 haben.

Die Sachkontenlänge ist elementar bei der Validierung aller Datentransfers nach "JustOn Connector for DATEV" und von dort nach DATEV. Der Wert muss mit der Sachkontolänge in den Anwendungen in DATEV Unternehmen online übereinstimmen. Bei Fragen wenden Sie sich bitte an Ihren Steuerberater.

Als default-Wert ist 4 hinterlegt. Bitte hinterlegen Sie den für Sie zutreffenden Wert der Sachkontenlänge **vor dem ersten Transfer von Daten aus anderen Salesforce-Anwendungen**.

### Voreinstellungen für die Übertragung von Daten an DATEV {#voreinstellungen-datenuebertragung}

Im Reiter "Einstellungen" können Sie folgende Voreinstellungen für die Übertragung von Daten an DATEV hinterlegen, ändern oder entfernen:

* Bevorzugter Mandant (Beraternummer und Mandantennummer)
* Bevorzugte Ordner (Rechnungsordner / Kassenname)

Haben Sie hier Voreinstellungen hinterlegt, so werden diese bei zukünftigen Datenübertragungen übernommen. Sie werden bei der Neuanlage einer Datenübertragung nicht mehr nach diesen Angaben gefragt, die entsprechenden Dialoge werden dann nicht angezeigt.

Werte für diese Voreinstellungen können Sie auch im Dialog beim Anlegen neuer Datenübertragungen hinterlegen, indem Sie die entsprechenden Checkboxen zum Speichern der Werte anhaken.

Möchten Sie Werte löschen, so leeren Sie das Feld im Reiter "Einstellungen". Sie werden dann bei der nächsten Datenübertragung um eine erneute Angabe / Auswahl gebeten.


## Wichtige Hinweise zur GoBD-Konformität {#gobd-konformität}

Ziel der GoBD-Konformität in „JustOn Connector for DATEV“ ist es, Sie als Nutzer bestmöglich bei der Einhaltung der GoBD zu unterstützen. 

Sie als Unternehmer sind für die GoBD-konforme Aufbewahrung und Verarbeitung der Belege verantwortlich. Wichtige Eckpfeiler der GoBD-Konformität sind:
-	Unveränderbarkeit der Belege
-	Zeitnahe Buchung der Belege im Rechnungswesen

Bei Fragen wenden Sie sich bitte an Ihren Steuerberater.

### Wie kann mich JustOn Connector for DATEV bei GoBD-konformem Übertragen von Belegen unterstützen?

Die folgenden Bedingungen unterstützen Sie beim GoBD-konformen Arbeiten in „JustOn Connector for DATEV“. Für Regelungen in der angebundenen Salesforce-Anwendung wenden Sie sich bitte an den entsprechenden Softwarehersteller.

* Belege, die aus angebundenen Salesforce-Anwendungen an „JustOn Connector for DATEV“ transferiert werden, dürfen in „JustOn Connector for DATEV“ nicht verändert werden. Das betrifft sowohl das Ändern von Daten als auch das Hinzufügen oder Löschen von Belegbildern und weiteren Belegpositionen. Beim Transfer soll die angebundene Salesforce-Anwendung ein Kennzeichen für festgeschrieben setzen, so kann der Beleg nicht mehr verändert werden. Nur der Administrator kann das „festgeschrieben“-Kennzeichen entfernen.
* Eine erfolgreich an DATEV übertragene Datenübertragung kann nicht mehr gelöscht werden. Es können auch keine einzelnen Daten der Datenübertragung entfernt werden (XML-Dateien, Belegbild).
* Die Datenübertragung ist samt übertragenen Daten (Metadaten Beleg und Belegbild) nach der Erstanlage unveränderlich.
* Der Beleg selbst mit Belegpositionen und Belegbildern kann nach erfolgreicher Übertragung an DATEV gelöscht werden.
* Abschalten einer dieser Funktionen kann zum Verlust der GoBD-Konformität führen. Das Abschalten einer dieser Funktionen wird im System protokolliert.
* Manuell vom Benutzer angelegte Daten sind nicht GoBD-konform.

Bitte achten Sie darauf, dass Sie die Anwendung nicht anders verwenden als hier im Handbuch und die Anwendungs-Einstellungen nicht anders verwenden als im Abschnitt [„Administration“](4_administration.md#administration) beschrieben. 

**Achtung:** Dies betrifft auch Einstellungen in den Layouts, ob Feldänderungen protokolliert werden, Schreibschutz von Feldern bis hin zum Entfernen von Validierungsregeln, die jeder Nutzer selbst vornehmen kann!

**"JustOn Connector for DATEV" bietet ihnen Unterstützung, für die Einhaltung der GoBD sind Sie aber letztendlich selbst verantwortlich.**

**Hinweis:** Bei der Übermittlung eines Belegdatensatzes ohne Belegbild ist es nötig, dass Ihnen das Original des Belegs vorliegt und über den gesetzlich vorgeschriebenen Zeitraum vorzeigbar gehalten wird.

Bei weiteren Fragen zur GoBD-Konformität gehen Sie bitte auf Ihren Steuerberater zu. 

### Was wird von JustOn Connector for DATEV hinsichtlich GoBD abgedeckt?

GoBD-Konformität kann in zwei verschiedene Prozesse unterteilt werden:

* GoBD-konformes Arbeiten       
* Nachweis, dass GoBD-konform gearbeitet wurde

"JustOn Connector for DATEV" in Salesforce unterstützt Sie beim ersten Prozess – vorausgesetzt Sie haben die Anwendung nach der Installation nach den Vorgaben eingerichtet (siehe Abschnitt [„Administration“](4_administration.md#administration)) und keine der Vorgaben verändert, wie z.B. die Protokollierung von Änderungen ausgeschaltet (nach den Vorgaben für die Einrichtung sollte das nur mit Administrator-Rechten möglich sein). 

**Für einen Zeitraum über sechs Monate in die Vergangenheit ist in Salesforce dann nachvollziehbar, ob Sie Daten GoBD-konform an DATEV übertragen haben** bzw. bis zu welchem Zeitpunkt. Ein länger zurückliegender Nachweis, dass Sie in „JustOn Connector for DATEV“ in Salesforce GoBD-konform gearbeitet haben (Prozess 2) ist schon deshalb nicht möglich, weil Salesforce in der Standard-Variante Veränderungen durch einen Administrator nur sechs Monate protokolliert. 

Möchten Sie hier eine Verlängerung des Protokollierungs-Zeitraums, so gehen Sie bitte auf Salesforce zu. (Salesforce empfiehlt seinen Kunden das Aufsetzen einer Data Retention Policy, die das Archivieren von Daten in Drittsystemen und das Aggregieren von 'Altdaten' in Salesforce umfasst).

**JustOn Connector for DATEV kann Sie also dabei unterstützen, bei der Übertragung von Belegen GoBD-konform zu arbeiten. Für die Einhaltung der Richtlinien sind Sie aber selbst verantwortlich.**

**Achtung:** Sie können an einer Datenübertragung an den zugeordneten Belegpositionen nicht erkennen, ob nur die oder noch mehr übertragen wurden, weil Sie Belege löschen können nach erfolgreicher Übertragung an DATEV. Um definitiv zu wissen was alles an DATEV übertragen wurde müssen Sie die XML-Dateien an der Datenübertragung prüfen.

Für Prüfungen sind Daten aus dem Vorsystem mit den Daten in DATEV Unternehmen online manuell zu vergleichen, wenn der Prüfungszeitraum mehr als sechs Monate umfasst und nachgewiesen werden soll, dass Sie Daten unverändert aus ihrem rechnungsschreibenden Vorsystem an DATEV übertragen haben.



## Einen Dummy-Beleg für Testzwecke anlegen {#dummy-beleg-fuer-testzwecke}

Die manuelle Erfassung von Belegen in „JustOn Connector for DATEV“ dient nur zu Testzwecken.

Bitte übertragen Sie manuell angelegte Belege nicht ins DATEV-Rechenzentrum oder stellen Sie sicher, dass zu Testzwecken übertragene Daten als solche erkennbar sind und kümmern Sie sich um eine Löschung der Daten aus DATEV Unternehmen online, sobald Sie sie nach DATEV übertragen haben.

**Achtung:** „JustOn Connector for DATEV“ bietet keine GoBD-konforme Unterstützung für die manuelle Erfassung von Belegen. Wenden Sie sich an Ihren Steuerberater, um dafür gegebenenfalls eine Anwendung in DATEV Unternehmen online zu nutzen. 

Um einen neuen Beleg anzulegen wählen Sie bitte zuerst den Typ des Belegs aus: Eingangsrechnung, Ausgangsrechnung oder Kasse. Anschließend erfassen Sie die Angaben zum Beleg. Ein Rechnungsbeleg besteht mindestens aus dem Beleg-Datum, einer Rechnungsnummer und der ersten Belegposition mit einem Betrag. Dieser Betrag ist der Rechnungsbetrag, wenn Sie nur eine Belegposition zum Beleg erfassen. Weitere Belegpositionen können sinnvoll sein, wenn z. B. Beträge mit verschiedenen Steuersätzen vorliegen oder wenn unterschiedliche Warengruppen oder Kostenstellen ausgewiesen werden sollen. Speichern Sie den Beleg. Jetzt können Sie ein oder mehrere Belegbilder anhängen und weitere Belegpositionen zum Beleg erfassen.

Der Gesamtbetrag eines Beleges setzt sich aus den Beträgen aller Belegpositionen zusammen und wird automatisch berechnet.


## Löschen von Daten {#loeschen-von-dateien}

Bei der Nutzung von "JustOn Connector for DATEV" werden Daten an mehreren Stellen gehalten:
* Sie legen  Belege (Belegdaten und das Belegbild) in einem Vorsystem an, 
* übertragen die Belege dann in die Datenstrukturen nach "JustOn Connector for DATEV", 
* und erzeugen bei der Datenübertragung Duplikate der Belegbilder plus die Metadaten mit den Belegdaten.

Falls sie Speicherplatz in Salesforce freigeben möchten, so können Sie nach erfolgreichen Datenübertragungen die Belege gegebenenfalls selbst (im Reiter "Belege") löschen. 
Die Datenübertragung mit allen identischen Daten muss erhalten bleiben, um Nachvollziehbarkeit der Datenübertragungen zu gewährleisten.

Des Weiteren können Sie Datenübertragungen löschen, die nicht erfolgreich waren.

