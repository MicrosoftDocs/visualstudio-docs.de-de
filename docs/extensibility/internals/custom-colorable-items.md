---
title: Benutzerdefinierte färb Bare Elemente | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie benutzerdefinierte Elemente als Teil eines sprach Dienstanbieter erstellen, indem Sie die Elemente im Dialogfeld Schriftarten und Farben überschreiben, z. b. Schlüsselwörter und Kommentare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7df029be478fef3cf1e9b6138456986016465d5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903014"
---
# <a name="custom-colorable-items"></a>Benutzerdefinierte färb Bare Elemente
Sie können die Liste der Typen für die Farbgebung (z. b. Schlüsselwörter und Kommentare) überschreiben, indem Sie benutzerdefinierte kolorierbare Elemente als Teil Ihres sprach Dienstanbieter implementieren.

## <a name="user-settings-of-colorable-items"></a>Benutzereinstellungen von Kolb baren Elementen
 Sie können das Dialogfeld **Schriftarten und Farben** anzeigen, indem Sie im **Menü Extras** auf Optionen klicken und dann unter **Umgebung** die **Option** **Schriftarten und Farben** auswählen. Wenn Sie eine Anzeige (z. b. **Text-Editor** oder **Befehlsfenster**) auswählen, werden im Listenfeld **Elemente anzeigen** alle für diese Anzeige aktivierbaren Elemente angezeigt. Sie können Schriftart, Größe, Vordergrundfarbe und Hintergrundfarbe für jedes farbige Element anzeigen und ändern. Ihre Auswahl wird in einem Cache in der Registrierung gespeichert, und der Zugriff erfolgt über den Namen des färb baren Elements.

## <a name="presentation-of-colorable-items"></a>Darstellung von färb baren Elementen
 Da die IDE Benutzer Überschreibungen von kolonier baren Elementen im Dialogfeld **Schriftarten und Farben** verarbeitet, müssen Sie nur jedes benutzerdefinierte Kolon-Element mit einem Namen angeben. Dieser Name wird in der Liste **Elemente anzeigen** angezeigt. Die färb baren Elemente werden in alphabetischer Reihenfolge angezeigt. Wenn Sie die benutzerdefinierten Elemente Ihres sprach Dienstanbieter gruppieren möchten, können Sie jeden Namen mit Ihrem Sprachen Namen (z. b. **NewLanguage-Comment** und **NewLanguage-Keywords**) beginnen.

> [!CAUTION]
> Sie sollten den Namen der Sprache in den Namen des kolamable-Elements einschließen, um Konflikte mit vorhandenen färb baren Elementnamen zu vermeiden. Wenn Sie den Namen eines der färb baren Elemente während der Entwicklung ändern, müssen Sie den Cache zurücksetzen, der beim erstmaligen Zugriff auf die auf die Elemente aktivierbaren Elemente erstellt wurde. Sie können den experimentellen Cache mit dem Tool " **deateexpinstance** " zurücksetzen, das mit dem Visual Studio SDK installiert wird, in der Regel im Verzeichnis:
>
> *C:\Programme (x86) \Microsoft Visual Studio 14,0 \ vssdk\visualstudiointegration\tools\bin*
>
> Um den Cache zurückzusetzen, geben Sie " **/Reset**" ein. Weitere Informationen zu " **kreateexpinstance**" finden Sie unter dem [Hilfsprogramm "kreateexpinstance](../../extensibility/internals/createexpinstance-utility.md)".

 Auf das erste Element in der Liste der färb baren Elemente wird nie verwiesen. Das erste Element entspricht einem kolaktivierbaren Element Index von 0 und stellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] immer die Standardtext Farben und-Attribute für das Element bereit. Der einfachste Weg, dieses Element, auf das nicht verwiesen wird, zu behandeln, besteht darin, in der Liste als erstes Element einen Platzhalter für ein Platzhalter Element bereitzustellen.

## <a name="implement-custom-colorable-items"></a>Implementieren von benutzerdefinierten färb baren Elementen

1. Definieren Sie, was in Ihrer Sprache eingefärbt werden muss, z. b. Schlüsselwort, Operator und Bezeichner.

2. Erstellen Sie eine Enumeration dieser färb baren Elemente.

3. Ordnen Sie die von einem Parser oder Scanner zurückgegebenen Tokentypen den Enumerationswerten zu.

    Beispielsweise können die Werte, die die Tokentypen darstellen, die gleichen Werte in der Enumeration für benutzerdefinierte kolatable-Elemente sein.

4. Füllen Sie in der Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode im- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Objekt die Liste der Attribute mit den Werten aus der Enumeration der benutzerdefinierten Kolon-Elemente aus, die den Tokentypen entsprechen, die vom Parser oder Scanner zurückgegeben werden.

5. Implementieren Sie in derselben Klasse, in der die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle implementiert wird, die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Schnittstelle und ihre zwei Methoden, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>-Schnittstelle.

7. Wenn Sie 24-Bit-oder hohe Farbwerte unterstützen möchten, müssen Sie auch die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle implementieren.

8. Erstellen Sie in Ihrem Sprachdienst Objekt eine Liste, die die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Objekte enthält, eine für jedes kolatable-Element, das von Ihrem Parser oder Scanner identifiziert werden kann.

    Sie können auf jedes Element in der Liste zugreifen, indem Sie den entsprechenden Wert aus der Enumeration benutzerdefinierte Kolon-Elemente verwenden. Verwenden Sie die Enumerationswerte als Index in der Liste. Auf das erste Element in der Liste wird nie zugegriffen, weil es dem Standard Textformat entspricht, das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sich immer selbst behandelt. Sie können dies kompensieren, indem Sie am Anfang der Liste einen Platzhalter für ein Kolon-Element einfügen.

9. Geben Sie in der Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> Methode die Anzahl der Elemente in der Liste der benutzerdefinierten Elemente mit aktivierbaren Elementen zurück.

10. Geben Sie in der Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode das angeforderte kolorierbaren-Element aus der Liste zurück.

    Ein Beispiel für das Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> -Schnittstelle und der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Weitere Informationen
- [Modell eines Legacy sprach Dienstanbieter](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Syntax Farbgebung in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Syntax Farbgebung implementieren](../../extensibility/internals/implementing-syntax-coloring.md)
- [Gewusst wie: Verwenden integrierter, Färb baren Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
