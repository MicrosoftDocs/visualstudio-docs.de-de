---
title: 'Vorgehensweise: Ignorieren von Fehlern in Aufgaben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5025cc3e9dc0e13c3ae4658d129f5d0ac94f6fd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156594"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Gewusst wie: Ignorieren von Fehlern in Aufgaben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manchmal benötigen Sie ein Build, der in bestimmten Aufgaben fehlertolerant ist. Wenn diese nicht kritischen Aufgaben fehlschlagen, soll der Buildvorgang fortgesetzt werden, da er immer noch die gewünschte Ausgabe erzeugen kann. Wenn z.B. ein Projekt eine Aufgabe `SendMail` zum Senden einer E-Mail-Nachricht verwendet, nachdem jede Komponente erzeugt wurde, sollte der Build bis zum Abschluss weiterarbeiten, selbst wenn der Mailserver nicht verfügbar ist und die Statusnachricht nicht gesendet werden kann. Oder wenn beispielsweise temporäre Dateien während des Buildvorgangs normalerweise gelöscht werden, sollte der Build auch bis zum Abschluss weiterarbeiten, selbst wenn diese Dateien nicht gelöscht werden können.  
  
## <a name="using-the-continueonerror-attribute"></a>Verwenden des ContinueOnError-Attributs  
 Das Attribut `ContinueOnError` des Elements `Task` steuert, ob ein Build beendet oder fortgesetzt wird, wenn eine Aufgabe fehlschlägt. Dieses Attribut steuert auch, ob Fehler als Fehler oder Warnungen behandelt werden, wenn der Buildvorgang fortgesetzt wird.  
  
 Das Attribut `ContinueOnError` kann einen oder mehrere der folgenden Werte enthalten:  
  
- **WarnAndContinue** oder **TRUE**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.  
  
- **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.  
  
- **ErrorAndStop** oder **FALSE** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.  
  
  Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.  
  
  Der Standardwert von `ContinueOnError` ist `ErrorAndStop`. Wenn Sie das Attribut auf `ErrorAndStop` festlegen, machen Sie das Verhalten für jeden explizit, der die Projektdatei lesen kann.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>So ignorieren Sie Fehler in einer Aufgabe  
  
- Verwenden Sie das Attribut `ContinueOnError` der Aufgabe. Beispiel:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, dass das `Build`-Ziel weiter ausgeführt wird und der Build als erfolgreich betrachtet wird, selbst wenn die Aufgabe `Delete` fehlschlägt.  
  
```  
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
[MSBuild](msbuild.md)  
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
