## Reiter „Datenübertragung“: Daten an DATEV übertragen {#reiter-datenuebertragung}

Nach dem Prüfen der Belege, die Sie aus einer angebundenen Salesforce Anwendung in "JustOn Connector for DATEV" transferiert haben, können Sie die Belege im Reiter „Datenübertragung“ an DATEV übertragen. Dazu klicken Sie bitte auf „Neue Datenübertragung“. 

In einer Datenübertragung übertragen Sie alle noch nicht übertragenen Belege, die zum gleichen Buchungsmonat und zur gleichen Beleg-Art gehören, an DATEV. 

Bei der Neuanlage einer Datenübertragung wählen Sie zunächst das Jahr, den Buchungsmonat und die Beleg-Art aus. Sind Belege für einen Buchungsmonat und eine Beleg-Art vorhanden, die noch nicht an DATEV übertragen wurden, so sind der entsprechende Monat mit einem Stern und die Beleg-Art mit der Anzahl der übertragbaren Belege gekennzeichnet.

Ein Beleg kann Belegpositionen zu unterschiedlichen Buchungsmonaten enthalten. In diesem Fall benötigt es mehrere Datenübertragungen, um alle Belegpositionen des Belegs zu übertragen.  Die  angehängten Belegbilder des Beleges werden bei der ersten Datenübertragung von Belegpositionen dieses Belegs an DATEV übertragen.
 
**Hinweis:** Es können weder einzelne Belege noch einzelne Belegpositionen für die Datenübertragung selektiert werden. Die Selektion erfolgt ausschließlich über den Buchungsmonat und die Beleg-Art. Es werden immer alle noch nicht übertragenen Belegpositionen der Belege übertragen, die zum gewählten Buchungsmonat und zur gewählten Beleg-Art gehören.

Bitte prüfen Sie nach jeder Datenübertragung, dass die Datenübertragung erfolgreich war. Das können Sie über den Button "Status aktualisieren" tun, wo sie auch das Protokoll zur Übertragung einsehen können.

Diese Schritte werden nachfolgend detailliert beschrieben.


### Authentisierung {#authentisierung}
Für folgende Aktionen müssen Sie sich mit Ihrem DATEV Authentifizierungsmedium authentifizieren (falls nicht schon in der aktuellen Session in einer vorhergehenden Aktion geschehen):

* Anlegen einer Datenübertragung
* Aktualisieren von Statusinformationen und Abrufen von Protokollinformationen zu einer Datenübertragung
* Neuübertragung einer Datenübertragung
* Löschen einer Datenübertragung, die sich im Status „Offen“ befindet

Für die Authentifizierung bei DATEV wird das Verfahren OAuth2.0 mit OpenID Connect verwendet, um Sie als Benutzer zu authentifizieren und die Berechtigung für den Zugriff auf die Anwendungen in DATEV Unternehmen online durch Sie freizugeben. Das Verfahren ermöglicht es Ihnen 11 Stunden zu arbeiten, ohne sich erneut bei DATEV authentifizieren zu müssen.

Wenn Sie sich von der Salesforce-Plattform abmelden oder den Browser schließen müssen Sie sich bei erneuter Anmeldung in Salesforce für die erste Aktion, die eine Authentisierung benötigt erneut mit Ihrem DATEV Authentifizierungsmedium anmelden.


### Eine neue Datenübertragung anlegen {#neue-datenuebertragung-anlegen}
Eine Datenübertragung kann in „JustOn Connector for DATEV“ nur manuell durch Sie angelegt und durchgeführt werden. Eine angebundene Salesforce-Anwendung kann eine Datenübertragung weder anlegen noch durchführen.

Eine neue Datenübertragung können Sie nur anlegen, wenn keine Datenübertragung innerhalb der Organisationseinheit in Übertragung ist bzw. erst wenn alle Datenübertragungen an DATEV vollständig übertragen wurden. 

Schritte beim Anlegen einer neuen Datenübertragung: 

**Hinweis:** Die Webseiten können inhaltlich von den hier abgebildeten Webseiten abweichen.


#### 1. Authentisieren
***Hinweis:*** *Dieser Schritt entfällt, falls Sie in der Browser-Sitzung bereits in der Anwendung „JustOn Connector for DATEV“ authentisiert sind.*

##### 1.a) Wählen Sie Ihr Authentisierungsmedium aus 
![](/images/06_authentication.png)
    
##### 1.b) Geben Sie die Berechtigung zum Zugriff auf DATEV Unternehmen online frei 
![](/images/07_authorization.png)


#### 2. Mandanten für die Datenübertragung auswählen

***Hinweis***: *Dieser Schritt entfällt, falls Mandanten- und Beraternummer in den „Einstellungen“ in „JustOn Connector for DATEV“ hinterlegt sind.*

![](/images/08_datatransfer-mandant.png)

Bei der Neuanlage einer Datenübertragung wählen Sie zunächst den Mandanten aus der Liste aller für Sie zugänglichen Mandanten aus. 

Diese Auswahl können Sie über das Häkchen in der Checkbox auch für künftige Übertragungen speichern. Die Mandantenauswahl für zukünftige Übertragungen können Sie im Reiter „Einstellungen“ wieder aufheben, indem Sie die Felder Mandantennummer und Beraternummer leeren und dann die Einstellungen speichern. Bei der nächsten Neuanlage einer Datenübertragung wird Ihnen wieder die Liste aller Ihnen zur Verfügung stehenden Mandanten angezeigt.

#### 3.	Buchungsmonat und Beleg-Art für die Datenübertragung auswählen
![](/images/08_datatransfer-belegart.png)

Nach der Auswahl des Mandanten wählen Sie das Jahr, den Buchungsmonat und die Beleg-Art aus, für die Sie Belege übertragen möchten. Buchungsmonate, die noch nicht übertragene Belege enthalten, sind mit einem schwarzen Stern gekennzeichnet. Die Liste der Beleg-Arten enthält nur die Beleg-Arten, für die zum ausgewählten Jahr und Buchungsmonat noch nicht übertragene Belege vorliegen. Die Anzahl der noch nicht übertragenen Belege steht im Klammern bei der jeweiligen Beleg-Art.<br/>
Daten werden zur Übertragung an DATEV nach Buchungsmonat und Beleg-Art zusammengefasst. Eine Datenübertragung bündelt alle Belegpositionen eines Buchungsmonats und einer Beleg-Art, die noch keiner Datenübertragung zugeordnet sind. Belegpositionen verschiedener Belege von derselben Beleg-Art (Eingangsrechnung, Ausgangsrechnung oder Kasse) mit demselben Buchungsmonat (z.B. Januar 2017) werden in einer Datenübertragung an DATEV übertragen. Eine kleinere Stückelung ist nicht möglich: z.B. kann keine einzelne Belegposition übertragen werden, wenn innerhalb desselben Buchungsmonats mehrere Belegpositionen mit derselben Buchungs-Art vorliegen, die noch nicht an DATEV übertragen wurden. 

#### 4. Ziel-Ordner bei DATEV festlegen
***Hinweis***: *Dieser Schritt entfällt, falls ein Ziel-Ordner für die gewählten Beleg-Art in den „Einstellungen“ in „JustOn Connector for DATEV“ hinterlegt ist.*

![](/images/08_datatransfer-ordner.png)
    
Als letzten Schritt vor der Datenübertragung an DATEV wählen Sie den Rechnungsordner bei Eingangs- und bei Ausgangsrechnungen bzw. den Kassennamen bei Kassenbelegen aus. Die in den Anwendungen in DATEV Unternehmen online verfügbaren Rechnungsordner bzw. Kassen werden Ihnen in einer Auswahlliste angezeigt. Bei Fragen wenden Sie sich bitte an Ihren Steuerberater. Ihre Auswahl für die gewählte Beleg-Art können Sie für zukünftige Datenübertragungen als Favorit hinterlegen. Im Reiter „Einstellungen“ können Sie diese Festlegung manuell entfernen. 

#### 5. Datenübertragung starten
Die Datenübertragung beginnt sobald Sie alle relevanten Angaben für die Datenübertragung getroffen haben. 

Die Datenübertragung geschieht in zwei Schritten: 

1.	Aufbereitung der Belege für die Übertragung an DATEV: Die Daten werden in XML-Dateien aufbereitet
2.	Übertragung der Daten an DATEV

#### 6. Datenübertragung abschließen
Nach der Datenübertragung an DATEV wird sowohl der Salesforce-Status (Verarbeitungsstatus in "JustOn Connector for DATEV") als auch der DATEV Status (Verarbeitungsstatus bei DATEV)  angezeigt. Bitte aktualisieren Sie den Status der Datenübertragung so lange manuell, bis der Status bei DATEV "Datenübertragung erfolgreich" oder "Datenübertragung abgebrochen" anzeigt. Erst dann wissen Sie, ob die Datenübertragung erfolgreich abgeschlossen wurde.

In den Details einer Datenübertragung sehen Sie alle übertragenen Belegpositionen im Abschnitt „Belegpositionen“ und alle übertragenen Belegbilder im Abschnitt „Notizen und Anhänge“.

Nachdem Daten an DATEV übertragen wurden wird der Status der Datenübertragung sowohl lokal auf Salesforce-Seite als auch bei DATEV in der Datenübertragung angezeigt. 


**Achtung**: Eine Datenübertragung bleibt ohne Ihr Zutun immer im zuletzt aktiv abgerufenen Status – der Status der Datenübertragung aktualisiert sich nicht automatisch. Bitte aktualisieren Sie den Status manuell über den Button „Status aktualisieren“ und in der Folgeansicht über „Bestätigen“. Ohne den Klick auf „Bestätigen“ werden die Änderungen nicht in die Datenübertragung übernommen.

### Fachliche Besonderheiten Datenübertragung bei Kassendaten {#besonderheiten-kassendaten}

In "JustOn Connector for DATEV" können auch Kassenbewegungen aus einer angebundenen Salesforce Anwendung transferiert werden. Sowohl beim Transfer in "JustOn Connector for DATEV" als auch bei der Datenübertragung ins Kassenbuch online in DATEV Unternehmen online ist darauf zu achten, dass Sie die Regeln der Kassenbuchführung einhalten, wie z.B. das Beachten der zeitlichen Reihenfolge der Kassenbewegungen beim Transfer und der Datenübertragung. Sie als Unternehmer sind für die Korrektheit des Kassenbuchs verantwortlich. 

Es wird empfohlen, Daten täglich nach DATEV Unternehmen online zu übertragen. Bei Fragen zur korrekten Kassenführung wenden Sie sich bitte an Ihren Steuerberater. 

Bitte beachten Sie, dass "JustOn Connector for DATEV" die Kassenbelege chronologisch überträgt. Innerhalb eines Buchungsmonats werden die Kassenbelege in der Reihenfolge übertragen, in der sie nach "JustOn Connector for DATEV" transferiert wurden. Achten Sie beim Transfer der Kassenbelege in "JustOn Connector for DATEV" auf die genaue zeitliche Reihenfolge, damit kein Minusbestand entsteht. Wenn Sie nicht die einzelnen Kassenbewegungen, sondern saldierte Werte in "JustOn Connector for DATEV"  transferieren, dann müssen zuerst die Zuflüsse und dann die Abflüsse transferiert werden. "JustOn Connector for DATEV" übernimmt keine Prüfungen der Kassenbewegungen (Ausnahme: formale Prüfung wie unter [Validierungen](2-2_reiter-datenuebertragung-weiteres.md#validierungen) beschrieben).

Bitte übertragen Sie ältere Monate vor den neueren Monaten. Kassenbelege können nur chronologisch übertragen werden, d.h. sobald Sie Kassenbelege für einen Buchungsmonat übertragen haben können Sie keine Kassenbelege mehr für ältere Buchungsmonate übertragen.

Bitte beachten Sie, dass bei der Erzeugung eines Kassenbelegs alle Belegpositionen das gleiche Belegdatum haben. 

