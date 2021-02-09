---
title: 'IDebugProgram3:: executeonthread | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8df69c02fb7e78dbb107db906de59d8b7e5881b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887067"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Führt das Debugger-Programm aus. Der Thread wird zurückgegeben, um den Debuggerinformationen zu dem Thread zu übergeben, den der Benutzer beim Ausführen des Programms anzeigen kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parameter
`pThread`\
in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Es gibt drei verschiedene Möglichkeiten, wie ein Debugger die Ausführung nach dem Beenden fortsetzen kann:

- Ausführen: brechen Sie alle vorherigen Schritte ab, und führen Sie bis zum nächsten Breakpoint und so weiter aus.

- Schritt: brechen Sie jeden alten Schritt ab, und führen Sie aus, bis der neue Schritt abgeschlossen ist.

- Continue: führen Sie den Vorgang erneut aus, und lassen Sie jeden alten Schritt aktiv.

  Der an über gegebene Thread `ExecuteOnThread` ist hilfreich bei der Entscheidung, welcher Schritt abgebrochen werden soll. Wenn Sie den Thread nicht kennen, werden bei der Ausführung von Execute alle Schritte abgebrochen. Wenn Sie wissen über den Thread verfügen, müssen Sie nur den Schritt im aktiven Thread abbrechen.

## <a name="see-also"></a>Weitere Informationen
- [Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
