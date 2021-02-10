---
title: Hinzufügen von Verzeichnissen zum Dialog Feld "Neues Projekt" | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie dem Dialogfeld "Neues Projekt" in Visual Studio Verzeichnisse hinzufügen, sodass Sie neue Projekttypen erstellen und für die Verwendung als Vorlagen anzeigen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d65b7e4adc6d235bcb925efae1cef20d0aa2c9c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969034"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Hinzufügen von Verzeichnissen zum Dialogfeld "Neues Projekt"
Wenn Sie neue Projekttypen erstellen, können Sie auch ein neues Verzeichnis im Dialogfeld **Neues Projekt** registrieren, um Sie für die Verwendung als Vorlagen anzuzeigen. Im folgenden Codebeispiel wird erläutert, wie ein neues Verzeichnis registriert wird, das auch als-Knoten bezeichnet wird. Im Beispiel werden Vorlagen, die vom VSPackage bereitgestellt werden, *CLSID_Package*, registriert. Folglich bietet die linke Seite des Dialog Felds **Neues Projekt** den hinzugefügten Knoten mit einem Namen, der von der *Folder_Label_ResID* Ressource bestimmt wird. Diese Ressource wird aus der VSPackage-Satelliten-DLL geladen.

 Der **Ordner** Wert stellt eine GUID eines Ordners dar, in dem der *Folder_Label_ResID* Knoten angezeigt wird. Im Beispiel stellt die GUID den Ordner **andere Projekte** im Bereich **Projekttypen** des Dialog Felds **Neues Projekt** dar. Wenn der Wert **anderer Projekte** nicht vorhanden ist, wird die Bezeichnung auf der obersten Ebene positioniert.

 Der- `TemplatesDir` Wert gibt den vollständigen Pfad des Verzeichnisses an, das die Projektvorlagen enthält. Diese Dateien können entweder *VSZ* -Dateien oder typische Vorlagen Dateien sein, die geklont werden sollen.

 Wenn Sie angeben `TemplatesLocalizedSubDir` , muss es sich um die Ressourcen-ID einer Zeichenfolge handeln, die das Unterverzeichnis von benennt, `TemplatesDir` das lokalisierte Vorlagen enthält. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Zeichen folgen Ressource aus einer Satelliten-DLL lädt (sofern vorhanden), kann jede Satelliten-DLL einen anderen Namen für das Unterverzeichnis enthalten. Der `SortPriority` Wert gibt eine Sortier Priorität an.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Hinzufügen von Verzeichnissen zum Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
