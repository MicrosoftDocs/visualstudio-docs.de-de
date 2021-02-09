---
title: Verwenden von Modulen zum Einbinden von Dateien in eine Projektmappe | Microsoft-Dokumentation
description: Verwenden Sie Module oder Container für Dateien in einer SharePoint-Lösung, um Dateien auf dem SharePoint-Server unabhängig von ihrem Dateityp bereitzustellen (z. B. Masterseiten).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 86aea9800d0eaad4c36d5598e52dd7a35f3a7534
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892176"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Verwenden von Modulen zum Einbinden von Dateien in eine Projektmappe
  Manchmal kann es vorkommen, dass Sie Dateien auf dem SharePoint-Server unabhängig vom Dateityp bereitstellen möchten, z. B. neue Masterseiten. Zu diesem Zweck können Sie *Module* verwenden (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]-Codemodulen). Module sind Container für Dateien in einer SharePoint-Lösung. Wenn die Lösung bereitgestellt wird, werden die Dateien im Modul in die angegebenen Ordner auf dem SharePoint-Server kopiert.

## <a name="module-items-and-elements"></a>Module-Elemente und Elements-Dateien
 Um ein Modul zu erstellen, fügen Sie es einem Projekt hinzu, indem Sie es im Dialogfeld **Neues Element hinzufügen** auswählen. Ändern Sie dann seine Datei *Elements.xml* so, dass sie die Namen der Dateien enthält, die Sie bereitstellen möchten, und angibt, wo sie sich im System befinden und wohin sie auf dem SharePoint-Server kopiert werden sollen.

 Im Folgenden finden Sie ein Beispiel für die Datei *Elements.xml* für ein Modul:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Neu erstellte Module enthalten die folgenden Standarddateien:

|Dateiname|Beschreibung|
|---------------|-----------------|
|*Elements.xml*|Die Definitionsdatei für das Modul.|
|*Sample.txt*|Eine Platzhalterdatei, die als Beispiel für eine Datei im Modul dient.|

 Die Datei *Elements.xml* enthält die folgenden Elemente:

|Elementname|BESCHREIBUNG|
|------------------|-----------------|
|Elemente|Enthält alle Elemente, die im Modul definiert sind.|
|Modul|Das Module-Element verfügt über ein einzelnes Attribut (*Name*), das den Namen des Moduls im Format `<Module Name="Module1">` angibt.<br /><br /> Beachten Sie Folgendes: Wenn Sie den Namen des Moduls (oder dessen Eigenschaft *Folder Name*) ändern, müssen Sie den Namen im Module-Element manuell aktualisieren.<br /><br /> Wenn Sie ein Unterverzeichnis für die Dateien im Module-Element angeben, erstellt [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automatisch eine passende Verzeichnisstruktur.|
|Datei|Das File-Element verfügt über zwei Parameter: *Path* und *Url*.<br /><br /> - Path: Der Name und Speicherort der Datei in der SharePoint-Lösung. Das Format lautet: `Path="Module1\Sample.txt"`.<br /><br /> - Url: Der Speicherort, in dem die Datei auf dem SharePoint-Server bereitgestellt wird. Das Format lautet: `Url="Module1/Sample.txt"`.<br /><br /> - Type: Ein optionales Attribut, das über zwei Einstellungen verfügt: *GhostableInLibrary* und *Ghostable*. Das Format lautet: `Type="GhostableInLibrary"`. Wenn Sie *GhostableInLibrary* angeben, wird die Datei einer Dokumentbibliothek in SharePoint gemeinsam mit einem Listenelement hinzugefügt, das die Datei begleitet, wenn sie der Bibliothek hinzugefügt wird. Wenn Sie *Ghostable* angeben, wird die Datei SharePoint außerhalb der Dokumentbibliothek hinzugefügt.|

 Für jede Datei, die Sie bereitstellen möchten, ist ein separater `<File>`-Elementeintrag in *Elements.xml* erforderlich.

## <a name="see-also"></a>Weitere Informationen
- [How to: Einbinden von Dateien mithilfe eines Moduls](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Vorgehensweise: Bereitstellen einer Datei](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
