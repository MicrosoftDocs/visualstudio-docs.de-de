---
description: Ruft den Text an der angegebenen Position im Dokument ab.
title: 'IDebugDocumentText2:: gettext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53ee0ff735cfbec4835e762dfa95e293c95885b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154222"
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
Ruft den Text an der angegebenen Position im Dokument ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetText(
    TEXT_POSITION pos,
    ULONG         cMaxChars,
    WCHAR*        pText,
    ULONG*        pcNumChars
);
```

```csharp
int GetText(
    eumn_TEXT_POSITION pos,
    uint               cMaxChars,
    IntPtr             pText,
    out uint           pcNumChars
);
```

## <a name="parameters"></a>Parameter
`pos`\
in Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die die Position des abzurufenden Texts angibt.

`cMaxChars`\
in Die maximale Anzahl von Zeichen, die abgerufen werden sollen.

`pText`\
[in, out] Ein Zeiger auf einen Puffer, der mit dem gewünschten Text aufgefüllt werden soll. Dieser Puffer muss mindestens eine `cMaxChars` Anzahl von breit Zeichen enthalten können.

`pcNumChars`\
vorgenommen Gibt die Anzahl der tatsächlich abgerufenen Zeichen zurück.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie diese Methode aus c# aufgerufen werden kann.

```csharp
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Debugger.Interop;

namespace Mynamespace
{
    class MyClass
    {
        string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)
        {
            string documentText = string.Empty;
            if (pText != null)
            {
                uint numLines = 0;
                uint numChars = 0;
                int hr;
                hr = pText.GetSize(ref numLines, ref numChars);
                if (ErrorHandler.Succeeded(hr))
                {
                    IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));
                    uint actualChars = 0;
                    hr = pText.GetText(pos, numChars, buffer, out actualChars);
                    if (ErrorHandler.Succeeded(hr))
                    {
                        documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);
                    }
                    Marshal.FreeCoTaskMem(buffer);
                }
            }
            return documentText;
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
