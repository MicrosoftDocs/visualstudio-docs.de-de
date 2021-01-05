---
title: Vstextview-Objekt | Microsoft-Dokumentation
description: Das vstextview-Objekt ist ein Fenster, mit dem Benutzer den Unicode-Text des Text Puffers anzeigen und bearbeiten können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d7309e05c3763794deb344a978dd188dbfddd79
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863816"
---
# <a name="vstextview-object"></a>Vstextview-Objekt

Die Textansicht ist ein Fenster, in dem Benutzer den Unicode-Text des Text Puffers anzeigen und bearbeiten können. Im Wesentlichen ist die Sicht, auf die die meisten Benutzer als Editor verweisen. Da die Ansicht durch verschiedene Textebenen (Zeilenumbruch, Gliederung von Text usw.) vom Puffer getrennt ist, ist die Sicht nicht garantiert eine exakte Darstellung des Texts im Puffer. Weitere Informationen zur Textansicht finden Sie unter Zugreifen auf die [Textansicht mithilfe der Legacy-API](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

In der folgenden Tabelle werden die Schnittstellen im- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt angezeigt.

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von Verbund Aktionen (d. h. Aktionen, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert sind).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegenden Methoden zum Verwalten von und Zugreifen auf die Ansicht bereit. `IVsTextView` ist nicht Thread sicher.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagiert mit Textebenen.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Ansicht aus einem anderen Thread aus.|

## <a name="see-also"></a>Weitere Informationen

- [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)
- [Vstextbuffer-Objekt](../extensibility/vstextbuffer-object.md)