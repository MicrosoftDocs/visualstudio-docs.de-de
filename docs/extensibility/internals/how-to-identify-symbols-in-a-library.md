---
title: 'Gewusst wie: Identifizieren von Symbolen in einer Bibliothek | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie Symbole in einer Bibliothek ermitteln, indem Sie Methoden implementieren, mit denen Navigationsinformationen aus der Symbol Bibliothek an den Visual Studio-Objekt-Manager übergeben werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b1dab9dc6bee4ed987141057194d8b00ff35f99
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761376"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Gewusst wie: Identifizieren von Symbolen in einer Bibliothek
Tools zum Durchsuchen von Symbolen zeigen hierarchische Ansichten von Symbolen an. Die Symbole stellen Namespaces, Objekte, Klassen, Klassenmember und andere Sprachelemente dar.

 Jedes Symbol in der Hierarchie kann durch die Navigationsinformationen identifiziert werden, die von der Symbol Bibliothek an den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager über die folgenden Schnittstellen übermittelt werden:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Der Speicherort des Symbols in der Hierarchie unterscheidet ein Symbol. Mit diesem Tool können Tools zum Durchsuchen von Symbolen zu einem bestimmten Symbol navigieren. Der eindeutige, voll qualifizierte Pfad zum Symbol bestimmt den Speicherort. Jedes Element im Pfad ist ein Knoten. Der Pfad beginnt mit dem Knoten der obersten Ebene und endet mit dem spezifischen Symbol. Wenn die M1-Methode z. b. ein Member der C1-Klasse und C1 im N1-Namespace ist, lautet der vollständige Pfad der M1-Methode N1. C1. M1. Dieser Pfad enthält drei Knoten: N1, C1 und M1.

 Mithilfe der Navigationsinformationen kann der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager die Symbole in der Hierarchie suchen, auswählen und beibehalten. Sie ermöglicht die Navigation von einem Browsertool zu einem anderen. Wenn Sie **Objektkatalog** zum Durchsuchen von Symbolen in einem [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekt verwenden, können Sie mit der rechten Maustaste auf eine Methode klicken und das **Aufrufbrowser** Tool starten, um die Methode in einem Aufruf Diagramm anzuzeigen.

 Zwei Formen beschreiben den Symbol Speicherort. Die kanonische Form basiert auf dem voll qualifizierten Pfad des Symbols. Sie stellt eine eindeutige Position des Symbols in der Hierarchie dar. Es ist unabhängig vom Tool zum Durchsuchen von Symbolen. Zum Abrufen der kanonischen Formularinformationen ruft der Objekt-Manager die- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Methode auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> . Das Präsentations Formular beschreibt den Speicherort des Symbols innerhalb eines bestimmten Tools zum Durchsuchen von Symbolen. Die Position des Symbols ist relativ zur Position von anderen Symbolen in der Hierarchie. Ein bestimmtes Symbol weist möglicherweise mehrere Präsentations Pfade auf, aber nur einen kanonischen Pfad. Wenn z. b. die C1-Klasse von der C2-Klasse geerbt wird und sich beide Klassen im N1-Namespace befinden, zeigt der **Objektkatalog** die folgende hierarchische Struktur an:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Der kanonische Pfad der C2-Klasse, in diesem Beispiel, ist N1 + C2. Der Präsentations Pfad von C2 umfasst die Knoten C1 und "Basen und Schnittstellen": N1 + C1 + "Basen und Schnittstellen" + C2.

 Zum Abrufen der Präsentations Formularinformationen ruft der Objekt-Manager die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> Methode auf.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>So erhalten Sie kanonische und Präsentations Formularinformationen

1. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>-Methode.

     Der Objekt-Manager ruft diese Methode auf, um die Liste der Knoten zu erhalten, die im kanonischen Pfad des Symbols enthalten sind.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>-Methode.

     Der Objekt-Manager ruft diese Methode auf, um die Liste der Knoten zu erhalten, die im Präsentations Pfad des Symbols enthalten sind.

## <a name="see-also"></a>Weitere Informationen
- [Unterstützung von Symbol Suchtools](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Vorgehensweise: Registrieren einer Bibliothek mit dem Objekt-Manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Gewusst wie: verfügbar machen von Listen von Symbolen, die von der Bibliothek für den Objekt-Manager bereitgestellt werden](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
