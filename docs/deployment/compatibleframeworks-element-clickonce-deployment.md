---
title: '&lt;compatibleframe- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
description: Das compatibleframe-Element identifiziert die Versionen der .NET Framework, in denen diese Anwendung installiert und ausgeführt werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5da9819cd3df667be5e8fa04372684f82762c037
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383065"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleframe- &gt; Element (ClickOnce-Bereitstellung)
Identifiziert die Versionen von .NET Framework, mit denen diese Anwendung installiert und ausgeführt werden kann.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) unterstützt das- `compatibleFrameworks` Element nicht, wenn ein Anwendungs Manifest gespeichert wird, das bereits mit einem Zertifikat signiert wurde, das [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)verwendet. Stattdessen müssen Sie [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)verwenden.

## <a name="syntax"></a>Syntax

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das- `compatibleFrameworks` Element ist für Bereitstellungs Manifeste erforderlich, die auf die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] von .NET Framework 4 oder höher bereitgestellte Laufzeit abzielen. Das- `compatibleFrameworks` Element enthält ein oder mehrere- `framework` Elemente, die die .NET Framework Versionen angeben, auf denen diese Anwendung ausgeführt werden kann. Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Laufzeit führt die Anwendung auf dem ersten aus, der `framework` in dieser Liste verfügbar ist.

 In der folgenden Tabelle werden die Attribute aufgelistet, die das- `compatibleFrameworks` Element unterstützt.

|attribute|Beschreibung|
|---------------|-----------------|
|`S` `upportUrl`|Optional. Gibt eine URL an, unter der die bevorzugte kompatible .NET Framework Version heruntergeladen werden kann.|

## <a name="framework"></a>Framework
 Erforderlich. In der folgenden Tabelle werden die Attribute aufgelistet, die das- `framework` Element unterstützt.

|attribute|Beschreibung|
|---------------|-----------------|
|`targetVersion`|Erforderlich. Gibt die Versionsnummer des Ziel .NET Framework an.|
|`profile`|Erforderlich. Gibt das Profil des Ziel .NET Framework an.|
|`supportedRuntime`|Erforderlich. Gibt die Versionsnummer der Laufzeit an, die der Ziel .NET Framework zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel zeigt ein- `compatibleFrameworks` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungs Manifest. Diese Bereitstellung kann auf dem ausgeführt werden [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Sie kann auch auf dem .NET Framework 4 ausgeführt werden, da es sich um eine übergeordnete Gruppe von handelt [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)