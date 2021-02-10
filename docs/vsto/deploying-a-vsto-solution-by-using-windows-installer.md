---
title: Bereitstellen einer VSTO-Lösung mithilfe von Windows Installer
description: Erfahren Sie, wie Sie ein Microsoft Visual Studio Tools für Office-Add-in (VSTO) oder eine Lösung auf Dokument Ebene mithilfe eines Visual Studio-Installer Projekts bereitstellen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75c2d97e8cd30bb3cf5605d50e65a68513590647
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939369"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Bereitstellen einer VSTO-Lösung mithilfe von Windows Installer

## <a name="summary"></a>Zusammenfassung

Erfahren Sie, wie Sie ein Microsoft Visual Studio Tools für Office-Add-in (VSTO) oder eine Lösung auf Dokument Ebene mithilfe eines Visual Studio-Installer Projekts bereitstellen.

Wouter van Vugt, Code Ratgeber

Ted Pattison, Ted Pattison Group

Dieser Artikel wurde von Microsoft mit der Berechtigung von den ursprünglichen Autoren aktualisiert.

**Gilt für:** Visual Studio-Tools für Office, Microsoft Office Microsoft Visual Studio.

## <a name="overview"></a>Übersicht

Sie können eine VSTO-Lösung entwickeln und die Lösung mithilfe eines Windows Installer Pakets bereitstellen. Diese Erörterung umfasst Schritte zum Bereitstellen eines einfachen Office-Add-Ins.

## <a name="deployment-methods"></a>Bereitstellungsmethoden

ClickOnce kann problemlos verwendet werden, um Setups für Ihre Add-Ins und Projektmappen zu erstellen. Es können jedoch keine Add-Ins installiert werden, für die Administratorrechte erforderlich sind, z. b. Add-Ins auf Computer Ebene.

Add-Ins, die Administratorrechte erfordern, können mit Windows Installer installiert werden, es ist jedoch mehr Aufwand erforderlich, um das Setup zu erstellen.

Eine Übersicht über das Bereitstellen einer VSTO-Lösung mithilfe von ClickOnce finden Sie unter Bereitstellen einer Office-Projekt Mappe mithilfe [von ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Bereitstellen von Office-Projektmappen für die VSTO-Laufzeit

ClickOnce-und Windows Installer Pakete müssen bei der Installation einer Office-Projekt Mappe die gleichen rudimentären Aufgaben ausführen.

1. Installieren Sie die erforderlichen Komponenten auf dem Benutzer Computer.
2. Stellen Sie die spezifischen Komponenten für die Lösung bereit.
3. Erstellen Sie Registrierungseinträge für Add-Ins.
4. Vertrauen Sie der Lösung, damit Sie ausgeführt werden kann.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Erforderliche Komponenten auf dem Bereitstellungs Ziel Computer

Im folgenden finden Sie eine Liste der Software, die auf dem Computer installiert werden muss, um VSTO-Lösungen auszuführen:

- Microsoft Office 2010 oder neuer.
- Das Microsoft .NET Framework 4 oder höher.
- Microsoft Visual Studio 2010-Tools für Office-Laufzeit.
  Die Laufzeit stellt eine Umgebung bereit, mit der Add-Ins und Projektmappen auf Dokument Ebene verwaltet werden. Eine Version der Laufzeit wird mit Microsoft Office ausgeliefert, Sie möchten jedoch möglicherweise eine bestimmte Version mit dem Add-in neu verteilen.
- Die primären Interop-Assemblys für Microsoft Office, wenn Sie keine eingebetteten Interop-Typen verwenden.
- Alle Hilfsprogramme-Assemblys, auf die von-Projekten

### <a name="specific-components-for-the-solution"></a>Bestimmte Komponenten für die Lösung

Vom Installationspaket müssen diese Komponenten auf dem Computer des Benutzers installiert werden:

- Das Microsoft Office Dokument, wenn Sie eine Projekt Mappe auf Dokument Ebene erstellen.
- Die Anpassungsassembly und alle erforderlichen Assemblys.
- Zusätzliche Komponenten, z. b. Konfigurationsdateien.
- Das Anwendungs Manifest (. manifest).
- Das Bereitstellungs Manifest (. VSTO).

### <a name="registry-entries-for-add-ins"></a>Registrierungseinträge für Add-ins

Microsoft Office verwendet Registrierungseinträge, um Add-Ins zu suchen und zu laden. Diese Registrierungseinträge sollten im Rahmen des Bereitstellungs Prozesses erstellt werden. Weitere Informationen zu diesen Registrierungs Einträgen finden Sie unter [Registrierungseinträge für VSTO-Add-ins](registry-entries-for-vsto-add-ins.md).

Outlook-Add-Ins, die benutzerdefinierte Formular Bereiche anzeigen, benötigen zusätzliche Registrierungseinträge, die die Identifizierung der Formular Bereiche ermöglichen. Weitere Informationen zu Registrierungs Einträgen finden Sie unter [Registrierungseinträge für Outlook-Formular Bereiche](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Für Projektmappen auf Dokument Ebene sind keine Registrierungseinträge erforderlich. Stattdessen werden Eigenschaften innerhalb des Dokuments verwendet, um die Anpassung zu suchen. Weitere Informationen zu diesen Eigenschaften finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Vertrauen der VSTO-Lösung

Damit eine Anpassung ausgeführt werden kann, muss eine Lösung vom Computer als vertrauenswürdig eingestuft werden. Das Add-in kann vertrauenswürdig sein, indem Sie das Manifest mit einem Zertifikat signieren, eine Vertrauensstellung mit einer Inklusions Liste erstellen oder es an einem vertrauenswürdigen Speicherort auf dem Computer installieren.

Weitere Informationen zum Abrufen eines Zertifikats für die Signierung finden Sie unter [ClickOnce-Bereitstellung und Authenticode](../deployment/clickonce-and-authenticode.md). Weitere Informationen zu vertrauenden Lösungen finden Sie unter vertrauende Office-Projektmappen [mithilfe von Inklusions Listen](trusting-office-solutions-by-using-inclusion-lists.md). Sie können einen Inklusions Listeneintrag mit einer benutzerdefinierten Aktion in der Windows Installer-Datei hinzufügen. Weitere Informationen zum Aktivieren der Aufnahme Liste finden Sie unter Vorgehens [Weise: Konfigurieren der Sicherheit für die Inklusions Liste](how-to-configure-inclusion-list-security.md).

Wenn keine der Optionen verwendet wird, wird dem Benutzer eine Vertrauensstellungs Aufforderung angezeigt, um die Entscheidung zu treffen, ob der Lösung vertraut werden soll.

Weitere Informationen zur Sicherheit im Zusammenhang mit Lösungen auf Dokument Ebene finden [Sie unter Gewähren von Vertrauenswürdigkeit für Dokumente](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Erstellen eines einfachen Installers

Die Projektvorlagen für Setup und Bereitstellung sind in der Erweiterung [Microsoft Visual Studio Installer-Projekte](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) enthalten, die zum Download zur Verfügung steht.

Um ein Installationsprogramm für eine Office-Projekt Mappe zu erstellen, müssen diese Aufgaben ausgeführt werden:

- Fügen Sie die Komponenten der Office-Projekt Mappe hinzu, die bereitgestellt werden.
- Konfigurieren Sie die Registrierungsschlüssel für Add-Ins auf Anwendungsebene.
- Konfigurieren Sie die erforderlichen Komponenten, damit Sie auf den Computern der Endbenutzer installiert werden können.
- Konfigurieren Sie Startbedingungen, um zu überprüfen, ob die erforderlichen erforderlichen Komponenten verfügbar sind. Startbedingungen können verwendet werden, um die Installation zu blockieren, wenn alle erforderlichen Komponenten nicht installiert sind.

Der erste Schritt besteht darin, das Setup-Projekt zu erstellen.

### <a name="to-create-the-addin-setup-project"></a>So erstellen Sie das AddIn-Setup-Projekt

1. Öffnen Sie das Office-AddIn-Projekt, das Sie bereitstellen möchten. In diesem Beispiel verwenden wir ein Excel-Add-in mit dem Namen ExcelAddIn.
2. Wenn das Office-Projekt geöffnet ist, erweitern Sie im Menü **Datei** die Option **Hinzufügen** , und klicken Sie auf **Neues Projekt** , um ein neues Projekt hinzuzufügen.
::: moniker range="=vs-2017"
3. Erweitern Sie im Dialogfeld **Neues Projekt hinzufügen** im Bereich **Projekttypen die** Option **andere Projekttypen** , erweitern Sie **Setup und Bereitstellung** , und wählen Sie dann **Visual Studio-Installer** aus.
4. Wählen Sie im Bereich **Vorlagen** die Option **Setup-Projekt** aus der Gruppe installierte Vorlagen von **Visual Studio** aus.
::: moniker-end
::: moniker range="=vs-2019"
3. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die **Setup-Projekt** Vorlage aus.
4. Klicken Sie auf **Weiter**.
::: moniker-end

5. Geben Sie im Feld **Name den Namen** **officeaddinsetup** ein.
::: moniker range="=vs-2017"
6. Klicken Sie auf **Öffnen** , um das neue Setup-Projekt zu erstellen.
::: moniker-end
::: moniker range="=vs-2019"
6. Klicken Sie auf **Erstellen** , um das neue Setup-Projekt zu erstellen.
::: moniker-end

Visual Studio öffnet den Datei System-Explorer für das neue Setup-Projekt. Mit dem Datei System-Explorer können Sie dem Setup-Projektdateien hinzufügen.

   ![Screenshot des Datei System-Explorers für das Setup-Projekt](media/setup-project-figure-1.png)

   **Abbildung 1: Datei System-Explorer für das Setup-Projekt**

Das Setup-Projekt muss ExcelAddIn bereitstellen. Sie können das Setup-Projekt für diese Aufgabe konfigurieren, indem Sie die Projekt Ausgabe ExcelAddIn dem Setup-Projekt hinzufügen.

### <a name="to-add-the-exceladdin-project-output"></a>So fügen Sie die ExcelAddIn-Projekt Ausgabe hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **officeaddinsetup**, klicken Sie auf **Hinzufügen** und dann auf **Projekt Ausgabe**.
2. Wählen Sie im Dialogfeld " **Projekt Ausgabe Gruppe hinzufügen** " die Option " **ExcelAddIn** " aus der Projektliste und die **primäre Ausgabe** aus.
3. Klicken Sie auf **OK** , um die Projekt Ausgabe dem Setup-Projekt hinzuzufügen.

    ![Screenshot des Setup-Projekts Projekt Ausgabe Gruppe hinzufügen (Dialogfeld)](media/setup-project-figure-2.png)

    **Abbildung 2: Einrichten des Dialog Felds "Projekt Ausgabe Gruppe hinzufügen"**

Das Setup-Projekt muss das Bereitstellungs Manifest und das Anwendungs Manifest bereitstellen. Fügen Sie diese beiden Dateien dem Setup-Projekt als eigenständige Dateien aus dem Ausgabeordner des ExcelAddIn-Projekts hinzu.

### <a name="to-add-the-deployment-and-application-manifests"></a>So fügen Sie die Bereitstellungs-und Anwendungs Manifeste hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **officeaddinsetup**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Datei**.
2. Navigieren Sie im Dialogfeld **Dateien hinzufügen** zum Ausgabeverzeichnis **ExcelAddIn** . Normalerweise ist das Ausgabeverzeichnis abhängig von der ausgewählten Buildkonfiguration der Unterordner " **bin \\ Release** " des Stamm Verzeichnisses des Projekts.
3. Wählen Sie die Dateien **ExcelAddIn. VSTO** und **ExcelAddIn.dll. Manifest** aus, und klicken Sie auf **Öffnen** , um diese beiden Dateien dem Setup-Projekt hinzuzufügen.

    ![Screenshot der Anwendungs-und Bereitstellungs Manifeste in Projektmappen-Explorer](media/setup-project-figure-3.jpg)

    **Abbildung 3: Anwendungs-und Bereitstellungs Manifeste für das Add-in in Projektmappen-Explorer**

Der Verweis auf ExcelAddIn umfasst alle Komponenten, die ExcelAddIn benötigt. Diese Komponenten müssen ausgeschlossen und mithilfe von erforderlichen Paketen bereitgestellt werden, damit Sie ordnungsgemäß registriert werden können. Außerdem müssen die Software Lizenzbedingungen vor Beginn der Installation angezeigt und akzeptiert werden.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>So schließen Sie die ExcelAddIn-Projekt Abhängigkeiten aus

1. Wählen Sie im **Projektmappen-Explorer** im Knoten **officeaddinsetup** alle Abhängigkeits Elemente unter dem Element **erkannte Abhängigkeiten** aus, mit Ausnahme von **Microsoft .NET Framework** oder einer Assembly, die mit **\*.Utilities.dll** endet. Die hilfsprogrammassemblys sollen zusammen mit Ihrer Anwendung bereitgestellt werden.
2. Klicken Sie mit der rechten Maustaste auf die Gruppe, und wählen Sie **Eigenschaften**
3. Ändern Sie im Fenster **Eigenschaften** die Eigenschaft **ausschließen** in **true** , um die abhängigen Assemblys aus dem Setup-Projekt auszuschließen. Stellen Sie sicher, dass keine hilfsprogrammassemblys ausgeschlossen werden.

    ![Screenshot der Projektmappen-Explorer, die die auszuschließenden Abhängigkeiten anzeigt](media/setup-project-figure-4.jpg)

    **Abbildung 4: Ausschließen von Abhängigkeiten**

Sie können Ihr Windows Installer Paket so konfigurieren, dass die erforderlichen Komponenten installiert werden, indem Sie ein Setup Programm, das auch als Boots Trapper bezeichnet wird, hinzufügen. Mit diesem Setup Programm können die erforderlichen Komponenten installiert werden. dabei handelt es sich um einen Prozess namens Bootstrapping.

Für **ExcelAddIn** müssen diese Voraussetzungen installiert werden, bevor das Add-in ordnungsgemäß ausgeführt werden kann:

- Die Microsoft .NET Framework-Version, auf die die Office-Projekt Mappe abzielt.
- Microsoft Visual Studio 2010 Tools für Office-Laufzeit.

So konfigurieren Sie abhängige Komponenten als erforderliche Komponenten

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **officeaddinsetup** , und wählen Sie **Eigenschaften** aus.
2. Das Dialogfeld **officeaddinsetup-Eigenschaften Seiten** wird angezeigt.
3. Klicken Sie **auf die Schalt** Fläche erforderliche Komponenten
4. Wählen Sie im Dialogfeld Voraussetzungen die richtige Version des .NET Framework und Microsoft Visual Studio Tools für Office-Laufzeit aus.

    ![Screenshot des Dialog Felds "Voraussetzungen"](media/setup-project-figure-5.png)

    **Abbildung 5: Dialog Feld "erforderliche Komponenten"**

    > [!NOTE]
    >Einige der konfigurierten erforderlichen Pakete in Ihrem Visual Studio-Setup-Projekt sind von der ausgewählten Buildkonfiguration abhängig. Sie müssen die richtigen erforderlichen Komponenten für jede Buildkonfiguration auswählen, die Sie verwenden.

Microsoft Office nach Add-Ins mithilfe von Registrierungs Schlüsseln. Die Schlüssel in der HKEY \_ Current \_ User-Struktur werden verwendet, um das Add-in für jeden einzelnen Benutzer zu registrieren. Die Schlüssel unter der HKEY-Struktur des \_ lokalen Computers \_ werden verwendet, um das Add-in für alle Benutzer auf dem Computer zu registrieren. Weitere Informationen zu Registrierungs Schlüsseln finden Sie unter [Registrierungseinträge für VSTO-Add-ins](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Konfigurieren der Registrierung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **officeaddinsetup**.
2. Erweitern Sie **Ansicht**.
3. Klicken Sie auf **Registrierung** , um das Fenster Registrierungs-Editor zu öffnen.
4. Erweitern Sie im Registrierungs-Editor **(officeaddinsetup)** **HKEY \_ local \_ Machine** und dann **Software**.
5. Löschen Sie den Schlüssel " **\[ Hersteller \]**?", der unter **HKEY \_ local \_ Machine \\ Software** gefunden wird.
6. Erweitern Sie **HKEY \_ aktueller \_ Benutzer** und dann **Software**.
7. Löschen Sie den **\[ Hersteller \]** Schlüssel, der unter **HKEY \_ Current \_ User \\ Software** gefunden wurde.
8. Klicken Sie zum Hinzufügen von Registrierungs Schlüsseln für die Add-in-Installation mit der rechten Maustaste auf den **Benutzer-/Computer-Hive** -Schlüssel, **und wählen Sie** Verwenden Sie die Text **Software** als Namen für den neuen Schlüssel. Klicken Sie mit der rechten Maustaste auf den neu erstellten **Software** Schlüssel, und erstellen Sie einen neuen Schlüssel mit dem Text **Microsoft**.
9. Verwenden Sie einen ähnlichen Prozess zum Erstellen der gesamten Schlüssel Hierarchie, die für die Add-in-Registrierung erforderlich ist:

    **User/Machine Hive \\ Software \\ Microsoft \\ Office \\ Excel \\ AddIns \\ SampleCompany. ExcelAddIn**

    Der Name des Unternehmens wird häufig als Präfix für den Namen des Add-Ins verwendet, um Eindeutigkeit zu gewährleisten.

10. Klicken Sie mit der rechten Maustaste auf den Schlüssel **Sample Company. ExcelAddIn** , wählen Sie **neu** aus, und klicken Sie auf **Zeichen folgen Wert**. Verwenden Sie die Text **Beschreibung** für den Namen.
11. Verwenden Sie diesen Schritt, um drei weitere Werte hinzuzufügen:
    - **FriendlyName** des Typs " **String** "
    - **LoadBehavior** des Typs **DWORD**
    - **Manifest** des Typs " **String** "

12. Klicken Sie mit der rechten Maustaste im Registrierungs-Editor auf den Wert **Beschreibung** , und klicken Sie auf **Eigenschaften Fenster**. Geben Sie im **Fenster Eigenschaften** für die Value-Eigenschaft **Excel-Demo** -Add-in ein.
13. Wählen Sie im Registrierungs-Editor den Schlüssel **FriendlyName** aus. Ändern Sie im **Fenster Eigenschaften** die Eigenschaft **Wert** in **Excel-Demo**-Add-in.
14. Wählen Sie im Registrierungs-Editor den Schlüssel **LoadBehavior** aus. Ändern Sie im **Fenster Eigenschaften** die Eigenschaft **Wert** in **3.** Der Wert 3 für das LoadBehavior-Verhalten gibt an, dass das Add-in beim Start der Host Anwendung geladen werden soll. Weitere Informationen zum Ladeverhalten finden Sie unter [Registrierungseinträge für VSTO-Add-ins](registry-entries-for-vsto-add-ins.md).

15. Wählen Sie im Registrierungs-Editor den Schlüssel **Manifest** aus. Ändern Sie im **Eigenschaften Fenster** die **value** -Eigenschaft in **file:///[TARGETDIR] ExcelAddIn. VSTO | vstolocal**

    ![Screenshot des Registrierungs-Editors](media/setup-project-figure-6.png)

    **Abbildung 6: Einrichten von Registrierungs Schlüsseln**

      Die VSTO-Laufzeit verwendet diesen Registrierungsschlüssel, um das Bereitstellungs Manifest zu suchen. Das Makro [TARGETDIR] wird durch den Ordner ersetzt, in dem das Add-in installiert wird. Das Makro schließt das nachfolgende \ Zeichen ein, sodass der Dateiname des Bereitstellungs Manifests ExcelAddIn. VSTO ohne das Zeichen \ lauten soll.
      Das **vstolocal** -postfix weist die VSTO-Laufzeit an, dass das Add-in anstelle des ClickOnce-Caches von diesem Speicherort geladen werden soll. Das Entfernen dieses postfixes bewirkt, dass die Laufzeit die Anpassung in den ClickOnce-Cache kopiert.

   >[!WARNING]
   >Sie sollten mit dem Registrierungs-Editor in Visual Studio sehr vorsichtig sein. Wenn Sie z. b. die DeleteAtUninstall versehentlich für den falschen Schlüssel festgelegt haben, können Sie einen aktiven Teil der Registrierung löschen und den Benutzer Computer in einem inkonsistenten oder noch schlechteren, unterbrochenen Zustand belassen.

in 64-Bit-Versionen von Office wird die 64-Bit-Registrierungs Struktur verwendet, um nach Add-Ins zu suchen. Zum Registrieren von Add-Ins unter der 64-Bit-Registrierungs Struktur muss die Zielplattform des Setup Projekts nur auf 64 Bit festgelegt werden.

1. Wählen Sie im Projektmappen-Explorer das Projekt **officeaddinsetup** aus.
2. Wechseln Sie zum **Eigenschaften** Fenster, und legen Sie die **TargetPlatform** -Eigenschaft auf **x64** fest.

Wenn Sie ein Add-in für die 32-Bit-und 64-Bit-Version von Office installieren, müssen Sie zwei separate MSI-Pakete erstellen. Einen für 32-Bit und einen für 64-Bit.

  ![Screenshot des Fensters "Eigenschaften", das die Zielplattform zum Registrieren von Add-Ins mit 64-Bit-Office anzeigt](media/setup-project-figure-7.jpg)

  **Abbildung 7: Zielplattform zum Registrieren von Add-Ins mit 64-Bit-Office**

Wenn das MSI-Paket zum Installieren des Add-Ins oder der Lösung verwendet wird, kann es installiert werden, ohne dass die erforderlichen Komponenten installiert werden müssen. Sie können Startbedingungen in der MSI verwenden, um die Installation des Add-Ins zu blockieren, wenn die erforderlichen Komponenten nicht installiert sind.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Konfigurieren einer Startbedingung zum Erkennen der VSTO-Laufzeit

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **officeaddinsetup**.
2. Erweitern Sie **Ansicht**.
3. Klicken Sie auf **Startbedingungen**.
4. Klicken Sie im Editor für **Startbedingungen (officeaddinsetup)** mit der rechten Maustaste **auf Anforderungen auf dem Zielcomputer**, und klicken Sie dann auf **Registrierungs Startbedingung hinzufügen**. Diese Such Bedingung kann die Registrierung nach einem Schlüssel durchsuchen, den die VSTO-Laufzeit installiert. Der Wert des Schlüssels ist dann über eine benannte Eigenschaft für die verschiedenen Teile des Installers verfügbar. Die Startbedingung verwendet die von der Such Bedingung definierte Eigenschaft, um einen bestimmten Wert zu überprüfen.
5. Wählen Sie im Editor **Startbedingungen (officeaddinsetup)** die Such Bedingung **Suchen nach RegistryEntry1 aus** , klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaften Fenster** aus.

6. Legen Sie im **Eigenschaftsfenster** diese Eigenschaften fest:
   1. Legen Sie den Wert von **(Name)** für die **Suche nach VSTO 2010 Runtime** fest.
   2. Ändern Sie den Wert der- **Eigenschaft** in **vstoruntimeredist**.
   3. Legen Sie den Wert von **RegKey** auf **Software \\ Microsoft \\ VSTO Runtime Setup \\ v4R**
   4. Belassen Sie die **root** -Eigenschaft auf **vsdrrHKLM**.
   5. Ändern Sie die **value** -Eigenschaft in **Version**.

7. Wählen Sie im Editor **Startbedingungen (officeaddinsetup)** die Bedingung **Bedingung1** Launch aus, klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaften Fenster** aus.
8. Legen Sie im Eigenschaftsfenster diese Eigenschaften fest:
   1. Legen Sie den **Namen (Name)** so fest, dass **VSTO 2010-Lauf Zeitverfügbarkeit überprüft**
   2. Ändern Sie den Wert der **Bedingung** in **vstoruntimeredist \> = "10.0.30319"** .
   3. Lassen Sie die **InstallUrl** -Eigenschaft leer.
   4. Legen Sie fest, dass die **Nachricht** auf **Visual Studio 2010-Tools für Office-Laufzeit nicht installiert ist. Führen Sie Setup.exe aus, um das Add-in zu installieren**.

        ![Screenshot des Fensters "Eigenschaften" für die Startbedingung "Lauf Zeitverfügbarkeit überprüfen"](media/setup-project-figure-8.jpg)

        **Abbildung 8: Eigenschaften Fenster für die Startbedingung zum Überprüfen der Lauf Zeitverfügbarkeit**

 Die obige Startbedingung überprüft explizit, ob die VSTO-Laufzeit vorhanden ist, wenn Sie vom Bootstrapperpaket installiert wird.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Konfigurieren einer Startbedingung zum Erkennen der von Office installierten VSTO-Laufzeit

1. Klicken Sie im **Startbedingungen-Editor (officeaddinsetup)** mit der rechten Maustaste auf **Zielcomputer suchen**, und klicken Sie dann auf **Registrierungs Suche hinzufügen**.
2. Wählen Sie die Such Bedingung **Suchen nach RegistryEntry1 aus** , klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaften Fenster** aus.
3. Legen Sie im **Eigenschaftsfenster** diese Eigenschaften fest:
    1. Legen Sie den Wert von **(Name)** für die **Suche nach Office VSTO Runtime** fest.
    2. Ändern Sie den Wert der- **Eigenschaft** in **officeruntime**.
    3. Legen Sie den Wert von **RegKey** auf **Software \\ Microsoft \\ VSTO Runtime Setup \\ V4** fest.
    4. Belassen Sie die **root** -Eigenschaft auf **vsdrrHKLM**.
    5. Ändern Sie die **value** -Eigenschaft in **Version**.

4. Wählen Sie im Editor **Startbedingungen (officeaddinsetup)** die Bedingung überprüfen Sie die Startbedingung für die **VSTO 2010-Lauf Zeitverfügbarkeit** aus, klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaften Fenster** aus.

5. Ändern Sie den Wert der **Condition** -Eigenschaft in **vstoruntimeredist \> = "10.0.30319" oder officeruntime \> = "10.0.21022"**. Abhängig von den Versionen der Laufzeit, die für das Add-in erforderlich sind, sind die Versionsnummern für Sie möglicherweise unterschiedlich.

    ![Screenshot der Fenster "Eigenschaften" für die Startbedingung](media/setup-project-figure-9.jpg)
  
    **Abbildung 9: Eigenschaften Fenster für das Überprüfen der Lauf Zeitverfügbarkeit über die Redist-oder Office-Startbedingung**

Wenn ein Add-in .NET Framework 4 oder höher als Ziel hat, können die Typen in den primären Interopassemblys (PIA), auf die verwiesen wird, in die VSTO-Assembly eingebettet werden.

Um zu überprüfen, ob die Interop-Typen in das Add-in eingebettet werden, führen Sie die folgenden Schritte aus:

1. Erweitern Sie den Knoten Verweise in Projektmappen-Explorer
2. Wählen Sie einen der Pia-Verweise aus, z. b. **Office**.
3. Zeigen Sie die Eigenschaften Fenster an, indem Sie F4 drücken oder im Kontextmenü Assemblys die Option Eigenschaften auswählen.
4. Überprüfen Sie den Wert der Eigenschaft **Interop-Typen einbetten**.

Wenn der Wert auf **true** festgelegt ist, werden die Typen eingebettet, und Sie können den Abschnitt [**zum Erstellen des Setup-Projekts**](#to-build-the-setup-project) überspringen.

Weitere Informationen finden Sie unter [typäquivalenz und eingebettete Interop-Typen](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>So konfigurieren Sie Startbedingungen, um dies für Office PIAs zu erkennen

1. Klicken Sie im Editor für **Startbedingungen (officeaddinsetup)** mit der rechten Maustaste **auf Anforderungen auf dem Zielcomputer**, und **Klicken Sie dann auf Windows Installer Startbedingung hinzufügen**. Diese Startbedingung sucht nach einer Office-Pia, indem Sie nach der jeweiligen Komponenten-ID sucht.
2. Klicken Sie mit der rechten Maustaste auf **Suchen nach Component1** , und klicken Sie auf **Eigenschaften Fenster** , um die Eigenschaften der Startbedingung anzuzeigen.
3. Legen Sie im **Fenster Eigenschaften** die folgenden Eigenschaften fest:

    1. Ändern Sie den Wert der Eigenschaft **(Name)** , um nach **Office Shared Pia zu suchen** .
    2. Ändern Sie den Wert der **ComponentID** in Komponenten-ID für die von Ihnen verwendete Office-Komponente. Sie finden die Liste der Komponenten-IDs in der folgenden Tabelle, z. **b. {64e2917e-aa13-4ca4-bffe-ea6eda3afcb4}**.
    3. Ändern Sie den Wert der **Eigenschaft Eigenschaft** in **hassharedpia**.

4. Klicken Sie im **Startbedingungen-Editor (officeaddinsetup)** mit der rechten Maustaste auf **Bedingung1** , und klicken Sie dann auf **Eigenschaften Fenster** , um die Eigenschaften der Startbedingung anzuzeigen.

5. Ändern Sie diese Eigenschaften von **Bedingung1**:

    1. Ändern Sie den **Namen (Name)** , um die frei **gegebene Office-Pia-Verfügbarkeit**
    2. Ändern Sie die **Bedingung** in **hassharedpia**.
    3. Lassen Sie **InstallUrl** leer.
    4. Das Ändern der **Nachricht** in **eine erforderliche Komponente für die Interaktion mit Excel ist nicht verfügbar. Führen Sie setup.exe** aus.

    ![Screenshot des Fensters "Eigenschaften" für die Startbedingung "Shared Office Shared Pia"](media/setup-project-figure-10.jpg)
  
    **Abbildung 10: Eigenschaften Fenster für die Shared Office Shared Pia-Startbedingung**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Komponenten-IDs der primären Interop-Assemblys für Microsoft Office

|Primäre Interop-Assembly|Office 2010|Office 2013|Office 2013 (64 Bit)|Office 2016|Office 2016 (64 Bit)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26e4fc2223ff}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153b732-d670-4e44-8ab7-500t2b576bda}|{0F 825a16-25b2-4771-a497-fc8af3b355d8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1d844339-3dae-413E-BC13-62d6a52816b2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824a03f-28CC-4371-BC54-93d15efc1e7f}|{7c6d92ef-7b45-46e5-8670-819663220e4e}|{7c6d92ef-7b45-46e5-8670-819663220e4e}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139ad-6dab-4ddd-8c6d-0ca30d073b41}|{05758318-bcfd-4288-AD8D-81185841c235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3ea123b5-6316-452e-9d51-a489e06e2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2cc0b221-22d2-4c15-a9f b-de818e51af75}|{2d4540ec-2c88-4c28-ae88-2614b5460648}|{2d4540ec-2c88-4c28-ae88-2614b5460648}|
|Word|{8b74a499-37F 8-4dea-b5a0-d72fc501cefa}|{9fe736b7-b1ee-410C-8d07-082891c3dac8}|{13c07af5-B206-4a48-bb5b-b8022333e3ca}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2,0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011b9112-ebb1-4a6c-86cb-c2fdc9ea7b0e}|{52da4b37-b8eb-4b7b-89c1-824654ce4c70}|{24706f 33-bc91-9e935394, BC e B510}|-|-|
|Smart Tag|{7102c98c-ef47-4b04-A227-fe33650bf 954}|{487a7921-EB3A-4262-BB5B-A5736B732486}|{74efc1f-747d-4867-B951-EFCF29F51AF7}|-|-|
|Office Shared|{64e2917e-aa13-4ca4-bffe-ea6eda3afcb4}|{6a174bdb-0049-4d1c-86ef-3114cb0c4c4e}|{76601ebb-44a7-49ee-8un3-7b7b9d7ebb05}|{625F 5772-c1b3-497e-8abe-7254edb00506}|{625F 5772-c1b3-497e-8abe-7254edb00506}|
|Project|{957a4ec0-e67b-4e86-a383-6af7270b216a}|{1c50e422-24FA-44a9-A120-e88280c8c341}|{706d7f 44-8231-489D-9b25-3025ade9b114}|{107bcd9a-F1DC-4004-A444-33706fc10058}|{107bcd9a-F1DC-4004-A444-33706fc10058}|

  ![Screenshot der abschließenden Startbedingungen](media/setup-project-figure-11.jpg)

  **Abbildung 11: endgültige Startbedingungen**

Sie können die Startbedingungen der ExcelAddIn-Installation weiter verfeinern. Beispielsweise kann es hilfreich sein, zu überprüfen, ob die tatsächliche Office-Zielanwendung installiert ist.

### <a name="to-build-the-setup-project"></a>So erstellen Sie das Setup-Projekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **officeaddinsetup** , und klicken Sie auf **Erstellen**.
2. Navigieren Sie in **Windows-Explorer** zum Ausgabeverzeichnis des Projekts **officeaddinsetup** , und wechseln Sie abhängig von der ausgewählten Buildkonfiguration zum Ordner Freigabe oder Debuggen. Kopieren Sie alle Dateien aus dem Ordner an einen Speicherort, auf den Benutzer zugreifen können.

So testen Sie das ExcelAddIn-Setup

1. Navigieren Sie zu dem Speicherort, in den Sie **officeaddinsetup** kopiert haben.
2. Doppelklicken Sie auf die Datei setup.exe, um das **officeaddinsetup** -Add-in zu installieren. Akzeptieren Sie sämtliche Software Lizenzbedingungen, die angezeigt werden, und schließen Sie den Setup-Assistenten ab, um das Add-in auf dem Benutzer Computer zu installieren.

Die Excel Office-Projekt Mappe sollte an dem während der Installation angegebenen Speicherort installiert und ausgeführt werden.

## <a name="additional-requirements-for-document-level-solutions"></a>Zusätzliche Anforderungen für Projektmappen auf Dokument Ebene

Zum Bereitstellen von Projektmappen auf Dokument Ebene sind einige verschiedene Konfigurationsschritte im Windows Installer Setup-Projekt erforderlich.

Hier finden Sie eine Liste der grundlegenden Schritte, die für die Bereitstellung einer Lösung auf Dokument Ebene erforderlich sind:

- Erstellen Sie das Visual Studio-Setup-Projekt.
- Fügen Sie die primäre Ausgabe der Projekt Mappe auf Dokument Ebene hinzu. Die primäre Ausgabe enthält auch das Microsoft Office Dokument.
- Fügen Sie die Bereitstellungs-und Anwendungs Manifeste als lose Dateien hinzu.
- Ausschließen der abhängigen Komponenten aus dem Installationspaket (mit Ausnahme von Hilfsprogrammen-Assemblys).
- Konfigurieren Sie die erforderlichen Pakete.
- Startbedingungen konfigurieren.
- Erstellen Sie das Setup-Projekt, und kopieren Sie die Ergebnisse an den Bereitstellungs Speicherort.
- Stellen Sie die Projekt Mappe auf Dokument Ebene auf dem Benutzer Computer bereit, indem Sie das-Setup ausführen.
- Aktualisieren Sie die benutzerdefinierten Dokumenteigenschaften bei Bedarf.

### <a name="changing-the-location-of-the-deployed-document"></a>Ändern des Speicher Orts des bereitgestellten Dokuments

Eigenschaften in einem Office-Dokument werden verwendet, um Lösungen auf Dokument Ebene zu suchen. Wenn das Dokument in demselben Ordner wie die VSTO-Assembly installiert wird, sind keine Änderungen erforderlich. Wenn Sie jedoch in einem anderen Ordner installiert ist, müssen diese Eigenschaften während des Setups aktualisiert werden.

Weitere Informationen zu diesen Dokumenteigenschaften finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](custom-document-properties-overview.md).

Um diese Eigenschaften zu ändern, müssen Sie während des Setups eine benutzerdefinierte Aktion verwenden.

Im folgenden Beispiel wird eine Lösung auf Dokument Ebene mit dem Namen excelworkbookproject und ein Setup Projekt mit dem Namen excelworkbooksetup verwendet. Das excelworkbooksetup-Projekt wird mit den oben beschriebenen Schritten konfiguriert, mit Ausnahme der Festlegung der Registrierungsschlüssel.

So fügen Sie das benutzerdefinierte Aktionsprojekt zu Ihrer Visual Studio-Projekt Mappe hinzu

1. Fügen Sie **der Projekt Mappe** ein neues .net-Konsolen Projekt hinzu, indem Sie im **Projektmappen-Explorer**
2. Erweitern Sie **Hinzufügen** , und klicken Sie auf **Neues Projekt**.
3. Wählen Sie die Vorlage Konsolen-App aus, und nennen Sie das Projekt **addcustomizationcustomaction**.

    ![Screenshot der Projektmappen-Explorer-addcustomizationcustomaction](media/setup-project-figure-15.jpg)
  
    **Abbildung 12: Projektmappen-Explorer-addcustomizationcustomaction**

4. Fügen Sie einen Verweis auf diese Assemblys hinzu:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft. VisualStudio. Tools. Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Kopieren Sie diesen Code in Program.cs oder Program. vb.

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Um dem Dokument die Anpassung hinzuzufügen, benötigen Sie die projektmappenkennung der VSTO-Projekt Mappe auf Dokument Ebene. Dieser Wert wird aus der Visual Studio-Projektdatei abgerufen.

So rufen Sie die Lösungs-ID ab

1. Klicken Sie im Menü **Erstellen** auf Projekt Mappe **Erstellen** , um die Projekt Mappe auf Dokument Ebene zu erstellen, und fügen Sie der Projektdatei die Eigenschaft projektmappenkennung hinzu.
2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt auf Dokument Ebene **excelworkbookproject** .
3. Klicken Sie auf **UnloadProject** , um in Visual Studio auf die Projektdatei zuzugreifen.

    ![Screenshot der Projektmappen-Explorer Entladen der Excel-Dokument Lösung](media/setup-project-figure-16.jpg)

    **Abbildung 13: Entladen der Excel-Dokument Lösung**

4. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **excelworkbookproject** , und klicken Sie auf **editexcelworkbookproject. vbproj** oder **Bearbeiten excelworkbookproject. csproj**.
5. Suchen Sie im **excelworkbookproject** -Editor das **SolutionId** -Element innerhalb des **PropertyGroup** -Elements.
6. Kopieren Sie den GUID-Wert dieses Elements.

    ![Abrufen von SolutionID](media/setup-project-figure-17.jpg)

    **Abbildung 14: Abrufen der SolutionID**

7. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **excelworkbookproject** , und klicken Sie dann auf **Projekt erneut laden**.
8. Klicken Sie im angezeigten Dialogfeld auf **Ja** , um den **excelworkbookproject** -Editor zu schließen.
9. Die **Lösungs-ID** wird in der benutzerdefinierten Aktion installieren verwendet.

Der letzte Schritt besteht darin, die benutzerdefinierte Aktion für die Schritte zum **Installieren** und **deinstallieren** zu konfigurieren.

### <a name="to-configure-the-setup-project"></a>So konfigurieren Sie das Setup-Projekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **excelworkbooksetup**, erweitern Sie **Hinzufügen** , und klicken Sie dann auf **Projekt Ausgabe**.
2. Klicken Sie im Dialogfeld **Projekt Ausgabe Gruppe hinzufügen** in der Liste **Projekt** auf **addcustomizationcustomaction**.
3. Wählen Sie **primäre Ausgabe** aus, und klicken Sie auf **OK** , um das Dialogfeld zu schließen und die Assembly mit der benutzerdefinierten Aktion dem Setup-Projekt hinzuzufügen.

    ![Screenshot des Dokument Manifest benutzerdefinierte Aktion-Projekt Ausgabe Gruppe hinzufügen](media/setup-project-figure-18.jpg)

    **Abbildung 15: Dokument Manifest benutzerdefinierte Aktion-Projekt Ausgabe Gruppe hinzufügen**

4. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **excelworkbooksetup**.
5. Erweitern Sie **Ansicht** , und klicken Sie auf **benutzerdefinierte Aktionen**.
6. Klicken Sie im Editor für **benutzerdefinierte Aktionen (excelworkbooksetup)** mit der rechten Maustaste auf **benutzerdefinierte Aktionen** und dann auf **benutzerdefinierte Aktion hinzufügen**.
7. Klicken Sie im Dialogfeld **Element in Projekt auswählen** in der Liste **Suchen in** auf **Anwendungsordner**. Wählen Sie **primäre Ausgabe aus addcustomizationcustomaction (aktiv) aus** , und klicken Sie auf **OK** , um die benutzerdefinierte Aktion dem Installationsschritt hinzuzufügen.
8. Klicken Sie unter dem **Knoten installieren** mit der rechten Maustaste auf **primäre Ausgabe von addcustomizationcustomaction (aktiv)**, und klicken Sie dann auf **Umbenennen**. Benennen Sie die benutzerdefinierte Aktion "Dokument kopieren" in "eigene Dateien" **, und fügen Sie**
9. Klicken Sie unter dem **Knoten deinstallieren** mit der rechten Maustaste auf **primäre Ausgabe von addcustomizationcustomaction (aktiv)** , und klicken Sie dann auf **Umbenennen**. Benennen Sie die benutzerdefinierte Aktion **Dokument entfernen aus dem Ordner Dokumente**.

    ![Screenshot des Fensters "benutzerdefinierte Aktionen" des Dokument Manifests](media/setup-project-figure-19.jpg)

    **Abbildung 16: benutzerdefinierte Aktionen im Dokument Manifest**

10. Klicken Sie im Editor für **benutzerdefinierte Aktionen (excelworkbooksetup)** mit der rechten Maustaste auf **Dokument in eigene Dateien kopieren, und fügen Sie Anpassung an,** und klicken Sie auf **Eigenschaften Fenster**.
11. Geben Sie im **Eigenschaften** Fenster von **customaktiondata** den Speicherort der Anpassungs-DLL, das Bereitstellungs Manifest und den Speicherort des Microsoft Office Dokuments ein. Die SolutionID ist ebenfalls erforderlich.
12. Wenn Sie Setup Fehler in einer Datei protokollieren möchten, fügen Sie einen Logfile-Parameter ein.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Screenshot der benutzerdefinierten Aktion zum Kopieren von Dokumenten in eigene Dokumente Eigenschaftenfenster](media/setup-project-figure-20.jpg)

    **Abbildung 17: benutzerdefinierte Aktion zum Kopieren von Dokumenten in eigene Dokumente**

13. Die benutzerdefinierte Aktion für die Deinstallation erfordert den Namen des Dokuments, das Sie mithilfe des gleichen documentlocation-Parameters in **CustomAction Data** angeben können.

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Kompilieren Sie das Projekt **excelworkbooksetup** , und stellen Sie es bereit.
15. Suchen Sie im Ordner **eigene** Dateien, und öffnen Sie die Datei ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Weitere Ressourcen

[Vorgehensweise: Installieren des Visual Studio-Tools für die Office-Laufzeit](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Primäre Interop-Assemblys in Office](office-primary-interop-assemblies.md)

[Registrierungseinträge für VSTO-Add-ins](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Angeben von Formular Bereichen in der Windows-Registrierung](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Über die Autoren

Wouter van Vugt ist ein Microsoft MVP mit Office Open XML-Technologien und ein unabhängiger Berater, der sich auf die Erstellung von Office Business Applications (OBAs) mit SharePoint, Microsoft Office und Verwandten .NET-Technologien konzentriert.
Wouter ist ein häufig Mitwirkender für Entwickler Community-Websites, z. b. [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Er hat eine Reihe von Whitepapers und Artikeln sowie ein Buch mit dem Titel Open XML: erläutertes e-Book zur Verfügung gestellt.
Wouter ist der Gründer von Code-Ratgeber, einem niederländischen Unternehmen, das sich auf die Bereitstellung von hochmodernen technischen Inhalten über eine Vielzahl von Kanälen konzentriert. Weitere Informationen zu Wouter finden Sie in seinem Blog.

Ted Pattison ist ein SharePoint MVP, Author, Trainer und der Gründer der Ted Pattison Group. Im Fall von 2005 wurde Ted von der Entwicklerplattform der Entwicklerplattform von Microsoft beauftragt, den Aufstiegs Schulungs Lehrplan für Entwickler für Windows SharePoint Services 3,0 und Microsoft Office SharePoint Server 2007 zu verfassen. Seit dieser Zeit hat sich Ted vollständig auf die Ausbildung professioneller Entwickler auf SharePoint 2007-Technologien konzentriert. Ted hat das Schreiben eines Buchs für Microsoft Press mit dem Titel in Windows SharePoint Services 3,0 abgeschlossen, das sich auf die Verwendung von SharePoint als Entwicklungsplattform zum Erstellen von Geschäftslösungen konzentriert. Ted schreibt auch eine im Entwickler fokussierte Spalte für das MSDN Magazine mit dem Titel "Office Space".
