---
title: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung
description: Erfahren Sie, wie Sie mithilfe des Code Beispiels in dieser exemplarischen Vorgehensweise auf das DTE-Objekt aus einer Editor-Erweiterung zugreifen.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7228165d49c7f11c15d12086933c473699ef6bc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905580"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung

In VSPackages können Sie das DTE-Objekt abrufen, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode mit dem Typ des DTE-Objekts aufrufen. In Managed Extensibility Framework-Erweiterungen (MEF) können Sie <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> die-Methode mit dem Typ importieren und anschließend aufzurufen <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Voraussetzungen

Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>DTE-Objekt

1. Erstellen Sie ein c#-VSIX-Projekt, und nennen Sie es **dtetest**. Fügen Sie eine **Editor-Klassifizierungs** Element Vorlage hinzu, und nennen Sie Sie **dtetest**.

   Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. immutable. 10.0

3. Fügen Sie in der Datei *DTETestProvider.cs* die folgenden- `using` Anweisungen hinzu:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Importieren Sie in der- `DTETestProvider` Klasse <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Fügen Sie in der- `GetClassifier()` Methode den folgenden Code vor der- `return` Anweisung hinzu:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. Fügen Sie in der Datei *DTETestProvider.cs* die folgenden- `using` Anweisungen hinzu:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Importieren Sie in der- `DTETestProvider` Klasse <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Fügen Sie in der- `GetClassifier()` Methode den folgenden Code vor der- `return` Anweisung hinzu:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
- [Starten von Visual Studio mit DTE](launch-visual-studio-dte.md)
