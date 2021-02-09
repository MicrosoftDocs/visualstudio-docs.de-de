---
title: 'Gewusst wie: Öffnen von Office-Projektmappen ohne Ausführen von Code'
description: Erfahren Sie, wie Sie ein Dokument oder eine Arbeitsmappe öffnen können, die Erweiterungen durch verwalteten Code enthält, ohne den Assemblycode ausführen
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99f1a01a745544e7e11e724db9c6eafacf0ca201
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876588"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Gewusst wie: Öffnen von Office-Projektmappen ohne Ausführen von Code
  Eine Microsoft Office Lösung, die mit Erweiterungen für verwalteten Code erstellt wurde, wird auch dann ausgeführt, wenn die Sicherheitseinstellung in der Office-Anwendung des Endbenutzers auf hoch festgelegt ist Dies liegt daran, dass die .net-Assemblycode-Sicherheit vom Microsoft .NET Framework verwaltet wird, nicht durch Microsoft Office.

 Es kann jedoch vorkommen, dass Sie ein Dokument öffnen möchten, ohne den Code ausführen zu müssen. Beispielsweise kann Code, der ausgeführt wird, wenn das Dokument geöffnet wird, den Inhalt ändern, aber Sie möchten die Art und Weise aktualisieren, in der das Dokument aussieht, bevor es vom Code geändert wird. Oder Sie möchten das Dokument mit bestimmten Informationen an eine Person senden, und Sie möchten, dass der Code nicht ausgeführt wird und möglicherweise den Inhalt ändert.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Es gibt mehrere Möglichkeiten, ein Dokument oder eine Arbeitsmappe zu öffnen, die Erweiterungen durch verwalteten Code enthält, ohne den Assemblycode zu ausführen.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>So umgehen Sie die Assembly mit der UMSCHALTTASTE

- Öffnen Sie Dokumente und Arbeitsmappen über das Menü **Datei** , und halten Sie die **UMSCHALT** Taste gedrückt, um zu verhindern, dass Word und Excel Initialisierungs Ereignisse beim Öffnen des Dokuments aufhebt.

    > [!NOTE]
    > Wenn Sie im Aufgabenbereich " **Getting Started** " ein Dokument oder eine Arbeitsmappe öffnen, wird der Code durchhalten der **UMSCHALT** Taste nicht umgangen. Wenn Sie die UMSCHALTTASTE gedrückt halten, wird auch nicht verhindert, dass Ereignisse ausgelöst werden, nachdem das Dokument geöffnet ist.

     Diese Methode ist hilfreich, wenn Sie ein Dokument öffnen möchten, um Änderungen vorzunehmen, ohne dass der Code ausgeführt wird, und das Dokument zuerst zu ändern.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>So umgehen Sie eine Assembly durch Umbenennen oder entfernen

- Wenn Sie auf dem Computer, auf dem sich die Assembly befindet, über die erforderlichen Berechtigungen verfügen, können Sie die Assembly umbenennen oder entfernen, sodass Sie vom Dokument oder der Arbeitsmappe nicht gefunden werden kann. Dies führt zu einem Fehler, wenn das Office-Dokument geöffnet wird.

     Wenn die Lösung von mehreren Personen verwendet wird, verhindert diese Methode, dass die Lösung für alle ausgeführt wird. Dies kann hilfreich sein, wenn ein Problem im Code oder auf einem Server gefunden wird, auf den verwiesen wird, und Sie alle Benutzer daran hindern möchten, Sie auszuführen.

## <a name="see-also"></a>Weitere Informationen
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Anwendungs-und Bereitstellungs Manifeste in Office-Lösungen](../vsto/application-and-deployment-manifests-in-office-solutions.md)
