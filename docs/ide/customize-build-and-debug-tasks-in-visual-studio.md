---
title: Anpassen von Build- und Debugaufgaben mit JSON-Dateien
description: Lernen Sie, Aufgaben anzupassen, um einige Konfigurationsdetails zum Ausführen und Debuggen einer Codebasis bereitzustellen, die von Visual Studio nicht erkannt wird.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26f529fe8d9d8731375c4aa0783dde0dadb28a1d
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006457"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Anpassen von Build- und Debugtasks für die Open Folder-Entwicklung

Visual Studio weiß, wie viele verschiedene Sprachen und Codebasen ausgeführt werden, aber nicht, wie alles ausgeführt wird. Wenn Sie in Visual Studio [einen Codeordner geöffnet haben](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) und Visual Studio weiß, wie der Code ausgeführt wird, können Sie die Ausführung ohne weitere Konfiguration sofort starten.

Wenn die Codebasis benutzerdefinierte Buildtools verwendet, die Visual Studio nicht erkennt, müssen Sie einige Konfigurationsdetails angeben, um den Code in Visual Studio auszuführen und zu debuggen. Sie definieren *Buildtasks*, um Visual Studio anzuweisen, wie der Code kompiliert werden soll. Sie können eine oder mehrere Buildtasks erstellen, um alle Elemente anzugeben, die eine Sprache benötigt, um den Code zu kompilieren und auszuführen. Sie können auch frei wählbare Buildtasks erstellen, die nahezu alles ausführen können, was Sie möchten. Beispielsweise können Sie einen Task erstellen, um den Inhalt eines Ordners aufzulisten oder eine Datei umzubenennen.

Passen Sie Ihre Codebasis ohne Projekt mithilfe der folgenden *JSON*-Dateien an:

|Dateiname|Zweck|
|-|-|
|*tasks.vs.json*|Geben Sie benutzerdefinierte Buildbefehle und Compileroptionen sowie frei wählbare (nicht auf den Build bezogene) Tasks an.<br>Der Zugriff erfolgt über das Kontextmenüelement **Tasks konfigurieren** im **Projektmappen-Explorer**.|
|*launch.vs.json*|Geben Sie Befehlszeilenargumente für das Debuggen an.<br>Der Zugriff erfolgt über das Kontextmenüelement **Einstellungen für Debuggen und Starten** im **Projektmappen-Explorer**.|

Diese *JSON*-Dateien befinden sich in einem ausgeblendeten Ordner namens *.vs* im Stammverzeichnis Ihrer Codebasis. Die Dateien *tasks.vs.json* und *launch.vs.json* werden von Visual Studio bei Bedarf erstellt, wenn Sie im **Projektmappen-Explorer** für eine Datei oder einen Ordner die Option **Tasks konfigurieren** oder **Einstellungen für Debuggen und Starten** auswählen. Diese *JSON*-Dateien werden ausgeblendet, da Benutzer sie in der Regel nicht in die Quellcodeverwaltung einchecken möchten. Wenn Sie jedoch die Möglichkeit haben möchten, sie in die Quellcodeverwaltung einzuchecken, ziehen Sie die Dateien in das Stammverzeichnis Ihrer Codebasis, wo sie sichtbar sind.

> [!TIP]
> Klicken Sie zum Anzeigen ausgeblendeter Dateien in Visual Studio auf die Schaltfläche **Alle Dateien anzeigen** auf der Symbolleiste des **Projektmappen-Explorers**.

## <a name="define-tasks-with-tasksvsjson"></a>Definieren von Tasks mit „tasks.vs.json“

Sie können Buildskripts oder andere externe Vorgänge in den Dateien automatisieren, die sich in Ihrem aktuellen Arbeitsbereich befinden, indem Sie sie direkt in der IDE als Tasks ausführen. Sie können einen neuen Task konfigurieren, indem Sie mit der rechten Maustaste auf eine Datei oder einen Ordner klicken und **Tasks konfigurieren** auswählen.

![Menü „Tasks konfigurieren“](../ide/media/customize-configure-tasks-menu.png)

Dadurch wird die Datei *tasks.vs.json* im Ordner *.vs* erstellt (oder geöffnet). Sie können in dieser Datei einen Buildtask oder einen frei wählbaren Task definieren und diesen dann unter Verwendung des Namens aufrufen, den Sie dem Task im **Projektmappen-Explorer**-Kontextmenü zugewiesen haben.

Benutzerdefinierte Tasks können zu einzelnen Dateien oder zu allen Dateien eines bestimmten Typs hinzugefügt werden. Sie können z.B. NuGet-Paketdateien mit einem Task „Pakete wiederherstellen“ konfigurieren. Sie können auch alle Quelldateien so konfigurieren, dass sie einen statischen Task aufweisen, z.B. einen Linter für alle *JS*-Dateien.

### <a name="define-custom-build-tasks"></a>Definieren von benutzerdefinierten Buildtasks

Wenn Ihre Codebasis benutzerdefinierte Buildtools verwendet, die von Visual Studio nicht erkannt werden, können Sie den Code in Visual Studio erst ausführen und debuggen, wenn Sie einige Konfigurationsschritte ausgeführt haben. Visual Studio stellt *Buildtasks* bereit, mit denen Sie Visual Studio anweisen können, wie Ihr Code kompiliert, neu kompiliert und bereinigt wird. Die Buildtaskdatei *tasks.vs.json* koppelt die innere Entwicklungsschleife von Visual Studio mit den benutzerdefinierten Buildtools, die Ihre Codebasis verwendet.

Betrachten wir eine Codebasis, die aus einer einzelnen C#-Datei namens *hello.cs* besteht. Das *Makefile* für eine solche Codebasis könnte folgendermaßen aussehen:

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

Für ein solches *Makefile*, das Ziele für die Kompilierung, Bereinigung und Neukompilierung enthält, können Sie die folgende *tasks.vs.json*-Datei definieren. Die Datei enthält drei Buildtasks zum Kompilieren, Neukompilieren und Bereinigen der Codebasis und verwendet NMAKE als Buildtool.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Nachdem Sie Buildtasks in *tasks.vs.json* definiert haben, werden den entsprechenden Dateien im **Projektmappen-Explorer** zusätzliche Kontextmenüelemente hinzugefügt. Bei diesem Beispiel werden die Optionen „Erstellen“, „Neu erstellen“ und „Bereinigen“ zum Kontextmenü jedes *Makefiles* hinzugefügt.

![Kontextmenü für „makefile“ zum Kompilieren, Neukompilieren und Bereinigen](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Die Befehle werden aufgrund ihrer `contextType`-Einstellungen im Kontextmenü unterhalb des Befehls **Tasks konfigurieren** angezeigt. „build“, „rebuild“ und „clean“ sind Buildbefehle und werden daher im Buildabschnitt in der Mitte des Kontextmenüs angezeigt.

Wenn Sie eine dieser Optionen auswählen, wird der entsprechende Task ausgeführt. Die Ausgabe wird im Fenster **Ausgabe** angezeigt, Buildfehler in der **Fehlerliste**.

### <a name="define-arbitrary-tasks"></a>Definieren von frei wählbaren Tasks

Sie können frei wählbare Tasks in der Datei *tasks.vs.json* definieren, um so ziemlich jede gewünschte Aktion auszuführen. Sie können z.B. einen Task definieren, um den Namen der aktuell ausgewählten Datei im Fenster **Ausgabe** anzuzeigen oder um die Dateien in einem bestimmten Verzeichnis aufzulisten.

Das folgende Beispiel zeigt eine *tasks.vs.json*-Datei, die einen einzelnen Task definiert. Wenn der Task aufgerufen wird, zeigt er den Dateinamen der aktuell ausgewählten *JS*-Datei an.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` gibt den Namen an, der im Kontextmenü angezeigt wird.
- `appliesTo` gibt an, für welche Dateien der Befehl ausgeführt werden kann.
- Die `command`-Eigenschaft gibt den Befehl an, der aufgerufen werden soll. In diesem Beispiel wird die Umgebungsvariable `COMSPEC` verwendet, um den Befehlszeileninterpreter zu identifizieren, in der Regel *cmd.exe*.
- Die `args`-Eigenschaft gibt die Argumente an, die an den aufgerufenen Befehl übergeben werden sollen.
- Das `${file}`-Makro ruft die ausgewählte Datei im **Projektmappen-Explorer** ab.

Nach dem Speichern von *tasks.vs.json* können Sie mit der rechten Maustaste auf eine beliebige *JS*-Datei im Ordner klicken und **Echo für Dateiname** auswählen. Der Dateiname wird im Fenster **Ausgabe** angezeigt.

> [!NOTE]
> Wenn Ihre Codebasis keine *tasks.vs.json*-Datei enthält, können Sie eine solche Datei erstellen, indem Sie im **Projektmappen-Explorer** im Kontextmenü einer Datei auf **Tasks konfigurieren** klicken.

Das nächste Beispiel definiert einen Task, der die Dateien und Unterordner des *bin*-Verzeichnisses auflistet.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` ist ein benutzerdefiniertes Makro, das zuerst vor dem `tasks`-Block definiert wird. Danach wird es in der `args`-Eigenschaft aufgerufen.

Dieser Task gilt für alle Dateien. Wenn Sie das Kontextmenü für eine beliebige Datei im **Projektmappen-Explorer** öffnen, wird der Name des Tasks, **List Outputs** am unteren Rand des Menüs angezeigt. Wenn Sie **List Outputs** auswählen, werden die Inhalte des *bin*-Verzeichnisses im Fenster **Ausgabe** in Visual Studio angezeigt.

![Frei wählbarer Task im Kontextmenü](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Einstellungsbereich

Im Stammverzeichnis und den Unterverzeichnisse einer Codebasis können mehrere *tasks.vs.json*-Dateien vorhanden sein. Dieses Design bietet die Flexibilität, in verschiedenen Unterverzeichnissen der Codebasis verschiedene Verhaltensweisen zu erzielen. Visual Studio aggregiert oder überschreibt Einstellungen in der gesamten Codebasis und priorisiert Dateien in der folgenden Reihenfolge:

- Einstellungsdateien im *.vs*-Verzeichnis des Stammverzeichnisses.
- Das Verzeichnis, in dem eine Einstellung berechnet wird.
- Das übergeordnete Verzeichnis des aktuellen Verzeichnisses, bis hoch zum Stammverzeichnis.
- Einstellungsdateien im Stammverzeichnis.

Diese Aggregationsregeln gelten für *tasks.vs.json*. Informationen darüber, wie Einstellungen in anderen Dateien aggregiert werden, finden Sie im entsprechenden Abschnitt für die Datei im vorliegenden Artikel.

### <a name="properties-for-tasksvsjson"></a>Eigenschaften für „tasks.vs.json“

Dieser Abschnitt beschreibt einige der Eigenschaften, die Sie in *tasks.vs.json* angeben können.

#### <a name="appliesto"></a>appliesTo

Sie können Tasks für jede Datei und jeden Ordner erstellen, indem Sie den Namen der Datei bzw. des Ordners im Feld `appliesTo` angeben. Beispiel: `"appliesTo": "hello.js"`. Die folgenden Dateimasken können als Werte verwendet werden:

|Dateimaske|Beschreibung|
|-|-|
|`"*"`| Der Task ist für alle Dateien und Ordner im Arbeitsbereich verfügbar.|
|`"*/"`| Der Task ist für alle Ordner im Arbeitsbereich verfügbar.|
|`"*.js"`| Der Task ist für alle Dateien mit der Erweiterung *.js* im Arbeitsbereich verfügbar.|
|`"/*.js"`| Der Task ist für alle Dateien mit der Erweiterung *.js* im Stammverzeichnis des Arbeitsbereichs verfügbar.|
|`"src/*/"`| Der Task ist für alle Unterordner des Ordners *src* verfügbar.|
|`"makefile"`| Der Task ist für alle *Makefiles* im Arbeitsbereich verfügbar.|
|`"/makefile"`| Der Task ist nur für das *Makefile* im Stammverzeichnis des Arbeitsbereichs verfügbar.|

#### <a name="macros-for-tasksvsjson"></a>Makros für „tasks.vs.json“

|Makro|Beschreibung|
|-|-|
|`${env.<VARIABLE>}`| Gibt jede Umgebungsvariable an (z.B. ${env.PATH}, ${env.COMSPEC} usw.), die für die Developer-Eingabeaufforderung festgelegt ist. Weitere Informationen finden Sie unter [Developer-Eingabeaufforderung für Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Der vollständige Pfad zum Arbeitsbereichsordner (z.B. *C:\sources\hello*).|
|`${file}`| Der vollständige Pfad der Datei oder des Ordners, für die bzw. den dieser Task ausgeführt werden soll (z.B. *C:\sources\hello\src\hello.js*).|
|`${relativeFile}`| Der relative Pfad zu der Datei oder dem Ordner (z.B. *src\hello.js*).|
|`${fileBasename}`| Der Name der Datei ohne Pfad oder Erweiterung (z.B. *hello*).|
|`${fileDirname}`| Der vollständige Pfad zur Datei ohne den Dateinamen (z.B. *C:\sources\hello\src*).|
|`${fileExtname}`| Die Erweiterung der ausgewählten Datei (z.B. *.js*).|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurieren des Debuggens mit „launch.vs.json“

Informationen zum Konfigurieren von CMake-Projekten für das Debuggen finden Sie unter [Konfigurieren von CMake-Debugsitzungen](/cpp/build/configure-cmake-debugging-sessions).

1. Um Ihre Codebasis für das Debuggen zu konfigurieren, wählen Sie im **Projektmappen-Explorer** aus dem Kontextmenü Ihrer ausführbaren Datei das Menüelement **Einstellungen für Debuggen und Starten** aus.

   ![Kontextmenü „Einstellungen für Debuggen und Starten“](media/customize-debug-launch-menu.png)

1. Wählen Sie im Dialogfeld **Debugger auswählen** eine Option aus, und klicken Sie dann auf die Schaltfläche **Auswählen**.

   ![Dialogfeld „Debugger auswählen“](media/customize-select-a-debugger.png)

   Wenn die *launch.vs.json*-Datei noch nicht vorhanden ist, wird sie erstellt.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Klicken Sie als Nächstes im **Projektmappen-Explorer** mit der rechten Maustaste auf die ausführbare Datei, und wählen Sie **Als Startelement festlegen** aus.

   Die ausführbare Datei wird als Startelement für Ihre Codebasis festgelegt, und die Bezeichnung der **Startschaltfläche** für das Debuggen spiegelt den Namen Ihrer ausführbaren Datei wider.

   ![Angepasste Startschaltfläche](media/customize-start-button.png)

   Wenn Sie **F5** drücken, wird der Debugger gestartet und hält an jedem Haltepunkt an, den Sie festgelegt haben. Alle vertrauten Debuggerfenster sind verfügbar und funktionsfähig.

   > [!IMPORTANT]
   > Weitere Informationen zu benutzerdefinierten Build- und Debugtasks in „Ordner öffnen“-Projekten für C++ finden Sie unter [„Ordner öffnen“-Unterstützung für C++-Buildsysteme in Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Angeben von Argumenten für das Debuggen

Sie können Befehlszeilenargumente angeben, die in der Datei *launch.vs.json* zum Debuggen übergeben werden. Fügen Sie die Argumente im `args`-Array hinzu, wie im folgenden Beispiel gezeigt:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Wenn Sie diese Datei speichern, wird der Name der neuen Konfiguration in der Dropdownliste der Debugziele angezeigt, und Sie können diese auswählen, um den Debugger zu starten. Sie können so viele Debugkonfigurationen erstellen, wie Sie möchten.

![Dropdownliste der Debugkonfigurationen](media/customize-debug-configurations.png)

> [!NOTE]
> Die `configurations`-Arrayeigenschaft in *launch.vs.json* wird aus zwei Speicherorten gelesen: dem Stammverzeichnis für die Codebasis und dem *.vs*-Verzeichnis. Wenn ein Konflikt vorliegt, erhält der Wert in *.vs\launch.vs.json* Priorität.

## <a name="additional-settings-files"></a>Zusätzliche Einstellungsdateien

Zusätzlich zu den drei in diesem Thema beschriebenen *JSON*-Dateien liest Visual Studio auch Einstellungen aus einigen weiteren Dateien, wenn diese in Ihrer Codebasis vorhanden sind.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio liest eingeschränkte Einstellungen aus einer Datei namens *settings.json*, wenn diese sich in einem Verzeichnis namens *.vscode* befindet. Diese Funktionalität wurde für Codebasen bereitgestellt, die zuvor in Visual Studio Code entwickelt wurden. Zurzeit wird aus *.vscode\settings.json* nur die Einstellung `files.exclude` gelesen, die Dateien visuell im Projektmappen-Explorer und aus einigen Suchtools filtert.

Sie können beliebig viele *.vscode\settings.json*-Dateien in Ihrer Codebasis verwenden. Aus dieser Datei gelesene Einstellungen werden auf das übergeordnete Verzeichnis von *.vscode* und alle Unterverzeichnisse angewendet.

### <a name="gitignore"></a>.gitignore

Mit *.gitignore*-Dateien wird Git angewiesen, welche Dateien ignoriert werden sollen, d.h. welche Dateien und Verzeichnisse Sie nicht einchecken möchten. *.gitignore*-Dateien werden üblicherweise in die Codebasis aufgenommen, damit die Einstellungen für alle Entwickler der Codebasis freigegeben werden können. Visual Studio liest Muster in *.gitignore*-Dateien, um Elemente visuell und aus einigen Suchtools zu filtern.

Aus der *.gitignore*-Datei gelesene Einstellungen werden auf das übergeordnete Verzeichnis und alle Unterverzeichnisse angewendet.

## <a name="see-also"></a>Siehe auch

- [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Open Folder-Projekte für C++](/cpp/build/open-folder-projects-cpp)
- [CMake-Projekte für C++](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE-Referenz](/cpp/build/reference/nmake-reference)
- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
