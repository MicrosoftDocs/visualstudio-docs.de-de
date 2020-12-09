---
title: 'Paket-Explorer: Hinzufügen & Features & Elementen zum Paket entfernen'
titleSuffix: ''
description: Hinzufügen und Entfernen von Features und Elementen zu einem SharePoint-Paket mithilfe des Paket-Explorers in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee9b2a12c9eaa168f0223dff29a3379a12b3d691
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915348"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Vorgehensweise: Hinzufügen und Entfernen von Features und Elementen zu einem Paket mit dem Paket-Explorer
  Zum Konfigurieren eines Pakets für die Bereitstellung von SharePoint-Elementen und-Features können Sie den Paket-Explorer verwenden. Sie können die SharePoint-Projekt Elemente und-Funktionen in der wsp-Datei anpassen.

 Alternativ können Sie den Paket-Designer verwenden, um die Features anzuzeigen und neu zu ordnen, um die Aktivierungs Reihenfolge zu ändern. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen von Features und Elementen in einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Öffnen Sie den Paket-Explorer.
 Sie können das folgende Verfahren verwenden, um den Paket-Explorer zu öffnen, wenn die Visual Studio-Projekt Mappe mindestens ein SharePoint-Projekt enthält. Alternativ wird der Paket-Explorer automatisch geöffnet, wenn Sie eine Funktion oder einen Paket-Designer anzeigen. Nachdem Sie alle Funktions-und Paket-Designer geschlossen haben, wird der paketexplorer ebenfalls geschlossen.

#### <a name="to-open-the-packaging-explorer"></a>So öffnen Sie den Paket-Explorer

1. Wählen Sie in der Menüleiste **View** die Option  >  **anderen Windows**-  >  **Paket-Explorer** anzeigen aus.

     Der **Paket-Explorer** wird in der **Toolbox** angezeigt.

## <a name="adding-a-feature-to-a-package"></a>Hinzufügen einer Funktion zu einem Paket
 Sie können einem Paket mithilfe des Paket-Explorers neue und vorhandene Funktionen hinzufügen.

#### <a name="to-add-a-sharepoint-feature"></a>So fügen Sie ein SharePoint-Feature hinzu

1. Öffnen Sie den **Paket-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Funktion hinzufügen** aus.

#### <a name="to-move-an-existing-sharepoint-feature"></a>So verschieben Sie eine vorhandene SharePoint-Funktion

1. Öffnen Sie den **Paket-Explorer**, und führen Sie dann einen der folgenden Schritte aus:

    - Ziehen Sie eine **Funktion** von einem Projekt in ein anderes Projekt.

    - Öffnen Sie das Kontextmenü für eine Funktion, wählen Sie **Ausschneiden** aus, öffnen Sie das Kontextmenü für das Projekt, in das Sie die Funktion verschieben möchten, und wählen Sie dann **Einfügen** aus.

    > [!NOTE]
    > Verwenden Sie dieses Verfahren, wenn Sie über mehr als ein SharePoint-Projekt in der Projekt Mappe verfügen.

## <a name="validate-a-feature-or-package"></a>Überprüfen eines Features oder Pakets
 Sie können potenzielle Probleme in den SharePoint-Funktionen und-Paketen erkennen, indem Sie die Dateien validieren. Warnungen und Fehler werden im Fenster Ausgabe und Fehlerliste angezeigt.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>So überprüfen Sie ein SharePoint-Feature oder-Paket

1. Öffnen Sie den **Paket-Explorer**.

2. Öffnen **Sie ein** Kontextmenü für ein Feature oder Paket, und wählen Sie dann überprüfen aus.

## <a name="see-also"></a>Weitere Informationen
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
