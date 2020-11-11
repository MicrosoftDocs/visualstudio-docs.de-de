---
title: Datenbankprojekte und DAC-Projekte
description: Informieren Sie sich über Datenbankprojekte und Datenebenenanwendungen (DACs). Verwenden Sie DB-Projekte, um neue Datenbanken zu erstellen, neue DACs zu erstellen und vorhandene Datenbanken und DACs zu aktualisieren.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 57b889f025b06e127e8e4bb38be311f6bbe55952
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436601"
---
# <a name="database-projects-and-data-tier-applications"></a>Datenbankprojekte und Datenebenenanwendungen

Sie können Datenbankprojekte zum Erstellen neuer Datenbanken, neuer Datenebenenanwendungen (DACs) und zum Aktualisieren vorhandener Datenbanken und Datenebenenanwendungen verwenden. Sowohl Datenbankprojekte als auch DAC-Projekte ermöglichen es Ihnen, Versionskontrolle und Projekt Verwaltungsverfahren auf die Datenbankentwicklung anzuwenden, ähnlich wie Sie diese Techniken auf verwalteten oder systemeigenen Code anwenden. Sie können dem Entwicklungsteam dabei helfen, Änderungen an Datenbanken und Datenbankservern zu verwalten, indem Sie ein DAC-Projekt, ein Datenbankprojekt oder ein Server Projekt erstellen und es in die Versionskontrolle versetzen. Mitglieder des Teams können dann Dateien Auschecken, um Änderungen in einer isolierten Entwicklungsumgebung oder in einem Sandkasten auszuführen, zu erstellen und zu testen, bevor Sie Sie für das Team freigeben. Um die Codequalität zu gewährleisten, kann Ihr Team alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung abschließen und testen, bevor Sie die Änderungen in der Produktionsumgebung bereitstellen.

Eine Liste der Datenbankfunktionen, die von Datenebenenanwendungen unterstützt werden, finden Sie [unter DAC-Unterstützung für SQL Server Objekte](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Wenn Sie Funktionen in der Datenbank verwenden, die nicht von Datenebenenanwendungen unterstützt werden, sollten Sie stattdessen ein Datenbankprojekt verwenden, um Änderungen an der Datenbank zu verwalten.

## <a name="common-high-level-tasks"></a>Allgemeine allgemeine Aufgaben

| High-Level Aufgabe | Hilfreiche Themen |
| - | - |
| **Beginnen Sie mit der Entwicklung einer Datenebenenanwendung:** Das Konzept einer Datenebenenanwendung (DAC) wurde mit SQL Server 2008 eingeführt. Eine DAC enthält die Definition für eine SQL Server Datenbank und die unterstützenden Instanzobjekte, die von einer Client-oder 3-Tier-Anwendung verwendet werden. Eine DAC enthält Datenbankobjekte, z. b. Tabellen und Sichten, sowie instanzentitäten, z. b. Anmeldungen. Sie können Visual Studio verwenden, um ein DAC-Projekt zu erstellen, eine DAC-Paketdatei zu erstellen und die DAC-Paketdatei an einen Datenbankadministrator für die Bereitstellung auf einer Instanz der SQL Server Datenbank-Engine zu senden. | - [Datenebenenanwendungen](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Ausführen einer iterativen Datenbankentwicklung:** Entwickler können Teile des Projekts auschecken und in einer isolierten Entwicklungsumgebung aktualisieren. Mit dieser Art von Umgebung können Sie Ihre Änderungen testen, ohne dass sich dies auf andere Mitglieder des Teams auswirkt. Nachdem die Änderungen vorgenommen wurden, überprüfen Sie die Dateien wieder in die Versionskontrolle, wo andere Teammitglieder ihre Änderungen abrufen und auf einem Testserver bereitstellen können. | - [Projektorientierte Offline Datenbankentwicklung (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Transact-SQL-Debugger (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Prototypen, überprüfen von Testergebnissen und Ändern von Daten Bank Skripts und Objekten:** Sie können den Transact-SQL-Editor verwenden, um eine dieser allgemeinen Aufgaben auszuführen. | - [Abfrage-und Text-Editoren (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
