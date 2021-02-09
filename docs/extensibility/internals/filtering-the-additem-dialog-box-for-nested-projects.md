---
title: Filtern des AddItem-Dialog Felds für in der Liste von Projekten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das AddItem-Dialogfeld für ein geschsted-Projekt in Visual Studio filtern, indem Sie die ivsfilteraddprojectitemdlg-Schnittstelle des übergeordneten Projekts implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 668a1c3bae34caa2dc6a12def2bcee56765adbb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886950"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Dialogfeld "AddItem" für die Liste der Projekte filtern
Wenn Sie ein **AddItem** -Dialogfeld für ein untergeordnetes Projekt anzeigen, kann das übergeordnete Projekt steuern, welche Elemente im Dialogfeld angezeigt werden.

 Mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle können Sie die Knoten filtern, die sich in einem **AddItem** -Dialogfeld befinden. Wenn das untergeordnete Projekt das **AddItem** -Dialogfeld anzeigt, kann das übergeordnete Projekt die `IVsFilterAddProjectItemDlg` -Schnittstelle implementieren und Elemente filtern, die andernfalls im Projekt des Kindes angezeigt werden.

 Wenn Projekte unter bestimmten übergeordneten Projekten nach Funktion gruppiert werden, können Sie implementieren, `IVsFilterAddProjectItemDlg` Wenn der Benutzer im Kontextmenü eines untergeordneten Projekts die Option **Projekt Element hinzufügen** auswählt. `IvsFilterAddProjectItemDlg displays`Nur für diese Gruppe spezifische Projekt Elemente oder Dateien werden implementiert. Projekt Elemente für andere Gruppen werden aus dem Dialogfeld herausgefiltert, auch wenn Sie im selben Verzeichnis gespeichert werden.

 Wenn ein Benutzer das **AddItem** -Dialogfeld für das untergeordnete Element öffnet, wird die Implementierung der-Schnittstelle des übergeordneten Projekts `IVsFilterAddProjectItemDlg` aufgerufen.

 Die `IVsFilterAddProjectItemDlg` Schnittstelle kann auch das Filtern nach Kategorie implementieren. Weitere Informationen finden Sie unter [Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) " und [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
