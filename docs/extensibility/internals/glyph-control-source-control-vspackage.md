---
title: Glyphe-Steuerelement (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie benutzerdefinierte Symbole in einem Quellcodeverwaltungs-VSPackage anzeigen, sodass Sie Ihre eigenen Symbole verwenden können, um den Status von Elementen unter Quell Code Verwaltung anzugeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3ea9300c96cf63c932d88335c0ca0f9fd4542f72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954773"
---
# <a name="glyph-control-source-control-vspackage"></a>Glyphe-Steuerelement (Quellcodeverwaltungs-VSPackage)
Ein Teil der umfassenden Integration, der für Quell Code Verwaltungs-VSPackages verfügbar ist, ist die Möglichkeit, eigene Symbole anzuzeigen, um den Status von Elementen unter Quell Code Verwaltung anzuzeigen.

## <a name="levels-of-glyph-control"></a>Ebenen des Glyphe-Steuer Elements
 Ein Statussymbol ist ein Symbol, das den aktuellen Status eines Elements anzeigt, wenn es angezeigt wird, z. b. in **Projektmappen-Explorer** oder **Klassenansicht**. Ein Quellcodeverwaltungs-VSPackage kann zwei Ebenen des Glyphe-Steuer Elements ausführen. Sie kann die Wahl der Symbole auf einen vordefinierten Satz von Symbolen beschränken, die von der IDE bereitgestellt werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , oder es kann eine benutzerdefinierte Gruppe von Symbolen definiert werden, die angezeigt werden soll.

### <a name="default-set-of-glyphs"></a>Standardsatz von Symbolen
 Um die Statussymbole zu ermitteln, die einem Element in **Projektmappen-Explorer** zugeordnet sind, fordert ein Projekt das Zustands Symbol aus der Quell Code Verwaltung mithilfe von an <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Ein Quellcodeverwaltungs-VSPackage kann entscheiden, dass die Auswahl der Glyphen auf vordefinierte Glyphen beschränkt ist, die von der IDE bereitgestellt werden. In diesem Fall gibt das VSPackage ein Array von Werten zurück, die die in *vsshell. idl* definierten Glyphe-Enumerationen darstellen. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Dies ist ein vordefinierter Satz von Symbolen, die von der IDE festgelegt werden, z. b. ein Vorhängeschloss für das eingecheckte Symbol und ein Häkchen für das ausgecheckte Symbol.

### <a name="custom-set-of-glyphs"></a>Benutzerdefinierter Satz von Symbolen
 Ein Quellcodeverwaltungs-VSPackage kann seine eigenen Symbole für ein eindeutiges Aussehen und Gefühl verwenden, wenn es installiert wird. Wenn ein neues VSPackage für die Quell Code Verwaltung aktiv ist, sollte es in der Lage sein, eigene Symbole zu verwenden, auch wenn ein vorheriges VSPackage für die Quell Code Verwaltung noch geladen, aber inaktiv ist. In diesem Modus kann das VSPackage für die Quell Code Verwaltung die vorhandenen Symbole weiterhin verwenden, um ein Aussehen in Übereinstimmung mit zu behalten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Der <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Dienst unterstützt eine Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> , die das VSPackage optional implementieren kann und die von der IDE angefordert werden. Wenn die IDE eine Anforderung sendet, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht wiederum, diese Schnittstelle aus dem aktuell registrierten VSPackage für die Quell Code Verwaltung zu erhalten. Wenn die Schnittstelle im registrierten VSPackage vorhanden ist, ist die Anforderung der IDE für benutzerdefinierte Symbole erfolgreich. Andernfalls verwendet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ihren Standardsatz von Symbolen.

 Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Methode wird von verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , um eine Liste von Bildern zu erhalten, die verschiedene Quell Code Verwaltungs Zustände anzeigen. Das VSPackage der Quell Code Verwaltung kehrt der IDE ein Handle für die Bildliste für seine benutzerdefinierten Symbole hinzu. Die IDE erstellt an dieser Stelle eine Kopie der Bildliste und verwendet Sie später, um die anzuzeigenden Symbole auszuwählen. Wenn die neue Schnittstelle nicht unterstützt wird oder die `IVsSccGlyphs::GetCustomGlyphList` Methode zurückgibt `E_NOTIMPL` , ruft die IDE die Symbole aus der Standardliste der von bereitgestellten Symbole ab [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
