---
title: Iwef debuggingsupport-Schnittstelle
description: Erfahren Sie, wie Sie eine Debugumgebung wie Visual Studio verwenden können, um das Debugging von Microsoft Office Anwendungen zu vereinfachen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a818973bdc2f62194d6ed0026c0798806fe5f2a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525317"
---
# <a name="iwefdebuggingsupport-interface"></a>Iwef debuggingsupport-Schnittstelle
  Wird von einer Debugumgebung implementiert, z. b. Visual Studio, um das Debuggen von Apps für Office zu vereinfachen. Die Office-Anwendung, z. b. Word oder Excel, ruft diese Schnittstelle von Visual Studio ab und ruft dann an bestimmten Punkten während der Debugsitzung Methoden für die Schnittstelle auf.

## <a name="syntax"></a>Syntax

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Methoden
 In der folgenden Tabelle werden die Methoden aufgelistet, die von der iwefdebuggingsupport-Schnittstelle definiert werden.

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Getautoinsertextensions-Methode](../vsto/getautoinsertextensions-method.md)|Ruft Informationen zu den Apps für Office ab, die während des Debuggens automatisch eingefügt werden sollen.|
|[Setwef ProcessID-Methode](../vsto/setwefprocessid-method.md)|Stellt den Prozess Bezeichner bereit, mit dem WEF-Inhalte (Web Extensions Framework) ausgeführt werden.|
