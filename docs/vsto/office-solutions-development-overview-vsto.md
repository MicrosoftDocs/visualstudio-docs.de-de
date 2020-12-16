---
title: Übersicht über die Entwicklung von Office-Lösungen (VSTO)
description: Erfahren Sie, wie Sie Anpassungen für die vertrauten Microsoft Office Benutzeroberflächen und-Tools entwickeln, wie z. b. die Textverarbeitungsfunktionen in Word und die Datenanalyse Funktionen von Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9bb964e90c44c4e0b41e0f09df8931665426dc70
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527719"
---
# <a name="office-solutions-development-overview-vsto"></a>Übersicht über die Entwicklung von Office-Lösungen (VSTO)
  Wenn Sie Microsoft Office als Front-End für Projektmappen verwenden, können Sie die vertrauten Microsoft Office-Benutzeroberflächen und -Tools verwenden, z. B. die Textverarbeitungsfunktionen in Word, die Datenanalysefunktionen von Excel und die E-Mail-Verwaltungsfunktionen von Outlook. Sie können Projektmappen in Visual Studio entwickeln, um Office-Anwendungen anzupassen und die speziellen Funktionen hinzuzufügen, die Sie für Ihre Geschäftsprozesse benötigen. Beispielsweise können Sie Word in einen Vertragsgenerator verwandeln, mit dem Verträge aus bereits vorhandenen Teilen zusammengestellt werden können. Die Teile können dabei bearbeitbar oder nicht bearbeitbar sein. Mit Excel können Sie ein automatisiertes Budgetarbeitsblatt erstellen, das für unterschiedliche Projekte angepasst werden kann. Ihre Benutzer können Bürolösungen auch offline verwenden. Dies ist bei komplexen Lösungen praktikabler als die Verwendung einer webbasierten Architektur.

 Dieses Thema enthält eine Übersicht über die Arten von Office-Lösungen, die Sie mit den Vorlagen vom Typ "Visual Studio-Tools für Office" (VSTO) erstellen können. Sie sind in den Office Developer Tools von Visual Studio enthalten. Allgemeine Informationen zur Entwicklung mit Office finden Sie im [Office Developer Center](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Auswählen eines Office-Projekt Typs
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] stellt die folgenden Arten von Projektvorlagen für die VSTO-basierte Office-Entwicklung bereit:

- **Anpassungen auf Dokumentebene** sind mit einem bestimmten Dokument verknüpft.

- **VSTO Add-ins** sind mit der Anwendung selbst verknüpft.

  Für die Entscheidung, welche dieser Projekttypen für Ihre Lösung am besten geeignet ist, sollten Sie sich folgende Frage stellen: Möchten Sie, dass Ihr Code nur ausgeführt wird, wenn ein bestimmtes Dokument geöffnet ist, oder soll der Code immer verfügbar sein, wenn die Anwendung ausgeführt wird. Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

  Welche Typen von Projekten Sie erstellen können, hängt davon ab, welche Office-Anwendungen Sie auf dem Entwicklungscomputer installiert haben. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Anpassungen auf Dokumentebene
 Anpassungen auf Dokumentebene bestehen aus einer Assembly, die einem einzelnen Dokument, einer Arbeitsmappe oder einer Vorlage in Microsoft Office Word oder Microsoft Office Excel zugeordnet ist. Dies Assembly wird geladen, wenn das zugeordnete Dokument geöffnet wird. Funktionen in von Ihnen erstellten Anpassungen sind nur verfügbar, wenn das zugeordnete Dokument geöffnet ist. Mit Anpassungen können keine anwendungsweiten Änderungen vorgenommen werden, z. B. das Anzeigen eines neuen Menüelements oder einer Menübandregisterkarte, wenn ein Dokument geöffnet ist.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält Tools, die für die Erstellung von Anpassungen auf Dokumentebene hilfreich sind. Das Dokument, das Sie anpassen, wird in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]als Entwurfsoberfläche gehostet. So können Sie das Dokument entwerfen, indem Sie Steuerelemente ziehen und darauf ablegen. Für Projekte auf Dokumentebene sind noch viele weitere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Funktionen verfügbar, z. B. Windows Forms-Steuerelemente, Drag &amp; Drop-Datenbindung und ein integrierter Debugger.

 Weitere Informationen zu Anpassungen finden Sie in den folgenden Themen:

- [Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>VSTO-Add-Ins
 VSTO-Add-Ins bestehen aus einer Assembly, die einer Microsoft Office-Anwendung zugeordnet ist. Normalerweise wird das VSTO-Add-In ausgeführt, wenn die zugeordnete Anwendung gestartet wird, Benutzer können VSTO-Add-Ins aber auch laden, nachdem die Anwendung bereits ausgeführt wird. Funktionen in VSTO-Add-Ins, die Sie erstellen, sind für die eigentliche Anwendung verfügbar. Dabei spielt es keine Rolle, welche Dokumente geöffnet sind.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält Tools, die Sie beim Erstellen von VSTO-Add-Ins unterstützen. Add-in-Projekte enthalten eine automatisch generierte Klasse, die das VSTO-Add-in darstellt. Diese Klasse stellt Eigenschaften und Ereignisse bereit, mit denen Sie auf das Objektmodell der Hostanwendung zugreifen und Code ausführen können, wenn das VSTO-Add-In geladen und heruntergefahren wird. Es sind noch viele weitere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Funktionen in VSTO-Add-In-Projekten verfügbar, z. B. Windows Forms und ein integrierter Debugger.

 Weitere Informationen zu VSTO-Add-Ins finden Sie unter den folgenden Themen:

- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)

- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatisieren von Office-Anwendungen mithilfe primärer Interop-Assemblys
 Sie können die Funktionen einer Office-Anwendung programmgesteuert in Ihre Projektmappe einbinden, indem Sie Code schreiben, mit dem auf das Objektmodell der Anwendung zugegriffen wird. Bei Objektmodellen handelt es sich um eine Anordnung von Klassen, mit denen die Funktionalität unter Verwendung verschiedener Eigenschaften und Methoden verfügbar gemacht wird. Das Objektmodell ist für jede Office-Anwendung anders.

 Sie müssen die primäre Interopassembly (PIA) für die Anwendung verwenden, um das Objektmodell einer Office-Anwendung aus einer Projektmappe zu nutzen, die mit den Office-Entwicklungstools in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]erstellt wurde. Mit der PIA kann der verwaltete Code in Ihrer Projektmappe mit dem COM-basierten Objektmodell der Office-Anwendung interagieren.

 Die Office-PIAs müssen im globalen Assemblycache auf dem Entwicklungscomputer installiert und registriert sein, damit Sie die meisten Entwicklungsaufgaben ausführen können. Weitere Informationen finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)-Projektmappen. Zur Ausführung von VSTO-Office-Projektmappen sind die Office-PIAs auf Endbenutzercomputern nicht erforderlich. Weitere Informationen finden Sie unter [Entwerfen und Erstellen von Office-](../vsto/designing-and-creating-office-solutions.md)Projektmappen.

 Weitere Informationen zum Verwenden der PIAs in VSTO-Office-Projektmappen finden Sie unter den folgenden Themen:

- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)

- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Ausführen von Microsoft VSTO-Office-Projektmappen auf Endbenutzer Computern
 Berücksichtigen Sie beim Erstellen einer VSTO-Office-Projektmappe, wie sich die Bereitstellungsanforderungen auf Ihre Entwicklungsentscheidungen auswirken.

### <a name="deployment-options"></a>Bereitstellungsoptionen
 Verwenden Sie ClickOnce oder Windows Installer zum Bereitstellen von Projektmappen, die Sie mit den Office-Entwicklungstools in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]erstellen. Mit der ClickOnce-Bereitstellung können Sie sich selbst aktualisierende Projektmappen erstellen, die mit minimaler Benutzerinteraktion installiert und ausgeführt werden können. Windows Installer Dateien (*. msi*) können problemlos auf Endbenutzer Computer verteilt oder mithilfe von Systems Management Server (SMS) verteilt werden. Weitere Informationen zum Bereitstellen von VSTO-Office-Lösungen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

### <a name="install-prerequisites"></a>Installieren der erforderlichen Komponenten
 Bevor Endbenutzer eine Projektmappe ausführen können, die Sie mit den Office-Entwicklungstools in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]erstellen, müssen auf deren Computern bestimmte erforderliche Komponenten installiert werden. Wenn Sie Ihre Projektmappe per ClickOnce oder per Erstellung einer Windows Installer-Datei bereitstellen, können diese erforderlichen Komponenten mit Ihrer Projektmappe installiert werden. Weitere Informationen finden Sie unter [Voraussetzungen für die Bereitstellung von Office](/previous-versions/bb608617(v=vs.110)) -Lösungen und Gewusst [wie: Installieren von erforderlichen Komponenten auf Endbenutzer Computern zum Ausführen von Office-Lösungen](/previous-versions/bb608608(v=vs.110)).

### <a name="security"></a>Sicherheit
 Die Sicherheit für VSTO-Office-Projektmappen wird mit einer Reihe von Prüfungen durchgesetzt, die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] durchgeführt werden, wenn die Projektmappe installiert und geladen wird. Bei diesen Prüfungen wird unter anderem überprüft, ob der Speicherort des Bereitstellungsmanifests vertrauenswürdig ist oder ob das Zertifikat, mit dem das Bereitstellungsmanifest signiert wurde, vertrauenswürdig ist. Weitere Informationen finden Sie unter [sichere Office-Lösungen](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Weitere Informationen
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
