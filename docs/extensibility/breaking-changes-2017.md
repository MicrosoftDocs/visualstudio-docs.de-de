---
title: Wichtige Änderungen in Visual Studio 2017-Erweiterbarkeit
description: Erfahren Sie mehr über technische Details zu wichtigen Änderungen, die an dem Erweiterbarkeits Modell in Visual Studio 2017 vorgenommen wurden, und wie Sie Sie beheben können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3121189b1d73543d2a01bbf0b149c6a98eab6909
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973752"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Änderungen in Visual Studio 2017-Erweiterbarkeit

Visual Studio 2017 bietet eine [schnellere Visual Studio-Installations](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) Darstellung, die die Auswirkungen von Visual Studio auf Benutzer Systeme verringert und gleichzeitig den Benutzern mehr Möglichkeiten für die installierten Workloads und Features bietet. Zur Unterstützung dieser Verbesserungen haben wir Änderungen am Erweiterbarkeits Modell vorgenommen, einschließlich einiger grundlegende Änderungen. In diesem Artikel werden die technischen Details dieser Änderungen und deren Behandlung beschrieben.

> [!NOTE]
> Einige Informationen sind Zeit Punkt Implementierungsdetails und können später geändert werden.

## <a name="changes-affecting-vsix-format-and-installation"></a>Änderungen, die das VSIX-Format und die Installation beeinträchtigen

Visual Studio 2017 hat das VSIX v3-Format (Version 3) zur Unterstützung der Lightweight-Installation eingeführt.

Änderungen am VSIX-Format umfassen Folgendes:

* Deklaration der Setup Voraussetzungen. Um die Zusage einer vereinfachten, schnellen Installation von Visual Studio zu gewährleisten, bietet das Installationsprogramm jetzt mehr Konfigurationsoptionen für Benutzer. Daher müssen Erweiterungen ihre Abhängigkeiten deklarieren, um sicherzustellen, dass die für eine Erweiterung benötigten Features und Komponenten installiert sind.

  * Das Visual Studio 2017-Installationsprogramm bietet automatisch die erforderlichen Komponenten für den Benutzer als Teil der Installation der Erweiterung.
  * Benutzer werden ebenfalls gewarnt, wenn Sie versuchen, eine Erweiterung zu installieren, die nicht mit dem neuen VSIX v3-Format erstellt wurde, auch wenn Sie in ihrem Manifest als Zielversion 15,0 gekennzeichnet wurden.

* Erweiterte Funktionen für das VSIX-Format. Zur Bereitstellung einer Installation von Visual Studio mit [geringen Auswirkungen](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) , die auch parallele Installationen unterstützt, werden die meisten Konfigurationsdaten nicht mehr in der Systemregistrierung gespeichert, und die Visual Studio-spezifischen Assemblys wurden aus dem GAC verschoben. Wir haben auch die Funktionen des VSIX-Formats und der VSIX-Installations-Engine erweitert, sodass Sie es anstelle einer MSI-oder exe-Datei verwenden können, um die Erweiterungen für einige Installationstypen zu installieren.

Zu den neuen Funktionen gehören:

* Registrierung bei der angegebenen Visual Studio-Instanz.
* Installation außerhalb des [Ordners "Erweiterungen](set-install-root.md)".
* Erkennen der Prozessorarchitektur.
* Abhängigkeit von sprach getrennten Sprachpaketen.
* Installation mit [ngen-Unterstützung](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Erstellen einer Erweiterung für Visual Studio 2017

Designer Werkzeuge zum Erstellen des neuen VSIX V3-Manifest-Formats sind in Visual Studio 2017 verfügbar. Ausführliche Informationen zur Verwendung der Designer Tools oder zum Erstellen manueller Updates für das Projekt und das Manifest für die Entwicklung von VSIX V3-Erweiterungen finden Sie im Begleitdokument Gewusst [wie: Migrieren von Erweiterungs Projekten zu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

## <a name="change-visual-studio-user-data-path"></a>Änderung: Visual Studio-Benutzerdaten Pfad

Bisher konnte auf jedem Computer nur eine Installation der einzelnen Hauptversionen von Visual Studio vorhanden sein. Zur Unterstützung paralleler Installationen von Visual Studio 2017 sind möglicherweise mehrere Benutzerdaten Pfade für Visual Studio auf dem Computer des Benutzers vorhanden.

Code, der innerhalb des Visual Studio-Prozesses ausgeführt wird, sollte aktualisiert werden, damit der Visual Studio-Einstellungs-Manager verwendet Code, der außerhalb des Visual Studio-Prozesses ausgeführt wird, kann den Benutzer Pfad einer bestimmten Visual Studio-Installation ermitteln, [indem Sie die Anleitungen hier befolgen](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Änderung: globaler Assemblycache (GAC)

Die meisten Visual Studio-Kernassemblys werden nicht mehr im GAC installiert. Die folgenden Änderungen wurden vorgenommen, damit Code, der in Visual Studio ausgeführt wird, weiterhin erforderliche Assemblys zur Laufzeit finden kann.

> [!NOTE]
> [INSTALLDIR] unten bezieht sich auf das Installations Stammverzeichnis von Visual Studio. Diese wird von *VSIXInstaller.exe* automatisch aufgefüllt, aber um benutzerdefinierten Bereitstellungs Code zu schreiben, lesen Sie suchen von [Visual Studio](locating-visual-studio.md).

* Assemblys, die nur im GAC installiert wurden:

  Diese Assemblys sind nun unter <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \common7\ide\publicassemblies</em> oder *[INSTALLDIR] \common7\ide\privateassemblys* installiert. Diese Ordner sind Teil der Überprüfungs Pfade des Visual Studio-Prozesses.

* Assemblys, die in einen nicht zu testende Pfad und in den GAC installiert wurden:

  * Die Kopie im GAC wurde aus dem Setup entfernt.
  * Eine *pkgdef* -Datei wurde hinzugefügt, um einen Code Basiseintrag für die Assembly anzugeben.

    Beispiel:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Zur Laufzeit führt das Visual Studio pkgdef-Subsystem diese Einträge in der Lauf Zeit Konfigurationsdatei des Visual Studio-Prozesses (unter *[vsappdata] \devenv.exe.config*) als [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) Elemente zusammen. Dies ist die empfohlene Vorgehensweise, damit der Visual Studio-Prozess Ihre Assembly finden kann, da Sie das Durchsuchen von Suchpfaden vermeidet.

### <a name="reacting-to-this-breaking-change"></a>Reaktion auf dieses Breaking Change

* Wenn die Erweiterung innerhalb des Visual Studio-Prozesses ausgeführt wird:

  * Der Code wird in der Lage sein, Visual Studio-Kernassemblys zu finden.
  * Verwenden Sie ggf. eine *pkgdef* -Datei, um einen Pfad zu den Assemblys anzugeben.

* Wenn Ihre Erweiterung außerhalb des Visual Studio-Prozesses ausgeführt wird:

  Sie sollten Visual Studio-Kernassemblys unter <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \common7\ide\publicassemblies</em> oder *[INSTALLDIR] \common7\ide\privateassemblys* mithilfe der Konfigurationsdatei oder des Assemblyresolvers suchen.

## <a name="change-reduce-registry-impact"></a>Änderung: Verringerung der Auswirkung auf die Registrierung

### <a name="global-com-registration"></a>Globale com-Registrierung

* Zuvor hat Visual Studio viele Registrierungsschlüssel im HKEY_CLASSES_ROOT und HKEY_LOCAL_MACHINE Strukturen installiert, um die Native COM-Registrierung zu unterstützen. Um diese Auswirkung auszuschließen, verwendet Visual Studio jetzt die [Registrierungs freie Aktivierung für COM-Komponenten](/previous-versions/dotnet/articles/ms973913(v=msdn.10)).
* Folglich werden die meisten TLB/OLB/dll-Dateien unter% Program Files (x86)% \ Common Files\Microsoft shared\msenv nicht mehr standardmäßig von Visual Studio installiert. Diese Dateien werden jetzt unter [INSTALLDIR] mit den entsprechenden Registration-Free com-Manifesten installiert, die vom Visual Studio-Host Prozess verwendet werden.
* Folglich findet externer Code, der auf der globalen com-Registrierung für Visual Studio-com-Schnittstellen basiert, diese Registrierungen nicht mehr. Im Code, der in Visual Studio ausgeführt wird, wird kein Unterschied angezeigt.

### <a name="visual-studio-registry"></a>Visual Studio-Registrierung

* Zuvor hat Visual Studio viele Registrierungsschlüssel im System **HKEY_LOCAL_MACHINE** und **HKEY_CURRENT_USER** Strukturen unter einem Visual Studio-spezifischen Schlüssel installiert:

  * **Hklm\software\microsoft\visualstudio \{ Version}**: Registrierungsschlüssel, die von MSI-Installationsprogrammen und Erweiterungen pro Computer erstellt werden.
  * **Hkcu\software\microsoft\visualstudio \{ Version}**: Registrierungsschlüssel, die von Visual Studio erstellt wurden, um benutzerspezifische Einstellungen zu speichern.
  * **Hkcu\software\microsoft\visualstudio \{ Version} _Config**: eine Kopie des obigen Visual Studio-HKLM-Schlüssels sowie die Registrierungsschlüssel, die von *pkgdef* -Dateien durch Erweiterungen zusammengeführt werden.

* Um die Auswirkungen auf die Registrierung zu reduzieren, verwendet Visual Studio jetzt die [regloadappkey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) -Funktion, um Registrierungsschlüssel in einer privaten Binärdatei unter *[vsappdata] \privateregistry.bin* zu speichern. In der Systemregistrierung verbleiben nur eine sehr geringe Anzahl von Visual Studio-spezifischen Schlüsseln.
* Vorhandener Code, der innerhalb des Visual Studio-Prozesses ausgeführt wird, ist nicht betroffen. Visual Studio leitet alle Registrierungs Vorgänge unter dem Visual Studio-spezifischen HKCU-Schlüssel in die private Registrierung um. Beim Lesen und Schreiben in andere Registrierungs Speicherorte wird die Systemregistrierung weiterhin verwendet.
* Für Visual Studio-Registrierungseinträge muss externer Code geladen und aus dieser Datei gelesen werden.

### <a name="react-to-this-breaking-change"></a>Auf diese Breaking Change reagieren

* Externer Code sollte konvertiert werden, um auch Registration-Free Aktivierung für COM-Komponenten zu verwenden.
* Externe Komponenten finden den Visual Studio-Speicherort, [indem Sie die Anleitungen hier befolgen](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Es wird empfohlen, dass externe Komponenten den [externen Einstellungs-Manager](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) verwenden, anstatt direkt in Visual Studio-Registrierungsschlüssel zu lesen/schreiben.
* Überprüfen Sie, ob die von ihrer Erweiterung verwendeten Komponenten möglicherweise eine andere Methode für die Registrierung implementiert haben. Debugger-Erweiterungen können z. b. die neue [msvsmon JSON-Datei-com-Registrierung](migrate-debugger-COM-registration.md)nutzen.