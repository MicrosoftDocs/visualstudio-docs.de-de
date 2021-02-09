---
title: Windows Communication Foundation und WCF Data Services
description: Machen Sie sich mit Windows Communication Foundation-Diensten (WCF) und WCF Data Services in Visual Studio vertraut, sodass Sie verteilte Anwendungen erstellen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- VB
- CSharp
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: fb5ace269d7770d0e7d360734268d3e7adfda319
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866124"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio

In Visual Studio stehen Tools für das Arbeiten mit Windows Communication Foundation (WCF) und WCF Data Services zur Verfügung, also Technologien von Microsoft für das Erstellen verteilter Anwendungen. In diesem Thema erhalten Sie eine Einführung in die Dienste aus einer Visual Studio-Perspektive. Die vollständige Dokumentation finden Sie unter [WCF Data Services 4.5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Was ist WCF?

Windows Communication Foundation (WCF) ist ein einheitliches Framework für das Erstellen sicherer, zuverlässiger, transaktiver und interoperabler verteilter Anwendungen. Es ersetzt ältere Technologien für die prozessübergreifende Kommunikation wie ASMX-Webdienste, .NET Remoting, Enterprise Services (DCOM) und MSMQ. WCF vereint die Funktionen all dieser Technologien unter einem vereinheitlichten Programmiermodell. Dies vereinfacht die Entwicklung verteilter Anwendungen.

### <a name="what-are-wcf-data-services"></a>Informationen zu WCF Data Services

Bei WCF Data Services handelt es sich um eine Implementierung des OData-Protokollstandards (Open Data).  Mithilfe der WCF Data Services können Sie Tabellendaten über REST-APIs verfügbar machen, was Ihnen die Möglichkeit gibt, mithilfe von HTTP-Standardverben wie GET, POST, PUT oder DELETE Daten zurückgeben. Auf Serverseite werden die WCF Data Services für die Erstellung neuer OData-Dienste von der [ASP.NET-Web-API](https://dotnet.microsoft.com/apps/aspnet/apis) abgelöst. Die WCF Data Services-Clientbibliothek eignet sich weiterhin gut für die Nutzung von OData-Diensten in einer .NET-Anwendung in Visual Studio (**Projekt** > **Dienstverweis hinzufügen**). Weitere Informationen finden Sie unter [WCF Data Services 4.5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>WCF-Programmiermodell

Das WCF-Programmiermodell basiert auf der Kommunikation zwischen zwei Entitäten: einem WCF-Dienst und einem WCF-Client. Das Programmiermodell wird im <xref:System.ServiceModel>-Namespace in .NET eingekapselt.

### <a name="wcf-service"></a>WCF-Dienst

Ein WCF-Dienst basiert auf einer Schnittstelle, die einen Vertrag zwischen dem Dienst und dem Client definiert. Sie ist mit einem <xref:System.ServiceModel.ServiceContractAttribute>-Attribut markiert, wie im folgenden Code ersichtlich wird:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Sie definieren Funktionen oder Methoden, die von einem WCF-Dienst verfügbar gemacht werden, indem sie mit einem <xref:System.ServiceModel.OperationContractAttribute>-Attribut markiert werden.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Außerdem können Sie serialisierte Daten verfügbar machen, indem ein zusammengesetzter Typ mit einem <xref:System.Runtime.Serialization.DataContractAttribute>-Attribut markiert wird. Dies ermöglicht Datenbindungen auf einem Client.

Nachdem eine Schnittstelle und die dazugehörigen Methoden definiert wurden, werden sie in einer Klasse eingekapselt, die die Schnittstelle implementiert. Eine einzelne Klasse eines WCF-Diensts kann mehrere Dienstverträge implementieren.

Die Nutzung eines WCF-Diensts wird über einen *Endpunkt* ermöglicht. Der Endpunkt bietet die einzige Möglichkeit der Kommunikation mit dem Dienst. Sie können auf den Dienst nicht über einen direkten Verweis zugreifen, wie dies für andere Klassen möglich wäre.

Ein Endpunkt besteht aus einer Adresse, einer Bindung und einem Vertrag. Die Adresse definiert, wo sich der Dienst befindet. Dabei könnte es sich um eine URL, eine FTP-Adresse oder einen Netzwerk- oder lokalen Pfad handeln. Eine Bindung definiert die Art der Kommunikation mit dem Dienst. WCF-Bindungen bieten ein vielseitiges Modell u. a. für das Angeben eines Protokolls wie HTTP oder FTP, einen Sicherheitsmechanismus wie die Windows-Authentifizierung oder Benutzernamen und Kennwörter. Ein Vertrag schließt die Vorgänge ein, die von der Klasse des WCF-Diensts verfügbar gemacht werden.

Mehrere Endpunkte können für einen einzelnen WCF-Dienst verfügbar gemacht werden. Dies ermöglicht es verschiedenen Clients, mit demselben Dienst auf verschiedene Art zu kommunizieren. Ein Dienst für das Bankwesen könnte beispielsweise einen Endpunkt für Mitarbeiter und einen anderen für externe Kunden bereitstellen. Für jeden wird eine andere Adresse, eine andere Bindung und/oder ein anderer Vertrag genutzt.

### <a name="wcf-client"></a>WCF-Client (WCF client)

Ein WCF-Client besteht aus einem *Proxy*, der es einer Anwendung ermöglicht, mit einem WCF-Dienst zu kommunizieren, und aus einem Endpunkt, der mit einem für den Dienst definierten Endpunkt übereinstimmt. Der Proxy wird clientseitig in der *app.config*-Datei generiert und enthält Informationen zu den Typen und Methoden, die vom Dienst verfügbar gemacht werden. Für Dienste, die mehrere Endpunkte verfügbar machen, kann der Client den einen auswählen, der die Anforderungen am besten erfüllt, z. B. für die Kommunikation über HTTP und die Verwendung der Windows-Authentifizierung.

Nach der Erstellung eines WCF-Clients verweisen Sie in Ihrem Code auf den Dienst, genau so, wie Sie es auch für jedes andere Objekt tun würden. Wenn Sie beispielsweise die `GetData`-Methode, die Sie sich vorhin angesehen haben, aufrufen möchten, würden Sie Code schreiben, der in etwa folgendermaßen aussieht:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>WCF-Tools in Visual Studio

Visual Studio stellt Tools zur Verfügung, mit denen Sie sowohl WCF-Dienste als auch WCF-Clients erstellen können. Eine exemplarische Vorgehensweise, in der die Tools gezeigt werden, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Erstellen und Testen von WCF-Diensten

Sie können die WCF-Vorlagen in Visual Studio als Grundlage verwenden, um schnell einen eigenen Dienst zu erstellen. Sie können dann den WCF-Dienst-Auto-Host und den WCF-Testclient verwenden, um den Dienst zu debuggen und zu testen. Diese Tools ermöglichen Ihnen die Durchführung eines schnellen und problemlosen Test- und Debugzyklus, ohne dass Sie sich bereits in einem frühen Stadium auf ein Hostmodell festlegen müssen.

#### <a name="wcf-templates"></a>WCF-Vorlagen

WCF-Vorlagen aus Visual Studio stellen eine grundlegende Klassenstruktur zur Dienstentwicklung bereit. Mehrere WCF-Vorlagen sind im Dialogfeld **Neues Projekt hinzufügen** verfügbar. Dazu gehören Bibliotheksprojekte des WCF-Diensts, Websites des WCF-Diensts und Elementvorlagen des WCF-Diensts.

Wenn Sie eine Vorlage auswählen, werden Dateien für einen Dienstvertrag, eine Dienstimplementierung und eine Dienstkonfiguration hinzugefügt. Alle erforderlichen Attribute wurden bereits hinzugefügt, wodurch ein Dienst des Typs „Hallo Welt“ erstellt wurde. Dafür mussten Sie keinen Code schreiben. Sie werden natürlich noch Code hinzufügen, um Funktionen und Methoden für Ihren realen Dienst zu implementieren, die Vorlagen stellen jedoch die Grundlagen bereit.

Weitere Informationen zu WCF-Vorlagen erhalten Sie unter [WCF-Vorlagen in Visual Studio](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>WCF-Diensthost

Wenn Sie den Visual Studio-Debugger für ein Projekt des WCF-Diensts starten, indem Sie auf **F5** drücken, wird das Hosttool des WCF-Diensts automatisch gestartet, um den Dienst lokal zu hosten. Der Host des WCF-Diensts listet die Dienste in einem Projekt des WCF-Diensts auf, lädt die Projektkonfiguration und instanziiert einen Host für jeden gefundenen Dienst.

Wenn Sie den Host des WCF-Diensts verwenden, können Sie einen WCF-Dienst testen, ohne zusätzlichen Code schreiben oder einen bestimmten Host bei der Entwicklung bereitstellen zu müssen.

Weitere Informationen zum Host des WCF-Diensts finden Sie unter [Host des WCF-Diensts (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>WCF-Testclient

Der WCF-Testclient ist ein Tool, mit dem Sie Testparameter eingeben, die Eingabe an einen WCF-Dienst senden und die zurückgesendete Antwort des Diensts anzeigen können. Es bietet die Möglichkeit, problemlos Tests für einen Dienst ausführen zu können, wenn Sie es mit dem Host des WCF-Diensts kombinieren. Das Tool befindet sich im Ordner *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

Wenn Sie **F5** drücken, um ein Projekt des WCF-Diensts zu debuggen, wird der WCF-Testclient geöffnet und zeigt eine Liste der Dienstendpunkte an, die in der Konfigurationsdatei definiert sind. Sie können die Parameter testen und den Dienst starten und anschließend den Vorgang wiederholen, um den Dienst kontinuierlich zu testen und zu validieren.

Weitere Informationen zum WCF-Testclient finden Sie unter [WCF-Testclient (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Zugreifen auf WCF-Dienste in Visual Studio

Visual Studio vereinfacht das Erstellen von WCF-Clients, indem automatisch ein Proxy und ein Endpunkt für Dienste generiert werden, die Sie mithilfe des Dialogfelds **Dienstverweis hinzufügen** hinzufügen können. Alle erforderlichen Konfigurationsinformationen werden in der *app.config*-Datei hinzugefügt. Meistens müssen Sie den Dienst nur instanziieren, um ihn verwenden zu können.

Über das Dialogfeld **Dienstverweis hinzufügen** können Sie die Adresse für einen Dienst eingeben oder nach einem Dienst suchen, der in Ihrer Projektmappe definiert ist. Das Dialogfeld gibt eine Liste der von diesen Diensten bereitgestellten Dienste und Vorgänge zurück. Außerdem können Sie darüber den Namespace definieren, nach dem Sie im Code auf die Dienste verweisen können.

Mithilfe des Dialogfelds **Dienstverweise konfigurieren** können Sie die Konfiguration für einen Dienst anpassen. Sie können die Adresse für einen Dienst ändern, die Zugriffsebene, asynchrones Verhalten sowie Nachrichtenvertragstypen angeben, und die Typwiederverwendung konfigurieren.

## <a name="how-to-select-a-service-endpoint"></a>Vorgehensweise: Auswählen eines Dienstendpunkts

Manche der Windows Communication Foundation-Dienste (WCF) stellen mehrere Endpunkte zur Verfügung, über die ein Client mit dem Dienst kommunizieren kann. Ein Dienst könnte beispielsweise einen Endpunkt zur Verfügung stellen, der eine HTTP-Bindung und Sicherheit durch Benutzername und Kennwort verwendet, und einen zweiten Endpunkt, der FTP und die Windows-Authentifizierung verwendet. Der erste Endpunkt könnte von Anwendungen verwendet werden, die von außerhalb einer Firewall auf den Dienst zugreifen, während der zweite Endpunkt als Intranet genutzt werden könnte.

In so einem Fall können Sie `endpointConfigurationName` in einem Dienstverweis als Parameter für den Konstruktor angeben.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Auswählen eines Dienstendpunkts

1. Fügen Sie einem WCF-Dienst einen Verweis hinzu, indem Sie im **Projektmappen-Explorer** auf den Projektknoten rechtsklicken und dann auf **Dienstverweis hinzufügen** klicken.

2. Fügen Sie im Code-Editor einen Konstruktor für den Dienstverweis hinzu:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Ersetzen Sie *ServiceReference* durch den Namespace für den Dienstverweis, und ersetzen Sie *Service1Client* durch den Name des Diensts.

3. Eine IntelliSense-Liste wird angezeigt, die die Überladungen des Konstruktors enthält. Klicken Sie auf die `endpointConfigurationName As String`-Überladung.

4. Geben Sie nach der Überladung `=` *KonfigurationsName* ein. *KonfigurationsName* steht dabei für den Name des Endpunkts, den Sie verwenden möchten.

    > [!NOTE]
    > Wenn Sie die Namen der verfügbaren Endpunkte nicht kennen, finden Sie sie in der *app.config*-Datei.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Auffinden der verfügbaren Endpunkte für einen WCF-Dienst

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die **app.config**-Datei des Projekts, die den Dienstverweis enthält, und klicken Sie dann auf **Öffnen**. Die Datei wird im Code-Editor angezeigt.

2. Suchen Sie nach dem `<Client>`-Tag in der Datei.

3. Suchen Sie unterhalb des `<Client>`-Tags nach einem Tag, der mit `<Endpoint>` beginnt.

     Wenn der Dienstverweis mehrere Endpunkte bereitstellt, gibt es mindestens zwei `<Endpoint`-Tags.

4. Innerhalb des `<EndPoint>`-Tags finden Sie einen `name="`*BeliebigerDienst*`"`-Parameter. *BeliebigerDienst* steht dabei für einen Endpunktname. Dies ist der Name für den Endpunkt, der im Rahmen eines Dienstverweises an die `endpointConfigurationName As String`-Überladung eines Konstruktors übergeben werden kann.

## <a name="how-to-call-a-service-method-asynchronously"></a>Vorgehensweise: Asynchrones Aufrufen einer Dienstmethode

Die meisten Methoden in Windows Communication Foundation-Diensten (WCF) können entweder synchron oder asynchron aufgerufen werden. Das asynchrone Aufrufen einer Methode ermöglicht es, dass Ihre Anwendung weiter funktioniert, wenn die Methode aufgerufen wird, wenn sie über eine langsame Verbindung ausgeführt wird.

Standardmäßig sind Dienstverweise beim Hinzufügen zu einem Projekt so konfiguriert, dass Methoden synchron aufgerufen werden. Sie können das Verhalten ändern, sodass Methoden asynchron aufgerufen werden, indem Sie eine Einstellung im Dialogfeld **Dienstverweise konfigurieren** ändern.

> [!NOTE]
> Diese Option wird pro Dienst festgelegt. Sobald eine Methode für einen Dienst asynchron aufgerufen wird, müssen alle Methoden asynchron aufgerufen werden.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Asynchrones Aufrufen einer Dienstmethode

1. Wählen Sie im **Projektmappen-Explorer** den Dienstverweis aus.

2. Klicken Sie im Menü **Projekt** auf **Dienstverweis konfigurieren**.

3. Klicken Sie im Dialogfeld **Dienstverweis konfigurieren** auf das Kontrollkästchen **Asynchrone Vorgänge generieren**.

## <a name="how-to-bind-data-returned-by-a-service"></a>Vorgehensweise: Erstellen von Bindungen für von einem Dienst zurückgegebene Daten

Sie können Daten, die von einem Windows Communication Foundation-Dienst (WCF) zurückgegeben wurden, an ein Steuerelement binden, genauso wie Sie jede andere Datenquelle an ein Steuerelement binden können. Wenn ein WCF-Dienst zusammengesetzte Typen enthält, die Daten zurückgeben, werden diese beim Hinzufügen eines Verweises auf den Dienst automatisch im Fenster **Datenquellen** hinzugefügt.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Binden eines Steuerelements an ein einzelnes von einem WCF-Dienst zurückgegebenes Datenfeld

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

   Das Fenster **Datenquellen** wird angezeigt.

2. Erweitern Sie im Fenster **Datenquellen** den Knoten für Ihren Dienstverweis. Zusammengesetzte Typen, die vom Dienst zurückgegeben wurden, werden angezeigt.

3. Erweitern Sie einen Knoten für einen Typ. Die Datenfelder für diesen Typ werden angezeigt.

4. Wählen Sie ein Feld aus, und klicken Sie auf den Dropdownpfeil, um eine Liste der Steuerelemente anzuzeigen, die für den Datentyp zur Verfügung stehen.

5. Klicken Sie auf den Steuerelementtyp, zu dem Sie eine Bindung herstellen möchten.

6. Ziehen Sie das Feld in ein Formular. Das Steuerelement wird dem Formular hinzugefügt, zusammen mit einer <xref:System.Windows.Forms.BindingSource>-Komponente und einer <xref:System.Windows.Forms.BindingNavigator>-Komponente.

7. Wiederholen Sie die Schritte 4 bis 6 für alle anderen Felder, die Sie binden möchten.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Binden eines Steuerelements an einen zusammengesetzten von einem WCF-Dienst zurückgegebenen Typ

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**. Das Fenster **Datenquellen** wird angezeigt.

2. Erweitern Sie im Fenster **Datenquellen** den Knoten für Ihren Dienstverweis. Zusammengesetzte Typen, die vom Dienst zurückgegeben wurden, werden angezeigt.

3. Wählen Sie einen Knoten für einen Typ aus, und klicken Sie auf den Dropdownpfeil, um eine Liste verfügbarer Optionen anzuzeigen.

4. Klicken Sie entweder auf **DataGridView**, um die Daten in einem Raster anzuzeigen, oder auf **Details**, um die Daten in einzelnen Steuerelementen anzuzeigen.

5. Ziehen Sie den Knoten in das Formular. Die Steuerelemente werden dem Formular hinzugefügt, zusammen mit einer <xref:System.Windows.Forms.BindingSource>-Komponente und einer <xref:System.Windows.Forms.BindingNavigator>-Komponente.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Vorgehensweise: Konfigurieren eines Diensts für die Wiederverwendung vorhandener Typen

Wenn einem Projekt ein Dienstverweis hinzugefügt wird, werden alle im Dienst definierten Typen im lokalen Projekt generiert. In vielen Fällen führt dies zu duplizierten Typen, wenn ein Dienst gängige .NET-Typen nutzt oder wenn Typen in einer gemeinsam genutzten Bibliothek definiert werden.

Zur Vermeidung dieses Problems werden Typen in Assemblys, auf die verwiesen wird, standardmäßig freigegeben. Wenn Sie die Freigabe von Typen für eine oder mehrere Assemblys deaktivieren möchten, können Sie dies über das Dialogfeld **Dienstverweise konfigurieren** tun.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Deaktivieren der Freigabe von Typen in einer einzelnen Assembly

1. Wählen Sie im **Projektmappen-Explorer** den Dienstverweis aus.

2. Klicken Sie im Menü **Projekt** auf **Dienstverweis konfigurieren**.

3. Klicken Sie im Dialogfeld **Dienstverweise konfigurieren** auf **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**.

4. Klicken Sie für alle Assemblys, für die Sie die Freigabe von Typen aktivieren möchten, auf das Kontrollkästchen. Wenn Sie die Freigabe von Typen für eine Assembly deaktivieren möchten, lassen Sie das Kontrollkästchen leer.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Deaktivieren der Freigabe von Typen in allen Assemblys

1. Wählen Sie im **Projektmappen-Explorer** den Dienstverweis aus.

2. Klicken Sie im Menü **Projekt** auf **Dienstverweis konfigurieren**.

3. Entfernen Sie im Dialogfeld **Dienstverweise konfigurieren** das Häkchen aus dem Kontrollkästchen **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**.

## <a name="related-topics"></a>Verwandte Themen

| Titel | BESCHREIBUNG |
| - | - |
| [Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Hier finden Sie eine ausführliche Anleitung für das Erstellen und Verwenden von WCF-Diensten in Visual Studio. |
| [Exemplarische Vorgehensweise: Erstellen eines WCF-Datendiensts mit WPF und Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Hier finden Sie eine ausführliche Anleitung für das Erstellen und Verwenden von WCF Data Services in Visual Studio. |
| [Using the WCF development tools (Verwenden der WCF-Entwicklungstools)](/dotnet/framework/wcf/using-the-wcf-development-tools) | Hier wird erläutert, wie Sie WCF-Dienste in Visual Studio erstellen und testen. |
| | [How to: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Troubleshooting service references (Problembehandlung bei Dienstverweisen)](../data-tools/troubleshooting-service-references.md) | Hier finden Sie Informationen zu einigen häufig auftretenden Fehlern, die bei Dienstverweisen auftreten können, sowie dazu, wie Sie sie verhindern können. |
| [Debugging WCF services (Debuggen von WCF-Diensten)](../debugger/debugging-wcf-services.md) | Hier werden allgemeine Debugprobleme erläutert, die beim Debuggen von WCF-Diensten auftreten können, sowie Verfahren beschrieben, die hilfreich sein können. |
| [Exemplarische Vorgehensweise: Erstellen einer n-schichtigen Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Liefert eine Schritt-für-Schritt-Anleitung für das Erstellen eines typisierten Datasets und das Aufteilen des Codes für TableAdapter und Dataset in mehrere Projekte. |
| [Configure Service Reference dialog box (Dialogfeld „Dienstverweis konfigurieren“)](../data-tools/configure-service-reference-dialog-box.md) | Hier werden die Benutzeroberflächenelemente des Dialogfelds **Dienstverweis konfigurieren** beschrieben. |

## <a name="reference"></a>Referenz

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
