---
title: Anwenden von Bearbeitungen im Unterbrechungsmodus mit „Bearbeiten und fortfahren“ | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit „Bearbeiten und fortsetzen“ Ihren Visual Basic-Code im Unterbrechungsmodus bearbeiten können. Es gibt verschiedene Möglichkeiten, in den Unterbrechungsmodus zu wechseln.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9074d992c06c1b7d49f59481bee35345c5199f8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155041"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit „Bearbeiten und fortfahren“ (Visual Basic)
Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.

Informationen zu Einschränkungen bei der Verwendung von „Bearbeiten und fortfahren“ beim Debuggen finden Sie unter [Unterstützte Codeänderungen ( C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus

1. Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:

    - Legen Sie einen Breakpoint im Code fest, wählen Sie im Menü **Debuggen** den Befehl **Debuggen starten** aus, und warten Sie, bis die Anwendung den Breakpoint erreicht.

         - oder -

    - Beginnen Sie mit dem Debuggen, und wählen Sie anschließend im Menü **Debuggen** den Befehl **Alle unterbrechen** aus.

         - oder -

    - Wenn eine Ausnahme auftritt, wählen Sie im **Ausnahmen-Assistenten** den Befehl **Bearbeiten aktivieren** aus.

2. Nehmen Sie die gewünschten und unterstützten Codeänderungen vor.

     Weitere Informationen finden Sie unter [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.

3. Klicken Sie im Menü **Debuggen** auf **Weiter**, um mit der Ausführung fortzufahren.

     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.

## <a name="see-also"></a>Siehe auch
- [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
