---
title: Einrichten von Konfigurationsinformationen für eine Office-Projekt Mappe
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e47ad00e3f9e90913784196894d514a755699864
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91581038"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Vorgehensweise: Einrichten von Konfigurationsinformationen für eine Office-Projekt Mappe
  Mit Konfigurationsdateien können Sie Einstellungen konfigurieren, die für Ihre Office-Projektmappen spezifisch sind. Sie können Einstellungen wie Assemblybindungsrichtlinie, Remoting-Objekte, Debug-und Ablauf Verfolgungs Einstellungen angeben.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>So fügen Sie dem Office-Projekt eine Konfigurationsdatei hinzu

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Klicken Sie im Bereich " **Kategorien** " auf **Allgemein**.

3. Wählen Sie im Bereich **Vorlagen** die Option **Anwendungs Konfigurationsdatei**aus.

4. Geben Sie im Feld **Name** den gleichen Namen wie die Assembly sowie die Erweiterung *. config*ein. Beispielsweise würde eine Konfigurationsdatei für eine Excel-projekassembly mit dem Namen *ExcelWorkbook1.dll* *ExcelWorkbook1.dll.config*lauten.

5. Klicken Sie auf **Hinzufügen**.

6. Erstellen Sie die Konfigurationsdatei gemäß dem Schema der Anwendungs Konfigurationsdatei. Weitere Informationen finden Sie unter [Schema der Konfigurationsdatei für die .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Es gibt keine besonderen Überlegungen für die Verwendung von Konfigurationsdateien mit Office-Projekten.

## <a name="see-also"></a>Weitere Informationen
- [Konfigurationsdatei Schema für die .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
