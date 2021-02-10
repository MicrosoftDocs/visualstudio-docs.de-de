---
title: VCMessage-Aufgabe| Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „VCMessage“ während eines Builds für C++-Projekte Warnungen und Fehlermeldungen protokolliert.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8db60044080726b61a02a59cad68d93f683e282
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908828"
---
# <a name="vcmessage-task"></a>VCMessage-Aufgabe

Protokolliert Warn- und Fehlermeldungen während eines Builds

## <a name="remarks"></a>Hinweise

 Diese Aufgabe unterstützt bei der Implementierung von MSBuild für C++-Projekte und ist nicht dazu gedacht, vom Benutzer aufgerufen zu werden. Weitere Informationen finden Sie unter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **VCMessage**-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**Argumente**|Optionaler **String** -Parameter.<br /><br /> Eine durch Semikolons getrennte Liste der Nachrichten, die angezeigt werden sollen|
|**Code**|Erforderlicher **String**-Parameter.<br /><br /> Eine Fehlernummer, die die Nachricht identifiziert|
|**Typ**|Optionaler **String** -Parameter.<br /><br /> Gibt die Art der auszugebenden Meldung an Gibt entweder „Warning“ an, um eine Warnung auszugeben, oder „Error“ für eine Fehlermeldung.|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
