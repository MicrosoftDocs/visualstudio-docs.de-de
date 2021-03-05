---
description: Legt den Pfad zu dem im Debugger geladenen Common Language Runtime (CLR) fest.
title: 'IDebugExpressionEvaluator2:: setcorpath | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetCorPath
- IDebugExpressionEvaluator2::SetCorPath
ms.assetid: 27b614ff-7325-4f9b-8da4-61ee020c9410
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afa363b620702c244484612606274dd1cbddb523
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152311"
---
# <a name="idebugexpressionevaluator2setcorpath"></a>IDebugExpressionEvaluator2::SetCorPath
Legt den Pfad zu dem im Debugger geladenen Common Language Runtime (CLR) fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetCorPath(
   LPCOLESTR pcstrCorPath
);
```

```csharp
int SetCorPath(
   string pcstrCorPath
);
```

## <a name="parameters"></a>Parameter
`pcstrCorPath`\
in Der Pfad zu der CLR, die im Debugger geladen wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **expressionevaluatorpackage** -Objekt implementiert wird, das die [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) -Schnittstelle verfügbar macht.

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::SetCorPath(LPCOLESTR pcstrCorPath)
{
    VerifyInPtr(pcstrCorPath);
    HRESULT hr = E_FAIL;

    VBEECompilerSingleton *pVBEECompilerSingleton = VBEECompilerSingleton::Instance();

    if (pVBEECompilerSingleton)
    {
        pVBEECompilerSingleton->LockEECompiler();

        try
        {
            if (!m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))
            {
                CComObject<CVBEECompilerHost> *pEECompilerHost;

                if (SUCCEEDED(CComObject<CVBEECompilerHost>::CreateInstance(&pEECompilerHost)))
                {
                    pEECompilerHost->AddRef();
                    pEECompilerHost->Init(pcstrCorPath);

                    CComPtr<IVbCompilerHost> srpVBHost;
                    HRESULT hr2 = pEECompilerHost->QueryInterface(IID_IVbCompilerHost, (void **)&srpVBHost);

                    pEECompilerHost->Release();

                    if (SUCCEEDED(hr2))
                    {
                        m_pCompiler->RegisterEECompilerHost(srpVBHost);
                    }
                }
            }
            else
            {
                hr = S_OK;
            }

            if (m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))
            {
                ULONG cErrors = 0;
                ULONG cWarnings = 0;

                m_pCompiler->CompileToBound(m_pCompilerHost, &cErrors, &cWarnings, NULL);

                // This needs to happen after bound
                if (m_pCompilerHost->GetVbLibraryType() == TLB_AutoDetect)
                {
                    m_pCompilerHost->AutoSetVbLibraryType();
                }

                VSASSERT(m_pCompiler && m_pCompilerHost && m_pCompilerHost->GetIntrinsicSymbol(t_i4) != NULL, "Invalid state");

                if (cErrors + cWarnings > 0)
                {
                    VSFAIL("Errors from mscorlib.dll and vb runtime!");
                    __leave;
                }

                hr = S_OK;
            }
            else
            {
                VSFAIL("FindCompilerHost shouldn't have failed!");
            }
        }
        catch_hresult;

        VSASSERT(m_pCompilerHost->GetComPlusProject()->GetCompState() >= CS_Bound, "Debugger mscorlib not in bound state");

        pVBEECompilerSingleton->UnlockEECompiler();
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
