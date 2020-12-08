---
title: 'Gewusst wie: Erstellen von Office-Projekten in Visual Studio'
description: Erfahren Sie, wie Sie Visual Studio zum Erstellen von VSTO-Add-Ins und Anpassungen auf Dokument Ebene für Microsoft Office-Anwendungen verwenden können.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 652b7676ddf5d7e095010e711ab0dabc5b5f2ab7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844373"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Gewusst wie: Erstellen von Office-Projekten in Visual Studio
  Sie können verwenden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , um VSTO-Add-Ins und Anpassungen auf Dokument Ebene für Microsoft Office-Anwendungen zu erstellen. Weitere Informationen zu diesen Projekttypen finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>So erstellen Sie ein VSTO-Add-In-Projekt

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus. Wenn die integrierte Entwicklungsumgebung (IDE) für die Verwendung von [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Entwicklungseinstellungen festgelegt ist, wählen Sie im Menü **Datei** die Option **Neues**  >  **Projekt** aus.

    Das Dialogfeld **Neues Projekt** wird angezeigt.

   > [!NOTE]
   > Standardmäßig wird für Office-Projekte [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] als Ziel festgelegt. Weitere Informationen finden Sie unter [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).

2. Erweitern Sie im Bereich Vorlagen unter dem Knoten für die Sprache, die Sie verwenden möchten, **Office/SharePoint**.

3. Wählen Sie den Knoten **Office-Add-ins** aus.

4. Wählen Sie in der Liste der Projektvorlagen eine VSTO-Add-In-Projektvorlage aus. Eine Liste der verfügbaren VSTO-Add-in-Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Wenn Projektvorlagen beim Auswählen des Knotens **Office-Add-ins** nicht sichtbar sind, stellen Sie sicher, dass **.NET Framework 4** oder höher im Kombinations Feld am oberen Rand des Dialog Felds ausgewählt ist. Office-Projektvorlagen sind für beide .NET Framework-Versionen sichtbar.

5. Geben Sie im Feld **Name** einen Namen für das Projekt ein. Dieser Projektname wird standardmäßig auch für die Projektmappenname verwendet.

6. Geben Sie im Feld **Speicherort** den Pfad ein, in dem Sie das Projekt erstellen möchten. Sie können absolute und UNC-Pfade (Universal Naming Convention) verwenden. Verwenden Sie keinen HTTP-, FTP- oder sonstigen Protokollpfad.

    Die Speicherorte haben die folgende Formate:

   * [*Laufwerk*\]\:

   * \\\\*Server* \\ *Freigabe*

     Verwenden Sie in der Pfadangabe keine der folgenden Zeichen:

   * Sternchen (*)

   * Senkrechter Strich (|)

   * Doppelpunkt (:) (außer nach dem Laufwerkbuchstaben)

   * Anführungszeichen (") (bei Pfaden mit Leerzeichen sind keine Anführungszeichen erforderlich)

   * Kleiner als (\<)

   * Größer als (>)

   * Fragezeichen (?)

   * Prozentzeichen (%)

7. Klicken Sie auf die Schaltfläche **OK** .

   ::: moniker range="vs-2017"

   > [!NOTE]
   > Add-In-Projekte werden immer gespeichert, wenn sie erstellt werden. Sie können nicht als temporäre Projekte erstellt werden. Weitere Informationen zu temporären Projekten finden Sie unter [temporäre Projekte](../ide/creating-solutions-and-projects.md#create-a-temporary-project).

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>So erstellen Sie ein Projekt für Anpassungen auf Dokumentebene

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus. Wenn die IDE für die Verwendung Visual Basic Entwicklungseinstellungen festgelegt ist, wählen Sie im Menü **Datei** die Option **Neues**  >  **Projekt** aus.

    Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Erweitern Sie im Bereich Vorlagen unter dem Knoten für die Sprache, die Sie verwenden möchten, **Office/SharePoint**.

3. Wählen Sie den Knoten **Office-Add-Ins** aus.

4. Wählen Sie in der Liste der Projektvorlagen eine Projektvorlage auf Dokumentebene aus. Eine Liste der verfügbaren Projektvorlagen auf Dokument Ebene finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Wenn Projektvorlagen beim Auswählen des Knotens **Office-Add-ins** nicht sichtbar sind, stellen Sie sicher, dass **.NET Framework 4** oder höher ausgewählt ist.

5. Geben Sie im Feld **Name** einen Namen für das Projekt ein. Dieser Name wird standardmäßig auch für das Dokument verwendet. Falls Sie für die IDE Visual C#-Entwicklungseinstellungen oder Allgemeine Entwicklungseinstellungen festgelegt haben, müssen Sie zusätzlich einen Speicherort und einen Projektmappennamen eingeben.

   > [!NOTE]
   > Der Pfad des Projektspeicherorts oder der Projektname dürfen keine Ersatzzeichen enthalten. Wenn Sie die Projektmappe für die Offlineverwendung bereitstellen möchten, müssen außerdem die Zeichen im Projektnamen den Spezifikationen des HTTP-Protokolls entsprechen.

6. Klicken Sie auf die Schaltfläche **OK** .

    Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.

7. Wählen Sie **Neues Dokument erstellen** aus, wenn Sie ein neues Dokument für die Projekt Mappe erstellen möchten, oder wählen Sie **vorhandenes Dokument kopieren** aus, wenn Sie ein vorhandenes Dokument anpassen möchten.

    Wenn Sie ein neues Dokument erstellen, geben Sie den Namen im Feld **Name** an, und wählen Sie im Feld **Format** das Format des Dokuments aus. Weitere Informationen zu den verfügbaren Formaten finden Sie unter [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md).

    Wenn Sie ein vorhandenes Dokument verwenden, geben Sie den Speicherort des Dokuments im Feld **Vollständiger Pfad zum vorhandenen Dokument** an. Sie können sowohl absolute Pfade als auch UNC-Pfade verwenden. Verwenden Sie keinen HTTP-, FTP- oder sonstigen Protokollpfad für das Dokument.

    Die Speicherorte haben die folgende Formate:

   - [*Laufwerk*\]\:

   - \\\\*Server* \\ *Freigabe*

     Verwenden Sie in der Pfadangabe keine der folgenden Zeichen:

   - Sternchen (*)

   - Senkrechter Strich (|)

   - Doppelpunkt (:) (außer nach dem Laufwerkbuchstaben)

   - Anführungszeichen (") (bei Pfaden mit Leerzeichen sind keine Anführungszeichen erforderlich)

   - Kleiner als (\<)

   - Größer als (>)

   - Fragezeichen (?)

   - Prozentzeichen (%)

   > [!NOTE]
   > Öffnen Sie in einem [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]-Projekt nur in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] erstellte oder in dieses Format konvertierte Dokumente. Öffnen Sie entsprechend in einem Word 2010-Projekt nur in Word 2010 erstellte oder in dieses Format konvertierte Dokumente. Bestimmte Funktionen werden im Dokument deaktiviert, wenn Sie ein Dokument öffnen, das in einer früheren Word-Version erstellt wurde. Wenn Sie Code schreiben, von dem diese Funktionen verwendet werden, können Fehler im Projekt auftreten. Um ein Dokument zu konvertieren, öffnen Sie es in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder Word 2010, und wählen Sie auf der Registerkarte **Datei** auf dem Menüband die Option **Informationen**  >  **konvertieren** aus.

8. Klicken Sie auf **Fertig stellen**.

9. Fügen Sie der Liste von vertrauenswürdigen Speicherorten im Sicherheitscenter in Word in den folgenden Fällen den Projektordner und seine Unterordner hinzu:

   - Sie erstellen ein Word-Dokument, das auf einer *DOCM* -Datei basiert, und das Dokument enthält ein VBA-Projekt oder Hosts Windows Forms-Steuerelementen. Durch Hinzufügen des Projektordners zur Liste der vertrauenswürdigen Speicherorte können Sie sicherstellen, dass das zur Entwurfszeit wie erwartet funktioniert.

   - Sie erstellen ein Word-Vorlagen Projekt, das auf einer *DOTX* -Datei basiert. Sie müssen der Liste der vertrauenswürdigen Speicherorte den Projektordner hinzufügen, damit das Projekt ausgeführt und gedebuggt werden kann.

     Weitere Informationen zum Hinzufügen eines Dokuments zu den vertrauenswürdigen Speicherorten finden Sie auf der Microsoft Office Online Website [erstellen, entfernen oder Ändern eines vertrauenswürdigen Speicher Orts für Ihre Dateien](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="see-also"></a>Siehe auch
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
- [Gemeinsame Entwicklung von Office-Lösungen](../vsto/collaborative-development-of-office-solutions.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
