---
title: Fehlermeldungs-Dialogfeld für „Bearbeiten und Fortfahren“ | Microsoft-Dokumentation
description: Die Option „Bearbeiten und fortfahren“ meldet möglicherweise, dass sie für Ihre Codeänderungen nicht verfügbar ist. In diesem Artikel sind mögliche Gründe hierfür aufgeführt.
ms.custom: SEO-VS-2020
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ef34889b838e2f7eaa92420eec90db9def57e65
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862843"
---
# <a name="edit-and-continue-error-message"></a>Fehlermeldung für „Bearbeiten und Fortfahren“

Das Dialogfeld **Bearbeiten und Fortfahren** wird angezeigt, wenn Sie in einer Codesprache debuggen, bei der die Funktion „Bearbeiten und Fortfahren“ unterstützt wird, „Bearbeiten und Fortfahren“ aber für die von Ihnen vorgenommenen Codeänderungen nicht verfügbar ist. Die Fehlermeldung enthält eine ausführlichere Erklärung. Um auf das Dialogfeld zu reagieren, wählen Sie **OK** aus, um das Dialogfeld zu schließen und den Bearbeitungsversuch abzubrechen.

Mögliche Ursachen für diesen Fehler:

- Sie versuchen, SQL Server-Code zu bearbeiten.
- Sie versuchen, optimierten Code zu bearbeiten. Möglicherweise müssen Sie von einem Releasebuild zu einem Debugbuild wechseln.
- Sie versuchen, Code zu bearbeiten, während er ausgeführt wird (und nicht, während er im Debugger angehalten ist). Versuchen Sie, [einen Breakpoint festzulegen](../debugger/using-breakpoints.md) und den Code im angehaltenen Zustand zu bearbeiten.
- Sie versuchen, verwalteten Code zu bearbeiten, wenn nur nicht verwaltetes Debuggen aktiviert ist. „Bearbeiten und Fortfahren“ funktioniert nicht bei [Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).
- Sie nehmen eine Codeänderung vor, die in Ihrer Programmiersprache von „Bearbeiten und Fortfahren“ nicht unterstützt wird. Weitere Informationen finden Sie in den Artikeln über [unterstützte Codeänderungen in C#](supported-code-changes-csharp.md), [nicht unterstützte Bearbeitungen in „Bearbeiten und Fortfahren“ in Visual Basic](supported-code-changes-csharp.md) und [unterstützte C++-Codeänderungen](supported-code-changes-cpp.md).
- Sie versuchen, Code in einer angefügten App zu bearbeiten, statt das Debuggen über das Menü **Debuggen** zu starten.
- Sie versuchen, Code während des Debuggens einer Watson-Sicherungskopie zu bearbeiten.
- Sie versuchen, Code nach dem Auftreten eines Ausnahmefehlers zu bearbeiten, und die Option **Aufrufliste für Ausnahmefehler entladen** ist dabei nicht aktiviert.
- Sie versuchen, Code zu bearbeiten, während Sie eine eingebettete Laufzeitanwendung debuggen.
- Sie versuchen, verwalteten Code mit einer älteren .NET Framework-Version als 4.5.1 mit einem 64-Bit-App-Ziel zu bearbeiten. Wenn Sie „Bearbeiten und fortfahren“ für ältere .NET Framework-Versionen als 4.5.1 verwenden möchten, legen Sie unter **\<ProjectName>**  > **Eigenschaften** > **Kompilieren** für die Einstellung **Advanced Compiler** (Erweiterter Compiler) als Ziel **x86** fest.
- Sie versuchen, Code in einer Assembly zu bearbeiten, die während des Debuggens geändert und erneut geladen wurde.
- Sie versuchen, Code in einer Assembly zu bearbeiten, die nicht geladen wurde.
- Sie starten das Debugging einer alten Version einer App, da die aktuelle Version Buildfehler enthält.

Weitere Informationen finden Sie unter:
- [Blogbeitrag zu „Bearbeiten und Fortfahren“ in C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)
- [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)