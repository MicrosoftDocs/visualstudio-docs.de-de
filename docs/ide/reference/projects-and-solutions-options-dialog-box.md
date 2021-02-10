---
title: 'Projekte und Projektmappen: Dialogfeld „Optionen“'
description: Hier erfahren Sie, wie Sie die Seite „Allgemein“ im Abschnitt „Projekte und Projektmappen“ verwenden, um das Verhalten von Visual Studio im Zusammenhang mit Projekten und Projektmappen zu definieren.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2fab59a590b59452362a47d48bcdfa7dd8661f57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907514"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Dialogfeld „Optionen“: Projekte und Projektmappen \> Allgemein

Auf dieser Seite können Sie das Verhalten von Visual Studio für Projekte und Projektmappen festlegen. Klicken Sie zum Zugriff auf diese Optionen auf **Extras** > **Optionen**, erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.

Die folgenden Optionen sind auf der Seite **Allgemein** verfügbar.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Fehlerliste bei Buildfertigstellung mit Fehlern immer anzeigen

Öffnet das Fenster **Fehlerliste** nachdem der Build fertig gestellt ist nur dann, wenn ein Projekt nicht erstellt werden konnte. Hier werden während des Buildvorgangs aufgetretene Fehler angezeigt. Wenn diese Option deaktiviert ist, treten die Fehler weiterhin auf, aber das Fenster wird nicht geöffnet, wenn der Build abgeschlossen ist. Diese Option ist standardmäßig aktiviert.

## <a name="track-active-item-in-solution-explorer"></a>Aktives Element im Projektmappen-Explorer überwachen

Bei Auswahl dieser Option wird der **Projektmappen-Explorer** automatisch geöffnet, und das aktive Element ist ausgewählt. Das ausgewählte Element ändert sich beim Arbeiten mit unterschiedlichen Dateien in einem Projekt oder einer Projektmappe bzw. mit verschiedenen Komponenten in einem Designer. Wenn diese Option deaktiviert ist, ändert sich die Auswahl im **Projektmappen-Explorer** nicht automatisch. Diese Option ist standardmäßig aktiviert.

## <a name="show-advanced-build-configurations"></a>Erweiterte Buildkonfigurationen anzeigen

Wenn diese Option ausgewählt ist, werden die Optionen für die Buildkonfiguration im Dialogfeld **Projekt-Eigenschaftenseiten** und im Dialogfeld **Projektmappen-Eigenschaftenseiten** angezeigt. Wenn diese Option deaktiviert ist, werden die Optionen für die Buildkonfiguration nicht im Dialogfeld **Projekt-Eigenschaftenseiten** und **Projektmappen-Eigenschaftenseiten** für Visual Basic- und C#-Projekte angezeigt, die eine Konfiguration oder beide Konfigurationen (Debug und Release) enthalten. Wenn ein Projekt eine benutzerdefinierte Konfiguration hat, werden die Optionen für die Buildkonfiguration angezeigt.

Wenn diese Option deaktiviert ist, werden die Befehle im Menü **Erstellen**, z.B. **Projektmappe erstellen**, **Projektmappe neu erstellen** und **Projektmappe bereinigen**, für die Releasekonfiguration ausgeführt, und die Befehle im Menü **Debuggen**, z.B. **Debuggen starten** und **Starten ohne Debugging**, werden für die Debugkonfiguration ausgeführt.

## <a name="always-show-solution"></a>Projektmappe immer anzeigen

Bei Auswahl dieser Option werden die Projektmappe und alle Befehle, die für Projektmappen ausgeführt werden, immer in der IDE angezeigt. Wenn diese Option deaktiviert ist, werden alle Projekte als eigenständige Projekte erstellt, und Sie können die Projektmappe im Projektmappen-Explorer oder Befehle, die für Projektmappen ausgeführt werden, in der IDE nicht sehen, wenn die Projektmappe nur ein Projekt enthält.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Neue Projekte beim Erstellen speichern

Bei Auswahl dieser Option können Sie einen Speicherort für das Projekt im Dialogfeld **Neues Projekt** festlegen. Wenn diese Option deaktiviert ist, werden alle neuen Projekte als temporäre Projekte erstellt. Bei der Arbeit mit temporären Projekten können Sie ein Projekt erstellen und damit experimentieren, ohne einen Speicherort angeben zu müssen.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Benutzer bei nicht vertrauenswürdigem Projektspeicherort warnen

Wenn Sie versuchen, ein neues Projekt zu erstellen oder ein vorhandenes Projekt an einem Speicherort zu öffnen, der nicht vollständig vertrauenswürdig ist (z. B. auf einem UNC-Pfad oder HTTP-Pfad), wird eine Meldung angezeigt. Verwenden Sie diese Option, um anzugeben, ob die Meldung jedes Mal angezeigt wird, wenn Sie versuchen, ein Projekt an einem Speicherort zu erstellen oder zu öffnen, der nicht vollständig vertrauenswürdig ist.

## <a name="show-output-window-when-build-starts"></a>Ausgabefenster bei Buildbeginn anzeigen

Zeigt zu Beginn der Projektmappenerstellung automatisch das [Ausgabefenster](../../ide/reference/output-window.md) in der IDE an.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Beim Umbenennen von Dateien zum symbolischen Umbenennen auffordern

Wenn diese Option aktiviert ist, werden Sie in einer Meldung gefragt, ob Visual Studio alle im Projekt enthaltenen Verweise auf das Codeelement umbenennen soll.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Vor dem Verschieben von Dateien an einen neuen Speicherort fragen

Wenn diese Option aktiviert ist, zeigt Visual Studio ein Bestätigungsmeldungsfeld an, bevor die Speicherorte von Dateien durch Aktionen im **Projektmappen-Explorer** verändert werden.

## <a name="reopen-documents-on-solution-load"></a>Dokumente beim Laden der Projektmappe erneut öffnen

Wenn diese Option aktiviert ist, werden die Dokumente, die beim letzten Schließen dieser Projektmappe noch geöffnet waren, automatisch geöffnet, wenn die Projektmappe geöffnet wird.

Das erneute Öffnen von bestimmten Dateitypen oder Designern kann das Laden von Projektmappen verzögern. Deaktivieren Sie diese Option, um die [Leistung beim Laden von Projektmappen](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) zu verbessern, wenn Sie den vorherigen Kontext der Projektmappe nicht wiederherstellen möchten.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Wiederherstellen des Status der Projektmappen-Explorer-Projekthierarchie beim Laden der Projektmappe

Wenn diese Option ausgewählt ist, wird der Zustand der Knoten im Projektmappen-Explorer in Bezug darauf wieder hergestellt, ob sie beim letzten Öffnen der Projektmappe erweitert oder zugeklappt wurden. Deaktivieren Sie diese Option, um die Ladezeit für große Projektmappen zu verringern.

> [!TIP]
> Wenn Sie diese Option deaktivieren, können Sie zum aktiven Dokument im Projektmappen-Explorer navigieren, indem Sie auf der Symbolleiste **Projektmappen-Explorer** auf **Mit aktivem Dokument synchronisieren** klicken.
>
> ![Mit aktivem Dokument im Projektmappen-Explorer synchronisieren](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Öffnen von Projektdateien im SDK-Format mit Doppelklick oder der Eingabetaste

Wenn diese Option ausgewählt ist und Sie im Projektmappen-Explorer auf einen Projektknoten im SDK-Format doppelklicken oder diesen auswählen und dann die **EINGABETASTE** drücken, wird die Projektdatei (z. B. \*CSPROJ-Datei) als XML-Datei im Editor geöffnet. Wenn diese Option deaktiviert ist, wird der Knoten nur erweitern oder zugeklappt, wenn Sie auf einen Projektknoten im SDK-Format im Projektmappen-Explorer doppelklicken oder diesen auswählen und die **EINGABETASTE** drücken.

Wenn Sie diese Option nicht ausgewählt haben und eine Projektdatei im SDK-Format bearbeiten möchten, klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen-Explorer und danach auf **Projektdatei bearbeiten**. Bei anderen Projekttypen müssen Sie das Projekt vor der Bearbeitung in Visual Studio erst noch hochladen.

> [!TIP]
> Ein *Projekt im SDK-Format* oder ein [Projekt-SDK](../../msbuild/how-to-use-project-sdk.md) verfügt über ein neueres und optimiertes Projektdateiformat, das mit MSBuild 15.0 eingeführt wurde. Ein Projekt im SDK-Format enthält ein `Sdk`-Attribut für das `Project`-Element (beispielsweise `<Project Sdk="Microsoft.NET.Sdk">`). Visual Studio erstellt ein Projekt im SDK-Format, wenn Sie beispielsweise ein neues .NET Core-Projekt aus einer der Visual Studio-Vorlagen erstellen.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Dialogfeld „Optionen“: Projekte und Projektmappen \> Speicherorte](projects-solutions-locations-options.md)
- [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Dialogfeld „Optionen“, Projekte und Projektmappen, Webprojekte](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
