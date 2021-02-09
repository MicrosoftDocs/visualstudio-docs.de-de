---
title: Host mit generiertem Direktivenprozessor verbinden
description: Erfahren Sie, wie Sie den benutzerdefinierten Host erweitern können, sodass er Textvorlagen unterstützt, die direktivenprozessoren aufzurufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: a815718f099b024708b86658e10fc0e85c087b4c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924131"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Exemplarische Vorgehensweise: Verbinden eines Hosts mit einem generierten Direktivenprozessor

Sie können einen eigenen Host schreiben, der Textvorlagen verarbeitet. Ein einfacher benutzerdefinierter Host wird in Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Text Vorlagen Hosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)veranschaulicht. Sie können diesen Host erweitern, um Funktionen hinzuzufügen, z. b. das Erstellen mehrerer Ausgabedateien.

In dieser exemplarischen Vorgehensweise erweitern Sie den benutzerdefinierten Host, sodass er Textvorlagen unterstützt, die direktivenprozessoren aufzurufen. Wenn Sie eine domänenspezifische Sprache definieren, generiert Sie einen *Direktivenprozessor* für das Domänen Modell. Der Direktivenprozessor erleichtert Benutzern das Schreiben von Vorlagen, die auf das Modell zugreifen, wodurch das Schreiben von Assemblys und Import Direktiven in den Vorlagen verringert wird.

> [!NOTE]
> Diese exemplarische Vorgehensweise baut auf Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Text Vorlagen Hosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)auf. Führen Sie diese exemplarische Vorgehensweise zuerst aus.

Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:

- Mithilfe [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] von können Sie einen Direktivenprozessor generieren, der auf einem Domänen Modell basiert.

- Verbinden eines benutzerdefinierten Textvorlagen Hosts mit dem generierten Direktivenprozessor.

- Testen des benutzerdefinierten Hosts mit dem generierten Direktivenprozessor.

## <a name="prerequisites"></a>Voraussetzungen

Zur Definition einer DSL müssen folgende Komponenten installiert sein:

| Komponente | Link |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Außerdem muss die Transformation für benutzerdefinierte Textvorlagen in Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Textvorlagen Hosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)erstellt werden.

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Generieren eines direktivenprozessors mit Domain-Specific-Sprach Tools

In dieser exemplarischen Vorgehensweise verwenden Sie den Domain-Specific-sprach-Designer-Assistenten, um eine domänenspezifische Sprache für die Lösung dslminimaltest zu erstellen.

1. Erstellen Sie eine domänenspezifische Sprachlösung mit folgenden Merkmalen:

   - Name: dslminimaltest

   - Lösungs Vorlage: minimale Sprache

   - Dateierweiterung: min

   - Firmenname: fabrikam

   Weitere Informationen zum Erstellen einer domänenspezifischen Sprachlösung finden Sie unter Vorgehens [Weise: Erstellen einer Domain-Specific-Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

   > [!IMPORTANT]
   > In diesem Schritt wird der Direktivenprozessor generiert und der Schlüssel für ihn in der Registrierung hinzugefügt.

3. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

    Eine zweite Instanz von Visual Studio wird geöffnet.

4. Doppelklicken Sie im experimentellen Build in **Projektmappen-Explorer** auf die Datei **Sample. min**.

    Die Datei wird im Designer geöffnet. Beachten Sie, dass das Modell zwei Elemente, ExampleElement1 und ExampleElement2, und einen Link zwischen Ihnen enthält.

5. Schließen Sie die zweite Instanz von Visual Studio.

6. Speichern Sie die Projekt Mappe, und schließen Sie dann den Domain-Specific-sprach-Designer.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Verbinden eines benutzerdefinierten Text Vorlagen Hosts mit einem Direktivenprozessor

Nachdem Sie den Direktivenprozessor generiert haben, verbinden Sie den Direktivenprozessor und den benutzerdefinierten Textvorlagen Host, den Sie in Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Textvorlagen Hosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)erstellt haben.

1. Öffnen Sie die Projekt Mappe "customhost".

2. Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.

     Das Dialogfeld **Verweis hinzufügen** wird geöffnet, und die Registerkarte **.net** wird angezeigt.

3. Fügen Sie die folgenden Verweise hinzu:

    - Microsoft. VisualStudio. Modeling. SDK. 11.0

    - Microsoft. VisualStudio. Modeling. SDK. Diagramms. 11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft. VisualStudio. TextTemplating. Modeling. 11.0

    - Microsoft. VisualStudio. TextTemplating. vshost. 11.0

4. Fügen Sie am Anfang von Program.cs oder Module1. vb die folgende Codezeile hinzu:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Suchen Sie den Code für die `StandardAssemblyReferences` -Eigenschaft, und ersetzen Sie ihn durch den folgenden Code:

    > [!NOTE]
    > In diesem Schritt fügen Sie Verweise auf die Assemblys hinzu, die vom generierten Direktivenprozessor benötigt werden, der vom Host unterstützt wird.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. Suchen Sie den Code für die Funktion `ResolveDirectiveProcessor` , und ersetzen Sie ihn durch den folgenden Code:

    > [!IMPORTANT]
    > Dieser Code enthält hart codierte Verweise auf den Namen des generierten direktivenprozessors, mit dem Sie eine Verbindung herstellen möchten. Dies kann auf einfache Weise allgemeineres sein. in diesem Fall sucht es nach allen in der Registrierung aufgelisteten direktivenprozessoren und versucht, eine Entsprechung zu finden. In diesem Fall würde der Host mit einem beliebigen generierten Direktivenprozessor funktionieren.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. Klicken Sie im Menü **Datei** auf **Alle speichern**.

8. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Testen des benutzerdefinierten Hosts mit dem Direktivenprozessor

Zum Testen des benutzerdefinierten Textvorlagen Hosts müssen Sie zunächst eine Textvorlage schreiben, die den generierten Direktivenprozessor aufruft. Führen Sie dann den benutzerdefinierten Host aus, übergeben Sie den Namen der Textvorlage, und überprüfen Sie, ob die Direktive ordnungsgemäß verarbeitet wird.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Erstellen einer Textvorlage zum Testen des benutzerdefinierten Hosts

1. Erstellen Sie eine Textdatei, und benennen Sie Sie `TestTemplateWithDP.tt` . Sie können einen beliebigen Text-Editor, z. b. Notepad, verwenden, um die Datei zu erstellen.

2. Fügen Sie folgenden Text in der Textdatei ein:

    > [!NOTE]
    > Die Programmiersprache der Textvorlage muss nicht mit der Programmiersprache des benutzerdefinierten Hosts identisch sein.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. Ersetzen Sie im Code \<YOUR PATH> durch den Pfad der Datei Sample. Min aus der Entwurfs spezifischen Sprache, die Sie im ersten Verfahren erstellt haben.

4. Speichern und schließen Sie die Datei.

### <a name="test-the-custom-host"></a>Testen des benutzerdefinierten Hosts

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Geben Sie den Pfad der ausführbaren Datei für den benutzerdefinierten Host ein, drücken Sie aber noch nicht die EINGABETASTE.

     Beispiel:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Anstatt die Adresse einzugeben, können Sie in **Windows-Explorer** zu der Datei CustomHost.exe navigieren und die Datei dann in das Eingabe Aufforderungs Fenster ziehen.

3. Geben Sie ein Leerzeichen ein.

4. Geben Sie den Pfad der Textvorlagendatei ein, und drücken Sie dann die EINGABETASTE.

     Beispiel:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Anstatt die Adresse einzugeben, können Sie in **Windows-Explorer** zu der Datei TestTemplateWithDP.txt navigieren und die Datei dann in das Eingabe Aufforderungs Fenster ziehen.

     Die Anwendung für benutzerdefinierte Hosts wird ausgeführt, und der Textvorlagen-Transformationsprozess wird gestartet.

5. Navigieren Sie in **Windows-Explorer** zu dem Ordner, der die Datei TestTemplateWithDP.txt enthält.

     Der Ordner enthält auch die Datei TestTemplateWithDP1.txt.

6. Öffnen Sie diese Datei, um die Ergebnisse der Textvorlagentransformation anzuzeigen.

     Die Ergebnisse der generierten Textausgabe werden angezeigt und sollten wie folgt aussehen:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)
