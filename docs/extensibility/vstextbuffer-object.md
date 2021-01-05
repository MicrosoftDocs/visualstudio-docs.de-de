---
title: Vstextbuffer-Objekt | Microsoft-Dokumentation
description: Das vstextbuffer-Objekt stellt einen Stream von Unicode-Text dar, der in der Regel mit einer Datei verknüpft ist. In diesem Artikel werden die Schnittstellen von vstextbuffer aufgelistet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5c2afa08e9c480342bff95d417dfb9174250b83
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863952"
---
# <a name="vstextbuffer-object"></a>Vstextbuffer-Objekt
Das Text Puffer Objekt stellt einen Stream von Unicode-Text dar, der in der Regel mit einer Datei verknüpft ist. Ein- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt kann außerhalb des Kontexts des Kern Editors verwendet werden, wie in, einem Assistenten.

 In der folgenden Tabelle werden die Schnittstellen von angezeigt `VSTextBuffer` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standard-OLE-Schnittstelle. Wird für die rückgängig-/Wiederholungs-Behandlung im Puffer verwendet.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standard-OLE-Schnittstelle.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von zuordnungsaktionen (d. h. Aktionen, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert sind).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Ermöglicht die Persistenz von Dokument Daten, die vom Text Puffer verwaltet werden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt grundlegende Dienste bereit. wird von vielen Clients verwendet.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Wird zum Durchsuchen eines Puffers verwendet.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese-und Schreibfunktionen mit zweidimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese-und Schreibfunktionen mithilfe eindimensionaler Koordinaten. Erbt von `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Bietet schnellen, streamorientierten, sequenziellen Zugriff auf Text im Puffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Ermöglicht den Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder Moniker des Puffers. Mit dieser Schnittstelle können Sie Ihre eigenen zufälligen Daten im Puffer speichern, indem Sie eine GUID erstellen und Sie als Schlüssel verwenden.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt Verbindungspunkte für Ereignisse.|

## <a name="remarks"></a>Hinweise
 Der `VSTextBuffer` wird normalerweise durch einen- `QueryInterface` Aufrufwert gefunden `IVsTextBuffer` . Weitere Informationen finden Sie unter [Text Puffer](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)