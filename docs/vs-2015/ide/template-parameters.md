---
title: Vorlagenparameter | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d7bb7e0f3dfee3dd1bf3e9b42afd5837a29f6ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646804"
---
# <a name="template-parameters"></a>Vorlagenparameter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Indem Sie Parameter in Ihren Vorlagen verwenden, können Sie die Werte von Schlüsselteilen der Vorlage, wie z. B. Klassennamen und Namespaces, bei Instanziierung die Vorlage ersetzen. Diese Parameter werden durch den Vorlagen-Assistenten ersetzt, der im Hintergrund ausgeführt wird, wenn ein Benutzer in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** auf **OK** klickt.

## <a name="declaring-and-enabling-template-parameters"></a>Deklarieren und Aktivieren von Vorlagenparametern
 Vorlagenparameter werden im Format $*parameter*$ deklariert. Beispiel:

- $safeprojectname$

- $guid1$

- $guid5$

#### <a name="to-enable-parameter-substitution-in-templates"></a>So aktivieren Sie die Parameterersetzung in Vorlagen

1. Suchen Sie in der VSTEMPLATE-Datei der Vorlage das `ProjectItem`-Element, das dem Element entspricht, für das Sie die Parameterersetzung aktivieren möchten.

2. Legen Sie das `ReplaceParameters`-Attribut des `ProjectItem`-Elements auf `true` fest.

3. Schließen Sie in der Codedatei für das Projektelement ggf. Parameter ein. Durch den folgenden Parameter wird beispielsweise angegeben, dass der sichere Projektname für den Namespace in einer Datei verwendet werden soll:

    ```
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Reservierte Vorlagenparameter
 In der folgenden Tabelle sind die reservierten Vorlagenparameter aufgelistet, die von beliebigen Vorlagen verwendet werden können.

> [!NOTE]
> Bei Vorlagenparametern wird die Groß-/Kleinschreibung beachtet.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|`clrversion`|Aktuelle Version der Common Language Runtime (CLR).|
|`GUID [1-10]`|Eine GUID zum Ersetzen der Projekt-GUID in einer Projektdatei. Sie können bis zu 10 eindeutige GUIDs (z. B. `guid1)`) angeben.|
|`itemname`|Der vom Benutzer im Dialogfeld **Neues Element hinzufügen** angegebene Name|
|`machinename`|Der aktuelle Computername (z. B. Computer01).|
|`projectname`|Der vom Benutzer im Dialogfeld **Neues Projekt** angegebene Name|
|`registeredorganization`|Der Registrierungsschlüsselwert aus HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|`rootnamespace`|Der Stammnamespace des aktuellen Projekts. Dieser Parameter gilt nur für Elementvorlagen.|
|`safeitemname`|Der vom Benutzer im Dialogfeld **Neues Element hinzufügen** angegebene Name, aus dem alle unsicheren Zeichen sowie Leerzeichen entfernt wurden|
|`safeprojectname`|Der vom Benutzer im Dialogfeld **Neues Projekt** angegebene Name, aus dem alle unsicheren Zeichen sowie Leerzeichen entfernt wurden|
|`time`|Die aktuelle Uhrzeit im Format TT/MM/JJJJ 00:00:00.|
|`SpecificSolutionName`|Der Name der Projektmappe. Wenn "Projektmappenverzeichnis erstellen" aktiviert ist, verfügt `SpecificSolutionName` über den Projektmappennamen. Wenn "Projektmappenverzeichnis erstellen" nicht aktiviert ist, ist `SpecificSolutionName` leer.|
|`userdomain`|Die aktuelle Benutzerdomäne.|
|`username`|Der aktuelle Benutzername.|
|`webnamespace`|Der Name der aktuellen Website. Dieser Parameter wird in der Web Form-Vorlage verwendet und gewährleistet eindeutige Klassennamen. Wenn sich die Website im Stammverzeichnis des Webservers befindet, wird dieser Vorlagenparameter in das Stammverzeichnis des Webservers aufgelöst.|
|`year`|Das aktuelle Jahr im Format JJJJ.|

## <a name="custom-template-parameters"></a>Benutzerdefinierte Vorlagenparameter
 Zusätzlich zu den reservierten Standardvorlagenparametern, die während der Parameterersetzung verwendet werden, können Sie eigene Vorlagenparameter und -werte angeben. Weitere Informationen finden Sie unter [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-replacing-files-names"></a>Beispiel: Ersetzen von Dateinamen
 Sie können variable Dateinamen für Projektelemente festlegen, indem Sie einen Parameter mit dem `TargetFileName`-Attribut verwenden. Beispielsweise können Sie angeben, dass die EXE-Datei den von `$projectname$` angegebenen Projektnamen als Dateinamen verwendet.

```
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-project-name-for-the-namespace-name"></a>Beispiel: Verwenden des Projektnamens für den Namespacenamen
 Um den Projektnamen für den Namespace in einer Visual C#-Klassendatei (Class1.cs) zu übernehmen, verwenden Sie folgende Syntax:

```
#region Using directives

using System;
using System.Collections.Generic;
using System.Text;

#endregion

namespace $safeprojectname$
{
    public class Class1
        {
            public Class1()
                {

                }
         }
}
```

 Schließen Sie in der VSTEMPLATE-Datei für die Projektvorlage den folgenden XML-Code ein, wenn Sie auf die Datei Class1.cs verweisen:

```
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Weitere Informationen
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)
