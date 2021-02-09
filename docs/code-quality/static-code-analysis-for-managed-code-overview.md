---
title: Legacy Analyse für verwalteten Code
ms.date: 06/12/2019
description: Erfahren Sie mehr über die Legacy Analyse in Visual Studio. Erfahren Sie, wie Sie Warnungen unterdrücken und Analysen manuell, automatisch und während der Eincheck Vorgänge und Builds ausführen.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e8d9ddf88086772e0cd21bde856184954bc7143b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867684"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Übersicht über die Legacy-Analyse für verwalteten Code in Visual Studio

Visual Studio kann eine Code Analyse von verwaltetem Code auf zweierlei Weise durchführen: mit [Legacy Analyse](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), auch als "FxCop Static Analysis of Managed Assemblys" bezeichnet, und mit den moderneren .NET Compiler Platform basierten [Code](../code-quality/roslyn-analyzers-overview.md)Analysemodulen. In diesem Thema wird die Legacy Analyse behandelt. Weitere Informationen zur .NET Compiler Platform basierten Code Analyse finden Sie unter [Übersicht über .NET Compiler Platform-basierte Analysen](../code-quality/roslyn-analyzers-overview.md).

Die Code Analyse für verwalteten Code analysiert verwaltete Assemblys und meldet Informationen über die Assemblys, z. b. Verstöße gegen die Programmier-und Entwurfs Regeln, die in den [.net-Entwurfs Richtlinien](/dotnet/standard/design-guidelines/)festgelegt sind

Das Analysetool stellt die während einer Analyse durchgeführten Prüfungen als Warnmeldungen dar. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

> [!NOTE]
> Die Legacy Analyse (statische Code Analyse) wird für .net Core-und .NET Standard-Projekte in Visual Studio nicht unterstützt. Wenn Sie die Code Analyse in einem .net Core-oder .NET Standard Projekt als Teil von MSBuild ausführen, wird eine Fehlermeldung ähnlich der folgenden angezeigt **: CA0055: die \<your.dll> Plattform konnte nicht identifiziert** werden. Verwenden Sie stattdessen [Code Analysen](../code-quality/roslyn-analyzers-overview.md) , um Code in .net Core-oder .NET Standard Projekten zu analysieren.

## <a name="ide-integrated-development-environment-integration"></a>Integration der IDE (integrierte Entwicklungsumgebung)

Sie können die Code Analyse für Ihr Projekt manuell oder automatisch ausführen.

Wenn Sie die Code Analyse bei jedem Erstellen eines Projekts ausführen möchten, wählen Sie die Option auf der Eigenschaften Seite **Code Analyse** des Projekts aus. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der automatischen Code Analyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Um die Code Analyse für ein Projekt manuell auszuführen, wählen Sie in der Menüleiste **Analyse**  >  **Ausführen Code Analyse**  >  **Ausführen Code \<project> Analyse für** aus.

## <a name="rule-sets"></a>Regelsätze

Codeanalyseregeln für verwalteten Code werden in [Regelsätze](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) gruppiert. Sie können einen der Standardregel Sätze von Microsoft verwenden, oder Sie können [einen benutzerdefinierten Regelsatz erstellen](../code-quality/how-to-create-a-custom-rule-set.md) , um einen bestimmten Bedarf zu erfüllen.

## <a name="suppress-warnings"></a>Unterdrücken von Warnungen

Es kann häufig hilfreich sein anzugeben, dass eine Warnung nicht zutreffend ist. Entwickler und andere Personen, die später möglicherweise den Code überprüfen, wissen dann, dass eine Warnung untersucht und unterdrückt oder ignoriert wurde.

Die Quell Unterdrückung von Warnungen wird durch benutzerdefinierte Attribute implementiert. Fügen Sie zum Unterdrücken einer Warnung das Attribut `SuppressMessage` zum Quellcode hinzu, wie im folgenden Beispiel dargestellt:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Weitere Informationen finden Sie unter [Unterdrücken von Warnungen](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> Wenn Sie ein Projekt zu Visual Studio 2017 migrieren, kann es vorkommen, dass Sie mit einer großen Anzahl von Code Analyse Warnungen konfrontiert werden. Wenn Sie die Warnungen nicht beheben können, können Sie alle unterdrücken, indem Sie **analysieren**  >  **Code Analyse ausführen und aktive Probleme unterdrücken** auswählen.
>
> ![Ausführen der Code Analyse und unterdrücken von Problemen in Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Wenn Sie ein Projekt zu Visual Studio 2019 migrieren, kann es vorkommen, dass Sie mit einer großen Anzahl von Code Analyse Warnungen konfrontiert werden. Wenn Sie die Warnungen nicht beheben können, können Sie alle unterdrücken, indem Sie die Option Build **analysieren**  >  **und aktive Probleme unterdrücken** auswählen.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ausführen der Codeanalyse im Rahmen der Eincheckrichtlinien

In einer Organisation ist es sinnvoll festzulegen, dass beim Einchecken stets bestimmte Richtlinien beachtet werden müssen. Insbesondere die folgenden Richtlinien sollten eingehalten werden:

- Beim Einchecken von Code sind keine Buildfehler vorhanden.

- Die Code Analyse wird als Teil des letzten Builds ausgeführt.

Die Einhaltung dieser Vorgaben können Sie durch das Definieren von Eincheckrichtlinien gewährleisten. Weitere Informationen finden Sie unter [verbessern der Code Qualität mit Project Check-in-Richtlinien](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-Integration

Sie können die integrierten Features des Buildsystems verwenden, um das Analysetool im Rahmen des Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über .NET Compiler Platform-basierte Analysetools](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
