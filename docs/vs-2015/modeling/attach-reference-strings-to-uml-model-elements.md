---
title: Zuordnen von Verweis Zeichenfolgen an UML-Modellelemente | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7726379258ef474b57f1ca4a924413cd93cf80bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672795"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Anfügen von Referenzzeichenfolgen an UML-Modellelemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Code schreiben, um beliebige Zeichenfolgen an Modellelemente anzufügen. Eine Zeichenfolge könnte z. B. ein URI, das zwischengespeicherte Ergebnis einer Berechnung oder ein ModelBus-Verweis auf ein Element in einem anderen Modell sein. Jede Zeichenfolge ist in einem „IReference“-Objekt enthalten. Jedem Modellelement kann eine beliebige Anzahl von „IReference“-Objekten zugeordnet werden.

 Jedes „IReference“-Objekt hat einen Namen. Sie können über diesen Namen angeben, wie der Verweiswert interpretiert werden soll. Beispielsweise könnten Sie für den Namen „URI“ festlegen, um anzugeben, dass der Wert als URI interpretiert werden soll. Es gibt einige vordefinierte Verweisnamenwerte, die von den Modellierungstools verwendet werden.

## <a name="attaching-a-reference-to-an-ielement"></a>Anfügen eines Verweises an ein „IElement“
 Wenn Sie die folgenden Methoden verwenden möchten, müssen Sie einen Verweis auf Folgendes hinzufügen:

 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

 Sie sollten diese Direktive in Ihren Code einfügen:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

|Methodenaufruf|Beschreibung|
|-----------------|-----------------|
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Erstellt ein `IReference` mit den angegebenen Zeichenfolge für Name und Wert und verknüpft diese mit `element`. Gibt `IReference` zurück.<br /><br /> Löst eine Ausnahme aus, wenn `duplicatesAllowed` dem Wert „False“ entspricht und bereits ein `IReference` mit dem gleichen Namen zu `element` zugeordnet ist.|
|`element.GetReferences(name)`|Gibt alle `IReference`-Objekte zurück, die mit `element` verknüpft sind und den angegebenen `name` aufweisen.|
|`element.DeleteAllReferences(name)`|Gibt alle `IReference`-Objekte zurück, die mit dem Element verknüpft sind und den angegebenen Namen aufweisen.|
|`reference.Delete()`|Löscht dieses `IReference`.|
|`ReferenceConstants.WorkItem`|Der zum Benennen von Arbeitselementeverweisen verwendete Wert.|

## <a name="see-also"></a>Weitere Informationen
 [Definieren eines Link Handlers für Arbeitselemente](../modeling/define-a-work-item-link-handler.md) [definieren und Installieren einer Modellierungs Erweiterung](../modeling/define-and-install-a-modeling-extension.md) [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)
