---
title: Schaltflächen für Eigenschaften Fenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b66015ef2e2ab0c8105b6f84486fa890adbf8b1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841044"
---
# <a name="properties-window-buttons"></a>Schaltflächen des Eigenschaftenfensters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abhängig von der Entwicklungssprache und dem Produkttyp werden standardmäßig bestimmte Schaltflächen auf der Symbolleiste für das **Eigenschaften** Fenster angezeigt. In allen Fällen werden die Schaltflächen **kategorisiert**, **alphabetisch**, **Eigenschaften und Eigenschaften** **Seiten** angezeigt. In Visual c# und Visual Basic wird auch die Schaltfläche **Ereignisse** angezeigt. In bestimmten Visual C++ Projekten werden die Schaltflächen " **VC + +** " und " **VC Overrides** " angezeigt. Für andere Projekttypen können zusätzliche Schaltflächen angezeigt werden. Weitere Informationen zu Schaltflächen im **Eigenschaften** Fenster finden Sie unter [Eigenschaften Fenster](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementierung von Eigenschaften Fenster Schaltflächen  
 Wenn Sie auf die Schaltfläche **kategorisieren** klicken, ruft Visual Studio die- <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> Schnittstelle für das Objekt auf, das den Fokus besitzt, um die Eigenschaften nach Kategorie zu sortieren <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> wird für das- `IDispatch` Objekt implementiert, das dem **Eigenschaften** Fenster angezeigt wird.  
  
 Es gibt 11 vordefinierte Eigenschaften Kategorien, die negative Werte aufweisen. Sie können benutzerdefinierte Kategorien definieren, aber es wird empfohlen, dass Sie Ihnen positive Werte zuweisen, um Sie von den vordefinierten Kategorien zu unterscheiden.  
  
 Die- <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Methode gibt den entsprechenden Wert der Eigenschafts Kategorie für die angegebene Eigenschaft zurück. Die- <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Methode gibt eine Zeichenfolge zurück, die den Kategorien Amen enthält. Sie müssen nur Unterstützung für benutzerdefinierte Kategoriewerte bereitstellen, da Visual Studio die Standardwerte für die Eigenschaften Kategorie kennt.  
  
 Wenn Sie auf die Schaltfläche " **alphabetisch** " klicken, werden die Eigenschaften in alphabetischer Reihenfolge nach Name angezeigt. Die Namen werden von `IDispatch` gemäß einem lokalisierten Sortieralgorithmus abgerufen.  
  
 Wenn das Fenster **Eigenschaften** geöffnet ist, wird die Schaltfläche **Eigenschaften** automatisch als ausgewählt angezeigt. In anderen Teilen der Umgebung wird dieselbe Schaltfläche angezeigt, und Sie können darauf klicken, um das Fenster **Eigenschaften** anzuzeigen.  
  
 Die Schaltfläche " **Eigenschaften Seiten** " ist nicht verfügbar, wenn `ISpecifyPropertyPages` für das ausgewählte Objekt nicht implementiert ist. Eigenschaften Seiten zeigen Konfigurations abhängige Eigenschaften an, die in der Regel mit Projektmappen und Projekten verknüpft sind. Sie können jedoch auch Projekt Elementen zugeordnet werden (z. b. in Visual C++).  
  
> [!NOTE]
> Mithilfe von nicht verwaltetem Code können Sie dem **Eigenschaften** Fenster keine Symbolleisten-Schaltflächen hinzufügen. Zum Hinzufügen einer Symbolleisten-Schaltfläche müssen Sie ein verwaltetes Objekt erstellen, das von abgeleitet wird <xref:System.Windows.Forms.Design.PropertyTab> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
