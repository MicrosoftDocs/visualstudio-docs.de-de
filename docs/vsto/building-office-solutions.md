---
title: Erstellen von Office-Lösungen
description: Informieren Sie Windows Forms sich über die Unterschiede zwischen dem entwickeln und Debuggen von Office-Projekten und dem entwickeln und Debuggen von anderen Projekttypen in Visual Studio
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31cb28ad2c332d0afea9bef8cbe1c979b58536e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896711"
---
# <a name="build-office-solutions"></a>Erstellen von Office-Lösungen
  Im Allgemeinen ist das Erstellen und Debuggen von Office-Projekten mit dem Erstellen und Debuggen von anderen Projekttypen in Visual Studio identisch, z. B. von Windows Forms. Die vorhandenen Unterschiede werden in diesen Themen des Abschnitts erläutert. Allgemeine Informationen zum Erstellen von Anwendungen finden Sie unter [Kompilieren und erstellen in Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Projekt Ausgabe für Office-Projekte
 Der Ausgabeort für Office-Projekte ist „ *Projektname*\bin\release“ oder „ *Projektname*\bin\debug“. Sie können die Erstellung nicht in einem Bereitstellungsverzeichnis vornehmen.

### <a name="document-level-projects"></a>Projekte auf Dokument Ebene
 Wenn Sie ein Projekt auf Dokumentebene erstellen, sind die folgenden Elemente in der Projektausgabe enthalten:

- Eine Kopie des Projektdokuments.

- Die Projektassembly und alle referenzierten Assemblys, deren **Lokale Kopie** -Eigenschaft auf **true** festgelegt ist.

- Das Anwendungs Manifest mit der Dateinamenerweiterung " *. Manifest*". Weitere Informationen finden Sie unter [Anwendungs Manifeste für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen.

- Das Bereitstellungs Manifest mit der Dateinamenerweiterung *. VSTO*. Weitere Informationen finden Sie unter [Bereitstellungs Manifeste für Office](../vsto/deployment-manifests-for-office-solutions.md)-Projektmappen.

- Eine Programm Datenbankdatei (*PDB*-Datei).

> [!NOTE]
> Wenn Sie eine Projektmappe auf Dokumentebene an einem Remotespeicherort anstatt auf dem lokalen Computer erstellen, fügen Sie den vollqualifizierten Pfad zur Liste vertrauenswürdiger Speicherorte im Vertrauensstellungscenter der Anwendung hinzu. Weitere Informationen finden Sie im Abschnitt "gewähren von Vertrauenswürdigkeit für Dokumente in [sicheren Office-Lösungen](../vsto/securing-office-solutions.md)".

### <a name="application-level-projects"></a>Projekte auf Anwendungsebene
 Wenn Sie ein VSTO-Add-in-Projekt erstellen, sind die folgenden Elemente in der Projekt Ausgabe enthalten:

- Die Projektassembly und alle referenzierten Assemblys, deren **Lokale Kopie** -Eigenschaft auf **true** festgelegt ist.

- Das Anwendungs Manifest mit der Dateinamenerweiterung " *. Manifest*". Weitere Informationen finden Sie unter [Anwendungs Manifeste für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen.

- Das Bereitstellungs Manifest mit der Dateinamenerweiterung *. VSTO*. Weitere Informationen finden Sie unter [Bereitstellungs Manifeste für Office](../vsto/deployment-manifests-for-office-solutions.md)-Projektmappen.

- Eine Programm Datenbankdatei (*PDB*) für die Projektassembly.

  Der Buildprozess für VSTO-Add-In-Projekte erstellt auch einen Satz von Registrierungseinträgen auf dem Entwicklungscomputer, die zum Laden des VSTO-Add-Ins erforderlich sind. Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).

  Wenn Sie ein VSTO-Add-In-Projekt für Outlook erstellen, das Formularbereiche enthält, werden die folgenden Informationen vom Buildprozess zur Registrierung hinzugefügt:

- Einen Schlüssel für jede Nachrichtenklasse, die mindestens einem Formularbereich zugeordnet ist.

- Einen Eintrag für jeden Formularbereich und einen zugeordneten Wert, der den Namen des Outlook VSTO-Add-Ins darstellt.

  Outlook benötigt diese Informationen zum Laden der Formularbereiche.

## <a name="referenced-assemblies"></a>Assemblys, auf die verwiesen wird
 Sie können aus Ihrem Projekt „Erstellen von Office-Projektmappen“ auf Assemblys verweisen (einschließlich Klassenbibliotheksprojekte). Jede referenzierte Assembly enthält eine Eigenschaft namens **Lokale Kopie**. **Lokale Kopie** gibt an, ob die Assembly in das Ausgabeverzeichnis kopiert wird. Standardmäßig ist der Wert auf **true** festgelegt. Jede referenzierte Assembly, bei der **Lokale Kopie** auf **true** festgelegt ist, wird in das Ausgabeverzeichnis kopiert.

## <a name="security-during-the-build-process"></a>Sicherheit während des Buildprozesses
 Visual Studio konfiguriert automatisch die Sicherheitseinstellungen auf dem Entwicklungscomputer, um während des Buildprozesses der Projektmappe Vertrauenswürdigkeit zu gewähren. Dadurch kann die Projektmappe beim Debuggen ausgeführt werden.

 Office-Projekte verwenden Zertifikate, um den Herausgeber zu überprüfen. Visual Studio erstellt automatisch ein temporäres Zertifikat zur Identifizierung von Office-Projektmappen und konfiguriert den Entwicklungscomputer, damit dem temporären Zertifikat vertraut wird.

 Weitere Informationen finden Sie unter [sichere Office-Lösungen](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Netzwerkprojekte
 Wenn sich der Speicherort der Assembly oder des Dokuments auf einer Netzwerkfreigabe befindet, ist die Aktualisierung der lokalen Sicherheitsrichtlinie (auf Benutzerebene) nicht ausreichend, um die Ausführung der Projektmappe zu gestatten. Ein Administrator muss Assemblys und Dokumenten, die sich auf einer Netzwerkfreigabe befinden, volle Vertrauenswürdigkeit auf Computerebene gewähren, bevor die Projektmappe ausgeführt werden kann. Weitere Informationen zum Festlegen von Sicherheitsrichtlinien finden Sie unter [sichere Office-Lösungen](../vsto/securing-office-solutions.md).

 Für Projekte auf Dokumentebene müssen Sie außerdem den vollqualifizierten Speicherort des Dokuments zur Office-Liste vertrauenswürdiger Ordner hinzufügen. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Ändern der Zielplattform
 Standardmäßig ist die Zielplattform für Office-Projekte **Beliebige CPU**. In der Regel sollten Sie diese Einstellung nicht ändern. Office-Projektmappen, die mit der Zielplattformeinstellung **Beliebige CPU** erstellt werden, werden in 32-Bit- und 64-Bit-Versionen von Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]ausgeführt.

 Sie sollten die Zielplattform nur auf x64 festlegen, wenn Sie eine Projektmappe erstellen, die nur in 64-Bit-Versionen von Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]ausgeführt wird, und die Projektmappe systemeigene 64-Bit-APIs aufruft. Weitere Informationen zum Ändern der Zielplattform finden Sie unter Gewusst [wie: Konfigurieren von Projekten für Zielplattformen](../ide/how-to-configure-projects-to-target-platforms.md).

 Wenn Sie für die Zielplattform x64 festlegen, kann die Projektmappe nicht in 32-Bit-Versionen von Windows oder Office ausgeführt werden. Die x64-Zielplattform erfordert, dass die Projektmappe in einem 64-Bit-Prozess ausgeführt wird.

## <a name="use-the-clean-command"></a>Verwenden des Befehls "bereinigen"
 Um die erstellten Projektdateien vom Entwicklungscomputer zu entfernen, können Sie den Befehl **Bereinigen** aus dem Menü **Erstellen** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]verwenden. Der Befehl **Bereinigen** löscht alle Dateien im Ausgabespeicherort des Builds. Für Projekte auf Anwendungsebene entfernt der Befehl **Bereinigen** auch die vom Buildprozess erstellten Registrierungseinträge.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Debugging von Office-Projekten](../vsto/debugging-office-projects.md)|Beschreibt Probleme beim Debuggen von Office-Projekten.|
|[Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Veranschaulicht, wie Sie eine Standardanpassung auf Dokumentebene für Excel erstellen.|
|[Gewusst wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert wurde](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Beschreibt, wie ein VSTO-Add-in, das hart oder weich deaktiviert wurde, erneut aktiviert wird.|
|[Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)|Enthält Links zu Informationen über das Erstellen von Office-Projektmappen und über die Aufgabe, die Assemblys dabei zukommt.|