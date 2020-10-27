---
title: Problembehandlung und bekannte Probleme (VS-Tools für Unity)
description: Hier erfahren Sie mehr über die Problembehandlung in Visual Studio-Tools für Unity. Lesen Sie die Beschreibungen bekannter Probleme, und informieren Sie sich über deren Lösungen.
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d096a431b7a345d2218c46969dc1a1a21af1f45a
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039832"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Problembehandlung und bekannte Probleme (Visual Studio-Tools für Unity)

In diesem Abschnitt finden Sie Lösungen für häufige Probleme mit Visual Studio-Tools für Unity und Beschreibungen bekannter Probleme. Außerdem erfahren Sie, wie Sie Visual Studio-Tools für Unity verbessern können, indem Sie Fehler melden.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Problembehandlung bei der Verbindung zwischen Unity und Visual Studio

### <a name="confirm-editor-attaching-is-enabled"></a>Vergewissern Sie sich, dass „Editor Attaching“ (Editoranhängen) aktiviert ist

Wählen Sie im Menü Unity **Bearbeiten > Voreinstellungen** und dann die Registerkarte **Externe Tools** aus. Vergewissern Sie sich, dass das Kontrollkästchen **Editor Attaching** aktiviert ist. Weitere Informationen finden Sie in der [Dokumentation zu Unity-Einstellungen](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Anfügen nicht möglich.

- Versuchen Sie, Ihr Antivirenprogramm kurzzeitig zu deaktivieren, oder erstellen Sie Ausschlussregeln für Visual Studio und Unity.
- Versuchen Sie, Ihre Firewall kurzzeitig zu deaktivieren, oder erstellen Sie Regeln, um das TCP/UDP-Netzwerken zwischen Visual Studio und Unity zuzulassen.
- Einige Programme wie Team Viewer können die Prozesserkennung beeinträchtigen. Sie können versuchen, zusätzliche Software vorübergehend zu beenden, um festzustellen, ob sich dadurch etwas ändert.
- Benennen Sie die wichtigste ausführbare Komponente nicht um, da VSTU nur „Unity.exe“-Vorgänge überwacht.

## <a name="visual-studio-crashes"></a>Visual Studio stürzt ab

Dies kann daran liegen, dass der MEF-Cache für Visual Studio beschädigt ist.

Versuchen Sie, den folgenden Ordner zu entfernen, um den MEF-Cache zurückzusetzen (bitte schließen Sie vorher Visual Studio):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Dadurch sollte das Problem behoben werden. Wenn Sie immer noch auf Probleme stoßen sollten, führen Sie eine Developer-Eingabeaufforderung für Visual Studio als Administrator aus, und verwenden Sie den folgenden Befehl:

```batch
 devenv /setup
```

## <a name="visual-studio-stops-responding"></a>Visual Studio reagiert nicht mehr

Mehrere Unity-Plug-Ins wie Parse, FMOD, UMP (Universal Media Player), ZFBrowser oder Embedded Browser verwenden native Threads. Wenn ein Plug-In der Runtime einen nativen Thread hinzufügt, führt dies zu einem Problem, da die Runtime dann Blockierungsaufrufe an das Betriebssystem ausgibt. Das bedeutet, dass Unity den Thread für den Debugger (oder das Neuladen einer Domäne) nicht unterbrechen kann und nicht mehr reagiert.

Für FMOD gibt es eine Möglichkeit zur Problemumgehung: Sie können das Initialisierungs-[Flag](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags)`FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` weitergeben, um die asynchrone Verarbeitung zu deaktivieren und die gesamte Verarbeitung auf dem Hauptthread durchzuführen.

## <a name="incompatible-project-in-visual-studio"></a>Nicht kompatibles Projekt in Visual Studio

Überprüfen Sie zunächst, ob Visual Studio als externer Skript-Editor in Unity festgelegt ist (Bearbeiten > Einstellungen > Externe Tools). Überprüfen Sie anschließend, dass das Visual Studio-Plug-In in Unity installiert ist (die Felder „Hilfe“ bzw. „Info“ müssen in der Ansicht im unteren Bereich eine Nachricht wie „Microsoft Visual Studio Tools für Unity ist aktiviert“ anzeigen). Überprüfen Sie dann, ob die Erweiterung korrekt in Visual Studio installiert wurde (Hilfe bzw. Info).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Zusätzliches Neuladen oder Visual Studio verliert alle geöffneten Fenster

Stellen Sie sicher, dass Sie Projektdateien nie direkt über Asset Processor oder ein anderes Tool direkt bearbeiten. Wenn Sie die Projektdatei wirklich bearbeiten müssen, verwenden Sie die hierfür verfügbare API. Lesen Sie den Abschnitt zu [Problemen mit Assemblyverweisen](#assembly-reference-issues).

Wenn zusätzliches Neuladen auftritt oder Visual Studio alle geöffneten Fenster beim Neuladen verliert, stellen Sie sicher, dass die richtigen .NET-Pakete zur Festlegung von Zielversionen installiert sind. Weitere Informationen zu Frameworks finden Sie in folgendem Abschnitt.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Der Debugger wird bei Ausnahmen nicht unterbrochen

Wenn Sie die veraltete Unity-Runtime (entspricht .NET 3.5) verwenden, wird der Debugger immer dann unterbrochen, wenn eine Ausnahme nicht behandelt wurde (d.h. außerhalb eines try/catch-Blocks). Wenn eine Ausnahme behandelt wird, verwendet der Debugger das Fenster „Ausnahmeeinstellungen“, um zu bestimmen, ob eine Unterbrechung erforderlich ist.

Mit der neuen Runtime (entspricht .NET 4.6) wurde in Unity eine neue Möglichkeit zum Verwalten von Benutzerausnahmen eingeführt. Dadurch werden alle Ausnahmen als „Vom Benutzer behandelt“ betrachtet, auch wenn diese außerhalb eines try/catch-Blocks auftreten. Deshalb sollten Sie diese explizit im Fenster „Ausnahmeeinstellungen“ überprüfen, wenn Sie möchten, dass der Debugger unterbrochen wird.

Erweitern Sie im Fenster „Ausnahmeeinstellungen“ (Debuggen > Fenster > Ausnahmeeinstellungen) den Knoten für eine Ausnahmekategorie (z.B. Common Language Runtime-Ausnahmen, also .NET-Ausnahmen), und aktivieren Sie das Kontrollkästchen für die Ausnahme, die Sie innerhalb dieser Kategorie abfangen möchten (z.B. „System.NullReferenceException“). Sie können auch eine ganze Kategorie von Ausnahmen auswählen.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Unter Windows fordert Visual Studio das Herunterladen des Unity-Zielframeworks an.

Visual Studio-Tools für Unity erfordert .NET Framework 3.5, das nicht standardmäßig unter Windows 8 oder 10 installiert ist. Befolgen Sie die Anweisungen zum Herunterladen und Installieren von .NET Framework 3.5, um dieses Problem zu beheben.

Wenn Sie die neue Unity-Runtime verwenden, sind ebenfalls die Pakete zur Festlegung der Zielversion für Version 4.6 und 4.7.1 von .NET erforderlich. Es ist möglich, diese im Installer von Visual Studio 2017 schnell zu installieren. Wählen Sie hierzu eine benutzerdefinierte Installation von Visual Studio 2017 aus, klicken Sie auf „Einzelne Komponenten“, und wählen Sie in der Kategorie „.NET“ alle Pakete zur Festlegung der Zielversion mit 4.x aus.

## <a name="assembly-reference-issues"></a>Probleme mit dem Assemblyverweis

Wenn Ihr Projekt im Hinblick auf Verweise komplex ist, oder wenn Sie diesen Generationsschritt besser steuern möchten, können Sie unsere [API](../cross-platform/customize-project-files-created-by-vstu.md) verwenden, um das generierte Projekt oder den Projektmappeninhalt zu bearbeiten. Sie können auch [Antwortdateien](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) in Ihrem Unity-Projekt verwenden, die dann verarbeitet werden.

## <a name="breakpoints-with-a-warning"></a>Haltepunkte mit einer Warnung

Wenn Visual Studio keinen Quellspeicherort für einen bestimmten Haltepunkt finden kann, wird Ihnen eine Warnung um Ihren Haltepunkt angezeigt. Überprüfen Sie, ob das von Ihnen verwendete Skript in der Unity-Szene korrekt geladen bzw. verwendet wird.

## <a name="breakpoints-not-hit"></a>Haltepunkte werden nicht erreicht.

Überprüfen Sie, ob das von Ihnen verwendete Skript in der Unity-Szene korrekt geladen bzw. verwendet wird. Beenden Sie Visual Studio und Unity, und löschen Sie anschließend alle generierten Dateien (\*.csproj, \*.sln) sowie den gesamten Bibliotheksordner.

## <a name="unable-to-debug-android-players"></a>Debuggen von Android Players nicht möglich

Multicast wird für die Erkennung von Players (der von Unity verwendete Standardmechanismus) verwendet. Anschließend wird allerdings eine gewöhnliche TCP-Verbindung verwendet, um den Debugger anzufügen. Die Erkennungsphase stellt für Android-Geräte das größte Problem dar.

WLAN ist zwar vielseitig, aber aufgrund der Wartezeit extrem langsam im Vergleich zu USB. Es wurde mangelnde Unterstützung für einige Router oder Geräte festgestellt (die Nexus-Serien sind dafür besonders bekannt).

USB ist für ein schnelles Debuggen geeignet, und Visual Studio-Tools für Unity kann nun USB-Geräte erkennen und mit dem Adb-Server kommunizieren, um die Ports für das Debuggen ordnungsgemäß weiterzuleiten.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Probleme mit Visual Studio 2015 und IntelliSense oder der Codeeinfärbung

Versuchen Sie, Ihre Version von Visual Studio 2015 auf Update 3 zu aktualisieren.

## <a name="known-issues"></a>Bekannte Probleme

 Es gibt bekannte Probleme in Visual Studio-Tools für Unity, deren Ursache die Interaktion des Debuggers mit der älteren Version von Unity des C#-Compilers ist. Wir arbeiten daran, diese Fehler zu beheben, aber in der Zwischenzeit können die folgenden Probleme weiterhin auftreten:

- Beim Debuggen stürzt Unity manchmal ab.

- Beim Debuggen friert Unity manchmal ein.

- Bei Einzel- und Prozedurschritten für Methoden kommt es mitunter zu einem Fehlverhalten, insbesondere bei Iteratoren oder innerhalb von Switch-Anweisungen.

## <a name="report-errors"></a>Importfehler

 Helfen Sie uns, die Qualität von Visual Studio-Tools für Unity zu verbessern, indem Sie Fehlerberichte senden, sollte das Programm abstürzen, einfrieren oder ein anderer Fehler auftreten. Dies hilft uns beim Untersuchen und Beheben von Problemen in Visual Studio-Tools für Unity. Vielen Dank!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Wie Sie einen Fehler melden, wenn Visual Studio einfriert

 Uns wurde gemeldet, dass Visual Studio beim Debuggen mit Visual Studio-Tools für Unity mitunter einfriert, aber wir benötigen mehr Daten, um dieses Problem zu verstehen. Sie können uns bei der Untersuchung helfen, indem Sie die folgenden Schritte ausführen.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>So melden Sie, dass Visual Studio beim Debuggen mit Visual Studio-Tools für Unity einfriert

*Unter Windows:*

1. Öffnen Sie eine Instanz von Visual Studio.

1. Öffnen Sie das Dialogfeld "An den Prozess anhängen". Wählen Sie in der neuen Instanz von Visual Studio im Hauptmenü **Debuggen** , **An den Prozess anhängen** .

1. Hängen Sie den Debugger an die eingefrorene Instanz von Visual Studio an. Wählen Sie im Dialogfeld **An den Prozess anhängen** die eingefrorene Instanz von Visual Studio in der Tabelle **Verfügbare Prozesse** aus, und klicken Sie dann auf die Schaltfläche **Anhängen** .

1. Halten Sie den Debugger an. Klicken Sie in der neuen Instanz von Visual Studio im Hauptmenü auf **Debuggen** , **Alle unterbrechen** , oder drücken Sie **STRG+ALT+UNTRBR** .

1. Erstellen Sie einen Thread-Dump. Geben Sie im Befehlsfenster den folgenden Befehl ein, und drücken Sie die **EINGABETASTE** :

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Möglicherweise müssen Sie zuerst das Fenster **Befehl** einblenden. Wählen Sie in Visual Studio im Hauptmenü **Ansicht** , **Weitere Fenster** , **Befehlsfenster** .

*Unter Mac:*

1. Öffnen Sie ein Terminal, und rufen Sie die PID von Visual Studio für Mac ab:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Starten Sie den LLDB-Debugger:

    ```shell
    lldb
    ```

1. Führen Sie eine Anfügung an die Visual Studio für Mac-Instanz durch:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Rufen Sie StackTrace für alle Threads ab:

    ```shell
    bt all
    ```

Senden Sie zum Schluss den Thread-Dump an [vstusp@microsoft.com](mailto:vstusp@microsoft.com)zusammen mit einer Beschreibung, was Sie gerade getan haben, als Visual Studio eingefroren ist.

## <a name="see-also"></a>Siehe auch

- [Problembehandlung für Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
