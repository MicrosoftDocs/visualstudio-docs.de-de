---
title: Arbeiten mit Daten in Visual Studio
description: Arbeiten mit Daten in Visual Studio. Erstellen Sie apps, die eine Verbindung mit Daten in anderen Datenbankprodukten oder-Diensten über lokale Computer, LANs oder öffentliche oder Private Clouds herstellen.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 846898c1cf93d0f90ce04e77ee93bd8802e22ec2
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382090"
---
# <a name="work-with-data-in-visual-studio"></a>Arbeiten mit Daten in Visual Studio

In Visual Studio können Sie Anwendungen erstellen, die eine Verbindung mit Daten in praktisch allen Datenbankprodukten oder-Diensten in beliebiger Form herstellen – auf einem lokalen Computer, in einem lokalen Netzwerk oder in einem öffentlichen, privaten oder Hybrid Cloud.

Für Anwendungen in JavaScript, Python, PHP, Ruby oder C++ Stellen Sie eine Verbindung mit Daten her, wie Sie nichts anderes tun, indem Sie Bibliotheken abrufen und Code schreiben. Für .NET-Anwendungen stellt Visual Studio Tools bereit, die Sie zum Durchsuchen von Datenquellen, zum Erstellen von Objekt Modellen zum Speichern und Bearbeiten von Daten im Arbeitsspeicher und zum Binden von Daten an die Benutzeroberfläche verwenden können. Microsoft Azure bietet sdert für .net-, Java-, Node.js-, PHP-, Python-, Ruby-und Mobile-Apps sowie Tools in Visual Studio zum Herstellen einer Verbindung mit Azure Storage.

::: moniker range="vs-2017"
Die folgenden Listen enthalten nur einige der vielen Daten Bank-und Speichersysteme, die in Visual Studio verwendet werden können. Die [Microsoft Azure](https://azure.microsoft.com/) Angebote sind Datendienste, die die gesamte Bereitstellung und Verwaltung des zugrunde liegenden Datenspeicher beinhalten. Mit der Arbeitsauslastung für die **Azure-Entwicklung** in [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) können Sie direkt in Visual Studio mit Azure-Daten speichern arbeiten.
::: moniker-end
::: moniker range=">=vs-2019"
Die folgenden Listen enthalten nur einige der vielen Daten Bank-und Speichersysteme, die in Visual Studio verwendet werden können. Die [Microsoft Azure](https://azure.microsoft.com/) Angebote sind Datendienste, die die gesamte Bereitstellung und Verwaltung des zugrunde liegenden Datenspeicher beinhalten. Mit der Arbeitsauslastung für die **Azure-Entwicklung** in [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) können Sie direkt in Visual Studio mit Azure-Daten speichern arbeiten.
::: moniker-end

![Workload „Azure-Entwicklung“](media/azure-development-workload.png)

Die meisten anderen in diesem Abschnitt aufgeführten SQL-und nosql-Daten Bankprodukte können auf einem lokalen Computer, in einem lokalen Netzwerk oder in Microsoft Azure auf einem virtuellen Computer gehostet werden. Wenn Sie die Datenbank auf einem Microsoft Azure virtuellen Computer hosten, sind Sie für die Verwaltung der Datenbank selbst verantwortlich.

**Microsoft Azure**

- SQL-Datenbank
- Azure Cosmos DB
- Speicher (BLOB, Tabellen, Warteschlangen, Dateien)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- Und vieles mehr...

**SQL**

- SQL Server 2005-2016 (einschließlich Express und localdb)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- Und vieles mehr...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatenbank
- OrientDB|
- RavenDB
- VelocityDB
- Und vieles mehr...

::: moniker range="vs-2017"

Viele Datenbankanbieter und Drittanbieter unterstützen die Visual Studio-Integration von nuget-Paketen. Sie können die Angebote auf nuget.org oder über den nuget-Paket-Manager in Visual Studio unter **Suchen (Extras**  >  **nuget-Paket-Manager**  >  **nuget-Pakete für** Projekt Mappe verwalten). Andere Daten Bankprodukte werden in Visual Studio als Erweiterung integriert. Sie können diese Angebote im [Visual Studio Marketplace](https://marketplace.visualstudio.com/) durchsuchen **oder zu Extras**  >  **Erweiterungen und Updates** navigieren und dann im linken Bereich des Dialog Felds **Online** auswählen. Weitere Informationen finden Sie unter [kompatible Datenbanksysteme für Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Viele Datenbankanbieter und Drittanbieter unterstützen die Visual Studio-Integration von nuget-Paketen. Sie können die Angebote auf nuget.org oder über den nuget-Paket-Manager in Visual Studio unter **Suchen (Extras**  >  **nuget-Paket-Manager**  >  **nuget-Pakete für** Projekt Mappe verwalten). Andere Daten Bankprodukte werden in Visual Studio als Erweiterung integriert. Sie können diese Angebote im [Visual Studio Marketplace](https://marketplace.visualstudio.com/) durchsuchen oder zu Erweiterungen Erweiterungen **Extensions**  >  **Verwalten** navigieren und dann im linken Bereich des Dialog Felds **Online** auswählen. Weitere Informationen finden Sie unter [kompatible Datenbanksysteme für Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Der erweiterte Support für SQL Server 2005 wurde am 12. April 2016 eingestellt. Es gibt keine Garantie dafür, dass Data Tools in Visual Studio 2015 und höher weiterhin mit SQL Server 2005 funktionieren. Weitere Informationen finden Sie in der [Ankündigung zum Ende des Supports für SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>.NET-Sprachen

Alle .NET-Daten Zugriffe, einschließlich in .net Core, basieren auf ADO.net, einer Reihe von Klassen, die eine Schnittstelle für den Zugriff auf eine beliebige Art von Datenquelle definieren, sowohl relationale als auch nicht relationale. Visual Studio verfügt über mehrere Tools und Designer, die mit ADO.NET verwendet werden können, um eine Verbindung mit Datenbanken herzustellen, die Daten zu bearbeiten und die Daten dem Benutzer vorzustellen. In der Dokumentation in diesem Abschnitt wird beschrieben, wie diese Tools verwendet werden. Sie können auch direkt mit den ADO.NET-Befehls Objekten programmieren. Weitere Informationen zum direkten Aufrufen der ADO.NET-APIs finden Sie unter [ADO.net](/dotnet/framework/data/adonet/index).

Informationen zur Datenzugriffs Dokumentation im Zusammenhang mit ASP.net finden Sie unter [Arbeiten mit Daten](https://www.asp.net/web-forms/overview/presenting-and-managing-data) auf der ASP.NET-Website. Ein Tutorial zur Verwendung von Entity Framework mit ASP.NET MVC finden [Sie unter Getting Started with Entity Framework 6 Code First using MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Universelle Windows-Plattform-Apps (UWP) in c# oder Visual Basic können mithilfe des Microsoft Azure SDK für .net auf Azure Storage und andere Azure-Dienste zugreifen. Die Windows. Web. HttpClient-Klasse ermöglicht die Kommunikation mit einem beliebigen Rest-Dienst. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem HTTP-Server mithilfe von Windows. Web. http](/previous-versions/windows/apps/dn469430(v=win.10)).

Für die Datenspeicherung auf dem lokalen Computer wird empfohlen, SQLite zu verwenden, das in demselben Prozess wie die app ausgeführt wird. Wenn eine ORM-Ebene (Object-Relational Mapping) erforderlich ist, können Sie Entity Framework verwenden. Weitere Informationen finden Sie unter [Datenzugriff](/windows/uwp/data-access/index) im Windows Developer Center.

Wenn Sie eine Verbindung mit Azure-Diensten herstellen, stellen Sie sicher, dass Sie die neuesten [Azure SDK-Tools](https://azure.microsoft.com/downloads/)herunterladen.

### <a name="data-providers"></a>Datenanbieter

Damit eine Datenbank in ADO.net verwendbar ist, muss Sie über einen benutzerdefinierten *ADO.NET-Datenanbieter* verfügen, oder es muss eine ODBC-oder OLE DB-Schnittstelle verfügbar gemacht werden. Microsoft bietet eine [Liste von ADO.NET-Datenanbietern](/dotnet/framework/data/adonet/ado-net-overview) für SQL Server Produkte sowie ODBC-und OLE DB-Anbieter.

### <a name="data-modeling"></a>Datenmodellierung

In .net haben Sie drei Möglichkeiten, um Daten im Arbeitsspeicher zu modellieren und zu bearbeiten, nachdem Sie Sie aus einer Datenquelle abgerufen haben:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Die bevorzugte Microsoft ORM-Technologie. Sie können Sie verwenden, um für relationale Daten als erstklassige .NET-Objekte zu programmieren. Bei neuen Anwendungen sollte es sich um die standardmäßige erste Wahl handeln, wenn ein Modell erforderlich ist. Hierfür ist eine benutzerdefinierte Unterstützung des zugrunde liegenden ADO.NET-Anbieters erforderlich.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Ein objektrelationaler Mapper der früheren Generation. Dies funktioniert gut für weniger komplexe Szenarien, ist jedoch nicht mehr in der aktiven Entwicklung.

[DataSets](../data-tools/dataset-tools-in-visual-studio.md) Die älteste der drei Modellierungs Technologien. Es wurde hauptsächlich für die schnelle Entwicklung von "Forms over Data"-Anwendungen entwickelt, bei denen keine großen Datenmengen verarbeitet werden oder komplexe Abfragen oder Transformationen ausgeführt werden. Ein DataSet-Objekt besteht aus Datable-und DataRow-Objekten, die SQL-Datenbankobjekten wesentlich mehr als .NET-Objekte ähneln. Für relativ einfache Anwendungen, die auf SQL-Datenquellen basieren, sind Datasets möglicherweise trotzdem eine gute Wahl.

Es ist nicht erforderlich, eine dieser Technologien zu verwenden. In einigen Szenarien, insbesondere bei kritischer Leistung, können Sie einfach ein DataReader-Objekt verwenden, um Daten aus der Datenbank zu lesen und die Werte, die Sie benötigen, in ein Auflistungs Objekt, z. b. List, zu kopieren \<T> .

## <a name="native-c"></a>Systemeigenes C++

C++-Anwendungen, die eine Verbindung mit SQL Server herstellen, sollten in den meisten Fällen den [Microsoft® ODBC-Treiber 13,1 für SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) verwenden. Wenn die Server verknüpft sind, ist OLE DB erforderlich, damit Sie die [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)verwenden können. Sie können auf andere Datenbanken zugreifen, indem Sie [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017&preserve-view=true) oder OLE DB Treiber direkt verwenden. ODBC ist die aktuelle Standarddaten bankschnittstelle, aber die meisten Datenbanksysteme bieten benutzerdefinierte Funktionen, auf die über die ODBC-Schnittstelle nicht zugegriffen werden kann. OLE DB ist eine veraltete com-Datenzugriffs Technologie, die weiterhin unterstützt wird, aber für neue Anwendungen nicht empfohlen wird. Weitere Informationen finden Sie unter [Datenzugriff in Visual C++](/cpp/data/data-access-in-cpp).

C++-Programme, die Rest-Dienste nutzen, können das [C++-Rest-SDK](https://github.com/Microsoft/cpprestsdk)verwenden.

C++-Programme, die mit Microsoft Azure Storage arbeiten, können den [Microsoft Azure Storage-Client](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)verwenden.

Datenmodellierung &mdash; Visual Studio stellt keine ORM-Ebene für C++ bereit. [ODB](https://www.codesynthesis.com/products/odb/) ist eine beliebte Open Source-ORM für C++.

Weitere Informationen zum Herstellen einer Verbindung mit Datenbanken aus C++-apps finden Sie unter [Visual Studio Data Tools für C++](../data-tools/visual-studio-data-tools-for-cpp.md). Weitere Informationen zu Legacy-Visual C++ Datenzugriffs Technologien finden Sie unter [Datenzugriff](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript in Visual Studio](/scripting/javascript/javascript-language-reference) ist eine erstklassige Sprache zum Entwickeln von plattformübergreifenden apps, UWP-apps, Cloud Services, Websites und Web-Apps. Sie können Bower, Grunt, Gulp, NPM und nuget in Visual Studio verwenden, um Ihre bevorzugten JavaScript-Bibliotheken und-Daten Bankprodukte zu installieren. Stellen Sie eine Verbindung mit Azure Storage und Diensten her, indem Sie sdken von der [Azure-Website](https://azure.microsoft.com/)herunterladen Edge.js ist eine Bibliothek, die serverseitiges JavaScript (Node.js) mit ADO.NET-Datenquellen verbindet.

## <a name="python"></a>Python

Installieren [der Python-Unterstützung in Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) zum Erstellen von Python-Anwendungen. Die Azure-Dokumentation enthält mehrere Tutorials zum Verbinden mit Daten, einschließlich der folgenden:

- [Django und SQL-Datenbank in Azure](/azure/app-service/app-service-web-get-started-python)
- [Django und MySQL in Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Arbeiten mit [blobdateien](/azure/storage/blobs/storage-quickstart-blobs-python), [Dateien](/azure/storage/files/storage-python-how-to-use-file-storage), [Warteschlangen](/azure/storage/queues/storage-python-how-to-use-queue-storage)und [Tabellen (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Verwandte Themen

[Microsoft Ki-Plattform](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Bietet eine Einführung in die Microsoft Intelligent Cloud, einschließlich der Cortana Analytics Suite und der Unterstützung für Internet der Dinge.

[Microsoft Azure Storage](/azure/storage/) &mdash; Beschreibt Azure Storage und das Erstellen von Anwendungen mithilfe von Azure-blobdateien,-Tabellen,-Warteschlangen und-Dateien.

[Azure SQL-Datenbank](/azure/sql-database/) &mdash; Beschreibt das Herstellen einer Verbindung mit Azure SQL-Datenbank, einem relationalen Database as a Service.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Beschreibt die Tools, die das Entwerfen, durchsuchen, testen und Bereitstellen von Daten verbundenen Anwendungen und Datenbanken vereinfachen.

[ADO.net](/dotnet/framework/data/adonet/index) &mdash; Beschreibt die ADO.NET-Architektur und die Verwendung der ADO.NET-Klassen zum Verwalten von Anwendungsdaten und interagieren mit Datenquellen und XML.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Beschreibt, wie Sie Daten Anwendungen erstellen, die es Entwicklern ermöglichen, anstelle einer relationalen Datenbank direkt mit einem konzeptionellen Modell zu programmieren.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index) &mdash; Beschreibt, wie verwendet wird, [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] um Datendienste im Internet oder in einem Intranet bereitzustellen, die die [Open Data Protocol (odata)](https://www.odata.org/)implementieren.

[Daten in Office](../vsto/data-in-office-solutions.md) &mdash; -Projektmappen Enthält Links zu Themen, in denen die Funktionsweise von Daten in Office-Lösungen erläutert wird. Dazu gehören Informationen über schemaorientierte Programmierung, Datenzwischenspeicherung und serverseitigen Datenzugriff.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) &mdash; Beschreibt die in c# und Visual Basic integrierten Abfragefunktionen und das gängige Modell zum Abfragen von relationalen Datenbanken, XML-Dokumenten, Datasets und in-Memory-Auflistungen.

[XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; Erläutert das Arbeiten mit XML-Daten, das Debuggen von XSLT, .NET-XML-Funktionen und die Architektur von XML Query.

[XML-Dokumente und-Daten](/dotnet/standard/data/xml/index) &mdash; Bietet einen Überblick über einen umfassenden und integrierten Satz von Klassen, die mit XML-Dokumenten und-Daten in .net funktionieren.