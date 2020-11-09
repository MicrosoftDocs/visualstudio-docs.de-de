---
title: Bereitstellen von COM-Komponenten mit ClickOnce | Microsoft-Dokumentation
description: Erfahren Sie mehr über die erforderlichen Schritte zum Bereitstellen von .NET-Anwendungen in ClickOnce mit älteren COM-Komponenten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fc6ef0e4d682f0f712eefc4c139895331c31688
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382922"
---
# <a name="deploy-com-components-with-clickonce"></a>Bereitstellen von COM-Komponenten mit ClickOnce
Die Bereitstellung von Legacy-COM-Komponenten war bisher eine schwierige Aufgabe. Komponenten müssen global registriert werden und können daher unerwünschte Nebeneffekte zwischen überlappenden Anwendungen verursachen. Diese Situation ist in .NET Framework Anwendungen in der Regel kein Problem, da Komponenten vollständig für eine Anwendung isoliert sind oder nebeneinander kompatibel sind. Mit Visual Studio können Sie isolierte COM-Komponenten auf dem Betriebssystem Windows XP oder höher bereitstellen.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bietet einen einfachen und sicheren Mechanismus zum Bereitstellen von .NET-Anwendungen. Wenn in Ihren Anwendungen ältere COM-Komponenten verwendet werden, müssen Sie jedoch zusätzliche Schritte für die Bereitstellung ausführen. In diesem Thema wird beschrieben, wie Sie isolierte COM-Komponenten bereitstellen und auf native Komponenten verweisen (z. b. von Visual Basic 6,0 oder Visual C++).

 Weitere Informationen zum Bereitstellen isolierter COM-Komponenten finden Sie unter [vereinfachen der APP-Bereitstellung mit ClickOnce und Registration-Free com](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).

## <a name="registration-free-com"></a>COM ohne Registrierung
 Com (com) ist eine neue Technologie für die Bereitstellung und Aktivierung isolierter COM-Komponenten. Dabei werden die Typbibliothek-und Registrierungsinformationen aller Komponenten, die in der Regel in der Systemregistrierung installiert werden, in eine XML-Datei, die als Manifest bezeichnet wird, in demselben Ordner wie die Anwendung gespeichert.

 Das Isolieren einer COM-Komponente erfordert, dass Sie auf dem Computer des Entwicklers registriert ist, aber nicht auf dem Computer des Endbenutzers registriert werden muss. Um eine COM-Komponente zu isolieren, müssen Sie lediglich die **isolierte** Eigenschaft des Verweises auf " **true** " festlegen. Standardmäßig ist diese Eigenschaft auf **false** festgelegt, was darauf hinweist, dass Sie als registrierter com-Verweis behandelt werden soll. Wenn diese Eigenschaft auf **true** gesetzt ist, wird zum Zeitpunkt der Erstellung ein Manifest für diese Komponente generiert. Außerdem bewirkt dies, dass die entsprechenden Dateien während der Installation in den Anwendungsordner kopiert werden.

 Wenn der Manifest-Generator auf einen isolierten COM-Verweis stößt, listet er alle `CoClass` Einträge in der Typbibliothek der Komponente auf, wobei jeder Eintrag mit den entsprechenden Registrierungsdaten abgeglichen und Manifest-Definitionen für alle COM-Klassen in der Typbibliotheks Datei erzeugt werden.

## <a name="deploy-registration-free-com-components-using-clickonce"></a>Bereitstellen von COM-Komponenten ohne Registrierung mit ClickOnce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Bereitstellungs Technologie eignet sich gut für die Bereitstellung isolierter COM-Komponenten, da sowohl [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] als auch Registrierungs freies com erfordert, dass eine Komponente ein Manifest hat, um bereitgestellt werden zu können.

 In der Regel sollte der Autor der Komponente ein Manifest bereitstellen. Andernfalls kann Visual Studio ein Manifest für eine COM-Komponente automatisch erstellen. Die Generierung von Manifesten wird während des [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veröffentlichungs Vorgangs durchgeführt. Weitere Informationen finden Sie unter [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md). Mit dieser Funktion können Sie auch ältere Komponenten nutzen, die Sie in früheren Entwicklungsumgebungen erstellt haben, z. b. Visual Basic 6,0.

 Es gibt zwei Möglichkeiten, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] com-Komponenten bereitzustellen:

- Verwenden Sie den Boots Trapper zum Bereitstellen der COM-Komponenten. Dies funktioniert auf allen unterstützten Plattformen.

- Verwenden Sie die native Komponenten Isolation (auch bekannt als com-Bereitstellung). Dies funktioniert jedoch nur bei einem Betriebssystem unter Windows XP oder höher.

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Beispiel für das isolieren und Bereitstellen einer einfachen COM-Komponente
 Um die Bereitstellung von COM-Komponenten ohne Registrierung zu veranschaulichen, wird in diesem Beispiel eine Windows-basierte Anwendung in Visual Basic erstellt, die auf eine isolierte Native COM-Komponente verweist, die mit Visual Basic 6,0 erstellt wurde, und mithilfe von bereitgestellt werden [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Zuerst müssen Sie die Native COM-Komponente erstellen:

##### <a name="to-create-a-native-com-component"></a>So erstellen Sie eine Native COM-Komponente

1. Wenn Sie Visual Basic 6,0 verwenden, klicken Sie im Menü **Datei** auf **neu** und dann auf **Projekt**.

2. Wählen Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** aus, und wählen Sie ein **ActiveX-DLL** -Projekt aus. Geben Sie im Feld **Name**`VB6Hello`ein.

    > [!NOTE]
    > Nur ActiveX-DLL-und ActiveX-Steuerelement-Projekttypen werden mit Registrierungs freiem com unterstützt. ActiveX-EXE-und ActiveX-Dokument Projekttypen werden nicht unterstützt.

3. Doppelklicken Sie in **Projektmappen-Explorer** auf **Class1. vb** , um den Text-Editor zu öffnen.

4. Fügen Sie in Class1. vb nach dem generierten Code für die-Methode den folgenden Code hinzu `New` :

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. Erstellen Sie die Komponente. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

> [!NOTE]
> Registrierungs freies com unterstützt nur die Projekttypen DLLs und com-Steuerelemente. Sie können keine exe-Datei mit Registrierungs freiem com verwenden.

 Nun können Sie eine Windows-basierte Anwendung erstellen und ihr einen Verweis auf die COM-Komponente hinzufügen.

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>So erstellen Sie eine Windows-basierte Anwendung mithilfe einer COM-Komponente

1. Wenn Sie Visual Basic verwenden, klicken Sie im Menü **Datei** auf **neu** und dann auf **Projekt**.

2. Wählen Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** aus, und wählen Sie **Windows-Anwendung** aus. Geben Sie im Feld **Name**`RegFreeComDemo`ein.

3. Klicken Sie in **Projektmappen-Explorer** auf die Schaltfläche **alle Dateien anzeigen** , um die Projekt Verweise anzuzeigen.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Verweise** , und wählen Sie im Kontextmenü **Verweis hinzufügen** aus.

5. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Durchsuchen** , navigieren Sie zu VB6Hello.dll, und wählen Sie Sie aus.

    Ein **VB6Hello** -Verweis wird in der Verweis Liste angezeigt.

6. Zeigen Sie auf die **Toolbox** , wählen Sie ein **Schalt** Flächen-Steuerelement aus, und ziehen Sie es in das Formular **Form1** .

7. Legen Sie im Fenster **Eigenschaften** die **Text** -Eigenschaft der Schaltfläche auf **Hello** fest.

8. Doppelklicken Sie auf die Schaltfläche, um Handlercode hinzuzufügen, und fügen Sie in der Codedatei Code hinzu, damit der Handler wie folgt aussieht:

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. Führen Sie die Anwendung aus. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

   Als nächstes müssen Sie das Steuerelement isolieren. Jede COM-Komponente, die Ihre Anwendung verwendet, wird in Ihrem Projekt als COM-Verweis dargestellt. Diese Verweise sind unter dem Knoten **Verweise** im Fenster **Projektmappen-Explorer** sichtbar. (Beachten Sie, dass Sie Verweise entweder direkt über den Befehl **Verweis hinzufügen** im Menü **Projekt** oder indirekt durchziehen eines ActiveX-Steuer Elements auf das Formular hinzufügen können.)

   Die folgenden Schritte zeigen, wie Sie die COM-Komponente isolieren und die aktualisierte Anwendung mit dem isolierten Steuerelement veröffentlichen:

##### <a name="to-isolate-a-com-component"></a>So isolieren Sie eine COM-Komponente

1. Wählen Sie in **Projektmappen-Explorer** im Knoten **Verweise** den Verweis **VB6Hello** aus.

2. Ändern Sie im Fenster **Eigenschaften** den Wert der **isolierten** Eigenschaft von **false** in **true**.

3. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Wenn Sie jetzt F5 drücken, funktioniert die Anwendung erwartungsgemäß, aber Sie wird jetzt unter com registriert. Um dies zu beweisen, versuchen Sie, die Registrierung der VB6Hello.dll-Komponente zu aufheben und RegFreeComDemo1.exe außerhalb der Visual Studio-IDE auszuführen. Wenn Sie auf die Schaltfläche klicken, funktioniert Sie immer noch. Wenn Sie das Anwendungs Manifest temporär umbenennen, tritt ein Fehler auf.

> [!NOTE]
> Sie können das Fehlen einer COM-Komponente simulieren, indem Sie die Registrierung vorübergehend aufheben. Öffnen Sie eine Eingabeaufforderung, navigieren Sie zum Systemordner, indem Sie eingeben `cd /d %windir%\system32` , und heben Sie die Registrierung der Komponente auf, indem Sie eingeben `regsvr32 /u VB6Hello.dll` . Sie können Sie erneut registrieren, indem Sie eingeben `regsvr32 VB6Hello.dll` .

 Der letzte Schritt besteht darin, die Anwendung mit folgenden Aktionen zu veröffentlichen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] :

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>So veröffentlichen Sie ein Anwendungs Update mit einer isolierten COM-Komponente

1. Klicken Sie im Menü **Erstellen** auf **regfrecomdemo veröffentlichen**.

    Der Webpublishing-Assistent wird angezeigt.

2. Geben Sie im Veröffentlichungs-Assistenten einen Speicherort auf dem Datenträger des lokalen Computers an, auf den Sie zugreifen und die veröffentlichten Dateien untersuchen können.

3. Klicken Sie auf **Fertig stellen** , um die Anwendung zu veröffentlichen.

   Wenn Sie die veröffentlichten Dateien untersuchen, werden Sie feststellen, dass die Datei "sysmon. ocx" enthalten ist. Das-Steuerelement ist vollständig für diese Anwendung isoliert, was bedeutet, dass die Anwendung nicht beeinträchtigt werden kann, wenn der Computer des Endbenutzers eine andere Anwendung verwendet, die eine andere Version des-Steuer Elements verwendet.

## <a name="reference-native-assemblies"></a>Referenzieren von systemeigenen
 Visual Studio unterstützt Verweise auf systemeigene Visual Basic 6,0-oder C++-Assemblys. solche Verweise werden als Native Verweise bezeichnet. Sie können erkennen, ob ein Verweis System eigen ist, indem Sie überprüfen, ob seine **Dateityp** - **Eigenschaft auf System** eigen oder **ActiveX** festgelegt

 Um einen nativen Verweis hinzuzufügen, verwenden Sie den Befehl **Verweis hinzufügen** , und navigieren Sie dann zum Manifest. Einige Komponenten platzieren das Manifest in der dll. In diesem Fall können Sie einfach die DLL selbst auswählen, und Visual Studio fügt sie als nativen Verweis hinzu, wenn Sie erkennt, dass die Komponente ein eingebettetes Manifest enthält. Visual Studio schließt auch automatisch alle abhängigen Dateien oder Assemblys ein, die im Manifest aufgelistet sind, wenn Sie sich im selben Ordner wie die Komponente befinden, auf die verwiesen wird.

 Die com-Steuerungs Isolation vereinfacht das Bereitstellen von COM-Komponenten, die nicht bereits über Manifeste verfügen. Wenn jedoch eine Komponente mit einem Manifest bereitgestellt wird, können Sie direkt auf das Manifest verweisen. Tatsächlich sollten Sie immer das Manifest verwenden, das vom Autor der Komponente bereitgestellt wird, anstatt die **isolierte** Eigenschaft zu verwenden.

## <a name="limitations-of-registration-free-com-component-deployment"></a>Einschränkungen bei der Bereitstellung von COM-Komponenten ohne Registrierung
 COM ohne Registrierung bietet deutliche Vorteile gegenüber herkömmlichen Bereitstellungs Verfahren. Es gibt jedoch einige Einschränkungen und Einschränkungen, auf die ebenfalls verwiesen werden sollte. Die größte Einschränkung ist, dass Sie nur unter Windows XP oder höher funktioniert. Die Implementierung des com-Registrierungs freien com erforderte Änderungen an der Art und Weise, in der Komponenten im Kernbetriebssystem geladen werden. Leider gibt es keine unterstützte Unterstützungs Schicht für Registrierungs freies com.

 Nicht jede Komponente ist ein geeigneter Kandidat für Registrierungs freies com. Eine Komponente ist nicht geeignet, wenn Folgendes zutrifft:

- Bei der Komponente handelt es sich um einen Out-of-Process-Server. EXE-Server werden nicht unterstützt. Es werden nur DLLs unterstützt.

- Die Komponente ist Teil des Betriebssystems oder eine Systemkomponente, wie z. b. XML, Internet Explorer oder Microsoft Data Access Components (MDAC). Befolgen Sie die weitergaberichtlinie des Komponenten Autors. wenden Sie sich an Ihren Hersteller.

- Die Komponente ist Teil einer Anwendung, z. b. Microsoft Office. Sie sollten z. b. nicht versuchen, das Microsoft Excel-Objektmodell zu isolieren. Diese ist Teil von Office und kann nur auf einem Computer verwendet werden, auf dem das vollständige Office-Produkt installiert ist.

- Die Komponente ist für die Verwendung als Add-in oder ein Snap-in gedacht, z. b. ein Office-Add-in oder ein-Steuerelement in einem Webbrowser. Diese Komponenten erfordern in der Regel eine Art Registrierungs Schema, das von der Host Umgebung definiert wird, die den Gültigkeitsbereich des Manifests überschreitet.

- Die Komponente verwaltet ein physisches oder virtuelles Gerät für das System, z. b. einen Gerätetreiber für einen Druck Spooler.

- Bei der Komponente handelt es sich um einen verteilbaren Datenzugriff. Daten Anwendungen erfordern in der Regel eine separate Datenzugriffs weitervertreibbare Komponente, die installiert werden muss, bevor Sie ausgeführt werden können. Sie sollten nicht versuchen, Komponenten wie das Microsoft ADO-Daten Steuerelement, Microsoft OLE DB oder Microsoft Data Access Components (MDAC) zu isolieren. Stattdessen sollten Sie, wenn Ihre Anwendung MDAC oder SQL Server Express verwendet, Sie als erforderliche Komponenten festlegen. Siehe Gewusst [wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

  In einigen Fällen kann es für den Entwickler der Komponente möglich sein, ihn für Registrierungs freies com umzugestalten. Wenn dies nicht möglich ist, können Sie mithilfe des Boots Trappers weiterhin Anwendungen erstellen und veröffentlichen, die von Ihnen abhängig sind. Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).

  Eine COM-Komponente kann nur einmal pro Anwendung isoliert werden. Beispielsweise können Sie nicht die gleiche COM-Komponente von zwei verschiedenen **Klassen Bibliotheks** Projekten isolieren, die Teil derselben Anwendung sind. Dadurch wird eine Buildwarnung erzeugt, und die Anwendung kann zur Laufzeit nicht geladen werden. Um dieses Problem zu vermeiden, empfiehlt Microsoft, com-Komponenten in einer einzigen Klassenbibliothek zu kapseln.

  Es gibt verschiedene Szenarien, in denen die com-Registrierung auf dem Computer des Entwicklers erforderlich ist, auch wenn die Bereitstellung der Anwendung keine Registrierung erfordert. Die- `Isolated` Eigenschaft erfordert, dass die COM-Komponente auf dem Computer des Entwicklers registriert wird, um das Manifest während des Builds automatisch zu generieren. Es gibt keine Registrierungs Erfassungs Funktionen, die die Selbstregistrierung während des Builds aufrufen. Außerdem werden alle Klassen, die nicht explizit in der Typbibliothek definiert sind, im Manifest nicht berücksichtigt. Wenn eine COM-Komponente mit einem bereits vorhandenen Manifest verwendet wird, z. b. ein nativer Verweis, muss die Komponente möglicherweise nicht zur Entwicklungszeit registriert werden. Die Registrierung ist jedoch erforderlich, wenn es sich bei der Komponente um ein ActiveX-Steuerelement handelt und Sie Sie in die **Toolbox** und den Windows Forms-Designer einschließen möchten.

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)