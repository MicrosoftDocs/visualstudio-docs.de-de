---
title: Unterstützen des Fensters Auto in einem Legacy Sprachdienst
description: Erfahren Sie, wie Sie Unterstützung für das Fenster Auto implementieren, in dem Ausdrücke angezeigt werden, die sich im Gültigkeitsbereich befinden, wenn das debuggende Programm angehalten wird
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c97ab4db9b71c91689abe0afb85230e5b0242962
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876505"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Unterstützung für das Fenster "Auto" in einem Legacy Sprachdienst

Im **Fenster Auto** werden Ausdrücke wie Variablen und Parameter angezeigt, die sich im Gültigkeitsbereich befinden, wenn das Programm, das gedebuggt wird, angehalten wurde (entweder aufgrund eines Breakpoints oder einer Ausnahme). Die Ausdrücke können Variablen, lokale oder globale Variablen und Parameter enthalten, die im lokalen Gültigkeitsbereich geändert wurden. Das **Fenster** Auto kann auch Instanziierungen einer Klasse, Struktur oder eines anderen Typs einschließen. Alle Elemente, die von einer Ausdrucks Auswertung ausgewertet werden können, können im **Fenster Auto** angezeigt werden.

 Das Managed Package Framework (MPF) stellt keine direkte Unterstützung für das Auto **-Fenster bereit** . Wenn Sie jedoch die- <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Methode überschreiben, können Sie eine Liste der Ausdrücke zurückgeben, die im Fenster **Auto angezeigt** werden sollen.

## <a name="implementing-support-for-the-autos-window"></a>Implementieren der Unterstützung für das Fenster "Auto"

 Um das Auto **-Fenster zu** unterstützen, müssen Sie lediglich die- <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse implementieren. Ihre Implementierung muss bei Angabe eines Speicher Orts in der Quelldatei entscheiden, welche Ausdrücke **im Fenster "** Auto" angezeigt werden sollen. Die-Methode gibt eine Liste von Zeichen folgen zurück, in denen jede Zeichenfolge einen einzelnen Ausdruck darstellt. Der Rückgabewert gibt an, <xref:Microsoft.VisualStudio.VSConstants.S_OK> dass die Liste Ausdrücke enthält, während <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> angibt, dass keine Ausdrücke angezeigt werden.

 Die tatsächlich zurückgegebenen Ausdrücke sind die Namen der Variablen oder Parameter, die an dieser Stelle im Code angezeigt werden. Diese Namen werden an die Ausdrucks Auswertung weitergegeben, um Werte und Typen abzurufen **, die dann im Fenster Auto** angezeigt werden.

### <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Implementierung der- <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Methode veranschaulicht, die eine Liste der Ausdrücke aus der- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode mithilfe der Analyse Ursache abruft <xref:Microsoft.VisualStudio.Package.ParseReason> . Jeder Ausdruck wird als umschließt `TestVsEnumBSTR` , der die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> Schnittstelle implementiert.

 Beachten Sie, dass die `GetAutoExpressionsCount` -Methode und die- `GetAutoExpression` Methode benutzerdefinierte Methoden für das `TestAuthoringSink` -Objekt sind und für dieses Beispiel hinzugefügt wurden. Sie stellen eine Art dar, in der Ausdrücke, die dem- `TestAuthoringSink` Objekt vom Parser hinzugefügt werden (durch Aufrufen der- <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> Methode), außerhalb des Parsers aufgerufen werden können.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
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
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
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
