---
title: Validieren von Breakpoints in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die ValidateBreakpointLocation-Methode in einem Legacy Sprachdienst überschreiben können, um Breakpoints vor dem Starten des Debuggers zu überprüfen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d48db7397e2f9a5921315036bea15551fb7baa9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488023"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Überprüfen von Haltepunkten in einem Legacysprachdienst
Ein Haltepunkt gibt an, dass die Programmausführung an einem bestimmten Punkt angehalten werden soll, während Sie in einem Debugger ausgeführt wird. Ein Benutzer kann einen Haltepunkt in jeder Zeile in der Quelldatei platzieren, da der Editor nicht weiß, was einen gültigen Speicherort für einen Haltepunkt ausmacht. Wenn der Debugger gestartet wird, werden alle markierten Haltepunkte (die als ausstehende Breakpoints bezeichnet werden) an die entsprechende Position im laufenden Programm gebunden. Gleichzeitig werden die Breakpoints überprüft, um sicherzustellen, dass Sie gültige Code Speicherorte markieren. Beispielsweise ist ein Haltepunkt in einem Kommentar ungültig, da an dieser Stelle im Quellcode kein Code vorhanden ist. Der Debugger deaktiviert ungültige Breakpoints.

 Da der Sprachdienst den angezeigten Quellcode kennt, kann er Breakpoints vor dem Start des Debuggers überprüfen. Sie können die- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode überschreiben, um eine Spanne zurückzugeben, die einen gültigen Speicherort für einen Haltepunkt angibt. Die Haltepunkt Position wird immer noch überprüft, wenn der Debugger gestartet wird. der Benutzer wird jedoch über ungültige Breakpoints benachrichtigt, ohne darauf zu warten, dass der Debugger geladen wird.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementieren von Unterstützung für die Überprüfung von Breakpoints

- Die- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode erhält die Position des Breakpoints. Die-Implementierung muss entscheiden, ob der Speicherort gültig ist, und gibt dies an, indem eine Text Spanne zurückgegeben wird, die den Code identifiziert, der der Zeilen Position des Breakpoints zugeordnet ist.

- Gibt zurück <xref:Microsoft.VisualStudio.VSConstants.S_OK> , wenn der Speicherort gültig ist, oder, <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> Wenn er ungültig ist.

- Wenn der Breakpoint gültig ist, wird der Textbereich zusammen mit dem Breakpoint hervorgehoben.

- Wenn der Breakpoint ungültig ist, wird eine Fehlermeldung in der Statusleiste angezeigt.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine Implementierung der- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode, die den Parser aufruft, um den Code Abschnitt (sofern vorhanden) an der angegebenen Position abzurufen.

 In diesem Beispiel wird davon ausgegangen, dass Sie der-Klasse eine Methode hinzugefügt haben `GetCodeSpan` <xref:Microsoft.VisualStudio.Package.AuthoringSink> , die den Textabschnitt überprüft und zurückgibt, `true` Wenn es sich um eine gültige breakpointposition handelt.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
