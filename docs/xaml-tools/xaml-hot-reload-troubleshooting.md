---
title: Problembehandlung beim Neuladen von XAML im laufenden Betrieb
description: Beheben Sie Probleme, die beim erneuten Laden von XAML auftreten können.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03c5dca96b4e20e36bc6c69b907423f27ac4af71
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833220"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Problembehandlung beim Neuladen von XAML im laufenden Betrieb

Dieses Handbuch zur Problembehandlung umfasst ausführliche Anweisungen, mit denen die meisten Probleme gelöst werden, die verhindern, dass XAML Hot-Neuladen ordnungsgemäß

Das Laden von XAML-Hot wird für WPF-und UWP-Apps unterstützt. Ausführliche Informationen zu den Anforderungen an das Betriebssystem und die Tools finden Sie unter [schreiben und Debuggen von XAML-Code mit XAML Hot Neuladen](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>Das heiße laden ist nicht verfügbar.

Wenn beim Debuggen Ihrer APP die Meldung "das Laden ist nicht verfügbar" in der Symbolleiste in der App angezeigt wird, befolgen Sie die Anweisungen in diesem Artikel, um das Problem zu beheben.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Überprüfen, ob das aktive XAML-laden aktiviert ist

Die Funktion ist standardmäßig aktiviert. Wenn Sie mit dem Debuggen Ihrer APP beginnen, sollten Sie sicherstellen, dass die in-App-Symbolleiste angezeigt wird, die bestätigt, dass das Laden von XAML Hot

![XAML-Hot-Upload verfügbar](../debugger/media/xaml-hot-reload-available.png)

Wenn die in-App-Symbolleiste nicht angezeigt wird, öffnen Sie **Debugoptionen**  >    >  **Allgemein**. Stellen Sie sicher, dass beide Optionen **UI-Debuggingtools für XAML aktivieren** und **XAML-Hot-Neuladen aktivieren** ausgewählt sind.

![Screenshot des Visual Studio-Fensters "Debugoptionen". Es sind allgemeine Debugoptionen ausgewählt, und die Option XAML-Hot-Upload aktivieren ist aktiviert.](../debugger/media/xaml-hot-reload-enable.png)

Wenn diese Optionen ausgewählt sind, wechseln Sie zu Live Visual Tree (**Debuggen** Sie  >  **Windows**  >  **Live Visual Tree**), und vergewissern Sie sich, dass die Schaltfläche **Lauf Zeit Tools in der Anwendungs** Symbolleiste anzeigen (ganz links) ausgewählt ist.

![Screenshot der Symbolleiste am oberen Rand des visuellen Fensters der visuellen Struktur mit ausgewählter Schaltfläche "Lauf Zeit Tools in Anwendung anzeigen".](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Vergewissern Sie sich, dass Sie Debuggen statt an den Prozess anhängen verwenden.

XAML Hot Neuladen erfordert, dass die Umgebungsvariable zum `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` Zeitpunkt des Starts der Anwendung auf 1 festgelegt ist. Visual Studio legt dies automatisch als **Teil des**  >  Befehls **Debuggen Debuggen starten** (oder **F5**) fest. Wenn Sie XAML Hot Upload mit dem Befehl **Debuggen**  >  **an den Prozess anhängen** verwenden möchten, legen Sie die Umgebungsvariable selbst fest.

> [!NOTE]
> Um eine Umgebungsvariable festzulegen, verwenden Sie die Schaltfläche Start, um nach "Umgebungsvariable" zu suchen, und wählen Sie " **System Umgebungsvariablen bearbeiten**" aus. Wählen Sie im daraufhin geöffneten Dialogfeld **Umgebungsvariablen** aus, fügen Sie es als Benutzervariable hinzu, und legen Sie den Wert auf fest `1` . Entfernen Sie die Variable, wenn Sie das Debuggen abgeschlossen haben.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Überprüfen Sie, ob die MSBuild-Eigenschaften richtig sind

Standardmäßig sind Quell Informationen in einer Debugkonfiguration enthalten. Sie wird von MSBuild-Eigenschaften in ihren Projektdateien (z. b. *. csproj) gesteuert. Für WPF ist die-Eigenschaft `XamlDebuggingInformation` , die auf festgelegt werden muss `True` . Bei UWP ist die-Eigenschaft `DisableXbfLineInfo` , die auf festgelegt werden muss `False` . Zum Beispiel:

WPF:

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Vergewissern Sie sich, dass Sie den richtigen Buildkonfigurationsnamen verwenden.

Sie müssen entweder die korrekte MSBuild-Eigenschaft manuell festlegen, um das Laden von XAML Hot (siehe vorheriger Abschnitt) zu unterstützen, oder Sie müssen den standardbuildkonfigurationsnamen (Debug) verwenden. Wenn Sie die MSBuild-Eigenschaft nicht ordnungsgemäß festlegen, funktioniert ein benutzerdefinierter buildkonfigurationsname weder, noch wird ein Releasebuild ausgeführt.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Überprüfen Sie, ob die XAML-Datei keine Fehler aufweist.

Wenn die XAML-Datei Fehler im **Fehlerliste** anzeigt, funktioniert das Laden von XAML-Hot möglicherweise nicht.

## <a name="see-also"></a>Weitere Informationen

[Schreiben und Debuggen von XAML-Code mit XAML Hot Neuladen](xaml-hot-reload.md)
