---
title: Ermitteln von Änderungen am Code und andere Verläufe mit CodeLens
description: Erfahren Sie mehr über CodeLens, und wie Sie es verwenden können, um den Verlauf Ihres Codes zu untersuchen, ohne den Editor verlassen zu müssen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 485287239a13f61d10ee39bad854a0f3bdae4f55
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006704"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Ermitteln von Änderungen am Code und andere Verläufe mit CodeLens

Mit CodeLens können Sie sich auf Ihre Arbeit konzentrieren, während Sie ermitteln, was mit Ihrem Code geschehen ist. Dazu müssen Sie nicht einmal den Editor schließen. Suchen Sie Verweise auf Codeabschnitte und -änderungen, verknüpfte Fehler, Arbeitselemente, Code Reviews und Komponententests.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens ist in Visual Studio Community Edition verfügbar. Die Indikatoren für die *Quellcodeverwaltung* sind in der Visual Studio Community Edition jedoch nicht verfügbar.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens steht nur in Visual Studio Enterprise- und Professional-Versionen zur Verfügung. Es ist nicht in Visual Studio Community verfügbar.

::: moniker-end

Sehen Sie, wo und wie die einzelnen Codeausschnitte in der Projektmappe verwendet werden:

![CodeLens-Indikatoren im Code-Editor](../ide/media/codelens-overview.png)

Diskutieren Sie die Codeänderungen mit Ihrem Team, ohne den Editor verlassen zu müssen:

![CodeLens – Sich an das Team wenden](../ide/media/codelens-contact-info.png)

Um die Indikatoren auswählen, die Sie anzeigen möchten, oder CodeLens zu aktivieren bzw. deaktivieren, navigieren Sie zu **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Referenzen zu Ihrem Code finden

Sie können Verweise in C#- oder Visual Basic-Code suchen.

1. Klicken Sie auf den Indikator **Verweise**, oder drücken Sie **ALT**+**2**.

   ![CodeLens-Verweise](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Wenn der Indikator **0 Verweise** anzeigt, bedeutet dies lediglich, dass Sie über keine Verweise aus C#- oder Visual Basic-Code verfügen. Allerdings können Verweise immer noch in anderen Elementen vorhanden sein, z.B. in *XAML-* und *ASPX-Dateien*.

2. Zeigen Sie mit dem Mauszeiger auf den Verweis in der Liste, um den verweisenden Code anzuzeigen.

   ![CodeLens – Peek-Verweis](../ide/media/codelens-peek-reference.png)

3. Führen Sie einen Doppelklick auf den Verweis aus, um die Datei zu öffnen, die den Verweis enthält.

### <a name="code-maps"></a>Codezuordnungen

[Erstellen Sie eine Code Map](../modeling/map-dependencies-across-your-solutions.md), um die Beziehungen zwischen dem Code und seinen Verweisen anzuzeigen. Wählen Sie im Code Map-Kontextmenü **Alle Verweise anzeigen** aus.

![CodeLens – Verweise in Codezuordnung](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Suchen nach Änderungen im Code

Überprüfen Sie den Codeverlauf, um zu ermitteln, was mit Ihrem Code geschehen ist. Sie können die Änderungen auch überprüfen, bevor sie mit Ihrem Code zusammengeführt werden. Auf diese Weise können Sie besser beurteilen, wie sich Änderungen in anderen Verzweigungen möglicherweise auf Ihren Code auswirken.

Erforderlich:

- Visual Studio Enterprise- oder Professional-Edition

- Azure DevOps Services, Team Foundation Server 2013 oder höher, Azure DevOps Services oder Git

- [Skype for Business](/skypeforbusiness/) für das Kontaktieren Ihres Teams über den Code-Editor

Detaillierte Informationen zu CodeLens für C#- oder Visual Basic-Code, der mit der Team Foundation-Versionskontrolle (TFVC) oder Git gespeichert ist, finden Sie auf den Klassen- und Methodenebenen (*Codeindikatoren auf Elementebene*). Wenn Ihr Git-Repository in TfGit gehostet ist, finden Sie auch Links zu TFS-Arbeitselementen.

![Codeindikatoren auf Elementebene](../ide/media/codelens-element-level-indicators.png)

Bei anderen Dateitypen als *CS* oder *VB* erhalten Sie detaillierte Informationen zu CodeLens für die gesamte Datei am unteren Rand des Fensters (*Indikatoren auf Dateiebene*).

![CodeLens-Indikatoren auf Dateiebene](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Codeindikatoren auf Elementebene

Codeindikatoren auf Elementebene zeigen Ihnen an, wer welche Änderungen an Ihrem Code vorgenommen hat. Codeindikatoren auf Elementebene sind für C#- und Visual Basic-Code verfügbar.

Wenn Sie die Team Foundation-Versionskontrolle (TFVC) in Team Foundation Server oder Azure DevOps Services verwenden, wird die folgende Ansicht angezeigt:

![CodeLens: Änderungsprotokoll für den Code in TFVC abrufen](../ide/media/codelens-code-changes.png)

Der Standardzeitraum umfasst die letzten 12 Monate. Wenn Ihr Code in Team Foundation Server gespeichert ist, können Sie den Zeitraum ändern, indem Sie den [TFSConfig-Befehl](/azure/devops/server/command-line/tfsconfig-cmd) mit dem [CodeIndex-Befehl](../ide/codeindex-command.md) und dem Flag **/indexHistoryPeriod** ausführen.

Zum Anzeigen eines ausführlichen Verlaufs aller Änderungen, einschließlich der von vor über einem Jahr, wählen Sie **Alle Dateiänderungen anzeigen** aus:

![Alle Codeänderungen anzeigen](../ide/media/codelens-show-all-file-changes.png)

Das Fenster **Versionsgeschichte** wird geöffnet:

![Verlaufsfenster für alle Codeänderungen](../ide/media/codelenscodechangeshistory.png)

Wenn Ihre Dateien sich in einem Git-Repository befinden und Sie den Codeindikator für Änderungen auf Elementebene auswählen, wird Folgendes angezeigt:

![CodeLens: Änderungsprotokoll für den Code in Git abrufen](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Indikatoren auf Dateiebene

Suchen Sie in den Indikatoren auf Dateiebene am unteren Rand des Fensters nach Änderungen für eine gesamte Datei:

![CodeLens: Codedateidetails abrufen](../ide/media/codelens-file-level.png)

> [!NOTE]
> Indikatoren auf Dateiebene sind für C#- und Visual Basic-Dateien nicht verfügbar.

Um weitere Details zu einer Änderung zu erhalten, klicken Sie mit der rechten Maustaste auf dieses Element. Abhängig davon, ob Sie TFVC oder Git verwenden, stehen Ihnen mehrere Optionen zum Vergleichen der Dateiversionen, zum Anzeigen detaillierter Informationen und zum Nachverfolgen von Änderungen, zum Abrufen der ausgewählten Dateiversion und zum Senden einer E-Mail an den Autor einer Änderung zur Verfügung. Einige dieser detaillierten Informationen werden in **Team Explorer** angezeigt.

Sie können auch sehen, wer den Code in einem bestimmten Zeitraum geändert hat. Dadurch können Sie Muster bei den Änderungen Ihres Teams erkennen und ihre Auswirkung bewerten.

![CodeLens: Anzeigen des Verlaufs von Codeänderungen als Diagramm](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Änderungen in der aktuellen Verzweigung finden

Möglicherweise verfügt Ihr Team über mehrere Branches, z.B. einen Hauptbranch und einen untergeordnete Entwicklungsbranch, um das Risiko von Schäden an stabilem Code zu verringern.

![CodeLens: Änderungen in der aktuellen Verzweigung finden](../ide/media/codelensfirstbranchconceptual.png)

Sie können herausfinden, wie viele Personen Ihren Code geändert haben und wie viele Änderungen am Hauptbranch vorgenommen wurden, indem Sie **ALT**+**6** drücken:

![CodeLens: Erfahren, wie viele Änderungen in Ihrer Verzweigung vorhanden sind](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Sehen, wann Ihr Code verzweigt wurde

Navigieren Sie im untergeordneten Branch zu Ihrem Code, um herauszufinden, wann Ihr Code gebrancht wurde. Klicken Sie dann auf den Indikator **Änderungen**, oder drücken Sie **ALT**+**6**:

![CodeLens: Sehen, wann Ihr Code verzweigt wurde](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Eingehende Änderungen aus anderen Verzweigungen sehen

![CodeLens: Codeänderungen in anderen Verzweigungen sehen](../ide/media/codelensbranchchangecheckinconceptual.png)

Sie können eingehende Änderungen anzeigen. Im folgenden Screenshot wurde ein Fehler im Branch „Dev“ behoben:

![CodeLens: Aktiviertes in andere Verzweigung ändern](../ide/media/codelens-branch-changes-dev.png)

Sie können die Änderung überprüfen, ohne den aktuelle Branch zu verlassen (Hauptbranch):

![CodeLens: Eingehende Änderungen von anderer Verzweigung sehen](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Herausfinden, wann Änderungen zusammengeführt wurden

Sie können sehen, wann die Änderungen zusammengeführt wurden, sodass Sie ermitteln können, welche Änderungen in Ihrem Branch enthalten sind:

![CodeLens: Herausfinden, wann Änderungen zusammengeführt wurden](../ide/media/codelensbranchmergedconceptual.png)

Zum Beispiel enthält der Code im Hauptbranch jetzt die Fehlerkorrektur des Branches „Dev“:

![CodeLens - Zusammengeführte Änderungen zwischen Verzweigungen](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Vergleichen einer eingehenden Änderung mit der lokalen Version

Vergleichen Sie eine eingehende Änderung mit Ihrer lokalen Version, in dem Sie **UMSCHALT**+**F10** drücken oder einen Doppelklick auf das Changeset ausführen.

![CodeLens: Eingehende Änderung mit lokaler vergleichen](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Symbole für Branches

Das Symbol in der Spalte **Branch** gibt die Beziehung des Branches zu dem Branch an, in dem Sie arbeiten.

|**Symbol:**|**Ursprung der Änderung:**|
|--------------| - |
|![CodeLens: Änderung des Symbols für aktuelle Verzweigung](../ide/media/codelensbranchcurrenticon.png)|Die aktuelle Verzweigung|
|![CodeLens: Symbol für Änderungen durch den übergeordneten Branch](../ide/media/codelensbranchparenticon.png)|Die übergeordnete Verzweigung|
|![CodeLens: Änderung vom Symbol für untergeordnete Verzweigung](../ide/media/codelensbranchchildicon.png)|Eine untergeordnete Verzweigung|
|![CodeLens: Symbol für Änderungen durch einen Peerbranch](../ide/media/codelensbranchpeericon.png)|Eine Peerverzweigung|
|![CodeLens: Symbol für Änderungen durch einen weiter entfernten Branch](../ide/media/codelensbranchfurtherawayicon.png)|Eine Verzweigung, die sich weiter entfernt befindet als über- oder untergeordnet und Peer|
|![CodeLens: Vom übergeordneten Symbol zusammenführen](../ide/media/codelensbranchmergefromparenticon.png)|Eine Zusammenführung von der übergeordneten zu einer untergeordneten Verzweigung|
|![CodeLens: Vom Symbol für untergeordnete Verzweigung zusammenführen](../ide/media/codelensbranchmergefromchildicon.png)|Eine Zusammenführung von der untergeordneten zu einer übergeordneten Verzweigung|
|![CodeLens: Vom Symbol für nicht zugeordnete Verzweigung zusammenführen](../ide/media/codelensbranchmergefromunrelatedicon.png)|Eine Zusammenführung von einer nicht verwandten Verzweigung (Zusammenführung ohne Basis)|

## <a name="linked-work-items"></a>Verknüpfte Arbeitselemente

Suchen Sie verknüpfte Arbeitselemente, indem Sie auf den Indikator **Arbeitselemente** klicken oder **ALT**+**8** drücken.

![CodeLens – Arbeitselemente für bestimmten Code suchen](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Verknüpfte Code Reviews

Suchen Sie verknüpfte Code Reviews, indem Sie auf den Indikator **Reviews** klicken. Halten Sie die **ALT**-Taste gedrückt, und drücken Sie dann die **NACH-LINKS-TASTE** oder die **NACH-RECHTS-TASTE**, um die Indikatoroptionen mit der Tastatur zu navigieren.

![CodeLens – Codeüberprüfungsanforderungen anzeigen](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Verknüpfte Fehler

Suchen Sie verknüpfte Fehler, indem Sie auf den Indikator **Fehler** klicken oder **ALT**+**7** drücken.

![CodeLens – Mit Changeset verknüpfte Fehler finden](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Den Besitzer eines Elements kontaktieren

Suchen Sie den Autor eines Elements, indem Sie auf den Indikator **Autoren** klicken oder **ALT**+**5** drücken.

![Den Besitzer eines Elements kontaktieren](../ide/media/codelens-contact-item-owner.png)

Öffnen Sie das Kontextmenü für ein Element, um die Kontaktoptionen anzuzeigen. Wenn Sie Lync oder Skype for Business installiert haben, werden folgende Optionen angezeigt:

![Kontaktoptionen für ein Element](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Zugehörige Komponententests

Sie können weitere Komponententests für Ihren C#- oder Visual Basic-Code ermitteln, ohne den **Test-Explorer** öffnen zu müssen.

1. Navigieren Sie zum Anwendungscode, der über zugehörigen [Komponententestcode](../test/unit-test-your-code.md) verfügt.

2. Falls Sie Ihre Anwendung noch nicht erstellt haben, holen Sie dies nach, um die CodeLens-Testindikatoren zu laden.

3. Überprüfen Sie die Tests für den Code, indem Sie **ALT**+**3** drücken.

     ![CodeLens – Teststatus im Code-Editor auswählen](../ide/media/codelens-choose-test-indicator.png)

4. Wenn das Warnsymbol ![Warnsymbol](../ide/media/codelenstestwarningicon.png)angezeigt wird, wurden die Tests noch nicht ausgeführt. Führen Sie sie also aus.

     ![CodeLens – Noch nicht ausgeführte Komponententests anzeigen](../ide/media/codelens-tests-not-yet-run.png)

5. Zum Überprüfen der Definition eines Tests doppelklicken Sie im CodeLens-Indikatorfenster auf das Testelement, um die Codedatei im Editor zu öffnen.

     ![CodeLens – Zur Komponententestdefinition wechseln](../ide/media/codelens-unit-test-definition.png)

6. Klicken Sie auf den Teststatusindikator (![Symbol für fehlerhaften Test](../ide/media/codelenstestfailedicon.png) oder ![Symbol für erfolgreichen Test](../ide/media/codelenstestpassedicon.png)), oder drücken Sie **ALT**+**1**, um die Ergebnisse des Tests zu überprüfen.

     ![CodeLens – Komponententestergebnis anzeigen](../ide/media/codelens-unit-test-result.png)

7. Zum Überprüfen, wie viele Personen diesen Test geändert haben, wer ihn geändert hat oder wie viele Änderungen an diesem Test durchgeführt wurden, [ermitteln Sie den Codeverlauf](#find-changes-in-your-code) und verknüpfte Elemente.

## <a name="keyboard-shortcuts"></a>Tastenkombinationen

Drücken und halten Sie zum Auswählen von Indikatoren über die Tastatur die **ALT**-Taste, um die zugehörigen Nummerntasten anzuzeigen, und drücken Sie dann die Nummer, die dem Indikator entspricht, den Sie auswählen möchten.

![Tastaturzugriffsnummern](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Halten Sie die **ALT**-Taste gedrückt, und verwenden Sie die Pfeiltasten zum Navigieren, um den Indikator **Reviews** auszuwählen.

## <a name="q--a"></a>Fragen und Antworten

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>Frage: Wie aktiviere oder deaktiviere ich CodeLens, bzw. wie wähle ich die anzuzeigenden Indikatoren aus?

**A:**  Sie können die Indikatoren aktivieren und deaktivieren, mit Ausnahme des Verweisindikators. Navigieren Sie zu **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **CodeLens**.

Wenn die Indikatoren aktiviert wurden, können Sie die CodeLens-Optionen auch über die Indikatoren öffnen.

![CodeLens - Indikatoren aktivieren oder deaktivieren](../ide/media/codelensturnoffonindicatorsfromcode.png)

Aktivieren bzw. deaktivieren Sie CodeLens-Indikatoren auf Dateiebene mithilfe der Chevron-Symbole unten im Editor-Fenster.

![Dateiebenenindikatoren aktivieren und deaktivieren](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>F: Wo befindet sich CodeLens?

**A**: CodeLens wird in C#- und Visual Basic-Code auf der Methoden-, Klassen-, Indexer- und Eigenschaftsebene angezeigt. CodeLens wird auf Dateiebene für alle anderen Dateitypen angezeigt.

- Stellen Sie sicher, dass CodeLens aktiviert ist. Navigieren Sie zu **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **CodeLens**.

- Wenn Ihr Code in TFS gespeichert ist, stellen Sie sicher, dass die Codeindizierung aktiviert ist. Verwenden Sie hierzu den [CodeIndex-Befehl](../ide/codeindex-command.md) mit dem [TFSConfig-Befehl](/azure/devops/server/command-line/tfsconfig-cmd).

- DevOps-bezogene Indikatoren werden nur angezeigt, wenn Arbeitselemente mit dem Code verknüpft sind und Sie über Berechtigungen zum Öffnen verknüpfter Arbeitselemente verfügen. Stellen Sie sicher, dass Sie über [Teammitgliedsberechtigungen](/azure/devops/organizations/security/view-permissions?view=vsts&preserve-view=true) verfügen.

- Komponententestindikatoren werden nicht angezeigt, wenn der Anwendungscode nicht über Komponententests verfügt. Teststatusindikatoren werden automatisch in Testprojekten angezeigt. Wenn Sie wissen, dass der Anwendungscode über Komponententests verfügt, die Testindikatoren jedoch nicht angezeigt werden, versuchen Sie, die Projektmappe zu erstellen (**STRG**+**UMSCHALT**+**B**).

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens ist in Visual Studio Community Edition verfügbar. Die Indikatoren für die *Quellcodeverwaltung* sind in der Visual Studio Community Edition jedoch nicht verfügbar.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens ist nicht in Visual Studio Community verfügbar.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>F: Warum sehe ich keine Arbeitselementdetails für einen Commit?

**A:** Dies kann passieren, wenn CodeLens die Arbeitselemente in Azure Boards oder TFS nicht finden kann. Stellen Sie sicher, dass Sie mit dem Projekt verbunden sind, das diese Arbeitselemente enthält, und dass Sie über die erforderlichen Berechtigungen verfügen, diese Arbeitselemente anzuzeigen. Arbeitselementdetails werden möglicherweise ebenfalls nicht angezeigt, wenn die Commitbeschreibung falsche Informationen zu den Arbeitselement-IDs in Azure Boards oder TFS enthält.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>F: Warum sehe ich keine Skype-Indikatoren?

**A:** Skype-Indikatoren werden nicht angezeigt, wenn Sie nicht bei Skype for Business angemeldet sind, es nicht installiert haben oder über keine unterstützte Konfiguration verfügen. Allerdings können Sie weiterhin E-Mails senden:

![CodeLens – Sich per E-Mail an den Besitzer des Changesets wenden](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Welche Skype- und Lync-Konfigurationen werden unterstützt?**

- Skype for Business(32-Bit- oder 64-Bit)

- Lync 2010 oder höher allein (32-Bit- oder 64-Bit), aber nicht Lync Basic 2013 mit Windows 8.1

CodeLens unterstützt nicht die Installation verschiedener Versionen von Lync oder Skype. Sie sind möglicherweise nicht für alle lokalisierten Versionen von Visual Studio lokalisiert.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>F: Wie ändere ich Schriftart und Farbe für CodeLens?

**A:** Navigieren Sie zu **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben**.

![CodeLens – Schriftart- und Farbeinstellungen ändern](../ide/media/codelensoptionsfontscolorssettings.png)

So verwenden Sie die Tastatur:

1. Drücken Sie **ALT**+**T**+**O**, um das Dialogfeld **Optionen** zu öffnen.

2. Drücken Sie die **NACH-OBEN-TASTE** oder die **NACH-UNTEN-TASTE** , um zum Knoten **Umgebung** zu wechseln, und dann die **NACH-LINKS-TASTE** , um den Knoten zu erweitern.

3. Drücken Sie die **NACH-UNTEN-TASTE** , um zu **Schriftarten und Farben** zu wechseln.

4. Drücken Sie die **TAB-TASTE**, um zur Liste **Einstellungen anzeigen für** zu wechseln, und drücken Sie dann die **NACH-UNTEN-TASTE**, um **CodeLens** auszuwählen.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>F: Kann ich das CodeLens-Heads-up-Display verschieben?

**A:** Ja, klicken Sie auf ![Andocksymbol](../ide/media/codelensdockwindow.png), um CodeLens als Fenster anzudocken.

![Schaltfläche „Andocken“ im CodeLens-Indikatorfenster](../ide/media/codelensselectdockwindow.png)

![Angedocktes CodeLens-Verweisfenster](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>F: Wie aktualisiere ich die Indikatoren?

**A:** Dies hängt vom Indikator ab:

- **Verweise**: Dieser Indikator wird bei einer Änderung des Codes automatisch aktualisiert. Wenn der Indikator **Verweise** als separates Fenster angedockt ist, aktualisieren Sie den Indikator, indem Sie auf **Aktualisieren** klicken:

   ![Schaltfläche „Aktualisieren“ in CodeLens-Verweise](../ide/media/codelensviewreferencesdocked.png)

- **Team:** Aktualisieren Sie diese Indikatoren, indem Sie im Kontextmenü auf **CodeLens-Teamindikatoren aktualisieren** klicken:

   ![Menüelement „CodeLens-Teamindikatoren aktualisieren“](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test:**[Suchen von Komponententests für Ihren Code](#associated-unit-tests) zum Aktualisieren des Indikators **Test**.

### <a name="q-whats-local-version"></a>F: Was bedeutet „Lokale Version“?

**A:** Der Pfeil **Lokale Version** zeigt auf das neueste Changeset in der lokalen Version einer Datei. Wenn der Server über neuere Changesets verfügt, werden sie je nach Reihenfolge, in der sie sortiert sind, über oder unter dem Pfeil **Lokale Version** angezeigt.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>F: Kann ich verwalten, wie CodeLens den Code verarbeitet, um den Verlauf und verknüpfte Elemente anzuzeigen?

**A:** Ja. Wenn sich der Code in TFS befindet, können Sie hierzu den [CodeIndex-Befehl](../ide/codeindex-command.md) mit dem [TFSConfig-Befehl](/azure/devops/server/command-line/tfsconfig-cmd) verwenden.

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>F: Meine CodeLens-Testindikatoren werden beim ersten Öffnen der Projektmappe nicht mehr in meiner Datei angezeigt. Wie kann ich sie laden?

**A:** Erstellen Sie Ihr Projekt erneut, damit die CodeLens-Testindikatoren in Ihre Datei geladen werden. Zur Verbesserung der Leistung ruft Visual Studio beim Laden von Codedateien keine Quellinformationen mehr für Testindikatoren ab. Testindikatoren werden geladen, nachdem ein Build geladen wurde, oder wenn Sie zu einem Test navigieren, indem Sie im **Test-Explorer** darauf doppelklicken.

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
