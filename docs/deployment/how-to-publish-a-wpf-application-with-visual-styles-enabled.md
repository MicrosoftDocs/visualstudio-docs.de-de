---
title: Veröffentlichen einer WPF-App mit aktivierten visuellen Stilen
description: Erfahren Sie, wie Sie eine WPF-Anwendung mit aktivierten visuellen Stilen veröffentlichen, sodass die Darstellung von Steuerelementen basierend auf dem vom Benutzer ausgewählten Design geändert werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e372d3163dcef84d76d77e54c66cf9f7c788e213
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349853"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Vorgehensweise: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Designs

Durch visuelle Stile kann die Darstellung von allgemeinen Steuerelementen auf Grundlage des vom Benutzer ausgewählten Designs geändert werden. Standardmäßig werden keine visuellen Stile für WPF-Anwendungen (Windows Presentation Foundation) aktiviert. Daher müssen Sie sie manuell aktivieren. Allerdings tritt bei der Veröffentlichung der Projektmappe ein Fehler auf, wenn visuelle Stile für eine WPF-Anwendung aktiviert sind. In diesem Thema wird beschrieben, wie dieser Fehler zu beheben ist und wie eine WPF-Anwendung mit aktivierten visuellen Stilen veröffentlicht werden kann. Weitere Informationen zu visuellen Stilen finden Sie unter [Übersicht über visuelle Stile](/windows/desktop/Controls/visual-styles-overview). Weitere Informationen zur Fehlermeldung finden Sie unter [Beheben von spezifischen Fehlern in ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)-bereit Stellungen.

 Um den Fehler zu beheben und die Projektmappe zu veröffentlichen, müssen Sie die folgenden Schritte ausführen:

- [Veröffentlichen Sie die Projekt Mappe ohne aktivierte visuelle Stile](#publish-the-solution-without-visual-styles-enabled).

- [Erstellen Sie eine Manifest-Datei](#create-a-manifest-file).

- [Betten Sie die Manifest-Datei in die ausführbare Datei der veröffentlichten](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)Projekt Mappe ein.

- [Signieren Sie die Anwendungs-und Bereitstellungs Manifeste](#sign-the-application-and-deployment-manifests).

  Anschließend können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem Endbenutzer die Anwendung installieren sollen.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>So veröffentlichen Sie die Projektmappe ohne aktivierte visuelle Stile

1. Stellen Sie sicher, dass visuelle Stile für das Projekt nicht aktiviert sind. Überprüfen Sie zunächst die Manifestdatei des Projekts auf folgenden XML-Code. Wenn der XML-Code vorhanden ist, schließen Sie ihn in ein Kommentartag ein.

     Visuelle Stile sind standardmäßig nicht aktiviert.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     Die folgenden Prozeduren zeigen, wie die Manifestdatei geöffnet wird, die Ihrem Projekt zugeordnet ist.

    **So öffnen Sie die Manifestdatei in einem Visual Basic-Projekt**

    1. Wählen Sie in der Menüleiste **Projekt, Projekt** *Name* **Eigenschaften** aus, wobei *ProjectName* der Name des WPF-Projekts ist.

         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.

    2. Klicken Sie in der Registerkarte **Anwendung** auf **Windows-Einstellungen anzeigen**.

         Die Datei „app.manifest“ wird im **Code-Editor** geöffnet.

    **So öffnen Sie die Manifestdatei in einem C#-Projekt**

    1. Wählen Sie in der Menüleiste **Projekt, Projekt** *Name* **Eigenschaften** aus, wobei *ProjectName* der Name des WPF-Projekts ist.

         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.

    2. Beachten Sie auf der Registerkarte **Anwendung** den Namen, der im Manifestfeld angezeigt wird. Dies ist der Name des Manifests, das dem Projekt zugeordnet ist.

        > [!NOTE]
        > Wenn **Manifest mit Standardeinstellungen einbetten** oder **Anwendung ohne Manifest erstellen** im Manifestfeld angezeigt wird, werden visuelle Designs nicht aktiviert. Wenn der Name einer Manifestdatei im Manifestfeld angezeigt wird, wechseln Sie zum nächsten Schritt in diesem Verfahren.

    3. Klicken Sie im **Projektmappen-Explorer** auf **Alle Dateien anzeigen**.

         Mit dieser Schaltfläche werden alle Projektelemente angezeigt, einschließlich der ausgeschlossen und derjenigen, die normalerweise ausgeblendet werden. Die Manifestdatei erscheint als Projektelement.

2. Erstellen und veröffentlichen Sie die Projektmappe. Weitere Informationen zum Veröffentlichen der Lösung finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a>So erstellen Sie eine Manifestdatei

1. Fügen Sie folgendes XML in eine Editor-Datei ein.

     Dieser XML-Code beschreibt die Assembly, die Steuerelemente enthält, die visuelle Stile unterstützen.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0"
        xmlns="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. Klicken Sie im Editor auf **Datei** und dann auf **Speichern unter**.

3. Klicken Sie im Dialogfeld **Speichern unter** auf die Dropdownliste **Dateityp** , und wählen Sie **Alle Dateien** aus.

4. Geben Sie im Feld **Dateiname** einen Namen für die Datei ein, und fügen Sie dem Ende des Namens *.manifest* an. Beispiel: *themes.manifest*.

5. Klicken Sie auf die Schaltfläche **Ordner durchsuchen** , wählen Sie einen beliebigen Ordner aus, und klicken Sie dann auf **Speichern**.

    > [!NOTE]
    > Im verbleibenden Verfahren wird davon ausgegangen, dass der Name dieser Datei *themes.manifest* ist und auf dem Computer im Verzeichnis *C:\temp* gespeichert wird.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>So fügen Sie die Manifestdatei in die ausführbare Datei der veröffentlichten Projektmappe ein

1. Öffnen Sie die **Visual Studio-Eingabeaufforderung**.

    Weitere Informationen zum Öffnen der **Visual Studio-Eingabeaufforderung** finden Sie unter [Eingabe Aufforderungen](/dotnet/framework/tools/developer-command-prompt-for-vs).

   > [!NOTE]
   > In den verbleibenden Schritten werden die folgenden Annahmen über die Projektmappe gemacht:
   >
   > - Der Name der Projektmappe ist **MyWPFProject**.
   > - Die Lösung befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - Die Projekt Mappe wird im folgenden Verzeichnis veröffentlicht: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - Die neueste Version der veröffentlichten Anwendungs Dateien befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Sie müssen die oben genannten Namen und Verzeichnisspeicherorte nicht verwenden. Die oben genannten Namen und Speicherorte dienen nur als Beispiele bei der Veranschaulichung der Schritte, die für die Veröffentlichung der Projektmappe erforderlich sind.

2. Ändern Sie an der Eingabeaufforderung den Pfad zu dem Verzeichnis, das die neueste Version der veröffentlichten Anwendungsdateien enthält. Das folgende Beispiel veranschaulicht diesen Schritt.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Manifestdatei in die ausführbare Datei der Anwendung einzubetten:

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>So signieren Sie die Anwendungs- und Bereitstellungsmanifeste

1. Führen Sie an der Eingabeaufforderung den folgenden Befehl aus, um die Erweiterung *.* Bereitstellungs Erweiterung aus der ausführbaren Datei im aktuellen Verzeichnis zu entfernen.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass nur eine Datei die Dateierweiterung *.* bereitstellen hat. Stellen Sie sicher, dass Sie alle Dateien in diesem Verzeichnis mit der Dateierweiterung *.* bereitstellen umbenennen.

2. Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Anwendungsmanifests ein:

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass Sie das Manifest mit der *PFX* -Datei des Projekts signieren. Wenn Sie das Manifest nicht signieren, können Sie den-Parameter weglassen, der `-cf` in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat signieren, das ein Kennwort erfordert, geben Sie die `-password` Option ( `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` ) an.

3. Führen Sie an der Eingabeaufforderung den folgenden Befehl aus, um die *.* Bereitstellungs Erweiterung dem Namen der Datei hinzuzufügen, die Sie in einem vorherigen Schritt dieses Verfahrens umbenannt haben.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass nur eine Datei die Dateierweiterung *.* bereitstellen hat. Stellen Sie sicher, dass Sie alle Dateien in diesem Verzeichnis umbenennen, die zuvor die Dateinamenerweiterung *.* bereitstellen.

4. Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Verteilungsmanifests ein:

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass Sie das Manifest mit der *PFX* -Datei des Projekts signieren. Wenn Sie das Manifest nicht signieren, können Sie den-Parameter weglassen, der `-cf` in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat signieren, das ein Kennwort erfordert, geben Sie die `-password` Option an, wie in diesem Beispiel: `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

   Nachdem Sie diese Schritte ausgeführt haben, können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem aus Endbenutzer die Anwendung installieren sollen. Wenn Sie beabsichtigen, die Projektmappe häufig zu aktualisieren, können Sie diese Befehle in ein Skript übernehmen und das Skript jedes Mal ausführen, wenn Sie eine neue Version veröffentlichen.

## <a name="see-also"></a>Weitere Informationen

-[Problembehandlung bei bestimmten Fehlern in ClickOnce-bereit Stellungen](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Übersicht über visuelle Stile](/windows/desktop/Controls/visual-styles-overview)
- [Aktivieren von visuellen Stilen](/windows/desktop/Controls/cookbook-overview)
- [Eingabeaufforderungen](/dotnet/framework/tools/developer-command-prompt-for-vs)
