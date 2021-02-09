---
title: Projekt Modellierung | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Standard Projekt Objekte, die zum Erstellen der Automatisierung für den neuen Projekttyp und den Pfad, dem die Projektautomatisierung folgt, erforderlich sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e167a974dde1b98d43f7515581658f1ea549df9d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896826"
---
# <a name="project-modeling"></a>Projektmodellierung
Der nächste Schritt bei der Bereitstellung der Automatisierung für Ihr Projekt besteht darin, die Standard Projekt Objekte zu implementieren: die-und-Auflistungen <xref:EnvDTE.Projects> `ProjectItems` , das `Project` - <xref:EnvDTE.ProjectItem> Objekt und das-Objekt sowie die übrigen-Objekte, die für Diese Standardobjekte sind in der Datei "Dteinternal. h" definiert. Eine Implementierung der Standardobjekte wird im bscprj-Beispiel bereitgestellt. Diese Klassen können als Modelle verwendet werden, um eigene Standard Projekt Objekte zu erstellen, die gleichzeitig mit Projekt Objekten von anderen Projekttypen nebeneinander stehen.

 Ein Automatisierungs Consumer nimmt an, dass es möglich <xref:EnvDTE.Solution> ist, ("und ()" aufzurufen, `<UniqueProjName>")` wobei "n" <xref:EnvDTE.ProjectItems> `n` eine Indexnummer zum Abrufen eines bestimmten Projekts in der Projekt Mappe ist. Durch die Durchführung dieses Automatisierungs aufrubens <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> wird die Umgebung in der entsprechenden Projekt Hierarchie aufgerufen, VSITEMID_ROOT als Itemid-Parameter übergeben und als vshpropid-Parameter VSHPROPID_ExtObject. `IVsHierarchy::GetProperty` Gibt einen `IDispatch` Zeiger auf das Automatisierungs Objekt zurück, das die von `Project` Ihnen implementierte Kernschnittstelle bereitstellt.

 Im folgenden finden Sie die Syntax von `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projekte ermöglichen das Schachteln und Verwenden von Auflistungen zum Erstellen von Gruppen von Projekt Elementen. Die Hierarchie sieht wie folgt aus.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Schachtelung bedeutet, dass ein- <xref:EnvDTE.ProjectItem> Objekt gleichzeitig eine Auflistung sein kann, da eine Auflistung die geschachtelten- <xref:EnvDTE.ProjectItems> `ProjectItems` Objekte enthalten kann. Das grundlegende Projektbeispiel demonstriert diese Schachtelung nicht. Indem Sie das- `Project` Objekt implementieren, nehmen Sie an der Struktur ähnlichen Struktur Teil, die den Entwurf des gesamten Automatisierungs Modells kennzeichnet.

 Die Projektautomatisierung folgt dem Pfad im folgenden Diagramm.

 ![Visual Studio-Projekt Objekte](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Projektautomatisierung

 Wenn Sie kein-Objekt implementieren `Project` , gibt die Umgebung immer noch ein generisches- `Project` Objekt zurück, das nur den Namen des Projekts enthält.

## <a name="see-also"></a>Weitere Informationen
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
