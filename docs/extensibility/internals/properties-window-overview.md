---
title: Übersicht über das Eigenschaften Fenster | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Schnittstellen, die für die Interaktion mit dem Eigenschaftenfenster in der Visual Studio-IDE in dieser Übersicht verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a33d393cfd904bdae890f4ead9a4c25a6451460
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837293"
---
# <a name="properties-window-overview"></a>Übersicht über Eigenschaftenfenster
Das Fenster **Eigenschaften** wird zum Anzeigen von Eigenschaften für Objekte verwendet, die in den beiden Haupttypen von Windows in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) ausgewählt sind. Diese beiden Windows-Typen sind:

- Tool Fenster, z. b. Projektmappen-Explorer, Klassenansicht und Objektkatalog

- Dokument Fenster, die Editoren und Designer als den Formular-Designer, den XML-Editor und den HTML-Editor enthalten

## <a name="using-the-properties-window"></a>Verwenden des Fensters "Eigenschaften"
 Das Fenster **Eigenschaften** zeigt die Eigenschaften von einzelnen oder mehreren ausgewählten Elementen an. Wenn mehrere Elemente ausgewählt sind, wird die Schnittmenge aller Eigenschaften für alle ausgewählten Objekte angezeigt.

 Im **Eigenschaften** Fenster werden Ereignisse angezeigt, die sich auf ein ausgewähltes Objekt innerhalb eines Formular Entwurfs Fensters oder HTML-Editor mit com+-Metadaten beziehen. Beispielsweise können Sie eine Schaltfläche auswählen und die zugehörigen Ereignisse anzeigen, z. b `OnClick` . ein Ereignis, das mit dieser Schaltfläche verknüpft werden kann.

 Ereignisse, die im **Eigenschaften** Fenster angezeigt werden, werden hauptsächlich mit Objekten verwendet, die an Code gebunden sind. Wenn Sie ein Dateiformat bearbeiten, das nicht mit Code zu tun hat, sind keine Ereignisse vorhanden. Ereignisse werden nur im **Eigenschaften** Fenster angezeigt, wenn eine Bindung zwischen ausgelaufendem Code und bestimmten Ereignissen besteht, die bestimmten Objekten zugeordnet sind. Ein Beispiel hierfür wäre Code hinter einem ausgewählten Objekt, das ausgeführt wird, wenn dieses Objekt aktiviert wird.

 In der folgenden Tabelle werden die primären Schnittstellen aufgelistet, die im Fenster **Eigenschaften** verwendet werden.

|Schnittstellenname|BESCHREIBUNG|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Stellt eine Liste von Kategorien für das **Eigenschaften** Fenster bereit und ordnet jede Eigenschaft einer Kategorie zu.|
|[IDispatch-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Macht die Methoden und Eigenschaften eines Objekts für Programmier Tools und andere Anwendungen verfügbar, die Automation unterstützen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Bietet Schaltflächen mit Auslassungs Zeichen (... *), die* als Generatoren bezeichnet werden. Wird verwendet, wenn ein Wert nicht einfach vom Benutzer in einem Textfeld eingegeben wird. Beispielsweise kann Sie verwendet werden, um eine Farbauswahl zu öffnen, die den RGB-Wert bestimmt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Bietet Zugriff auf Objekte, die zum Aktualisieren von Informationen verwendet werden, die im **Eigenschaften** Fenster angezeigt werden. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für jedes Fenster implementiert, das auswählbare Objekte mit zugehörigen Eigenschaften enthält, die angezeigt werden sollen.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Bietet Informationen zum Typ eines Objekts, z. b. Methoden einer Schnittstelle und Felder einer Struktur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Ermöglicht VSPackages das Empfangen von Benachrichtigungen über Auswahl Ereignisse und das Abrufen von Informationen über die aktuelle Projekt Hierarchie, das Element, den Elementwert und den Befehls Benutzeroberflächen Kontext.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Stellt die Umgebung mit Zugriff auf die Mehrfachauswahl bereit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Wird verwendet, um lokalisierte Namen für einige Eigenschaften bereitzustellen, die im **Eigenschaften** Fenster angezeigt werden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Benachrichtigt registrierte VSPackages über Änderungen an der aktuellen Auswahl, am Elementwert oder am Befehlsbenutzeroberflächenkontext.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Benachrichtigt die Umgebung über eine Änderung in der aktuellen Auswahl und bietet Zugriff auf die Hierarchie- und Elementinformationen in Bezug auf die neue Auswahl.|

 Weitere Informationen zu finden Sie in `IDispatch` der MSDN Library.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
- [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)
