---
title: Hinzufügen eines Attributs zu einem Projekt Element | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Attribut zu einem Projekt Element in Visual Studio hinzufügen, indem Sie die shellinterop-Methoden getitemattribute und setitemattribute verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d43745155193baadc87784c0e99123461dda1eed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951315"
---
# <a name="add-an-attribute-to-a-project-item"></a>Hinzufügen eines Attributs zu einem Projekt Element
Mit den Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> und wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> der Wert der Attribute eines Projekt Elements erhalten und festgelegt. "", Wenn das Attribut nicht bereits vorhanden ist, wird das Attribut erstellt, und die Metadaten werden den Projekt Element Metadaten hinzugefügt.

## <a name="add-an-attribute-to-a-project-item"></a>Hinzufügen eines Attributs zu einem Projekt Element

- Im folgenden Code werden das <xref:EnvDTE.DTE> Automation-Objekt und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> Methode verwendet, um einem Projekt Element ein Attribut hinzuzufügen. Die Projekt Element-ID wird aus dem Projekt Elementnamen "Program.cs" abgerufen. Das Attribut "MyAttribute" wird diesem Projekt Element hinzugefügt und erhält den Wert "myValue".

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Weitere Informationen
- [Persistente Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
