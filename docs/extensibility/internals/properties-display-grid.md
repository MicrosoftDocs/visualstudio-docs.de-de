---
title: Eigenschaften Anzeige Raster | Microsoft-Dokumentation
description: Erfahren Sie, wo sich die Felder Eigenschaftsnamen und Eigenschaftswerte im Raster des Eigenschaftenfenster befinden und wie Sie mit dem Raster beim Erweitern von Eigenschaften arbeiten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 418501ada340614d084e9796a59a46f8612aa743
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878026"
---
# <a name="properties-display-grid"></a>Eigenschaften Anzeige Raster

Im Fenster **Eigenschaften** werden Felder in einem Raster angezeigt. Die linke Spalte enthält die Eigenschaftsnamen. die Rechte Spalte enthält die Eigenschaftswerte.

## <a name="work-with-the-grid"></a>Arbeiten mit dem Raster

Die Liste mit zwei Spalten zeigt Konfigurations unabhängige Eigenschaften, die zur Entwurfszeit und ihren aktuellen Einstellungen geändert werden können. Beachten Sie, dass möglicherweise nicht alle Eigenschaften angezeigt werden. Eine Eigenschaft kann als ausgeblendet festgelegt werden, z. b. durch Implementieren der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> Methode. Vor allem, um Eigenschaften mit untergeordneten Eigenschaften auszublenden:

1. Legen Sie den- `pfDisplay` Parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> auf fest `FALSE` .

2. Legen Sie den- `pfHide` Parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> auf fest `TRUE` .

Um Informationen per Push an das **Eigenschaften** Fenster zu Übertragung, verwendet die IDE <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für jedes Fenster aufgerufen, das auswählbare Objekte mit zugehörigen Eigenschaften enthält, die im **Eigenschaften** Fenster angezeigt werden sollen. **Projektmappen-Explorer** Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> aufrufen `GetProperty` mithilfe von [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) in der Projekt Hierarchie, um die durchsuchbaren Objekte in der Hierarchie abzurufen.

Wenn das VSPackage keine __VSHPROPID unterstützt [. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)versucht die IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> mithilfe des Werts für __VSHPROPID zu verwenden [. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , den das Hierarchie Element oder die Elemente bereitstellen.

Das Projekt-VSPackage muss nicht erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> werden, weil das von der IDE bereitgestellte Fenster Paket, das es implementiert (z. b. **Projektmappen-Explorer**), <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in seinem Auftrag erstellt.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> besteht aus drei Methoden, die von der IDE aufgerufen werden:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> enthält die Anzahl der ausgewählten Objekte, die im **Eigenschaften** Fenster angezeigt werden sollen.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Gibt die `IDispatch` Objekte zurück, die ausgewählt werden, um im **Eigenschaften** Fenster angezeigt zu werden.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> ermöglicht es, dass alle-Objekte, die von zurückgegeben <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> werden, vom Benutzer ausgewählt werden. Dadurch kann das VSPackage die Auswahl, die dem Benutzer in der Benutzeroberfläche angezeigt wird, visuell aktualisieren.

Im Fenster **Eigenschaften** werden Informationen aus den `IDispatch` Objekten extrahiert, um die durchsuchten Eigenschaften abzurufen. Der Eigenschaften Browser verwendet `IDispatch` , um das Objekt zu Fragen, welche Eigenschaften durch Abfragen `ITypeInfo` abgerufen werden, die von abgerufen werden `IDispatch::GetTypeInfo` . Der Browser verwendet dann diese Werte, um das **Eigenschaften** Fenster auszufüllen und die Werte für die einzelnen Eigenschaften zu ändern, die im Raster angezeigt werden. Die Eigenschaften Informationen werden innerhalb des Objekts selbst beibehalten.

Da die zurückgegebenen Objekte unterstützen `IDispatch` , kann der Aufrufer Informationen wie den Namen des Objekts abrufen, indem er entweder `IDispatch::Invoke` oder `ITypeInfo::Invoke` mit einem vordefinierten Dispatchbezeichner (DISPID) aufruft, der die gewünschten Informationen darstellt. Deklarierte DISPIDs sind negativ, um sicherzustellen, dass Sie nicht mit benutzerdefinierten bezeichlern in Konflikt stehen.

Das Fenster **Eigenschaften** zeigt verschiedene Typen von Feldern an, abhängig von den Attributen spezifischer Eigenschaften eines ausgewählten Objekts. Zu diesen Feldern zählen Bearbeitungsfelder, Dropdown Listen und Links zu benutzerdefinierten Editor-Dialogfeldern.

- Werte, die in einer Aufzählungs Liste enthalten sind, werden von einer <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Abfrage an abgerufen `IDispatch` . Werte aus einer Aufzählungs Liste können im Eigenschaften Raster geändert werden, indem Sie auf den Feldnamen doppelklicken, oder indem Sie auf den Wert klicken und den neuen Wert aus der Dropdown Liste auswählen. Für Eigenschaften, die über vordefinierte Einstellungen aus aufgelisteten Listen verfügen, werden durch Doppelklicken auf den Eigenschaftsnamen in der Eigenschaften Liste die verfügbaren Optionen durchlaufen. Doppelklicken Sie für vordefinierte Eigenschaften, die nur über zwei Optionen verfügen, z. b. true/false, auf den Eigenschaften Namen, um zwischen den Optionen zu wechseln.

- Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false` den Wert aufweist und angibt, dass der Wert geändert wurde, wird der Wert in fettem Text angezeigt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> wird verwendet, um zu bestimmen, ob der Wert auf den ursprünglichen Wert zurückgesetzt werden kann. Wenn dies der Fall ist, können Sie wieder zum Standardwert wechseln, indem Sie mit der rechten Maustaste auf den Wert klicken und im angezeigten Menü zurück **setzen** auswählen. Andernfalls müssen Sie den Wert manuell wieder in den Standardwert ändern. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> mit können Sie auch die Namen von Eigenschaften lokalisieren und ausblenden, die während der Entwurfszeit angezeigt werden, aber nicht die Eigenschaftsnamen, die während der Laufzeit angezeigt werden.

- Wenn Sie auf die Schaltfläche mit den Auslassungs Punkten (...) klicken, wird eine Liste mit Eigenschafts Werten angezeigt, aus denen der Benutzer auswählen kann (z. b. eine Farbauswahl oder eine Schriftart <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> stellt diese Werte bereit.

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
