---
title: Definieren von benutzerdefinierten Menübefehlen für Python-Projekte
description: Durch Bearbeiten von Projekt- und TARGETS-Dateien können Sie benutzerdefinierte Befehle zum Kontextmenü des Python-Projekts in Visual Studio hinzufügen, um ausführbare Programme, Skripts, Module, Inline-Codeausschnitte und pip aufzurufen.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 43270ee1ec956f45b76d23a6b649ad2d870638c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887925"
---
# <a name="define-custom-commands-for-python-projects"></a>Definieren von benutzerdefinierten Befehlen für Python-Projekte

Bei der Arbeit mit Ihren Python-Projekten werden Sie oft zu einem Befehlsfenster wechseln, um spezifische Skripts oder Module, PIP-Befehle oder andere beliebige Tools auszuführen. Sie können Ihrem **Python**-Untermenü benutzerdefinierte Befehle im Kontextmenü Ihres Python-Projekts hinzufügen, um Ihren Workflow zu verbessern. Diese Befehle können in einem Konsolenfenster oder im **Ausgabefenster** von Visual Studio ausgeführt werden. Sie können auch reguläre Ausdrücke verwenden, um Visual Studio anzuweisen, wie Fehler und Warnungen von der Ausgabe des Befehls analysiert werden sollen.

Standardmäßig enthält dieses Menü nur den Befehl **PyLint ausführen**:

![Standarddarstellung des Python-Untermenüs im Kontextmenü eines Projekts](media/custom-commands-default-menu.png)

Benutzerdefinierte Befehle werden in eben diesem Kontextmenü angezeigt. Benutzerdefinierte Befehle werden einer Projektdatei direkt hinzugefügt, sie werden nur auf dieses einzelne Projekt angewendet. Sie können benutzerdefinierte Befehle auch in einer *.targets*-Datei definieren, die problemlos in mehrere Projektdateien importiert werden kann.

Bestimmte Python-Projektvorlagen in Visual Studio fügen bereits ihre eigenen benutzerdefinierten Befehle über ihre *.targets*-Datei hinzu. Die Vorlagen „Bottle-Webprojekt“ und „Flask-Webprojekt“ fügen beispielsweise die zwei Befehle **Start server** und **Start debug server** hinzu. Die Vorlage „Django-Webprojekt“ fügt dieselben zwei Befehle und noch ein paar weitere hinzu:

![Darstellung des Python-Untermenüs im Kontextmenü des Django-Webprojekts](media/custom-commands-django-menu.png)

Jeder benutzerdefinierte Befehl kann auf folgendes verweisen: Eine Python-Datei, ein Python-Modul, Inline-Python-Code, eine beliebige ausführbare Datei oder ein PIP-Befehl. Sie können auch angeben, wie und wo der Befehl ausgeführt wird.

> [!Tip]
> Wenn Sie Änderungen an einer Projektdatei in einem Text-Editor vornehmen, müssen Sie das Projekt in Visual Studio erneut laden, damit diese Änderungen angewendet werden. Zum Beispiel müssen Sie ein Projekt erneut laden, nachdem Sie die Definitionen für benutzerdefinierte Befehle hinzugefügt haben, damit diese im Kontextmenü des Projekts angezeigt werden.
>
> Wie Sie vermutlich wissen, bietet Visual Studio die Möglichkeit, Projektdateien direkt zu bearbeiten. Klicken Sie zunächst mit der rechten Maustaste auf die Projektdatei, und wählen Sie **Projekt entladen** aus, klicken Sie erneut mit der rechten Maustaste, und wählen Sie **Bearbeiten\<project-name>** aus, um das Projekt im Visual Studio-Editor zu öffnen. Nehmen Sie dann Ihre Änderungen vor und speichern diese, klicken Sie ein weiteres Mal mit der rechten Maustaste auf das Projekt und wählen **Projekt neu laden** aus. Dann werden Sie dazu aufgefordert, das Schließen der Projektdatei im Editor zu bestätigen.
>
> Beim Entwickeln eines benutzerdefinierten Befehls wird das viele Klicken jedoch mühsam. Laden Sie das Projekt in Visual Studio, und öffnen Sie die *.pyproj*-Datei in einem separatem Editor (z.B. eine weitere Instanz von Visual Studio, Visual Studio Code, Notepad, usw.), um einen effizienteren Workflow zu ermöglichen. Wenn Sie im Editor Änderungen speichern und zu Visual Studio wechseln, erkennt Visual Studio, dass Änderungen vorgenommen wurden, und fragt Sie, ob das Projekt neu geladen werden soll (**Das Projekt \<name> wurde außerhalb der Umgebung geändert.** ). Wählen Sie **Erneut laden** aus, und Ihre Änderungen werden in einem Schritt sofort angewendet.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Exemplarische Vorgehensweise: Hinzufügen eines Befehls zu einer Projektdatei

Dieser Abschnitt zeigt ein einfaches Beispiel, in dem die Startdatei eines Projekts mit *python.exe* direkt ausgeführt wird, damit Sie sich mit benutzerdefinierten Befehlen vertraut machen können. (So ein Befehl entspricht der Verwendung von **Debuggen** > **Starten ohne Debugging**.)

1. Erstellen Sie ein neues Projekt namens „Python-CustomCommands“ mithilfe der Vorlage **Python-Anwendung**. (Siehe [Schnellstart: Erstellen eines Python-Projekts aus einer Vorlage](quickstart-02-python-in-visual-studio-project-from-template.md), falls Sie mit diesem Vorgang noch nicht vertraut sind.)

1. Fügen Sie in *Python_CustomCommands.py* den Code `print("Hello custom commands")` hinzu.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Python** aus. Beachten Sie, dass der einzige Befehl, der im Untermenü angezeigt wird, **PyLint ausführen** ist. Ihre benutzerdefinierten Befehle werden im gleichen Untermenü angezeigt.

1. Öffnen Sie *Python-CustomCommands.pyproj* in einem separaten Text-Editor, wie Ihnen bereits in der Einführung geraten wurde. Fügen Sie dann die folgenden Zeilen innerhalb des schließenden `</Project>` am Ende der Datei ein und speichern die Datei.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Klicken Sie in Visual Studio auf **Erneut laden**, wenn die Dateiänderungen gemeldet werden. Wenn Sie das **Python**-Menü erneut überprüfen, werden Sie sehen, dass **PyLint ausführen** immer noch das einzige Element ist, das dort angezeigt wird, da die von Ihnen hinzugefügten Zeilen nur die Standardeigenschaftengruppe `<PythonCommands>` replizieren, die den PyLint-Befehl enthält.

1. Fügen Sie im Editor die folgende `<Target>`-Definition nach `<PropertyGroup>` ein. Wie weiter unten in diesem Artikel erklärt wird, definiert das Element `Target` einen benutzerdefinierten Befehl, um die Startdatei (die über die Eigenschaft „StartupFile“ identifiziert wird) mithilfe von *python.exe* in einem Konsolenfenster auszuführen. Das Attribut `ExecuteIn="consolepause"` nutzt eine Konsole, die darauf wartet, dass Sie eine Taste drücken, bevor sie geschlossen wird.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Fügen Sie den Wert des Attributs `Name` vom Element „Target“ der Eigenschaftengruppe `<PythonCommands>` hinzu, die Sie zuvor hinzugefügt haben. Das Element sollte dann wie im folgenden Beispiel aussehen. Durch das Hinzufügen des Namens von „Target“ in diese Liste wird es dem **Python**-Menü hinzugefügt.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Wenn Sie möchten, dass Ihr Befehl vor denen aufgeführt wird, die in `$(PythonCommands)` definiert sind, platzieren Sie sie vor diesem Token.

1. Speichern Sie die Projektdatei, und laden Sie das Projekt in Visual Studio erneut. Klicken Sie dann mit der rechten Maustaste auf das Projekt **Python-CustomCommands**, und wählen Sie **Python** aus. Sie sollten das Element **Startdatei ausführen** sehen. Wenn Sie das Menüelement nicht finden können, stellen Sie sicher, dass Sie den Namen dem Element `<PythonCommands>` hinzugefügt haben. Weitere Informationen finden Sie unter [Problembehandlung](#troubleshooting) weiter unten in diesem Artikel.

    ![Benutzerdefinierter Befehl der im Python-Kontextmenü angezeigt wird](media/custom-commands-walkthrough-menu-item.png)

1. Wählen Sie den Befehl **Run startup file** (Startdatei ausführen) aus. Es sollte ein Befehlsfenster mit dem Text **Hello custom commands** (Hallo, benutzerdefinierte Befehle) gefolgt von **Drücken Sie eine beliebige Taste, um fortzufahren** angezeigt werden.  Drücken Sie eine beliebige Taste, um das Fenster zu schließen.

    ![Ausgabe des benutzerdefinierten Befehls in einem Konsolenfenster](media/custom-commands-walkthrough-console.png)

1. Ändern Sie im Editor in der Projektdatei den Wert des Attributs `ExecuteIn` in `output`. Speichern Sie die Datei, laden Sie das Projekt erneut, und rufen Sie den Befehl erneut auf. Dieses Mal wird die Ausgabe des Programms im Fenster **Ausgabe** von Visual Studio angezeigt:

    ![Ausgabe des benutzerdefinierten Befehls im Ausgabefenster](media/custom-commands-walkthrough-output-window.png)

1. Zum Hinzufügen weiterer Befehle definieren Sie ein geeignetes `<Target>`-Element für jeden Befehl, fügen den Namen des Elements „Target“ in die Eigenschaftengruppe `<PythonCommands>` ein und laden das Projekt erneut in Visual Studio.

>[!Tip]
> Wenn Sie einen Befehl aufrufen, der Projekteigenschaften verwendet (z.B. `($StartupFile)`), und der Befehl fehlschlägt, da das Token nicht definiert ist, deaktiviert Visual Studio den Befehl, bis Sie das Projekt erneut laden. Änderungen an dem Projekt, die die Eigenschaft definieren würden, aktualisieren jedoch nicht den Status dieser Befehle. Sie müssen das Projekt in solchen Fällen also erneut laden.

## <a name="command-target-structure"></a>Befehlsstruktur von „Target“

Das allgemeine Format des Elements `<Target>` wird im folgenden Codebeispiel gezeigt:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Verwenden Sie zum Verweisen auf Projekteigenschaften oder Umgebungsvariablen in Attributwerten den Namen in einem `$()`-Token (z.B. `$(StartupFile)` und `$(MSBuildProjectDirectory)`). Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Attribute von „Target“

| Attribut | Erforderlich | Beschreibung |
| --- | --- | --- |
| name | Ja | Der Bezeichner für den Befehl im Visual Studio-Projekt. Dieser Name muss der Eigenschaftengruppe `<PythonCommands>` hinzugefügt werden, damit der Befehl im Python-Untermenü angezeigt wird. |
| Bezeichnung | Ja | Der Anzeigename für die Benutzeroberfläche der im Python-Untermenü angezeigt wird. |
| Rückgabe | Ja | Muss `@(Commands)` enthalten, damit „Target“ als Befehl identifiziert wird. |

### <a name="createpythoncommanditem-attributes"></a>Attribute von CreatePythonCommandItem

Alle Attributwerte beachten die Groß-/Kleinschreibung.

| Attribut | Erforderlich | Beschreibung |
| --- | --- | --- |
| TargetType | Ja | Gibt an, was das Attribut „Target“ enthält , und wie es dem Attribut „Arguments“ verwendet wird:<ul><li>**executable:** Führt die ausführbare Datei aus, die in „Target“ angegeben ist, und fügt den Wert an „Arguments“ an, als ob er direkt in die Befehlszeile eingegeben worden wäre. Der Wert darf nur einen Programmnamen ohne Argumente enthalten.</li><li>**script:** Führt *python.exe* mit dem Dateinamen in „Target“ aus, gefolgt von dem Wert in „Arguments“.</li><li>**module:** Führt `python -m` gefolgt von dem Modulnamen in „Target“ und dem Wert in „Arguments“ aus.</li><li>**code:** Führt den in „Target“ enthaltenen Inlinecode aus. Der Wert „Arguments“ wird ignoriert.</li><li>**pip:** Führt `pip` mit dem in „Target“ enthaltenen Befehl gefolgt von „Arguments“ aus. Wenn „ExecuteIn“ jedoch auf „output“ festgelegt ist, geht pip von einem `install`-Befehl aus und nutzt „Target“ als den Paketnamen.</li></ul> |
| Target | Ja | Der Dateiname, Modulname, Code oder PIP-Befehl, der je nach TargetType genutzt wird. |
| Argumente | Optional | Gibt eine Zeichenfolge der Argumente (sofern vorhanden) an, die an „Target“ übergeben werden. Beachten Sie: Wenn TargetType `script` entspricht, werden die Argumente an das Python-Programm übergeben und nicht an *python.exe*. Wird beim TargetType `code` ignoriert. |
| ExecuteIn | Ja | Gibt die Umgebung an, in der die Anwendung ausgeführt wird:<ul><li>**console:** (Standard) Führt „Target“ und die Argumente aus, als würden sie direkt in die Befehlszeile eingegeben werden. Während „Target“ ausgeführt wird, wird ein Befehlsfenster angezeigt, das dann automatisch geschlossen wird.</li><li>**consolepause:** Entspricht „console“, wartet mit dem Schließen des Befehlsfenster jedoch, bis Sie eine Taste drücken.</li><li>**output:** Führt „Target“ aus und zeigt die Ergebnisse im **Ausgabefenster** in Visual Studio an. Wenn der TargetType „PIP“ ist, verwendet Visual Studio „Target“ als den Paketnamen und fügt „Arguments“ an.</li><li>**repl:** Führt „Target“ im [interaktiven Python-Fenster](python-interactive-repl-in-visual-studio.md) aus. Der optionale Anzeigename wird als Titel des Fensters verwendet.</li><li>**none**: Verhält sich wie „console“.</li></ul>|
| WorkingDirectory | Optional | Der Ordner, in dem der Befehl ausgeführt wird. |
| ErrorRegex<br>WarningRegEx | Optional | Wird nur verwendet, wenn ExecuteIn `output` entspricht. Beide Werte geben einen regulären Ausdruck an, mit dem Visual Studio die Ausgabe des Befehls analysiert, um Fehler und Warnungen im Fenster **Fehlerliste** anzuzeigen. Wenn das Argument nicht angegeben wird, wirkt der Befehl sich nicht auf das Fenster **Fehlerliste** aus. Weitere Informationen darüber, was Visual Studio erwartet, finden Sie unter [Named capture groups (Benannte Erfassungsgruppen)](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Optional | Eine Liste der Paketanforderungen für den Befehl mit demselben Format wie [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (pip.readthedocs.io). Der Befehl **PyLint ausführen** gibt zum Beispiel `pylint>=1.0.0` an. Visual Studio prüft, ob alle in der Liste aufgelisteten Pakete installiert sind, bevor der Befehl ausgeführt wird. Visual Studio nutzt PIP zum Installieren fehlender Pakete. |
| Umgebung | Optional | Eine Zeichenfolge von Umgebungsvariablen, die definiert werden müssen, bevor der Befehl ausgeführt wird. Jede Variable verwendet das Format \<NAME>=\<VALUE> mit mehreren Variablen, die durch Semikolons getrennt werden. Eine Variable mit mehreren Werten muss in einfache oder doppelte Anführungszeichen gesetzt werden, z.B. 'NAME=WERT1;WERT2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Benannte Erfassungsgruppen für reguläre Ausdrücke

Beim Analysieren von Fehlern und Warnungen aus der Ausgabe eines Befehls, erwartet Visual Studio, dass die regulären Ausdrücke in den Werten `ErrorRegex` und `WarningRegex` die folgenden benannten Gruppen verwenden:

- `(?<message>...)`: Fehlertext
- `(?<code>...)`: Fehlercode
- `(?<filename>...)`: Name der Datei, für die der Fehler gemeldet wird.
- `(?<line>...)`: Zeilennummer der Position in der Datei, für die der Fehler gemeldet wird.
- `(?<column>...)`: Spaltennummer der Position in der Datei, für die der Fehler gemeldet wird.

Zum Beispiel erzeugt PyLint Warnungen in folgendem Format:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Damit Visual Studio die richtigen Informationen aus solchen Warnungen extrahieren und in dem Fenster **Fehlerliste** anzeigen kann, sollte der Wert `WarningRegex` für den Befehl **PyLint ausführen** wie folgt aussehen:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Beachten Sie, dass `msg_id` in dem Wert eigentlich `code` sein sollte, siehe [Problem 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Erstellen einer .targets-Datei mit benutzerdefinierten Befehlen

Benutzerdefinierte Befehle, die Sie in einer Projektdatei definieren, macht sie nur für diese Projektdatei verfügbar. Damit Sie diese Befehle in mehreren Projektdateien verwenden können, müssen Sie stattdessen die Eigenschaftengruppe `<PythonCommands>` und all Ihre `<Target>`-Elemente in einer *.targets*-Datei definieren. Importieren Sie diese Datei dann in individuelle Projektdateien.

Die Datei *.targets* hat das folgende Format:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Platzieren Sie ein `<Import Project="(path)">`-Element an einer beliebigen Stelle im Element `<Project>`, um eine *.targets*-Datei in ein Projekt zu laden. Wenn Sie zum Beispiel eine Datei namens *CustomCommands.targets* im Unterordner *targets* in Ihrem Projekt haben, verwenden Sie folgenden Code:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Wenn Sie Änderungen an der Datei *.targets* vornehmen, müssen Sie die *Projektmappe*, die das Projekt enthält, neu laden und nicht nur das Projekt selbst.

## <a name="example-commands"></a>Beispielbefehle

### <a name="run-pylint-module-target"></a>PyLint ausführen (Target-Modul)

Der folgende Code wird in der Datei *Microsoft.PythonTools.targets* angezeigt:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Ausführen der PIP-Installation mit einem spezifischen Paket (PIP-Target)

Der folgende Befehl führt `pip install my-package` im **Ausgabefenster** aus. Diese Art Befehl ist nützlich, wenn Sie ein Paket entwickeln und dessen Installation testen. Beachten Sie, dass „Target“ den Paketnamen enthält, anstelle des Befehls `install`, der vorausgesetzt wird, wenn `ExecuteIn="output"` verwendet wird.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Anzeigen von veralteten PIP-Paketen (PIP-Target)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Ausführen einer ausführbaren Datei mit „consolepause“

Der folgende Befehl führt `where` aus, um Python-Dateien zu veranschaulichen, die im Projektordner starten:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Ausführen der Befehle „run server“ und „run debug server“

Für Informationen darüber, wie die Befehle **Start server** (Server starten) und **Start debug server** (Debugserver starten) für Webprojekte definiert werden, sehen Sie sich [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) auf GitHub an.

### <a name="install-package-for-development"></a>Installationspaket für die Entwicklung

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Aus [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), Verwendung mit Berechtigung.*

### <a name="generate-windows-installer"></a>Generieren des Windows Installer

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Aus [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), Verwendung mit Berechtigung.*

### <a name="generate-wheel-package"></a>Generieren des wheel-Pakets

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*Aus [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), Verwendung mit Berechtigung.*

## <a name="troubleshooting"></a>Problembehandlung

### <a name="message-the-project-file-could-not-be-loaded"></a>Meldung: „Die Projektdatei konnte nicht geladen werden.“

Gibt an, dass Ihre Projektdatei Syntaxfehler enthält. Die Meldung enthält den spezifischen Fehler mit einer Zeilennummer und Zeichenposition.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Das Konsolenfenster wird direkt nach dem Ausführen des Befehls geschlossen

Verwenden Sie `ExecuteIn="consolepause"` anstelle von `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Der Befehl wird nicht im Menü angezeigt

Prüfen Sie, ob der Befehl in der Eigenschaftengruppe `<PythonCommands>` enthalten ist, und ob der Name in der Befehlsliste dem Namen entspricht, der in dem Element `<Target>` angegeben ist.

Zum Beispiel stimmt in den folgenden Elementen der Name „Example“ in der Eigenschaftengruppe nicht mit dem Namen „ExampleCommand“ in Target überein. Visual Studio findet keinen Befehl mit dem Namen „Example“, weshalb kein Befehl erscheint. Nutzen Sie entweder „ExampleCommand“ in der Befehlsliste, oder ändern Sie den Namen von Target in „Example“.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Meldung: „Fehler beim Ausführen von \<command name>. Befehl \<target-name> konnte nicht aus dem Projekt abgerufen werden.“

Gibt an, dass der Inhalt der Elemente `<Target>` oder `<CreatePythonCommandItem>` falsch ist. Mögliche Ursachen schließen ein:

- Das benötigte Attribut `Target` ist leer.
- Das benötigte Attribut `TargetType` ist leer oder enthält einen unbekannten Wert.
- Das benötigte Attribut `ExecuteIn` ist leer oder enthält einen unbekannten Wert.
- `ErrorRegex` oder `WarningRegex` werden angegeben, ohne dass `ExecuteIn="output"` festgelegt ist.
- Unbekannte Attribute sind in dem Element vorhanden. Zum Beispiel haben Sie vielleicht `Argumnets` (falsch geschrieben) anstelle von `Arguments` verwendet.

Attributwerte können leer sein, wenn Sie auf eine nicht definierte Eigenschaft verweisen. Wenn Sie zum Beispiel das Token `$(StartupFile)` verwenden, aber keine Startdatei für das Projekt definiert haben, dann wird das Token zu einer leeren Zeichenfolge aufgelöst. In solchen Fällen sollten Sie einen Standardwert definieren. Die Befehle **Run server** (Server ausführen) und **Run debug server** (Debugserver ausführen) sind zum Beispiel in den Projektvorlagen „Bottle“, „Flask“ und „Django“ standardmäßig als *manage.py* definiert, wenn Sie keine andere Serverstartdatei in den Projekteigenschaften angegeben haben.

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Visual Studio reagiert beim Ausführen des Befehls nicht mehr und stürzt ab

Wenn Sie versuchen, einen Konsolenbefehl mit `ExecuteIn="output"` auszuführen, kann es sein, dass Visual Studio bei dem Versuch, die Ausgabe zu analysieren, abstürzt. Verwenden Sie stattdessen `ExecuteIn="console"`. (Siehe [Problem 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Der ausführbare Befehl „ist entweder falsch geschrieben oder konnte nicht gefunden werden.“

Wenn Sie `TargetType="executable"` verwenden, muss der Wert in `Target`*ausschließlich* der Programmname ohne jegliche Argumente sein, z.B. nur *Python* oder *python.exe*. Verschieben Sie alle Argumente in das Attribut `Arguments`.
