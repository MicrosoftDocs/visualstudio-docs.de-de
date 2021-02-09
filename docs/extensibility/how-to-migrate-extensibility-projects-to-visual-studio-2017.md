---
title: Migrieren von Erweiterungsprojekten zu Visual Studio 2017
titleSuffix: ''
description: Erfahren Sie, wie Sie ein Upgrade von Erweiterungs Projekten auf Visual Studio 2017 durchführen und wie Sie ein Upgrade von Erweiterungs Manifest Version 2 auf das VSIX-Manifest der Version 3 durchführen.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 39efb082f8a551ea016e856ba45c9dbb4e8eed0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850699"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Vorgehensweise: Migrieren von Erweiterungs Projekten zu Visual Studio 2017

In diesem Dokument wird erläutert, wie Erweiterbarkeits Projekte auf Visual Studio 2017 aktualisiert werden. Außerdem wird beschrieben, wie Sie die Projektdateien aktualisieren. Außerdem wird beschrieben, wie Sie ein Upgrade von der Erweiterung Manifest Version 2 (VSIX v2) auf das neue VSIX-Manifest-Format (VSIX v3) der Version 3 durchführen.

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installieren von Visual Studio 2017 mit erforderlichen Workloads

Stellen Sie sicher, dass die Installation die folgenden Arbeits Auslastungen umfasst:

* .NET-Desktopentwicklung
* Entwicklung von Visual Studio-Erweiterungen

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Öffnen der VSIX-Projekt Mappe in Visual Studio 2017

Alle VSIX-Projekte erfordern ein unidirektionales Upgrade der Hauptversion auf Visual Studio 2017.

Die Projektdatei (z *. b. *. csproj*) wird aktualisiert:

* Minimumvisualstudioversion: ist jetzt auf 15,0 festgelegt.
* Oldtoolsversion (falls bereits vorhanden): jetzt auf 14,0 festgelegt

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualisieren Sie das nuget-Paket Microsoft. VSSDK. Buildtools.

> [!Note]
> Wenn Ihre Lösung nicht auf das nuget-Paket Microsoft. VSSDK. Buildtools verweist, können Sie diesen Schritt überspringen.

Um die Erweiterung im neuen VSIX v3-Format (Version 3) zu erstellen, muss Ihre Lösung mit den neuen VSSDK-Buildtools erstellt werden. Dies wird mit Visual Studio 2017 installiert, aber die VSIX v2-Erweiterung enthält möglicherweise einen Verweis auf eine ältere Version über nuget. Wenn dies der Fall ist, müssen Sie manuell ein Update für das nuget-Paket Microsoft. VSSDK. Buildtools für die Lösung installieren.

So aktualisieren Sie die nuget-Verweise auf Microsoft. VSSDK. Buildtools:

* Klicken Sie mit der rechten Maustaste auf die Lösung, und wählen Sie **nuget-Pakete für** Projekt Mappe verwalten.
* Navigieren Sie zur Registerkarte **Updates** .
* Wählen Sie **Microsoft. VSSDK. Buildtools (neueste Version)** aus.
* Klicken Sie auf **Aktualisieren**.

![VSSDK-Buildtools](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Ändern des VSIX-Erweiterungs Manifests

Um sicherzustellen, dass die Installation von Visual Studio für den Benutzer alle Assemblys enthält, die zum Ausführen der Erweiterung erforderlich sind, geben Sie alle erforderlichen Komponenten oder Pakete in der Erweiterungs Manifest-Datei an. Wenn ein Benutzer versucht, die Erweiterung zu installieren, prüft vsixinstaller, ob alle erforderlichen Komponenten installiert sind. Wenn einige fehlen, wird der Benutzer zur Installation der fehlenden Komponenten im Rahmen der Erweiterungs Installation aufgefordert.

> [!Note]
> Alle Erweiterungen sollten mindestens die Komponente "Visual Studio-Kern-Editor" als Voraussetzung angeben.

* Bearbeiten Sie die Datei mit dem Erweiterungs Manifest (in der Regel " *Source. Extension. vsixmanifest*" genannt).
* Stellen Sie sicher, dass `InstallationTarget` 15,0.
* Fügen Sie erforderliche Installations Voraussetzungen hinzu (wie im folgenden Beispiel gezeigt).
  * Es wird empfohlen, nur Komponenten-IDs für die Installations Voraussetzungen anzugeben.
  * Weitere [Informationen zum Identifizieren von Komponenten-IDs](#find-component-ids)finden Sie im Abschnitt am Ende dieses Dokuments.

Beispiel:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option: Verwenden des Designers zum Ändern des VSIX-Erweiterungs Manifests

Anstatt das Manifest-XML direkt zu bearbeiten, können Sie **die Registerkarte** neue erforderliche Komponenten im Manifest-Designer verwenden, um die erforderlichen Komponenten auszuwählen, und die XML-Datei wird für Sie aktualisiert.

> [!Note]
> Der Manifest-Designer ermöglicht nur das Auswählen von Komponenten (nicht von Arbeits Auslastungen oder Paketen), die auf der aktuellen Visual Studio-Instanz installiert sind. Wenn Sie eine erforderliche Komponente für eine Arbeitsauslastung, ein Paket oder eine Komponente hinzufügen müssen, die derzeit nicht installiert ist, bearbeiten Sie die XML-Datei des Manifests direkt.

* Öffnen Sie die Datei " *Source. Extension. vsixmanifest [Design]* ".
* Wählen **Sie** die Registerkarte erforderliche Komponenten aus, **und drücken Sie**

   ![VSIX-Manifest-Designer](media/vsix-manifest-designer.png)

* Das Fenster " **neue Voraussetzung hinzufügen** " wird geöffnet.

   ![VSIX-Voraussetzung hinzufügen](media/add-vsix-prerequisite.png)

* Klicken Sie auf die Dropdown Liste **Name** , und wählen Sie die gewünschte Voraussetzung aus.
* Aktualisieren Sie die Version bei Bedarf.

   > [!Note]
   > Das Feld Version wird mit der Version der derzeit installierten Komponente vorab aufgefüllt, wobei sich der Bereich bis zu der nächsten Hauptversion der Komponente erstreckt (aber nicht einschließlich des Bereichs).

   ![Roslyn-Voraussetzung hinzufügen](media/add-roslyn-prerequisite.png)

* Klicken Sie auf **OK**.

## <a name="update-debug-settings-for-the-project"></a>Debugeinstellungen für das Projekt aktualisieren

Wenn Sie die Erweiterung in einer experimentellen Instanz von Visual Studio debuggen möchten, müssen Sie sicherstellen, dass für die Projekteinstellungen für die Aktion " **Debugstart**"  >   der Wert " **externen Programm starten** " auf die *devenv.exe* Datei Ihrer Visual Studio 2017-Installation festgelegt ist.

Dies könnte wie folgt aussehen: *c:\Programme (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![externes Programm starten](media/start-external-program.png)

> [!Note]
> Die Aktion zum Starten des Debuggens wird in der Regel in der *csproj. User* -Datei gespeichert. Diese Datei ist normalerweise in der *gitignore* -Datei enthalten und wird daher normalerweise nicht mit anderen Projektdateien gespeichert, wenn ein Commit in die Quell Code Verwaltung erfolgt. Wenn Sie Ihre Projekt Mappe aus der Quell Code Verwaltung herausgezogen haben, ist es wahrscheinlich, dass für das Projekt keine Werte für die Start Aktion festgelegt sind. Neue VSIX-Projekte, die mit Visual Studio 2017 erstellt wurden, verfügen über die Datei " *. csproj. User* ", die standardmäßig auf das aktuelle Visual Studio-Installationsverzeichnis verweist. Wenn Sie jedoch eine VSIX v2-Erweiterung migrieren, ist es wahrscheinlich, dass die Datei " *. csproj. User* " Verweise auf das Installationsverzeichnis der früheren Version von Visual Studio enthält. Durch Festlegen des Werts für die Aktion "Start **Debuggen**"  >   kann die richtige Visual Studio-Instanz gestartet werden, wenn Sie versuchen, die Erweiterung zu debuggen.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Überprüfen Sie, ob die Erweiterung ordnungsgemäß erstellt wird (als VSIX v3).

* Erstellen Sie das VSIX-Projekt.
* Entzippen Sie die generierte VSIX.
  * Standardmäßig befindet sich die vsix-Datei in *bin/debug* oder *bin/Release* als *[yourcustomextension]. vsix*.
  * Benennen Sie *VSIX* in *. zip* um, um die Inhalte leicht anzuzeigen.
* Überprüfen Sie, ob drei Dateien vorhanden sind:
  * *Erweiterung. vsixmanifest*
  * *manifest.js*
  * *catalog.js*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Überprüfen Sie, ob alle erforderlichen Komponenten installiert sind.

Testen Sie, ob die VSIX erfolgreich auf einem Computer installiert ist, auf dem alle erforderlichen Komponenten installiert sind.

> [!Note]
> Schließen Sie alle Instanzen von Visual Studio ab, bevor Sie eine Erweiterung installieren.

Versuchen Sie, die Erweiterung zu installieren:

* In Visual Studio 2017

![VSIX-Installer auf Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Optional: Überprüfen Sie die vorherigen Versionen von Visual Studio.
  * Bestätigt die Abwärtskompatibilität.
  * Sollte für Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 funktionieren.
* Optional: Überprüfen Sie, ob der VSIX-Installer Version Checker eine Auswahl von Versionen bietet.
  * Enthält frühere Versionen von Visual Studio (sofern installiert).
  * Umfasst Visual Studio 2017.

Wenn Visual Studio vor kurzem geöffnet wurde, wird möglicherweise ein Dialogfeld wie das folgende angezeigt:

![vs, die Prozesse ausführen](media/vs-running-processes.png)

Warten Sie, bis die Prozesse heruntergefahren sind, oder beenden Sie die Tasks manuell. Sie finden die Prozesse nach dem aufgelisteten Namen oder mit der in Klammern aufgeführten PID.

> [!Note]
> Diese Prozesse werden nicht automatisch heruntergefahren, während eine Instanz von Visual Studio ausgeführt wird. Stellen Sie sicher, dass Sie alle Instanzen von Visual Studio auf dem Computer heruntergefahren haben, einschließlich der von anderen Benutzern, und wiederholen Sie dann den Vorgang.

## <a name="check-when-missing-the-required-prerequisites"></a>Überprüfen, ob die erforderlichen Voraussetzungen erfüllt sind

* Versuchen Sie, die Erweiterung auf einem Computer mit Visual Studio 2017 zu installieren, der nicht alle Komponenten enthält, die in den Voraussetzungen (oben) definiert sind.
* Überprüfen Sie, ob die Installation der fehlenden Komponenten durch die Installation identifiziert wird, und listet Sie diese als erforderliche Komponente im vsixinstaller auf.
* Hinweis: Es ist eine Erhöhung der Rechte erforderlich, wenn alle Voraussetzungen mit der Erweiterung installiert werden müssen.

![VSIX fehlt Voraussetzung](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Entscheidung für Komponenten

Beim Suchen ihrer Abhängigkeiten werden Sie feststellen, dass eine Abhängigkeit mehreren Komponenten zugeordnet werden kann. Um zu ermitteln, welche Abhängigkeiten Sie als Voraussetzung angeben sollten, empfiehlt es sich, eine Komponente auszuwählen, die eine ähnliche Funktionalität wie Ihre Erweiterung aufweist. Außerdem sollten Sie Ihre Benutzer berücksichtigen und die Art der Komponenten, die Sie am wahrscheinlichsten installiert haben, oder die Installation nicht hätten. Wir empfehlen auch, Ihre Erweiterungen auf eine Weise zu entwickeln, in der die erforderlichen Voraussetzungen nur dem minimal entsprechen, mit dem Ihre Erweiterung ausgeführt werden kann. wenn bestimmte Komponenten nicht erkannt werden, sind Sie für zusätzliche Features inaktiv.

Um weitere Anleitungen bereitzustellen, haben wir einige allgemeine Erweiterungs Typen und ihre vorgeschlagenen Voraussetzungen identifiziert:

Erweiterungstyp | Anzeigename | id
--- | --- | ---
Editor | Visual Studio-Kern-Editor | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# und Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Core für Arbeitsauslastung verwalteter Desktops | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Just-In-Time-Debugger | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Komponenten-IDs suchen

Die Liste der von Visual Studio-Produkten sortierten Komponenten finden Sie unter [Visual Studio 2017-Arbeitsauslastung und Komponenten-IDs](../install/workload-and-component-ids.md?view=vs-2019&preserve-view=true). Verwenden Sie diese Komponenten-IDs für die erforderlichen IDs im Manifest.

Wenn Sie nicht sicher sind, welche Komponente eine bestimmte Binärdatei enthält, laden Sie das Arbeitsblatt für die [Binär Zuordnung von Komponenten >](https://aka.ms/vs2017componentid-binaries)herunter.

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Die Excel-Tabelle enthält vier Spalten: **Komponenten Name**, **ComponentID**, **Version** und **Binär-/Dateinamen**.  Mit den Filtern können Sie bestimmte Komponenten und Binärdateien suchen und suchen.

Legen Sie für alle Verweise zunächst fest, welche in der Kern-Editor-Komponente (Microsoft. VisualStudio. Component. coreeditor) enthalten sind.  Es ist mindestens erforderlich, dass die Kern-Editor-Komponente als Voraussetzung für alle Erweiterungen angegeben wird. Fügen Sie für die Links, die nicht im Kern-Editor enthalten sind, Filter im Abschnitt " **Binärdateien/Dateinamen** " hinzu, um Komponenten zu suchen, die über eine der Teilmengen dieser Verweise verfügen.

Beispiele:

* Wenn Sie über eine Debugger-Erweiterung verfügen und wissen, dass das Projekt über einen Verweis auf *VSDebugEng.dll* und *VSDebug.dll* verfügt, klicken Sie auf die Schaltfläche Filter im Header **Binärdateien/Dateinamen** .  Suchen Sie nach "VSDebugEng.dll", und wählen Sie *OK* aus.  Klicken Sie dann erneut auf die Filter Schaltfläche im Header **Binärdateien/Dateinamen** , und suchen Sie nach "VSDebug.dll".  Aktivieren Sie das Kontrollkästchen **aktuelle Auswahl zum Filtern hinzufügen,** und wählen Sie **OK** aus.  Sehen Sie sich nun den **Komponentennamen** an, um eine Komponente zu finden, die sich am meisten auf Ihren Erweiterungstyp bezieht. In diesem Beispiel würden Sie den Just-in-Time-Debugger auswählen und ihn Ihrem vsixmanifest hinzufügen.
* Wenn Sie wissen, dass das Projekt debuggerelemente behandelt, können Sie im Filter Suchfeld nach "Debugger" suchen, um zu sehen, welche Komponenten Debugger in seinem Namen enthalten.

## <a name="specify-a-visual-studio-2017-release"></a>Visual Studio 2017-Release angeben

Wenn Ihre Erweiterung eine bestimmte Version von Visual Studio 2017 erfordert, z. b. von einer Funktion, die in 15,3 veröffentlicht wurde, müssen Sie die Buildnummer in Ihrem VSIX- **installationtarget** angeben. Release 15,3 hat z. b. die Buildnummer "15.0.26730.3". [Hier](../install/visual-studio-build-numbers-and-release-dates.md)können Sie die Zuordnung von Releases zu Buildnummern sehen. Die Verwendung der Releasenummer "15,3" funktioniert nicht ordnungsgemäß.

Wenn Ihre Erweiterung 15,3 oder höher erfordert, deklarieren Sie die **installationtarget-Version** als [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```