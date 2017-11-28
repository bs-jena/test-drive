# FAQ – Häufig gestellte Fragen {#faq}

## Wohin werden meine Daten übertragen? {#faq-daten-wohin}
Ihre Daten werden ins DATEV Rechenzentrum übertragen. Sie können die Daten über die Online-Anwendung "DATEV Unternehmen online" einsehen. Ein- und Ausgangsrechnungen können Sie im Abschnitt "Belege" verwalten, Kassenbelege unter "Belegwesen" --> "Kasse". 

Ihr Steuerberater überträgt die Daten von dort weiter in sein DATEV Rechnungswesen Programm.

## Sind mehrere Buchungsperioden in einem Beleg möglich? {#faq-mehrere-buchungsperioden}
Ja, Sie können einen Beleg mit mehreren Belegpositionen anlegen. Jede Belegposition kann einen anderen Buchungsmonat haben. Bitte beachten Sie, dass für jeden Buchungsmonat eine eigene Datenübertragung an DATEV nötig ist.

## Ist es möglich nur ein Belegbild an DATEV zu senden? {#faq-nur-ein-belegbild}
Innerhalb von JustOn Connector for DATEV ist das nicht möglich. Bitte gehen Sie auf Ihren Steuerberater zu, falls Sie Belegbilder ohne Belegdaten an Ihren Steuerberater übertragen möchten. 

## Ich kann mich nicht authentisieren, obwohl ich ein DATEV-Authentisierungsmedium verwende. Was kann ich tun? {#faq-problem-authentisierung}
Sprechen Sie mit Ihrem Steuerberater.

## Woran erkenne ich, dass die Übertragung geklappt hat? {#faq-erfolg-uebertragung}
Aktualisieren Sie den Status der Datenübertragung über den Button "Status aktualisieren" in der Datenübertragung, und **bestätigen** Sie die Daten dann über den Button "Bestätigen".  

War die Übertragung und die Verarbeitung der Belege bei DATEV erfolgreich, so wird als DATEV-Status „Fertig“ und als lokaler Status „Transferiert“ angezeigt. 

## Warum bietet JustOn Connector for DATEV keine Unterstützung für die manuelle Anlage und Übertragung von Belegen?

Mit "JustOn Connector for DATEV" werden Belege und Belegdaten aus angebundenen Salesforce-Anwendungen an DATEV übertragen, um die Zusammenarbeit mit dem Steuerberater zu erleichtern. "JustOn Connector for DATEV" ist weder eine Rechnungsschreibung noch eine Belegerfassungsanwendung. Dafür gibt es andere Anwendungen.

## Wie arbeite ich mit JustOn Connector for DATEV bestmöglich GoBD-konform? {#faq-gobd}
Wie Sie JustOn Connector for DATEV bestmöglich bei GoBD-konformem Übertragen von Belegen unterstützt können Sie im Abschnitt [Wichtige Hinweise zur GoBD-Konformität](2-3_einstellungen.md#gobd-konformität) nachlesen.

## Kann ich in JustOn Connector for DATEV sehen, ob Daten aus einem Vorsystem stammen? {#faq-vorsystem}
Ja, Sie können das am Feld "Aus Drittsystem" des Belegs in „JustOn Connector for DATEV“ sehen. Eine detailliertere Antwort auf die Frage finden Sie unter [hier](2-1_reiter-belege.md#unterscheidung-vorsystem)

## Ich möchte Kassendaten übertragen, eine neue Datenübertragung ist aber nicht möglich, obwohl Belege vorliegen {#faq-kassendaten-ohne-wirtschaftsjahr}
Um Daten an DATEV übertragen zu können muss in DATEV Unternehmen online das zugehörige Wirtschaftsjahr angelegt sein. Für Eingangs- und Ausgangsrechnungen wird dies teilweise automatisch angelegt, bei Kassendaten muss es immer manuell angelegt werden.
Möchten Sie Kassenbelege mit einem nicht angelegten Wirtschaftsjahr übertragen, so prüfen Sie bitte, ob das Wirtschaftsjahr in DATEV Unternehmen online angelegt ist oder gehen Sie auf Ihren Steuerberater zu.

## Was ist zu beachten, wenn ich Belege zum ersten Mal für ein nächsthöhreres Wirtschaftsjahr übertrage? {#faq-jahresuebernahme}
Wenn Sie Rechnungsbelege übertragen, für die in den Anwendungen in "DATEV Unternehmen online" noch kein nächsthöheres Wirtschaftsjahr für den die jeweilige Beleg-Art angelegt ist, so wird bei der Datenübertragung von Rechnungen in der Regel automatisch das nächsthöhere Wirtschaftsjahr angelegt. Falls die automatische Anlage nicht erfolgreich war, erhalten Sie eine entsprechende Fehlermeldung bei der Datenübertragung.

**Hinweis:** Für Belege vom Typ Kasse ist eine automatische Erzeugung eines neuen Rechnungsjahres grundsätzlich nicht möglich. 

