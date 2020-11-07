---
title: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutz-Eingabeaufforderung
description: Erfahren Sie, wie Sie ClickOnce-Anwendungen für die automatische Aktualisierung konfigurieren, wenn Assemblys mit neueren Dateiversionen und Assemblyversionen verfügbar werden
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06effb313dc2b8a247eeeab99290a289717bc960
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350464"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutz-Eingabeaufforderung
Sie können ClickOnce-Anwendungen so konfigurieren, dass Sie automatisch aktualisiert werden, wenn Assemblys mit neueren Dateiversionen und Assemblyversionen verfügbar Um sicherzustellen, dass Ihre Kunden diesem Verhalten zustimmen, können Sie Ihnen eine Datenschutz Aufforderung anzeigen. Anschließend können Sie auswählen, ob Sie der Anwendung die Berechtigung zum automatischen Aktualisieren gewähren möchten. Wenn die Anwendung nicht automatisch aktualisiert werden kann, wird Sie nicht installiert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Dialogfeld "Zustimmung aktualisieren" erstellen
 Um eine Datenschutz Aufforderung anzuzeigen, erstellen Sie eine Anwendung, in der der Leser aufgefordert wird, automatische Updates für die Anwendung zuzustimmen.

#### <a name="to-create-a-consent-dialog-box"></a>So erstellen Sie ein Zustimmungs Dialogfeld

1. Zeigen Sie im Menü **Datei** auf **Neu** , und klicken Sie dann auf **Projekt**.

2. Klicken Sie im Dialogfeld **Neues Projekt** auf **Fenster** , und klicken Sie dann auf **windowsformsapplication**.

3. Geben Sie als **Name den Namen** " **Zustimmung Dialog** " ein, und klicken Sie dann auf **OK**.

4. Klicken Sie im Designer auf das Formular.

5. Ändern Sie im **Eigenschaften** Fenster die Text-Eigenschaft in das Dialog **Feld** zum **Aktualisieren der Zustimmung**.

6. Erweitern Sie **Toolbox** in der Toolbox **alle Windows Forms** , und ziehen Sie ein **Label** -Steuerelement auf das Formular.

7. Klicken Sie im Designer auf das Label-Steuerelement.

8. Ändern Sie im **Eigenschaften** Fenster die **Text** - **Eigenschaft unter Darstellung** wie folgt:

    Die Anwendung, die Sie installieren möchten, prüft auf die neuesten Updates im Web. Wenn Sie auf "Ich stimme zu" klicken, autorisieren Sie die Anwendung für die automatische Überprüfung und Installation von Updates über das Internet.

9. Ziehen Sie in der **Toolbox** ein **CheckBox** -Steuerelement in die Mitte des Formulars.

10. Ändern Sie im **Eigenschaften** Fenster die **Text** -Eigenschaft unter **Layout** in **Ich stimme** zu.

11. Ziehen Sie in der **Toolbox** ein **Schalt** Flächen-Steuerelement in die linke untere Ecke des Formulars.

12. Ändern Sie im **Eigenschaften** Fenster die **Text** -Eigenschaft unter **Layout** , um **fortzufahren**.

13. Ändern Sie im **Eigenschaften** Fenster die **(Name)** -Eigenschaft unter **Entwurf** in **proceedbutton**.

14. Ziehen Sie in der **Toolbox** ein **Schalt** Flächen-Steuerelement in die untere rechte Ecke des Formulars.

15. Ändern Sie im **Eigenschaften** Fenster die **Text** -Eigenschaft unter **Layout** in **Abbrechen**.

16. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **(Name)** unter **Entwurf** in **CancelButton**.

17. Doppelklicken Sie im Designer auf das Kontrollkästchen **Ich stimme** zu, um den CheckedChanged-Ereignishandler zu generieren.

18. Fügen Sie in der Form1-Codedatei den folgenden Code für den CheckedChanged-Ereignishandler hinzu.

     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]

19. Aktualisieren Sie den Klassenkonstruktor, um die Schaltfläche **fortfahren** standardmäßig zu deaktivieren.

     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]

20. Fügen Sie in der Form1-Codedatei den folgenden Code für eine boolesche Variable hinzu, um nachverfolgen zu können, ob der Endbenutzer den Online Updates zugestimmt hat.

     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]

21. Doppelklicken Sie im Designer auf die Schaltfläche " **weiter** ", um den Click-Ereignishandler zu generieren.

22. Fügen Sie in der Form1-Codedatei dem Click-Ereignishandler für die Schaltfläche " **weiter** " den folgenden Code hinzu.

     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]

23. Doppelklicken Sie im Designer auf die Schaltfläche **Abbrechen** , um den Click-Ereignishandler zu generieren.

24. Fügen Sie in der Form1-Codedatei den folgenden Code für den Click-Ereignishandler für die Schaltfläche **Abbrechen** hinzu.

     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]

25. Aktualisieren Sie die Anwendung so, dass ein Fehler zurückgegeben wird, wenn der Endbenutzer keine Online Updates zustimmt.

     Nur für Visual Basic-Entwickler:

    1. Klicken Sie in **Projektmappen-Explorer** auf das Dialogfeld " **Zustimmung** ".

    2. Klicken Sie im Menü **Projekt** auf **Modul hinzufügen** , und klicken Sie dann auf **Hinzufügen**.

    3. Fügen Sie in der Codedatei " *Module1. vb* " den folgenden Code hinzu.

        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]

    4. Klicken Sie im Menü **Projekt** auf die Registerkarte **Eigenschaften** , und klicken Sie dann auf die Registerkarte **Anwendung** .

    5. Deaktivieren Sie **Anwendungs Framework aktivieren**.

    6. Wählen Sie im Dropdown Menü **Start Objekt** die Option **Module1** aus.

       > [!NOTE]
       > Durch die Deaktivierung des Anwendungs Frameworks werden Features wie visuelle Windows XP-Stile, Anwendungs Ereignisse, Begrüßungsbildschirm, Einzelinstanzanwendungen und vieles mehr deaktiviert. Weitere Informationen finden Sie unter [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Nur für Visual c#-Entwickler:

       Öffnen Sie die *Program.cs* -Codedatei, und fügen Sie den folgenden Code hinzu.

       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]

26. Klicken Sie im Menü **Erstellen** auf **BUILDSOLUTION**.

## <a name="create-the-custom-bootstrapper-package"></a>Erstellen des benutzerdefinierten Bootstrapperpakets
 Zum Anzeigen der Datenschutz-Eingabeaufforderung für Endbenutzer können Sie ein benutzerdefiniertes Bootstrapperpaket für die Anwendung zum Aktualisieren der Zustimmung erstellen und als erforderliche Komponente für alle Ihre ClickOnce-Anwendungen einschließen.

 In diesem Verfahren wird veranschaulicht, wie Sie ein benutzerdefiniertes Bootstrapperpaket erstellen, indem Sie die folgenden Dokumente erstellen:

- Eine *product.xml* Manifest-Datei, um den Inhalt des Boots Trappers zu beschreiben.

- Eine *package.xml* Manifest-Datei zum Auflisten der Lokalisierungs spezifischen Aspekte Ihres Pakets, z. b. Zeichen folgen und die Software Lizenzbedingungen.

- Ein Dokument für die Software-Lizenzbedingungen.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Schritt 1: So erstellen Sie das Bootstrapperverzeichnis

1. Erstellen Sie ein Verzeichnis mit dem Namen **updateconsentdialog** in *%ProgramFiles%\Microsoft SDKs\Windows\v7.0a\bootstrapper\packages*.

    > [!NOTE]
    > Möglicherweise benötigen Sie Administratorrechte, um diesen Ordner zu erstellen.

2. Erstellen Sie im Verzeichnis *updateconsentdialog* ein Unterverzeichnis mit dem Namen *en*.

    > [!NOTE]
    > Erstellen Sie ein neues Verzeichnis für jedes Gebiets Schema. Beispielsweise können Sie Unterverzeichnisse für die Gebiets Schemas "fr" und "de" hinzufügen. Diese Verzeichnisse enthalten bei Bedarf die Zeichen folgen und Sprachpakete von Französisch und Deutsch.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Schritt 2: So erstellen Sie die product.xml Manifest-Datei

1. Erstellen Sie eine Textdatei mit dem Namen *product.xml*.

2. Fügen Sie in der *product.xml* -Datei den folgenden XML-Code hinzu. Stellen Sie sicher, dass Sie den vorhandenen XML-Code nicht überschreiben.

    ```xml
    <Product
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      ProductCode="Microsoft.Sample.EULA">
      <!-- Defines the list of files to be copied on build. -->
      <PackageFiles CopyAllPackageFiles="false">
        <PackageFile Name="ConsentDialog.exe"/>
      </PackageFiles>

      <!-- Defines how to run the Setup package.-->
      <Commands >
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>
          <ExitCodes>
            <ExitCode Value="0" Result="Success" />
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />
            <DefaultExitCode Result="Fail"
              FormatMessageFromSystem="true" String="GeneralFailure" />
          </ExitCodes>
        </Command>
      </Commands>

    </Product>
    ```

3. Speichern Sie die Datei im Verzeichnis updateconsentdialog Boots Trapper.

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Schritt 3: So erstellen Sie die package.xml Manifest-Datei und die Software-Lizenzbedingungen

1. Erstellen Sie eine Textdatei mit dem Namen *package.xml*.

2. Fügen Sie in der *package.xml* -Datei den folgenden XML-Code hinzu, um das Gebiets Schema zu definieren und die Software Lizenzbedingungen einzubeziehen. Stellen Sie sicher, dass Sie den vorhandenen XML-Code nicht überschreiben.

    ```xml
    <Package
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      Name="DisplayName"
      Culture="Culture"
      LicenseAgreement="eula.rtf">
      <PackageFiles>
        <PackageFile Name="eula.rtf"/>
      </PackageFiles>

      <!-- Defines a localizable string table for error messages. -->
      <Strings>
        <String Name="DisplayName">Update Consent Dialog</String>
        <String Name="Culture">en</String>
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>
      </Strings>
    </Package>
    ```

3. Speichern Sie die Datei im Unterverzeichnis "en" im Verzeichnis "updateconsentdialog Boots Trapper".

4. Erstellen Sie ein Dokument mit dem Namen *EULA. RTF* für die Software-Lizenzbedingungen.

    > [!NOTE]
    > Die Software Lizenzbedingungen sollten Informationen zu Lizenzierung, Gewährleistungen, Verpflichtungen und lokalen Gesetzen enthalten. Diese Dateien sollten Gebiets Schema spezifisch sein. Stellen Sie daher sicher, dass die Datei in einem Format gespeichert wird, das MBCS-oder Unicode-Zeichen unterstützt. Wenden Sie sich an Ihre Rechtsabteilung über den Inhalt der Software-Lizenzbedingungen.

5. Speichern Sie das Dokument in dem Unterverzeichnis "en" im Verzeichnis " *updateconsentdialog* Boots Trapper".

6. Erstellen Sie ggf. eine neue *package.xml* Manifest-Datei und ein neues Dokument " *EULA. RTF* " für die Software Lizenzbedingungen für jedes Gebiets Schema. Wenn Sie beispielsweise Unterverzeichnisse für die Protokolle "fr" und "de" erstellt haben, erstellen Sie separate package.xml Manifest-Dateien und Software Lizenzbedingungen, und speichern Sie Sie in den Unterverzeichnissen "fr" und "de"

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Festlegen der Anwendung für die Update Zustimmung als erforderliche Komponente
 In Visual Studio können Sie die Anwendung zum Aktualisieren der Zustimmung als erforderliche Komponente festlegen.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>So legen Sie die Update Zustimmungs Anwendung als erforderliche Komponente fest

1. Klicken Sie in **Projektmappen-Explorer** auf den Namen der Anwendung, die Sie bereitstellen möchten.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften** von *ProjectName* .

3. Klicken Sie auf die Seite **veröffentlichen** , und klicken Sie dann auf **Voraussetzungen**.

4. Wählen Sie die Option **Zustimmung aktualisieren** aus.

    > [!NOTE]
    > Möglicherweise müssen Sie Visual Studio schließen und erneut öffnen, um das Dialogfeld "Zustimmung aktualisieren" im Dialogfeld "Voraussetzungen" anzuzeigen.

5. Klicken Sie auf **OK**.

## <a name="create-and-test-the-setup-program"></a>Erstellen und Testen des Setup Programms
 Nachdem Sie die Anwendung zum Aktualisieren der Zustimmung als erforderliche Komponente festgelegt haben, können Sie den Installer und den Boots Trapper für Ihre Anwendung generieren.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>So erstellen und testen Sie das Setup Programm, indem Sie nicht auf Ich stimme zu klicken

1. Klicken Sie in **Projektmappen-Explorer** auf den Namen der Anwendung, die Sie bereitstellen möchten.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften** von *ProjectName* .

3. Klicken Sie auf die Seite **veröffentlichen** , und klicken Sie dann auf **Jetzt veröffentlichen**.

4. Wenn die Veröffentlichungs Ausgabe nicht automatisch geöffnet wird, navigieren Sie zur Veröffentlichungs Ausgabe.

5. Führen Sie das *Setup.exe* Programm aus.

     Das Setup Programm zeigt den Software Lizenzvertrag zum Aktualisieren der Zustimmung.

6. Lesen Sie den Software Lizenzvertrag, und klicken Sie dann auf **akzeptieren**.

     Die Anwendung Update Consent Dialog wird angezeigt und zeigt den folgenden Text an: die Anwendung, die Sie installieren möchten, prüft, ob die neuesten Updates im Web vorhanden sind. Wenn ich auf "Ich stimme zu" klicke, autorisiere ich die Anwendung für die automatische Suche nach Updates im Internet.

7. Schließen Sie die Anwendung, oder klicken Sie auf Abbrechen.

     Die Anwendung zeigt einen Fehler an: Fehler beim Installieren der Systemkomponenten für *ApplicationName*. Setup kann erst fortgesetzt werden, wenn alle Systemkomponenten erfolgreich installiert wurden.

8. Klicken Sie auf Details, um die folgende Fehlermeldung anzuzeigen: das Dialog Feld für die Zustimmung der Komponenten Aktualisierung konnte nicht installiert werden. die folgende Fehlermeldung lautet: "die automatische Update Vereinbarung wird nicht akzeptiert." Fehler beim Installieren der folgenden Komponenten:-Update Zustimmung (Dialog Feld)

9. Klicken Sie auf **Schließen**.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>So erstellen und testen Sie das Setup Programm durch Klicken auf "Ich stimme zu"

1. Klicken Sie in **Projektmappen-Explorer** auf den Namen der Anwendung, die Sie bereitstellen möchten.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften** von *ProjectName* .

3. Klicken Sie auf die Seite **veröffentlichen** , und klicken Sie dann auf **Jetzt veröffentlichen**.

4. Wenn die Veröffentlichungs Ausgabe nicht automatisch geöffnet wird, navigieren Sie zur Veröffentlichungs Ausgabe.

5. Führen Sie das *Setup.exe* Programm aus.

     Das Setup Programm zeigt den Software Lizenzvertrag zum Aktualisieren der Zustimmung.

6. Lesen Sie den Software Lizenzvertrag, und klicken Sie dann auf **akzeptieren**.

     Die Anwendung Update Consent Dialog wird angezeigt und zeigt den folgenden Text an: die Anwendung, die Sie installieren möchten, prüft, ob die neuesten Updates im Web vorhanden sind. Wenn ich auf "Ich stimme zu" klicke, autorisiere ich die Anwendung für die automatische Suche nach Updates im Internet.

7. Klicken Sie auf **Ich stimme** zu, und klicken Sie dann auf **weiter**.

     Die Installation der Anwendung wird gestartet.

8. Wenn das Dialogfeld Anwendungs Installation angezeigt wird, klicken Sie auf **Installieren**.

## <a name="see-also"></a>Weitere Informationen
- [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)
- [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)
- [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md)
- [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md)
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)