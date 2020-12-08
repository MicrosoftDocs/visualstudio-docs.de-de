---
title: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen
description: Erfahren Sie, wie Sie eine unterstützte Version von Visual Studio, die .NET Framework und Microsoft Office installieren können, um VSTO-Add-Ins und Anpassungen für Microsoft Office erstellen zu können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3658f655c50c9d1a0775a8cc69dd65baf32d1408
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847259"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen

Installieren Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office, um VSTO-Add-Ins und Anpassungen für Microsoft Office zu erstellen.

|Software|Unterstützte Versionen|
|--------------|------------------------|
|Visual Studio 2017| Eine beliebige Edition mit der Arbeitsauslastung für **Office/SharePoint-Entwicklung** .|
|.NET Framework|-Die .NET Framework 4 oder höher.|
|Microsoft Office|<ul><li>Jede Suite-Edition von Office, einschließlich Microsoft 365 Apps für Unternehmen.</li><li>Eine der folgenden eigenständigen Anwendungen:<br /><br /> <ul><li>Excel</li><li>InfoPath (nur Office 2013 und Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) muss als Teil von Office installiert sein. **Wichtig:** Click-to-Run-Versionen von Office 2010-Anwendungen werden nicht unterstützt.|

Ausführliche Installationsschritte finden Sie unter Gewusst [wie: Konfigurieren eines Computers zum Entwickeln von Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)-Projektmappen.

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Wenn Projektvorlagen nicht angezeigt werden oder Sie nicht in Visual Studio funktionieren

Wenn Sie eine unterstützte Version von Visual Studio, die .NET Framework und Microsoft Office installieren, aber Office-Projektvorlagen nicht im Visual Studio-Dialogfeld " **Neues Projekt** " angezeigt werden, oder wenn Sie einen Fehler erhalten, wenn Sie versuchen, eine Version zu verwenden, überprüfen Sie Folgendes:

- Stellen Sie sicher, dass die Microsoft Office Developer Tools auf Ihrem Computer installiert sind.

     Office Developer Tools sind eine optionale Komponente von Visual Studio, werden aber automatisch zusammen mit Visual Studio installiert. Wenn Sie die Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, legen Sie beim Setup zum Installieren der Tools **Microsoft Office Developer Tools** fest.

     Um sicherzustellen, dass diese Tools installiert sind, starten Sie das Visual Studio-Setup Programm, und klicken Sie auf die Schaltfläche **ändern** . Aktivieren Sie das Kontrollkästchen **Microsoft Office Developer Tools** , und wählen Sie dann die Schaltfläche **Aktualisieren** aus.

- Stellen Sie sicher, dass Sie keine Version von Office ausführen, die durch Klicken auf die Ausführung übermittelt wurde. Weitere Informationen finden [Sie unter Gewusst wie: überprüfen, ob Outlook eine Klick-und-Los-Anwendung auf einem Computer ist](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Stellen Sie sicher, dass nur eine Version von Microsoft Office ausgeführt wird.

Wenn weiterhin Probleme auftreten, finden Sie [Weitere Informationen unter zusätzliche Unterstützung für Fehler in Office](../vsto/additional-support-for-errors-in-office-solutions.md)-Projektmappen.

## <a name="see-also"></a>Siehe auch
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Vorgehensweise: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Gewusst wie: Installieren von primären Interop-Assemblys in Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md)