---
title: Empfohlene Debuggereigenschafteneinstellungen für C# und VB | Microsoft-Dokumentation
description: Sehen Sie sich die Einstellungen für Build- und Kompilierungseigenschaften an, die für das gesamte verwaltete Debuggen identisch sein sollten. Andere Einstellungen können je nach Projekttyp variieren.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 57740c05e31bde2ae4e5143735e3bba1f3fc112c
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903804"
---
# <a name="managed-debugging-recommended-property-settings"></a>Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen
Bestimmte Eigenschaften sollten für alle Szenarios des verwalteten Debuggens gleich festgelegt werden.

 Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen.

 Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein. So wird beispielweise die Einstellung für **Startaktion** in einem Windows Forms-Projekt anders als in einem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Projekt festgelegt.

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Konfigurationseigenschaften auf der Registerkarte Erstellen (C#) oder auf der Registerkarte Kompilieren (Visual Basic)

|**Eigenschaftenname**|**Einstellung**|
|-----------------------|-----------------|
|**DEBUG-Konstante definieren**|C# and F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Debug-Klasse verwenden.|
|**TRACE-Konstante definieren**|C# and F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Trace-Klasse verwenden.|
|**Code optimieren**|C#, F# und Visual Basic: auf „false“ festlegen. Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im Fenster **Disassembly** angezeigte Code aus optimiertem Code generiert wurde, der möglicherweise nicht mit dem Code im Code-Editor übereinstimmt. Um optimierten Code zu debuggen, müssen Sie Nur mein Code deaktivieren. (Weitere Informationen finden Sie unter [Restrict stepping to Just My Code (Schrittweises Durchlaufen auf „Nur eigenen Code“ beschränken)](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).)<br /><br /> Weitere Informationen finden Sie unter [Projekteinstellungen für C#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md) und [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Ausgabepfad**|Legen Sie als Ausgabepfad „bin\Debug\\\“ fest.|
|**Erweiterte Kompilierungsoptionen**|nur Visual Basic. Klicken Sie auf **Erweitert**, um die erweiterten Eigenschaften festzulegen, die in der folgenden Tabelle beschrieben werden.|

### <a name="advanced-compiler-settings-dialog-box"></a>Dialogfeld "Erweiterte Compilereinstellungen"

|**Eigenschaftenname**|**Einstellung**|
|-----------------------|-----------------|
|**Optimierungen aktivieren**|Legen Sie die Einstellung auf „false“ fest. Die Gründe hierfür finden Sie in der vorherigen Tabelle unter der Option **Code optimieren**.|
|**Debuginformationen generieren**|Aktivieren Sie das Kontrollkästchen, damit das /DEBUG-Flag beim Kompilieren festgelegt wird. Dadurch werden Informationen generiert, die das Debuggen erleichtern.|
|**DEBUG-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `DEBUG`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Debug>-Klasse verwenden.|
|**TRACE-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `TRACE`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Trace>-Klasse verwenden.|

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)