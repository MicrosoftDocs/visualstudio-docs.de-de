---
title: Installieren von FxCop-Analysetools
ms.date: 08/03/2018
description: Erfahren Sie, wie Sie FxCop-Analysen in Visual Studio installieren. Erfahren Sie, wie Sie diese Analysen entweder als nuget-Paket oder als VSIX-Erweiterung installieren.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e9950941680f9e251fe9c589a1df1d0314f149a7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435520"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installieren von FxCop-Analyzern in Visual Studio

Microsoft hat eine Reihe von Analyzern namens [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)erstellt, die die wichtigsten "FxCop"-Regeln aus der Legacy Analyse enthalten. Diese Analysen überprüfen den Code unter anderem auf Sicherheits-, Leistungs-und Entwurfs Probleme.

Sie können diese FxCop-Analysen entweder als nuget-Paket oder als VSIX-Erweiterung für Visual Studio installieren. Weitere Informationen zu den vor-und Nachteile finden Sie unter [nuget-Paket im Vergleich zu VSIX-Erweiterungen](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>NuGet-Paket

::: moniker range=">=vs-2019"

In Visual Studio 2019 Version 16,3 und höher können Sie das nuget-Paket [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) direkt über die Eigenschaften Seite Code Analyse des Projekts installieren:

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, wählen Sie **Eigenschaften** aus, und wählen Sie dann die Registerkarte **Code Analyse** aus.

   ![Paket "FxCop-Analysen" über die Seite "Eigenschaften" in Visual Studio installieren](media/install-fxcop-properties-page.png)

2. Klicken Sie auf **Installieren**.

   Visual Studio installiert die neueste Version des Pakets Microsoft. Code Analysis. fxcopanalyzers. Die Assemblys werden in **Projektmappen-Explorer** unter **Verweise** -  >  **Analyzers** angezeigt.

   ![Analyzers-Knoten in Projektmappen-Explorer](media/solution-explorer-analyzers-node.png)

Wenn Sie eine ältere Version von Visual Studio 2019 verwenden, installieren Sie das Paket entweder über die [Paket-Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder über die [Benutzeroberfläche des Paket-Managers](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. Bestimmen Sie basierend auf Ihrer Version von Visual Studio, [welche Version des Analyzer-Pakets](#fxcopanalyzers-package-versions) installiert werden muss.

2. Installieren Sie das Paket in Visual Studio über die [Paket-Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder die [Benutzeroberfläche des Paket-Managers](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Die Seite "nuget.org" für jedes Analysepaket zeigt den Befehl an, der in die **Paket-Manager-Konsole** eingefügt werden soll. Es gibt sogar eine praktische Schaltfläche, um den Text in die Zwischenablage zu kopieren.
   >
   > ![NuGet.org Seite mit dem Befehl "Paket-Manager-Konsole"](media/nuget-package-manager-command.png)

   Die Analyzer-Assemblys werden installiert und in **Projektmappen-Explorer** unter **Verweise** - > **Analyzers** angezeigt.

::: moniker-end

### <a name="custom-installation"></a>Benutzerdefinierte Installation

Wenn Sie z. b. eine andere Version des Pakets angeben möchten, wählen Sie die Schaltfläche mit den Auslassungs Punkten (...) auf der Eigenschaften Seite Code Analyse des Projekts aus. Diese Schaltfläche öffnet den nuget-Paket-Manager mit "Microsoft. Code Analysis. fxcopanalyzers" als Such Zeichenfolge.

![Installieren des benutzerdefinierten Pakets FxCop Analyzer von der Seite "Eigenschaften" in Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Bestimmen Sie basierend auf Ihrer Version von Visual Studio, [welche Version des Analyzer-Pakets](#fxcopanalyzers-package-versions) installiert werden muss. Sie können das Paket auch über die [Benutzeroberfläche des Paket-Managers](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)installieren.

### <a name="fxcopanalyzers-package-versions"></a>Fxcopanalyzers-Paketversionen

Verwenden Sie die folgenden Richtlinien, um zu bestimmen, welche Version des FxCop-Analysen-Pakets für Ihre Version von Visual Studio installiert werden soll:

| Visual Studio-Version | FxCop Analyzer-Paketversion |
| - | - |
| Visual Studio 2019 (alle Versionen) | [Neueste](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 Version 15.9 | [2.9.10](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.10) |
| Visual Studio 2017, Version 15,5 bis 15,8 | [2.6.4](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.4) |
| Visual Studio 2017, Version 15,3 bis 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017, Version 15,0 bis 15,2 | [2.0.0-Beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 und 3 | [1.2.0-Beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

In Visual Studio 2017, Version 15,5 und höher, können Sie die [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) -Erweiterung installieren, die alle FxCop-Analysen für verwaltete Projekte enthält.

1. **Wählen Sie** in Visual Studio Extras > **Erweiterungen und Updates** aus.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Erweiterung direkt von [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)herunterladen.

2. Erweitern Sie im linken Bereich **Online** , und wählen Sie dann **Visual Studio Marketplace** aus.

3. Geben Sie im Suchfeld "Code Analyse" ein, und suchen Sie nach der Erweiterung **Microsoft Code Analysis 2017** .

   ![Microsoft Code Analysis 2017-Erweiterung](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Die [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) -Erweiterung enthält alle FxCop-Analysen für verwaltete Projekte. So installieren Sie diese Erweiterung:

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten Erweiterungen** aus.

   Das Dialogfeld **Erweiterungen verwalten** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Erweiterung direkt von [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)herunterladen.

2. Erweitern Sie im linken Bereich **Online** , und wählen Sie dann **Visual Studio Marketplace** aus.

3. Geben Sie im Suchfeld "Code Analyse" ein, und suchen Sie nach der Erweiterung **Microsoft Code Analysis 2019** .

   ![Microsoft Code Analysis 2019-Erweiterung](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Wählen Sie **Herunterladen** aus.

   Die Erweiterung wird heruntergeladen.

5. Wählen Sie **OK** aus, um das Dialogfeld zu schließen, und schließen Sie dann alle Instanzen von Visual Studio, um das **VSIX-Installations** Programm zu starten.

   Das Dialogfeld **VSIX-Installer** wird geöffnet.

   ::: moniker range="vs-2017"

   ![VSIX-Installer für die Microsoft-Code Analyse](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Wählen Sie **ändern** aus, um die Installation zu starten.

   Nach einer oder zwei Minuten wird die Installation abgeschlossen.

7. Wählen Sie **Schließen** aus, und öffnen Sie Visual Studio erneut.

::: moniker range="vs-2017"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, **Wählen Sie** Extras  >  **Erweiterungen und Updates** aus. Wählen Sie im Dialogfeld **Erweiterungen und Updates** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, klicken Sie auf **Erweiterungen**  >  **Verwalten Erweiterungen**. Wählen Sie im Dialogfeld **Erweiterungen verwalten** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Übersicht über Code Analysen in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Codeanalysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migration von der Legacy Analyse zu Code Analysen](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
