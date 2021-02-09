---
title: 'Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys | Microsoft-Dokumentation'
description: Weitere Informationen zum Hinzufügen und Entfernen zusätzlicher Assemblys in SharePoint-Lösungs Paketen. Fügen Sie außerdem sichere Steuerelemente und Klassen Ressourcen hinzu oder löschen Sie Sie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc672a8a0ff7edd66504b5ecbf48e622fad085ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923618"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys
  Wenn ein SharePoint-Paket im Hinblick auf Funktionen oder Daten von anderen Assemblys abhängig ist, können Sie die Assemblys dem Lösungspaket (.wsp) hinzufügen. Auf diese Weise stellt der SharePoint-Server sicher, dass benutzerdefinierte Assemblys mit einem Paket installiert werden.

 Sie können auch die zugeordneten sicheren Steuerelemente und Klassenressourcendateien der Assemblys hinzufügen und ändern.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Zusätzliche Assemblys, sichere Steuerelemente und Klassen Ressourcen hinzufügen
 Sie können im SharePoint-Lösungspaket zusätzliche Assemblys hinzufügen. Zusätzliche Assemblys in einer Sandkastenlösung werden im globalen Assemblycache bereitgestellt, die SharePoint-Projektelemente in einer Sandkastenlösung werden jedoch der Inhaltsdatenbank hinzugefügt. Darüber hinaus können Sie diesen zusätzlichen Assemblys sichere Steuerelemente und Klassenressourcen hinzufügen. Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) oder "Erstellen eines SafeControl-Eintrags" in Bereitstellen von [Webparts in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

#### <a name="to-add-an-existing-assembly"></a>So fügen Sie eine vorhandene Assembly hinzu

1. Öffnen Sie den **Paket-Designer**. Weitere Informationen finden Sie unter Gewusst [wie: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wählen Sie die Registerkarte **Erweitert** aus.

3. Wählen Sie die Schaltfläche **Hinzufügen** aus, und wählen Sie dann in der Liste **vorhandene Assembly hinzufügen** aus.

     Das Dialogfeld **vorhandene Assembly hinzufügen** wird angezeigt.

4. Wählen Sie die Auslassungs Punkte (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) aus, und wählen Sie dann die Assembly aus, die Sie hinzufügen möchten. Aus Gründen der Portabilität wird empfohlen, einen relativen Pfad zur ausgewählten Assembly zu verwenden.

5. Wählen Sie für das **Bereitstellungs Ziel** die Options Schaltfläche **GlobalAssemblyCache** aus, um die Assembly im globalen Assemblycache bereitzustellen, oder wählen Sie das Optionsfeld **WebApplication** aus, um die Assembly im WebApplication-Ordner auf dem Server bereitzustellen, auf dem SharePoint ausgeführt wird.

#### <a name="to-add-an-assembly-from-project-output"></a>So fügen Sie eine Assembly aus der Projektausgabe hinzu

1. Öffnen Sie den **Paket-Designer**.

     Weitere Informationen finden Sie unter Gewusst [wie: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wählen Sie die Registerkarte **Erweitert** aus.

3. Wählen Sie die Schaltfläche **Hinzufügen** aus, und wählen Sie dann in der Liste **Assembly aus Projekt Ausgabe hinzufügen** aus.

     Das Dialogfeld **Assembly aus Projekt Ausgabe hinzufügen** wird angezeigt.

4. Wählen Sie in der Liste **Quell Projekt** das Quell Projekt aus, das Sie hinzufügen möchten.

5. Wählen Sie für das **Bereitstellungs Ziel** die Options Schaltfläche **GlobalAssemblyCache** aus, um die Assembly im globalen Assemblycache bereitzustellen, oder wählen Sie das Optionsfeld **WebApplication** aus, um die Assembly im WebApplication-Ordner auf dem Server bereitzustellen, auf dem SharePoint ausgeführt wird.

#### <a name="to-add-a-safe-control"></a>So fügen Sie ein sicheres Steuerelement hinzu

1. Öffnen Sie das Dialogfeld **vorhandene Assembly bearbeiten** . Öffnen Sie hierzu den Paket-Designer, wählen Sie die Registerkarte **erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten** .

2. Wählen Sie im Bereich **sichere Steuerelemente** die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** aus.

3. Geben Sie  in der Spalte Assemblyname den Namen der Assembly ein.

4. Geben Sie in der Spalte **Namespace** den Namen des Namespace für das sichere Steuerelement ein.

5. Geben Sie in der Spalte **Typname** den Namen des Typs ein.

#### <a name="to-add-a-class-resource"></a>So fügen Sie eine Klassenressource hinzu

1. Öffnen Sie das Dialogfeld **vorhandene Assembly bearbeiten** . Öffnen Sie hierzu den Paket-Designer, wählen Sie die Registerkarte **erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten** .

2. Wählen Sie im Bereich **Klassen Ressourcen** die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** aus.

3. Wählen Sie in der Spalte **Dateiname** die Auslassungs Punkte (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) aus, und wählen Sie die Klassen Ressource aus, die Sie hinzufügen möchten.

## <a name="delete-custom-assemblies"></a>Benutzerdefinierte Assemblys
 Sie können Assemblys aus einem SharePoint-Paket oder sichere Steuerelemente und Klassenressourcen aus vorhandenen Assemblys löschen.

#### <a name="to-delete-an-existing-assembly"></a>So löschen Sie eine vorhandene Assembly

1. Öffnen Sie den **Paket-Designer**. Weitere Informationen finden Sie unter Gewusst [wie: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wählen Sie die Registerkarte **Erweitert** aus.

3. Wählen Sie im Bereich **Weitere** Assemblys die benutzerdefinierte Assembly aus, die Sie löschen möchten.

4. Klicken Sie auf die Schaltfläche **Löschen**.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>So löschen Sie ein sicheres Steuerelement für eine Assembly

1. Öffnen Sie das Dialogfeld **vorhandene Assembly bearbeiten** . Öffnen Sie hierzu den Paket-Designer, wählen Sie die Registerkarte **erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten** .

2. Wählen Sie das zu löschende sichere Steuerelement aus.

3. Wählen Sie die ENTF-TASTE aus.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>So löschen Sie eine Klassenressource für eine Assembly

1. Öffnen Sie das Dialogfeld **vorhandene Assembly bearbeiten** . Öffnen Sie hierzu den Paket-Designer, wählen Sie die Registerkarte **erweitert** aus, wählen Sie eine Assembly aus, und klicken Sie dann auf die Schaltfläche **Bearbeiten** .

2. Wählen Sie die zu löschende Klassenressource aus.

3. Wählen Sie die ENTF-TASTE aus.

## <a name="see-also"></a>Weitere Informationen
- [SharePoint-Features erstellen](../sharepoint/creating-sharepoint-features.md)
- [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Gewusst wie: Hinzufügen und Entfernen von Elementen zu SharePoint-Features](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
