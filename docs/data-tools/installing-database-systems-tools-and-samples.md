---
title: Daten Bank Kompatibilität
description: Überprüfen Sie die kompatiblen Datenbanksysteme für Visual Studio, z. b. Microsoft SQL Server, Oracle, MySQL, PostgreSQL, SQLite und Firebird.
ms.custom: SEO-VS-2020
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 598d48d560db58a40b04e9d7684e98df22291a6a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434854"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Kompatible Datenbanksysteme für Visual Studio

Zum Entwickeln einer mit einem Daten verbundenen Anwendung in Visual Studio installieren Sie in der Regel das Datenbanksystem auf dem lokalen Entwicklungs Computer und stellen die Anwendung und die Datenbank anschließend in einer Produktionsumgebung bereit, wenn Sie bereit sind. Visual Studio installiert SQL Server Express localdb auf dem Computer im Rahmen der **Datenspeicher-und Verarbeitungs** Arbeitsauslastung. Diese localdb-Instanz ist nützlich für die schnelle und einfache Entwicklung von Anwendungen, die mit Daten verbunden sind.

Damit ein Datenbanksystem von .NET-Anwendungen zugänglich ist und in Visual Studio Data Tools-Fenstern sichtbar ist, muss es über einen ADO.NET-Datenanbieter verfügen. Ein Anbieter muss Entity Framework speziell unterstützen, wenn Sie die Verwendung von Entity Data Models in der .NET-Anwendung planen. Viele Anbieter werden über den nuget-Paket-Manager oder über die Visual Studio Marketplace angeboten.

Wenn Sie Azure Storage-APIs verwenden, installieren Sie die Azure-Speicher Emulatoren auf dem lokalen Computer während der Entwicklung, um Kosten zu vermeiden, bis Sie bereit für die Bereitstellung in der Produktionsumgebung sind. Weitere Informationen finden Sie unter [Verwenden des Azure-Speicheremulators für Entwicklung und Tests](/azure/storage/common/storage-use-emulator).

Die folgende Liste enthält einige der beliebtesten Datenbanksysteme, die in Visual Studio-Projekten verwendet werden können. Die Liste ist nicht vollständig. Eine Liste von Drittanbietern, die ADO.NET-Datenanbieter anbieten, die eine umfassende Integration in Visual Studio-Tools ermöglichen, finden Sie unter [ADO.NET Data Providers](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server ist das Microsoft-Flaggschiff-Datenbankangebot. SQL Server 2016 bietet bahnbrechende Leistung, erweiterte Sicherheit und umfangreiche, integrierte Berichte und Analysen. Es ist in verschiedenen Editionen enthalten, die für unterschiedliche Zwecke entwickelt wurden: von hochgradig skalierbaren, hochleistungsfähigen Business Analytics-Funktionen für die Verwendung auf einem einzelnen Computer. SQL Server Express ist eine voll ausgestattete Edition von SQL Server, die auf die Verteilung und Einbettung zugeschnitten ist.  Localdb ist eine vereinfachte Edition von SQL Server Express, die keine Konfiguration erfordert und im Prozess ihrer Anwendung ausgeführt wird. Sie können entweder oder beide Produkte von der [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)herunterladen. Viele der SQL-Beispiele in diesem Abschnitt verwenden SQL Server localdb. SQL Server Management Studio (SSMS) ist eine eigenständige Daten Bank Verwaltungs Anwendung mit mehr Funktionalität als in Visual Studio SQL Server-Objekt-Explorer bereitgestellt. Sie können SSMS über den vorherigen Link erhalten.

## <a name="oracle"></a>Oracle

Sie können eine kostenpflichtige oder kostenlose Edition der Oracle-Datenbank von der Seite [Oracle Technology Network](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) herunterladen. Zur Entwurfszeit Unterstützung für Entity Framework und TableAdapters benötigen Sie die [Oracle Developer Tools für Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Andere offizielle Oracle-Produkte, einschließlich des Oracle Instant Client, sind über den nuget-Paket-Manager verfügbar. Sie können Oracle-Beispiel Schemas herunterladen, indem Sie die Anweisungen in der [Oracle-Online Dokumentation](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)befolgen.

## <a name="mysql"></a>MySQL

MySQL ist ein gängiges Open-Source-Datenbanksystem, das in Unternehmen und Websites häufig verwendet wird. Downloads für MySQL, MySQL für Visual Studio und Verwandte Produkte finden Sie unter [MySQL unter Windows](https://www.mysql.com/why-mysql/windows/). Drittanbieter bieten verschiedene Visual Studio-Erweiterungen und eigenständige Verwaltungs Anwendungen für MySQL. Sie können die Angebote im nuget-Paket-Manager durch **Suchen (Extras**  >  **nuget-Paket-Manager**  >  **nuget-Pakete für** Projekt Mappe verwalten).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL ist ein kostenloses Open-Source-Objekt für relationale Datenbanken. Um es unter Windows zu installieren, können Sie es von der [PostgreSQL-Downloadseite](https://www.postgresql.org/download/windows/)herunterladen. Sie können PostgreSQL auch aus dem Quellcode erstellen. Das PostgreSQL-Kernsystem umfasst eine Schnittstelle der Programmiersprache C. Viele Drittanbieter stellen nuget-Pakete für die Verwendung von PostgreSQL aus .NET-Anwendungen bereit. Sie können die Angebote im nuget-Paket-Manager durch **Suchen (Extras**  >  **nuget-Paket-Manager**  >  **nuget-Pakete für** Projekt Mappe verwalten). Möglicherweise wird das beliebteste Paket von [npgsql.org](http://www.npgsql.org)bereitgestellt.

## <a name="sqlite"></a>SQLite

SQLite ist eine eingebettete SQL-Datenbank-Engine, die im eigenen Prozess der Anwendung ausgeführt wird. Sie können es von der [SQLite-Downloadseite](https://www.sqlite.org/download.html)herunterladen. Viele nuget-Pakete von Drittanbietern für SQLite sind ebenfalls verfügbar. Sie können die Angebote im nuget-Paket-Manager durch **Suchen (Extras**  >  **nuget-Paket-Manager**  >  **nuget-Pakete für** Projekt Mappe verwalten).

## <a name="firebird"></a>Firebird

Firebird ist ein Open-Source-SQL-Datenbanksystem. Sie können es von der [Downloadseite von Firebird](http://firebirdsql.org/en/downloads/)herunterladen. Ein ADO.NET-Datenanbieter ist über den nuget-Paket-Manager verfügbar.

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Informationen zum Ermitteln der Version und Edition von SQL Server und zugehöriger Komponenten](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
