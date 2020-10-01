---
title: Migrieren von Office-Projektmappen zu den .NET Framework 4 oder höher
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86b975b7e84c69ff072df06e0a2c7701ab1909e7
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584489"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrieren von Office-Projektmappen zu den .NET Framework 4 oder höher
  Wenn das Ziel Framework eines Office-Projekts [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] von einer früheren Version des .NET Framework in oder höher geändert wird, sind möglicherweise einige zusätzliche Schritte erforderlich, um die Lösung auf Entwicklungs-und Endbenutzer Computern weiter auszuführen. Weitere Informationen finden Sie unter [erforderliche Änderungen zum Ausführen von Office-Projekten, die Sie zum .NET Framework 4 oder zum .NET Framework 4,5 migrieren](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Darüber hinaus wird das Projekt möglicherweise nicht mehr kompiliert. Einige Funktionen von Office-Projekten verfügen über unterschiedliche Programmiermodelle für die verschiedenen Versionen von .NET Framework. Wenn das Zielframework eines Office-Projekts von einer früheren .NET Framework-Version auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie die folgenden Codeänderungen am Projekt vornehmen:

- [Aktualisieren Sie Excel-und Word-Projekte, die Sie zum .NET Framework 4 oder zum .NET Framework 4,5 migrieren.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualisieren von Menü Band Anpassungen in Office-Projekten, die Sie zum .NET Framework 4 oder zum .NET Framework 4,5 migrieren](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aktualisieren von Formular Bereichen in Outlook-Projekten, die Sie zum .NET Framework 4 oder zum .NET Framework 4,5 migrieren](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Das Zielframework eines Office-Projekts ändert sich, wenn Sie dieses Projekt von einer früheren Visual Studio-Version aktualisieren. Weitere Informationen finden Sie unter [aktualisieren und Migrieren von Office-](../vsto/upgrading-and-migrating-office-solutions.md)Projektmappen.

  Weitere Informationen dazu, warum einige Funktionen in Office-Projekten ein anderes Programmiermodell aufweisen, wenn Sie auf oder höher abzielen [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , finden Sie unter [Änderungen am Entwurf von Office-Projekten, die auf die .NET Framework 4 abzielen, und in der Übersicht über die .NET Framework 4,5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) und [Visual Studio-Tools für Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Gewusst wie: Ziel einer Version des .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Beheben von Fehlern in Office-Projektmappen](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Zusätzliche Unterstützung für Fehler in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md)
