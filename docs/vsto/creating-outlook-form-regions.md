---
title: Erstellen von Outlook-Formular Bereichen
description: Erfahren Sie, wie Sie Formular Bereiche zum Anpassen von Microsoft Outlook-Formularen für das Entwerfen, entwickeln und Debuggen von Formular Bereichen verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba2c4412b344a37e1b1db74cdddea8c5b60b69d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947892"
---
# <a name="create-outlook-form-regions"></a>Erstellen von Outlook-Formular Bereichen
  Formularbereiche können zum Anpassen von Microsoft Office Outlook-Formularen verwendet werden. Visual Studio bietet erweiterte Tools, die Ihnen das Entwerfen, Entwickeln und Debuggen von Formularbereichen erleichtern.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Dieses Thema enthält die folgenden Informationen:

- [Vorteile der Verwendung von Formular Bereichen](#Enhance)

- [Hinzufügen eines Outlook-Formular Bereichs zu Ihrem Projekt](#Adding)

- [Verwenden des Formular Bereich-Designers](#UsingFormRegionDesigner)

- [Verwenden eines in Outlook entworfenen Formular Bereichs](#UsingFormRegionDesignedOutlook)

- [Hinzufügen von benutzerdefiniertem Code zu einem Formular Bereich](#AddingCustomCode)

- [Erstellen des Projekts](#Building)

- [Debuggen eines Formular Bereichs](#Debugging)

- [Bereitstellen eines Formular Bereichs](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Vorteile der Verwendung von Formular Bereichen
 Formularbereiche bieten zahlreiche Verbesserungen gegenüber der traditionellen Outlook-Formularentwicklung:

- Anpassen der Standardseite beliebiger Standardformulare.

- Hinzufügen von bis zu 12 zusätzlichen Seiten zu einem beliebigen Standardformular.

- Ersetzen Sie oder Optimieren beliebiger Standardformulare.

- Anzeigen einer benutzerdefinierten Benutzeroberfläche im Lesebereich und in den Inspektoren.

  Weitere Informationen finden Sie unter [Anpassen von Formular Seiten und Formular](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions)Bereichen.

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a> Hinzufügen eines Outlook-Formular Bereichs zu Ihrem Projekt
 Sie können den Assistenten **Neuer Outlook-Formular Bereich** verwenden, um einen neuen Formular Bereich zu entwerfen oder einen in Outlook entworfenen Formular Bereich zu importieren. Wenn Sie über einen Formularbereich verfügen, den Sie in einem anderen Outlook VSTO-Add-In-Projekt verwendet haben, können Sie außerdem Ihren vorhandenen Formularbereich wiederverwenden.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Erstellen eines neuen Formular Bereichs mithilfe des Assistenten
 Um einen Formular Bereich zu erstellen, fügen Sie einem Outlook VSTO-Add-in-Projekt ein **Outlook-Formular Bereichs** Element hinzu. Dadurch wird der Assistent **Neuer Outlook-Formular Bereich** gestartet.

 Verwenden Sie den Assistenten, um anzugeben, ob Sie einen neuen Formularbereich entwerfen oder einen in Outlook entworfenen Formularbereich importieren möchten. Weitere Informationen zum Entwerfen eines neuen Formular Bereichs finden Sie unter [Verwenden des Formular Bereich-Designers](#UsingFormRegionDesigner). Weitere Informationen zum Verwenden eines in Outlook entworfenen Formular Bereichs finden Sie unter [Importieren eines in Outlook entworfenen Formular Bereichs](#UsingFormRegionDesignedOutlook).

 Verwenden Sie den Assistenten, um den Typ des zu erstellenden Formularbereichs auszuwählen. In der folgenden Tabelle werden die einzelnen Formularbereichtypen beschrieben.

|Regionstyp|BESCHREIBUNG|
|-----------------|-----------------|
|Getrennt|Fügt den Formularbereich als neue Seite in einem Outlook-Formular hinzu.|
|Benachbart|Fügt den Formularbereich am unteren Rand einer Outlook-Standardseite des Formulars hinzu.|
|Ersetzung|Fügt den Formularbereich als neue Seite hinzu, die die Standardseite eines Outlook-Formulars ersetzt.|
|Alle ersetzen|Ersetzt das gesamte Outlook-Formular durch den Formularbereich.|

 Sie können den Assistenten auch verwenden, um Anzeigebedingungen anzugeben und den Typ des zu erweiternden Formulars auszuwählen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Die Auswahl, die Sie im Assistenten vornehmen, besitzt Auswirkungen auf die auf den anderen Seiten des Assistenten verfügbaren Optionen. Wenn Sie z. b. auf der Seite **neuen Outlook-Formular Bereich erstellen** die Option **angrenzend** oder **getrennt** auswählen, sind die Felder **Titel** und **Beschreibung** auf der Seite **beschreibenden Text angeben und Ihre Anzeigeeinstellungen auswählen** nicht verfügbar. Der Grund besteht darin, dass Outlook diese Felder beim Anzeigen eines benachbarten oder getrennten Formularbereichs nicht verwendet.

#### <a name="form-region-files"></a>Formular Regions Dateien
 Wenn Sie den Assistenten für **neue Outlook-Formular** Bereiche Fertigstellen, fügt Visual Studio dem Projekt automatisch die folgenden Dateien hinzu:

- Eine Formularbereich-Codedatei. Diese Datei enthält den Namen, den Sie für das **Outlook-Formular Bereich** -Element im Dialogfeld **Neues Element hinzufügen** angeben. Fügen Sie dieser Datei Code zum Behandeln von Formularbereichereignissen hinzu.

- Eine Codedatei des Formularbereich-Designers. Diese Datei beinhaltet vom Formularbereich-Designer generierten Code und sollte nicht direkt bearbeitet werden.

- Eine *OFS*-Datei (Outlook Form Storage).

    > [!NOTE]
    > Diese Datei wird dem Projekt nur hinzugefügt, wenn Sie einen Formularbereich importieren, der in Outlook entworfenen wurde.

#### <a name="form-region-factory-class"></a>Formularbereichsfactory-Klasse
 Die Formularbereich-Codedatei enthält eine partielle Klasse, die die <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>-Schnittstelle implementiert. Dies ist die Formularbereichsfactory-Klasse. Die Formularbereichsfactory-Klasse ist für das Erstellen neuer Instanzen des Formularbereichs verantwortlich.

 Sie können diese Klasse suchen, indem Sie den Bereich der **Formular Bereich-Factory** erweitern.

 Der Assistent **Neuer Outlook-Formular Bereich** fügt dieser Klasse Attribute hinzu, die den internen Namen des Formular Bereichs und die Nachrichten Klassen angeben, die den Formular Bereich anzeigen. Sie können diese Attribute manuell ändern, nachdem die Datei dem Projekt hinzugefügt wurde.

 Ein Großteil der Formularbereichsfactory-Klasse wird in der Codedatei des Formularbereich-Designers implementiert. Allerdings wird der `FormRegionInitializing`-Ereignishandler in der Formularbereich-Codedatei bereitgestellt. Sie können diesen Ereignishandler zum Angeben verwenden, ob Outlook den Formularbereich anzeigen soll. Weitere Informationen finden Sie unter [Behandeln von Formular Bereichs Ereignissen](#HandlingFormRegionEvents).

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Fügen Sie dem Projekt einen vorhandenen Formular Bereich hinzu.
 Wenn Sie über einen Outlook-Formularbereich verfügen, den Sie in einem anderen Outlook-Projekt verwendet haben, können Sie diesen in Ihrem aktuellen Outlook VSTO-Add-In-Projekt wiederverwenden, indem Sie mit das Dialogfeld **Vorhandenes Element hinzufügen** verwenden.

 Der vorhandene Formular Bereich muss eine Codedatei (*. vb* oder *. cs*) enthalten. mit dem Dialogfeld **Vorhandenes Element hinzufügen** können Sie keine *OFS*-Dateien (Outlook Form Storage) hinzufügen. Allerdings können Sie einen neuen Formularbereich durch Importieren einer OSF-Datei (Outlook Form Storage) erstellen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Verwenden des Formular Bereich-Designers
 Der Formularbereich-Designer unterstützt Sie beim Entwerfen des Layouts und des Erscheinungsbilds eines Formularbereichs. Sie können verwaltete Steuerelemente auf die Oberfläche des Designers ziehen, auf Steuerelemente doppelklicken, um Ereignishandler zu öffnen, und Eigenschaften im **Eigenschaften** Fenster festlegen.

> [!NOTE]
> Sie können nach Eigenschaften suchen, die sich auf die Darstellung des Formular Bereichs in Outlook unterhalb des Knotens " **Manifest** " im **Eigenschaften** Fenster auswirken.

 Der Formular Bereich-Designer ist nur verfügbar, wenn **Sie auf der** Seite Wählen Sie aus **, wie der Formular Bereich erstellt werden soll** der Formular Bereich auswählen des Assistenten für **neue Outlook-Formular** Bereiche ausgewählt ist

 Zum Öffnen des Formularbereich-Designers stehen drei Möglichkeiten zur Verfügung:

- Doppelklicken Sie in **Projektmappen-Explorer** auf die Formular Bereich-Codedatei.

- Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Formular Bereich-Codedatei, und klicken Sie dann auf **Designer anzeigen**.

- Wählen Sie in **Projektmappen-Explorer** die Formular Bereich-Codedatei aus, und klicken Sie dann im Menü **Ansicht** auf **Designer**.

  Der Formularbereich-Designer unterstützt nur verwaltete Steuerelemente. Sie können keine systemeigenen Outlook-Steuerelemente hinzufügen.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a> Importieren eines in Outlook entworfenen Formular Bereichs
 Wenn Sie in Outlook entwerfen, können Sie dem Formularbereich systemeigene Outlook-Steuerelemente hinzufügen. Systemeigene Outlook-Steuerelemente ermöglichen es Ihnen, Outlook-Daten zur Entwurfszeit zu binden. Allerdings können Sie den Formularbereich-Designer nicht zum Hinzufügen verwalteter Steuerelemente oder zum Ändern des Entwurfs des Formularbereichs verwenden.

 Sie können Formular Bereiche mithilfe des Assistenten **Neuer Outlook-Formular Bereich** in ein Outlook VSTO-Add-in-Projekt importieren. Wählen Sie auf der Seite Wählen Sie aus, **wie der Formular Bereich erstellt** werden soll die **Option eine OFS-Datei (Outlook Form Storage) importieren** aus. Sie können dann zum Speicherort einer Datei im Outlook-Formular Speicherdatei (*. OFS*) navigieren. (Outlook speichert Formular Bereiche als *OFS* -Dateien.)

 Der Assistent für **neue Outlook-Formular** Bereiche kopiert die *. OFS* -Datei in das Projektverzeichnis und fügt der Formular Bereich-Designer-Datei Steuerungs Verweise hinzu. Anschließend können Sie die Steuerelementereignisse in der Formularbereich-Codedatei behandeln.

 Wählen Sie ein Ereignis aus der Methodennamenliste oben im Code-Editor aus, um Ereignisse in einem Visual Basic-Projekt zu behandeln.

 Um Ereignisse in einem C#-Projekt zu behandeln, abonnieren Sie Steuerelementereignisse in der Methode <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Weitere Informationen finden Sie unter Gewusst [wie: Abonnieren von Ereignissen und kündigen von Ereignis &#40;C&#35; Programmier Handbuch&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).

 Sie können die Eigenschaften von Formularbereichen in der Methode `InitializeManifest` der Formularbereichsfactory-Klasse ändern.

> [!NOTE]
> Um einen Formularbereich zu importieren, müssen Sie in einem Projekt arbeiten, das als Ziel dieselbe Version von Outlook verwendet, die Sie auf dem Entwicklungscomputer installiert haben. Wenn Sie z. b. Outlook 2010 installiert haben, funktioniert das Importieren eines Formular Bereichs nur in einem Projekt, das mithilfe der **Outlook 2010-Add-in** -Projektvorlage erstellt wurde.

### <a name="update-an-imported-form-regions-design"></a>Aktualisieren des Entwurfs eines importierten Formular Bereichs
 Sie können Steuerelemente für den Formularbereich hinzufügen, entfernen oder ändern. Bevor Sie diese Aufgaben ausführen, erstellen Sie eine Sicherung des Codes, den Sie der Formularbereich-Codedatei hinzugefügt haben. Öffnen Sie dann die *OFS* -Datei in Outlook, ändern Sie den Formular Bereich, und speichern Sie die Änderungen. Verwenden Sie den Assistenten **Neuer Outlook-Formular Bereich** , um die geänderte *OFS* -Datei zu importieren. Anschließend können Sie Ihren Code in die neue Formularbereich-Codedatei einfügen.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Hinzufügen von benutzerdefiniertem Code zu einem Formular Bereich
 Der Namespace <xref:Microsoft.Office.Tools.Outlook> ermöglicht Ihnen den Zugriff auf Klassen, die den Formularbereich darstellen, das Outlook-Element, das den Formularbereich angezeigt, und andere nützliche Elemente. Das **Outlook-Formular Bereichs** Element fügt dem Projekt automatisch einen Verweis auf diese Assembly hinzu und fügt die entsprechende **using** -oder **Imports** -Anweisung am Anfang der Formular Bereich-Codedatei ein.

 Sie können Klassen, Methoden und Eigenschaften im Namespace `Microsoft.Office.Interop.Outlook` verwenden, um die meisten Outlook-Programmieraufgaben auszuführen. Weitere Informationen zum Outlook-Objektmodell finden Sie unter Übersicht über das Outlook- [Objektmodell](../vsto/outlook-object-model-overview.md). Beispiele für typische Aufgaben, die das Outlook-Objektmodell verwenden, finden Sie unter [Outlook-Lösungen](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Behandeln von Formular Bereichs Ereignissen
 Das **Outlook-Formular Bereichs** Element fügt automatisch die folgenden drei Ereignishandler zur Formular Bereich-Codedatei hinzu.

|event|BESCHREIBUNG|
|-----------|-----------------|
|FormRegionInitializing|Tritt auf, bevor der Formularbereich initialisiert wird. Sie können die Bedingungen in diesem Ereignishandler überprüfen, um zu ermitteln, ob Outlook den Formularbereich anzeigen soll. Weitere Informationen finden Sie unter Gewusst [wie: verhindern der Anzeige eines Formular Bereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|
|FormRegionShowing|Tritt nach dem Erstellen einer Instanz des Formularbereichs, jedoch vor dem Anzeigen des Formularbereichs auf.|
|FormRegionClosed|Tritt auf, bevor der Formularbereich geschlossen wird.|

## <a name="build-the-project"></a><a name="Building"></a> Erstellen des Projekts
 Wenn Sie ein Outlook VSTO-Add-In-Projekt erstellen, das einen Formularbereich enthält, fügt Visual Studio der Registrierung die folgenden Informationen hinzu:

- Einen Schlüssel für jede Nachrichtenklasse, die mindestens einem Formularbereich zugeordnet ist.

- Einen Eintrag für jeden Formularbereich und einen zugeordneten Wert, der den Namen des Outlook VSTO-Add-Ins darstellt.

  Outlook verwendet diese Informationen zum Laden der Formularbereiche.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Debuggen eines Formular Bereichs
 Sie können ein Outlook VSTO-Add-in, das einen Formularbereich enthält, auf die gleiche Weise wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekte debuggen. Beim Starten des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debuggers startet Visual Studio automatisch Outlook.

 Um den Formularbereich anzuzeigen, müssen Sie das entsprechende Outlook-Element öffnen. Öffnen Sie z. B. ein E-Mail-Element, wenn ein benachbarter Formularbereich am Ende des E-Mail-Elements angefügt wird.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Bereitstellen eines Formular Bereichs
 Formularbereiche werden automatisch mit dem zugehörigen Outlook VSTO-Add-In bereitgestellt. Daher müssen Sie keine besonderen Aufgaben ausführen, um einen Formularbereich bereitzustellen. Weitere Informationen zum Bereitstellen von VSTO-Add-Ins finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Richtlinien zum Erstellen von Outlook-Formular Bereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)|Enthält Informationen, mit denen Sie Formularbereiche optimieren und potenzielle Probleme vermeiden können.|
|[Gewusst wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Veranschaulicht, wie ein Formular Bereich erstellt wird, um ein Standard-oder benutzerdefiniertes Microsoft Office Outlook-Formular mithilfe des Assistenten **Neuer Outlook-Formular Bereich** zu erweitern.|
|[Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Erläutert, wie angegeben wird, welche Elemente von Microsoft Office Outlook einen Formularbereich anzeigen, indem der Formularbereich der Nachrichtenklasse jedes Elements zugeordnet wird.|
|[Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)|Zeigt, wie ein benutzerdefinierter Formularbereich entworfen wird, der als neue Seite im Inspektor-Fenster eines Kontaktelements angezeigt wird.|
|[Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Zeigt, wie ein Formular Bereich in Microsoft Office Outlook entworfen und anschließend der Formular Bereich mithilfe des Assistenten für **neue Outlook-Formular** Bereiche in ein Outlook VSTO-Add-in-Projekt importiert wird.|
|[Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)|Beschreibt, wie Sie Code zum Einblenden, Ausblenden oder Ändern von Steuerelementen in einem Formularbereich schreiben und Benutzern ermöglichen, den Code aus anderen Bereichen im Projekt mithilfe der Klasse `Globals` auszuführen.|
|[Gewusst wie: verhindern der Anzeige eines Formular Bereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Zeigt, wie verhindert wird, dass Microsoft Office Outlook einen Formularbereich für ein bestimmtes Element anzeigt.|
|Zeigt, wie auf das Outlook-Element zugegriffen wird, in dem ein Formularbereich angezeigt wird.|
|[Benutzerdefinierte Aktionen in Outlook-Formular Bereichen](../vsto/custom-actions-in-outlook-form-regions.md)|Beschreibt, wie es Benutzern ermöglicht wird, auf ein Outlook-Element zu reagieren.|
