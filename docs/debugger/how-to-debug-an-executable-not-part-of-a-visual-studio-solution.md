---
title: Debuggen einer App, die nicht Teil einer Visual Studio-Projektmappe ist
titleSuffix: ''
description: Informationen zum Debuggen einer App, die nicht Teil einer Visual Studio-Projektmappe ist. Möglicherweise können Sie den Visual Studio-Debugger anfügen.
ms.custom: SEO-VS-2020
ms.date: 02/21/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f201121eb65f7c045ac42783ac71b2d49fafd802
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155002"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Debuggen einer App, die nicht Teil einer Visual Studio-Projektmappe ist (C++, C#, Visual Basic, F#)

Möglicherweise möchten Sie eine App (*EXE*-Datei) debuggen, die nicht Teil einer Visual Studio-Projektmappe ist. Dabei kann es sich um ein Projekt handeln, bei dem [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) verwendet wird, oder Sie bzw. eine andere Person haben die App außerhalb von Visual Studio erstellt, oder Sie haben die App von einem anderen Speicherort abgerufen.

- Informationen zu einem Projekt in Visual Studio, bei dem „Ordner öffnen“ verwendet wird (das keine Projekt- oder Projektmappendatei enthält) finden Sie unter [Ausführen und Debuggen Ihres Codes](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) oder unter [Konfigurieren von Parametern für das Debuggen mit „launch.vs.json“](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson) (für C++).

- Für eine App, die in Visual Studio nicht vorhanden ist, besteht die übliche Methode zum Debuggen darin, die App außerhalb von Visual Studio zu starten und dann im Visual Studio-Debugger mit **An den Prozess anhängen** anzufügen. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Das Anfügen an eine App erfordert manuelle Schritte, die einige Sekunden in Anspruch nehmen. Aufgrund dieser Verzögerung unterstützt das Anfügen nicht das Debuggen eines Startproblems oder eine App, die nicht auf Benutzereingaben wartet und schnell beendet wird.

   In diesen Situationen können Sie ein EXE-Projekt von Visual Studio für die App erstellen oder es in eine vorhandene C#-, Visual Basic- oder C++-Projektmappe importieren. EXE-Projekte werden nicht von allen Programmiersprachen unterstützt.

>[!IMPORTANT]
>Die Debugfunktionen für eine App, die nicht in Visual Studio erstellt wurde, sind begrenzt, unabhängig davon, ob Sie der App etwas anfügen oder sie zu einer Visual Studio-Projektmappe hinzufügen.
>
>Wenn Sie über den Quellcode verfügen, empfiehlt es sich, den Code in ein Visual Studio-Projekt zu importieren. Führen Sie dann einen Debugbuild der App aus.
>
>Wenn Sie nicht über den Quellcode verfügen und die App keine [Debuginformationen](../debugger/how-to-set-debug-and-release-configurations.md) in einem kompatiblen Format aufweist, sind nur wenige Debugfunktionen verfügbar.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>So erstellen Sie ein neues EXE-Projekt für eine vorhandene App

1. Klicken Sie in Visual Studio auf **Datei** > **Öffnen** > **Projekt**.

1. Wählen Sie im Dialogfeld **Projekt öffnen** in der Dropdownliste neben **Dateiname** die Option **Alle Projektdateien** aus, falls diese nicht bereits ausgewählt ist.

1. Navigieren Sie zu der *EXE*-Datei, und wählen Sie sie aus. Anschließend wählen Sie **Öffnen** aus.

   Die Datei wird in einer neuen temporären Visual Studio-Projektmappe angezeigt.

1. Starten Sie das Debuggen der App, indem Sie im Menü **Debuggen** einen Ausführungsbefehl wie **Debuggen starten** auswählen.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>So importieren Sie eine App in eine vorhandene Visual Studio-Projektmappe

1. Wenn eine C++-, C#- oder Visual Basic-Projektmappe in Visual Studio geöffnet ist, wählen Sie **Datei** > **Hinzufügen** > **Vorhandenes Projekt** aus.

1. Wählen Sie im Dialogfeld **Projekt öffnen** in der Dropdownliste neben **Dateiname** die Option **Alle Projektdateien** aus, falls diese nicht bereits ausgewählt ist.

1. Navigieren Sie zu der *EXE*-Datei, und wählen Sie sie aus. Anschließend wählen Sie **Öffnen** aus.

   Die Datei wird als neues Projekt unter der aktuellen Projektmappe angezeigt.

1. Wenn die neue Datei ausgewählt ist, starten Sie das Debuggen der App, indem Sie einen Ausführungsbefehl wie **Debuggen starten** aus dem Menü **Debuggen** auswählen.

### <a name="see-also"></a>Siehe auch
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [DBG files (DBG-Dateien)](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))
