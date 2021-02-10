---
title: 'Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien | Microsoft-Dokumentation'
description: Hier erfahren Sie, wie Sie Buildprotokolldateien anzeigen, speichern und konfigurieren können. Diese Dateien bieten nützliche Informationen für Aufgaben wie die Problembehandlung bei einem Buildfehler.
ms.custom: SEO-VS-2020
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8bca2ae08037a63cfbf8647808c7b1c7329ad2aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914917"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien

Nachdem Sie ein Projekt in der Visual Studio-IDE erstellt haben, werden Informationen zu diesem Build im Fenster **Ausgabe** angezeigt. Anhand dieser Informationen können Sie beispielsweise einen Buildfehler beheben.

- Bei C++-Projekten können Sie die gleichen Informationen in einer Protokolldatei anzeigen, die beim Erstellen eines Projekts erstellt und gespeichert wird. 

- Bei Projekten mit verwaltetem Code können Sie in das Buildausgabefenster klicken und **STRG**+**S** drücken. Visual Studio fordert Sie auf, einen Speicherort auszuwählen, an dem die Informationen aus dem **Ausgabefenster** in einer Protokolldatei gespeichert werden sollen.

Sie können die IDE ebenfalls verwenden, um anzugeben, welche Informationen zu jedem Build angezeigt werden sollen.

Wenn Sie ein Projekt mithilfe von MSBuild erstellen, können Sie eine Protokolldatei erstellen, um Informationen zum Build zu speichern. Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Anzeigen der Buildprotokolldatei für ein C++-Projekt

1. Öffnen Sie die folgende Datei über den **Windows-Explorer** oder den **Datei-Explorer** (relativ zum Projektstammordner): *Release*\\<ProjectName>\>.Log* oder *Debug\\<ProjectName\>.log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Erstellen einer Buildprotokolldatei für ein Projekt mit verwaltetem Code

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

2. Klicken Sie im **Ausgabefenster** auf eine beliebige Stelle im Text.

3. Drücken Sie **STRG**+**S**.

   Visual Studio fordert Sie auf, einen Speicherort auszuwählen, an dem die Buildausgabe gespeichert werden soll.

Sie können auch Protokolle generieren, indem Sie MSBuild direkt von der Befehlszeile ausführen. Verwenden Sie dabei die Befehlszeilenoption `-fileLogger` (`-fl`). Informationen dazu finden Sie unter [Erhalten von Buildprotokollen mit MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Ändern der Informationsmenge im Buildprotokoll

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**.

2. Klicken Sie auf der Seite **Projekte und Projektmappen** auf **Erstellen und Ausführen**.

3. Wählen Sie einen der folgenden Werte aus der Liste **Ausführlichkeit der MSBuild-Projektbuildausgabe** aus, und klicken Sie dann auf die Schaltfläche **OK**.

    |Ausführlichkeitsgrad|Beschreibung|
    | - |-----------------|
    |**Still**|Zeigt ausschließlich eine Zusammenfassung des Builds an.|
    |**Minimal**|Zeigt eine Zusammenfassung des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden.|
    |**Normal**|Zeigt eine Zusammenfassung des Builds, die wichtigsten Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Diese Detailebene verwenden Sie am häufigsten.|
    |**Detailliert**|Zeigt eine Zusammenfassung des Builds, alle Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Außerdem werden Meldungen von normaler Wichtigkeit angezeigt.|
    |**Diagnose**|Zeigt alle Daten an, die für den Build verfügbar sind. Sie können diese Detailebene für das Debuggen von Fehlern bei benutzerdefinierten Buildskripts und anderen Buildfehlern verwenden.|

     Weitere Informationen finden Sie unter [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) und <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Sie müssen das Projekt neu erstellen, damit Ihre Änderungen im Fenster **Ausgabe** (für alle Projekte) und in der Datei *\<ProjectName>.txt* (nur C++-Projekte) wirksam werden.

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Verwenden von Binärprotokollen, um das Durchsuchen großer Protokolldateien zu vereinfachen

Binärprotokolle sind ein optionales Feature für .NET-Projekte, mit dem das Suchen von Informationen in umfangreichen Protokollen benutzerfreundlicher und einfacher wird. Um Binärprotokolle zu verwenden, installieren Sie die [Projektsystemtools](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Weitere Informationen finden Sie unter [https://msbuildlog.com](https://msbuildlog.com) und [Binary Log](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md) (Binärprotokoll).

## <a name="see-also"></a>Siehe auch

- [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
