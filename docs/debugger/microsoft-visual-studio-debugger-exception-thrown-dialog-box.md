---
title: Microsoft Visual Studio Debugger (Ausnahmeverweis) (Dialogfeld) | Microsoft-Dokumentation
titleSuffix: ''
description: 'In diesem Artikel erfahren Sie, wie Sie vorgehen müssen, wenn eine Ausnahme auftritt, die von Ihrem Programm verarbeitet werden muss. Sie haben folgende Möglichkeiten: Sie können den Debugger unterbrechen, die Ausführung fortsetzen oder die Ausnahme ignorieren.'
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2982912a0bf165f25b7777311d6db9a1bbe01a8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930277"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (Ausnahmeverweis) (Dialogfeld)
Im Programm ist eine Ausnahme aufgetreten. In diesem Dialogfeld wird die Art der ausgelösten Ausnahme angezeigt. Die Ausnahme muss durch den Code behandelt werden. Folgende Optionen stehen für das Behandeln der Ausnahme zur Verfügung:

 **Unterbrechen** Die Ausführung wird im Debugger unterbrochen. Der Ausnahmehandler wird vor der Unterbrechung nicht aufgerufen. Wenn Sie ab der Unterbrechung fortsetzen, wird der Ausnahmehandler aufgerufen.

 **Weiter** Die Ausführung wird fortgesetzt, sodass die Ausnahme vom Ausnahmehandler behandelt werden kann. Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar. Mit **Weiter** kann die Anwendung fortgesetzt werden. In einer systemeigenen Anwendung wird die Ausnahme bei dieser Option erneut ausgelöst. In einer verwalteten Anwendung wird dadurch entweder das Programm beendet oder die Ausnahme wird von einer Hostanwendung behandelt.

> [!NOTE]
> In verwaltetem Code können Sie die Ausführung nach einem Ausnahmefehler nicht fortsetzen. Wenn Sie nach einem Ausnahmefehler in verwaltetem Code auf **Weiter** klicken, wird das Debuggen beendet.

 **Ignorieren** Diese Option ermöglicht das Fortsetzen der Ausführung ohne Aufrufen des Ausnahmehandlers. Dies kann sich weiter auswirken und beispielsweise zu weiteren Ausnahmen und Fehlern führen. Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar.

## <a name="see-also"></a>Siehe auch
- [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)
- [Bewährte Methoden für Ausnahmen](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Ausnahmebehandlung](/cpp/extensions/exception-handling-cpp-component-extensions)