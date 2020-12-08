---
title: 'Gewusst wie: verwenden Built-In Kolb baren Elementen | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie die integrierten, in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio für Ihren Sprachdienst integrierten Elemente verwenden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 926cb77fe9477b7dc78c35c2ab58f9b73530e4fa
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761009"
---
# <a name="how-to-use-built-in-colorable-items"></a>Gewusst wie: Verwenden integrierter, Färb baren Elemente
Vor der Verwendung der integrierten färb baren Elemente müssen Sie zunächst ein Signal an die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) senden, dass Sie keine eigenen, benutzerdefinierten Elemente bereitstellen, die in diesem Fall <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Objekte sind. Hierzu legen Sie einen Registrierungs Eintrag für den Sprachdienst fest.

## <a name="to-use-built-in-colorable-items"></a>So verwenden Sie integrierte färb Bare Elemente

1. Erstellen Sie unter **HKEY_LOCAL_MACHINE\VisualStudio\\<X. Y> \Languages\Language Services \\<\> sprach Name**, wobei \<X.Y> eine Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und \<Language Name> der Name Ihrer Sprache ist, den DWORD-Registrierungs Eintrags Wert **RequestStockColors**.

2. Legen Sie den Registrierungs Eintrags Wert **RequestStockColors** auf *1* fest.

    Nachdem Sie den Registrierungs Eintrag erstellt haben, kann die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode der Farbgebung die Member der- <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> Enumeration verwenden, um das Array von Farb Attributen auszufüllen, die vom Editor verwendet werden sollen.

   > [!NOTE]
   > Legen Sie diesen Registrierungs Eintrag nicht fest, wenn Sie benutzerdefinierte Elemente bereitstellen. Weitere Informationen finden Sie unter [benutzerdefinierte Kolon-Elemente](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Weitere Informationen
- [Syntax Farbgebung in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntax Farben](../../extensibility/internals/implementing-syntax-coloring.md)
- [Benutzerdefinierte färb Bare Elemente](../../extensibility/internals/custom-colorable-items.md)
- [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service2.md)
