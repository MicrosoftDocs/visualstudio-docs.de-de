---
title: 'Vorgehensweise: Festlegen von SharePoint-Bereitstellungs Befehlen | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie den Bereitstellungs Prozess anpassen, indem Sie die SharePoint-Befehle vor und nach der Bereitstellung festlegen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc1da67206e5e5c9fde1b5c595424239d1685ac7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304383"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Vorgehensweise: Festlegen von SharePoint-Bereitstellungs Befehlen
  Sie können den Bereitstellungs Prozess anpassen, indem Sie Befehle vor und nach der Bereitstellung festlegen. Diese Befehle werden vor und nach anderen Bereitstellungs Aktionen ausgeführt, wenn Sie SharePoint-Lösungen aus Visual Studio debuggen.

### <a name="to-add-a-pre-deployment-command"></a>So fügen Sie einen Befehl vor der Bereitstellung hinzu

1. Wählen Sie in der Menüleiste die Option **Projekt**  >  **\<*ProjectName*> Eigenschaften** aus.

2. Wählen Sie die Registerkarte **SharePoint** aus.

3. Geben Sie im Textfeld **Befehlszeile vor der Bereitstellung** MS-DOS-oder MSBuild-Befehle ein, um diesen Schritt anzupassen.

     Wenn Sie z. b. den Verzeichnis Inhalt vor dem Abschluss der Bereitstellung auflisten möchten, geben Sie **dir** ein.

### <a name="to-add-a-post-deployment-command"></a>So fügen Sie einen Befehl nach der Bereitstellung hinzu

1. Wählen Sie in der Menüleiste die Option **Projekt**  >  **\<*ProjectName*> Eigenschaften** aus.

2. Wählen Sie die Registerkarte **SharePoint** aus.

3. Geben Sie im Textfeld für die **Befehlszeile nach der Bereitstellung** MS-DOS-oder MSBuild-Befehle ein, um diesen Schritt anzupassen.

     Wenn Sie z. b. den Verzeichnis Inhalt nach Abschluss der Bereitstellung auflisten möchten, geben Sie **dir** ein. Wenn Sie eine MSBuild-Variable zum Kopieren der Assembly aus dem Buildverzeichnis verwenden möchten, geben Sie **Copy $ (TargetPath) c:\deploymentdirectory** ein.

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
