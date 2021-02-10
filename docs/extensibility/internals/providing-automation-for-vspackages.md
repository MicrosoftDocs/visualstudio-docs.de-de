---
title: Bereitstellen von Automatisierung für VSPackages | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Automation für Ihre VSPackages bereitstellen, indem Sie VSPackage-spezifische Objekte implementieren und standardmäßige Automatisierungs Objekte implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d5a0bd912dadf6b8f90aabd846c6ac44534c917
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934076"
---
# <a name="providing-automation-for-vspackages"></a>Bereitstellen von Automatisierung für VSPackages
Es gibt zwei Hauptmethoden zum Bereitstellen von Automatisierung für Ihre VSPackages: durch das Implementieren von VSPackage-spezifischen Objekten und durch Implementieren von Automation-Standardobjekten. Diese werden in der Regel verwendet, um das Automatisierungs Modell der Umgebung zu erweitern.

## <a name="vspackage-specific-objects"></a>VSPackage-Specific Objekte
 Für bestimmte Orte innerhalb des Automatisierungs Modells müssen Sie Automatisierungs Objekte bereitstellen, die für Ihr VSPackage eindeutig sind. Beispielsweise erfordern neue Projekte eindeutige Objekte, die nur von Ihrem VSPackage bereitstellt werden. Die Namen dieser Objekte werden in der Registrierung eingegeben und durch Aufrufe des Umgebungs `DTE` Objekts abgerufen.

 VSPackage-spezifische Objekte können auch abgerufen werden, wenn ein automatisierungsconsumer das Objekt verwendet, das durch die Object-Eigenschaft eines Standard Objekts bereitgestellt wird. Beispielsweise verfügt das-Standard `Window` Objekt über eine- `Object` Eigenschaft, die in der Regel als-Eigenschaft bekannt ist `Windows.Object` . Wenn Consumer den `Window.Object` in einem in Ihrem VSPackage implementierten Fenster aufzurufen, geben Sie ein bestimmtes Automatisierungs Objekt Ihres eigenen Entwurfs zurück.

#### <a name="projects"></a>Projekte
 VSPackages können das Automatisierungs Modell für neue Projekttypen über ihre eigenen VSPackage-spezifischen Objekte erweitern. Der Hauptzweck der Bereitstellung neuer Automatisierungs Objekte für Ihr VSPackage besteht darin, Ihre eindeutigen Projekt Objekte von einem- <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> Objekt oder einem-Objekt zu unterscheiden <xref:VSLangProj80.VSProject2> . Diese Differenzierung ist praktisch, wenn Sie eine Möglichkeit bereitstellen möchten, den Projekttyp außer anderen Projekttypen auszulagern oder zu durchlaufen, wenn Sie in einer Projekt Mappe nebeneinander angezeigt werden. Weitere Informationen finden Sie unter verfügbar machen von [Projekt Objekten](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Ereignisse
 Die Ereignis Architektur der Umgebung bietet einen weiteren Ort, an dem Sie Ihre eigenen VSPackage-spezifischen Objekte anfügen können. Wenn Sie z. b. ihre eigenen eindeutigen Ereignis Objekte erstellen, können Sie das-Ereignis Modell der Umgebung für-Projekte erweitern. Sie können Ihre eigenen Ereignisse auch dann bereitstellen, wenn Ihrem eigenen Projekttyp ein neues Element hinzugefügt wird. Weitere Informationen finden Sie unter verfügbar machen von [Ereignissen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Fensterobjekte
 Windows kann ein VSPackage-spezifisches Automatisierungs Objekt zurück an die Umgebung zurückgeben, wenn es aufgerufen wird. Sie implementieren ein Objekt, das von abgeleitet <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> ist <xref:EnvDTE.IExtensibleObject> oder `IDispatch` Eigenschaften zurückgibt, um das Fenster Objekt zu erweitern, in dem es sich befindet. Beispielsweise können Sie diesen Ansatz verwenden, um die Automatisierung für ein Steuerelement bereitzustellen, das in einem Fensterrahmen positioniert ist. Die Semantik dieses Objekts und aller anderen Objekte, die es erweitern kann, ist die Entwurfs-. Weitere Informationen finden Sie unter Gewusst [wie: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Options Seiten im Menü "Extras"
 Sie können Seiten erstellen, um die Tools, das Automatisierungs Modell für Optionen durch das Implementieren von Seiten und das Hinzufügen von Informationen zur Registrierung zu erweitern, um eigene Optionen zu erstellen. Ihre Seiten können dann über das Umgebungs Objektmodell wie alle anderen Options Seiten aufgerufen werden. Wenn der Entwurf des Features, das Sie der Umgebung mithilfe von VSPackages hinzufügen, Options Seiten erfordert, sollten Sie auch die Automation-Unterstützung hinzufügen. Weitere Informationen finden Sie [unter Automatisierungsunterstützung für options Seiten](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Standard mäßige Automatisierungs Objekte
 Um die Automatisierung für Projekte zu erweitern, implementieren Sie auch Standard Automatisierungs Objekte (abgeleitet von `IDispatch` ), die neben den anderen Projekt Objekten stehen, und implementieren Standardmethoden und-Eigenschaften. Beispiele für Standardobjekte sind die Projekt Objekte, die in die Projektmappenhierarchie eingefügt werden, wie z `Projects` `Project` . b.,, `ProjectItem` und `ProjectItems` . Jeder neue Projekttyp sollte diese Objekte (und möglicherweise andere) implementieren, abhängig von der Semantik Ihres Projekts.

 In gewisser Weise bieten diese Objekte den entgegengesetzten Vorteil der VSPackage-spezifischen Projekt Objekte. Mit den standardmäßigen Automatisierungs Objekten kann das Projekt generalisiert verwendet werden, wie bei jedem anderen Projekt, das dieselben Objekte unterstützt. Folglich kann ein Add-in, das für allgemeine `Project` und-Objekte geschrieben wird, `ProjectItem` für Projekte eines beliebigen Typs funktionieren. Weitere Informationen finden Sie unter [Projekt Modellierung](../../extensibility/internals/project-modeling.md).
