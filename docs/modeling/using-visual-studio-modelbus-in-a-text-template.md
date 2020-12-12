---
title: Verwenden von ModelBus in einer Text Vorlage
description: Erfahren Sie, wie Sie Verweise auf Ziel Modelle auflösen, wenn Sie Textvorlagen schreiben, die ein Modell lesen, das Visual Studio ModelBus Verweise enthält.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1025e7d35c20dc18c87942e23cf71b598d85637a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361364"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Verwenden von Visual Studio-ModelBus in einer Textvorlage

Wenn Sie Textvorlagen schreiben, die ein Modell lesen, das Visual Studio ModelBus Verweise enthält, können Sie die Verweise auflösen, um auf die Ziel Modelle zuzugreifen. In diesem Fall müssen Sie die Textvorlagen und die referenzierten domänenspezifischen Sprachen (DSLs) anpassen:

- Die DSL, die das Ziel der Verweise ist, muss über einen ModelBus-Adapter verfügen, der für den Zugriff aus Textvorlagen konfiguriert ist. Wenn Sie auch über anderen Code auf die DSL zugreifen, ist der neu konfigurierte Adapter zusätzlich zum Standard-ModelBus-Adapter erforderlich.

     Der Adapter-Manager muss von [vstexttemplatingmodelingadaptermanager](/previous-versions/ee844317(v=vs.140)) erben und muss über das-Attribut verfügen `[HostSpecific(HostName)]` .

- Die Vorlage muss von [modelbusenabledtexttransformation](/previous-versions/ee844263(v=vs.140))erben.

> [!NOTE]
> Wenn Sie DSL-Modelle lesen möchten, die keine ModelBus-Verweise enthalten, können Sie die in Ihren DSL-Projekten generierten direktivenprozessoren verwenden. Weitere Informationen finden Sie unter [zugreifen auf Modelle aus Text Vorlagen](../modeling/accessing-models-from-text-templates.md).

Weitere Informationen zu Textvorlagen finden Sie unter [Entwurfszeit Code Generierung mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Erstellen eines modellbus Adapters für den Zugriff aus Text Vorlagen

Um einen ModelBus-Verweis in einer Textvorlage aufzulösen, muss die Ziel-DSL über einen kompatiblen Adapter verfügen. Text Vorlagen werden in einer separaten AppDomain aus den Visual Studio-Dokument-Editoren ausgeführt. Daher muss der Adapter das Modell laden, anstatt über DTE darauf zuzugreifen.

1. Wenn die Ziel-DSL-Lösung nicht über ein **modelbusadapter** -Projekt verfügt, erstellen Sie eine mit dem modellbus-Erweiterungs-Assistenten:

    1. Laden Sie die Visual Studio ModelBus Erweiterung herunter, und installieren Sie Sie, falls Sie dies noch nicht getan haben. Weitere Informationen finden Sie unter [Visualisierungs-und Modellierungs-SDK](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Öffnen Sie die DSL-Definitionsdatei. Klicken Sie mit der rechten Maustaste auf die Entwurfs Oberfläche und dann auf **ModelBus aktivieren**.

    3. Wählen Sie im Dialogfeld **Ich möchte diese DSL für ModelBus** verfügbar machen aus. Sie können beide Optionen auswählen, wenn Sie möchten, dass diese DSL Ihre Modelle verfügbar macht und Verweise auf andere DSLs verwendet.

    4. Klicken Sie auf **OK**. Der DSL-Projektmappe wird ein neues ModelBusAdapter-Projekt hinzugefügt.

    5. Klicken Sie auf **alle Vorlagen transformieren**.

    6. Generieren Sie die Projektmappe neu.

2. Wenn Sie auf die DSL sowohl über eine Textvorlage als auch über anderen Code (z. b. über einen Befehl) zugreifen möchten, duplizieren Sie das **modelbusadapter** -Projekt:

    1. Kopieren Sie in Windows-Explorer den Ordner, der " **modelbusadapter. csproj**" enthält, und fügen Sie ihn ein.

    2. Benennen Sie die Projektdatei um (z **. b. in T4ModelBusAdapter. csproj**).

    3. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Lösungs Knoten, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**. Suchen Sie das neue Adapter Projekt, **T4ModelBusAdapter. csproj**.

    4. Ändern Sie `*.tt` den Namespace in jeder Datei des neuen Projekts.

    5. Klicken Sie mit der rechten Maustaste auf das neue Projekt in **Projektmappen-Explorer** und klicken Sie dann auf **Eigenschaften**. Ändern Sie im Eigenschaften-Editor die Namen der generierten Assembly und des Standard Namespace.

    6. Fügen Sie im dslpackage-Projekt einen Verweis auf das neue Adapter Projekt hinzu, sodass es Verweise auf beide Adapter enthält.

    7. Fügen Sie in DslPackage\source.Extension.tt eine Zeile hinzu, die auf das neue Adapter Projekt verweist.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformieren Sie alle Vorlagen** , und erstellen Sie die Lösung neu. Es sollten keine Buildfehler auftreten.

3. Fügen Sie im neuen Adapter Projekt Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft. VisualStudio. TextTemplating. Modeling. 11.0

4. In AdapterManager.tt:

    - Ändern Sie die Deklaration von adaptermanagerbase, sodass Sie von [vstexttemplatingmodelingadaptermanager](/previous-versions/ee844317(v=vs.140))erbt.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Ersetzen Sie das hostspecific-Attribut in der Nähe des Datei Endes vor der adaptermanager-Klasse. Entfernen Sie die folgende Zeile:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Fügen Sie die folgende Zeile ein:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Dieses Attribut filtert den Satz von Adaptern, der verfügbar ist, wenn ein ModelBus-Consumer nach einem Adapter sucht.

5. **Transformieren Sie alle Vorlagen** , und erstellen Sie die Lösung neu. Es sollten keine Buildfehler auftreten.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Schreiben einer Text Vorlage, mit der ModelBus-Verweise aufgelöst werden können

In der Regel beginnen Sie mit einer Vorlage, die Dateien aus einer "Quell-DSL" liest und generiert. Diese Vorlage verwendet die-Direktive, die im Quell-DSL-Projekt generiert wird, um Quell Modelldateien in der Art und Weise zu lesen, die unter [zugreifen auf Modelle aus Text Vorlagen](../modeling/accessing-models-from-text-templates.md)beschrieben wird. Die Quell-DSL enthält jedoch ModelBus-Verweise auf eine "Ziel"-DSL. Daher möchten Sie den Vorlagen Code aktivieren, um die Verweise aufzulösen und auf die Ziel-DSL zuzugreifen. Daher müssen Sie die Vorlage anpassen, indem Sie die folgenden Schritte ausführen:

- Ändern Sie die Basisklasse der Vorlage in [modelbusenabledtexttransformation](/previous-versions/ee844263(v=vs.140)).

- Fügen Sie `hostspecific="true"` in die Template-Direktive ein.

- Fügen Sie der Ziel-DSL und dem zugehörigen Adapter Assemblyverweise hinzu, und aktivieren Sie ModelBus.

- Sie benötigen nicht die Direktive, die als Teil der Ziel-DSL generiert wird.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 Beim Ausführen dieser Textvorlage lädt die- `SourceDsl` Anweisung die Datei `Sample.source` . Die Vorlage kann auf die Elemente dieses Modells zugreifen, beginnend mit `this.ModelRoot` . Im Code können die Domänen Klassen und Eigenschaften dieser DSL verwendet werden.

 Außerdem kann die Vorlage ModelBus-Verweise auflösen. Wenn die Verweise auf das Zielmodell verweisen, ermöglichen die assemblydirektiven dem Code, die Domänen Klassen und-Eigenschaften der DSL des Modells zu verwenden.

- Wenn Sie keine-Direktive verwenden, die von einem DSL-Projekt generiert wird, sollten Sie auch Folgendes einschließen.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Verwenden `this.ModelBus` Sie, um Zugriff auf ModelBus zu erhalten.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Exemplarische Vorgehensweise: Testen einer Text Vorlage, die ModelBus verwendet
 In dieser exemplarischen Vorgehensweise führen Sie die folgenden Schritte aus:

1. Erstellen Sie zwei DSLs. Eine DSL, der *Consumer*, verfügt über eine-Eigenschaft, die `ModelBusReference` auf die andere DSL, den- *Anbieter*, verweisen kann.

2. Erstellen Sie zwei ModelBus-Adapter im Anbieter: eine für den Zugriff durch Textvorlagen, die andere für den normalen Code.

3. Erstellen Sie instanzmodelle der DSLs in einem einzigen experimentellen Projekt.

4. Legen Sie eine Domänen Eigenschaft in einem Modell so fest, dass Sie auf das andere Modell verweist.

5. Schreiben Sie einen Doppelklick Handler, der das Modell öffnet, auf das verwiesen wird.

6. Schreiben Sie eine Textvorlage, mit der das erste Modell geladen werden kann, befolgen Sie den Verweis auf das andere Modell, und lesen Sie das andere Modell.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Erstellen einer DSL, die für ModelBus zugänglich ist

1. Erstellen Sie eine neue DSL-Projekt Mappe. Wählen Sie für dieses Beispiel die Lösungs Vorlage für den Task Ablauf aus. Legen Sie den Namen der Sprache auf `MBProvider` und die Dateinamenerweiterung auf ". bereitstellen" fest.

2. Klicken Sie im DSL-Definitions Diagramm mit der rechten Maustaste auf einen leeren Bereich des Diagramms, der sich nicht am oberen Rand befindet, und klicken Sie dann auf **ModelBus aktivieren**.

   Wenn Sie **ModelBus aktivieren** nicht sehen, laden Sie die vmsdk-ModelBus-Erweiterung herunter, und installieren Sie Sie.

3. Wählen Sie im Dialogfeld **ModelBus aktivieren** **die Option Diese DSL für ModelBus** verfügbar machen aus, und klicken Sie dann auf **OK**.

    Der Projekt Mappe wird ein neues Projekt `ModelBusAdapter` hinzugefügt.

Sie verfügen jetzt über eine DSL, auf die Textvorlagen über ModelBus zugreifen können. Verweise darauf können im Code von Befehlen, Ereignis Handlern oder Regeln aufgelöst werden, die alle in der AppDomain des Modelldatei-Editors ausgeführt werden. Textvorlagen werden jedoch in einer separaten AppDomain ausgeführt und können nicht auf ein Modell zugreifen, wenn es bearbeitet wird. Wenn Sie von einer Textvorlage aus auf ModelBus-Verweise auf diese DSL zugreifen möchten, benötigen Sie einen separaten modelbusadapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Erstellen eines ModelBus-Adapters, der für Text Vorlagen konfiguriert ist

1. Kopieren Sie im Datei-Explorer den Ordner, der " *modelbusadapter. csproj*" enthält, und fügen Sie ihn ein.

    Benennen Sie den Ordner **T4ModelBusAdapter**.

    Benennen Sie die Projektdatei *T4ModelBusAdapter. csproj* um.

2. Fügen Sie in Projektmappen-Explorer der mbprovider-Lösung T4ModelBusAdapter hinzu. Klicken Sie mit der rechten Maustaste auf den Projektmappenknoten, zeigen Sie auf **Hinzufügen** und dann auf **vorhandenes Projekt**

3. Klicken Sie mit der rechten Maustaste auf den Knoten T4ModelBusAdapter, und klicken Sie dann auf Eigenschaften. Ändern Sie im Fenster "Projekteigenschaften"  den Assemblynamen und den **Standard Namespace** in `Company.MBProvider.T4ModelBusAdapters` .

4. Fügen Sie in jeder *. tt-Datei in T4ModelBusAdapter "T4" in den letzten Teil des Namespace ein, sodass die Zeile der folgenden ähnelt.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. `DslPackage`Fügen Sie im-Projekt einen Projekt Verweis auf hinzu `T4ModelBusAdapter` .

6. Fügen Sie in DslPackage\source.Extension.tt die folgende Zeile unter hinzu `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. `T4ModelBusAdapter`Fügen Sie im Projekt einen Verweis auf: **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0** hinzu.

8. Öffnen Sie T4ModelBusAdapter\AdapterManager.tt:

   1. Ändern Sie die Basisklasse von adaptermanagerbase in [vstexttemplatingmodelingadaptermanager](/previous-versions/ee844317(v=vs.140)). Dieser Teil der Datei ähnelt nun der folgenden.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {
       ```

   2. Fügen Sie am Ende der Datei das folgende zusätzliche Attribut vor der Klasse adaptermanager ein.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Das Ergebnis ähnelt dem folgenden.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }
       ```

9. Klicken Sie in der Titelleiste von Projektmappen-Explorer auf **alle Vorlagen transformieren** .

10. Drücken Sie **F5**.

11. Überprüfen Sie, ob die DSL funktioniert. Öffnen Sie im experimentellen Projekt `Sample.provider` . Schließen Sie die experimentelle Instanz von Visual Studio.

    ModelBus-Verweise auf diese DSL können nun in Textvorlagen und auch in normalem Code aufgelöst werden.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Erstellen einer DSL mit einer ModelBus-Verweis Domänen Eigenschaft

1. Erstellen Sie eine neue DSL mithilfe der Vorlage für minimale Sprachlösungen. Benennen Sie die Sprache mbconsumer, und legen Sie die Dateinamenerweiterung auf ". Consumer" fest.

2. Fügen Sie im DSL-Projekt einen Verweis auf die mbprovider-DSL-Assembly hinzu. Klicken Sie mit der rechten Maustaste auf  `MBConsumer\Dsl\References` **Verweis hinzufügen**. Suchen Sie auf der Registerkarte **Durchsuchen** nach `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Dies ermöglicht es Ihnen, Code zu erstellen, der die andere DSL verwendet. Wenn Sie Verweise auf mehrere DSLs erstellen möchten, fügen Sie Sie hinzu.

3. Klicken Sie im DSL-Definitions Diagramm mit der rechten Maustaste auf das Diagramm, und klicken Sie dann auf **ModelBus aktivieren**. Aktivieren Sie im Dialogfeld **die Option Diese DSL zum Verwenden von ModelBus aktivieren**.

4. `ExampleElement`Fügen Sie in der-Klasse eine neue Domänen Eigenschaft hinzu `MBR` , und legen Sie im Eigenschaftenfenster ihren Typ auf fest `ModelBusReference` .

5. Klicken Sie im Diagramm mit der rechten Maustaste auf die Eigenschaft Domäne, und klicken Sie dann auf **modelbusreference-spezifische Eigenschaften bearbeiten**. Wählen Sie im Dialogfeld **ein Modellelement** aus.

    Legen Sie den Filter für Datei Dialogfelder auf Folgendes fest.

    `Provider File|*.provide`

    Die Teil Zeichenfolge nach "&#124;" ist ein Filter für das Dialogfeld zur Dateiauswahl. Sie können festlegen, dass alle Dateien mithilfe von * zugelassen werden.\*

    Geben Sie in der Liste **Modell Elementtyp** die Namen von mindestens einer Domänen Klasse in der Anbieter-DSL ein (z. b. Company. mbprovider. Task). Sie können abstrakte Klassen sein. Wenn Sie die Liste leer lassen, kann der Benutzer den Verweis auf ein beliebiges Element festlegen.

6. Schließen Sie das Dialogfeld, und **transformieren Sie alle Vorlagen**.

   Sie haben eine DSL erstellt, die Verweise auf Elemente in einer anderen DSL enthalten kann.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>ModelBus-Verweis auf eine andere Datei in der Projekt Mappe erstellen

1. Drücken Sie in der mbconsumer-Lösung STRG + F5. Eine experimentelle Instanz von Visual Studio wird im Projekt **mbconsumer\debugging** geöffnet.

2. Fügen Sie dem Projekt **mbconsumer\debug** eine Kopie von Sample. be hinzu. Dies ist erforderlich, da ein ModelBus-Verweis auf eine Datei in der gleichen Projekt Mappe verweisen muss.

   1. Klicken Sie mit der rechten Maustaste auf das Projekt Debugging, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **vorhandenes**

   2. Legen Sie im Dialogfeld **Element hinzufügen** den Filter auf **alle Dateien ( \* . \* )** fest.

   3. Navigieren Sie zu, `MBProvider\Debugging\Sample.provide` und klicken Sie dann auf **Hinzufügen**.

3. Öffnen Sie `Sample.consume`.

4. Klicken Sie auf eine Beispiel Form, und klicken Sie in der Eigenschaftenfenster auf **[...]** in der MBR-Eigenschaft. Klicken Sie im Dialogfeld auf **Durchsuchen** , und wählen Sie aus `Sample.provide` . Erweitern Sie im Fensterelemente den Typ Task, und wählen Sie eines der-Elemente aus.

5. Speichern Sie die Datei. (Schließen Sie die experimentelle Instanz von Visual Studio noch nicht.)

   Sie haben ein Modell erstellt, das einen ModelBus-Verweis auf ein Element in einem anderen Modell enthält.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Auflösen eines ModelBus-Verweises in einer Textvorlage

1. Öffnen Sie in der experimentellen Instanz von Visual Studio eine Beispiel-Textvorlagen Datei. Legen Sie den Inhalt wie folgt fest.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     Beachten Sie die folgenden Punkte:

    - Das `hostSpecific` -und das- `inherits` Attribut der- `template` Direktive müssen festgelegt werden.

    - Der Zugriff auf das consumermodell erfolgt auf die übliche Weise über den Direktivenprozessor, der in dieser DSL generiert wurde.

    - Die Assembly-und Import Direktiven müssen in der Lage sein, auf ModelBus und die Typen der Anbieter-DSL zuzugreifen.

    - Wenn Sie wissen, dass viele MBRs mit dem gleichen Modell verknüpft sind, empfiehlt es sich, "immer nur einmal" aufzurufen.

2. Speichern Sie die Vorlage. Überprüfen Sie, ob die resultierende Textdatei der folgenden ähnelt.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Auflösen eines ModelBus-Verweises in einem Gesten Handler

1. Schließen Sie die experimentelle Instanz von Visual Studio, wenn Sie ausgeführt wird.

2. Fügen Sie eine Datei mit dem Namen " *mbconsumer\dsl\custom.cs* " hinzu, und legen Sie deren Inhalt auf Folgendes fest:

    ```csharp
    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }
    ```

3. Drücken Sie **STRG** + **F5**.

4. Öffnen Sie in der experimentellen Instanz von Visual Studio `Debugging\Sample.consume` .

5. Doppelklicken Sie auf eine Form.

    Wenn Sie den MBR für dieses Element festgelegt haben, wird das Modell, auf das verwiesen wird, geöffnet und das Element, auf das verwiesen wird

## <a name="see-also"></a>Siehe auch

- [Integrieren von Modellen mit Visual Studio-ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Code Generierung und T4-Text Vorlagen](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
