---
description: Ermöglicht es der Ausdrucks Auswertung (EE), die Rückruf Schnittstelle anzugeben, die die Debugger-Engine (de) zum Lesen von Metrikeinstellungen verwendet.
title: 'IDebugExpressionEvaluator2:: SetCallback | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc858ab5d26ccffe33d26296e033ac577ddba440
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152389"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Ermöglicht es der Ausdrucks Auswertung (EE), die Rückruf Schnittstelle anzugeben, die die Debugger-Engine (de) zum Lesen von Metrikeinstellungen verwendet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Parameter
`pCallback`\
in Schnittstelle, die für den Einstellungs Rückruf verwendet werden soll.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Diese Methode stellt eine Schnittstelle zum sitzungsdebug-Manager bereit, der von einer Ausdrucks Auswertung zum Lesen von Metrikeinstellungen verwendet werden kann. Es ist beim Remote Debuggen hilfreich, um Metriken auf dem Computer zu lesen [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="example"></a>Beispiel
In den folgenden Beispielen wird gezeigt, wie Sie diese Methode für ein **CEE** -Objekt implementieren, das die [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
