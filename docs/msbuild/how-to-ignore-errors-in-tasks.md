---
title: 'Vorgehensweise: Ignorieren von Fehlern in Aufgaben | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie Fehler in MSBuild-Aufgaben ignorieren und steuern, ob ein Build bei einem Fehler in einer Aufgabe angehalten oder fortgesetzt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: f2c0b070868b8dc9fc10c4f493fbb75948485a5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914251"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Vorgehensweise: Ignorieren von Fehlern in Aufgaben

Manchmal benötigen Sie ein Build, der in bestimmten Aufgaben fehlertolerant ist. Wenn diese nicht kritischen Aufgaben fehlschlagen, soll der Buildvorgang fortgesetzt werden, da er immer noch die gewünschte Ausgabe erzeugen kann. Wenn z.B. ein Projekt eine Aufgabe `SendMail` zum Senden einer E-Mail-Nachricht verwendet, nachdem jede Komponente erzeugt wurde, sollte der Build bis zum Abschluss weiterarbeiten, selbst wenn der Mailserver nicht verfügbar ist und die Statusnachricht nicht gesendet werden kann. Oder wenn beispielsweise temporäre Dateien während des Buildvorgangs normalerweise gelöscht werden, sollte der Build auch bis zum Abschluss weiterarbeiten, selbst wenn diese Dateien nicht gelöscht werden können.

## <a name="use-the-continueonerror-attribute"></a>Verwenden des ContinueOnError-Attributs

Das Attribut `ContinueOnError` des Elements `Task` steuert, ob ein Build beendet oder fortgesetzt wird, wenn eine Aufgabe fehlschlägt. Dieses Attribut steuert auch, ob Fehler als Fehler oder Warnungen behandelt werden, wenn der Buildvorgang fortgesetzt wird.

Das Attribut `ContinueOnError` kann einen oder mehrere der folgenden Werte enthalten:

- **WarnAndContinue** oder **TRUE**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.

- **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.

- **ErrorAndStop** oder **FALSE** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.

Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.

Der Standardwert von `ContinueOnError` ist `ErrorAndStop`. Wenn Sie das Attribut auf `ErrorAndStop` festlegen, machen Sie das Verhalten für jeden explizit, der die Projektdatei lesen kann.

#### <a name="to-ignore-an-error-in-a-task"></a>So ignorieren Sie Fehler in einer Aufgabe

Verwenden Sie das Attribut `ContinueOnError` der Aufgabe. Zum Beispiel:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird veranschaulicht, dass das `Build`-Ziel weiter ausgeführt wird und der Build als erfolgreich betrachtet wird, selbst wenn die Aufgabe `Delete` fehlschlägt.

```xml
<Project DefaultTargets="FakeBuild"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Files Include="*.obj"/>
    </ItemGroup>
    <Target Name="Clean">
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
    </Target>

    <Target Name="FakeBuild" DependsOnTargets="Clean">
        <Message Text="Building after cleaning..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [MSBuild](../msbuild/msbuild.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)
