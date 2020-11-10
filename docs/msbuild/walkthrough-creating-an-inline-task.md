---
title: 'Exemplarische Vorgehensweise: Erstellen einer Inlineaufgabe | Microsoft-Dokumentation'
description: Exemplarische Vorgehensweise zum Erstellen einer MSBuild-Inlineaufgabe in der Projektdatei ohne Notwendigkeit zum Erstellen einer separaten Assembly zum Hosten der Aufgabe
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2d72745aebedb5dad5efc86d33804a51e36b762
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046632"
---
# <a name="walkthrough-create-an-inline-task"></a>Exemplarische Vorgehensweise: Erstellen eines Inlinetasks

MSBuild-Aufgaben werden in der Regel durch Kompilieren einer Klasse erstellt, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert. Ab .NET Framework Version 4 können Sie Aufgaben inline in der Projektdatei erstellen. Zum Hosten der Aufgabe müssen Sie keine separate Assembly erstellen. Weitere Informationen hierzu finden Sie unter [Inlineaufgaben](../msbuild/msbuild-inline-tasks.md).

 In dieser exemplarischen Vorgehensweise wird das Erstellen und Ausführen der folgenden Inlineaufgaben erläutert:

- Eine Aufgabe, die über keine Eingabe- oder Ausgabeparameter verfügt.

- Eine Aufgabe, die über einen Eingabeparameter und keine Ausgabeparameter verfügt.

- Eine Aufgabe, die über zwei Eingabeparameter und einen Ausgabeparameter verfügt, der eine MSBuild-Eigenschaft zurückgibt.

- Eine Aufgabe, die über zwei Eingabeparameter und einen Ausgabeparameter verfügt, der ein MSBuild-Element zurückgibt.

Verwenden Sie zum Erstellen und Ausführen der Aufgaben Visual Studio und das **Eingabeaufforderungsfenster von Visual Studio** wie folgt:

1. Erstellen Sie in Visual Studio eine MSBuild-Projektdatei.

2. Ändern Sie die Projektdatei in Visual Studio, um die Inlineaufgabe zu erstellen.

3. Erstellen Sie im **Eingabeaufforderungsfenster** das Projekt und untersuchen Sie die Ergebnisse.

## <a name="create-and-modify-an-msbuild-project"></a>Erstellen und Ändern eines MSBuild-Projekts

 Das Visual Studio-Projektsystem beruht auf MSBuild. Daher können Sie in Visual Studio eine Buildprojektdatei erstellen. In diesem Abschnitt erstellen Sie eine Visual C#-Projektdatei. (Stattdessen können Sie auch eine Visual Basic-Projektdatei erstellen. Im Kontext dieses Tutorials ist der Unterschied zwischen den zwei Projektdateien marginal.)

#### <a name="to-create-and-modify-a-project-file"></a>So erstellen und ändern Sie eine Projektdatei

1. Erstellen Sie in Visual Studio ein neues Projekt mit der **Windows Forms-Anwendungsvorlage** für C#. Geben Sie im Feld **Name**`InlineTasks`ein. Geben Sie einen **Speicherort** für die Projektmappe ein, z.B. *D:\\* . Stellen Sie sicher, dass die Option **Projektmappenverzeichnis erstellen** aktiviert wurde, die Option **Zur Quellcodeverwaltung hinzufügen** deaktiviert wurde und der **Projektmappenname** **InlineTasks** lautet.

3. Klicken Sie auf **OK** , um die neue Projektdatei zu erstellen.

3. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den **InlineTasks** -Projektknoten und anschließend auf **Projekt entladen**.

4. Klicken Sie erneut mit der rechten Maustaste auf den Projektknoten und anschließend auf **InlineTasks.csproj bearbeiten**.

     Die Projektdatei wird im Code-Editor angezeigt.

## <a name="add-a-basic-hello-task"></a>Hinzufügen einer einfachen „Hallo“-Aufgabe

 Fügen Sie der Projektdatei nun eine einfache Aufgabe hinzu, die die Nachricht „Hallo Welt“ anzeigt Fügen Sie des Weiteren ein TestBuild-Standardziel hinzu, um die Aufgabe aufzurufen.

#### <a name="to-add-a-basic-hello-task"></a>So fügen Sie eine einfache „Hallo“-Aufgabe hinzu

1. Ändern Sie im `Project`-Stammknoten das Attribut `DefaultTargets` in `TestBuild`. Der resultierende `Project`-Knoten sollte dem folgenden Beispiel ähneln:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Fügen Sie vor dem Tag `</Project>` die folgende Inlineaufgabe und das folgende Ziel zur Projektdatei hinzu.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Speichern Sie die Projektdatei.

   Dieser Code erstellt eine Inlineaufgabe mit dem Namen „Hallo“ und enthält keine Parameter, Verweise, oder `Using`-Anweisungen. Die „Hallo“-Aufgabe enthält nur eine Codezeile, die auf dem Standardprotokollierungsgerät, in der Regel dem Konsolenfenster, eine „Hallo“-Nachricht anzeigt.

### <a name="run-the-hello-task"></a>Ausführen der „Hallo“-Aufgabe

 Führen Sie im **Eingabeaufforderungsfenster** MSBuild aus, um die „Hallo“-Aufgabe zu erstellen und das TestBuild-Ziel für deren Aufruf zu verarbeiten.

##### <a name="to-run-the-hello-task"></a>So führen Sie die „Hallo“-Aufgabe aus

1. Klicken Sie auf **Start** > **Programme**. Suchen Sie anschließend den Ordner **Visual Studio-Tools** , und klicken Sie auf **Visual Studio-Eingabeaufforderung**.

2. Suchen Sie im **Eingabeaufforderungsfenster** nach dem Ordner mit der Projektdatei, in diesem Fall *D:\InlineTasks\InlineTasks\\* .

3. Geben Sie **msbuild** ohne Befehlsoptionen ein, und drücken Sie anschließend die **EINGABETASTE**. Standardmäßig wird so die Datei *InlineTasks.csproj* erstellt und das TestBuild-Standardziel verarbeitet, das die „Hallo“-Aufgabe aufruft.

4. Untersuchen Sie die Ausgabe im **Eingabeaufforderungsfenster**. Die folgende Zeile sollte angezeigt werden:

    `Hello, world!`

   > [!NOTE]
   > Wenn Ihnen die „Hallo“-Nachricht nicht angezeigt wird, speichern Sie die Projektdatei erneut, und führen Sie anschließend die „Hallo“-Aufgabe aus.

   Durch den Wechsel zwischen dem Code-Editor und dem **Eingabeaufforderungsfenster** können Sie die Projektdatei ändern und die Ergebnisse schnell anzeigen.

## <a name="define-the-echo-task"></a>Definieren der Echo-Aufgabe

 Erstellen Sie eine Inlineaufgabe, die einen Zeichenfolgenparameter akzeptiert und die Zeichenfolge für das Standardprotokollierungsgerät anzeigt.

#### <a name="to-define-the-echo-task"></a>So definieren Sie die Echo-Aufgabe

1. Ersetzen Sie im Code-Editor mithilfe des folgenden Codes die „Hallo“-Aufgabe und das TestBuild-Ziel.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. Geben Sie **msbuild** ohne Befehlsoptionen in das **Eingabeaufforderungsfenster** ein, und drücken Sie anschließend die **Eingabetaste**. Standardmäßig wird so das TestBuild-Standardziel verarbeitet, das die Echo-Aufgabe aufruft.

3. Untersuchen Sie die Ausgabe im **Eingabeaufforderungsfenster**. Die folgende Zeile sollte angezeigt werden:

    `Greetings!`

   Dieser Code definiert die Inlineaufgabe „Echo“ und verfügt nur über einen erforderlichen Eingabeparameter, „Text“. Parameter sind standardmäßig vom Typ „System.String“. Der Wert des Parameters „Text“ wird festgelegt, wenn das TestBuild-Ziel die Echo-Aufgabe aufruft.

## <a name="define-the-adder-task"></a>Definieren der Adder-Aufgabe

 Erstellen Sie eine Inlineaufgabe, bei der zwei ganzzahlige Parameter hinzugefügt werden und die deren Summe als MSBuild-Eigenschaft ausgibt.

#### <a name="to-define-the-adder-task"></a>So definieren Sie die Adder-Aufgabe

1. Ersetzen Sie im Codeeditor die Echo-Aufgabe und das TestBuild-Ziel durch den folgenden Code.

   ```xml
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <A ParameterType="System.Int32" Required="true" />
       <B ParameterType="System.Int32" Required="true" />
       <C ParameterType="System.Int32" Output="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         C = A + B;
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Adder A="4" B="5">
       <Output PropertyName="Sum" TaskParameter="C" />
     </Adder>
     <Message Text="The sum is $(Sum)" Importance="High" />
   </Target>
   ```

2. Geben Sie **msbuild** ohne Befehlsoptionen in das **Eingabeaufforderungsfenster** ein, und drücken Sie anschließend die **Eingabetaste**. Standardmäßig wird so das TestBuild-Standardziel verarbeitet, das die Echo-Aufgabe aufruft.

3. Untersuchen Sie die Ausgabe im **Eingabeaufforderungsfenster**. Die folgende Zeile sollte angezeigt werden:

    `The sum is 9`

   Dieser Code definiert die Inlineaufgabe „Adder“ und verfügt über die beiden erforderlichen ganzzahligen Eingabeparameter „A“ und „B“ sowie über den ganzzahligen Ausgabeparameter „C“. Die Adder-Aufgabe fügt die beiden Eingabeparameter hinzu und gibt die Summe im Ausgabeparameter zurück. Die Summe wird als MSBuild-Eigenschaft `Sum` ausgegeben. Die Werte der Eingabeparameter werden festgelegt, wenn das TestBuild-Ziel die Adder-Aufgabe aufruft.

## <a name="define-the-regx-task"></a>Definieren der RegX-Aufgabe

 Erstellen Sie eine Inlineaufgabe, die eine Elementgruppe sowie einen regulären Ausdruck akzeptiert und eine Liste aller Elemente mit Dateiinhalten zurückgibt, die mit dem Ausdruck übereinstimmen.

#### <a name="to-define-the-regx-task"></a>So definieren Sie die RegX-Aufgabe

1. Ersetzen Sie im Code-Editor die Adder-Aufgabe und das TestBuild-Ziel durch den folgenden Code.

   ```xml
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Expression Required="true" />
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />
     </ParameterGroup>
     <Task>
       <Using Namespace="System.Text.RegularExpressions"/>
       <Code Type="Fragment" Language="cs">
   <![CDATA[
         if (Files.Length > 0)
         {
           Result = new TaskItem[Files.Length];
           for (int i = 0; i < Files.Length; i++)
           {
             ITaskItem item = Files[i];
             string path = item.GetMetadata("FullPath");
             using(StreamReader rdr = File.OpenText(path))
             {
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)
               {
                 Result[i] = new TaskItem(item.ItemSpec);
               }
             }
           }
         }
   ]]>
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <RegX Expression="public|protected" Files="@(Compile)">
       <Output ItemName="MatchedFiles" TaskParameter="Result" />
     </RegX>
     <Message Text="Input files: @(Compile)" Importance="High" />
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />
   </Target>
   ```

2. Geben Sie **msbuild** ohne Befehlsoptionen in das **Eingabeaufforderungsfenster** ein, und drücken Sie anschließend die **Eingabetaste**. Standardmäßig wird so das TestBuild-Standardziel verarbeitet, das die RegX-Aufgabe aufruft.

3. Untersuchen Sie die Ausgabe im **Eingabeaufforderungsfenster**. Die folgenden Zeilen sollten angezeigt werden:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Dieser Code definiert eine Inlineaufgabe mit dem Namen „RegX“ und verfügt über die folgenden drei Parameter:

- `Expression` ist ein erforderlicher Zeichenfolgen-Eingabeparameter, der über einen Wert verfügt, der mit dem regulären Ausdruck übereinstimmt. In diesem Beispiel stimmt der Ausdruck mit dem Wort „public“ oder „protected“ überein.

- `Files` ist ein erforderlicher Eingabeparameter für Elementlisten, der über eine Liste von Dateien als Wert verfügt, die nach der Übereinstimmung durchsucht werden sollen. In diesem Beispiel ist `Files` auf das Element `Compile` festgelegt, das die Projektquelldateien aufführt.

- `Result` ist ein Ausgabeparameter, der über eine Liste mit Dateien als Wert verfügt, deren Inhalt mit dem regulären Ausdruck übereinstimmt.

  Der Wert der Eingabeparameter wird festgelegt, wenn das TestBuild-Ziel die RegX-Aufgabe aufruft. Die RegX-Aufgabe liest jede Datei und gibt die Liste der Dateien zurück, die mit dem regulären Ausdruck übereinstimmen. Diese Liste wird als `Result`-Ausgabeparameter zurückgegeben, der als MSBuild-Element `MatchedFiles` ausgegeben wird.

### <a name="handle-reserved-characters"></a>Verwenden reservierter Zeichen

 Der MSBuild-Parser verarbeitet Inlineaufgaben als XML. Zeichen, deren Bedeutung in XML reserviert ist, z. B. \<" and ">, werden erkannt und behandelt, als ob es sich um XML- und nicht um .NET-Quellcode handelt. Wenn Sie die reservierten Zeichen in Codeausdrücke einfügen möchten, z.B. `Files.Length > 0`, schreiben Sie das `Code`-Element so, dass die zugehörigen Inhalte in einem CDATA-Ausdruck enthalten sind:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  if (Files.Length > 0)
  {
      // Your code goes here.
  }
  ]]>
</Code>
```

## <a name="see-also"></a>Siehe auch

- [Inlineaufgaben](../msbuild/msbuild-inline-tasks.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Ziele](../msbuild/msbuild-targets.md)
