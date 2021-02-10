---
title: Erstellen von SharePoint-Features | Microsoft-Dokumentation
description: Erstellen Sie eine SharePoint-Funktion zum Gruppieren verwandter SharePoint-Projekt Elemente, um die Bereitstellung zu vereinfachen. Fügen Sie der SharePoint-Lösung Features hinzu. Verwenden Sie den Funktions-Designer.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc572f6fc5c0444fda619af5af49c6c2e52ac5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949115"
---
# <a name="create-sharepoint-features"></a>SharePoint-Features erstellen
  Sie können eine SharePoint-Funktion verwenden, um verwandte SharePoint-Projekt Elemente zur einfacheren Bereitstellung zu gruppieren. Mithilfe des SharePoint-Funktions-Designers können Sie Features erstellen, Bereiche festlegen und andere Features als Abhängigkeiten markieren. Der Designer generiert auch ein Manifest, das eine XML-Datei ist, in der die einzelnen Features beschrieben werden.

## <a name="add-features-to-the-sharepoint-solution"></a>Hinzufügen von Features zur SharePoint-Lösung
 Sie können der SharePoint-Lösung mithilfe Projektmappen-Explorer oder des Paket-Explorers eine Funktion hinzufügen. Sie können eine der folgenden Methoden verwenden, um eine Funktion hinzuzufügen.

- Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für **Features**, und wählen Sie dann **Feature hinzufügen** aus.

- Öffnen Sie im Paket- **Explorer** das Kontextmenü für das Paket, und wählen Sie dann **Funktion hinzufügen** aus.

## <a name="using-the-feature-designer"></a>Verwenden des Funktions-Designers
 Eine SharePoint-Lösung kann eine oder mehrere SharePoint-Features enthalten, die unter dem Funktions Knoten in Projektmappen-Explorer gruppiert sind. Jede Funktion verfügt über einen eigenen **Funktions-Designer** , den Sie zum Anpassen der Funktionseigenschaften verwenden können. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md). Um die Features voneinander zu unterscheiden, können Sie die Funktionseigenschaften wie Titel, Beschreibung, Version und Bereich konfigurieren.

### <a name="feature-designer-options"></a>Funktionen-Designer-Optionen
 Nachdem Sie ein Feature erstellt haben, können Sie es mithilfe des Funktions-Designers anpassen.

 In der folgenden Tabelle werden die Funktionseigenschaften beschrieben, die im Funktions-Designer angezeigt werden.

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|Titel|Dies ist optional. Der Standard Titel der Funktion ist auf *SolutionName* *FeatureName* festgelegt.|
|BESCHREIBUNG|Dies ist optional. Die Beschreibung des SharePoint-Features.|
|Bereich|Erforderlich. Wenn eine Funktion mithilfe von **Projektmappen-Explorer** erstellt wird, wird der Gültigkeitsbereich standardmäßig auf Web festgelegt.<br /><br /> -Farm: aktiviert eine Funktion für eine gesamte Server Farm.<br /><br /> -Site: aktiviert eine Funktion für alle Websites in einer Website Sammlung.<br /><br /> -Web: aktiviert eine Funktion für eine bestimmte Website.<br /><br /> -WebApplication: aktiviert eine Funktion für alle Websites in einer Webanwendung.|
|Elemente in der Lösung|Alle SharePoint-Elemente, die der Funktion hinzugefügt werden können.|
|Elemente in der Funktion|Die SharePoint-Projekt Elemente, die der Funktion hinzugefügt wurden.|

## <a name="add-and-remove-sharepoint-project-items"></a>Hinzufügen und Entfernen von SharePoint-Projekt Elementen
 Sie können auswählen, welcher SharePoint-Projekt Elemente Sie eine SharePoint-Funktion für die Bereitstellung hinzufügen möchten. Verwenden Sie den **Funktions-Designer** zum Hinzufügen und Entfernen von Elementen zu Features und zum Anzeigen des Funktions Manifests. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen von Elementen zu SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Funktions Abhängigkeiten hinzufügen
 Sie können das Featuremanifest so konfigurieren, dass bestimmte Features vom SharePoint-Server aktiviert werden, bevor das Feature aktiviert wird. Wenn die SharePoint-Funktion z. b. von anderen Features für Funktionen oder Daten abhängt, kann der SharePoint-Server zunächst versuchen, eine der Features zu aktivieren, von denen ihre Funktion abhängt. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen von Featureabhängigkeiten](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Gewusst wie: Hinzufügen und Entfernen von Elementen zu SharePoint-Features](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Featureabhängigkeiten](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
