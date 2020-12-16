---
title: Erforderliche Änderungen für Office-Projekte, die zu .NET 4,5 migriert wurden
description: Informieren Sie sich über die Änderungen, die Sie an Ihrem Projekt vornehmen müssen, wenn das Ziel Framework von einer früheren Version des .NET Framework in .NET Framework 4 oder höher geändert wird.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e92a7fc81f77244664be7285cc6fd414dc4409be
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527490"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>Erforderliche Änderungen für Office-Projekte, die zu .NET 4,5 migriert wurden

  Wenn das Ziel Framework eines Office-Projekts [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] von einer früheren Version des .NET Framework in oder höher geändert wird, müssen Sie die folgenden Aufgaben ausführen, um sicherzustellen, dass die Lösung auf dem Entwicklungs Computer und auf den Computern der Endbenutzer ausgeführt werden kann:

- Entfernen Sie das <xref:System.Security.SecurityTransparentAttribute> aus dem Projekt, wenn Sie ein Upgrade aus Visual Studio 2008 ausgeführt haben.

- Führen Sie in Visual Studio einen Befehl zum **Bereinigen** aus, um das Projekt auf dem Entwicklungs Computer ausführen oder Debuggen zu können.

- Aktualisieren Sie die .NET Framework-Voraussetzung für das Projekt.

- Endbenutzer müssen außerdem die Projektmappe neu installieren, wenn Sie diese zuvor mit ClickOnce bereitgestellt haben, bevor Sie das Zielframework geändert haben.

  Weitere Informationen zu den einzelnen Aufgaben finden Sie in den entsprechenden Abschnitten weiter unten.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Entfernen des SecurityTransparent-Attributs aus Projekten, die Sie von Visual Studio 2008 aktualisieren
 Wenn Sie ein Upgrade für ein Office-Projekt aus Visual Studio 2008 ausgeführt haben und sich das Zielframework des Projekts anschließend in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ändert, müssen Sie das <xref:System.Security.SecurityTransparentAttribute> aus dem Projekt entfernen. Visual Studio entfernt dieses Attribut nicht automatisch für Sie. Wenn Sie dieses Attribut nicht entfernen, erhalten Sie eine Fehlermeldung, wenn Sie das Projekt kompilieren.

 Weitere Informationen zu den Bedingungen, unter denen Visual Studio das Ziel Framework eines aktualisierten Projekts in oder ändern kann [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , finden Sie unter [aktualisieren und Migrieren von Office-](../vsto/upgrading-and-migrating-office-solutions.md)Projektmappen.

#### <a name="to-remove-the-securitytransparentattribute"></a>So entfernen Sie "SecurityTransparentAttribute"

1. Öffnen Sie den **Projektmappen-Explorer**, während das Projekt in Visual Studio geöffnet ist.

2. Doppelklicken Sie unter dem Knoten **Eigenschaften** (für C#) oder dem Knoten **Mein Projekt** (für Visual Basic) auf die Codedatei "AssemblyInfo", um diese im Code-Editor zu öffnen.

    > [!NOTE]
    > In Visual Basic-Projekten müssen Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen** klicken, um die Codedatei "AssemblyInfo" anzuzeigen.

3. Suchen Sie nach <xref:System.Security.SecurityTransparentAttribute>, und entfernen Sie das Attribut aus der Datei, oder kommentieren Sie es aus.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Ausführen des Befehls "Clean" zum Debuggen oder Ausführen eines Projekts auf dem Entwicklungs Computer
 Wenn ein Office-Projekt erstellt wurde, bevor das Ziel Framework des Projekts in oder höher geändert wird [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , müssen Sie einen **Clean** -Befehl ausführen und dann das Projekt neu erstellen, nachdem das Ziel Framework geändert wurde. Wenn Sie keinen **Clean** -Befehl ausführen, erhalten Sie eine, <xref:System.Runtime.InteropServices.COMException> Wenn Sie versuchen, das Projekt neu zu debuggen oder auszuführen.

 Weitere Informationen zum **Clean** -Befehl finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

## <a name="update-the-prerequisites-for-deployment"></a>Die Voraussetzungen für die Bereitstellung aktualisieren
 Wenn Sie ein Office-Projekt auf oder höher ausrichten [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , müssen Sie auch die entsprechenden .NET Framework erforderlichen Komponenten im Dialogfeld **Voraussetzungen** aktualisieren. Andernfalls sucht die ClickOnce-Bereitstellung oder das InstallShield Limited Edition-Projekt nach einer früheren Version von .NET Framework und installiert diese.

 Weitere Informationen zum Aktualisieren der Voraussetzungen für die Bereitstellung auf Endbenutzer Computern finden [Sie unter Gewusst wie: Installieren von erforderlichen Komponenten auf Endbenutzer Computern zum Ausführen von Office](/previous-versions/bb608608(v=vs.110))-Projektmappen.

## <a name="reinstall-solutions-on-end-user-computers"></a>Neuinstallieren von Lösungen auf Endbenutzer Computern
 Wenn Sie mithilfe von ClickOnce eine Office-Projektmappe bereitstellen, die als Zielframework .NET Framework 3.5 verwendet, und dann das Projekt auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher umstellen, müssen Endbenutzer die Projektmappe deinstallieren und dann erneut installieren, nachdem Sie sie veröffentlicht haben. Wenn Sie die neu ausgerichtete Lösung erneut veröffentlichen und die Lösung auf Endbenutzer Computern aktualisiert wird, erhalten Endbenutzer eine, <xref:System.Runtime.InteropServices.COMException> Wenn Sie die aktualisierte Lösung ausführen.

## <a name="see-also"></a>Weitere Informationen
- [Migrieren von Office-Projektmappen zu den .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)