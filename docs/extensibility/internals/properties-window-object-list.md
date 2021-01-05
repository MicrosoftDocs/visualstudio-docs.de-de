---
title: Objektliste "Eigenschaften Fenster" | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Schnittstellen, die für die Interaktion mit der Objektliste im Eigenschaftenfenster in der Visual Studio-IDE verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92fcce4dc62cdc84d15ca6dc51420791d4460340
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875426"
---
# <a name="properties-window-object-list"></a>Objektliste des Eigenschaftenfensters
Die Objektliste im **Eigenschaften** Fenster ist eine Dropdown Liste, mit der Sie die Auswahl in andere Objekte ändern können, die in einem oder mehreren ausgewählten Fenstern verfügbar sind. Wenn Sie ein anderes Objekt aus dieser Liste auswählen, wird ein Rückruf von ausgelöst <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> , um die Umgebung darüber zu informieren, dass ein neues-Objekt ausgewählt wurde. Die im **Eigenschaften** Fenster angezeigten Informationen werden dann geändert, um die Eigenschaften anzuzeigen, die dem neu ausgewählten Objekt zugeordnet sind.

## <a name="the-object-list"></a>Die Objektliste
 Die Objektliste besteht aus zwei Feldern: dem Objektnamen (fett angezeigt) und dem Objekttyp.

 Der im fett formatierten Objekttyp angezeigte Objektname wird aus dem Objekt selbst abgerufen, wobei die `Name` von der Schnittstelle bereitgestellte Eigenschaft verwendet wird <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> . <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, die einzige Methode für <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , gibt <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> für die Co-Klasse der Schnittstelle zurück. Im **Eigenschaften** Fenster wird verwendet, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> um den Namen der Co-Klasse zu erhalten, die als Objektname in der Dropdown Liste angezeigt wird.

 Wenn das Objekt nicht über eine `Name` Eigenschaft verfügt, wird ein Name nicht im namens Bereich der Objektliste angezeigt. Sie können dem-Objekt eine Name-Eigenschaft hinzufügen, wenn der Name in der Objektliste angezeigt werden soll.

 Wenn das COM-Objekt nicht implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , zeigt das **Eigenschaften** Fenster den Schnittstellennamen anstelle des Objekt namens auf der linken Seite der Liste an.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
