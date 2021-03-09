---
title: IManagedAddin::Load
description: Wird aufgerufen, wenn ein verwaltetes VSTO-Add-In geladen wird.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc89ba13e9fc0f62b264cdb926e1a8392c0b41bd
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469761"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wird aufgerufen, wenn ein verwaltetes VSTO-Add-In geladen wird.

## <a name="syntax"></a>Syntax

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*bstrManifestURL*|Der vollständige Pfad des Manifests für das VSTO-Add-In.|
|*pdispapplication*|Ein Zeiger auf eine IDispatch, die die Host Anwendung darstellt, die das VSTO-Add-in lädt.|

## <a name="return-value"></a>Rückgabewert
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.

## <a name="remarks"></a>Bemerkungen
 Ein Manifest ist eine Datei (normalerweise eine XML-Datei), die Informationen zum Laden des VSTO-Add-Ins bereitstellt. Beispielsweise kann ein Manifest den Speicherort der VSTO-Add-In-Assembly angeben und die Einstiegspunktklasse instanziieren, wenn das VSTO-Add-In geladen wird.

 Der *bstrinmanifesturl* -Parameter enthält den Wert des `Manifest` Eintrags unter dem **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** -Registrierungsschlüssel für das VSTO-Add-in. Weitere Informationen finden Sie unter [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md).

 Implementieren Sie die Methode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) , um Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO-Add-In auszuführen, das geladen wird.

## <a name="see-also"></a>Siehe auch
- [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
