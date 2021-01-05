---
title: Syntax Farbgebung in benutzerdefinierten Editoren | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Syntax Farbgebung in benutzerdefinierten Editoren von Visual Studio Environment SDK, die die angegebenen Farben für eine bestimmte Dokument Ansicht anzeigt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aac72cbc26ff5e6abf96259fd161cba63b3b2af
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716067"
---
# <a name="syntax-coloring-in-custom-editors"></a>Syntaxfarben in benutzerdefinierten Editoren
Visual Studio-Umgebungs-SDK-Editoren, einschließlich des Kern-Editors, verwenden Sprachdienste, um bestimmte syntaktische Elemente zu identifizieren und diese mit den angegebenen Farben für eine bestimmte Dokument Ansicht anzuzeigen.

## <a name="colorization-requirements"></a>Farbige Anforderungen
 Alle Editoren, die die Farbgebung eines sprach Dienstanbieter implementieren, müssen:

1. Verwenden Sie ein Objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> , das implementiert, um den Text für die Farbgebung zu verwalten, und ein Objekt, das implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , um eine Dokument Ansicht des Texts bereitzustellen.

2. Rufen Sie eine Schnittstelle zu einem bestimmten Sprachdienst ab, indem Sie den Dienstanbieter des VSPackages mithilfe der identifizierenden GUID des sprach Dienstanbieters Abfragen.

3. Ruft die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode des-Objekts auf, das implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Diese Methode ordnet den Sprachdienst der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Implementierung zu, die das VSPackage verwendet, um den Text zu verwalten, der farbig markiert werden soll.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Basis-Editor-Verwendung der Farbgebung eines sprach Dienstanbieter
 Wenn ein Sprachdienst mit einer Farbauswahl von einer Instanz des Kern-Editors abgerufen wird, werden die Text-und Renderingvorgänge durch die Farbgebung eines sprach Dienstanbieter automatisch durchgeführt, ohne dass ein weiterer Eingriff erforderlich ist.

 Die IDE ist transparent:

- Ruft die Farbgebung bei Bedarf auf, um Text beim Hinzufügen oder ändern in der Implementierung von zu analysieren und zu analysieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .

- Stellt sicher, dass die von der-Implementierung bereitgestellte Dokument Ansicht <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> mithilfe der von der Farbgebung zurückgegebenen Informationen aktualisiert und neu gezeichnet wird.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nicht-Kern-Editor-Verwendung der Farbgebung eines sprach Dienstanbieter
 Nicht-Kern-Editor-Instanzen können auch den Syntax Farb Erfassungs Dienst eines sprach Dienstanbieter verwenden. Sie müssen jedoch explizit die Farbgebung des dienstanwenders abrufen und anwenden und die Dokument Sichten selbst neu zeichnen.

 Zu diesem Zweck muss ein nicht-Kern-Editor folgende Aktionen ausführen:

1. Abrufen des Farb Erfassers Objekts eines sprach dienstanders (das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> und implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Das VSPackage bewirkt dies durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> -Methode für die-Schnittstelle des sprach Dienstanbieter.

2. Ruft die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode auf, um anzufordern, dass ein bestimmter Textabschnitt farbig markiert werden soll.

     Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode gibt ein Array von-Werten zurück, eines für jeden Buchstaben in der Text Spanne, die farbig markiert wird. Außerdem wird der Textabschnitt als eine bestimmte Art von Kolon-Element, z. b. ein Kommentar, ein Schlüsselwort oder ein Datentyp, identifiziert.

3. Verwenden Sie die von zurückgegebenen farbliche Informationen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> , um den Text neu zu zeichnen und anzuzeigen.

> [!NOTE]
> Zusätzlich zur Verwendung der Farbgebung eines sprach Dienstanbieter kann ein VSPackage auswählen, dass der Text Farb Mechanismus für das allgemeine Visual Studio-Umgebungs-SDK verwendet werden soll. Weitere Informationen zu diesem Mechanismus finden Sie unter [Verwenden von Schriftarten und Farben](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Weitere Informationen

- [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntaxfarben](../extensibility/internals/implementing-syntax-coloring.md)
- [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Benutzerdefinierte einfärbbare Elemente](../extensibility/internals/custom-colorable-items.md)