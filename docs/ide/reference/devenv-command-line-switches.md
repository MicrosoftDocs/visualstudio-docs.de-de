---
title: Devenv-Befehlszeilenschalter
description: Hier erfahren Sie mehr über die devenv-Befehlszeilenoptionen und darüber, wie Sie damit über die Befehlszeile IDE-Optionen festlegen sowie Projekte erstellen, debuggen und bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 597a3f7e9a9b36d52f55a9215891c40b18f1a9e9
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305505"
---
# <a name="devenv-command-line-switches"></a>Devenv-Befehlszeilenparameter

Mit Devenv können Sie über die Befehlszeile verschiedene Optionen für die IDE festlegen und Projekte erstellen, debuggen und bereitstellen. Verwenden Sie diese Schalter, um die IDE aus einem Skript oder einer BAT-Datei auszuführen (z.B. einem über Nacht ausgeführten Buildskript) oder um die IDE in einer bestimmten Konfiguration zu starten.

> [!NOTE]
> Für buildbezogene Tasks wird empfohlen, dass Sie MSBuild anstelle von Devenv verwenden. Weitere Informationen finden Sie unter [MSBuild-Befehlszeilenreferenz](../../msbuild/msbuild-command-line-reference.md).

Informationen zu Schaltern, die mit der VSPackage-Entwicklung in Zusammenhang stehen, finden Sie unter [Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Syntax des Devenv-Schalters

Befehle, die mit `devenv` beginnen, werden vom Hilfsprogramm `devenv.com` verarbeitet. Die Ausgabe wird über die Standardstreams des Systems (z.B. `stdout` und `stderr`) bereitgestellt. Das Hilfsprogramm bestimmt die entsprechende E/A-Umleitung, wenn es die Ausgabe beispielsweise in einer TXT-Datei erfasst.

Alternativ können Befehle, die mit `devenv.exe` beginnen, dieselben Schalter verwenden, das Hilfsprogramm `devenv.com` wird jedoch umgangen. Wenn Sie `devenv.exe` direkt verwenden, wird verhindert, dass die Ausgabe in der Konsole angezeigt wird.

Die Syntaxregeln für `devenv`-Schalter ähneln den Regeln für andere DOS-Befehlszeilenhilfsprogramme. Die folgenden Syntaxregeln gelten für alle `devenv`-Schalter und ihre Argumente:

- Befehle beginnen mit `devenv`.

- Die Groß-/Kleinschreibung wird bei Schaltern nicht beachtet.

- Sie können einen Schalter mit einem Bindestrich („-“) oder einem Schrägstrich („/“) angeben.

- Bei Angabe einer Projektmappe oder eines Projekts ist das erste Argument der Name der Projektmappendatei oder der Projektdatei, einschließlich Dateipfad.

- Wenn das erste Argument eine Datei ist, die keine Projektmappe bzw. kein Projekt ist, wird die Datei im entsprechenden Editor in einer neuen Instanz der IDE geöffnet.

- Wenn Sie anstelle des Namens einer Projektmappendatei den einer Projektdatei angeben, wird der übergeordnete Ordner der Projektdatei von einem `devenv`-Befehl nach einer Projektmappendatei mit demselben Namen durchsucht. Beispielsweise durchsucht der Befehl `devenv myproject1.vbproj /build` den übergeordneten Ordner nach einer Projektmappendatei mit dem Namen `myproject1.sln`.

  > [!NOTE]
  > In diesem übergeordneten Ordner darf genau eine Projektmappendatei enthalten sein, die auf dieses Projekt verweist. Wenn der übergeordnete Ordner keine oder zwei bzw. mehr Projektmappendateien enthält, die auf das Projekt verweisen, wird in diesem Ordner eine temporäre Projektmappendatei erstellt.

- Dateipfade und Dateinamen, die Leerzeichen enthalten, müssen in Anführungszeichen ("") eingeschlossen werden. Beispielsweise `"c:\project a\"`.

- Fügen Sie zwischen Schaltern und Argumenten auf der gleichen Zeile ein Leerzeichen ein. Der Befehl `devenv /log output.txt` öffnet z. B. die IDE und gibt alle Protokollinformationen für diese Sitzung in output.txt aus.

- In `devenv`-Befehlen kann keine Syntax zum Mustervergleich verwendet werden.

## <a name="devenv-switches"></a>Devenv-Schalter

Die folgenden Befehlszeilenschalter zeigen die IDE an und führen die beschriebene Aufgabe aus.

|Befehlszeilenschalter|Beschreibung|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Startet die IDE und führt den angegebenen Befehl aus.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Lädt eine ausführbare C++-Datei unter der Kontrolle des Debuggers. Dieser Schalter ist für ausführbare Visual Basic- oder C#-Dateien nicht verfügbar. Weitere Informationen finden Sie unter [Prozess im Debugger automatisch starten](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Vergleicht zwei Dateien. Erfordert vier Parameter: *SourceFile*, *TargetFile*, *SourceDisplayName* (optional) und *TargetDisplayName* (optional).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Öffnet die angegebene Lösung, ohne Projekte zu laden.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Öffnet die angegebenen Dateien in einer ausgeführten Instanz dieser Anwendung. Wenn keine ausgeführten Instanzen vorhanden sind, wird eine neue Instanz mit einem vereinfachten Fensterlayout gestartet.<br /><br /> `devenv /edit File1 File2`|
|[/LCID oder /L](lcid-devenv-exe.md)|Legt die Standardsprache für die IDE fest. Wenn die angegebene Sprache in der Installation von Visual Studio nicht enthalten ist, wird diese Einstellung ignoriert.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Startet Visual Studio und protokolliert sämtliche Aktivitäten in der Protokolldatei.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Öffnet die IDE ohne Anzeige der Begrüßungsbildschirms.<br /><br /> `devenv /nosplash File1 File2`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Stellt die Visual Studio-Standardeinstellungen wieder her. Setzt die Einstellungen optional auf die der angegebenen `.vssettings`-Datei zurück.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Run oder /R](run-devenv-exe.md)|Kompiliert die angegebene Projektmappe und führt sie aus.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Kompiliert die angegebene Projektmappe und führt sie aus, minimiert die IDE bei der Ausführung der Projektmappe und schließt die IDE nach beendeter Ausführung der Projektmappe.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Startet Visual Studio im abgesicherten Modus. Dieser Schalter lädt nur die Standardumgebung, die Standarddienste und die im Lieferumfang enthaltenen Versionen von Drittanbieterpaketen.<br /><br /> Der Schalter verwendet keine Argumente.|
|[/UseEnv](useenv-devenv-exe.md)|Bewirkt, dass die IDE die Umgebungsvariablen PATH, INCLUDE, LIBPATH und LIB für die C++-Kompilierung verwendet. Dieser Schalter wird mit der Workload **Desktopentwicklung mit C++** installiert. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Durch die folgenden Befehlszeilenschalter wird die IDE nicht angezeigt.

|Befehlszeilenschalter|Beschreibung|
| - |-----------------|
|[/?](q-devenv-exe.md)|Zeigt Hilfe für `devenv`-Schalter im **Eingabeaufforderungsfenster** an.<br /><br /> Der Schalter verwendet keine Argumente.|
|[/Build](build-devenv-exe.md)|Erstellt die angegebene Projektmappe oder das angegebene Projekt entsprechend der Konfiguration der angegebenen Projektmappe.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Löscht vom Buildbefehl erstellte Dateien, ohne die Quelldateien zu beeinflussen.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Erstellt die Projektmappe zusammen mit den für die Bereitstellung notwendigen Dateien gemäß der Konfiguration der Projektmappe.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Ermöglicht die Angabe einer Datei für Fehlermeldungen, wenn ein Build erstellt wird.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Das zu erstellende, bereinigende oder bereitzustellende Projekt. Dieser Schalter kann nur verwendet werden, wenn auch der Schalter `/Build`, `/Rebuild`, `/Clean`, oder `/Deploy` angegeben wurde.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Gibt die zu erstellende oder bereitzustellende Projektkonfiguration an. Dieser Schalter kann nur verwendet werden, wenn auch der Schalter `/Project` angegeben wurde.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Bereinigt die angegebene Projektmappe oder das angegebene Projekt und erstellt diese bzw. dieses entsprechend der Konfiguration der angegebenen Projektmappe durch.<br /><br /> `devenv mysln.sln /rebuild`|
|[/Upgrade](upgrade-devenv-exe.md)|Aktualisiert die angegebene Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen, für diese Dateien gültigen Visual Studio-Formaten.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](general-environment-options-dialog-box.md)
- [Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
