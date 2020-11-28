---
title: 'Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente | Microsoft-Dokumentation'
description: Markieren Sie Steuerelemente als sichere Steuerelemente in der Eigenschaft "Safe Control Entries" eines SharePoint-Projekt Elements oder im Paket-Designer, wenn Sie eine Assembly hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 024cd50fc36b84addca11dc3c0f23cdc64fa507d
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304512"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente
  Aus Sicherheitsgründen unterscheidet SharePoint zwischen websteuer Elementen, die vor Skript Injektion und websteuer Elementen geschützt sind. Auf geschützte Steuerelemente oder *sichere Steuerelemente* kann von nicht vertrauenswürdigen Benutzern zugegriffen werden. Sie können Steuerelemente als sicher in der Eigenschaft Safe Control Entries eines SharePoint-Projekt Elements oder im **Paket-Designer** markieren, wenn Sie dem Paket eine Assembly hinzufügen. Weitere Informationen finden Sie unter

- [web.config Datei Einstellungen ändern](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) und [Registrieren einer Webpartassembly als sicheres Steuer](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))Element.

> [!IMPORTANT]
> Diese Prozeduren dienen der Veranschaulichung. Markieren Sie Steuerelemente nur dann, wenn Sie sicher sind, dass Sie sicher sind.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Markieren von sicheren Steuerelementen in der Eigenschaft "sichere Steuerelement Einträge"

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>So markieren Sie Steuerelemente als sicher oder unsicher in der Eigenschaft "sichere Steuerelement Einträge"

1. Erstellen Sie eine SharePoint-Projekt Mappe mit einem Visual Web Part-Projekt.

2. Fügen Sie zwei-Steuerelemente zum Webpart hinzu: ein Textfeld und eine Schaltfläche. Belassen Sie die Namen der Standardwerte textBox1 bzw. Button1.

3. Fügen Sie der Eigenschaft " **Safe Control Entries** " des Webparts zwei Einträge hinzu. Wählen Sie hierzu die Schaltfläche mit den Auslassungs Zeichen (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) neben der Eigenschaft " **sichere Steuerelement Einträge** " im Fenster " **Eigenschaften** " aus.

     Das Dialogfeld **Einträge für sicheres Steuer** Element wird angezeigt.

4. Wählen Sie im Dialogfeld **Einträge für sicheres Steuer** **Element die Schalt** Fläche **Hinzufügen** zweimal aus, um dem Bereich Elemente zwei Einträge für sicheres Steuerelement hinzuzufügen: eine für die Schaltfläche und eine für das Textfeld.

5. Wählen Sie den ersten Eintrag für den sicheren Eintrag aus, und ändern Sie dann den Wert der **Safe** -Eigenschaft in **false**, seine **Typname** -Eigenschaft in **Button1** und die zugehörige Sicherheit für die **Script** -Eigenschaft in **false**.

     In diesem Schritt wird das Schaltflächen-Steuerelement als unsicherer Steuerelement identifiziert.

6. Wählen Sie den zweiten Eintrag für sicheres Steuerelement in der Liste aus. Belassen Sie den Wert der **sicheren** Eigenschaft auf **true** , und legen Sie die Eigenschaft **Typname** auf **TextBox1** und die Eigenschaft für die Eigenschaft für den **sicheren** Zustand auf **true** fest.

     Das Textfeld-Steuerelement ist nun als Steuerelement gekennzeichnet, das gegen Skript Injektion sicher ist.

7. Wählen Sie die Schaltfläche **OK** aus, um das Dialogfeld zu schließen.

## <a name="marking-safe-controls-in-the-package-designer"></a>Markieren sicherer Steuerelemente im Paket-Designer

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>So markieren Sie Steuerelemente im Paket-Designer als sicher oder unsicher

1. Erstellen Sie eine SharePoint-Projekt Mappe mit einem Visual Web Part-Projekt.

2. Fügen Sie zwei-Steuerelemente zum Webpart hinzu: ein Textfeld und eine Schaltfläche. Belassen Sie die Namen der Standardwerte textBox1 bzw. Button1.

     Notieren Sie sich den Namespace des Steuer Elements, da er später verwendet wird.

3. Wählen Sie in der Menüleiste **Build**-Projekt Mappe erstellen aus,  >  **Build Solution** um das Projekt zu erstellen.

4. Erstellen Sie eine weitere SharePoint-Lösung.

5. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die *Package. Package* -Datei, und wählen Sie dann **Öffnen** aus, um den **Paket-Designer** zu öffnen.

6. Wählen Sie im **Paket-Designer** die Registerkarte **erweitert** aus.

7. Wählen Sie unter **zusätzliche** Assemblys die Schaltfläche **Hinzufügen** aus, und wählen Sie dann vorhandene Assembly aus der Liste **Hinzufügen** aus.

8. Wählen Sie im Dialogfeld **vorhandene Assembly hinzufügen** die Schaltfläche mit den Auslassungs Zeichen (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) neben **Quellpfad** aus.

9. Wählen Sie die Assembly aus der SharePoint-Lösung aus, die Sie in Schritt 1 erstellt haben, und wählen Sie dann die Schaltfläche **Öffnen** aus.

10. Belassen Sie für dieses Beispiel die Option **Bereitstellungs Ziel** als GlobalAssemblyCache.

     Dieser Schritt bewirkt, dass die Assembly im globalen Assemblycache (GAC) des Systems bereitgestellt wird. Wenn Sie möchten, dass die Assembly im Ordner Webanwendung (bin) bereitgestellt wird, wählen Sie stattdessen diese Option aus. Weitere Informationen finden Sie unter Bereitstellen von [Webparts in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. Wählen Sie im Feld **sichere Steuerelemente** die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** aus.

12. Geben Sie die Werte für die Eigenschaften in der folgenden Tabelle ein.

    |Eigenschaftenname|Wert|
    |-------------------|-----------|
    |Namespace|Der voll qualifizierte Namespace für das Steuerelement, z. b **. BdcModelProject1. VisualWebPart1**.|
    |Typname|Schaltfläche1|
    |Assemblyname|Einen starken Assemblynamen, z. b.: Microsoft. Office. SharePoint. clientextensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Safe|Deaktivieren Sie das Kontrollkästchen **sicher** .|
    |Gegen Skript sichern|Deaktivieren Sie das Kontrollkästchen für das **sichere gegen Skript** .|

    > [!NOTE]
    > Der **assemblynamenswert** für Assemblys, die über die Registerkarte **erweitert** des **Paket-Designers** hinzugefügt wurden, kann kein Token sein, sondern muss eine Assembly mit starkem Namen sein. Weitere Informationen finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Wählen Sie die **Tab** -Taste, um einen weiteren sicheren Steuerungs Eintrag zu erstellen.

14. Klicken Sie erneut auf die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** .

15. Geben Sie die Werte für die Eigenschaften in der folgenden Tabelle ein.

    |Eigenschaftenname|Wert|
    |-------------------|-----------|
    |Namespace|Der voll qualifizierte Namespace für das Steuerelement, z. b **. BdcModelProject1. VisualWebPart1**.|
    |Typname|TextBox1|
    |Assemblyname|Einen starken Assemblynamen, z. b.: Microsoft. Office. SharePoint. clientextensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Safe|Aktivieren Sie das Kontrollkästchen **sicher** .|
    |Gegen Skript sichern|Aktivieren Sie das Kontrollkästchen für **Skript sichern** .|

16. Wählen Sie die **Tab** -Taste, und klicken Sie dann auf die Schaltfläche **OK** , um das Dialogfeld zu schließen.

## <a name="see-also"></a>Siehe auch
- [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
