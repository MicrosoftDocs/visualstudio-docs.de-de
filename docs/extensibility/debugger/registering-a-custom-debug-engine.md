---
title: Registrieren einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation
description: Erfahren Sie, wie sich das Debug-Modul als Klassenfactory registriert, den com-Konventionen folgt und sich über die Registrierung bei Visual Studio registriert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4581411a2601bf598762a7157f9df0e006995230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961117"
---
# <a name="register-a-custom-debug-engine"></a>Registrieren einer benutzerdefinierten Debug-Engine
Die Debug-Engine muss sich selbst als Klassenfactory registrieren, die auf com-Konventionen folgt und sich über den Visual Studio-Registrierungs Unterschlüssel bei Visual Studio registriert.

> [!NOTE]
> Ein Beispiel für die Registrierung einer Debug-Engine finden Sie im Textinterpreter-Beispiel, das im Rahmen des [Tutorials: Erstellen einer Debug-Engine mithilfe von ATL-COM](/previous-versions/bb147024(v=vs.90))erstellt wird.

## <a name="dll-server-process"></a>DLL-Server Prozess
 Eine Debug-Engine wird in der Regel in einer eigenen dll als com-Server eingerichtet. Daher muss die Debug-Engine die CLSID ihrer Klassenfactory bei com registrieren, bevor Visual Studio darauf zugreifen kann. Anschließend muss die Debug-Engine sich bei Visual Studio registrieren, um Eigenschaften (auch als Metriken bezeichnet) zu erstellen, die von der Debug-Engine unterstützt werden. Die Auswahl der in den Visual Studio-Registrierungs Unterschlüssel geschriebenen Metriken hängt von den Funktionen ab, die die Debug-Engine unterstützt.

 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) beschreiben nicht nur die Registrierungs Speicherorte, die zum Registrieren einer Debug-Engine erforderlich Außerdem wird die Bibliothek " *dbgmetric. lib* " beschrieben, die eine Reihe nützlicher Funktionen und Deklarationen für C++-Entwickler enthält, die die Bearbeitung der Registrierung vereinfachen.

### <a name="example"></a>Beispiel
 Im folgenden Beispiel (aus dem Textinterpreter-Beispiel) wird gezeigt, wie die- `SetMetric` Funktion (aus *dbgmetric. lib*) verwendet wird, um eine Debug-Engine in Visual Studio zu registrieren. Die zu über gebenden Metriken werden auch in *dbgmetric. lib* definiert.

> [!NOTE]
> Textinterpreter ist eine einfache Debug-Engine. Sie richtet – nicht ein und registriert – keine anderen Features. Eine vollständigere Debug-Engine verfügt über eine vollständige Liste mit `SetMetric` aufrufen oder deren Entsprechung, eine für jedes Feature, das die Debug-Engine unterstützt.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Weitere Informationen
- [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: aufbauen einer Debug-Engine mithilfe von ATL-COM](/previous-versions/bb147024(v=vs.90))