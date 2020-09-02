---
title: Hinzufügen einer benutzerdefinierten Architektur Validierung zu ebenendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b5ebe4e38878df209ab6065b1dbca88cd8404b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655303"
---
# <a name="add-custom-architecture-validation-to-layer-diagrams"></a>Hinzufügen einer benutzerdefinierten Architekturüberprüfung zu Ebenendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Benutzer den Quellcode in einem Projekt anhand eines Ebenenmodells validieren. So kann überprüft werden, ob der Quellcode den Abhängigkeiten in einem Ebenendiagramm entspricht. Es gibt zwar einen Standardvalidierungsalgorithmus, Sie können aber auch eigene Validierungserweiterungen definieren.

 Wenn der Benutzer den Befehl **Architektur überprüfen** für ein Ebenendiagramm auswählt, wird die Standardvalidierungsmethode aufgerufen, anschließend folgen alle installierten Validierungserweiterungen.

> [!NOTE]
> Die Validierung in einem Ebenendiagramm ist nicht mit einer Validierung in UML-Diagrammen vergleichbar. In einem Ebenendiagramm dient sie hauptsächlich dazu, das Diagramm mit dem Programmcode in anderen Teilen der Projektmappe zu vergleichen.

 Sie können die Ebenenvalidierungserweiterung in eine Visual Studio-Integrationserweiterung (VSIX) verpacken, die Sie an andere Visual Studio-Benutzer verteilen können. Sie können entweder das Validierungssteuerelement allein in eine VSIX einfügen, oder Sie können es in der gleichen VSIX mit anderen Erweiterungen kombinieren. Schreiben Sie den Code für das Validierungssteuerelement in einem eigenen Visual Studio-Projekt und nicht im gleichen Projekt wie andere Erweiterungen.

> [!WARNING]
> Nachdem Sie ein Überprüfungsprojekt erstellt haben, kopieren Sie den [Beispielcode](#example) am Ende dieses Themas und bearbeiten diesen dann Ihren Anforderungen entsprechend.

## <a name="requirements"></a>Anforderungen
 Siehe [Anforderungen](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definieren eines Ebenenvalidierungssteuerelements in einer neuen VSIX
 Projektvorlagen stellen die schnellste Methode dar, eine Validierungssteuerelement zu erstellen. Dabei werden der Code und die VSIX im selben Projekt platziert.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>So definieren Sie mithilfe einer Projektvorlage eine Erweiterung

1. Erstellen Sie in einer neuen Projektmappe ein Projekt. Verwenden Sie dazu den Befehl **Neues Projekt** im Menü **Datei** .

2. Klicken Sie im Dialogfeld **Neues Projekt** unter **Modellierungsprojekte**auf **Layer Designer Validation Extension**(Ebenen-Designer - Validierungserweiterung).

    Mit dieser Vorlage wird ein Projekt mit einem kleinen Beispiel erstellt.

   > [!WARNING]
   > Damit die Vorlage ordnungsgemäß funktioniert:
   >
   > - Bearbeiten Sie Aufrufe zu `LogValidationError` , um die optionalen Argumente `errorSourceNodes` und `errorTargetNodes`zu entfernen.
   >   - Wenn Sie benutzerdefinierte Eigenschaften verwenden, wenden Sie das in [Hinzufügen von benutzerdefinierten Eigenschaften zu ebenendiagrammen](../modeling/add-custom-properties-to-layer-diagrams.md)erwähnte Update an.

3. Bearbeiten Sie den Code, um die Validierung zu definieren. Weitere Informationen finden Sie unter [Programmieren einer Validierung](#programming).

4. Weitere Informationen zum Testen der Erweiterung finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).

   > [!NOTE]
   > Die Methode wird nur unter bestimmten Umständen aufgerufen, und Haltepunkte funktionieren nicht automatisch. Weitere Informationen finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).

5. Um die Erweiterung in der Hauptinstanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]oder auf einem anderen Computer zu installieren, suchen Sie die Datei **.vsix** im Ordner *bin\\*. Kopieren Sie die Datei auf den Computer, auf dem Sie sie installieren möchten, und doppelklicken Sie dann darauf. Verwenden Sie zum Deinstallieren der Datei die Option **Erweiterungen und Updates** im Menü **Extras** .

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Hinzufügen eines Ebenenvalidierungssteuerelements zu einer separaten VSIX
 Wenn Sie eine VSIX erstellen möchten, die Ebenenvalidierungssteuerelemente, Befehle und andere Erweiterungen enthält, empfiehlt es sich, ein Projekt zum Definieren der VSIX und getrennte Projekte für die Handler zu erstellen. Weitere Informationen zu anderen Typen der Modellierungs Erweiterung finden Sie unter [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>So fügen Sie einer separaten VSIX eine Ebenenvalidierung hinzu

1. Erstellen Sie in einer neuen oder vorhandenen Visual Studio-Projektmappe ein Klassenbibliotheksprojekt. Klicken Sie im Dialogfeld **Neues Projekt** auf **Visual C#** , und klicken Sie dann auf **Klassenbibliothek**. Dieses Projekt enthält die Ebenenvalidierungsklasse.

2. Identifizieren oder erstellen Sie ein VSIX-Projekt in der Projektmappe. Ein VSIX-Projekt enthält eine Datei mit dem Namen **source.extension.vsixmanifest**. Wenn Sie ein VSIX-Projekt hinzufügen müssen, führen Sie die folgenden Schritte aus:

    1. Wählen Sie im Dialogfeld **Neues Projekt** die Optionen **Visual C#Erweiterungen**, **Erweiterungen**und **VSIX-Projekt**aus.

    2. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü des VSIX-Projekts die Option **Als Startprojekt festlegen**aus.

3. Fügen Sie in **source.extension.vsixmanifest**unter **Objekte**das Ebenenvalidierungsprojekt als MEF-Komponente hinzu:

    1. Wählen Sie **Neu**.

    2. Legen Sie im Dialogfeld **Neues Objekt hinzufügen** Folgendes fest:

         **Typ**  =  **Microsoft. VisualStudio. MEFComponent**

         **Quelle**  =  **Ein Projekt in der aktuellen Projekt** Mappe.

         **Projekt**  =  *Ihr Validierungs* Steuerelement-Projekt

4. Außerdem müssen Sie das Projekt als Ebenenvalidierung hinzufügen:

    1. Wählen Sie **Neu**.

    2. Legen Sie im Dialogfeld **Neues Objekt hinzufügen** Folgendes fest:

         **Typ**  =  **Microsoft. VisualStudio. architecturetools. Layer. validator**. Dies ist keine der Optionen in der Dropdownliste. Sie müssen den Typ über die Tastatur eingeben.

         **Quelle**  =  **Ein Projekt in der aktuellen Projekt** Mappe.

         **Projekt**  =  *Ihr Validierungs* Steuerelement-Projekt

5. Kehren Sie zum Ebenenvalidierungsprojekt zurück, und fügen Sie die folgenden Projektverweise hinzu:

    |**Referenz**|**Optionen**|
    |-------------------|------------------------------------|
    |Microsoft.VisualStudio.GraphModel.dll|Lesen des Architekturdiagramms|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Lesen des Ebenen zugeordneten Code-DOMs|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Lesen des Ebenenmodells|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Lesen und Aktualisieren von Formen und Diagrammen.|
    |System.ComponentModel.Composition|Definieren der Validierungskomponente mithilfe von Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk.[Version]|Definieren von Modellierungserweiterungen|

6. Kopieren Sie den Beispielcode am Ende dieses Themas in die Klassendatei im Bestätigungsbibliotheksprojekt, damit sie den Code für die Überprüfung enthält. Weitere Informationen finden Sie unter [Programmieren einer Validierung](#programming).

7. Weitere Informationen zum Testen der Erweiterung finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).

    > [!NOTE]
    > Die Methode wird nur unter bestimmten Umständen aufgerufen, und Haltepunkte funktionieren nicht automatisch. Weitere Informationen finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).

8. Um die Erweiterung in der Hauptinstanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]oder auf einem anderen Computer zu installieren, suchen Sie die **.vsix** im Verzeichnis **bin** des VSIX-Projekts. Kopieren Sie die Datei auf den Computer, auf dem Sie die VSIX installieren möchten. Doppelklicken Sie in Windows-Explorer auf die VSIX-Datei. (Datei-Explorer in Windows 8.)

     Verwenden Sie zum Deinstallieren der Datei die Option **Erweiterungen und Updates** im Menü **Extras** .

## <a name="programming-validation"></a><a name="programming"></a> Programmier Validierung
 Zum Definieren einer Ebenenvalidierungserweiterung definieren Sie eine Klasse, die über die folgenden Eigenschaften verfügt:

- Die allgemeine Form der Deklaration lautet wie folgt:

  ```

  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Wenn Sie einen Fehler entdecken, können Sie ihn mit `LogValidationError()`melden.

  > [!WARNING]
  > Verwenden Sie nicht die optionalen Parameter von `LogValidationError`.

  Wenn der Benutzer den Menübefehl **Architektur überprüfen** aufruft, werden die Ebenen und ihre Artefakte vom Ebenenlaufzeitsystem analysiert, und es wird ein Diagramm erstellt. Das Diagramm besteht aus vier Teilen:

- Den Ebenenmodellen der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projektmappe, die als Knoten und Links im Diagramm dargestellt werden.

- Dem Code, Projektelementen und anderen Artefakte, die in der Projektmappe definiert und als Knoten dargestellt werden, sowie den Links, die die vom Analyseprozess ermittelten Abhängigkeiten vertreten.

- Links von den Ebenenknoten zu den Codeartefaktknoten.

- Knoten, die die vom Validierungssteuerelement ermittelten Fehler darstellen.

  Wenn das Diagramm erstellt wurde, wird die Standardvalidierungsmethode aufgerufen. Nachdem diese abgeschlossen ist, werden alle installierten Erweiterungsvalidierungsmethoden ohne spezifische Reihenfolge aufgerufen. Das Diagramm wird an jede `ValidateArchitecture` -Methode übergeben, die das Diagramm überprüfen und gefundene Fehler melden kann.

> [!NOTE]
> Dies ist nicht mit dem Validierungsprozess gleichzusetzen, der auf UML-Diagramme angewendet wird und auch nicht mit dem Validierungsprozess, der bei domänenspezifischen Sprachen verwendet werden kann.

 Validierungsmethoden sollten das zu überprüfende Ebenenmodell oder den Code nicht ändern.

 Das Diagrammmodell wird in <xref:Microsoft.VisualStudio.GraphModel>definiert. Seine Prinzipalklassen sind <xref:Microsoft.VisualStudio.GraphModel.GraphNode> und <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

 Jeder Knoten und jeder Link verfügt über mindestens eine Kategorie, die den Typ des Elements oder der Beziehung angibt, die von ihr dargestellt wird. Die Knoten eines typischen Diagramms verfügen über die folgenden Kategorien:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

  Links von Ebenen zu Elementen im Code haben die Kategorie "Represents".

## <a name="debugging-validation"></a><a name="debugging"></a> Debugvalidierung
 Drücken Sie STRG+F5, um die Ebenenvalidierungserweiterung zu debuggen. Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird geöffnet. Öffnen oder erstellen Sie ein Ebenenmodell in dieser Instanz. Dieses Modell muss Code zugeordnet sein und muss mindestens eine Abhängigkeit besitzen.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Test mit einer Projektmappe, die Abhängigkeiten enthält
 Die Validierung wird erst ausgeführt, wenn die folgenden Eigenschaften vorhanden sind:

- Es gibt mindestens einen Abhängigkeitslink im Ebenendiagramm.

- Es gibt Ebenen im Modell, die Codeelementen zugeordnet sind.

  Öffnen oder erstellen Sie eine Projektmappe mit diesen Eigenschaften, wenn Sie eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zum ersten Mal zum Testen der Validierungserweiterung starten.

### <a name="run-clean-solution-before-validate-architecture"></a>Ausführen einer Projektmappenbereinigung vor dem Überprüfen der Architektur
 Verwenden Sie bei jeder Aktualisierung des Validierungscodes im Menü **Erstellen** der experimentellen Instanz den Befehl **Projektmappe bereinigen** , bevor Sie den Befehl "Überprüfen" testen. Dies ist notwendig, da die Ergebnisse der Validierung zwischengespeichert werden. Wenn das Testebenendiagramm oder sein Code nicht aktualisiert wurden, werden die Validierungsmethoden nicht ausgeführt.

### <a name="launch-the-debugger-explicitly"></a>Explizites Starten des Debuggers
 Die Validierung wird in einem separaten Prozess ausgeführt. Daher werden die Haltepunkte in der Überprüfungsmethode nicht ausgelöst. Sie müssen den Debugger explizit dem Prozess anfügen, wenn die Validierung gestartet wurde.

 Fügen Sie am Anfang der Validierungsmethode einen Aufruf von `System.Diagnostics.Debugger.Launch()` ein, um den Debugger dem Validierungsprozess anzufügen. Wenn das Debugdialogfeld angezeigt wird, wählen Sie die Hauptinstanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]aus.

 Alternativ können Sie einen Aufruf von `System.Windows.Forms.MessageBox.Show()`einfügen. Wenn das Meldungsfeld angezeigt wird, wechseln Sie zur Hauptinstanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , und klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**. Wählen Sie den Prozess mit dem Namen **Graphcmd.exe**aus.

 Starten Sie die experimentelle Instanz immer mit STRG+F5 (**Starten ohne Debugging**).

### <a name="deploying-a-validation-extension"></a>Bereitstellen einer Validierungserweiterung
 Um die Validierungserweiterung auf einem Computer zu installieren, auf dem eine geeignete Version von Visual Studio installiert ist, öffnen Sie die VSIX-Datei auf dem Zielcomputer. Um die Installation auf einem Computer mit [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] auszuführen, müssen Sie den VSIX-Inhalt manuell in einen Ordner "Extensions" extrahieren. Weitere Informationen finden Sie unter Bereitstellen [einer ebenenmodellerweiterung](../modeling/deploy-a-layer-model-extension.md).

## <a name="example-code"></a><a name="example"></a> Beispielcode

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
 [Erweitern von Ebenendiagrammen](../modeling/extend-layer-diagrams.md)
