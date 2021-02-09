---
title: Setwef ProcessID-Methode
description: Erfahren Sie, wie die setwef ProcessID-Methode die Prozess-ID bereitstellt, mit der WEF-Inhalte (Web Extensions Framework) ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882407"
---
# <a name="setwefprocessid-method"></a>Setwef ProcessID-Methode
  Stellt den Prozess Bezeichner bereit, mit dem WEF-Inhalte (Web Extensions Framework) ausgeführt werden.

## <a name="syntax"></a>Syntax

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwProcessId*|Der Prozess Bezeichner, der zum Ausführen von WEF-Inhalten verwendet wird.|

## <a name="return-value"></a>Rückgabewert
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.

## <a name="remarks"></a>Bemerkungen
 Diese Methode muss aufgerufen werden, nachdem der WEF-Inhalts Prozess erstellt wurde, aber bevor WEF-Inhalte ausgeführt werden.

 Wenn Sie möchten, dass die Entwicklungsumgebung einen Debugger an den WEF-Inhalts Prozess anfügt, muss die Umgebung diesen Vorgang in der Implementierung dieser Methode ausführen.
