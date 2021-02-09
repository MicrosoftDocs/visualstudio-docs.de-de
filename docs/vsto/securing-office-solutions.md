---
title: Sichere Office-Lösungen
description: Erfahren Sie, wie das Sicherheitsmodell für Office-Lösungen verschiedene Technologien umfasst, einschließlich der Visual Studio-Tools für Office-Laufzeit und ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3576bdc41f25b95b68230e09e07b1a5ed97016c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906651"
---
# <a name="secure-office-solutions"></a>Sichere Office-Lösungen
  Das Sicherheitsmodell für Office-Lösungen umfasst verschiedene Technologien: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , das Trust Center in Microsoft Office und die Zone Eingeschränkte Sites in Internet Explorer. In den folgenden Abschnitten wird die Funktionsweise der verschiedenen Sicherheitsfunktionen beschrieben:

- [Gewähren von Vertrauenswürdigkeit für Office-Lösungen](#GrantingTrustToSolutions)

- [Gewähren von Vertrauenswürdigkeit für Dokumente](#GrantingTrustToDocuments)

- [Gewähren von Vertrauenswürdigkeit bei Verwendung von Windows Installer](#GrantingTrustWindowsInstaller)

- [Besondere Sicherheitsüberlegungen für Office-Lösungen](#Security)

- [Sicherheit während der Entwicklung](#SecurityDuringDeployment)

- [Visual Studio-Tools für Office-Laufzeit](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a> Gewähren von Vertrauenswürdigkeit für Office-Lösungen
 Das Gewähren von Vertrauenswürdigkeit für Office-Projektmappen bedeutet das Ändern der Sicherheitsrichtlinie jedes Endbenutzers, um der Office-Lösung auf Grundlage der folgenden Beweise zu vertrauen:

- Das Zertifikat, das zum Signieren des Bereitstellungsmanifests verwendet wird.

- Die URL des Bereitstellungsmanifests.

  Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office](../vsto/granting-trust-to-office-solutions.md)-Projektmappen.

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Gewähren von Vertrauenswürdigkeit für Dokumente
 Eine Anpassung auf Dokumentebene erfordert, dass sich das Dokument in einem Verzeichnis befindet, das als vertrauenswürdiger Speicherort festgelegt ist. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a> Gewähren von Vertrauenswürdigkeit bei Verwendung von Windows Installer
 Sie können Windows Installer verwenden, um eine MSI-Datei zum Installieren von Office-Projektmappen in das Verzeichnis "Programme" zu erstellen, wofür Administratorrechte erforderlich sind. Bei Office-Projektmappen im Verzeichnis "Programme" werden diese Office-Lösungen von Visual Studio 2010-Tools für Office-Laufzeit als vertrauenswürdig eingestuft, und die ClickOnce-Vertrauensstellungs Aufforderung wird nicht angezeigt.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a> Besondere Sicherheitsüberlegungen für Office-Lösungen
 Die Sicherheitsfeatures, die von [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] und Microsoft Office bereitgestellt werden, können zum Schutz vor verschiedenen Sicherheitsbedrohungen in Office-Projektmappen beitragen. Weitere Informationen finden Sie unter [spezifische Sicherheitsüberlegungen für Office](../vsto/specific-security-considerations-for-office-solutions.md)-Projektmappen.

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Sicherheit während der Entwicklung
 Um Ihren Entwicklungsprozess zu vereinfachen, legt Visual Studio die Sicherheitsrichtlinie, die zum Ausführen und Debuggen der Projektmappe auf dem Computer benötigt wird, bei jedem Erstellen eines Projekts fest. In einigen Szenarien müssen Sie möglicherweise zusätzliche Schritte zum Entwickeln des Projekts ausführen.

### <a name="document-level-solutions"></a>Projektmappen auf Dokument Ebene
 Wenn Sie die folgenden Typen von Projekten entwickeln, muss der vollqualifizierte Pfad eines Dokuments zur Liste der vertrauenswürdigen Speicherorte in der Microsoft Office-Anwendung hinzugefügt werden:

- Lösungen auf Dokument Ebene, die sich auf einer Netzwerkdatei Freigabe wie z. b. *\\ \servername\sharename* befinden.

- Projektmappen auf Dokument Ebene für Word, das *doc* -oder *DOCM* -Dateien verwendet.

  Schließen Sie die Unterverzeichnisse ein, wenn Sie den Dokumentspeicherort der Liste vertrauenswürdiger Speicherorte hinzufügen, oder schließen Sie insbesondere die Debug- und Buildordner ein. Weitere Informationen finden Sie im Microsoft Office Online Hilfeartikel [erstellen, entfernen oder Ändern eines vertrauenswürdigen Speicher Orts für Ihre Dateien](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Temporäre Zertifikate
 Visual Studio erstellt ein temporäres Zertifikat, wenn ein signierendes Zertifikat nicht bereits vorhanden ist. Sie sollten dieses temporäre Zertifikat nur während der Entwicklung verwenden und ein offizielles Zertifikat für die Bereitstellung erwerben.

 Das temporäre Zertifikat wird nach dem ersten Erstellen eines Office-Projekts generiert. Wenn Sie das nächste Mal **F5** drücken, wird das Projekt neu erstellt, da das Projekt beim Hinzufügen des Zertifikats als geändert markiert wird.

 Nach einer Weile kann es zahlreiche temporäre Zertifikate geben, sodass Sie sie gelegentlich löschen sollten.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio-Tools für Office-Laufzeit
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Verfügt über Funktionen zum Überprüfen der Identität des Verlegers und der Berechtigungen, die einer Anpassung gewährt werden. Diese Berechtigungen werden mithilfe einer Reihe von Sicherheitsüberprüfungen verifiziert.

### <a name="security-during-customization-loading"></a>Sicherheit beim Laden von Anpassungen
 Wenn eine Anpassung auf Dokument Ebene geladen wird, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] prüft immer, ob sich das Dokument in der Liste der vertrauenswürdigen Speicherorte befindet. Außerdem überprüft die Laufzeit, ob die Projektmappe im Anwendungsmanifest FullTrust anfordert. Beim Laden der Anpassung werden keine zusätzlichen Sicherheitsüberprüfungen durchgeführt.

### <a name="sequence-of-security-checks-during-installation"></a>Sequenz der Sicherheitsüberprüfungen während der Installation
 Wenn eine Office-Projektmappe installiert oder aktualisiert wird, führt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] eine Reihe von Sicherheitsüberprüfungen in einer bestimmten Reihenfolge aus, um eine Entscheidung über die Vertrauenswürdigkeit zu treffen. Eine Projektmappe wird nur dann installiert oder aktualisiert, wenn die Laufzeit bestimmt, dass die Projektmappe vertrauenswürdig ist.

 Sie können den Installationsvorgang auf eine von vier Arten starten: durch Ausführen des Setup Programms, durch Öffnen des Bereitstellungs Manifests, durch Öffnen des Microsoft Office Anwendungs Hosts oder durch Ausführen von *VSTOInstaller.exe*.

 Die erste Sicherheitsüberprüfung gilt nur für Projektmappen auf Dokumentebene. Das Dokument einer Projektmappe auf Dokumentebene muss sich an einem vertrauenswürdigen Speicherort befinden. Wenn sich das Dokument in einer Remote Netzwerk-Dateifreigabe befindet oder die Dateinamenerweiterung *. doc* oder *. docm* aufweist, muss der Speicherort des Dokuments der Liste vertrauenswürdiger Speicherorte hinzugefügt werden. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).

 ![VSTO-Sicherheit – Installation aus Microsoft Office](../vsto/media/host-install.png "VSTO-Sicherheit – Installation aus Microsoft Office")

 Die nächsten Sicherheitsüberprüfungen erfolgen durch [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und ClickOnce. Um diese Überprüfungen zu bestehen, müssen Office-Projektmappen FullTrust-Berechtigungen anfordern, mit einem Zertifikat signiert werden, das nicht in der Liste der nicht vertrauenswürdigen Herausgeber aufgeführt ist, und sich an einem Speicherort befinden, der sich nicht in der eingeschränkten Zone von Internet Explorer befindet. Wenn sich das Zertifikat in der Liste vertrauenswürdiger Herausgeber befindet, wird die Projektmappe sofort installiert. Andernfalls fährt die Lösung mit der letzten letzte Gruppe von Überprüfungen fort, sofern keine der Überprüfungen fehlgeschlagen ist.

 ![VSTO-Sicherheit für Installation von Lösungen](../vsto/media/installing.png "VSTO-Sicherheit für Installation von Lösungen")

 Wenn die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Vertrauensstellungs Aufforderung zulässig ist und der Lösung noch keine Vertrauensstellung gewährt wurde, kann die Laufzeit die Entscheidung über die Vertrauenswürdigkeit durch den Endbenutzer treffen. Wenn der Benutzer der Projektmappe Vertrauenswürdigkeit gewährt, wird der Benutzeraufnahmeliste ein Eintrag hinzugefügt. Alle Projektmappen in der Benutzeraufnahmeliste haben volle Vertrauenswürdigkeit und können installiert und ausgeführt werden.

 Ab Visual Studio 2010 wird die Aufnahmeliste umgangen, wenn die Office-Projektmappe mithilfe von Windows Installer (MSI) in das Verzeichnis "Programme" installiert wurde. Weitere Informationen finden Sie unter [Vertrauen von Office-Projektmappen mithilfe von Inklusions Listen](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![VSTO-Sicherheit – Installation mit dem Setupprogramm](../vsto/media/setup-vstoinstaller.png "VSTO-Sicherheit – Installation mit dem Setupprogramm")

## <a name="see-also"></a>Weitere Informationen

- [Gewähren von Vertrauenswürdigkeit für Office-Lösungen](../vsto/granting-trust-to-office-solutions.md)
- [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md)
- [Vertrauen von Office-Projektmappen mithilfe von Inklusions Listen](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Vorgehensweise: Konfigurieren der Sicherheit für die Aufnahme Liste](../vsto/how-to-configure-inclusion-list-security.md)
- [Gewusst wie: Signieren von Office-Lösungen](../vsto/how-to-sign-office-solutions.md)
- [Behandeln von Problemen mit der Sicherheit von Office](../vsto/troubleshooting-office-solution-security.md)
- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Referenz](../deployment/clickonce-reference.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
