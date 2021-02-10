---
title: Getautoinsertextensions-Methode
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
ms.openlocfilehash: 24fd5768a9eafa4a023aeabf21c862ea1a0d1891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931525"
---
# <a name="getautoinsertextensions-method"></a>Getautoinsertextensions-Methode
  Ruft Informationen zu den Apps für Office ab, die während des Debuggens automatisch eingefügt werden sollen.

 Diese Methode ist für eine spätere Verwendung vorgesehen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*psaextensionnames*|Die Erweiterungs Namen der Apps für Office.|

## <a name="return-value"></a>Rückgabewert
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.

## <a name="remarks"></a>Bemerkungen
 Jede APP für Office, die eingefügt werden soll, wird als Name der Office-Anwendungs Erweiterung zurückgegeben, was einem Wert unter **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer** entspricht. Der Host muss diese Werte in der Registrierung suchen und die Erweiterungen dann automatisch einfügen.
