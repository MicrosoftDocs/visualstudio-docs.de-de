---
title: Entwerfen und Erstellen von Office-Lösungen
description: Erfahren Sie, wie Visual Studio Projektvorlagen bereitstellt, die Sie verwenden können, um verschiedene Typen von Office-Projektmappen zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df634a7c242819e4f41a6fddeae4099a3d25fae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897640"
---
# <a name="design-and-create-office-solutions"></a>Entwerfen und Erstellen von Office-Lösungen

Visual Studio stellt Projektvorlagen bereit, mit denen Sie mehrere unterschiedliche Typen von Office-Projektmappen erstellen können. In diesem Abschnitt der Dokumentation werden die Projektvorlagen beschrieben und Anweisungen zum Erstellen von Office-Projekten bereitgestellt. Informationen zum Implementieren von Code-und Benutzeroberflächen Anpassungen, nachdem Sie das Projekt erstellt haben, finden Sie unter [entwickeln von Office](../vsto/developing-office-solutions.md)-Projektmappen.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Erstellen von Office-Projekten
 Bevor Sie beginnen, sollten Sie die Anforderungen bestimmen und den am besten geeigneten Lösungstyp festlegen. Wenn die Office-Projektmappe z. B. bei jeder Verwendung der Anwendung ausgeführt werden muss, ist ein VSTO-Add-In die beste Lösung für Ihre Anforderungen. Wenn der Code fest in ein einzelnes Dokument integriert ist, erstellen Sie eine Anpassung auf Dokumentebene. Diese Projekttypen sind als Visual Studio-Projektvorlagen verfügbar. Weitere Informationen zu den Office-Projektvorlagen, die in Visual Studio enthalten sind, finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md). Weitere Informationen zum Erstellen von Office-Projekten finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Office-Projekte enthalten Funktionen und Projektelemente, die sich von anderen Projekttypen in Visual Studio unterscheiden. Wenn Sie z. B. ein Projekt auf Dokumentebene erstellen, kann das Dokument oder die Arbeitsmappe im Projekt in Visual Studio geöffnet und bearbeitet werden. Weitere Informationen finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>Wählen Sie eine .NET Framework Version aus.
 Nachdem Sie den für Ihre Anforderungen am besten geeigneten Projekttyp ausgewählt haben, können Sie festlegen, welche .NET Framework-Version bei der Entwicklung verwendet werden soll. In Office-Projekten können die folgenden .NET Framework-Versionen verwendet werden:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  Die .NET Framework Version, die Sie für Ihr Projekt auswählen, ist auf Endbenutzer Computern erforderlich, damit die Projekt Mappe ausgeführt werden kann. Wenn das Projekt z [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . b. auf abzielt, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ist auf Endbenutzer Computern erforderlich. In diesem Beispiel wird die Projekt Mappe nicht ausgeführt, wenn nur der .NET Framework 3,5 auf Endbenutzer Computern installiert ist.

  Wenn Sie ein VSTO-Add-In-Projekt migrieren, das .NET Framework 3.5 als Ziel verwendet, ändert Visual Studio das Zielframework des Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher, je nach installierter Office-Version.

  Nachdem das Zielframework von Visual Studio geändert wurde, müssen Sie jedoch möglicherweise einen Teil des Codes im Projekt ändern, wenn es bestimmte Funktionen verwendet. Weitere Informationen zum Ändern des Ziel Frameworks finden Sie unter Gewusst [wie: Ausrichten auf eine Version der .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Weitere Informationen zu Änderungen, die Sie möglicherweise in Ihrem Projekt vornehmen müssen, finden Sie unter Migrieren von Office-Projektmappen [zum .NET Framework 4 oder](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)höher.

  Wenn Visual Studio die Ziel .NET Framework für Ihr Projekt ändert und Sie ClickOnce verwenden, um die Projekt Mappe bereitzustellen, müssen Sie auch die entsprechende Version des .NET Framework **im Dialogfeld** erforderliche Komponenten auswählen. Diese Auswahl wird nicht automatisch geändert, wenn Sie das Zielframework für das Projekt ändern. Weitere Informationen finden Sie unter Gewusst [wie: Installieren von erforderlichen Komponenten auf Endbenutzer Computern zum Ausführen von Office-](/previous-versions/bb608608(v=vs.110))Projektmappen.

> [!NOTE]
> Sie können .NET Framework 3.5 oder frühere Versionen in Office-Projekten, die Sie mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellen, nicht als Ziel verwenden. Office-Projekte, die Sie mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellen, erfordern Funktionen, die anfänglich in [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] eingeführt wurden.

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Verstehen, wann die Office-PIAs auf Endbenutzer Computern erforderlich sind
 Standardmäßig müssen primäre Interop-Assemblys (PIAs) von Office nicht auf Endbenutzer Computern installiert werden, wenn die Eigenschaft **Interoptypen einbetten** jedes Office-Pia-Verweises im Projekt auf **true** festgelegt ist. Dies ist der Standardwert. In diesem Szenario werden die in der Projektmappe für die PIA-Typen verwendeten Typinformationen beim Erstellen des Projekts in die Projektmappenassembly eingebettet. Zur Laufzeit werden die eingebetteten Typinformationen statt der PIAs verwendet, um das COM-basierte Objektmodell der Office-Anwendung aufzurufen. Weitere Informationen zur Einbettung von Typen aus PIAs in die Projekt Mappe finden Sie unter [typäquivalenz und eingebettete Interop-Typen](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Wenn die Eigenschaft **Interop-Typen einbetten** jedes Office-Pia-Verweises im Projekt auf **false** festgelegt ist, muss Office PIAs im globalen Assemblycache auf jedem Endbenutzer Computer installiert und registriert werden, auf dem die Lösung ausgeführt wird. In den meisten Fällen werden die PIAs standardmäßig mit Office installiert, Sie können die verteilbare PIA jedoch auch als erforderliche Komponente für die Lösung einschließen. Weitere Informationen finden Sie unter [Voraussetzungen für Office-Lösungen für die Bereitstellung](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>Grundlegendes zum Client Profil
 .NET Framework Client Profile ist eine Teilmenge der Vollversion von .NET Framework. Sie können .NET Framework Client Profile verwenden, wenn nur die Clientfunktionen in .NET Framework verwendet werden müssen und die schnellstmögliche Bereitstellung für die Office-Lösung angegeben werden soll. Weitere Informationen finden Sie unter [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).

 Wenn Sie ein Office-Projekt erstellen, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] abzielt, wird [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] standardmäßig als Ziel verwendet. Wenn Sie ein Projekt für das vollständige [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] entwickeln möchten, müssen Sie diese Option festlegen, nachdem das Projekt erstellt wurde. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Erstellen Sie Lösungen für die 64-Bit-Edition von Microsoft Office
 Microsoft Office ist in 64-Bit- und 32-Bit-Editionen verfügbar. Zum Erstellen von Office-Projektmappen, die in einer der Editionen ausgeführt werden können, muss die Zielplattform für das Projekt auf **eine beliebige CPU** festgelegt sein. Dies ist der Standardwert für Office-Projekte. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

 Es gibt separate 64-Bit- und 32-Bit-Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], die von den 64-Bit- und 32-Bit-Editionen von Microsoft Office verwendet werden. Weitere Informationen finden Sie unter [Visual Studio-Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Assemblys in Office-Lösungen
 Wenn Sie mit den Office-Entwicklungstools in Visual Studio ein Office-Projekt erstellen, wird der Code, den Sie schreiben, schließlich in eine Assembly kompiliert. Die Assembly wird auf einem freigegebenen Server oder in einem Verzeichnis auf dem Client Computer bereitgestellt.

 Assemblys in Office-Projektmappen werden von einer Office-Anwendung geladen. Nach dem Laden der Assembly kann Code in der Assembly auf Ereignisse reagieren, die in der Anwendung ausgelöst werden, z. B. wenn ein Benutzer auf ein Menüelement klickt. Der Code in der Assembly kann auch einen Aufruf an das Objektmodell ausführen, um die Anwendung zu automatisieren und zu erweitern, und der Code kann jede der Klassen in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] verwenden. Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md) und [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 Office-Lösungen identifizieren die Assembly mithilfe von Bereitstellungsmanifesten und Anwendungsmanifesten. Die Manifeste enthalten Informationen über Name, Version und Speicherort der Assembly, sodass die Anwendung die richtige Assembly suchen, eine Verbindung mit dieser herstellen und diese ausführen kann. Weitere Informationen finden Sie unter [Anwendungs-und Bereitstellungs Manifeste in Office-](../vsto/application-and-deployment-manifests-in-office-solutions.md)Projektmappen.

 Projekte auf Dokumentebene enthalten zusätzlich zu einer Assembly ein Dokument. Das Dokument bildet das Front-End der Anwendung, in dem alle Benutzerinteraktionen stattfinden. Jedes Dokument kann nur mit einer Hauptprojektassembly verknüpft sein, es können jedoch mehrere Dokumente auf dieselbe Assembly verweisen.

 Assemblys in Projekten auf Dokumentebene sind nicht im Dokument eingebettet, sondern werden an anderer Stelle gespeichert und durch das Anwendungsmanifest des Dokuments identifiziert.

## <a name="security-considerations-for-assemblies"></a>Sicherheitsüberlegungen für Assemblys
 Damit eine Office-Lösung auf einem Computer ausgeführt werden kann, müssen die von der Lösung verwendeten Assemblys als vertrauenswürdig gelten, um ausgeführt zu werden. Weitere Informationen zur Sicherheit finden Sie unter [sichere Office-Lösungen](../vsto/securing-office-solutions.md).

 Standardmäßig gelten die Projektmappenassembly und alle Assemblys, auf die verwiesen wird und die sich im Ausgabeordner des Projekts befinden, als vertrauenswürdig, um beim Erstellen des Projekts auf dem Entwicklungscomputer ausgeführt zu werden. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

 Aus Sicherheitsgründen empfiehlt es sich, Projekte auf dem lokalen Computer und nicht in einem freigegebenen Speicherort zu erstellen. Weitere Informationen finden Sie unter [Collaborative Development of Office Solutions](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Assemblys, auf die verwiesen wird
 Eine Assembly kann auf andere Assemblys verweisen, die in den Verweisen des Projekts aufgelistet sind. Eine Assembly in einem Projekt auf Dokumentebene kann jedoch auf keine andere Assembly in einem Projekt auf Dokumentebene verweisen.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md)
- [Ausführen von Lösungen in unterschiedlichen Versionen von Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Gewusst wie: Ausrichten von Office-Anwendungen über primäre Interop-Assemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Anwendungs-und Bereitstellungs Manifeste in Office-Lösungen](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Vorgehensweise: Einrichten von Konfigurationsinformationen für eine Office-Projekt Mappe](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Verwenden von Office-Funktionen in Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Häufige Aufgaben bei der Office-Programmierung](../vsto/common-tasks-in-office-programming.md)
- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)