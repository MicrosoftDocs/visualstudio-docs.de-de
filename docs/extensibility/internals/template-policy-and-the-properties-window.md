---
title: Vorlagen Richtlinie und Eigenschaften Fenster | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Verwendung von Vorlagen Richtlinien zum Festlegen von Standardwerten für Eigenschaften, zum Ausblenden von Eigenschaften und zum Hinzufügen von Eigenschaften im Eigenschaftenfenster.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 105a90699689ff6eab6ea5bdfa3d4037e700ecb5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877714"
---
# <a name="template-policy-and-the-properties-window"></a>Vorlagenrichtlinie und das Eigenschaftenfenster
Wenn ein Projekt in einem Enterprise-Vorlagen Projekt enthalten ist, kann dieses Enterprise-Vorlagen Projekt Richtlinien erzwingen. Die Vorlagen Richtlinie wird zu einem Einschränkungs System, das zum Festlegen von Standardwerten für Eigenschaften, zum Ausblenden von Eigenschaften, zum Hinzufügen von Eigenschaften usw. verwendet werden kann.

 Die Verwendung der Vorlagen Richtlinie zum Steuern der Anzeige von Informationen im **Eigenschaften** Fenster unterscheidet sich von der Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> behandelt Objekteigenschaften auf Komponentenebene, während Vorlagen Richtlinien verwendet werden können, um Objekteigenschaften auf Projektmappen-oder Projektebene einzuschränken. Mit anderen Worten,

- Implementieren Sie die Methoden auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> , um zu bestimmen, was im **Eigenschaften** Fenster für bestimmte Objekte angezeigt wird.

- Verwenden Sie die Vorlagen Richtlinie auf Projektmappen-und Projektebene, um zu bestimmen, was im **Eigenschaften** Fenster für zuvor angegebene Objekte angezeigt wird.

  Die Verwendung der Vorlagen Richtlinie, um bestimmte Eigenschaften im **Eigenschaften** Fenster selektiv einzuschränken, wenn ein Projekt Element eines bestimmten Typs in **Projektmappen-Explorer** ausgewählt ist, kann für alle Mitglieder des Entwicklungsteams, die an einem Projekt arbeiten, von Vorteil sein. Beispielsweise können Sie mithilfe der Vorlagen Richtlinie alle Verbindungs Zeichenfolgen-Informationen in einer Datenbank für Ihre Entwickler einrichten und die Verbindungs Zeichenfolge als schreibgeschützt festlegen. Auf diese Weise können Sie eine einfache Möglichkeit bereitstellen, um sicherzustellen, dass jeder Entwickler den richtigen Pfad für den Datenzugriff verwendet.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
