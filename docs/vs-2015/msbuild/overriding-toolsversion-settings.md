---
title: Überschreiben von ToolsVersion-Einstellungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 468561a627a3ad7eb477328b5afef794c7acf2c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199944"
---
# <a name="overriding-toolsversion-settings"></a>Überschreiben von ToolsVersion-Einstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das Toolset für Projekte und Projektmappen auf drei verschiedene Arten ändern:  
  
1. durch Verwendung des `/ToolsVersion`-Schalters (oder kurz `/tv`) beim Erstellen des Projekts oder der Projektmappe in der Befehlszeile  
  
2. durch Verwendung des `ToolsVersion`-Parameters in der MSBuild-Aufgabe  
  
3. durch Festlegen der `$(ProjectToolsVersion)`-Eigenschaft für ein Projekt in einer Projektmappe. So können Sie ein Projekt in einer Projektmappe mit einer anderen Toolsetversion erstellen als der, die in anderen Projekten verwendet wird.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Überschreiben der ToolsVersion-Einstellungen von Projekten und Projektmappen in Befehlszeilenbuilds  
 Obwohl Visual Studio-Projekte normalerweise mit der in der Projektdatei angegebenen ToolsVersion erstellt werden, können Sie den Schalter `/ToolsVersion` (oder `/tv`) in der Befehlszeile verwenden, um diesen Wert zu überschreiben und so alle Projekte und deren projektübergreifende Abhängigkeiten mit einem anderen Toolset zu erstellen. Beispiel:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 In diesem Beispiel werden alle Projekte mit ToolsVersion 12.0 erstellt. (Siehe jedoch auch den Abschnitt "Rangfolge" weiter unten in diesem Thema.)  
  
 Bei Verwendung des `/tv`-Schalters in der Befehlszeile können Sie optional die `$(ProjectToolsVersion)`-Eigenschaft für einzelne Projekte verwenden, um diese mit einem anderen ToolsVersion-Wert als für andere Projekte in der Projektmappe zu erstellen.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Überschreiben der ToolsVersion-Einstellung mit dem ToolsVersion-Parameter der MSBuild-Aufgabe  
 Die MSBuild-Aufgabe dient einem Projekt primär dazu, ein anderes Projekt zu erstellen. Damit die MSBuild-Aufgabe ein Projekt mit einer anderen ToolsVersion als der im Projekt angegebenen erstellen kann, stellt sie einen optionalen Aufgabenparameter mit dem Namen `ToolsVersion` zur Verfügung. Im folgenden Beispiel wird die Verwendung dieses Parameters veranschaulicht:  
  
1. Erstellen Sie eine Datei namens `projectA.proj`, die den folgenden Code enthält:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2. Erstellen Sie eine andere Datei mit dem Namen `projectB.proj`, die den folgenden Code enthält:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3. Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4. Die folgende Ausgabe wird angezeigt. Bei `projectA` überschreibt die `/toolsversion:3.5`-Einstellung in der Befehlszeile die `ToolsVersion=12.0`-Einstellung im `Project`-Tag.  
  
     `ProjectB` wird durch eine Aufgabe in `projectA` aufgerufen. Diese Aufgabe enthält die `ToolsVersion=2.0`, die die anderen `ToolsVersion`-Einstellungen für `projectB` überschreibt.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Rangfolge  
 Die Rangfolge, vom Höchsten zum Niedrigsten, mit der `ToolsVersion` bestimmt wird, ist:  
  
1. Das `ToolsVersion`-Attribut in der MSBuild-Aufgabe, die zum Erstellen des Projekts verwendet wird (soweit zutreffend).  
  
2. Der Schalter `/toolsversion` (oder `/tv`), der im msbuild.exe-Befehl verwendet wird, falls vorhanden.  
  
3. Wenn die Umgebungsvariable `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` festgelegt ist, verwenden Sie die aktuelle `ToolsVersion`.  
  
4. Wenn die Umgebungsvariable `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` festgelegt ist und die in der Projektdatei definierte `ToolsVersion` größer als die aktuelle `ToolsVersion` ist, verwenden Sie die aktuelle `ToolsVersion`.  
  
5. Wenn die Umgebungsvariable `MSBUILDLEGACYDEFAULTTOOLSVERSION` festgelegt ist oder wenn `ToolsVersion` nicht festgelegt ist, werden die folgenden Schritte verwendet:  
  
    1. Das Attribut `ToolsVersion` des [Project](../msbuild/project-element-msbuild.md)-Elements der Projektdatei. Wenn dieses Attribut nicht vorhanden ist, wird angenommen, dass es sich um die aktuelle Version handelt.  
  
    2. Die standardmäßige Toolsversion in der MSBuild.exe.config-Datei.  
  
    3. Die standardmäßige Toolsversion in der Registrierung. Weitere Informationen finden Sie unter [Standard mäßige und benutzerdefinierte Toolsetkonfigurationen](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6. Wenn die Umgebungsvariable `MSBUILDLEGACYDEFAULTTOOLSVERSION` nicht festgelegt ist, werden die folgenden Schritte verwendet:  
  
    1. Wenn die Umgebungsvariable `MSBUILDDEFAULTTOOLSVERSION` auf eine vorhandene `ToolsVersion` festgelegt ist, verwenden Sie diese Version.  
  
    2. Wenn `DefaultOverrideToolsVersion` in MSBuild.exe.config festgelegt ist, verwenden Sie diese Version.  
  
    3. Wenn `DefaultOverrideToolsVersion` in der Registrierung festgelegt ist, verwenden Sie diese Version.  
  
    4. Andernfalls verwenden Sie die aktuelle `ToolsVersion`.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ziel Versionen festlegen](../msbuild/msbuild-multitargeting-overview.md)   
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)   
 [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Standard mäßige und benutzerdefinierte Toolsetkonfigurationen](../msbuild/standard-and-custom-toolset-configurations.md)
