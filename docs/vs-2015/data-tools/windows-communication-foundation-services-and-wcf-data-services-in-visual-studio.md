---
title: Windows Communication Foundation-Dienste und WCF Data Services
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e988c8818cdee756310b73d0d214deda43226f2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850215"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio bietet Tools zum Arbeiten mit Windows Communication Foundation (WCF) und [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] Microsoft-Technologien für die Erstellung verteilter Anwendungen. Dieses Thema bietet eine Einführung in Dienste aus einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Perspektive. Die vollständige Dokumentation finden Sie unter [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>Was ist WCF?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] ist ein einheitliches Framework zum Erstellen sicherer, zuverlässiger, transaktiver und interoperable verteilter Anwendungen. Es ersetzt ältere Technologien für die prozessübergreifende Kommunikation, wie z. b. asmx-Webdienste, .NET Remoting, Enterprise Services (DCOM) und MSMQ. WCF vereint die Funktionen all dieser Technologien in einem einheitlichen Programmiermodell. Dies vereinfacht die Entwicklung verteilter Anwendungen.

#### <a name="what-are-wcf-data-services"></a>Was sind WCF Data Services
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] ist eine Implementierung des odata-Protokolls (Open Data).  Mit WCF Data Services können Sie tabellarische Daten als Satz von Rest-APIs verfügbar machen, sodass Sie Daten mit Standard-HTTP-Verben wie Get, Post, Put oder DELETE zurückgeben können. Auf der Serverseite werden WCF Data Services durch [ASP.net-Web-API](https://dotnet.microsoft.com/apps/aspnet/apis) zum Erstellen neuer odata-Dienste abgelöst. Die WCF Data Services-Client Bibliothek ist weiterhin eine gute Wahl für die Nutzung von odata-Diensten in einer .NET-Anwendung in Visual Studio (**Project &#124; Dienstverweis hinzufügen**). Weitere Informationen finden Sie unter [WCF Data Services 4.5](https://msdn.microsoft.com/library/cc668792.aspx).

### <a name="wcf-programming-model"></a>WCF-Programmiermodell
 Das WCF-Programmiermodell basiert auf der Kommunikation zwischen zwei Entitäten: einem WCF-Dienst und einem WCF-Client. Das-Programmiermodell wird im- <xref:System.ServiceModel> Namespace in gekapselt [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

#### <a name="wcf-service"></a>WCF-Dienst
 Ein WCF-Dienst basiert auf einer Schnittstelle, die einen Vertrag zwischen dem Dienst und dem Client definiert. Es ist mit einem- <xref:System.ServiceModel.ServiceContractAttribute> Attribut gekennzeichnet, wie im folgenden Code gezeigt:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 Sie definieren Funktionen oder Methoden, die von einem WCF-Dienst verfügbar gemacht werden, indem Sie Sie mit einem- <xref:System.ServiceModel.OperationContractAttribute> Attribut markieren. Außerdem können Sie serialisierte Daten verfügbar machen, indem Sie einen zusammengesetzten Typ mit einem- <xref:System.Runtime.Serialization.DataContractAttribute> Attribut markieren. Dadurch wird die Datenbindung in einem Client aktiviert.

 Nachdem eine Schnittstelle und ihre Methoden definiert wurden, werden Sie in einer Klasse gekapselt, die die-Schnittstelle implementiert. Eine einzelne WCF-Dienstklasse kann mehrere Dienstverträge implementieren.

 Ein WCF-Dienst wird über was als *Endpunkt*bezeichnet. Der Endpunkt stellt die einzige Möglichkeit dar, mit dem Dienst zu kommunizieren. Sie können nicht über einen direkten Verweis auf den Dienst zugreifen, wie dies bei anderen Klassen der Fall wäre.

 Ein Endpunkt besteht aus einer Adresse, einer Bindung und einem Vertrag. Die Adresse definiert, wo sich der Dienst befindet. Dabei kann es sich um eine URL, eine FTP-Adresse oder einen Netzwerk-oder lokalen Pfad handeln. Eine Bindung definiert die Art und Weise, wie Sie mit dem Dienst kommunizieren. WCF-Bindungen bieten ein vielseitiges Modell zum Angeben eines Protokolls, z. b. http oder FTP, eines Sicherheitsmechanismus wie Windows-Authentifizierung oder Benutzernamen und Kenn Wörter und vieles mehr. Ein Vertrag schließt die Vorgänge ein, die von der WCF-Dienstklasse verfügbar gemacht werden.

 Für einen einzelnen WCF-Dienst können mehrere Endpunkte verfügbar gemacht werden. Dadurch können unterschiedliche Clients auf unterschiedliche Weise mit demselben Dienst kommunizieren. Beispielsweise kann ein Bank Dienst einen Endpunkt für Mitarbeiter und einen anderen für externe Kunden bereitstellen, von denen jeder eine andere Adresse, Bindung und/oder einen anderen Vertrag verwendet.

#### <a name="wcf-client"></a>WCF-Client
 Ein WCF-Client besteht aus einem *Proxy* , der einer Anwendung die Kommunikation mit einem WCF-Dienst ermöglicht, und einem Endpunkt, der mit einem für den Dienst definierten Endpunkt übereinstimmt. Der Proxy wird auf der Clientseite in der app.config Datei generiert und enthält Informationen zu den Typen und Methoden, die vom Dienst verfügbar gemacht werden. Für Dienste, die mehrere Endpunkte verfügbar machen, kann der Client den Wert auswählen, der seinen Anforderungen am besten entspricht, z. b. für die Kommunikation über HTTP und die Verwendung der Windows-Authentifizierung.

 Nachdem Sie einen WCF-Client erstellt haben, verweisen Sie auf den Dienst im Code, genauso wie auf jedes andere Objekt. Um z. b. die `GetData` zuvor gezeigte-Methode aufzurufen, würden Sie Code schreiben, der etwa wie folgt aussieht:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>WCF-Tools in Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stellt Tools bereit, die Sie beim Erstellen von WCF-Diensten und WCF-Clients unterstützen. Eine exemplarische Vorgehensweise zur Veranschaulichung der Tools finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines einfachen WCF-Dienstanbieter in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Erstellen und Testen von WCF-Diensten
 Sie können die WCF- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vorlagen als Grundlage verwenden, um schnell einen eigenen Dienst zu erstellen. Anschließend können Sie den automatischen WCF-Dienst Host und den WCF-Test Client zum Debuggen und Testen des Diensts verwenden. Diese Tools bieten eine schnelle und bequeme Debug-und Testzyklen und vermeiden die Anforderung, in einem frühen Stadium auf ein Hostingmodell zu übertragen.

#### <a name="wcf-templates"></a>WCF-Vorlagen
 WCF- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vorlagen stellen eine grundlegende Klassenstruktur für die Dienst Entwicklung dar. Im Dialogfeld **Neues Projekt hinzufügen** sind mehrere WCF-Vorlagen verfügbar. Hierzu gehören WCF-Dienst Bibliotheks Projekte, WCF-Dienst Websites und Element Vorlagen für WCF-Dienste.

 Wenn Sie eine Vorlage auswählen, werden Dateien für einen Dienstvertrag, eine Dienst Implementierung und eine Dienst Konfiguration hinzugefügt. Alle erforderlichen Attribute wurden bereits hinzugefügt, und es wird ein einfacher Dienst vom Typ "Hallo Welt" erstellt, und Sie mussten keinen Code schreiben. Sie möchten natürlich Code hinzufügen, um Funktionen und Methoden für Ihren echten Dienst bereitzustellen, aber die Vorlagen stellen die Basis Grundlage dar.

 Weitere Informationen zu WCF-Vorlagen finden Sie unter [WCF Visual Studio-Vorlagen](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>WCF-Diensthost
 Wenn Sie den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Debugger (durch Drücken von F5) für ein WCF-Dienstprojekt starten, wird das WCF-Dienst Host Tool automatisch gestartet, um den Dienst lokal zu hosten. Der WCF-Dienst Host listet die Dienste in einem WCF-Dienstprojekt auf, lädt die Konfiguration des Projekts und instanziiert einen Host für jeden gefundenen Dienst.

 Mithilfe des WCF-Dienst Hosts können Sie einen WCF-Dienst testen, ohne zusätzlichen Code schreiben oder bei der Entwicklung einen Commit für einen bestimmten Host ausführen zu müssen.

 Weitere Informationen zum WCF-Dienst Host finden Sie unter [WCF-Dienst Host (WcfSvcHost.exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>WCF-Testclient
 Mit dem WCF-Test Client Tool können Sie Test Parameter eingeben, die Eingabe an einen WCF-Dienst übermitteln und die vom Dienst zurück gesendete Antwort anzeigen. Sie bietet eine praktische Dienst Überprüfung, wenn Sie Sie mit dem WCF-Dienst Host kombinieren. Das Tool befindet sich im Ordner "\Common7\IDE", der für Visual Studio 2015 in Laufwerk C: hier installiert ist: **c:\Programme (x86) \Microsoft Visual Studio 14,0 \ Common7\IDE \\ **.

 Wenn Sie zum Debuggen eines WCF-Dienst Projekts F5 drücken, wird der WCF-Test Client geöffnet, und es wird eine Liste der Dienst Endpunkte angezeigt, die in der Konfigurationsdatei definiert sind. Sie können die Parameter testen und den Dienst starten und diesen Vorgang wiederholen, um den Dienst fortlaufend zu testen und zu überprüfen.

 Weitere Informationen zum WCF-Test Client finden Sie unter [WCF-Test Client (WcfTestClient.exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Zugreifen auf WCF-Dienste in Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vereinfacht das Erstellen von WCF-Clients, das automatische Erstellen eines Proxys und eines Endpunkts für Dienste, die Sie über das Dialogfeld **Dienstverweis hinzufügen** hinzufügen. Alle erforderlichen Konfigurationsinformationen werden der app.config Datei hinzugefügt. In den meisten Fällen müssen Sie lediglich den Dienst instanziieren, um ihn zu verwenden.

 Im Dialogfeld **Dienstverweis hinzufügen** können Sie die Adresse für einen Dienst eingeben oder nach einem Dienst suchen, der in der Lösung definiert ist. Im Dialogfeld wird eine Liste der Dienste und die von diesen Diensten bereitgestellten Vorgänge zurückgegeben. Außerdem können Sie den Namespace definieren, in dem Sie im Code auf die Dienste verweisen.

 Im Dialogfeld **Dienst Verweise konfigurieren** können Sie die Konfiguration für einen Dienst anpassen. Sie können die Adresse für einen Dienst ändern, Zugriffsebene, asynchrones Verhalten und Nachrichten Vertragstypen angeben und die Wiederverwendung von Typen konfigurieren.

## <a name="how-to-select-a-service-endpoint"></a>Vorgehensweise: Auswählen eines Dienst Endpunkts
 Einige Windows Communication Foundation (WCF)-Dienste stellen mehrere Endpunkte zur Verfügung, über die ein Client mit dem Dienst kommunizieren kann. Ein Dienst kann z. b. einen Endpunkt verfügbar machen, der eine HTTP-Bindung und Benutzername/Kennwort-Sicherheit und einen zweiten Endpunkt verwendet, der die FTP-und Windows-Authentifizierung verwendet. Der erste Endpunkt kann von Anwendungen verwendet werden, die von außerhalb einer Firewall auf den Dienst zugreifen, während der zweite Endpunkt in einem Intranet verwendet werden kann.

 In einem solchen Fall können Sie `endpointConfigurationName` als Parameter für den Konstruktor eines Dienst Verweises angeben.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>So wählen Sie einen Dienst Endpunkt aus

1. Fügen Sie einen Verweis auf einen WCF-Dienst hinzu, indem Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten klicken und **Dienst Verweis hinzufügen**

2. Fügen Sie im Code-Editor einen Konstruktor für den Dienst Verweis hinzu:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Ersetzen Sie *servicereferenzierung* durch den Namespace für den Dienst Verweis, und ersetzen Sie *Service1Client* durch den Namen des Dienstanbieter.

3. Eine IntelliSense-Liste wird mit den über Ladungen für den Konstruktor angezeigt. Wählen Sie die Überladung aus `endpointConfigurationName As String` .

4. Geben Sie nach der Überladung `=` *ConfigurationName*ein, wobei *ConfigurationName* der Name des Endpunkts ist, den Sie verwenden möchten.

    > [!NOTE]
    > Wenn Sie die Namen der verfügbaren Endpunkte nicht kennen, können Sie Sie in der app.config-Datei finden.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>So finden Sie die verfügbaren Endpunkte für einen WCF-Dienst

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die app.config-Datei für das Projekt, das den Dienst Verweis enthält, und klicken Sie dann auf **Öffnen**. Die Datei wird im Code-Editor angezeigt.

2. Suchen Sie `<Client>` in der Datei nach dem-Tag.

3. Suchen Sie unterhalb des `<Client>` Tags nach einem Tag, das mit beginnt `<Endpoint>` .

     Wenn der Dienst Verweis mehrere Endpunkte bereitstellt, sind zwei oder mehr `<Endpoint` Tags vorhanden.

4. Innerhalb des `<EndPoint>` Tags finden Sie einen Parameter " `name="` *SOMESERVICE* " `"` (wobei " *SOMESERVICE* " einen Endpunkt Namen darstellt). Dies ist der Name des Endpunkts, der an die Überladung `endpointConfigurationName As String` eines Konstruktors für einen Dienst Verweis übergeben werden kann.

## <a name="how-to-call-a-service-method-asynchronously"></a>Vorgehensweise: Asynchrones Abrufen einer Dienst Methode
 Die meisten Methoden in Windows Communication Foundation (WCF)-Diensten können synchron oder asynchron aufgerufen werden. Wenn Sie eine Methode asynchron aufrufen, kann die Anwendung weiterhin ausgeführt werden, während die Methode aufgerufen wird, wenn Sie über eine langsame Verbindung arbeitet.

 Wenn ein Dienst Verweis zu einem Projekt hinzugefügt wird, wird er standardmäßig so konfiguriert, dass Methoden synchron aufgerufen werden. Sie können das Verhalten ändern, sodass Methoden asynchron aufgerufen werden, indem Sie eine Einstellung im Dialogfeld **Dienst Verweis konfigurieren** ändern.

> [!NOTE]
> Diese Option wird pro Dienst festgelegt. Wenn eine Methode für einen Dienst asynchron aufgerufen wird, müssen alle Methoden asynchron aufgerufen werden.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>So können Sie eine Dienst Methode asynchron aufzurufen

1. Wählen Sie in **Projektmappen-Explorer**den Dienst Verweis aus.

2. Klicken Sie im Menü **Projekt** auf **Dienst Verweis konfigurieren**.

3. Aktivieren Sie im Dialogfeld **Dienst Verweis konfigurieren** das Kontrollkästchen **asynchrone Vorgänge generieren** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Gewusst wie: Binden von Daten, die von einem Dienst zurückgegeben werden
 Sie können Daten, die von einem Windows Communication Foundation (WCF)-Dienst zurückgegeben werden, an ein Steuerelement binden, so wie Sie jede beliebige andere Datenquelle an ein Steuerelement binden können. Wenn Sie einen Verweis auf einen WCF-Dienst hinzufügen und der Dienst zusammengesetzte Typen enthält, die Daten zurückgeben, werden diese automatisch dem **Datenquellen** Fenster hinzugefügt.

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>So binden Sie ein Steuerelement an ein einzelnes von einem WCF-Dienst zurück gegebenes Daten Feld

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**. Das Fenster **Datenquellen** wird angezeigt.

2. Erweitern Sie im Fenster **Datenquellen** den Knoten für Ihren Dienst Verweis. Alle vom Dienst zurückgegebenen zusammengesetzten Typen werden angezeigt.

3. Erweitern Sie einen Knoten für einen Typ. Die Datenfelder für diesen Typ werden angezeigt.

4. Wählen Sie ein Feld aus, und klicken Sie auf den Dropdown Pfeil, um eine Liste der Steuerelemente anzuzeigen, die für den Datentyp verfügbar sind.

5. Klicken Sie auf den Typ des Steuer Elements, an das die Bindung erfolgen soll.

6. Ziehen Sie das Feld auf ein Formular. Das-Steuerelement wird dem Formular in Verbindung mit einer <xref:System.Windows.Forms.BindingSource> -Komponente und einer-Komponente hinzugefügt <xref:System.Windows.Forms.BindingNavigator> .

7. Wiederholen Sie die Schritte 4 bis 6 für alle anderen Felder, die Sie binden möchten.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>So binden Sie ein Steuerelement an einen von einem WCF-Dienst zurückgegebenen zusammengesetzten Typ

1. Wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen**aus. Das Fenster **Datenquellen** wird angezeigt.

2. Erweitern Sie im Fenster **Datenquellen** den Knoten für Ihren Dienst Verweis. Alle vom Dienst zurückgegebenen zusammengesetzten Typen werden angezeigt.

3. Wählen Sie einen Knoten für einen Typ aus, und klicken Sie auf den Dropdown Pfeil, um eine Liste der verfügbaren Optionen anzuzeigen.

4. Klicken Sie entweder auf **DataGridView** , um die Daten in einem Raster anzuzeigen, oder auf **Details** , um die Daten in einzelnen Steuerelementen anzuzeigen.

5. Ziehen Sie den Knoten auf das Formular. Die Steuerelemente werden dem Formular in Verbindung mit einer <xref:System.Windows.Forms.BindingSource> -Komponente und einer-Komponente hinzugefügt <xref:System.Windows.Forms.BindingNavigator> .

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Vorgehensweise: Konfigurieren eines Dienes für die Wiederverwendung vorhandener Typen
 Wenn ein Dienst Verweis zu einem Projekt hinzugefügt wird, werden alle im Dienst definierten Typen im lokalen Projekt generiert. In vielen Fällen werden dadurch doppelte Typen erstellt, wenn ein Dienst allgemeine [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Typen verwendet oder wenn Typen in einer freigegebenen Bibliothek definiert sind.

 Um dieses Problem zu vermeiden, werden Typen in referenzierten Assemblys standardmäßig freigegeben. Wenn Sie die Typfreigabe für eine oder mehrere Assemblys deaktivieren möchten, können Sie dies im Dialogfeld **Dienst Verweise konfigurieren** tun.

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>So deaktivieren Sie die Freigabe von Typen in einer einzelnen Assembly

1. Wählen Sie in **Projektmappen-Explorer**den Dienst Verweis aus.

2. Klicken Sie im Menü **Projekt** auf **Dienst Verweis konfigurieren**.

3. Wählen Sie im Dialogfeld **Dienst Verweise konfigurieren** die Option **Typen in angegebenen referenzierten Assemblys wieder verwenden aus**.

4. Aktivieren Sie das Kontrollkästchen für jede Assembly, in der Sie die Typfreigabe aktivieren möchten. Wenn Sie die Typfreigabe für eine Assembly deaktivieren möchten, lassen Sie das Kontrollkästchen deaktiviert.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>So deaktivieren Sie die Typfreigabe in allen Assemblys

1. Wählen Sie in **Projektmappen-Explorer**den Dienst Verweis aus.

2. Klicken Sie im Menü **Projekt** auf **Dienst Verweis konfigurieren**.

3. Deaktivieren Sie im Dialogfeld **Dienst Verweise konfigurieren** das Kontrollkästchen **Typen in referenzierten** Assemblys wieder verwenden.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Bietet eine Schritt-für-Schritt-Demonstration zum Erstellen und Verwenden von WCF-Diensten in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Exemplarische Vorgehensweise: Erstellen von und Zugreifen auf einen WCF-Datendienst mit WPF und Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Bietet eine Schritt-für-Schritt-Demonstration zum Erstellen und Verwenden von [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Verwenden der WCF-Entwicklungstools](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|Erläutert das Erstellen und Testen von WCF-Diensten in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Vorgehensweise: Hinzufügen, Aktualisieren oder Entfernen eines Dienstverweises](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Beschreibt das Hinzufügen, aktualisieren oder Entfernen von WCF-Diensten aus einem Projekt.|
|[Gewusst wie: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Erläutert, wie in auf verwiesen und verwendet wird [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md)|Zeigt einige allgemeine Fehler an, die bei Dienst verweisen auftreten können, und wie Sie verhindert werden.|
|[Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)|Beschreibt häufige Debugprobleme und Techniken, die beim Debuggen von WCF-Diensten auftreten können.|
|[Übersicht über Windows Communication Foundation Authentifizierungsdienst](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|Beschreibt, wie WCF verwendet wird, um einen Rollen Dienst für eine Website bereitzustellen.|
|[Exemplarische Vorgehensweise: Erstellen einer N-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Liefert eine Schritt-für-Schritt-Anleitung für das Erstellen eines typisierten Datasets und das Aufteilen des Codes für TableAdapter und Dataset in mehrere Projekte.|
|[Dialog Feld "Dienst Verweis konfigurieren"](../data-tools/configure-service-reference-dialog-box.md)|Beschreibt die Benutzeroberflächen Elemente des Dialog Felds **Dienst Verweis konfigurieren** .|

## <a name="reference"></a>Verweis
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
