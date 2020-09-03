---
title: 'Vorgehensweise: Festlegen von SharePoint-Bereitstellungs Befehlen | Microsoft-Dokumentation'
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
ms.openlocfilehash: c2329efef64e7d8605f8483ff7dce3107cd702fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015506"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Vorgehensweise: Festlegen von SharePoint-Bereitstellungs Befehlen
  Sie können den Bereitstellungs Prozess anpassen, indem Sie Befehle vor und nach der Bereitstellung festlegen. Diese Befehle werden vor und nach anderen Bereitstellungs Aktionen ausgeführt, wenn Sie SharePoint-Lösungen aus Visual Studio debuggen.

### <a name="to-add-a-pre-deployment-command"></a>So fügen Sie einen Befehl vor der Bereitstellung hinzu

1. Wählen Sie in der Menüleiste die Option **Projekt**  >  ** \<*ProjectName*> Eigenschaften**aus.

2. Wählen Sie die Registerkarte **SharePoint** aus.

3. Geben Sie im Textfeld **Befehlszeile vor der Bereitstellung** MS-DOS-oder MSBuild-Befehle ein, um diesen Schritt anzupassen.

     Wenn Sie z. b. den Verzeichnis Inhalt vor dem Abschluss der Bereitstellung auflisten möchten, geben Sie **dir**ein.

### <a name="to-add-a-post-deployment-command"></a>So fügen Sie einen Befehl nach der Bereitstellung hinzu

1. Wählen Sie in der Menüleiste die Option **Projekt**  >  ** \<*ProjectName*> Eigenschaften**aus.

2. Wählen Sie die Registerkarte **SharePoint** aus.

3. Geben Sie im Textfeld für die **Befehlszeile nach der Bereitstellung** MS-DOS-oder MSBuild-Befehle ein, um diesen Schritt anzupassen.

     Wenn Sie z. b. den Verzeichnis Inhalt nach Abschluss der Bereitstellung auflisten möchten, geben Sie **dir**ein. Wenn Sie eine MSBuild-Variable zum Kopieren der Assembly aus dem Buildverzeichnis verwenden möchten, geben Sie **Copy $ (TargetPath) c:\deploymentdirectory**ein.

## <a name="see-also"></a>Weitere Informationen
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
