---
title: Entwerfen von Projekt Untertypen | Microsoft-Dokumentation
description: Erfahren Sie, wie Projekt Untertypen VSPackages das Erweitern von Projekten basierend auf dem Microsoft-Build-Engine (MSBuild) ermöglichen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea4132f098658b3757d999ded537268cd9121e1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896844"
---
# <a name="project-subtypes-design"></a>Entwurf von Projektuntertypen

Mithilfe von Projekt Untertypen können VSPackages Projekte basierend auf dem Microsoft-Build-Engine (MSBuild) erweitern. Durch die Verwendung von Aggregationen können Sie den Großteil des verwalteten, in implementierten Projekt Systems wieder verwenden, indem Sie trotzdem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das Verhalten für ein bestimmtes Szenario anpassen.

 In den folgenden Themen wird das grundlegende Design und die Implementierung von Projekt Untertypen ausführlich erläutert:

- Design des Projekt unter Typs.

- Aggregation auf mehreren Ebenen.

- Unterstützende Schnittstellen.

## <a name="project-subtype-design"></a>Design des Projekt unter Typs

Die Initialisierung eines Projekt unter Typs wird durch aggregierten der Haupt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -und- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> Objekte erreicht. Diese Aggregation ermöglicht einem Projekt Untertyp, die meisten Funktionen des Basis Projekts zu überschreiben oder zu verbessern. Projekt Untertypen erhalten die erste Möglichkeit, Eigenschaften mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , Befehlen mit <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> und der Projekt Element Verwaltung mithilfe von zu verarbeiten <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Projekt Untertypen können auch erweitert werden:

- Projekt Konfigurationsobjekte.

- Konfigurations abhängige Objekte.

- Konfigurations unabhängige Objekte zum Durchsuchen.

- Project Automation-Objekte.

- Eigenschaften Auflistungen für Projektautomatisierung.

Weitere Informationen zur Erweiterbarkeit durch Projekt Untertypen finden Sie unter [Eigenschaften und Methoden, die von Projekt Untertypen erweitert](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)wurden.

### <a name="policy-files"></a>Richtliniendateien

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung bietet ein Beispiel für die Erweiterung des Basisprojekt Systems mit einem Projekt Untertyp in der Implementierung von Richtlinien Dateien. Eine Richtlinien Datei ermöglicht die Strukturierung der Umgebung durch die Verwaltung von Funktionen, die das Dialogfeld [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektmappen-Explorer, **Projekt hinzufügen** , Dialogfeld **Neues Element hinzufügen** und das Dialogfeld **Eigenschaften** enthalten. Der Richtlinientyp überschreibt und erweitert diese Features durch <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` -Implementierungen und- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Implementierungen.

### <a name="aggregation-mechanism"></a>Aggregations Mechanismus

Der Aggregations Mechanismus des Projekt unter Typs der Umgebung unterstützt mehrere Aggregations Ebenen, sodass ein erweiterter Untertyp implementiert werden kann, indem ein Projekt mit einem Projekt erweitert wird. Außerdem werden die unterstützenden Objekte eines Projekt unter Typs, wie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> . b., so entworfen, dass Sie mehrere Ebenen von Schichten ermöglichen. In Übereinstimmung mit den Einschränkungen von com-und com-Aggregations Regeln müssen Projekt Untertypen und Basisprojekte kooperativ programmiert werden, damit der innere Untertyp oder das Basisprojekt ordnungsgemäß an delegierenden Methoden aufrufen und der Verwaltung von Verweis Zählungen beteiligt sein kann. Das heißt, das Projekt, das aggregiert werden soll, muss zur Unterstützung von Aggregationen programmiert werden.

In der folgenden Abbildung ist eine Schema übergreifende Darstellung einer Projekt Untertypen Aggregation mit mehreren Ebenen dargestellt.

![Grafik zu Visual Studio-Mehrebenen-Projekttyp](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Eine mehrstufige Projekt Untertyp Aggregation besteht aus drei Ebenen, einem Basisprojekt, das durch einen Projekt Untertyp aggregiert wird, und wird dann durch einen erweiterten Projekt Untertyp aggregiert. Die Abbildung konzentriert sich auf einige der unterstützenden Schnittstellen, die als Teil der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Architektur des Projekt unter Typs bereitgestellt werden.

### <a name="deployment-mechanisms"></a>Bereitstellungs Mechanismen

Zu vielen der grundlegenden Projekt Systemfunktionen, die durch einen Projekt Untertyp erweitert werden, sind Bereitstellungs Mechanismen. Ein Projekt Untertyp wirkt sich auf Bereitstellungs Mechanismen durch Implementieren von Konfigurations Schnittstellen (z. b. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ) aus, die durch den Aufruf von QueryInterface in abgerufen werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> In einem Szenario, in dem sowohl der Projekt Untertyp als auch der erweiterte Projekt Untertyp verschiedene Konfigurations Implementierungen hinzufügen, ruft das Basisprojekt `QueryInterface` auf dem des erweiterten Projekt unter Typs auf `IUnknown` . Wenn der innere Projekt Untertyp die Konfigurations Implementierung enthält, die das Basisprojekt anfordert, delegiert der erweiterte Projekt Untertyp an die-Implementierung, die vom inneren Projekt Untertyp bereitgestellt wird. Um den Zustand von einer Aggregations Ebene in eine andere beizubehalten, werden alle Ebenen von Projekt Untertypen implementiert, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> um nicht auf Builds bezogene XML-Daten in den Projektdateien beizubehalten. Weitere Informationen finden Sie unter [persistente Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> ist als Mechanismus zum Abrufen von Automatisierungsextendern aus den Projekt Untertypen implementiert.

In der folgenden Abbildung liegt der Schwerpunkt auf der Implementierung des Automation-Extenders, dem speziellen Projekt Konfigurations Such Objekt, das von Projekt Untertypen verwendet wird, um das Basisprojekt System zu erweitern.

![Grafik zu VS-Projekttyp Automatisierungsextender](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Projekt Untertypen können das Basisprojekt System durch Erweitern des Automatisierungs Objektmodells weiter erweitern. Diese werden als Teil des DTE-Automatisierungs Objekts definiert und zum Erweitern des Project-Objekts, des `ProjectItem` -Objekts und des- `Configuration` Objekts verwendet. Weitere Informationen finden Sie unter [Erweitern des Objektmodells des Basis Projekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Aggregation auf mehreren Ebenen

Eine Projekt Untertyp Implementierung, die einen Projekt Untertyp auf niedrigerer Ebene umschließt, muss kooperativ programmiert werden, damit der innere Projekt Untertyp ordnungsgemäß funktioniert. Eine Liste der Programmier Zuständigkeiten umfasst:

- Die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementierung des Projekt unter Typs, der den inneren Untertyp umwickelt, muss für die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> -Methode und die-Methode an die-Implementierung des inneren Projekt unter Typs delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- Die <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des Wrapper Projekt unter Typs muss an den des inneren Projekt unter Typs delegieren. Insbesondere muss die Implementierung von <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> die Zeichenfolge der Namen aus dem inneren Projekt Untertyp erhalten und dann die Zeichen folgen verketten, die als Extender hinzugefügt werden sollen.

- Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Implementierung eines Wrapper Projekt unter Typs muss das <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> Objekt seines inneren Projekt unter Typs instanziieren und als privaten Delegaten speichern, da nur das Projekt Konfigurationsobjekt des Basis Projekts direkt weiß, dass das Konfigurationsobjekt des Wrapper Projekt unter Typs vorhanden ist. Der äußere Projekt Untertyp kann anfänglich Konfigurations Schnittstellen auswählen, die direkt behandelt werden sollen, und dann den Rest an die Implementierung von des inneren Projekt unter Typs delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Unterstützende Schnittstellen

Das Basisprojekt delegiert Aufrufe an unterstützende Schnittstellen, die von einem Projekt Untertyp hinzugefügt werden, um verschiedene Aspekte der Implementierung zu erweitern. Dies schließt die Erweiterung der Projekt Konfigurationsobjekte und verschiedener Eigenschaften Browser Objekte ein. Diese Schnittstellen werden durch Aufrufen `QueryInterface` von `punkOuter` (einem Zeiger auf `IUnknown` ) des äußersten Projekt Untertyp Aggregators abgerufen.

|Schnittstelle|Projekt Untertyp|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Ermöglicht dem Projekt Untertyp Folgendes:<br /><br /> : Stellen Sie eine Implementierung von bereit <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />-Steuern Sie den Start des Debuggers, indem Sie zulassen, dass der Projekt Untertyp seine eigene Implementierung von bereitstellt <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />-Deaktivieren Sie die Ausdrucks Auswertung zur Entwurfszeit, indem Sie den `DBGLAUNCH_DesignTimeExprEval` Fall in der Implementierung von ordnungsgemäß behandeln <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Ermöglicht dem Projekt Untertyp Folgendes:<br /><br /> -Erweitern <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> Sie den des Projekts, um die Konfigurations unabhängigen Eigenschaften des Projekts hinzuzufügen oder zu entfernen.<br />-Erweitern Sie das Project Automation-Objekt ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) des Projekts.<br /><br /> Die oben aufgeführten Eigenschaftswerte werden aus der- <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Enumeration entnommen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Ermöglicht, dass der Projekt Untertyp dem-Objekt zurückgegeben wird, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Wenn das Projekt Konfigurations Such Objekt angezeigt wird.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Ermöglicht, dass der Projekt Untertyp dem- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt oder dem- `VSITEMID` Objekt zugeordnet wird, wenn das Projekt Konfigurations Such Objekt angezeigt wird.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Ermöglicht dem Projekt Untertyp, beliebige strukturierte XML-Daten in der Projektdatei (. vbproj oder. csproj) beizubehalten. Diese Daten sind für MSBuild nicht sichtbar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Ermöglicht dem Projekt Untertyp Folgendes:<br /><br /> -Hinzufügen neuer MSBuild-Eigenschaften, die persistent gespeichert werden sollen.<br />-Entfernen Sie unnötige Eigenschaften aus MSBuild.<br />-Abfrage für einen aktuellen Wert einer MSBuild-Eigenschaft.<br />: Ändert den aktuellen Wert einer MSBuild-Eigenschaft.|

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
