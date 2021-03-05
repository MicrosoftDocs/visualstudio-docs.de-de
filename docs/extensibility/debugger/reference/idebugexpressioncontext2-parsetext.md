---
description: Analysiert einen Ausdruck in Textform zur späteren Auswertung.
title: IDebugExpressionContext2::P Ardie Text | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2095a1d6e035c676ab92722f9ae785e1a42c5b78
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152637"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analysiert einen Ausdruck in Textform zur späteren Auswertung.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Parameter
`pszCode`\
in Der Ausdruck, der analysiert werden soll.

`dwFlags`\
in Eine Kombination von Flags aus der [parameeflags](../../../extensibility/debugger/reference/parseflags.md) -Enumeration, mit der die Analyse gesteuert wird.

`nRadix`\
in Der Basis, der zum Auswerten numerischer Informationen in verwendet werden soll `pszCode` .

`ppExpr`\
vorgenommen Gibt das [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) -Objekt zurück, das den analysierten Ausdruck darstellt, der für die Bindung und Auswertung bereit ist.

`pbstrError`\
vorgenommen Gibt die Fehlermeldung zurück, wenn der Ausdruck einen Fehler enthält.

`pichError`\
vorgenommen Gibt den Zeichen Index des Fehlers in zurück, `pszCode` Wenn der Ausdruck einen Fehler enthält.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Wenn diese Methode aufgerufen wird, sollte die Debug-Engine (de) den Ausdruck analysieren und auf Richtigkeit überprüfen. Der `pbstrError` -Parameter und der- `pichError` Parameter können ausgefüllt werden, wenn der Ausdruck ungültig ist.

Beachten Sie, dass der Ausdruck nicht ausgewertet, sondern nur analysiert wird. Ein späterer Aufrufen der [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) -Methode oder der [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) -Methode wertet den analysierten Ausdruck aus.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches-Objekt implementiert wird `CEnvBlock` , das die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle verfügbar macht. In diesem Beispiel wird der Ausdruck als Name einer Umgebungsvariablen analysiert und der Wert aus dieser Variablen abgerufen.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
