---
title: Beispiele für Befehlszeilenparameter für die Installation
description: Passen Sie diese Beispiele an, um Ihre eigene Installation von Visual Studio über die Befehlszeile zu erstellen.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 02496f230338e429b281f2b0d516cb9a06fe9e7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868529"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Beispiele für Befehlszeilenparameter für die Installation von Visual Studio

Zur Veranschaulichung, wie [Befehlszeilenparameter zur Installation von Visual Studio](use-command-line-parameters-to-install-visual-studio.md) verwendet werden, sind hier einige Beispiele aufgeführt, die sie Ihren Bedürfnissen anpassen können.

In jedem Beispiel stellen `vs_enterprise.exe`, `vs_professional.exe` und `vs_community.exe` die jeweilige Edition des Visual Studio-Bootstrappers dar, was die kleine Datei ist (ca. 1 MB), die den Downloadprozess initiiert. Wenn Sie eine andere Edition verwenden, ersetzen Sie die entsprechenden Bootstrappernamen.

> [!NOTE]
> Alle Befehle erfordern administrative Erhöhung, und ein Befehl der Benutzerkontensteuerung wird angezeigt, wenn der Prozess nicht von einer erhöhten Aufforderung gestartet wurde.
>
> [!NOTE]
> Sie können die `^`-Zeichen am Ende einer Befehlszeile zum Verketten mehrerer Zeilen in einem einzigen Befehl verwenden. Alternativ können Sie einfach diese Zeilen zusammen in einer einzelnen Zeile platzieren. Die Entsprechung in PowerShell ist das Graviszeichen (`` ` ``).

Listen der Workloads und Komponenten, die Sie über die Befehlszeile installieren können, finden Sie auf der Seite [Visual Studio-Workload und Komponenten-IDs](workload-and-component-ids.md).

## <a name="using---installpath"></a>Verwenden von „--installPath“

* Installieren Sie eine minimale Instanz von Visual Studio ohne interaktive Anweisungen, aber mit angezeigtem Status:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aktualisieren Sie mithilfe der Befehlszeile eine Visual Studio-Instanz ohne interaktive Eingabeaufforderungen, aber mit angezeigtem Status:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Beide Befehle werden empfohlen. Mit dem ersten Befehl wird der Visual Studio-Installer aktualisiert. Mit dem zweiten Befehl wird die Visual Studio-Instanz aktualisiert. Um zu verhindern, dass ein Dialogfeld zur Benutzerkontensteuerung angezeigt wird, führen Sie die Eingabeaufforderung als Administrator aus.

* Installieren Sie automatisch eine Desktopinstanz von Visual Studio mit dem französischen Sprachpaket, die nur zurückgegeben wird, wenn das Produkt aufgerufen wird.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Verwenden von „--wait“

* Verwenden Sie diesen Befehlszeilenparameter in Dateien oder Skripts, um den Anschluss des Visual Studio-Installers abzuwarten, bevor der nächste Befehl ausgeführt wird. Für Batchdateien enthält die `%ERRORLEVEL%`-Umgebungsvariable den Rückgabewert des Befehls, so wie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md) dokumentiert. Bei einigen Befehlszeilen-Hilfsprogrammen sind zusätzliche Parameter erforderlich, damit der Abschluss abgewartet und der Rückgabewert des Installers abgerufen wird. Nachfolgend sehen Sie ein Beispiel der zusätzlichen Parameter, die mit dem PowerShell-Skriptbefehl „Start-Process“ verwendet werden:

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $process = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   Write-Output $process.ExitCode 
   ```

   oder

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* Der erste Parameter „--wait“ wird vom Visual Studio-Installer und der zweite Parameter „-Wait“ von „Start-Process“ verwendet, um den Abschluss abzuwarten. Der Parameter „-PassThru“ wird von „Start-Process“ verwendet, um den Exitcode des Installers für seinen Rückgabewert zu verwenden.

## <a name="using---layout"></a>Verwenden von „--layout“

* Laden Sie den Visual Studio-Kern-Editor (die minimalste Visual Studio-Konfiguration) herunter. Schließen Sie nur das englische Sprachpaket ein:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Laden Sie die .NET-Desktop- und .NET-Web-Arbeitsauslastungen zusammen mit allen empfohlenen Komponenten und der GitHub-Erweiterung herunter. Schließen Sie nur das englische Sprachpaket ein:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Verwenden von – „all“

* Starten Sie eine interaktive Installation aller Workloads und Komponenten, die in der Visual Studio Enterprise-Edition verfügbar sind:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Verwenden von „--includeRecommended“

* Installieren Sie eine zweite, benannte Instanz von Visual Studio Professional auf einem Computer, auf dem die Visual Studio Community-Edition bereits mit der Unterstützung für die Node.js-Entwicklung enthalten ist:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Verwenden von „--remove“

::: moniker range="vs-2017"

* Entfernen Sie die Komponente des Profilerstellungstools von der Standardinstanz, die auf Visual Studio installiert ist:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Entfernen Sie die Komponente des Profilerstellungstools von der Standardinstanz, die auf Visual Studio installiert ist:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Verwenden von „--path“

::: moniker range="vs-2017"

Diese Befehlszeilenparameter sind **neu in Version 15.7**. Weitere Informationen zu Befehlszeilenparametern finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Verwenden der Pfade „install“, „cache“ und „shared“:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Ausschließliches Verwenden der Pfade „install“ und „cache“:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Ausschließliches Verwenden der Pfade „install“ und „shared“:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Ausschließliches Verwenden des „install“-Pfads:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Verwenden von „export“

::: moniker range="vs-2017"

Dieser Befehlszeilenbefehl ist **neu in 15.9**. Weitere Informationen finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Verwenden von „export“ zum Speichern der Auswahl einer Installation:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Verwenden von „export“ zum Speichern einer neu erstellten benutzerdefinierten Auswahl:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Verwenden von „--config“

::: moniker range="vs-2017"

Dieser Befehlszeilenparameter ist **neu in 15.9**. Weitere Informationen finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Verwenden von „--config“ zum Installieren der Workloads und der Komponenten aus einer kürzlich gespeicherten Installationskonfigurationsdatei:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Verwenden von „--config“ zum Hinzufügen von Workloads und Komponenten zu einer bereits vorhandenen Installation:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
