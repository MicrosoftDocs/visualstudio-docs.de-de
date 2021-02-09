---
title: 'Neue Projektgenerierung: Teil 2 | Microsoft-Dokumentation'
description: Sehen Sie sich an, was in der integrierten Entwicklungsumgebung (IDE) von Visual Studio passiert, wenn Sie einen eigenen Projekttyp erstellen (Teil 2 von 2).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7891cb6a40e6b7de48ba11871688881625b9c68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895608"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Neue Projektgenerierung: Einblick in die Hintergründe, Teil 2

In [der neuen Projektgenerierung: im Teil der Hintergrundseite](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) haben wir gesehen, wie das Dialogfeld " **Neues Projekt** " ausgefüllt wird. Angenommen, Sie haben eine **Visual c#-Windows-Anwendung** ausgewählt, die Textfelder **Name** und **Speicherort** ausgefüllt und auf OK geklickt.

## <a name="generating-the-solution-files"></a>Erstellen der Projektmappendateien
 Die Auswahl einer Anwendungs Vorlage bewirkt, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die entsprechende VSTEMPLATE-Datei entzippt und geöffnet wird und eine Vorlage zum Interpretieren der XML-Befehle in dieser Datei gestartet wird. Diese Befehle erstellen Projekte und Projekt Elemente in der neuen oder vorhandenen Projekt Mappe.

 Die Vorlage entpackt Quelldateien, die als Element Vorlagen bezeichnet werden, aus demselben ZIP-Ordner, der die VSTEMPLATE-Datei enthält. Die Vorlage kopiert diese Dateien in das neue Projekt und passt Sie entsprechend an.

### <a name="template-parameter-replacement"></a>Vorlagen Parameter Ersetzung
 Wenn die Vorlage eine Element Vorlage in ein neues Projekt kopiert, ersetzt Sie alle Vorlagen Parameter durch Zeichen folgen, um die Datei anzupassen. Ein Vorlagen Parameter ist ein spezielles Token, dem ein Dollarzeichen vorangestellt und gefolgt wird, z. b. $Date $.

 Betrachten wir nun eine typische Projekt Element Vorlage. Extrahieren und untersuchen Sie Program.cs im Ordner "Programme\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip".

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

Wenn Sie ein neues Windows-Anwendungsprojekt mit dem Namen Simple erstellen, ersetzt die Vorlage den- `$safeprojectname$` Parameter durch den Namen des Projekts.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Eine umfassende Liste der Vorlagen Parameter finden Sie unter [Vorlagen Parameter](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Ein-Blick innerhalb eines. VSTEMPLATE-Datei
 Eine einfache VSTEMPLATE-Datei hat dieses Format.

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Wir haben uns den \<TemplateData> Abschnitt in der [neuen Projektgenerierung: unter der Haube, Teil 1,](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)angesehen. Mithilfe der Tags in diesem Abschnitt wird das Erscheinungsbild des Dialog Felds **Neues Projekt** gesteuert.

 Die Tags im- \<TemplateContent> Abschnitt steuern die Generierung neuer Projekte und Projekt Elemente. Im folgenden finden Sie den \<TemplateContent> Abschnitt der Datei "cswindowsapplication. vstemplate" im Ordner "\Programme\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip".

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 Das \<Project> -Tag steuert die Generierung eines Projekts, und das- \<ProjectItem> Tag steuert die Generierung eines Projekt Elements. Wenn der Parameter "ReplaceParameters" den Wert "true" hat, werden alle Vorlagen Parameter in der Projektdatei oder im Element von der Vorlage angepasst. In diesem Fall werden alle Projekt Elemente mit Ausnahme von Settings. Settings angepasst.

 Der TargetFileName-Parameter gibt den Namen und den relativen Pfad der resultierenden Projektdatei oder des resultierenden Elements an. Auf diese Weise können Sie eine Ordnerstruktur für das Projekt erstellen. Wenn Sie dieses Argument nicht angeben, hat das Projekt Element denselben Namen wie die Projekt Element Vorlage.

 Die resultierende Windows-Anwendungsordner Struktur sieht wie folgt aus:

 ![Screenshot der Windows-Anwendungsordner Struktur für die "Simple"-Lösung in Visual Studio Projektmappen-Explorer.](../../extensibility/internals/media/simplesolution.png)

 Das erste und einzige \<Project> Tag in der Vorlage lautet:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Dadurch wird die neue Projektvorlage angewiesen, die einfache csproj-Projektdatei zu erstellen, indem das Vorlagen Element WindowsApplication. csproj kopiert und angepasst wird.

### <a name="designers-and-references"></a>Designer und Verweise
 Sie können in der Projektmappen-Explorer sehen, dass der Ordnereigenschaften vorhanden ist und die erwarteten Dateien enthält. Aber wie sieht es mit Projekt verweisen und Designer-Datei Abhängigkeiten aus, z. b. resources.Designer.cs to Resources. resx und Form1.Designer.cs zu Form1.cs?  Diese werden in der Simple. CSPROJ-Datei eingerichtet, wenn Sie generiert wird.

 Hier ist der \<ItemGroup> von Simple. csproj, der die Projekt Verweise erstellt:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Sie sehen, dass es sich hierbei um sechs Projekt Verweise handelt, die in der Projektmappen-Explorer angezeigt werden. Hier ist ein Abschnitt von einem anderen \<ItemGroup> . Viele Codezeilen wurden aus Gründen der Übersichtlichkeit gelöscht. In diesem Abschnitt ist Settings.Designer.cs abhängig von Einstellungen. Settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Weitere Informationen

- [Neue Projektgenerierung: Einblick in die Hintergründe, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
