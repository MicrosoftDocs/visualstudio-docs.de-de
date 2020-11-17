---
title: EditorConfig
description: Verwendung einer EditorConfig-Datei zum Aktivieren konsistenter Codierungskonventionen für Projekte in Visual Studio für Mac.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.topic: how-to
ms.openlocfilehash: c7269b4272fb8ed2c73dbe9f57e94da071dc623e
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493061"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Erstellen und Bearbeiten einer benutzerdefinierten EditorConfig-Datei

In Visual Studio für Mac können Sie Ihrem Projekt oder Ihrer Projektmappe eine [EditorConfig](https://editorconfig.org/)-Datei hinzufügen, um einheitliche Codierungskonventionen für alle Benutzer durchzusetzen, die an der Codebasis arbeiten. Die in der EditorConfig-Datei deklarierten Einstellungen haben Vorrang vor den globalen Einstellungen des Visual Studio für Mac-Text-Editors. Die Verwendung einer EditorConfig-Datei in Ihrem Projekt oder Ihrer Codebase ermöglicht Ihnen, Codierungskonventionen, Einstellungen und Warnungen für Ihr Projekt festzulegen. Da die Datei Teil Ihrer Codebasis ist, ist es für alle Benutzer einfacher, sich an die Codierungspraktiken eines Projekts zu halten, unabhängig davon, welche IDE oder welchen Code-Editor sie verwenden.

[EditorConfig](https://editorconfig.org/)-Dateien werden von vielen IDEs und Code-Editoren unterstützt, einschließlich Visual Studio.

## <a name="supported-settings"></a>Unterstützte Einstellungen

Der Editor in Visual Studio für Mac unterstützt die gebräuchlichsten [EditorConfig-Eigenschaften](https://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

Eine EditorConfig-Datei unterstützt zudem [Codierungskonventionen](/visualstudio/ide/editorconfig-code-style-settings-reference) in C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Hinzufügen einer EditorConfig-Datei zu einem Projekt

### <a name="adding-a-new-editorconfig-file"></a>Hinzufügen einer neuen EditorConfig-Datei

1. Öffnen Sie Ihr Projekt in Visual Studio für Mac. Wählen Sie entweder den Projektmappen- oder den Projektknoten aus, zu dem Sie die EditorConfig-Datei hinzufügen möchten. Durch das Hinzufügen der Datei zum Projektmappenverzeichnis werden die Einstellungen aus .editorconfig auf alle Projekte in der Projektmappe angewendet.

2. Klicken Sie mit der rechten Maustaste auf den Knoten, und wählen Sie anschließend **Hinzufügen > Neue Datei** aus, um das Dialogfeld **Neue Datei** zu öffnen:

    ![Inhalt der Menüelemente](media/editorconfig-image0.png)

3. Wählen Sie **Sonstiges > Leere Textdatei** aus, und geben Sie ihr den **Namen** `.editorconfig`. Klicken Sie auf **Neu**, um die Datei zu erstellen und im Editor zu öffnen:

    ![Dialogfeld „Neue Datei“](media/editorconfig-image1.png)

    Das Hinzufügen des Elements auf Projektmappenebene erstellt und verschachtelt es automatisch in einen Ordner namens **Solution Items** (Projektmappenelemente):

    ![Im Projektmappenfenster angezeigtes Projektmappenelement](media/editorconfig-image1a.png)

4. Bearbeiten Sie die Datei. Zum Beispiel:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Die Einstellungen aus der `.editorconfig`-Datei gelten für jeden neuen Code, den Sie schreiben, aber es kann sein, dass vorhandener Code neu formatiert werden muss, um mit den neuen Einstellungen konsistent zu sein. Um die Einstellungen aus der `.editorconfig`-Datei in eine vorhandene Quelldatei zu übernehmen, öffnen Sie die Datei und klicken dann in der Menüleiste auf **Bearbeiten > Formatieren > Dokument formatieren**:

    ![Menüelement „Dokument formatieren“](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Hinzufügen einer vorhandenen EditorConfig-Datei

Wenn Sie mit einem Projekt oder einer Projektmappe arbeiten, die bereits eine `.editorconfig`-Datei enthält, müssen Sie nichts tun, um diese Einstellungen anzuwenden. Neue Codezeilen werden gemäß den EditorConfig-Einstellungen formatiert.

Sie sollten eine vorhandene `.editorconfig`-Datei in Ihrem Projekt wiederverwenden. Um eine vorhandene Datei hinzuzufügen, führen Sie folgende Schritte aus:

1. Klicken Sie mit der rechten Maustaste auf den Ordner, zu dem die Datei hinzugefügt werden soll, und wählen Sie **Hinzufügen > Dateien hinzufügen** aus.

2. Navigieren Sie zum Verzeichnis der gewünschten Datei.

3. Dateien, die mit `.` beginnen (z.B. `.editorconfig`) sind versteckte Dateien in macOS, drücken Sie daher auf **cmd+UMSCHALT+ .** , um die `.editorconfig`-Datei sichtbar zu machen.

4. Wählen Sie die `.editorconfig`-Datei aus, und klicken Sie auf **Öffnen**:

    ![Hinzufügen eines neuen Dateifensters](media/editorconfig-image3b.png)

5. Wenn das folgende Dialogfeld angezeigt wird, wählen Sie die Option **Datei in das Verzeichnis kopieren** aus, und klicken Sie auf **OK**:

    ![Optionen im Dialogfeld zum Hinzufügen einer Datei zum Ordner](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Spiegeln von .editorconfig-Einstellungen

Sobald Sie eine EditorConfig-Datei zu Ihrer Codebasis hinzufügen, wird jeder neu hinzugefügte Code automatisch entsprechend den angegebenen Einstellungen formatiert. Bestehender Code spiegelt nicht automatisch die Einstellungen wider, es sei denn, Sie formatieren die Codebasis.

Wählen Sie den Projektmappenknoten aus, und klicken Sie in der Menüleiste auf **Bearbeiten > Formatieren > Dokument formatieren**, um die Einstellungen der `.editorconfig`-Datei zu übernehmen:

![Dokument formatieren – Menüleiste](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>Bearbeiten von EditorConfig-Dateien

EditorConfig-Dateien verwenden ein einfaches Dateilayout zum Angeben von Einstellungen, was im Folgenden unter Verwendung eines vorherigen Beispiels erläutert wird:

```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Durch Festlegen von `root` auf `true` wird diese Datei als oberste Datei der Codebase markiert, und alle höheren `.editorconfig`-Dateien im Projekt werden ignoriert, wie im Abschnitt [Überschreiben der EditorConfig-Einstellungen](#override-editorconfig-settings) erläutert wird.

Jeder Abschnitt wird durch ein Quadrat ( **[ ]** ) gekennzeichnet und gibt Informationen zu den Arten von Dateien an, auf die die folgenden Eigenschaften sich beziehen.

Im obigen Beispiel werden einige Einstellungen auf alle Dateien im Projekt angewendet. Andere werden nur C#-Dateien hinzugefügt. Die folgenden Screenshots zeigen den Code vor und nach der Anwendung der `.editorconfig`-Einstellung:

**Vorher**:

![Bevor die EditorConfig-Einstellungen angewendet wurden](media/editorconfig-image4.png)

**Nachher**:

![Nachdem die EditorConfig-Einstellungen angewendet wurden](media/editorconfig-image5.png)

Weitere Informationen über die verfügbaren EditorConfig-Einstellungen finden Sie im Artikel [Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“](/visualstudio/ide/editorconfig-code-style-settings-reference) und im Abschnitt [Supported Properties (Unterstützte Eigenschaften)](https://editorconfig.org/#supported-properties) der offiziellen Dokumentation.

## <a name="override-editorconfig-settings"></a>Überschreiben von EditorConfig-Einstellungen

Es ist möglich, dass mehr als eine `.editorconfig`-Datei in einer Projektmappe enthalten ist. Visual Studio für Mac liest `.editorconfig`-Dateien in der Projektmappe von oben nach unten, wobei Einstellungen hinzugefügt und überschrieben werden. Dabei haben die Einstellungen in der `.editorconfig`-Datei Vorrang, die der von Ihnen bearbeiteten Datei am _nächsten_ liegen. Die Einstellungen werden aus der `.editorconfig`-Datei im gleichen Ordner (falls vorhanden), dann aus der `.editorconfig`-Datei im übergeordneten Ordner (falls vorhanden) usw. übernommen, bis `root=true` gefunden wird.

Wenn Sie sicherstellen möchten, dass _keine_ Einstellungen von übergeordneten `.editorconfig`-Dateien auf diesen Teil der Codebase angewendet werden, fügen Sie die `root=true`-Eigenschaft oben in der untergeordneten `.editorconfig`-Datei ein:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefinierten Editor-Einstellungen mit „EditorConfig“ (Visual Studio unter Windows)](/visualstudio/ide/create-portable-custom-editor-options)