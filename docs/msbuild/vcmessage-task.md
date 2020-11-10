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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046754"
---
# <a name="vcmessage-task"></a>VCMessage-Aufgabe

Protokolliert Warn- und Fehlermeldungen während eines Builds

## <a name="remarks"></a>Hinweise

 Diese Aufgabe unterstützt bei der Implementierung von MSBuild für C++-Projekte und ist nicht dazu gedacht, vom Benutzer aufgerufen zu werden. Weitere Informationen finden Sie unter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **VCMessage** -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**Argumente**|Optionaler **String** -Parameter.<br /><br /> Eine durch Semikolons getrennte Liste der Nachrichten, die angezeigt werden sollen|
|**Code**|Erforderlicher **String** -Parameter.<br /><br /> Eine Fehlernummer, die die Nachricht identifiziert|
|**Typ**|Optionaler **String** -Parameter.<br /><br /> Gibt die Art der auszugebenden Meldung an Gibt entweder „Warning“ an, um eine Warnung auszugeben, oder „Error“ für eine Fehlermeldung.|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
