---
title: Verwenden der Aufgabenliste
description: Hier erfahren Sie, wie Sie die Aufgabenliste in Visual Studio verwenden können, um Codekommentare effizienter nachverfolgen und verwenden zu können.
ms.date: 10/12/2020
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d19794b4fce3e4a1388f864cecf408e0f7e9c53
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959801"
---
# <a name="use-the-task-list"></a>Verwenden der Aufgabenliste

Verwenden Sie die **Aufgabenliste** , um Codekommentare, die Token wie `TODO` und `HACK` verwenden, nachzuverfolgen und um Verknüpfungen zu verwalten, mit denen Sie direkt zu einem vordefinierten Speicherort im Code gelangen. Klicken Sie auf das Element in der Liste, um an die entsprechende Position im Quellcode zu gelangen.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Aufgabenkommentare (Visual Studio für Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Das Fenster "Aufgabenliste"

Wird die **Aufgabenliste** geöffnet, wird sie unten im Anwendungsfenster angezeigt.

Wählen Sie zum Öffnen der **Aufgabenliste** **Ansicht** > **Aufgabenliste** aus, oder drücken Sie auf der Tastatur **STRG**+ **\\** , **T** .

![Aufgabenliste (Fenster)](../ide/media/vs2015_task_list.png)

Wählen Sie den Header einer beliebigen Spalte aus, um die Sortierreihenfolge der Liste zu verändern. Um die Suchergebnisse weiter zu verfeinern, drücken Sie die **UMSCHALTTASTE** , und klicken Sie auf einen zweiten Spaltenheader. Sie können auch im Kontextmenü die Option **Sortieren nach** und dann einen Header auswählen. Um die Suchergebnisse weiter zu verfeinern, drücken Sie die **UMSCHALTTASTE** , und wählen Sie einen zweiten Header aus.

Klicken Sie im Kontextmenü auf **Spalten einblenden** , um Spalte ein- oder auszublenden. Wählen Sie die Spalten aus, die Sie ein- oder ausblenden möchten.

Ziehen Sie zum Ändern der Spaltenreihenfolge einen Spaltenheader an die gewünschte Position.

## <a name="user-tasks"></a>Benutzeraufgaben

Das Feature „Benutzeraufgabe“ wurde aus Visual Studio 2015 entfernt. Wenn Sie eine Projektmappe mit Benutzeraufgabendaten aus Visual Studio 2013 oder früher öffnen, bleiben die Benutzeraufgabendaten in Ihrer *SUO* -Datei davon unberührt, aber die Benutzeraufgaben werden nicht in der Aufgabenliste angezeigt.

Um weiterhin auf Ihre Benutzeraufgabendaten zugreifen und diese aktualisieren zu können, sollten Sie das Projekt in Visual Studio 2013 öffnen und den Inhalt aller Benutzeraufgaben in Ihr bevorzugtes Projektmanagementtool (z.B. Team Foundation Server) kopieren.

## <a name="tokens-and-comments"></a>Token und Kommentare

Ein Kommentar im Code, dem ein Kommentarzeichen und ein vordefiniertes Token vorangestellt ist, wird ebenfalls in der **Aufgabenliste** angezeigt. Der folgende C#-Kommentar setzt sich beispielsweise aus drei verschiedenen Teilen zusammen:

- Kommentarzeichen (`//`)

- Das Token, z. B. (`TODO`)

- Kommentar (der restliche Text)

```csharp
// TODO: Load state from previously suspended application
```

Da `TODO` ein vordefiniertes Token ist, wird dieser Kommentar als eine `TODO`-Aufgabe in der Liste angezeigt.

### <a name="custom-tokens"></a>Benutzerdefinierte Token

Standardmäßig enthält Visual Studio die folgenden Token: `HACK`, `TODO`, `UNDONE` und `UnresolvedMergeConflict`. Bei ihnen wird nicht zwischen Groß-/Kleinschreibung unterschieden. Sie können außerdem eigene benutzerdefinierte Token erstellen.

> [!NOTE]
> Standardtoken sind nur für die Sprachen C/C++, C# und VB verfügbar. Führen Sie die folgenden Schritte aus, um eigene Token für andere Programmiersprachen zu erstellen.

So erstellen Sie ein benutzerdefiniertes Token:

1. Wählen Sie im Menü **Extras** den Befehl **Optionen** .

2. Öffnen Sie den Ordner **Umgebung** , und wählen Sie dann **Aufgabenliste** aus.

   [Die Seite „Aufgabenlistenoptionen“](../ide/reference/task-list-environment-options-dialog-box.md) wird angezeigt.

   ![Visual Studio – Aufgabenliste](../ide/media/vs2015_task_list_options.png)

3. Geben Sie in das Textfeld **Name** den Tokennamen ein, z.B. **BUG** .

4. Wählen Sie in der Dropdownliste **Priorität** eine Standardpriorität für das neue Token aus.

5. Wählen Sie **Hinzufügen** aus.

> [!TIP]
> Nachdem Sie einen Namen eingeben haben, wird die Schaltfläche **Hinzufügen** aktiviert. Sie müssen einen Namen eingeben, bevor Sie auf **Hinzufügen** klicken.

### <a name="c-todo-comments"></a>C++-TODO-Kommentare

Standardmäßig werden C++-TODO-Kommentare im Fenster **Aufgabenliste** angezeigt.

Wechseln Sie zum Deaktivieren der C++-TODO-Kommentare im Menü **Extras** zu **Optionen** > **Text-Editor** > **C/C++** > **Ansicht** > **Kommentaraufgaben aufzählen** , und legen Sie den Wert auf **FALSE** fest.

## <a name="shortcuts"></a>Verknüpfungen

Eine *Verknüpfung* ist eine Textmarke im Code, die in der **Aufgabenliste** nachverfolgt wird. Sie hat ein anderes Symbol als eine reguläre Textmarke. Doppelklicken Sie auf die Verknüpfung in der **Aufgabenliste** , um an die entsprechende Position im Code zu gelangen.

![Visual Studio – Aufgabenliste – Symbol „Verknüpfung“](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Erstellen einer Verknüpfung

Fügen Sie den Zeiger in den Code ein, in dem Sie eine Verknüpfung platzieren möchten, um eine Verknüpfung zu erstellen. Klicken Sie auf **Bearbeiten** > **Lesezeichen** > **Verknüpfung für Aufgabenliste hinzufügen** , oder drücken Sie **STRG**+**K** > **STRG**+**H** .

Um durch die Verknüpfungen im Code zu navigieren, wählen Sie eine Verknüpfung in der Liste und dann im Kontextmenü **Nächste Aufgabe** oder **Vorherige Aufgabe** aus.

## <a name="see-also"></a>Siehe auch

- [Aufgabenliste, Umgebung, Dialogfeld „Optionen“](../ide/reference/task-list-environment-options-dialog-box.md)
- [Aufgabenkommentare (Visual Studio für Mac)](/visualstudio/mac/task-comments)
