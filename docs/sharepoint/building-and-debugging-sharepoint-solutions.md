---
title: Erstellen und Debuggen von SharePoint-Lösungen | Microsoft-Dokumentation
description: Hier wird erläutert, wie Sie SharePoint-Lösungen erstellen und debuggen. Außerdem erfahren Sie, inwiefern sich dies vom Erstellen und Debuggen anderer Projekttypen in Visual Studio unterscheidet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c16414e6a49d727cf6b2113184c507feb7a73569
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955787"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Erstellen und Debuggen von SharePoint-Lösungen
  Im Allgemeinen gleicht das Erstellen und Debuggen von SharePoint-Lösungen dem Erstellen und Debuggen von anderen Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Die vorhandenen Unterschiede werden in diesen Themen des Abschnitts erläutert.

## <a name="project-output-for-sharepoint-solutions"></a>Projektausgabe für SharePoint-Lösungen
 Beim Erstellen von SharePoint-Lösungen werden Assemblys und ein Lösungspaket (*WSP*) erstellt. In der folgenden Tabelle sind die Speicherorte dieser Dateien während eines Builds aufgeführt.

|Buildelement|Ausgabeordner|
|----------------|-------------------|
|Assemblydateien, Programmdatenbankdateien (*PDB*) und *WSP*-Dateien|*\<ProjectName>\bin\debug* oder *\<ProjectName>\bin\release*|
|SharePoint-Projektelementdateien|*\<ProjectName>\pkg\debug* oder *\<ProjectName>\pkg\release*|
|Erstellen von Zwischendateien|*\<ProjectName>\obj\debug* oder *\<ProjectName>\obj\release*|
|Packen von Zwischendateien|*\<ProjectName>\pkgobj\debug* oder *\<ProjectName>\pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Erstellen von SharePoint-Lösungen
 Auf dem Entwicklungscomputer muss die richtige Version des SharePoint-Servers installiert sein, um SharePoint-Lösungen zu erstellen. Andernfalls gleicht das Erstellen von SharePoint-Lösungen dem Erstellen anderer Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von SharePoint-Lösungen](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Debuggen und Testen von SharePoint-Lösungen
 Vor dem Debuggen kopiert [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] das *WSP*-Paket auf den SharePoint-Server, aktiviert die Website- und Webfeatures und startet unter Umständen das Projekt. In anderen Fällen müssen Sie das Projekt möglicherweise manuell öffnen. Weitere Informationen finden Sie unter [Behandeln von Problemen im Zusammenhang mit SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md) und [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Debuggen und Überprüfen von SharePoint-Lösungen mithilfe von Azure DevOps Services-Features
 Azure DevOps Services-Features wie Unittests und IntelliTrace ermöglichen es Ihnen, Probleme in Ihren SharePoint-Lösungen genauer zu lokalisieren. Mit der Profilerstellung können Sie Bereiche mit Leistungsproblemen in Ihren SharePoint-Lösungen leichter identifizieren. Weitere Informationen finden Sie unter [Überprüfen und Debuggen von SharePoint-Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) und [Profilerstellung für die Leistung von SharePoint-Anwendungen](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Sicherheit während des Buildprozesses
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] muss über die Berechtigung zum Kopieren von Dateien auf den SharePoint-Server verfügen, um SharePoint-Lösungen zu packen oder bereitzustellen. Sie müssen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] als erweiterten Prozess ausführen, und Ihr Benutzerkonto muss ein Websitesammlungsadministrator auf dem SharePoint-Server sein. Außerdem müssen Sie angeben, ob es sich bei dem Projekt um eine Sandbox- oder Farmlösung handelt. Weitere Informationen finden Sie unter [Unterschiede zwischen Sandbox- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Verwenden des Befehls „Bereinigen“
 Wenn eine SharePoint-Lösung zum Debuggen auf einem SharePoint-Server installiert ist, wird die Lösung mit dem Befehl **Bereinigen** nicht deinstalliert. Stattdessen müssen Sie die Features über die SharePoint-Konfiguration deaktivieren.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
