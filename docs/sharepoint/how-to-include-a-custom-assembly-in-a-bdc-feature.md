---
title: 'Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion | Microsoft-Dokumentation'
description: Fügen Sie benutzerdefinierte Assemblys in eine Business Data Connectivity (BDC)-Funktion ein, damit Ihr Projekt auf Assemblys aus anderen Projekten in derselben Projekt Mappe verweisen kann.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a5bce649a0bd9411c064c463defa0946b47e81f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913614"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion
  Das Projekt kann auf Assemblys aus anderen Projekten in derselben Projekt Mappe verweisen. Allerdings müssen Sie diese Assemblys mithilfe des Dialog Felds referenzierte Assemblys **auf lobsystems zuweisen** der Featuredatei des Projekts hinzufügen.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>So fügen Sie eine benutzerdefinierte Assembly in ein Business Data Connectivity (BDC)-Feature ein

1. Wählen Sie in **Projektmappen-Explorer** den Ordner aus, der das BDC-Modell enthält.

2. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

3. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft Assemblys und **dann die Schalt** Fläche mit den Auslassungs Punkten aus (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")).

     Das Dialogfeld referenzierte Assemblys **zu lobsystems zuweisen** wird angezeigt.

4. Wählen Sie in der Liste **Wählen Sie eine Assembly** aus die benutzerdefinierte Assembly aus.

    > [!NOTE]
    > Assemblys werden nur im Dialogfeld **Zuweisen von referenzierten Assemblys zu lobsystems** angezeigt, wenn Sie einen Verweis auf das Projekt hinzugefügt haben, das die Assembly enthält. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen oder Entfernen von verweisen mithilfe des Dialog Felds "Verweis hinzufügen](/previous-versions/wkze6zky(v=vs.140))".

5. Öffnen Sie in der Gruppe **Verweis Eigenschaften** die Liste, die für die Eigenschaft **LobSystem Scope** angezeigt wird, wählen Sie das Branchen System der Methoden aus, die die benutzerdefinierte Assembly verwenden, und klicken Sie dann auf die Schaltfläche **OK** .

    > [!NOTE]
    > Zum Debuggen von Code in der benutzerdefinierten Assembly müssen Sie die Assembly dem Projektmappenpaket hinzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen zusätzlicher](../sharepoint/how-to-add-and-remove-additional-assemblies.md)Assemblys.

## <a name="see-also"></a>Weitere Informationen
- [How to: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [How to: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)