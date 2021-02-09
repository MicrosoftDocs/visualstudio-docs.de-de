---
title: Installieren von Analysemodulen von Drittanbietern
ms.date: 08/27/2020
description: Erfahren Sie, wie Sie Analysen von Drittanbietern in Visual Studio installieren. Weitere Informationen finden Sie unter Installieren von Analysen in VSIX-Dateien und nuget Analyzer-Paketen.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3d4833ba922ddde1a1770cfd75cf446f210e2c79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859852"
---
# <a name="install-third-party-analyzers"></a>Installieren von Drittanbieteranalysetools

Visual Studio enthält einen Kernsatz von .NET Compiler Platform-Analyzers (*Roslyn*). Diese Analysen sind immer eingeschaltet. Sie können zusätzliche Analysen entweder als nuget-Pakete oder als Visual Studio-Erweiterungen in *VSIX* -Dateien installieren.

## <a name="to-install-nuget-analyzer-packages"></a>So installieren Sie nuget Analyzer-Pakete

1. Suchen Sie das Analyzer-Paket, das Sie installieren möchten, auf www.nuget.org.

   Beispielsweise können Sie [StyleCop. Analyzers](https://www.nuget.org/packages/stylecop.analyzers/) installieren, um nach Stil Problemen in Ihrer Codebasis zu suchen.

2. Installieren Sie das Paket in Visual Studio, indem Sie entweder die [Paket-Manager-Konsole](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) oder die [Benutzeroberfläche des Paket-Managers](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)verwenden.

   > [!NOTE]
   > Die Seite "www.nuget.org" für jedes Analysepaket zeigt den Befehl an, der in die **Paket-Manager-Konsole** eingefügt werden soll. Es gibt sogar eine praktische Schaltfläche, um den Text in die Zwischenablage zu kopieren.

   Die Analyzer-Assemblys werden installiert und in **Projektmappen-Explorer** unter **Verweise**-  >  **Analyzers** angezeigt.

## <a name="to-install-vsix-analyzers"></a>So installieren Sie VSIX-Analysen

::: moniker range="vs-2017"

1. **Wählen Sie** in Visual Studio Extras > **Erweiterungen und Updates** aus.

   Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Analyseprogramm Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com)suchen und herunterladen.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten Erweiterungen** aus.

   Das Dialogfeld **Erweiterungen verwalten** wird geöffnet.

   > [!NOTE]
   > Alternativ können Sie die Analyseprogramm Erweiterung direkt aus [Visual Studio Marketplace](https://marketplace.visualstudio.com)suchen und herunterladen.

::: moniker-end

2. Erweitern Sie im linken Bereich **Online** , und wählen Sie dann **Visual Studio Marketplace** aus.

3. Geben Sie im Suchfeld den Namen der Analyzer-Erweiterung ein, die Sie installieren möchten.

4. Wählen Sie **Herunterladen** aus.

   Die Erweiterung wird heruntergeladen.

5. Wählen Sie **OK** aus, um das Dialogfeld zu schließen, und schließen Sie dann alle Instanzen von Visual Studio, um das **VSIX-Installations** Programm zu starten.

   Das Dialogfeld **VSIX-Installer** wird geöffnet.

   ![VSIX-Installer für die Microsoft-Code Analyse](media/vsix-installer-code-analysis.png)

6. Wählen Sie **ändern** aus, um die Installation zu starten.

7. Nach einer oder zwei Minuten wird die Installation abgeschlossen. Klicken Sie auf **Schließen**.

8. Öffnen Sie Visual Studio erneut.

::: moniker range="vs-2017"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, **Wählen Sie** Extras  >  **Erweiterungen und Updates** aus. Wählen Sie im Dialogfeld **Erweiterungen und Updates** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie überprüfen möchten, ob die Erweiterung installiert ist, klicken Sie auf **Erweiterungen**  >  **Verwalten Erweiterungen**. Wählen Sie im Dialogfeld **Erweiterungen verwalten** auf der linken Seite die Kategorie **installiert** aus, und suchen Sie nach der Erweiterung anhand des Namens.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Verwenden von Codeanalysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über Code Analysen in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Installieren von .NET-Analysetools](../code-quality/install-net-analyzers.md)
