---
title: Benutzeroberflächen Text und-Hilfe für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Benutzeroberflächen Text und die Terminologie, die in den Hilfe Informationen für Visual Studio verwendet werden.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0b0da682f8403890e57118384b7d979f8760d62f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926150"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Benutzeroberflächentext und -hilfe für Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> UI-Text und-Terminologie
 Verständlicher Text ist entscheidend für die effektive Benutzeroberfläche. Software Benutzer neigen dazu, Bezeichnungen zuerst zu lesen, nämlich diejenigen, die für die Ausführung der Aufgabe am relevantesten sind. Statischer Text wird mit weniger Häufigkeit gelesen. Planen Sie, dass Benutzer ihre Arbeitssitzungen mit einer schnell Überprüfung des gesamten Fensters starten, gefolgt von einem Lesevorgang für die Benutzeroberfläche in dieser ungefähren Reihenfolge:

1. Interaktive Steuerelemente im Mittelpunkt

2. Commit-Schaltflächen

3. Interaktive Steuerelemente gefunden an anderer Stelle

4. Haupt Anleitung

5. Ergänzende Erläuterungen

6. Fenstertitel

7. Anderer statischer Text im Haupttext

### <a name="usage-patterns-for-ui-text"></a>Verwendungs Muster für Benutzeroberflächen Text

#### <a name="title-bar-text"></a>Text der Titelleiste
 Der Titelleisten Text muss mit dem Befehl identisch sein, der die Benutzeroberfläche erzeugt hat.

#### <a name="instructional-text-helper-text"></a>Anweisungs Text (Hilfstext)
 In einigen Dialogfeldern ist es hilfreich, wichtige Haupt Anweisungen anzugeben, um zu erläutern, was im Fenster oder auf der Seite zu tun ist. Dies wird manchmal als "Hilfstext" bezeichnet.

##### <a name="writing-style-rules-for-helper-text"></a>Schreiben von Stilregeln für Hilfstext

- Erläutern Sie das offensichtliche nicht. Wenn dies nicht unbedingt erforderlich ist, sollten Sie keinen Anweisungs Text einschließen.

- Der Anweisungs Text wird immer am oberen Rand des Dialog Felds platziert und sollte auf die Aufgabe verweisen, die ausgeführt wird.

- Erläutern Sie den Benutzern genau, was Sie tun müssen. Vermeiden Sie übermäßige Kommunikation und Redundanz.

- Überprüfen Sie jedes Fenster, und vermeiden Sie doppelte Wörter und Anweisungen.

- Halten Sie den Anweisungs Text kurz. Wenn für bestimmte Benutzer oder Szenarien Weitere Informationen erforderlich sind, geben Sie einen Link zu einem ausführlichen konzeptionellen Online Thema ein.

- Schreiben Sie Ihren Text, sodass jedes Wort gewichtet und notwendig ist.

- Befolgen Sie den vorhandenen Leitfaden von Microsoft für den Text und [Stil und den Ton](/windows/desktop/uxguide/text-style-tone)der [Benutzeroberfläche](/windows/desktop/uxguide/text-ui) .

#### <a name="supplemental-instructions"></a>Ergänzende Anweisungen
 Ergänzende Anweisungen bieten zusätzliche Informationen, die dem Benutzer beim verstehen von Steuerelementen oder Steuerelement Gruppierungen helfen. Dies könnte auch Hinweis Text enthalten, der erforderlich ist, um zu verstehen, welches Format das Eingabe Steuerelement erwartet. Verwenden Sie ergänzende Anweisungen sparsam. Reservieren Sie Sie für Fälle, in denen es wahrscheinlich ist, dass der Benutzer die Auswirkungen der gewünschten Auswahl nicht vollständig versteht.

 ![Screenshot mit der Schaltfläche "Internet Explorer-Optionen" mit zusätzlichem Text unterhalb der Schaltfläche, in der die Auswirkungen der Änderung der Options Einstellungen beschrieben werden.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Ergänzender Text in Visual Studio**

 ![Screenshot des Dialog Felds "Quell Code Verwaltung auswählen" in Visual Studio mit zusätzlichem Text, in dem die einzelnen Optionen für das Quell Code Verwaltungssystem beschrieben werden.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Ergänzender Text in Visual Studio**

#### <a name="infotips"></a>Infotipps
 Häufig ist der Anweisungs Text möglicherweise zu lang, um auf der Benutzeroberfläche direkt zu positionieren, oder er ist möglicherweise nur für neue Benutzer nützlich, wie bei der Übersichtlichkeit für erfahrene Benutzer. In diesem Fall sollte der Text "Anweisungs Text" und "Information" als QuickInfo unter einem infotip abgelegt werden.

 Infotips sollten in der Nähe der Steuerelemente platziert werden, mit denen Sie verknüpft sind, und sollten das spezielle infotip-Symbol verwenden, das unaufdringlich und dennoch spürbar ist.

 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Beispiel eines Infotipps in Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Schreiben von Stilregeln für infotips

- Schreiben Sie infotips als vollständige Sätze. Sie erfordern bestimmte Verben, Sätze und Endpunkte.

- Verwenden Sie infotips, um die Haupt Anweisung oder die Informationen zu ergänzen. Wenn Sie nur verschiedene Wörter verwenden, um die Main-Idee neu zu machen, benötigen Sie keinen infotip.

- Lassen Sie infotips kurz und süß. Verwenden Sie kleine Wörter und eine einfache, alltägliche Sprache, die den Benutzer unterstützt und ermutigt.

- Befolgen Sie den vorhandenen Leitfaden von Microsoft für den Text und [Stil und den Ton](/windows/desktop/uxguide/text-style-tone)der [Benutzeroberfläche](/windows/desktop/uxguide/text-ui) .

#### <a name="control-labels"></a>Steuerelement Bezeichnungen
 Steuerelement Bezeichnungen sollten kurz, präzise und den [Windows-Desktop Anleitungen für Steuerelemente](/windows/desktop/uxguide/controls)entsprechen.

 Weitere Informationen zum Format und zur Platzierung der Steuerelement Bezeichnung in der Benutzeroberfläche finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Hilfe Links
 Hilfe Verknüpfungen können entweder innerhalb des Anweisungs Texts oder im Textkörper der Benutzeroberfläche abgelegt werden. Sie können Links zum Hilfe-oder zum Starten interner Dialogfelder sein.

##### <a name="visual-style-rules-for-help-links"></a>Visuelle Stilregeln für Hilfe Links

- Verwenden Sie die richtigen Umgebungs Farben für Hyperlinks. Ein ordnungsgemäß formatierten Hyperlink wird beim Klicken nicht kurz rot blinkt. Wenn dies angezeigt wird, ist dies ein Hinweis darauf, dass Umgebungs Farben nicht verwendet werden.

- Unterstriche sollten nur auf dem Mauszeiger oder bei der Einbettung des Links in einen Absatz verwendet werden.

- Ausführlichere Informationen zu visuellen und Interaktions Stilen für Hyperlinks finden Sie unter Schaltflächen und Hyperlinks.

##### <a name="writing-style-rules-for-help-links"></a>Schreiben von Stilregeln für Hilfe Links

- Behalten Sie beim Starten von Dialogfeldern die Standards für Ellipsen bei: keine Auslassungs Punkte für die Navigation, Auslassungs Punkte, wenn die Aufgabe zusätzliche Benutzeroberfläche erfordert.

     ![Hilfelink in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Ein Auslassungs Zeichen (...) in einem Hilfelink gibt an, dass der Task zusätzliche Benutzeroberfläche erfordert.**

- Links sollten nicht mit "Learn" beginnen, da dies nicht die Absicht des Benutzers ist. Der Benutzer möchte eine bestimmte Frage beantworten und keine allgemeine Ausbildung erhalten.

- Hilfe Links zur Formulierung, damit Sie die Frage stellen, die das Thema beantworten wird.

     Falsch: "Weitere Informationen zu Windows Azure Mobile Services Preise"

     Richtig: "welche Preisoptionen sind für Windows Azure Mobile Services verfügbar?"

- Verwenden *Sie niemals Click...* zum Linktext.

- Verknüpfen Sie niemals nur das Wort "This". Dies ist für einige Sprachausgaben problematisch, die nur mit dem hyperverknüpften Wort verknüpft werden.

     Falsch: "Informationen zu Windows Azure-Mobile Services finden Sie **hier**".

     Richtig: "welche Preisoptionen sind für Windows Azure Mobile Services verfügbar?"

- Weitere Informationen zum richtigen Schreibstil für Hilfe Links finden Sie in der [Anleitung zum Windows-Desktop](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Hinweis Text
 Der Hinweis Text wird als Wasserzeichen innerhalb eines Steuer Elements oder unterhalb des Steuer Elements angezeigt. Die korrekte Formatierung wird mithilfe des entsprechenden vscolors-Tokens,, angewendet `Environment.GrayText` .

 Sie kann in einer Reihe von Formularen angezeigt werden.

- Anstelle der Steuerelement Bezeichnung:

     ![Screenshot eines Dropdown-Steuer Elements mit Hinweis Text anstelle der Steuerelement Bezeichnung, das "Search Projektmappen-Explorer (STRG +;)") liest.](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Mit einem Verb, das Anweisungen bietet:

     ![Screenshot eines Textfelds mit dem Hinweis Text im-Steuerelement, das "Name eingeben" lautet.](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Mit Text, der einen erforderlichen Eintrag angibt:

     ![Screenshot eines Textfelds mit Hinweis Text im Steuerelement, das " \< Required \> " liest.](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Wasserzeichen Text
 Auf einer leeren Entwurfs Oberfläche sollte der Text angeben, was zu tun ist, und Links zum Öffnen anderer verwandter Fenster bereitstellen, falls dies erforderlich ist:

 ![Wasserzeichentext in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Beispiel für Wasserzeichen Text in Visual Studio**

### <a name="common-terminology"></a>Allgemeine Terminologie

|Begriff|Erklärung|Kommentar|
|----------|-----------------|-------------|
|Anmelden/Abmelden|Verben verwendeten Synonym mit dem Web zum Darstellen der Authentifizierung in einer webeigenschaft. Innerhalb von Clients verwenden wir dies einmal als Konzept der obersten Ebene für die Anmeldung und aus der IDE-Benutzer Verbindung, die eine Identität der obersten Ebene darstellt, die Funktionen auf höherer Ebene bereitstellt, z. b. Roaming und Lizenzierung, die nicht mit allen anderen Verbindungen verfügbar sind.|Der IDE-Benutzer ist die einzige Funktion, die ein Verb für das Anmelden/Abmelden darstellen sollte, da Sie den IDE-Benutzer der obersten Ebene darstellt.|
|Verbindung herstellen/trennen|Verwenden Sie an Orten, an denen eine Funktion eine einzelne Verbindung mit einem Onlinedienst beibehält.|Server-Explorer, in dem Sie jeweils nur eine aktive Azure-Verbindung haben können, ist ein Beispiel für Connect/Disconnect.|
|Hinzufügen/entfernen|Nicht destruktiv. Verwenden Sie, wenn Sie einer Liste etwas hinzufügen oder daraus entfernen.|Das Dialogfeld für den TFS-Verbindungs-Manager-Server ist ein Beispiel für das hinzufügen/entfernen.|
|Löschen|Erisches. Verwenden Sie nur, wenn das zu entfernende Element dauerhaft verworfen oder vom Datenträger gelöscht wird.|"Delete" erfordert im Allgemeinen eine Eingabeaufforderung, wenn das Ergebnis eine Datei von einem Datenträger löscht.|

## <a name="error-messages"></a>Fehlermeldungen

### <a name="overview"></a>Übersicht
 Fehler auftreten. Das Festlegen von Einschränkungen, die der Benutzer ausführen kann, ist ein sinnvoller erster Schritt, um vermeidbare Fehlermeldungen zu verhindern. Wenn jedoch ein Fehler auftritt, kann eine ordnungsgemäß geschriebene Fehlermeldung eine lange Methode zur Minderung des Problems sein. Fehlermeldungen sind wohl eine der wichtigsten Benachrichtigungs Typen, die dem Benutzer angezeigt werden, da sie synchron sind und auf ein Problem hinweisen, das gelöst werden muss. Durch schlecht geschriebene Fehlermeldungen können Benutzer selbst entscheiden, welche Fehlerursache und mögliche Lösungen vorhanden sind.

 Benutzer werden möglicherweise nicht mehr auf die übernutzenden oder verwirrenden Fehlermeldungen achten. schreiben Sie daher nur erforderliche Nachrichten, die den Benutzer nutzen. Wenn es sich bei der Nachricht lediglich um eine Benachrichtigung handelt, verwenden Sie eine Alternative Präsentation.

### <a name="rules-for-creating-an-error-message"></a>Regeln zum Erstellen einer Fehlermeldung

- Wenn Sie Fehlermeldungen erstellen, wählen Sie die entsprechende Fehlerstufe für die Zielgruppe aus. Abzielen Sie auf einfache Zusammenfassungen, die eine Aktion bereitstellen, die der Benutzer ggf. ausführen kann. Geben Sie nichts an, was der Benutzer nicht wissen muss.

- Stellen Sie konstruktive Unterstützung bereit. Es ist einfacher, eine Fehlermeldung zu lesen und zu reagieren, die Anweisungen enthält.

- Verwenden Sie keine doppelten negativen Ergebnisse.

- Führen Sie sowohl eine automatisierte als auch eine manuelle Grammatik und eine Rechtschreibprüfung für jede Fehlermeldung aus, die Sie schreiben.

- Vermeiden Sie für komplexe Fehlermeldungen die sequenzielle Kommunikation. Verwenden Sie für die Fehlermeldung niemals eine F1-Nachricht. Die Meldung selbst sollte ausreichend sein.

- Verwenden Sie das richtige Symbol.

- Stellen Sie Ihre Fragen leicht verständlich, und verwenden Sie Schaltflächen mit klaren Optionen, wie z. b. "Löschen" und "Abbrechen".

- Beachten Sie bei Warnungen, welche Konsequenzen das Fortsetzen des Verfahrens hat. Die Schaltflächen sollten die Folge angeben.

- Beschreiben Sie bei Fehlern, welche Aktionen der Benutzer durchführen kann, um das Problem zu beheben. Schaltflächen sollten Aktionen sein oder "Schließen" lauten. Verwenden Sie für eine Fehlermeldung nicht die Schaltfläche "OK".

- Einige Fragen, die Sie beim Erstellen einer Fehlermeldung stellen müssen:

  - Kann der Benutzer ermitteln, wie das Problem mit diesem Fehler allein gelöst werden soll?

  - Verwendet der Benutzer dasselbe Vokabular wie dieser Fehler?

  - Ist dieser Fehler in mehreren Fällen ambitionös oder freigegeben? Wenn dies der Fall ist, wie leiten Sie Benutzer an die Lösung, die Sie benötigen?

#### <a name="build-errors"></a>Buildfehler
 Da Visual Studio ein Software Entwicklungs Tool ist, verfügen viele Komponenten über einen Kompilierungs-, Konvertierungs-oder Codierungs Schritt, um die Arbeit des Entwicklers in binäre Formulare zu konvertieren. Diese Konvertierungen können Fehler verursachen, wenn der Compiler nicht ordnungsgemäß erstellte Dateien verarbeiten kann oder wenn die Compileroptionen nicht ordnungsgemäß festgelegt wurden.

 Visual Studio-Benutzer können eine enorme Anzahl von Entwicklungsstunden aufwenden, um Buildfehler zu beheben. Diese Auflösungszeit erhöht sich, wenn Fehler Abhängigkeiten aufweisen oder Fehlermeldungen unzureichend geschrieben werden, wodurch es schwierig werden kann, die Quelle des Fehlers zu erkennen.

 Die besten Buildfehler sind solche, die nicht an erster Stelle auftreten, weshalb Visual Studio AutoComplete und IntelliSense-Wellenlinien bereitstellt. Schema Validierungs Steuerelemente und ähnliche Tools bieten dieselbe Art von Feedback. Diese Mechanismen führen den Benutzer proaktiv durch das Erstellen von wohl geformtem Code und verringern die Wahrscheinlichkeit von Buildfehlern.

 Visual Studio stellt ein Tool Fenster bereit, in dem Benutzer die in den Dokument Fenstern aufgetretenen Fehler lesen und durch diese navigieren können. Tastenkombinationen werden bereitgestellt, sodass der Benutzer schnell auf große Mengen von Code navigieren und direkt zum Speicherort des Problems wechseln kann. Visual Studio ermöglicht außerdem, dass jeder Buildfehler an ein bestimmtes Hilfe Schlüsselwort/Kontext-ID gebunden wird, damit der Benutzer direkt zu einem Hilfethema wechseln kann, das ausführlichere Informationen über den Fehler enthält.

 Schreiben Sie klare, präzise Buildfehler:

- **Verwenden Sie eine einfache Sprache** , in der das Problem mit wenig oder ohne compilerjargon erläutert wird. Der Text eines Buildfehlers sollte nicht übermäßig technisch sein.

- **Mögliche Ursachen gliedern.** Beispiel: "fehlende Doppelpunkte zwischen der Eigenschaft und dem Wert in der Deklaration ' (Eigenschaft): (Value)".

- Details zu möglichen Korrekturen. Wenn nicht genügend Platz verfügbar ist, werden möglicherweise weitere Details im entsprechenden Hilfethema abgelegt.

### <a name="components-of-a-well-written-error-message"></a>Komponenten einer gut geschriebenen Fehlermeldung

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Verwenden Sie den Shell-Dialog Dienst für Fehlermeldungen.
 Mithilfe des Shell-Dialog Felds können Sie das Erscheinungsbild der Nachricht, insbesondere Schriftarten, ohne größere Änderungen an einzelnen Elementen steuern. Verwenden Sie die **IErrorInfo** -Mechanismen, und melden Sie Sie mithilfe von **IVsUIShell:: SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wählen Sie eine effektive und geeignete Benachrichtigungs Präsentation aus.
 Verwenden Sie ein modales Dialogfeld mit einer kritischen Warnung, wenn sofortige Maßnahmen erforderlich sind, um Datenverluste zu vermeiden (synchrone Benachrichtigung). Kritische Symbole sind für Situationen reserviert, in denen das Schließen der Nachricht ohne Lesevorgang zu negativen Konsequenzen führen kann. Der Verlust von Daten ist eine kritische Situation, die eine Antwort auf Alarm Ebene erfordert. Durch die über Verwendung des kritischen Symbols werden Benutzer auf ihre Wichtigkeit herabgesetzt. Wenn die Fehlermeldung in der Art "Information" ist, sollten Sie Alternativen zu einem modalen Dialogfeld (asynchrone Benachrichtigung) Unternehmen.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Sorgen Sie für eine saubere, prägnante Erläuterung, warum das Problem statt einer technischen Erklärung aufgetreten ist.
 Wenn Sie Benutzer mit technischen Details in der Erklärung überlastet haben, werden Sie die Wahrscheinlichkeit erhalten, dass Fehlermeldungen ignoriert werden. Beispiele für gutes Messaging:

- "Die angeforderte Datei kann nicht geöffnet werden."

- "Es kann keine Verbindung mit dem Internet hergestellt werden."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Geben Sie Informationen zum Beheben des Problems an.
 Geben Sie die Benutzer Vorschläge zur Behebung des Problems an. Wenn keine Vorschläge vorhanden sind, ist der Benutzer ehrlich. Stellen Sie direkte Links zu alternativen Online Quellen bereit, z. b. technischen Support oder CommunitySupport. Versuchen Sie, Benutzer auf bestimmte Online Informationen zu verweisen, die für das Problem relevant sind. Bei einer Fehler-ID sollten Sie Benutzer mit einem Diskussions Thread zu diesem speziellen Fehler verknüpfen. Beispiele für gutes Messaging:

- "Stellen Sie sicher, dass Sie mit dem Internet verbunden sind, und wiederholen Sie den Vorgang."

- "Stellen Sie sicher, dass die Datei vorhanden ist und Sie über die Berechtigung zum Öffnen verfügen."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Schreiben Sie eine Nachricht, die kurz und bis zum Punkt ist.
 Eine Fehlermeldung kann eine Projekt Mappe Benachrichtigen, erläutern und anbieten, aber dennoch ignoriert werden, wenn Sie zu viel zu tun hat. Eine Lösung besteht darin, die Progressive Offenlegung mit der Schaltfläche Details zu verwenden. Geben Sie z. b. eine kurze Beschreibung/Projekt Mappe an, und fügen Sie dann weitere Details unter der Schaltfläche Details ein. Wenn Benutzer weitere Informationen zu dem Fehler lesen möchten, können Sie dies tun.

 Die Sprache in der Nachricht sollte wie folgt lauten:

- **Domänen Bedarf.** Sprache verwenden, die der Benutzer versteht. Obwohl es sich bei unseren Kunden um Entwickler handelt, haben Sie oft nicht den Kontext und die Terminologie, die wir haben.

- **Zugeschnitten.** Vermeiden Sie eine vage Formulierung, und weisen Sie bestimmte Namen und Speicherorte von Objekten an. Beispielsweise ist eine Fehlermeldung wie z. b. "Zeichen ist ungültig" nicht nützlich. Welches Zeichen? "Die Datei wurde nicht gefunden." Welche Datei?

- **Liche.** Machen Sie die Verantwortung für den Benutzer nicht, oder machen Sie das Gefühl nicht Vermeiden Sie eine feindliche oder anstößige Sprache (Kill, Execute, End, fatal, unzulässig). Vermeiden Sie Großbuchstaben, die häufig als schreiende und nicht als lesbar angesehen werden. Verwenden Sie keinen Humor.

- **Richtig.** Verwenden Sie die richtige Rechtschreibung und Grammatik (auch in Alphas). Typos sind nicht professionell und peinlich.

- **Passend.** Verwenden Sie den entsprechenden Schaltflächen Text. Vermeiden Sie die Schaltfläche "OK", und verwenden Sie stattdessen "Continue" oder "Yes/No".

### <a name="error-message-examples"></a>Beispiele für Fehlermeldungen

|Gut|Schlecht|
|----------|---------|
|"Die gewählte Zahl ist nicht mehr im Dienst. Überprüfen Sie die Zahl, und wählen Sie erneut aus, oder wählen Sie 0 für den Operator aus. "|-"Fehler (449): ungültige Zahl"<br />-"Dieser Fehler bei nicht behandelten Ausnahmen weist darauf hin, dass der Vorgang erfolgreich abgeschlossen wurde."<br /><br /> ![Ungültige Fehlermeldung in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Zugreifen auf die Hilfe

### <a name="overview"></a>Übersicht
 Neben der Dokumentation in MSDN bietet ein Visual Studio-Benutzer mehrere Zugriffspunkte, um den Benutzer während der Benutzeroberfläche zu unterstützen. Um sicherzustellen, dass diese Zugriffspunkte konsistent verfügbar sind, müssen die Funktions Teams das von der Umgebung angebotene Hilfesystem nutzen. Diese Zugriffspunkte lauten:

- **Anweisungs-und ergänzender Text in Dialogfeldern.** Statischer Text, der Richtung oder Erklärung entweder auf der UI-Oberfläche oder auf einem infotip-Symbol angezeigt wird.

- **F1-Hilfe** (nur Editor). Innerhalb des Visual Studio-Editors kann ein Benutzer jederzeit darauf vertrauen, dass durch Drücken von F1 ein Hilfethema für die aktuelle Auswahl angezeigt wird. Stellen Sie sicher, dass die mit F1 verknüpften Themen geeignet und informativ sind.

- **Links zu Hilfe Themen.** Ein Link in einem Dialogfeld, einem Tool Fenster oder einer Entwurfs Oberfläche, mit dem ein Thema gestartet wird, mit dem der Benutzer mehr über eine Technologie, eine Funktion oder Informationen zum Ausführen einer Aufgabe erfahren kann.

- **Hilfsmechanismen für die Benutzeroberfläche, z. b. Smarttags und Dialogfelder** Diese Mechanismen unterstützen den Benutzer beim Verständnis eines UI-Elements oder beim vereinfachen einer Aufgabe, z. b. Smarttags oder Generator Dialogfelder.

- Hilfe Schaltflächen für die **Benutzeroberfläche** (veraltet). Ein sichtbarer Indikator in der Titelleiste, der den Zugriff auf das verwandte F1-Hilfethema ermöglicht.

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Anweisungs-und ergänzender Text in Dialogfeldern
 In Dialogfeldern, die komplexe Aufgaben unterstützen, ist es möglicherweise notwendig, einen Anweisungs Text in der Benutzeroberfläche anzugeben, häufig am oberen Rand des Dialog Felds oder in der Nähe komplexer Steuerelemente. Ausführliche Informationen zum Schreiben von Style finden Sie unter [UI-Text und-Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>Infotipps
 Häufig ist der Anweisungs Text möglicherweise zu lang, um auf der Benutzeroberfläche positioniert zu werden, oder er ist möglicherweise nur für neue Benutzer nützlich, wie bei der Übersichtlichkeit für erfahrene Benutzer. In diesem Fall sollte der Text "Anweisungs Text" und "Information" als QuickInfo unter einem infotip abgelegt werden.

 Infotips sollten in der Nähe der Steuerelemente platziert werden, mit denen Sie verknüpft sind, und sollten das spezielle infotip-Symbol verwenden, das unaufdringlich und dennoch spürbar ist.

 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Beispiel eines Infotipps in Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktive Hilfe Mechanismen

#### <a name="f1-help"></a>F1-Hilfe
 Die F1-Hilfe ist innerhalb eines Editors oder einer Entwurfs Oberfläche erforderlich, aber nicht an anderer Stelle in der Visual Studio-Umgebung.

#### <a name="hyperlinks-to-help-topics"></a>Links zu Hilfe Themen
 Hyperlinks können verwendet werden, um eine Aktion auszuführen, in der IDE zu navigieren oder die Hilfe in einem Browser zu starten. Ausführliche Informationen zu Sprach-und 07.10.01-Schaltflächen und Hyperlinks für visuelle und Layoutrichtlinien finden Sie unter [UI-Text und-Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Hilfe [?]-Schaltflächen in Dialog Titelleisten (veraltet)
 In den meisten Fällen sind die Schaltflächen Hilfe [?] in der Titelleiste von Dialogfeldern veraltet. Benutzeroberflächen Themen sind nicht mehr Bestandteil unseres doc-Modells. Daher gibt es möglicherweise kein relevantes Thema, mit dem Sie eine Verknüpfung herstellen können. Im Wesentlichen war die Titelleisten Schaltfläche identisch mit der F1-Hilfe, und das ist in Dialogfeldern nicht mehr erforderlich. In einigen Fällen kann dies weiterhin als Indikator verwendet werden, dass weitere konzeptionelle oder prozedurale Informationen verfügbar sind, obwohl Hyperlinks in neueren Benutzeroberflächen häufiger verwendet werden.

##### <a name="dialogs-created-through-the-environment"></a>Durch die Umgebung erstellte Dialoge
 Viele shelldialogfelder werden über die **vbdialogboxparam** -Funktion erstellt. Diese freigegebene Funktion wurde aktualisiert, um das Verschieben der **Hilfe** Schaltfläche aus dem Dialogfeld in zu unterstützen **?** , während eine Architektur beibehalten wird, die abwärts kompatibel und erweiterbar ist.

 Insbesondere sucht die **vbdialogboxparam** -Funktion in der Dialogfeld Vorlage nach einer Schaltfläche mit der ID **IDHELP** (9) oder der Bezeichnung " **Hilfe** " oder **&Hilfe**. Wenn eine Hilfe Schaltfläche gefunden wird, wird Sie ausgeblendet, und der **WS_EX_CONTEXTHELP** Stil **wird dem Dialog** Feld hinzugefügt. Schaltfläche in der Titelleiste des Dialog Felds.

 Wenn das Dialogfeld erstellt wird, wird das Dialogfeld proc auf einen Stapel übertragen und das Dialogfeld mit einem Vorverarbeitungs **Dialogfeld mit dem Namen dialogpreproc** aufgerufen. Wenn **?** auf die Schaltfläche wird geklickt, es wird eine **WM_SYSCOMMAND** **SC_CONTEXTHELP** an den Dialog gesendet. Der **dialogpreproc** erfasst diesen Befehl und ändert ihn in eine **WM_HELP** Nachricht, die an die ursprüngliche Dialogfeld Prozedur übergeben wird.

 Die meisten von der Umgebung erstellten Dialogfelder haben eine Schaltfläche "Hilfe" im Dialogfeld. Wenn das Dialogfeld angezeigt wird, wird die Schaltfläche Hilfe automatisch ausgeblendet, und nur die Schaltfläche **?** die Schaltfläche funktioniert. Wenn **?** Wenn die Schaltfläche in Windows entfernt oder geändert wird, können Sie mit dieser Lösung schnell zu den ursprünglichen Hilfe Schaltflächen zurück wechseln.

 Diese Lösung führt vier Annahmen aus, die zu Fehlern führen können:

- Die Schaltfläche Hilfe des Dialog Felds ist **IDHELP** (9).

- Wenn die Schaltfläche Hilfe ausgeblendet ist, wird das Dialogfeld korrekt angezeigt.

- Das Dialogfeld ersetzt nicht seine WinProc.

- Das Dialogfeld ist nicht in einem anderen Dialogfeld eingebettet.

  Wenn sich das Dialogfeld in msenv befindet und nicht **vbdialogboxparam** verwendet, sollten Sie die Nutzung von **vbdialogboxparam** vor der Implementierung Ihres eigenen Handlers untersuchen.

##### <a name="dialogs-created-through-other-packages"></a>Durch andere Pakete erstellte Dialoge
 Sie können Ihre eigene Lösung für Dialogfelder implementieren, die sich außerhalb von msenv befinden. Erwägen Sie für eine freigegebene Dialogfeld Klasse in Ihrem VSPackage die Verschiebung der Schaltfläche auf die Titelleiste oder die Implementierung eines Handlers für die einzelnen Dialogfelder. Der folgende Code ist ein Skelett einer Implementierung, die Ihnen beim Einstieg hilft:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Hilfe Schaltflächen in verwaltetem Code
 Das Standardverhalten der Hilfe Schaltfläche der Fenstertitelleiste wird in verwaltetem Code einfach überschrieben. Im folgenden finden Sie eine umfassende Demoanwendung, die dieses Verhalten veranschaulicht. Im Wesentlichen müssen Sie die **WndProc** -Methode Ihres Formulars überschreiben und dann F1-Hilfe Anforderungen auslösen, wenn eine **SC_CONTEXTHELP** Nachricht abgefangen wird.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Schriftarten und Formatierung für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
