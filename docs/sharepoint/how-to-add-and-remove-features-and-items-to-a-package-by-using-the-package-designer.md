---
title: 'Paket-Designer: Hinzufügen & Features und Elemente zum Paket entfernen'
titleSuffix: ''
description: Informieren Sie sich über das Hinzufügen und Entfernen von Features und Elementen zu einem SharePoint-Paket, indem Sie den Paket-Designer in Visual Studio verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
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
ms.openlocfilehash: 92503d8e29bac4f44df5376f3cecb24247b585d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923596"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Vorgehensweise: Hinzufügen und Entfernen von Features und Elementen zu einem Paket mit dem Paket-Designer
  Wenn Sie eine SharePoint-Lösung erstellen, fügt Visual Studio dem Paket in der Projekt Mappe die SharePoint-Standard Features hinzu. Vor der endgültigen Bereitstellung können Sie SharePoint-Projekt Elemente und-Funktionen hinzufügen und entfernen, um das SharePoint-Paket zu ändern.

 Alternativ können Sie den Paket-Explorer verwenden, um SharePoint-Projekt Elemente hinzuzufügen und zu entfernen. Sie können auch die Hierarchie der SharePoint-Projekt Elemente und-Funktionen anzeigen und ändern, die in das Paket (. wsp) eingefügt werden. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen von Features und Elementen in einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Hinzufügen von Funktionen zu einem SharePoint-Paket
 Sie können den Paket-Designer verwenden, um Funktionen zu einem SharePoint-Paket hinzuzufügen.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>So fügen Sie SharePoint-Features mit dem Paket-Designer hinzu

1. Öffnen Sie den **Paket-Designer**.

    Weitere Informationen finden Sie unter Gewusst [wie: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Fügen Sie eine oder mehrere SharePoint-Funktionen hinzu, indem Sie einen oder mehrere der folgenden Schritte ausführen:

   1. Doppelklicken Sie auf jedes Element in den **Elementen in der** projektmappenliste, das Sie hinzufügen möchten.

   2. Wählen Sie ein Element aus, das Sie hinzufügen möchten, und wählen Sie dann die Schaltfläche **Hinzufügen** (>) aus.

   3. Wählen Sie die Schaltfläche **Alle hinzufügen** (>>) aus, um alle Elemente gleichzeitig hinzuzufügen.

      Beispielsweise können Sie auf ein Element in den **Elementen in der** projektmappenliste doppelklicken, um es den **Elementen in der Paket** Liste hinzuzufügen.

      Die SharePoint-Projekt Elemente und-Funktionen werden in den **Elementen in der Paket** Liste angezeigt.

## <a name="remove-features-from-a-sharepoint-package"></a>Entfernen von Funktionen aus einem SharePoint-Paket
 Sie können den Paket-Designer verwenden, um Funktionen zu einem SharePoint-Paket zu entfernen.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>So entfernen Sie SharePoint-Funktionen mit dem Paket-Designer

1. Wählen Sie in der Liste **Elemente in der** Liste ein Element aus, das Sie entfernen möchten, und wählen Sie dann die Schaltfläche **Entfernen** (<) aus, oder klicken Sie auf die Schaltfläche **Alle entfernen** (<<), um alle Elemente zu entfernen.

     Die SharePoint-Elemente werden in den **Elementen in der** projektmappenliste angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von SharePoint-Lösungs Paketen](../sharepoint/creating-sharepoint-solution-packages.md)
- [Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Vorgehensweise: Erstellen eines Pakets](/previous-versions/ee231585(v=vs.110))