---
title: Erweitern des Objektmodells des Basis Projekts | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das Automatisierungs Objektmodell des Basis Projekts in Visual Studio mithilfe eines Projekt unter Typs erweitern.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4e3d7ad3f19aedc59288d6799e97d91499939c9
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479458"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Erweitern des Objektmodells des Basis Projekts

Mit einem Projekt Untertyp kann das Automatisierungs Objektmodell des Basis Projekts an den folgenden Stellen erweitert werden:

- Project. Extender (" \<ProjectSubtypeName> "): Dies ermöglicht einem Projekt Untertyp das anbieten eines Objekts mit benutzerdefinierten Methoden aus dem- <xref:EnvDTE.Project> Objekt. Ein Projekt Untertyp kann Automatisierungs Erweiterungen verwenden, um das Objekt verfügbar zu machen `Project` . Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, muss das-Objekt für den `VSHPROPID_ExtObjectCATID` von <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (entsprechend einem `itemid` Wert von [vsitemid) anbieten. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): Dies ermöglicht einem Projekt Untertyp das anbieten eines Objekts mit benutzerdefinierten Methoden aus einem bestimmten <xref:EnvDTE.ProjectItem> Objekt innerhalb des Projekts. Ein Projekt Untertyp kann Automatisierungs Erweiterungen verwenden, um dieses Objekt verfügbar zu machen. Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, muss das-Objekt für den `VSHPROPID_ExtObjectCATID` von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (entsprechend einer gewünschten <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ) CATID anbieten.

- Project. Properties: Diese Auflistung macht die Konfigurations unabhängigen Eigenschaften des- `Project` Objekts verfügbar. Weitere Informationen zu `Project`-Eigenschaften finden Sie unter <xref:EnvDTE.Project.Properties%2A>. Ein Projekt Untertyp kann mithilfe von Automatisierungsextendern seine Eigenschaften zu dieser Auflistung hinzufügen. Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, muss das-Objekt für den `VSHPROPID_BrowseObjectCATID` von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (entsprechend einem `itemid` Wert von [vsitemid) anbieten. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties: diese Sammlung macht die Konfigurations abhängigen Eigenschaften des Projekts für eine bestimmte Konfiguration verfügbar (z. b. Debug). Weitere Informationen finden Sie unter <xref:EnvDTE.Configuration>. Ein Projekt Untertyp kann mithilfe von Automatisierungsextendern seine Eigenschaften zu dieser Auflistung hinzufügen. Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, stellt das-Objekt für die CATID `VSHPROPID_CfgBrowseObjectCATID` (entsprechend einem `itemid` Wert von [vsitemid) zur Auswahl. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> Schnittstelle wird verwendet, um ein Konfigurations Such Objekt von einem anderen zu unterscheiden.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
