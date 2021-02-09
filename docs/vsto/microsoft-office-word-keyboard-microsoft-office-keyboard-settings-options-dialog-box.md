---
title: Office Word-Tastatur, Einstellungen, Dialogfeld "Optionen"
description: Erfahren Sie, wie Sie mit Microsoft Word Tastenkombinationen für Tastenkombinationen abrufen können, wenn das Dokument den Fokus besitzt, indem Sie dynamisches Tastatur Schema auswählen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0138fcd73ddf07202a9111ec2b3d17dcc0fb7a0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879422"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Microsoft Office Word-Tastatur, Einstellungen, Dialogfeld "Optionen"
  Microsoft Office Word und Visual Studio behandeln Tastenkombinationen. Die gleiche Tastenkombination kann für verschiedene Befehle in Word und in Visual Studio stehen. Wenn Word in einem Projekt auf Dokument Ebene in Visual Studio geöffnet ist, empfängt jeweils nur eine Anwendung die Tastenkombinationen. Standardmäßig empfängt Visual Studio alle Tastenkombinationen, Sie können Sie jedoch erhalten, wenn das Dokument den Fokus besitzt, indem Sie **dynamisches Tastatur Schema** auswählen.

 Wenn Sie eine Tastenkombination verwenden, die keinem Befehl in der Anwendung zugewiesen ist, die gerade die Tastenkombinationen verarbeitet, wird die Tastenkombination an die andere Anwendung weitergegeben.

 Die Option, die Sie auswählen, bleibt für Word-Projekte wirksam, bis Sie Sie ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Excel-Projekte aus. Sie müssen eine beliebige Änderung für Excel vornehmen, indem Sie die Microsoft Office Excel-Tastatur Optionen verwenden.

## <a name="uielement-list"></a>UIElement-Liste
 **Visual Studio-Tastatur Schema** Visual Studio empfängt alle Tastenkombinationen, auch wenn das Word-Dokument den Fokus besitzt. Wenn Sie z. b. die Funktionstaste **F5** drücken, während das Dokument den Fokus besitzt, beginnt Visual Studio mit dem Debuggen der Projekt Mappe.

 **Dynamisches Tastatur Schema** Visual Studio empfängt Tastenkombinationen nur dann, wenn es den Fokus besitzt. Wenn das Word-Dokument den Fokus besitzt, empfängt Word alle Tastenkombinationen. Wenn Sie z. b. die Funktionstaste **F5** drücken, während das Word-Dokument den Fokus besitzt, öffnet Word das Dialogfeld **Suchen und ersetzen** , in dem die Registerkarte **Gehe zu** ausgewählt ist. Wenn Sie **F5** drücken, während Visual Studio den Fokus besitzt, beginnt Visual Studio mit dem Debuggen der Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Microsoft Office Excel-Tastatur, Microsoft Office Tastatur Einstellungen, Dialogfeld "Optionen"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
