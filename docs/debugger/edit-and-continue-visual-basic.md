---
title: Bearbeiten und Fortfahren (Visual Basic) | Microsoft-Dokumentation
description: „Bearbeiten und fortfahren“ ist für Visual Basic-Projekte verfügbar. Hier erfahren Sie, welche Änderungen unterstützt werden und wie Sie steuern können, ob und wann Ihre Änderungen angewendet werden.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f5df9910d779a4c360a0c1f3b6482b5c51256d29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871922"
---
# <a name="edit-and-continue-visual-basic"></a>Bearbeiten und Fortfahren (Visual Basic)
Bearbeiten und Fortfahren ist ein Feature von [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)]-Debuggen, mit dem Sie den Code ändern können, während der Unterbrechungsmodus ausgeführt wird. Nachdem Codebearbeitungen übernommen wurden, können Sie die Ausführung mit den neuen Änderungen fortsetzen und deren Auswirkung beobachten.

 Sie können das Feature Bearbeiten und Fortfahren immer dann verwenden, wenn Sie sich im Unterbrechungsmodus befinden. Im Unterbrechungsmodus zeigt der Anweisungszeiger (eine gelbe Pfeilspitze im Quellcodefenster) auf die Zeile, die eine ausführbare Anweisung innerhalb eines Methodentexts oder eines Eigenschaftentexts enthält, die als Nächstes ausgeführt wird.

 Die Funktion "Bearbeiten und Fortfahren" unterstützt bis auf einige Ausnahmen die meisten Änderungen, die Sie möglicherweise während einer Debugsitzung vornehmen möchten. Weitere Informationen finden Sie unter [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Wenn Sie eine unberechtigte Bearbeitung vornehmen, wird die Änderung durch eine violette wellenförmige Linie gekennzeichnet, und in der Aufgabenliste wird eine Aufgabe angezeigt. Sie müssen eine unberechtigte Bearbeitung rückgängig machen, wenn Sie Bearbeiten und Fortfahren weiterhin verwenden möchten. Bestimmte unberechtigte Bearbeitungen sind möglicherweise zulässig, wenn sie außerhalb von Bearbeiten und Fortfahren durchgeführt werden. Wenn Sie die Ergebnisse einer solchen unberechtigten Bearbeitung beibehalten möchten, müssen Sie das Debuggen beenden und die Anwendung neu starten.

 „Bearbeiten und Fortfahren“ wird in UWP-Apps für Windows 10 sowie für x86- und x64-Apps unterstützt, die für .NET Framework 4.6 oder höhere Versionen vorgesehen sind (.NET Framework ist nur als Desktopversion verfügbar).

 > [!NOTE]
 > Nicht unterstützte Apps und Plattformen sind u. a. ASP.NET 5, Silverlight 5 und Windows 8.1.

 Bearbeiten und Fortfahren wird nicht unterstützt, wenn Sie das Debuggen mit **An den Prozess anhängen** beginnen. Die Funktion „Bearbeiten und Fortfahren“ wird für Projekte mit optimiertem Code oder Projekte mit gemischtem verwalteten und nativen Code nicht unterstützt. Weitere Informationen finden Sie unter [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

 In den Themen zu diesem Abschnitt finden Sie weitere Informationen darüber, wie diese Funktion verwendet wird, und welche Arten von Änderungen nicht zulässig sind.

## <a name="in-this-section"></a>In diesem Abschnitt
 [How to: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von „Bearbeiten und Fortfahren“](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Erläutert, wie Codeänderungen im Unterbrechungsmodus angewendet werden.

 [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md) Hier wird beschrieben, welche Arten von Bearbeitungen nicht mit der Funktion „Bearbeiten und Fortfahren“ in [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] ausgeführt werden können.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md) Enthält eine Liste mit Themen zur Funktion „Bearbeiten und Fortfahren“.
