---
title: Vscodewindow-Objekt | Microsoft-Dokumentation
description: Erfahren Sie mehr über Code Fenster, bei denen es sich um spezialisierte Dokument Fenster handelt, die eine oder mehrere Text Ansichten enthalten können, in der Regel das vstextview-Objekt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a778cde66bc85a6f3cd8a13b5f2bb6fdb41844de
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864002"
---
# <a name="vscodewindow-object"></a>Vscodewindow-Objekt
Ein Code Fenster ist ein spezielles Dokument Fenster, das mindestens eine Textansicht enthalten kann, in der Regel das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.

 In der Architektur ist das Code Fenster ein Dokument Fenster, das sich innerhalb eines Fensterrahmens befindet. Funktionell ist das Code Fenster einfach ein Dokument Fenster mit zusätzlichen Features. Im MDI-Modus (Multiple Document Interface) ist das Code Fenster der untergeordnete MDI-Frame. Weitere Informationen finden Sie unter [Anpassen von Code Fenstern mit der Legacy-API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

 In der folgenden Tabelle sind die Schnittstellen des- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekts enthalten.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Zugriffs Mechanismus bereit, um einen Dienst zu suchen, den eine Globally Unique Identifier (GUID) identifiziert.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt ein untergeordnetes Multiple Document Interface (MDI)-Element dar, das mindestens eine Code Ansicht enthält.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen.|

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)