---
title: Buildprozesse für Dateien
description: Hier erfahren Sie, dass alle Dateien in einem Visual Studio-Projekt eine Buildaktion aufweisen, die steuert, was bei einer Kompilierung des Projekts mit der Datei passiert.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8884eaa459fa3a2a7dd8d10f0ffeca5003398afd
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136731"
---
# <a name="build-actions"></a>Buildvorgänge

Sämtliche Dateien in einem Projekt von Visual Studio verfügen über einen Buildprozess. Durch den Buildprozess wird kontrolliert, was mit der Datei passiert, wenn das Projekt erstellt ist.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Buildprozesse in Visual Studio für Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Festlegen eines Buildprozesses

Öffnen Sie die Eigenschaften der Datei im Fenster **Eigenschaften** durch Auswahl der Datei im **Projektmappen-Explorer** , und drücken Sie **Alt**+**Eingabe** , um den Buildprozess für eine Datei festzulegen. Oder klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei, und wählen Sie **Eigenschaften** . Verwenden Sie im Fenster **Eigenschaften** unter **Erweitert** die Dropdownliste neben **Buildprozess** , um einen Buildprozess für die Datei festzulegen.

![Buildprozesse für eine Datei in Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Buildprozesswerte

Einige der gängigeren Buildprozesse für C# und Visual Basic-Projektdateien sind die folgenden:

|Buildvorgang | Projekttypen | BESCHREIBUNG |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | Eine Textdatei, die keine Quelldatei ist, die an den C#- oder Visual Basic-Compiler als Eingabe übergeben wird. Dieser Buildprozess wird hauptsächlich zum Bereitstellen von Eingaben für [Analysetools](../code-quality/roslyn-analyzers-overview.md) verwendet, auf die ein Projekt verweist, um die Codequalität zu überprüfen. Weitere Informationen finden Sie in der GitHub-Übersicht zum [Verwenden zusätzlicher Dateien](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **ApplicationDefinition** | WPF | Die Datei, die Ihre Anwendung definiert. Wenn Sie ein Projekt erstmalig erstellen, ist dies *App.XAML* . |
| **CodeAnalysisDictionary** | .NET | Ein benutzerdefiniertes Wörterbuch, das von der Codeanalyse für die Rechtschreibprüfung verwendet wird. Weitere Informationen finden Sie unter [How to: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Compile** | any | Die Datei wird an den Compiler als Quelldatei übergeben.|
| **Inhalt** | .NET | Eine Datei, die als **Content** markiert ist, kann als Stream abgerufen werden, indem Sie <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> aufrufen. Bei ASP.NET-Projekten werden diese Dateien bei der Bereitstellung als Teil der Website integriert.|
| **DesignData** | WPF | Wird für XAML-ViewModel-Dateien verwendet, um die Anzeige von Benutzersteuerelementen zur Entwurfszeit mit Dummytypen und Beispieldaten zu ermöglichen. |
| **DesignDataWithDesignTimeCreateable** | WPF | Wie **bei DesignData** , aber mit tatsächlichen Typen.  |
| **Embedded Resource** | .NET | Die Datei wird an den Compiler als Ressource übergeben, die in die Assembly eingebettet wird. Rufen Sie <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> zum Lesen der Datei aus der Assembly auf.|
| **EntityDeploy** | .NET | EDMX-Dateien von ‚Entity Framework (EF), die die Bereitstellung von EF-Artefakten angeben. |
| **Fakes** | .NET | Wird für das Microsoft Fakes-Testframework verwendet. Weitere Informationen finden Sie unter [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **None** | any | Die Datei ist in keiner Weise Teil des Builds. Dieser Wert kann für Dokumentationsdateien wie Infodateien verwendet werden.|
| **Seite** | WPF | Kompilieren Sie eine XAML-Datei in eine binäre BAML-Datei zum schnelleren Laden zur Laufzeit. |
| **Ressource** | WPF | Gibt an, dass die Datei in eine Ressourcendatei des Assemblymanifests mit der Erweiterung *.g.resources* eingebettet wird. |
| **Shadow** | .NET | Wird für eine Accessordatei verwendet, die eine Liste der erstellten Assemblydateinamen enthält (eine pro Zeile). Generieren Sie für jede Assembly in der Liste öffentliche Klassen mit den Namen `ClassName_Accessor`, die den Originalen entsprechen, aber mit öffentlichen Methoden anstelle von privaten Methoden. Wir für Komponententests verwendet. |
| **Begrüßungsbildschirm** | WPF | Gibt eine Bilddatei an, die zur Laufzeit angezeigt werden soll, wenn die App gestartet wird. |
| **XamlAppDef** | Windows Workflow Foundation | Weist den Build an, eine Workflow-XAML-Datei in eine Assembly mit einem eingebetteten Workflow zu erstellen. |

> [!NOTE]
> Zusätzliche Buildaktionen können für bestimmte Projekttypen definiert werden, sodass die Liste der Buildaktionen vom Projekttyp abhängt und Werte angezeigt werden können, die nicht in dieser Liste enthalten sind.

## <a name="see-also"></a>Siehe auch

- [C#-Compileroptionen](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic-Compileroptionen](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Buildprozesse (Visual Studio für Mac)](/visualstudio/mac/build-actions)
