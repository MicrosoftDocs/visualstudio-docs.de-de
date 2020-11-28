---
title: Codeformatoptionen und Codebereinigung
description: Lernen Sie, Visual Studio mithilfe der Befehle „Codebereinigung“ (Visual Studio 2019) und „Dokument formatieren“ (Visual Studio 2017) zur Anwendung von Codeformateinstellungen zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 04/25/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9172fff2dde1528c5ea382aea996d316e0738ea0
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006678"
---
# <a name="code-style-preferences"></a>Codeformateinstellungen

Codeformateinstellungen können projektweise mithilfe einer [EditorConfig-Datei](#code-styles-in-editorconfig-files) oder für den gesamten Code, den Sie in Visual Studio bearbeiten, auf der Seite [**Optionen** des Text-Editors](#code-styles-in-the-options-dialog-box) definiert werden. Für C#-Code können Sie Visual Studio außerdem mithilfe der Befehle **Codebereinigung** (Visual Studio 2019) und **Dokument formatieren** (Visual Studio 2017) für die Anwendung dieser Codeformateinstellungen konfigurieren.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Editorverhalten in Visual Studio für Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Codeformate in EditorConfig-Dateien

[Codeformateinstellungen](create-portable-custom-editor-options.md) für .NET können durch Hinzufügen einer [EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)-Datei zu Ihrem Projekt angegeben werden. Diese .editorconfig-Dateien sind nicht mit einem Visual Studio-Personalisierungskonto, sondern mit einer Codebasis verknüpft. Die Einstellungen in der Editorconfig-Datei haben Vorrang gegenüber den im Dialogfeld **Optionen** angegebenen Codeformaten. Verwenden Sie eine EditorConfig-Datei, wenn Sie Codierungsstile für alle Mitwirkenden an Ihrem Repository oder Projekt erzwingen möchten.

::: moniker range=">=vs-2019"

Sie können Ihre EditorConfig-Datei manuell auffüllen oder die Datei basierend auf den Codeformateinstellungen, die Sie im Dialogfeld **Optionen** von Visual Studio festgelegt haben, automatisch generieren. Diese Optionsseite finden Sie unter **Extras** > **Optionen** > **Text-Editor** > [**C#** oder **Basic**] > **Codeformat** > **Allgemein**. Klicken Sie auf **Generate .editorconfig file from settings** (Editorconfig-Datei aus Einstellungen generieren), um automatisch eine *.editorconfig*-Codeformatdatei auf Grundlage der Einstellungen auf dieser Seite **Optionen** zu generieren.

![Generieren einer Editorconfig-Datei aus den Einstellungen in Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Codeformate im Dialogfeld „Optionen“

Codeformateinstellungen können für alle Ihre C#- und Visual Basic-Projekte festgelegt werden, indem Sie das Dialogfeld **Optionen** im Menü **Extras** öffnen. Klicken Sie im Dialogfeld **Optionen** auf **Text-Editor** > [**C#** oder **Basic**] > **Codeformat** > **Allgemein**.

Jedes Element auf der Liste zeigt eine Vorschau der Einstellung an, wenn es ausgewählt wird:

::: moniker range="vs-2017"

![Codeformatoptionen](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Codeformatoptionen](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

In diesem Fenster festgelegte Optionen gelten für Ihr Visual Studio-Personalisierungskonto und sind keinem bestimmten Projekt bzw. keiner bestimmten Codebasis zugeordnet. Darüber hinaus werden sie nicht zur Buildzeit erzwungen. Das gilt auch für CI-Builds (Continuous Integration). Wenn Sie Codeformateinstellungen mit Ihrem Projekt verknüpfen möchten und die Formate während des Buildvorgangs erzwungen werden, geben Sie die Einstellungen in einer Datei vom Typ [.editorconfig](#code-styles-in-editorconfig-files) an, die mit dem Projekt verknüpft ist.

### <a name="preference-and-severity"></a>Einstellung und Schweregrad

Sie können für jede dieser Codeformateinstellungen auf dieser Seite über die Dropdownfelder jeder Zeile die Werte für **Preference** (Präferenz)und **Schweregrad** festlegen. Der Schweregrad kann auf **Nur Refactoring**, **Vorschlag**, **Warnung** oder **Fehler** festgelegt werden. Wenn Sie für ein Codeformat [Schnellaktionen](../ide/quick-actions.md) aktivieren möchten, stellen Sie sicher, dass die Einstellung für den **Schweregrad** auf einen anderen Wert als **Nur Refactoring** festgelegt ist. Das Glühbirnensymbol für **Schnellaktionen** :::image type="icon" source="media/light-bulb-dropdown.png":::, Fehlerglühbirnensymbol :::image type="icon" source="media/error-bulb.png"::: oder Schraubendrehersymbol :::image type="icon" source="media/screwdriver.png"::: wird angezeigt, wenn ein nicht bevorzugtes Format verwendet wird, und Sie können eine Option aus der Liste der **Schnellaktionen** auswählen, um den Code automatisch im bevorzugten Format neu zu schreiben.

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>Erzwingen von Codeformatregeln beim Build

Ab Visual Studio 2019 Version 16.8, wo das .NET 5.0 RC2 SDK enthalten ist, können Sie für alle .NET-Projekte die [.NET-Codierungskonventionen beim Build](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) erzwingen. Zur Erstellungszeit werden Verstöße gegen das .NET-Codeformat als Warnungen oder Fehler mit dem Präfix „IDE“ angezeigt. Dies ermöglicht Ihnen, konsistente Codeformate in Ihrer Codebasis strikt zu erzwingen.

::: moniker-end

## <a name="apply-code-styles"></a>Anwenden von Codeformaten

::: moniker range="vs-2017"

Sie können den Befehl **Dokument formatieren** (**Bearbeiten** > **Erweitert** > **Dokument formatieren**) so konfigurieren, dass er Ihre Codeformateinstellungen (aus einer EditorConfig-Datei oder den **Codeformat**-Optionen) zusammen mit der regulären Formatierung anwendet, die er ausführt (z.B. Einzug). Wenn für das Projekt eine *.editorconfig*-Datei vorhanden ist, hat sie den Vorrang.

> [!NOTE]
> Das Anwenden von Codeformaten mithilfe des Befehls **Dokument formatieren** steht nur für C#-Codedateien zur Verfügung. Dies ist ein experimentelles Feature.

Konfigurieren Sie auf der Seite [Formatierungsoptionen](reference/options-text-editor-csharp-formatting.md#format-document-settings), welche Einstellungen **Dokument formatieren** anwenden soll.

![Codeformateinstellungen für „Dokument formatieren“ in Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Regeln, die mit dem Schweregrad **Kein** konfiguriert sind, nehmen nicht an der Codebereinigung teil, können aber einzeln über das Menü **Schnellaktionen und Refactorings** angewendet werden.

Beim ersten Auslösen des Befehls **Dokument formatieren** werden Sie über eine gelbe Infoleiste aufgefordert, Ihre Codebereinigungseinstellungen zu konfigurieren.

::: moniker-end

::: moniker range=">=vs-2019"

Für C#-Codedateien verfügt Visual Studio 2019 über eine Schaltfläche **Codebereinigung** unten im Editor (Tastatur: **STRG**+**K**, **STRG**+**E**), um Codeformate aus einer EditorConfig-Datei oder von der Optionsseite **Codeformat** anzuwenden. Wenn für das Projekt eine *.editorconfig*-Datei vorhanden ist, haben diese Einstellungen Vorrang.

![Ausführen der Codebereinigung in Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Regeln, die mit dem Schweregrad **Kein** konfiguriert sind, nehmen nicht an der Codebereinigung teil, können aber einzeln über das Menü **Schnellaktionen und Refactorings** angewendet werden.

Konfigurieren Sie zunächst im Dialogfeld **Codebereinigung konfigurieren** (in einem von zwei Profilen), welche Codeformate Sie anwenden möchten. Um dieses Dialogfeld zu öffnen, klicken Sie auf den Erweiterungspfeil neben dem Besensymbol der Codebereinigung, und wählen Sie dann **Codebereinigung konfigurieren** aus.

![Codebereinigung konfigurieren in Visual Studio 2019](media/configure-code-cleanup.png)

Nach dem Konfigurieren der Codebereinigung können Sie auf das Besensymbol klicken oder **STRG**+**K** und **STRG**+**E** drücken, um die Codebereinigung auszuführen. Sie können die Codebereinigung auch für Ihr gesamtes Projekt oder Ihre gesamte Projektmappe ausführen. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Namen eines Projekts oder einer Projektmappe, wählen Sie **Analysieren und Code bereinigen** aus, und klicken Sie dann auf **Codebereinigung ausführen**.

![Ausführen der Codebereinigung für ein gesamtes Projekt oder eine gesamte Projektmappe](media/run-code-cleanup-project-solution.png)

Wenn Ihre Codeformateinstellungen bei jedem Speichern einer Datei angewendet werden sollen, gefällt Ihnen möglicherweise die Erweiterung [Code Cleanup on Save](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) (Codebereinigung beim Speichern).

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Schnelle Aktionen](../ide/quick-actions.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Editorverhalten (Visual Studio für Mac)](/visualstudio/mac/editor-behavior)
