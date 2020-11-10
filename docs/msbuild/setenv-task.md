---
title: SetEnv-Aufgabe| Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „SetEnv“ den Wert einer angegebenen Umgebungsvariable festlegt oder löscht.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7267e90c2fe3e4617fe2bec8bb177baf42ce37b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048305"
---
# <a name="setenv-task"></a>SetEnv-Aufgabe

Legt den Wert einer bestimmten Umgebungsvariable fest oder löscht ihn.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **SetEnv** -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**Name**|Erforderlicher **String** -Parameter.<br /><br /> Der Name einer Umgebungsvariablen.|
|**OutputEnvironmentVariable**|Optionaler **String** -Ausgabeparameter.<br /><br /> Enthält den Wert, der der Umgebungsvariablen zugewiesen ist, die durch den Parameter **Name** angegeben wird.|
|**Präfix**|Erforderlicher `Boolean`-Parameter.<br /><br /> Wenn `true`, wird der Wert des **Value** -Parameters vor dem Wert der Umgebungsvariablen verkettet, die durch den **Name** -Parameter angegeben wird. Anschließend wird der Umgebungsvariable das Ergebnis zugewiesen. Wenn `false`, wird der Umgebungsvariablen nur der Wert des **Value** -Parameters zugewiesen.|
|**Ziel**|Optionaler **String** -Parameter.<br /><br /> Gibt den Ort an, an dem eine Umgebungsvariable gespeichert wird. Geben Sie „User“ oder „Machine“ an.<br /><br /> Weitere Informationen finden Sie unter [EnvironmentVariableTarget-Enumeration](xref:System.EnvironmentVariableTarget).|
|**Wert**|Optionaler **String** -Parameter.<br /><br /> Der Wert, der der Umgebungsvariablen zugewiesen ist, die durch den Parameter **Name** angegeben wird. Die Variable wird gelöscht wenn **Value** leer und die Variable vorhanden ist. Wenn die Variable vorhanden ist, tritt kein Fehler auf, obwohl der Vorgang nicht ausgeführt werden kann.<br /><br /> Weitere Informationen finden Sie unter [Environment::SetEnvironmentVariable-Methode](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
