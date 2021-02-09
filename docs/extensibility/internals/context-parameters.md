---
title: Kontext Parameter | Microsoft-Dokumentation
description: Erfahren Sie mehr über Kontext Parameter in der integrierten Entwicklungsumgebung (IDE) von Visual Studio, die den Zustand eines Projekts definieren, wenn Sie einen Assistenten hinzufügen oder implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d2c6ded39564b91ba4f7b74fe2985aab14a7ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852621"
---
# <a name="context-parameters"></a>Kontextparameter
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) können Sie Assistenten zu den Dialogfeldern **Neues Projekt**, **Neues Element hinzu** fügen oder **Unterprojekt hinzufügen** hinzufügen. Die hinzugefügten Assistenten sind im Menü **Datei** verfügbar, oder Sie klicken mit der rechten Maustaste auf ein Projekt in **Projektmappen-Explorer**. Die IDE übergibt Kontext Parameter an die Implementierung des Assistenten. Die Kontext Parameter definieren den Status des Projekts, wenn der Assistent von der IDE aufgerufen wird.

 Die IDE startet Assistenten, indem das <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> -Flag im-Befehl der IDE auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> Methode für das Projekt festgelegt wird. Wenn festgelegt, muss das Projekt bewirken, `IVsExtensibility::RunWizardFile` dass die Methode ausgeführt wird, indem der Name oder die GUID des registrierten Assistenten und andere Kontext Parameter verwendet werden, die von der IDE an ihn weitergeleitet werden.

## <a name="context-parameters-for-new-project"></a>Kontext Parameter für neues Projekt

| Parameter | Beschreibung |
|-------------------------| - |
| `WizardType` | Registrierter Wizard Type ( <xref:EnvDTE.Constants.vsWizardNewProject> ) oder die GUID, die den Typ des Assistenten angibt. In der- [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Implementierung lautet der GUID für den Assistenten {0F 90e1d0-4999-11d1-B6D1-00a0c90f 2744}. |
| `ProjectName` | Eine Zeichenfolge, die der eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname ist. |
| `LocalDirectory` | Lokaler Speicherort von Arbeitsprojekt Dateien. |
| `InstallationDirectory` | Der Verzeichnispfad von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist "Installation". |
| `FExclusive` | Boolesches Flag, das angibt, dass das Projekt geöffnete Projektmappen schließen soll. |
| `SolutionName` | Der Name der Projektmappendatei ohne den Verzeichnis Teil bzw. die Erweiterung " *. sln* ". Der *suo* -Dateiname wird auch mithilfe von erstellt `SolutionName` . Wenn dieses Argument keine leere Zeichenfolge ist, verwendet der Assistent, <xref:EnvDTE._Solution.Create%2A> bevor das Projekt mit dem hinzugefügt wird <xref:EnvDTE._Solution.AddFromTemplate%2A> . Wenn dieser Name eine leere Zeichenfolge ist, verwenden Sie <xref:EnvDTE._Solution.AddFromTemplate%2A> ohne Aufrufen von <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll, als ob auf **Fertig** stellen geklickt wurde ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Kontext Parameter für "Neues Element hinzufügen"

| Parameter | Beschreibung |
|-------------------------| - |
| `WizardType` | Registrierter Wizard Type ( <xref:EnvDTE.Constants.vsWizardAddItem> ) oder die GUID, die den Typ des Assistenten angibt. In der- [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Implementierung lautet der GUID für den Assistenten {0F 90e1d1-4999-11d1-B6D1-00a0c90f 2744}. |
| `ProjectName` | Eine Zeichenfolge, die der eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname ist. |
| `ProjectItems` | Lokaler Speicherort, der funktionierende Projektdateien enthält. |
| `ItemName` | Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist entweder der Standard Dateiname oder der Dateiname, den der Benutzer im Dialogfeld **Elemente hinzufügen** eingibt. Der Name basiert auf den Flags, die in der *VSDIR* -Datei festgelegt sind. Der Name kann ein NULL-Wert sein. |
| `InstallationDirectory` | Der Verzeichnispfad von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist "Installation". |
| `Silent` | Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll, als ob auf **Fertig** stellen geklickt wurde ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Kontext Parameter für "Sub Project hinzufügen"

| Parameter | Beschreibung |
|-------------------------| - |
| `WizardType` | Registrierter Wizard Type ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) oder die GUID, die den Typ des Assistenten angibt. In der- [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Implementierung lautet der GUID für den Assistenten {0F 90e1d2-4999-11d1-B6D1-00a0c90f 2744}. |
| `ProjectName` | Eine Zeichenfolge, die der eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname ist. |
| `ProjectItems` | Ein Zeiger auf die Auflistung `ProjectItems` , in der der Assistent ausgeführt wird. Dieser Zeiger wird basierend auf der Auswahl der Projekt Hierarchie an den Assistenten weitergeleitet. Ein Benutzer wählt in der Regel einen Ordner aus, in den das Element eingefügt werden soll, und ruft dann das Dialogfeld **Element hinzufügen** des Projekts auf. |
| `LocalDirectory` | Lokaler Speicherort von Arbeitsprojekt Dateien. |
| `ItemName` | Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist entweder der Standard Dateiname oder der Dateiname, den der Benutzer im Dialogfeld **Elemente hinzufügen** eingibt. Der Name basiert auf den Flags, die in der *VSDIR* -Datei festgelegt sind. Der Name kann ein NULL-Wert sein. |
| `InstallationDirectory` | Verzeichnispfad der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installation. |
| `Silent` | Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll, als ob auf **Fertig** stellen geklickt wurde ( `TRUE` ). |

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)
- [The](../../extensibility/internals/wizards.md)
- [Assistenten Datei (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Kontext Parameter für das Starten von Assistenten](/previous-versions/tz690efs(v=vs.140))