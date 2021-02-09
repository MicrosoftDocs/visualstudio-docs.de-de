---
title: IManagedAddin-Schnittstelle
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 89e705296c6051b8bdec823e523f0a386ff7ff76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920440"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin-Schnittstelle
  Implementieren Sie die IManagedAddin-Schnittstelle, um eine Komponente zu erstellen, die verwaltete VSTO-Add-ins lädt. Diese Schnittstelle wurde im 2007-Microsoft Office System hinzugefügt.

## <a name="syntax"></a>Syntax

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>Methoden
 In der folgenden Tabelle werden die Methoden aufgelistet, die von der IManagedAddin-Schnittstelle definiert werden.

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Wird aufgerufen, wenn eine Microsoft Office-Anwendung ein verwaltetes VSTO-Add-In lädt.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Wird aufgerufen, direkt bevor eine Microsoft Office-Anwendung ein verwaltetes VSTO-Add-In entlädt.|

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie Microsoft Office Anwendungen, beginnend mit dem 2007 Microsoft Office System, die IManagedAddin-Schnittstelle zum Laden von Office-VSTO-Add-Ins. Sie können die IManagedAddin-Schnittstelle implementieren, um ein eigenes VSTO-Add-in-Lade Modul und eine Laufzeit für verwaltete VSTO-Add-Ins zu erstellen, anstatt das VSTO-Add-in-Lade Modul (*VSTOLoader.dll*) und zu verwenden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Weitere Informationen finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Wie verwaltete Add-Ins geladen werden
 Die folgenden Schritte werden beim Start einer Anwendung ausgeführt:

1. Die Anwendung ermittelt VSTO-Add-Ins, indem sie Einträge unter dem folgenden Registrierungsschlüssel sucht:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    Jeder Eintrag unter diesem Registrierungsschlüssel entspricht einer eindeutigen ID des VSTO-Add-Ins. In der Regel ist dies der Name der VSTO-Add-In-Assembly.

2. Die Anwendung sucht unter dem Eintrag für jedes VSTO-Add-In nach einem `Manifest` -Eintrag.

    Verwaltete VSTO-Add-Ins können den vollständigen Pfad eines Manifests im `Manifest` Eintrag unter **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** speichern. Ein Manifest ist eine Datei (normalerweise eine XML-Datei), die Informationen zum Laden des VSTO-Add-Ins bereitstellt.

3. Wenn die Anwendung einen `Manifest` -Eintrag findet, versucht sie, eine Ladekomponenten für verwaltete VSTO-Add-Ins zu laden. Die Anwendung versucht, ein COM-Objekt zu erstellen, das die IManagedAddin-Schnittstelle implementiert.

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Enthält eine VSTO-Add-in-Lade Komponente (*VSTOLoader.dll*), oder Sie können eigene erstellen, indem Sie die IManagedAddin-Schnittstelle implementieren.

4. Die Anwendung ruft die [IManagedAddin::Load](../vsto/imanagedaddin-load.md) -Methode auf und übergibt den Wert des `Manifest` -Eintrags.

5. Die [IManagedAddin::Load](../vsto/imanagedaddin-load.md) -Methode führt zum Laden des VSTO-Add-Ins erforderliche Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO-Add-In aus, das geladen wird.

   Weitere Informationen zu den Registrierungs Schlüsseln, die Microsoft Office-Anwendungen zum Ermitteln und laden verwalteter VSTO-Add-Ins verwenden, finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Leitfaden für die Implementierung von IManagedAddin
 Wenn Sie IManagedAddin implementieren, müssen Sie die dll, die die Implementierung enthält, mithilfe der folgenden CLSID registrieren:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office Anwendungen verwenden diese CLSID, um das COM-Objekt zu erstellen, das IManagedAddin implementiert.

> [!CAUTION]
> Diese CLSID wird auch von *VSTOLoader.dll* in der verwendet [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Wenn Sie IManagedAddin zum Erstellen eines eigenen VSTO-Add-in-Lade-und einer Laufzeitkomponente verwenden, können Sie die Komponente daher nicht auf Computern bereitstellen, auf denen VSTO-Add-Ins ausgeführt werden, die auf basieren [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Weitere Informationen
- [Referenz zur nicht verwalteten API &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
