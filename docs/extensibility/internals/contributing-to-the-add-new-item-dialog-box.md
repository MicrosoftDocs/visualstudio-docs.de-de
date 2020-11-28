---
title: Beitrag zum Dialog Feld "Neues Element hinzufügen" | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie im Dialogfeld Neues Element hinzufügen in Visual Studio mitwirken können, indem Sie unter dem Projekt Registrierungs Unterschlüssel die Option Element Vorlagen hinzufügen registrieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94a13890f0b5e60b1da204b89a01c1cadc6d00c4
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304637"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Mitwirken zum Dialogfeld "Neues Element hinzufügen"
Ein Projekt Untertyp kann ein neues Element Verzeichnis für das Dialogfeld **Neues Element hinzufügen** bereitstellen, indem Sie unter dem **Projekt** Registrierungs Unterschlüssel die Option **Element Vorlagen hinzufügen** registrieren.

## <a name="register-add-new-item-templates"></a>Register Hinzufügen neuer Element Vorlagen
 Dieser Abschnitt befindet sich in der Registrierung unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** . In den folgenden Registrierungs Einträgen wird davon ausgegangen, dass ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt durch einen hypothetischen Projekt Untertyp aggregiert wird. Die Einträge für das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt sind unten aufgeführt.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]
@="#2143"
"DefaultProjectExtension"="vbproj"
"PossibleProjectExtensions"="vbproj;vbp"
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]
@="#100"
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"
```

 Der Unterschlüssel **additemtemplates\templatedirs** enthält Registrierungseinträge mit dem Pfad zum Verzeichnis, in dem Elemente, die im Dialogfeld **Neues Element hinzufügen** verfügbar gemacht wurden, platziert werden.

 Die Umgebung lädt automatisch alle **additemtemplates** -Daten unter den **Projekt** Registrierungs Unterschlüssel. Diese Daten können die Daten für Basisprojekt Implementierungen sowie die Daten für bestimmte Projekt Untertypen Typen enthalten. Jeder Projekt Untertyp wird durch eine Projekttyp- **GUID** identifiziert. Der Projekt Untertyp kann angeben, dass ein alternativer Satz von **Add-Element** -Vorlagen für eine bestimmte Projekt Instanz verwendet werden soll, indem die `VSHPROPID_ AddItemTemplatesGuid` Enumeration von in der Implementierung unterstützt wird <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> , um den GUID-Wert des Projekt unter Typs zurückzugeben. Wenn die- `VSHPROPID_AddItemTemplatesGuid` Eigenschaft nicht angegeben wird, wird die Basisprojekt-GUID verwendet.

 Sie können Elemente im Dialogfeld **Neues Element hinzufügen** filtern, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> Schnittstelle für das Projekt Untertyp-Aggregator-Objekt implementieren. Beispielsweise kann ein Projekt Untertyp, der ein Datenbankprojekt durch das aggregierten eines [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekts implementiert, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bestimmten Elemente im Dialogfeld **Neues Element hinzufügen** filtern, indem Sie Filter implementiert und wiederum Datenbankprojekt spezifische Elemente hinzufügen, indem Sie in unterstützt `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Weitere Informationen zum Filtern und Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzu** fügen finden [Sie unter Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)fügen".

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
