---
title: Benutzeroberfläche der Projekteigenschaften | Microsoft-Dokumentation
description: Erfahren Sie, wie Projekt Untertypen das Dialogfeld Eigenschaften Seiten des Projekts ändern können, wie im Basisprojekt bereitgestellt.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c9bba8b163b7fd21cfa829bb26e06cf37b887bd
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877389"
---
# <a name="project-property-user-interface"></a>Benutzeroberfläche für Projekteigenschaften

Ein Projekt Untertyp kann die Elemente im Dialogfeld **Eigenschaften Seiten** des Projekts verwenden, da Sie vom Basisprojekt bereitgestellt werden, schreibgeschützte Steuerelemente und ganze Seiten als Bereitstellung ausblenden oder schreibgeschützte Steuerelemente und ganze Seiten als hinzufügen oder Projekt Untertyp spezifische Seiten zum Dialogfeld **Eigenschaften Seiten** hinzufügen.

## <a name="extending-the-project-property-dialog-box"></a>Erweitern der Projekt Eigenschaft (Dialog Feld)

Ein Projekt Untertyp implementiert Automatisierungsextenders und Projektkonfigurations-Such Objekte. Diese Extender implementieren die- <xref:EnvDTE.IFilterProperties> Schnittstelle, um bestimmte Eigenschaften als ausgeblendet oder schreibgeschützt zu gestalten. Im Dialogfeld **Eigenschaften Seiten** des Basis Projekts, das vom Basisprojekt implementiert wird, wird die von den Automatisierungsextendern ausgeführte Filterung berücksichtigt.

Der Prozess der Erweiterung des Dialog Felds " **Projekteigenschaften** " wird im folgenden beschrieben:

- Das Basisprojekt Ruft die Extender aus dem Projekt Untertyp ab, indem die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle implementiert wird. Diese Schnittstelle wird durch die Such-, Projekt Automation-und Projektkonfigurations-Such Objekte des Basis Projekts implementiert.

- Die Implementierung von <xref:EnvDTE80.IInternalExtenderProvider> für das Project Browse-Objekt und das Project Automation-Objekt Delegat zur <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des Projekt unter typaggregators (d. h `QueryInterface` ., für <xref:EnvDTE80.IInternalExtenderProvider> das <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Projekt Objekt).

- Das Basisobjekt für die Projekt Konfigurations Suche implementiert auch <xref:EnvDTE80.IInternalExtenderProvider> , um den Automation-Extender direkt aus dem Konfigurationsobjekt des Projekt unter Typs zu übertragen. Die Implementierung delegiert an die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die durch den Projekt Untertyp Aggregator implementiert wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>Gibt das-Objekt zurück, das vom Projekt Konfigurations Such Objekt implementiert wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, auch vom Projekt Konfigurations Such Objekt implementiert, gibt das- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Objekt zurück.

- Mit einem Projekt Untertyp können die entsprechenden CATIDs für die verschiedenen erweiterbaren Objekte des Basis Projekts zur Laufzeit ermittelt werden, indem die folgenden Werte abgerufen werden <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> :

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Zum Ermitteln der CATIDs für den Projektbereich ruft der Projekt Untertyp die oben genannten Eigenschaften für [vsitemid ab. Der Stamm aus der](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` . Ein Projekt Untertyp kann auch steuern, welche **Eigenschaften Seiten** -Dialogfeld Seiten für das Projekt angezeigt werden, und zwar sowohl von der Konfiguration abhängig als auch von der Konfiguration unabhängig voneinander. Einige Projekt Untertypen müssen möglicherweise integrierte Seiten entfernen und Projekt Untertyp spezifische Seiten hinzufügen. Um dies zu ermöglichen, ruft das verwaltete Client Projekt die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Methode für die folgenden Eigenschaften auf:

- `VSHPROPID_PropertyPagesCLSIDList` – eine durch Semikolons getrennte Liste von CLSIDs von Konfigurations unabhängigen Eigenschaften Seiten.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` eine durch Semikolons getrennte Liste von CLSIDs von Konfigurations abhängigen Eigenschaften Seiten.

Da der Projekt Untertyp das Objekt aggregiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , kann es die Definition dieser Eigenschaften überschreiben, um zu steuern, welche Eigenschaften **Seiten** Dialogfelder angezeigt werden. Der Projekt Untertyp kann diese Eigenschaften aus dem inneren Basisprojekt abrufen und dann ggf. CLSIDs hinzufügen oder entfernen.

Neue Eigenschaften Seiten, die durch einen Projekt Untertyp hinzugefügt wurden, werden einem Projekt Konfigurations Such Objekt aus der Basisprojekt Implementierung übergeben. Dieses Objekt zum Durchsuchen von Projekt Konfigurationen unterstützt Automatisierungs Erweiterungen. Weitere Informationen zu automationextenders finden Sie unter [implementieren und Verwenden von automatisierungsexextender](/previous-versions/0y92k2w2(v=vs.140)). Die Eigenschaften Seiten, die durch den Projekt Untertyp implementiert werden <xref:EnvDTE.Project.Extender%2A> , rufen Ihr eigenes Projekt Untertypen-Konfigurations Such Objekt ab, das das Konfigurations Such Objekt des Basis Projekts erweitert.

## <a name="see-also"></a>Weitere Informationen

- <xref:EnvDTE.IFilterProperties>
- [Dialog Feld "Eigenschaften Seiten"](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))