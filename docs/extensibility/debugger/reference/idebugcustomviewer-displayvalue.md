---
title: Idebugcustomviewer::D isplayvalue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732451"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Diese Methode wird aufgerufen, um den angegebenen Wert anzuzeigen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Parameter
`hwnd`\
in Übergeordnetes Fenster

`dwID`\
in ID für benutzerdefinierte Viewer, die mehr als einen Typ unterstützen.

`pHostServices`\
[in]: Reserviert Immer auf NULL festgelegt.

`pDebugProperty`\
in Eine Schnittstelle, mit der der anzuzeigende Wert abgerufen werden kann.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Anzeige ist "modal", da diese Methode das erforderliche Fenster erstellt, den Wert anzeigt, auf die Eingabe wartet und das Fenster schließt, bevor es an den Aufrufer zurückgegeben wird. Dies bedeutet, dass die Methode alle Aspekte der Anzeige des Eigenschafts Werts behandeln muss, von der Erstellung eines Fensters für die Ausgabe bis hin zum warten auf Benutzereingaben, um das Fenster zu zerstören.

 Um das Ändern des Werts für das angegebene [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Objekt zu unterstützen, können Sie die [setvalueasstringwitherror](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) -Methode – verwenden, wenn der Wert als Zeichenfolge ausgedrückt werden kann. Andernfalls ist es erforderlich, eine benutzerdefinierte Schnittstelle zu erstellen – exklusiv für die Ausdrucks Auswertung, die diese `DisplayValue` Methode implementiert – für dasselbe Objekt, das die- `IDebugProperty3` Schnittstelle implementiert. Diese benutzerdefinierte Schnittstelle stellt Methoden zum Ändern der Daten einer beliebigen Größe oder Komplexität bereit.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
