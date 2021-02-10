---
title: Gemeinsame Entwicklung von Office-Lösungen
description: Erfahren Sie, wie mehrere Entwickler an einem Office-Projekt genauso arbeiten können wie in anderen Visual Studio-Projekten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 028530014afdc78ab6c9c0483c3d443195383793
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942307"
---
# <a name="collaborative-development-of-office-solutions"></a>Gemeinsame Entwicklung von Office-Lösungen
  Mehrere Entwickler können wie in anderen Visual Studio-Projekten an einem Office-Projekt arbeiten. Visual Studio sucht die Microsoft Office Installation ordnungsgemäß auf den einzelnen Computern, auch wenn Office an verschiedenen Standorten installiert ist. Es gibt jedoch einige wichtige Überlegungen, die zu beachten sind.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Debug-Eigenschaften werden nicht freigegeben.
 In der Quellcodeverwaltung werden Debugeigenschaften nicht für mehrere Benutzer gemeinsam verwendet. In Visual Basic-und Visual c#-Projekten werden die Debugeigenschaften in einer benutzerspezifischen Datei ("*ProjectName*. vbproj. User" oder " *ProjectName*. csproj. User") gespeichert, und diese Datei befindet sich nicht in der Quell Code Verwaltung. Wenn mehrere Personen debuggen, muss jede Person die Debugeigenschaften manuell eingeben.

 Wenn das Projekt auf einer Netzwerkfreigabe statt in der Quell Code Verwaltung abgelegt ist, müssen einige zusätzliche Schritte ausgeführt werden, damit die zusammenarbeitenden Entwickler die Projekt Mappe öffnen und die Assembly testen können.

## <a name="source-control-requires-checking-out-all-files"></a>Die Quell Code Verwaltung erfordert das Auschecken aller Dateien.
 Wenn Sie die Quell Code Verwaltung für Ihre Projekte verwenden, sollten Sie jedes Mal, wenn Sie die Codedatei ändern (z. b. die Code Dateien *ThisDocument*, *ThisWorkbook* oder *ThisAddIn* ), alle Dateien **Projektmappen-Explorer** in einer Codedatei Auschecken, wenn Sie die Codedatei ändern, auch die Dateien, die standardmäßig ausgeblendet sind. Wenn Sie nur die Codedatei der obersten Ebene Auschecken, können Ihre Änderungen verloren gehen.

 Nachdem Sie die Änderungen vorgenommen haben, überprüfen Sie alle Dateien wieder in. Weitere Informationen zu ausgeblendeten Code Dateien in-Projekten finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Sicherheit für die informelle Zusammenarbeit in einem Netzwerk
 Für alle Lösungen auf Dokument Ebene, die sich an einem Netzwerk Speicherort (z. b. \\ \\ *Servername* \\ *ShareName*) befinden, muss der voll qualifizierte Speicherort der Liste vertrauenswürdiger Ordner in der Microsoft Office Anwendung hinzugefügt werden, mit der Sie arbeiten. Wählen Sie die Option zum Einschließen der Unterverzeichnisse in den Hauptordner aus, oder fügen Sie der Liste vertrauenswürdiger Ordner den Ordner Debug und Build hinzu. Weitere Informationen hierzu finden Sie unter Gewähren von Vertrauenswürdigkeit [für Dokumente](../vsto/granting-trust-to-documents.md).

 Die temporären Zertifikate, die automatisch zur Buildzeit generiert werden, werden nicht durch Kenn Wörter gesichert. Die Zertifikate enthalten den Anmelde Namen des Entwicklers und andere persönliche Informationen. Wenn Sie Anpassungen bereitstellen, die mit temporären Zertifikaten signiert sind, können andere möglicherweise auf diese Informationen zugreifen.

## <a name="see-also"></a>Weitere Informationen
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
