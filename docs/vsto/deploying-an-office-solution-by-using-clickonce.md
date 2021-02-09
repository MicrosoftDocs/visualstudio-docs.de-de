---
title: Bereitstellen einer Office-Projekt Mappe mithilfe von ClickOnce
description: Erfahren Sie, wie Sie Ihre Office-Projekt Mappe in weniger Schritten bereitstellen können, wenn Sie ClickOnce verwenden. Wenn Sie Updates veröffentlichen, erkennt die Projektmappe sie automatisch und installiert sie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: da527da4504d4c2d9375aee0209b0e261fe5fd0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877932"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Bereitstellen einer Office-Projekt Mappe mithilfe von ClickOnce
  Wenn Sie ClickOnce verwenden, können Sie die Office-Projektmappe in weniger Schritten bereitstellen. Wenn Sie Updates veröffentlichen, erkennt die Projektmappe sie automatisch und installiert sie. Für ClickOnce ist es jedoch erforderlich, die Projektmappe für jeden Benutzer eines Computers separat zu installieren. Daher sollten Sie die Verwendung von Windows Installer (*. msi*) in Erwägung gezogen, wenn die Projekt Mappe von mehreren Benutzern auf dem gleichen Computer ausgeführt wird.

## <a name="in-this-topic"></a>In diesem Thema

- [Veröffentlichen der Projektmappe](#Publish)

- [Festlegen, wie der Projektmappe Vertrauenswürdigkeit gewährt werden soll](#Trust)

- [Hilfe für Benutzer bei der Installation der Projektmappe](#Helping)

- [Kopieren des Dokuments einer Projektmappe auf den Computer des Endbenutzers (nur Anpassungen auf Dokumentebene)](#Put)

- [Kopieren des Dokuments einer Projektmappe auf einen Server, auf dem SharePoint ausgeführt wird (nur Anpassungen auf Dokumentebene)](#SharePoint)

- [Erstellen eines benutzerdefinierten Installationsprogramms](#Custom)

- [Veröffentlichen eines Updates](#Update)

- [Ändern des Installationspfads einer Projektmappe](#Location)

- [Zurücksetzen der Projektmappe auf eine frühere Version](#Roll)

  Weitere Informationen zum Bereitstellen einer Office-Projekt Mappe durch Erstellen einer Windows Installer Datei finden Sie unter Bereitstellen einer Office-Projekt Mappe [mithilfe Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a> Veröffentlichen der Projekt Mappe
 Sie können die Projekt Mappe mit dem **Webpublishing-Assistenten** oder dem **Projekt-Designer** veröffentlichen. In diesem Verfahren verwenden Sie den Projekt- **Designer** , da er den gesamten Satz von Veröffentlichungs Optionen bereitstellt. Informationen finden Sie [unter Veröffentlichungs-Assistent &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>So veröffentlichen Sie die Projektmappe

1. Wählen Sie in **Projektmappen-Explorer** den Knoten aus, der für Ihr Projekt benannt ist.

2. Wählen Sie in der Menüleiste **Projekt, Projekt** *Name* **Eigenschaften** aus.

3. Wählen Sie im **Projekt-Designer** die Registerkarte **veröffentlichen** aus, die in der folgenden Abbildung gezeigt wird.

    ![Registerkarte "Veröffentlichen" im Projekt-Designer](../vsto/media/vsto-publishtab.png "Registerkarte "Veröffentlichen" im Projekt-Designer")

4. Geben Sie im Feld **Speicherort des Veröffentlichungs Ordners (FTP-Server oder Dateipfad)** den Pfad des Ordners ein, in den der **Projekt-Designer** die Projektmappendateien kopieren soll.

    Folgende Pfadtypen sind möglich:

   - Ein lokaler Pfad (z. b. *c:\foldername\foldername*).

   - Ein UNC-Pfad (Uniform Naming Convention) zu einem Ordner im Netzwerk (z. b. *\\ \servername\foldername*).

   - Ein relativer Pfad (z. b. " *publishfolder \\*", bei dem es sich um den Ordner handelt, in dem das Projekt standardmäßig veröffentlicht wird).

5. Geben Sie im Feld **URL des Installations Ordners** den voll qualifizierten Pfad des Speicher Orts ein, an dem die Endbenutzer Ihre Lösung finden.

    Wenn Sie den Standort noch nicht kennen, geben Sie nichts in dieses Feld ein. Standardmäßig sucht ClickOnce in dem Ordner, von dem aus die Benutzer die Projektmappe installieren, nach Updates.

6. Klicken Sie auf die Schaltfläche **Erforderliche Komponenten** .

7. Vergewissern Sie sich, dass im Dialogfeld **Voraussetzungen** das Kontrollkästchen **Setup Programm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.

8. Aktivieren Sie in der Liste **Wählen Sie die zu installier** enden Komponenten aus die Kontrollkästchen für **Windows Installer 4,5** und das entsprechende .NET Framework Paket.

    Wenn die Projekt Mappe beispielsweise auf abzielt [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , aktivieren Sie die Kontrollkästchen für **Windows Installer 4,5** und **Microsoft .NET Framework 4,5 Full**.

9. Wenn die Projekt Mappe den .NET Framework 4,5 als Ziel hat, aktivieren Sie auch das Kontrollkästchen **Visual Studio 2010-Tools für Office-Laufzeit** .

    > [!NOTE]
    > Standardmäßig wird dieses Kontrollkästchen nicht angezeigt. Damit es angezeigt wird, müssen Sie ein Bootstrapperpaket erstellen. Weitere Informationen finden [Sie unter Erstellen eines Bootstrapperpakets für ein Office 2013 VSTO-Add-in mit Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. Wählen Sie unter **Installationsort für** erforderliche Komponenten angeben eine der angezeigten Optionen aus, und klicken Sie dann auf die Schaltfläche **OK** .

     In der folgenden Tabelle sind die einzelnen Optionen beschrieben.

    |Option|BESCHREIBUNG|
    |------------|-----------------|
    |**Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**|Der Benutzer wird aufgefordert, diese erforderlichen Komponenten vom Hersteller herunterzuladen und zu installieren.|
    |**Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**|Die erforderliche Software wird mit der Projektmappe installiert. Wenn Sie diese Option auswählen, kopiert Visual Studio alle erforderlichen Pakete für Sie an den Veröffentlichungsort. Damit diese Option funktioniert, müssen sich die erforderlichen Pakete auf dem Entwicklungscomputer befinden.|
    |**Erforderliche Komponenten von folgendem Speicherort herunterladen**|Visual Studio kopiert alle erforderlichen Pakete an den angegebenen Speicherort und installiert sie mit der Projektmappe.|

     Siehe [Voraussetzungen (Dialogfeld](../ide/reference/prerequisites-dialog-box.md)).

11. Wählen Sie die Schaltfläche **Updates** aus, geben Sie an, wie oft das VSTO-Add-in oder die Anpassung jedes Endbenutzers nach Updates suchen soll, und klicken Sie dann auf die Schaltfläche **OK** .

    > [!NOTE]
    > Wenn Sie die Bereitstellung über eine CD oder ein Wechsel Laufwerk durcharbeiten, aktivieren Sie das Optionsfeld **nie nach Updates suchen** .

     Informationen zum Veröffentlichen eines Updates finden Sie unter [Veröffentlichen eines Updates](#Update).

12. Wählen Sie die Schaltfläche **Optionen** aus, überprüfen Sie die Optionen im Dialogfeld **Optionen** , und klicken Sie dann auf die Schaltfläche **OK** .

13. Wählen Sie die Schaltfläche **Jetzt veröffentlichen** aus.

     Visual Studio fügt dem Veröffentlichungsordner die folgenden Ordner und Dateien hinzu, die Sie zuvor in dieser Prozedur angegeben haben.

    - Der Ordner " **Anwendungs Dateien** ".

    - Das Setupprogramm.

    - Ein Bereitstellungsmanifest, das auf das Bereitstellungsmanifest der neuesten Version verweist.

      Der Ordner **Anwendungs Dateien** enthält einen Unterordner für jede Version, die Sie veröffentlichen. Jeder versionsspezifische Unterordner enthält die folgenden Dateien.

    - Ein Anwendungsmanifest.

    - Ein Bereitstellungsmanifest.

    - Anpassungsassemblys.

      Die folgende Abbildung zeigt die Struktur des Veröffentlichungsordners für ein Outlook VSTO-Add-In.

      ![Struktur des Veröffentlichungs Ordners](../vsto/media/publishfolderstructure.png "Struktur des Veröffentlichungsordners")

    > [!NOTE]
    > ClickOnce fügt die Erweiterung *.* Bereitstellungs Erweiterung an Assemblys an, damit eine gesicherte Installation von Internetinformationsdienste (IIS) die Dateien aufgrund einer unsicheren Erweiterung nicht blockiert. Wenn der Benutzer die Projekt Mappe installiert, entfernt ClickOnce die Erweiterung *.* Bereitstellung.

14. Kopieren Sie die Projektmappendateien an den Installationspfad, den Sie zuvor in dieser Prozedur angegeben haben.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> Entscheiden Sie, wie Sie der Projekt Mappe Vertrauenswürdigkeit gewähren möchten.
 Bevor eine Projektmappe auf Benutzercomputern ausgeführt werden kann, müssen Sie entweder Vertraulichkeit gewähren, oder Benutzer müssen auf eine vertrauenswürdige Eingabeaufforderung antworten, wenn Sie die Projektmappe installieren. Um der Projektmappe Vertraulichkeit zu gewähren, signieren Sie die Manifeste, indem Sie ein Zertifikat verwenden, das einen bekannten und vertrauenswürdigen Herausgeber identifiziert. Weitere Informationen finden Sie [unter durch Signieren der Anwendungs-und Bereitstellungs Manifeste](../vsto/granting-trust-to-office-solutions.md#Signing).

 Wenn Sie eine Anpassung auf Dokument Ebene bereitstellen und das Dokument in einem Ordner auf dem Computer des Benutzers ablegen oder auf einer SharePoint-Website verfügbar machen möchten, müssen Sie sicherstellen, dass Office dem Speicherort des Dokuments vertraut. Siehe [Erteilen von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> Helfen Sie Benutzern bei der Installation der Lösung
 Benutzer können die Projekt Mappe installieren, indem Sie das-Setup Programm ausführen, das Bereitstellungs Manifest öffnen oder während der Anpassung auf Dokument Ebene das Dokument direkt öffnen. Als empfohlene Vorgehensweise sollten Benutzer die Projektmappe mithilfe des Setupprogramms installieren. Bei den anderen beiden Ansätzen wird nicht sichergestellt, dass die erforderliche Software installiert ist. Wenn Benutzer das Dokument vom Installationspfad öffnen möchten, müssen sie ihn der Liste vertrauenswürdiger Speicherorte im Sicherheitscenter der Office-Anwendung hinzufügen.

### <a name="opening-the-document-of-a-document-level-customization"></a>Öffnen des Dokuments einer Anpassung auf Dokumentebene
 Benutzer können das Dokument einer Anpassung auf Dokumentebene direkt vom Installationspfad öffnen, oder indem Sie das Dokument auf den lokalen Computer kopieren und dann die Kopie öffnen.

 Empfohlen wird, dass Benutzer eine Kopie des Dokuments auf ihrem Computer öffnen, damit nicht mehrere Benutzer gleichzeitig versuchen, die gleiche Kopie zu öffnen. Um diese Methode zu erzwingen, können Sie das Setupprogramm so konfigurieren, dass das Dokument auf die Benutzercomputer kopiert wird. Weitere Informationen finden Sie [unter ablegen des Dokuments einer Projekt Mappe auf dem Computer des Endbenutzers (nur Anpassungen auf Dokument Ebene)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installieren der Lösung durch Öffnen des Bereitstellungs Manifests von einer IIS-Website
 Benutzer können eine Office-Projektmappe installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Eine gesicherte Installation von Internetinformationsdienste (IIS) blockiert jedoch Dateien mit der Erweiterung " *. VSTO* ". Der MIME-Typ muss in IIS definiert werden, bevor Sie Office-Projektmappen mithilfe von IIS bereitstellen können.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>So fügen Sie den .vsto-MIME-Typ zu IIS 6.0 hinzu

1. Wählen Sie auf dem Server, auf dem IIS 6,0 ausgeführt wird, **Start**  >  **Alle Programme**  >  **Verwaltungs Tools**  >   **Internetinformationsdienste (IIS)-Manager** aus.

2. Wählen Sie den Computernamen, **den Ordner "Websites"** oder die Website aus, die Sie konfigurieren.

3. Wählen Sie in der Menüleiste **Aktions**  >  **Eigenschaften** aus.

4. Wählen Sie auf der Registerkarte **http-Header** die Schaltfläche **MIME-Typen** aus.

5. Wählen Sie im Fenster **MIME-Typen** die Schaltfläche **neu** aus.

6. Geben Sie im Fenster **MIME-Typ** als Erweiterung **. VSTO** ein, geben Sie **Application/x-ms-VSTO** als MIME-Typ ein, und wenden Sie dann die neuen Einstellungen an.

    > [!NOTE]
    > Damit die Änderungen wirksam werden, müssen Sie den WWW-Publishingdienst neu starten oder abwarten, bis der Arbeitsprozess wiederverwendet wird. Anschließend müssen Sie den Datenträger Cache des Browsers leeren und dann erneut versuchen, die *VSTO* -Datei zu öffnen.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>So fügen Sie den .vsto-MIME-Typ zu IIS 7,0 hinzu

1. Wählen Sie auf dem Server, auf dem IIS 7,0 ausgeführt wird, **Start**  >  **Alle Programme**  >  **Zubehör** aus.

2. Öffnen Sie das Kontextmenü für die **Eingabeaufforderung**, und wählen Sie dann  **als Administrator ausführen aus.**

3. Geben Sie im Feld **Öffnen** den folgenden Pfad ein, und klicken Sie dann auf die Schaltfläche **OK** .

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Geben Sie den folgenden Befehl ein, und wenden Sie dann die neuen Einstellungen an.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Damit die Änderungen wirksam werden, müssen Sie den WWW-Publishingdienst neu starten oder abwarten, bis der Arbeitsprozess wiederverwendet wird. Anschließend müssen Sie den Datenträger Cache des Browsers leeren und dann erneut versuchen, die *VSTO* -Datei zu öffnen.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> Speichern des Dokuments einer Projekt Mappe auf dem Computer des Endbenutzers (nur Anpassungen auf Dokument Ebene)
 Sie können das Dokument der Projekt Mappe auf den Computer des Endbenutzers kopieren, indem Sie eine Aktion nach der Bereitstellung erstellen. Auf diese Weise muss der Benutzer das Dokument nicht manuell vom Installations Speicherort auf den Computer kopieren, nachdem Sie die Lösung installiert haben. Sie müssen eine Klasse erstellen, die die Aktion nach der Bereitstellung definiert, die Projekt Mappe erstellen und veröffentlichen, das Anwendungs Manifest ändern und das Anwendungs-und Bereitstellungs Manifest neu signieren.

 Bei den folgenden Prozeduren wird davon ausgegangen, dass der Projektname **ExcelWorkbook** ist und Sie die Projekt Mappe in einem erstellten Ordner namens **c:\publish** auf Ihrem Computer veröffentlichen.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Erstellen einer Klasse, in der die Aktion nach der Bereitstellung definiert wird

1. Wählen Sie in der Menüleiste **Datei**  >  **Hinzufügen**  >  **Neues Projekt** aus.

2. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** im Bereich **installierte Vorlagen** den Ordner **Windows** aus.

3. Wählen Sie im Bereich **Vorlagen** die Vorlage **Klassenbibliothek** aus.

4. Geben Sie im Feld **Name den Namen** **FileCopyPDA** ein, und klicken Sie dann auf die Schaltfläche **OK** .

5. Wählen Sie in **Projektmappen-Explorer** das Projekt **FileCopyPDA** aus.

6. Wählen Sie in der Menüleiste die Optionen **Projekt** > **Verweis hinzufügen** aus.

7. Fügen Sie auf der Registerkarte **.net** Verweise auf `Microsoft.VisualStudio.Tools.Applications.Runtime` und hinzu `Microsoft.VisualStudio.Tools.Applications.ServerDocument` .

8. Benennen Sie die Klasse in `FileCopyPDA` um, und ersetzen Sie den Inhalt der Datei durch den Code. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Kopieren des Dokuments auf den Desktop des Benutzers.

   - Ändert die _AssemblyLocation-Eigenschaft von einem relativen Pfad zu einem voll qualifizierten Pfad für das Bereitstellungs Manifest.

   - Löschen der Datei, wenn der Benutzer die Projektmappe deinstalliert.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Erstellen und Veröffentlichen der Projektmappe

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **FileCopyPDA** , und wählen Sie dann **Erstellen** aus.

2. Öffnen Sie das Kontextmenü für das Projekt **ExcelWorkbook** , und wählen Sie dann **Erstellen** aus.

3. Öffnen Sie das Kontextmenü für das Projekt **ExcelWorkbook** , und wählen Sie dann **Verweis hinzufügen** aus.

4. Wählen Sie im Dialogfeld **Verweis hinzufügen** die Registerkarte **Projekte** aus, wählen Sie **FileCopyPDA** aus, und klicken Sie dann auf die Schaltfläche **OK** .

5. Wählen Sie in **Projektmappen-Explorer** das Projekt **ExcelWorkbook** aus.

6. Wählen Sie in der Menüleiste die Option **Projekt**  >  **neuer Ordner** aus.

7. Geben Sie **Daten** ein, und drücken Sie dann die **Eingabe** Taste.

8. Wählen Sie in **Projektmappen-Explorer** den Ordner **Data** aus.

9. Wählen Sie in der Menüleiste die Option **Projekt**  >  **Vorhandenes Element hinzufügen** aus.

10. Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zum Ausgabeverzeichnis für das Projekt **ExcelWorkbook** , wählen Sie die Datei **ExcelWorkbook.xlsx** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

11. Wählen Sie in **Projektmappen-Explorer** die **ExcelWorkbook.xlsx** Datei aus.

12. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **Buildaktion** in **Inhalt** und die Eigenschaft in **Ausgabeverzeichnis kopieren** in **kopieren, wenn neuer**.

     Wenn Sie diese Schritte ausgeführt haben, ähnelt das Projekt der folgenden Abbildung.

     ![Projektstruktur für die Aktion nach der Bereitstellung.](../vsto/media/vsto-postdeployment.png "Projektstruktur für die Aktion nach der Bereitstellung.")

13. Veröffentlichen Sie das Projekt **ExcelWorkbook** .

### <a name="modify-the-application-manifest"></a>Ändern des Anwendungsmanifests

1. Öffnen Sie das Projektmappenverzeichnis **c:\publish**, indem Sie den **Datei-Explorer** verwenden.

2. Öffnen Sie den Ordner **Anwendungs Dateien** , und öffnen Sie dann den Ordner, der der neuesten veröffentlichten Version der Lösung entspricht.

3. Öffnen Sie die Datei **ExcelWorkbook.dll. Manifest** in einem Text-Editor wie z. b. Notepad.

4. Fügen Sie nach dem `</vstav3:update>`-Element den folgenden Code ein. Verwenden Sie für das Class-Attribut des- `<vstav3:entryPoint>` Elements die folgende Syntax: *Namespace Name. ClassName*. Im folgenden Beispiel sind der Namespace und die Klassennamen gleich, sodass der Name des resultierenden Einstiegspunkts `FileCopyPDA.FileCopyPDA` lautet.

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>Erneutes Signieren der Anwendungs- und Bereitstellungsmanifeste

1. Kopieren Sie im Ordner **%USERPROFILE%\Documents\Visual Studio 2013 \ project\excelworkbook\excelworkbook** die Zertifikat Datei **ExcelWorkbook_TemporaryKey. pfx** , und fügen Sie Sie in den Ordner *publishfolder* **\anwendungsdateien\excelarbeitsmappe** Ordner " \_ _fistrecentpublishedversion_ " ein.

2. Öffnen Sie die Visual Studio-Eingabeaufforderung, und ändern Sie dann die Verzeichnisse in den Ordner **c:\publish\anwendungsdateien\excelarbeitsmappe** \_  (z. b. **c:\publish\anwendungsdateien \ ExcelWorkbook_1_0_0_4**).

3. Signieren Sie das geänderte Anwendungsmanifest, indem Sie den folgenden Befehl ausführen:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Die Meldung "ExcelWorkbook.dll.manifest erfolgreich signiert" wird angezeigt.

4. Wechseln Sie zum Ordner **c:\publish** , und aktualisieren und Signieren Sie das Bereitstellungs Manifest, indem Sie den folgenden Befehl ausführen:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Ersetzen Sie im vorherigen Beispiel "mustrecentversionnumber" durch die Versionsnummer der zuletzt veröffentlichten Version der Lösung (z. b. **1_0_0_4**).

     Die Meldung "ExcelWorkbook.vsto erfolgreich signiert" wird angezeigt.

5. Kopieren Sie die Datei " *ExcelWorkbook. VSTO* " in das Verzeichnis " **c:\publish\Application files\excelworkbook**" \_  .

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a> Speichern des Dokuments einer Projekt Mappe auf einem Server, auf dem SharePoint ausgeführt wird (nur Anpassungen auf Dokument Ebene)
 Sie können die Anpassung auf Dokumentebene für Endbenutzer mithilfe von SharePoint veröffentlichen. Wenn Benutzer die SharePoint-Site aufrufen und das Dokument öffnen, installiert die Laufzeit automatisch die Projektmappe aus dem freigegebenen Netzwerkordner auf den lokalen Computer des Benutzers. Nachdem die Projektmappe lokal installiert wurde, funktioniert die Anpassung sogar dann, wenn das Dokument an eine andere Stelle kopiert wird, z. B. auf den Desktop.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>So kopieren Sie das Dokument auf einen Server, auf dem SharePoint ausgeführt wird

1. Fügen Sie das Projektmappendokument einer Dokumentbibliothek auf einer SharePoint-Site hinzu.

2. Führen Sie die Schritte für eines der folgenden Verfahren aus:

    - Fügen Sie mit dem Office-Konfigurationstool den Server, auf dem SharePoint ausgeführt wird, auf allen Benutzercomputern dem Sicherheitscenter in Word oder Excel hinzu.

         Weitere Informationen finden Sie [unter Sicherheitsrichtlinien und Einstellungen in Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Stellen Sie sicher, dass jeder Benutzer die folgenden Schritte ausführt.

        1. Öffnen Sie auf dem lokalen Computer Word oder Excel, wählen Sie die Registerkarte **Datei** aus, und klicken Sie dann auf die Schaltfläche **Optionen** .

        2. Wählen Sie im Dialogfeld **Trust Center** die Schaltfläche **Vertrauenswürdige Speicherorte** aus.

        3. Aktivieren Sie das Kontrollkästchen **Vertrauenswürdige Speicherorte im Netzwerk zulassen (nicht empfohlen)** , und wählen Sie dann die Schaltfläche **neuen Speicherort hinzufügen** aus.

        4. Geben Sie im Feld **Pfad** die URL der SharePoint-Dokumentbibliothek ein, die das Dokument enthält, das Sie hochgeladen haben (z *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* . b.).

             Fügen Sie nicht den Namen der Standard Webseite hinzu, z. b. *default. aspx* oder *AllItems. aspx*.

        5. Aktivieren Sie das Kontrollkästchen **Unterordner dieses Speicher Orts sind ebenfalls vertrauenswürdig** , und klicken Sie dann auf die Schaltfläche **OK** .

             Wenn Benutzer das Dokument von der SharePoint-Site öffnen, wird das Dokument geöffnet, und die Anpassung wird installiert. Benutzer können das Dokument auf den Desktop kopieren. Die Anpassung wird nach wie vor ausgeführt, da Eigenschaften im Dokument auf den Netzwerkspeicherort des Dokuments verweisen.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> Erstellen eines benutzerdefinierten Installers
 Sie können ein benutzerdefiniertes Installationsprogramm für Ihre Office-Projekt Mappe erstellen, anstatt das Setup Programm zu verwenden, das beim Veröffentlichen der Lösung für Sie erstellt wurde. Beispielsweise können Sie ein Anmelde Skript verwenden, um die Installation zu starten, oder Sie können eine Batchdatei verwenden, um die Lösung ohne Benutzerinteraktion zu installieren. Diese Szenarios funktionieren am besten, wenn die erforderlichen Komponenten bereits auf den Endbenutzercomputern installiert sind.

 Nennen Sie als Teil des benutzerdefinierten Installationsvorgangs das Installations Tool für Office-Projektmappen (*VSTOInstaller.exe*), das standardmäßig an folgendem Speicherort installiert ist:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Wenn sich das Tool nicht an diesem Speicherort befindet, können Sie die **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** oder **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** Registrierungsschlüssel verwenden, um den Pfad zu diesem Tool zu suchen.

 Mit *VSTOinstaller.exe* können Sie die folgenden Parameter verwenden.

| Parameter | Definition |
|------------------| - |
| /Install oder /I | Installation der Projektmappe. Dieser Option muss der Pfad eines Bereitstellungsmanifests folgen. Sie können einen Pfad auf dem lokalen Computer angeben, eine Universal Naming Convention (UNC)-Dateifreigabe. Sie können einen lokalen Pfad (*c:\ordnername\publishfolder*), einen relativen Pfad (*Publish \\*) oder einen voll qualifizierten Speicherort (*\\ \servername\foldername* oder http://<em>Servername/FolderName</em>) angeben. |
| /Uninstall oder /U | Deinstallation der Projektmappe. Dieser Option muss der Pfad eines Bereitstellungsmanifests folgen. Sie können einen Pfad auf dem lokalen Computer, eine UNC-Dateifreigabe, angeben. Sie können einen lokalen Pfad (*c:\ordnername\publishfolder*), einen relativen Pfad (*Publish \\*) oder einen voll qualifizierten Speicherort (*\\ \servername\foldername* oder http://<em>Servername/FolderName</em>) angeben. |
| /Silent oder /S | Installation bzw. Deinstallation, ohne dass der Benutzer zu einer Eingabe aufgefordert wird oder Meldungen angezeigt werden. Wenn eine Vertrauensstellungs Aufforderung erforderlich ist, wird die Anpassung nicht installiert oder aktualisiert. |
| /Help oder /? | Anzeigen der Hilfeinformationen. |

 Wenn Sie *VSTOinstaller.exe* ausführen, werden möglicherweise die folgenden Fehlercodes angezeigt.

|Fehlercode|Definition|
|----------------|----------------|
|0|Die Projektmappe wurde erfolgreich installiert oder deinstalliert, oder die VSTOInstaller-Hilfe wurde angezeigt.|
|-100|Mindestens eine Befehlszeilenoption ist ungültig oder wurde mehrmals festgelegt. Weitere Informationen erhalten Sie, wenn Sie "VSTOInstaller/?" eingeben. oder siehe [Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Office](/previous-versions/bb772078(v=vs.110))-Projekt Mappe.|
|-101|Mindestens eine Befehlszeilenoption ist ungültig. Weitere Informationen erhalten Sie, indem Sie "vstoinstaller/?" eingeben.|
|-200|Der URI des Bereitstellungs Manifests ist ungültig. Weitere Informationen erhalten Sie, indem Sie "vstoinstaller/?" eingeben.|
|-201|Die Projekt Mappe konnte nicht installiert werden, da das Bereitstellungs Manifest ungültig ist. Siehe [Bereitstellungs Manifeste für Office](../vsto/deployment-manifests-for-office-solutions.md)-Projektmappen.|
|-202|Die Projekt Mappe konnte nicht installiert werden, da der Visual Studio-Tools für Office-Abschnitt des Anwendungs Manifests nicht gültig ist. Siehe [Anwendungs Manifeste für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen.|
|-203|Die Lösung konnte aufgrund eines Download Fehlers nicht installiert werden. Überprüfen Sie den URI bzw. den Netzspeicherort des Bereitstellungsmanifests, und versuchen Sie es erneut.|
|-300|Die Projekt Mappe konnte nicht installiert werden, da eine Sicherheits Ausnahme aufgetreten ist. Siehe [sichere Office-Lösungen](../vsto/securing-office-solutions.md).|
|-400|Die Projekt Mappe konnte nicht installiert werden.|
|-401|Die Lösung konnte nicht deinstalliert werden.|
|-500|Der Vorgang wurde abgebrochen, da die Projektmappe nicht installiert oder deinstalliert oder das Bereitstellungsmanifest nicht heruntergeladen werden konnte.|

## <a name="publish-an-update"></a><a name="Update"></a> Veröffentlichen eines Updates
 Um eine Projekt Mappe zu aktualisieren, veröffentlichen Sie Sie erneut mit dem **Projekt-Designer** oder dem Veröffentlichungs- **Assistenten**. anschließend kopieren Sie die aktualisierte Projekt Mappe an den Installations Speicherort. Wenn Sie die Dateien an den Installationsort kopieren, müssen Sie die älteren Dateien überschreiben.

 Wenn die Projekt Mappe das nächste Mal nach einem Update sucht, wird die neue Version automatisch gefunden und geladen.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> Ändern des Installations Speicher Orts einer Projekt Mappe
 Sie können den Installationspfad hinzufügen oder ändern, nachdem eine Projektmappe veröffentlicht wurde. Eine Änderung des Installationspfads kann aus einem oder mehreren der folgenden Gründe erforderlich werden:

- Das Setupprogramm wurde kompiliert, bevor der Installationspfad bekannt war.

- Die Projektmappendateien wurden an einen anderen Speicherort kopiert.

- Der Server, auf dem die Installationsdateien gehostet werden, hat einen neuen Namen oder einen neuen Speicherort.

  Um den Installationspfad einer Projektmappe zu ändern, müssen Sie das Setupprogramm aktualisieren, das dann von den Benutzern ausgeführt werden muss. Bei Anpassungen auf Dokumentebene müssen Benutzer außerdem eine Eigenschaft in dem Dokument aktualisieren, das auf den neuen Speicherort verweist.

> [!NOTE]
> Wenn Sie Benutzer nicht auffordern möchten, ihre Dokumenteigenschaften zu aktualisieren, können Sie die Benutzer auffordern, das aktualisierte Dokument vom Installations Speicherort zu erhalten.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>So ändern Sie den Installationspfad im Setupprogramm

1. Öffnen Sie ein **Eingabe** Aufforderungs Fenster, und wechseln Sie dann in den-Installationsordner.

2. Führen Sie das Setupprogramm aus, und geben Sie den `/url`-Parameter an, der den neuen Installationspfad als Zeichenfolge entgegennimmt.

    Das folgende Beispiel zeigt, wie der Installationspfad auf einen Speicherort auf der Fabrikam-Website geändert wird; Sie können diese URL durch den gewünschten Pfad ersetzen:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Wenn eine Meldung angezeigt wird, dass die Signatur der ausführbaren Datei ungültig gemacht wird, ist das Zertifikat, das zum Signieren der Projektmappe verwendet wurde, nicht mehr gültig, und der Herausgeber ist unbekannt. In diesem Fall müssen Benutzer bestätigen, dass die Quelle der Projektmappe vertrauenswürdig ist, bevor sie sie installieren können.

   > [!NOTE]
   > Um den aktuellen Wert der URL anzuzeigen, führen Sie `setup.exe /url` aus.

   Für Anpassungen auf Dokument Ebene müssen Benutzer das Dokument öffnen und dann die _AssemblyLocation-Eigenschaft aktualisieren. Die folgenden Schritte beschreiben, wie Benutzer diese Aufgabe ausführen können.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>So aktualisieren Sie die _AssemblyLocation-Eigenschaft in einem Dokument

1. Wählen Sie auf der Registerkarte **Datei** die Option **Info** aus, die in der folgenden Abbildung gezeigt wird.

     ![Registerkarte "Informationen" in Excel](../vsto/media/vsto-infotab.png "Registerkarte "Informationen" in Excel")

2. Wählen Sie in der Liste **Eigenschaften** die Option **Erweiterte Eigenschaften** aus, die in der folgenden Abbildung dargestellt sind.

     !["Erweiterte Eigenschaften" in Excel.](../vsto/media/vsto-advanceddocumentproperties.png ""Erweiterte Eigenschaften" in Excel.")

3. Wählen Sie auf der Registerkarte **Benutzer** definiert in der Liste **Eigenschaften** _AssemblyLocation aus, wie in der folgenden Abbildung dargestellt.

     ![Die AssemblyLocation-Eigenschaft.](../vsto/media/vsto-assemblylocationproperty.png "Die AssemblyLocation-Eigenschaft.")

     Das Feld **Wert** enthält den Bezeichner des Bereitstellungs Manifests.

4. Geben Sie vor dem Bezeichner den voll qualifizierten Pfad des Dokuments ein, gefolgt von einem Balken im Format *Pfad* | *Bezeichner* (z. b. *file://servername/foldername/filename|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*).

     Weitere Informationen zum Formatieren dieses Bezeichners finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](../vsto/custom-document-properties-overview.md).

5. Wählen Sie die Schaltfläche **OK** aus, und speichern und schließen Sie dann das Dokument.

6. Führen Sie das Setupprogramm ohne den /url-Parameter aus, um die Projektmappe am angegebenen Speicherort zu installieren.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> Ausführen eines Rollbacks für eine Lösung auf eine frühere Version
 Wenn Sie eine Projektmappe zurücksetzen, stellen Sie die Benutzer wieder auf eine frühere Version der Projektmappe um.

#### <a name="to-roll-back-a-solution"></a>So setzen Sie eine Projektmappe zurück

1. Öffnen Sie den Installationspfad der Projektmappe.

2. Löschen Sie im Veröffentlichungs Ordner der obersten Ebene das Bereitstellungs Manifest (die *VSTO* -Datei).

3. Suchen Sie nach dem Unterordner für die Version, auf die Sie die Datei zurücksetzen möchten.

4. Kopieren Sie das Bereitstellungsmanifest aus diesem Unterordner in den Veröffentlichungsordner der obersten Ebene.

     Wenn Sie z. b. ein Rollback für eine Projekt Mappe ausführen möchten, die von Version 1.0.0.1 auf Version 1.0.0.0 als **OutlookAddIn1** bezeichnet wird, kopieren Sie die Datei **OutlookAddin1. VSTO** aus dem Ordner **OutlookAddIn1_1_0_0_0** . Fügen Sie die Datei in den Veröffentlichungs Ordner der obersten Ebene ein, und überschreiben Sie das versionsspezifische Bereitstellungs Manifest für **OutlookAddIn1_1_0_0_1** , das bereits vorhanden war.

     Die folgende Abbildung zeigt die Struktur des Veröffentlichungsordners in diesem Beispiel.

     ![Struktur des Veröffentlichungs Ordners](../vsto/media/publishfolderstructure.png "Struktur des Veröffentlichungsordners")

     Wenn ein Benutzer das nächste Mal die Anwendung oder das benutzerdefinierte Dokument öffnet, wird die Änderung des Bereitstellungsmanifests erkannt. Die frühere Version der Office-Projektmappe wird vom ClickOnce-Cache ausgeführt.

> [!NOTE]
> Lokale Daten werden für nur eine vorherige Version einer Projektmappe gespeichert. Wenn Sie ein Rollback für zwei Versionen ausführen, werden lokale Daten nicht beibehalten. Weitere Informationen zu lokalen Daten finden Sie unter [zugreifen auf lokale und Remote Daten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Weitere Informationen

- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Veröffentlichen von Office-Lösungen](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Gewusst wie: Veröffentlichen einer Office-Projekt Mappe mit ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Gewusst wie: Installieren einer ClickOnce-Office-Projekt Mappe](/previous-versions/bb608592(v=vs.110))
- [Gewusst wie: Veröffentlichen einer Office-Projekt Mappe auf Dokument Ebene auf einem SharePoint-Server mithilfe von ClickOnce](/previous-versions/bb608595(v=vs.110))
- [Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Office-Projekt Mappe](/previous-versions/bb772078(v=vs.110))