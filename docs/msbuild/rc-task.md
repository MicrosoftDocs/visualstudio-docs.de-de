---
title: RC-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „RC“ das Microsoft Windows-Ressourcencompilertool (rc.exe) umschließt, das Ressourcen in eine RES-Datei kompiliert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (C++))
- MSBuild (C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a1babf518a3579246903f6479f999d8912dfe5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048785"
---
# <a name="rc-task"></a>RC-Aufgabe

Umschließt das Microsoft Windows-Ressourcencompilertool ( *rc.exe* ). Die **RC** -Aufgabe kompiliert Ressourcen in eine *RES* -Datei, z.B. Cursor, Symbole, Bitmaps, Dialogfelder und Schriftarten. Weitere Informationen finden Sie unter [Ressourcencompiler](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der RC-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige andere Parameter entsprechen einer Befehlszeilenoption.

|Parameter|Beschreibung|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Optionaler **String[]** -Parameter.<br /><br /> Fügt ein Verzeichnis zur Liste der Verzeichnisse hinzu, die nach Includedateien durchsucht werden.<br /><br /> Weitere Informationen finden Sie unter der **/I** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**AdditionalOptions**|Optionaler **String** -Parameter.<br /><br /> Eine Liste von Befehlszeilenoptionen, z. B./\<option1> /\<option2> /\<option#>. Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht durch einen anderen **RC** -Aufgabenparameter dargestellt werden.<br /><br /> Weitere Informationen finden Sie unter den Optionen im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Kultur**|Optionaler **String** -Parameter.<br /><br /> Gibt eine lokale ID an, die die in den Ressourcen verwendete Kultur darstellt.<br /><br /> Weitere Informationen finden Sie unter der **/l** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**IgnoreStandardIncludePath**|Optionaler **Boolean** -Parameter.<br /><br /> Wenn dieser `true` ist, wird verhindert, dass der Ressourcencompiler die INCLUDE-Umgebungsvariable überprüft, wenn nach Header- oder Ressourcendateien gesucht wird.<br /><br /> Weitere Informationen finden Sie unter der **/x** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**NullTerminateStrings**|Optionaler **Boolean** -Parameter.<br /><br /> Wenn dieser `true` ist, lässt er alle Zeichenfolgen in der Zeichenfolgentabelle auf NULL enden.<br /><br /> Weitere Informationen finden Sie unter der **/n** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**PreprocessorDefinitions**|Optionaler **String[]** -Parameter.<br /><br /> Definieren Sie ein oder mehrere Präprozessorsymbole für den Ressourcencompiler. Geben Sie eine Liste von Makrosymbolen an.<br /><br /> Weitere Informationen finden Sie unter der **/d** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-). Weitere Informationen finden Sie ebenfalls unter **UndefinePreprocessorDefinitions** in dieser Tabelle.|
|**ResourceOutputFileName**|Optionaler **String** -Parameter.<br /><br /> Gibt den Namen der Ressourcendatei an. Geben Sie einen Namen für die Ressourcendatei an.<br /><br /> Weitere Informationen finden Sie unter der **/fo** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**ShowProgress**|Optionaler **Boolean** -Parameter.<br /><br /> Wenn dieser `true` ist, werden Meldungen angezeigt, die über den Fortschritt des Compilers berichten.<br /><br /> Weitere Informationen finden Sie unter der **/v** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Quelle**|Erforderlicher `ITaskItem[]`-Parameter.<br /><br /> Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.|
|**SuppressStartupBanner**|Optionaler **Boolean** -Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Geben Sie für weitere Informationen die Befehlszeilenoption **/?** ein, und klicken Sie auf die Option **/nologo**.|
|**TrackerLogDirectory**|Optionaler **String** -Parameter.<br /><br /> Gibt das Verzeichnis des Nachverfolgungsprotokolls an.|
|**UndefinePreprocessorDefinitions**|Hebt ein Präprozessorsymbol auf.<br /><br /> Weitere Informationen finden Sie unter der **/u** -Option im Artikel [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-). Weitere Informationen finden Sie ebenfalls unter **PreprocessorDefinitions** in dieser Tabelle.|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)