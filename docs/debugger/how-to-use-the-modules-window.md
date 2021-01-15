---
title: Anzeigen von DLLs und ausführbaren Dateien
description: In diesem Artikel erfahren Sie, wie Sie DLLs und ausführbare Dateien (EXE-Dateien) im Fenster „Module“ anzeigen, die Ihre App während eines Debugsitzung in Visual Studio verwendet.
ms.custom: SEO-VS-2020, seodec18
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0471aa25b14111271e6f9219e8e849eed49f113f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150560"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Anzeigen von DLLs und ausführbaren Dateien im Fenster „Module“ (C#, C++, Visual Basic, F#)

Während des Debuggens in Visual Studio werden im Fenster **Module** die Informationen zu den DLLs und ausführbaren Dateien (*EXE*-Dateien), die von Ihrer App verwendet werden, aufgelistet und angezeigt.

> [!NOTE]
> Das Fenster „Module“ ist nicht für das SQL- oder Skriptdebuggen verfügbar.

## <a name="use-the-modules-window"></a>Verwenden des Modulfensters

Wählen Sie zum Öffnen des Fensters „Module“ während des Debuggens **Debuggen** > **Fenster** > **Module** aus (oder drücken Sie **STRG+ALT+U**).

Module werden im Fenster **Module** standardmäßig nach der Ladereihenfolge sortiert. Um nach einer beliebigen Fensterspalte zu sortieren, wählen Sie die Kopfzeile am oberen Rand der Spalte aus.

## <a name="load-symbols"></a>Laden von Symbolen

In der Spalte **Symbolstatus** im Fenster **Module** wird angezeigt, für welche Module Debugsymbole geladen sind. Wenn der Status **Das Laden von Symbolen wurde übersprungen**, **PDB-Datei wurde nicht gefunden oder konnte nicht geöffnet werden** oder **Der Ladevorgang wurde durch die Einstellung zum Einschließen/Ausschließen deaktiviert** lautet, können Sie Symbole manuell laden. Weitere Informationen zum Laden und Verwenden von Symbolen finden Sie unter [Angeben von Symbol (PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**So laden Sie Symbole manuell:**

1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf das Modul, für das keine Symbole geladen wurden.

   - Wählen Sie **Symbolladeinformationen** aus, um zu erfahren, warum die Symbole nicht geladen wurden.

   - Wählen Sie **Symbole laden** aus, um die Symbole manuell zu laden.

1. Wenn die Symbole nicht geladen werden, wählen Sie **Symboleinstellungen** aus, um das Dialogfeld **Optionen** zu öffnen, und geben Sie Orte für das Laden von Symbolen an, oder ändern Sie diese.

   Sie können Symbole von den öffentlichen Symbolservern von Microsoft oder von anderen Servern herunterladen oder Symbole aus einem Ordner auf dem Computer laden. Details hierzu finden Sie unter [Angeben der Symboldateispeicherorte und des Ladeverhaltens](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**So ändern Sie Einstellungen für das Ladeverhalten von Symbolen**

1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein beliebiges Modul.

1. Klicken Sie auf **Symboleinstellungen**.

1. Wählen Sie **Alle Symbole laden** aus, oder wählen Sie aus, welche Module eingeschlossen oder ausgeschlossen werden sollen.

1. Klicken Sie auf **OK**. Änderungen werden in der nächsten Debugsitzung wirksam.

**So ändern Sie das Symbolladeverhalten für ein bestimmtes Modul**

1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf das Modul.

1. Aktivieren bzw. deaktivieren Sie im Kontextmenü die Option **Immer automatisch laden**. Änderungen werden in der nächsten Debugsitzung wirksam.

## <a name="see-also"></a>Siehe auch
- [Breaking execution (Unterbrechen der Ausführung)](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
- [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)