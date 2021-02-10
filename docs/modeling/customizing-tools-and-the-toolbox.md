---
title: Anpassen der Tools und der Toolbox
description: Erfahren Sie, wie Sie Toolbox Elemente für die Elemente definieren müssen, die Benutzer zu Ihren Modellen hinzufügen möchten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 40341a0c74b371c4c84429474e58c7d338bb8059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935429"
---
# <a name="customizing-tools-and-the-toolbox"></a>Anpassen der Tools und der Toolbox

Sie müssen Toolboxelemente für die Elemente definieren, die die Benutzer ihren Modellen hinzufügen dürfen. Es gibt zwei Arten von Tools: Elementtools und Verbindungstools. Im generierten Designer kann ein Benutzer ein Elementtool auswählen, um Formen auf das Diagramm zu ziehen. Dann kann der Benutzer ein Verbindungstool auswählen, um die Verbindungen zwischen den Formen zu zeichnen. Im Allgemeinen können Benutzer mit Elementtools ihren Modellen Instanzen von Domänenklassen hinzufügen, und mit Verbindungstools können sie Instanzen von Domänenbeziehungen hinzufügen.

## <a name="how-the-toolbox-is-defined"></a><a name="ToolboxDef"></a> Definition der Toolbox
 Erweitern Sie im DSL-Explorer den Knoten "Editor" und die darunter liegenden Knoten. Normalerweise wird eine Hierarchie wie die folgende angezeigt:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

In diesem Teil des DSL-Explorers können Sie folgende Aufgaben ausführen:

- Neue Registerkarten erstellen. Mit Registerkarten werden die Abschnittsüberschriften in der Toolbox definiert.

- Neue Tools erstellen.

- Kopieren Sie Tools, und fügen Sie sie ein.

- Tools in der Liste nach oben oder unten verschieben.

- Registerkarten und Tools löschen.

> [!IMPORTANT]
> Sie können in einem DSL-Explorer Elemente hinzufügen oder einfügen, indem Sie mit der rechten Maustaste auf die zweite übergeordnete Ebene klicken. Um z. b. ein Tool hinzuzufügen, klicken Sie mit der rechten Maustaste auf die Registerkarte, nicht auf **den Knoten Extras** . Klicken Sie zum Hinzufügen einer Registerkarte mit der rechten Maustaste auf den **Editor** -Knoten.

Die **Toolbox Icon** -Eigenschaft jedes Tools verweist auf eine 16x16-Bitmapdatei. Diese Dateien werden in der Regel im Ordner " **dsl\resources** " gespeichert.

Die **Class** -Eigenschaft eines Element Tools verweist auf eine konkrete Domänen Klasse. Standardmäßig erstellt das Tool Instanzen dieser Klasse. Sie können jedoch Code schreiben, damit das Tool Gruppen von Elementen oder Elemente unterschiedlicher Typen erstellt.

Die **Verbindungs** -Generator-Eigenschaft eines Verbindungs Tools verweist auf einen Verbindungs-Generator, der definiert, welche Typen von Elementen das Tool verbinden kann und welche Beziehungen zwischen Ihnen erstellt werden. Verbindungs-Generatoren werden im DSL-Explorer als Knoten definiert. Verbindungs-Generatoren werden automatisch erstellt, wenn Sie Domänenbeziehungen definieren, aber Sie können sie über Code anpassen.

#### <a name="to-add-a-tool-to-the-toolbox"></a>So fügen Sie der Toolbox ein Tool hinzu

1. Normalerweise erstellen Sie ein Elementtool, nachdem Sie eine Formklasse erstellt und einer Domänenklasse zugeordnet haben.

     Normalerweise erstellen Sie ein Konnektortool, nachdem Sie eine Konnektorklasse erstellt und einer Verweisbeziehung zugeordnet haben.

2. Erweitern Sie im DSL-Explorer den Knoten **Editor** und den Knoten **Toolbox Registerkarten** .

     Klicken Sie mit der rechten Maustaste auf einen Toolbox-Registerkarten Knoten, und klicken Sie dann auf **Add New Element Tool** oder **Add New Connection Tool**.

3. Legen Sie die **Toolbox Icon** -Eigenschaft so fest, dass Sie auf eine 16x16-Bitmap verweist.

     Wenn Sie ein neues Symbol definieren möchten, erstellen Sie eine Bitmapdatei in Projektmappen-Explorer im Ordner " **dsl\resources** ". Die Datei sollte die folgenden Eigenschaftswerte aufweisen: Inhalt der **Buildaktion**  =  ; **In Ausgabeverzeichnis kopieren**  =  **Nicht kopieren**.

4. **Für ein Element Tool:** Legen Sie die Eigenschaft **Klasse** des Tools so fest, dass Sie auf eine konkrete Domänen Klasse verweist, die einer Form zugeordnet ist.

     **Für ein Connector-Tool:** Legen Sie die Eigenschaft **Verbindungs** -Generator des Tools auf eines der Elemente fest, die in der Dropdown Liste angeboten werden. Verbindungs-Generatoren werden automatisch erstellt, wenn Sie einen Konnektor einer Domänenbeziehung zuordnen. Wenn Sie gerade einen Konnektor erstellt haben, würden Sie normalerweise den zugehörigen Verbindungs-Generator auswählen.

5. Um die DSL zu testen, drücken Sie F5 oder STRG + F5, und öffnen Sie in der experimentellen Instanz von Visual Studio eine Beispielmodell Datei. Das neue Tool sollte in der Toolbox aufgeführt sein. Ziehen Sie es auf das Diagramm, um zu überprüfen, ob es ein neues Element erstellt.

     Wenn das Tool nicht angezeigt wird, können Sie die experimentelle Visual Studio-Datei abbrechen. Führen Sie im Windows- **Startmenü** **die Option 2010 Microsoft Visual Studio experimentellen Instanz zurücksetzen** aus. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**. Wiederholen Sie dann den DSL-Test.

## <a name="customizing-element-tools"></a><a name="customizing"></a> Anpassen von Element Tools
 Standardmäßig erstellt das Tool eine Instanz der angegebenen Klasse. Sie haben jedoch zwei Optionen, dies zu ändern:

- Definieren Sie Direktiven für Elementzusammenführungen für andere Klassen, sodass sie neue Instanzen dieser Klasse akzeptieren und weitere Links erstellen können, wenn ein neues Element erstellt wird. Sie können beispielsweise zulassen, dass ein Benutzer einem anderen Element einen Kommentar hinzufügt und auf diese Weise einen Verweislink zwischen beiden erstellt.

     Diese Anpassungen haben auch Auswirkungen darauf, was geschieht, wenn der Benutzer ein Element einfügt oder per Drag &amp; Drop ergänzt.

     Weitere Informationen finden Sie unter [Anpassen der Element Erstellung und-](../modeling/customizing-element-creation-and-movement.md)Verschiebung.

- Schreiben Sie Code, um das Tool so anzupassen, dass es Gruppen von Elementen erstellen kann. Das Tool wird von Methoden in "ToolboxHelper.cs" initialisiert, die Sie überschreiben können. Weitere Informationen finden Sie unter [Erstellen von Elementgruppen aus einem Tool](#groups).

## <a name="creating-groups-of-elements-from-a-tool"></a><a name="groups"></a> Erstellen von Elementgruppen aus einem Tool
 Jedes Elementtool enthält einen Prototyp der Elemente, die es erstellen soll. Standardmäßig erstellt jedes Elementtool ein Element. Es ist jedoch auch möglich, eine Gruppe verknüpfter Objekte mit einem Tool zu erstellen. Dazu initialisieren Sie das Tool mit einem <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>, der verknüpfte Elemente enthält.

 Das folgende Beispiel stammt aus DSL und enthält einen Typ "Transistor". Jeder Transistor weist drei benannte Terminals auf. Das Elementtool für Transistoren speichert einen Prototyp, der vier Modellelemente und drei Beziehungslinks enthält. Wenn der Benutzer das Tool auf das Diagramm zieht, wird der Prototyp instanziiert und mit dem Modellstamm verknüpft.

 Dieser Code überschreibt eine Methode, die in " **dsl\generatedcode\toolboxhelper.cs**" definiert ist.

 Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [navigieren und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="customizing-connection-tools"></a><a name="connections"></a> Anpassen von Verbindungs Tools
 Üblicherweise erstellen Sie ein Elementtool, wenn Sie eine neue Konnektorklasse erstellen. Alternativ können Sie ein Tool überladen, indem Sie den Beziehungstyp durch die Typen an den beiden Enden bestimmen lassen. Beispielsweise könnten Sie ein Verbindungstool erstellen, das Person-Person- und Person-Stadt-Beziehungen erstellen kann.

 Verbindungstools rufen Verbindungs-Generatoren auf. Verwenden Sie Verbindungs-Generatoren, um anzugeben, wie Benutzer Elemente im generierten Designer verknüpfen können. Mit Verbindungs-Generatoren werden die Elemente angegeben, die verknüpft werden können. Zudem wird die Art von Link bestimmt, der zwischen den Elementen erstellt werden kann.

 Wenn Sie eine Verweisbeziehung zwischen Domänenklassen erstellen, wird automatisch ein Verbindungs-Generator erstellt. Sie können diesen Verbindungs-Generator verwenden, wenn Sie ein Verbindungstool zuordnen. Weitere Informationen zum Erstellen von Verbindungs Tools finden Sie unter [Konfigurieren der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).

 Sie können den standardmäßigen Verbindungs-Generator so ändern, dass er mit einem anderen Bereich von Quell- und Zieltypen verwendet werden kann und unterschiedliche Typen von Beziehungen erstellen kann.

 Darüber hinaus können Sie benutzerdefinierten Code für Verbindungs-Generatoren schreiben, um die Quell- und Zielklassen für die Verbindung anzugeben, den Typ der herzustellenden Verbindung zu definieren und Aktionen im Zusammenhang mit der Verbindungserstellung auszuführen.

### <a name="the-structure-of-connection-builders"></a>Struktur der Verbindungs-Generatoren
 Verbindungs-Generatoren enthalten mindestens eine Direktive für Linkverbindungen, um die Domänenbeziehung sowie die Quell- und Zielelemente anzugeben. Beispielsweise können Sie in der Lösungs Vorlage für Aufgaben Abläufe den **commentreferencessubjezbuilder** im **DSL-Explorer** sehen. Dieser Verbindungs-Generator enthält eine Link Verbindungs Direktive mit dem Namen **commentreferencessubjects**, die der Domänen Beziehung **commentreferencessubjects** zugeordnet ist. Diese Direktive für Linkverbindungen enthält eine Direktive für die Quellrolle, die auf die `Comment`-Domänenklasse verweist, und eine Direktive für die Zielrolle, die auf die `FlowElement`-Domänenklasse verweist.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Verwenden von Verbindungs-Generatoren zum Beschränken von Quell- und Zielrollen
 Sie können mit Verbindungs-Generatoren das Auftreten bestimmter Klassen in der Quell- oder Zielrolle einer angegebenen Domänenbeziehung beschränken. Beispiel: Sie verfügen über eine Basisdomänenklasse, die eine Domänenbeziehung mit einer anderen Domänenklasse aufweist, Sie möchten jedoch nicht, dass alle abgeleiteten Klassen der Basisklasse in dieser Beziehung die gleiche Rolle haben. In der Lösung für den Task Ablauf gibt es vier konkrete Domänen Klassen (**StartPoint**, **EndPoint**, **mergebranch** und **Synchronisierung**), die direkt von der abstrakten Domänen Klasse " **flowelements**" und zwei konkrete Domänen Klassen (**Task** und **objectinstate**) erben, die indirekt von der Klasse erben. Es gibt auch eine **flowverweisbeziehung** , die **flowelements** -Domänen Klassen sowohl in der Quell-als auch in der Zielrolle übernimmt. Eine Instanz einer **Endpunkt** Domänen Klasse sollte jedoch nicht die Quelle einer Instanz einer **Flow** -Beziehung sein, und es sollte keine Instanz einer **Start Point** -Klasse das Ziel einer Instanz einer **Flow** -Beziehung sein. Der **flowbuilder** -Verbindungs-Generator verfügt über eine Link Verbindungs Direktive namens **Flow** , die angibt, welche Domänen Klassen die Quell Rolle wiedergeben können (**Task**, **mergebranch**, **StartPoint** und **Synchronisierung**) und welche die Zielrolle wiedergeben kann (**mergebranch**, **Endpunkt** und **Synchronisierung**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Verbindungs-Generatoren mit mehreren Direktiven für Linkverbindungen
 Sie können einem Verbindungs-Generator mehr als eine Direktive für Linkverbindungen hinzufügen. Dies kann Ihnen dabei helfen, einige der Komplexitäten des Domänen Modells vor Benutzern auszublenden und zu verhindern, dass die **Toolbox** zu überlastet ist. Sie können in einem Verbindungs-Generator für mehrere verschiedene Domänenbeziehungen Direktiven für Linkverbindungen hinzufügen. Sie sollten Domänenbeziehungen jedoch kombinieren, wenn sie annähernd die gleiche Funktion ausführen.

 In der Lösung für den Task Ablauf wird das **Flow** -Verbindungs Tool zum Zeichnen von Instanzen der Daten **Fluss** -und **objectflow** -Domänen Beziehungen verwendet. Der **flowbuilder** -Verbindungs-Generator hat zusätzlich zur zuvor beschriebenen Anweisung für die **Fluss** Link Verbindung zwei Verknüpfungs Verbindungs Direktiven namens **objectflow**. Diese Direktiven legen fest, dass eine Instanz einer **objectflow** -Beziehung zwischen Instanzen der **objectinstate** -Domänen Klasse oder von einer Instanz von **objectinstate** in eine Instanz eines **Tasks, jedoch** nicht zwischen zwei Instanzen einer **Aufgabe** oder von einer Instanz eines Tasks in eine Instanz von  **objectinstate** gezeichnet werden kann. Allerdings kann eine Instanz einer **Flow** -Beziehung zwischen zwei Instanzen einer **Aufgabe** gezeichnet werden. Wenn Sie die Lösung für den Task Ablauf kompilieren und ausführen, sehen Sie, dass das Zeichnen eines **Flows** von einer Instanz eines **objectinstate** zu einer Instanz eines Tasks eine Instanz eines **objectflow** **erstellt,** aber das Zeichnen eines **Flows** zwischen zwei Instanzen einer **Aufgabe** eine Instanz eines **Flows** erzeugt.

### <a name="custom-code-for-connection-builders"></a>Benutzerdefinierter Code für Verbindungs-Generatoren
 Es gibt vier Kontrollkästchen auf der Benutzeroberfläche, mit denen die unterschiedlichen Typen von Anpassungen der Verbindungs-Generatoren definiert werden:

- Kontrollkästchen **benutzerdefinierte Annahme** für eine Quell-oder zielrollendirektive

- Kontrollkästchen " **benutzerdefinierte Verbindung** " für eine Quell-oder Zielrollen-Direktive

- das Kontrollkästchen **benutzerdefinierte Verbindung** wird in einer Connect-Direktive verwendet.

- die Eigenschaft **ist Benutzer** definiert des Verbindungs-Generators.

  Für diese Anpassungen müssen Sie Programmcode angeben. Sie können herausfinden, welcher Code erforderlich ist, indem Sie eines dieser Kontrollkästchen aktivieren, auf "Alle Vorlagen transformieren" klicken und dann die Projektmappe erstellen. Ein Fehlerbericht wird erstellt. Doppelklicken Sie auf den Fehlerbericht, um einen Kommentar zu lesen, der den hinzuzufügenden Code erläutert.

> [!NOTE]
> Erstellen Sie zum Hinzufügen von benutzerdefiniertem Code eine partielle Klassendefinition in einer Codedatei, die nicht zu den Codedateien in den Ordnern "GeneratedCode" gehört. Damit Ihre Arbeit nicht verloren geht, sollten Sie die generierten Codedateien nicht bearbeiten. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Erstellen von benutzerdefiniertem Verbindungscode
 In jeder Link Verbindungs Direktive definiert die Registerkarte **Quell Rollen Direktiven** , welche Typen Sie ziehen können. Auf ähnliche Weise definiert die Registerkarte **Ziel Rollen Direktiven** , welche Typen Sie ziehen können. Für jeden Typ können Sie angeben, ob die Verbindung zugelassen werden soll (für diese Link Verbindungs Direktive), indem Sie das **benutzerdefinierte Accept** -Flag festlegen und dann den zusätzlichen Code bereitstellen.

 Darüber hinaus können Sie anpassen, was geschieht, wenn die Verbindung hergestellt wird. Sie können beispielsweise nur den Fall anpassen, wenn das Ziehen in eine oder aus einer bestimmten Klasse erfolgt. Sie können aber auch alle Fälle, für die eine Direktive für Linkverbindungen gilt, oder den gesamten FlowBuilder-Verbindungs-Generator anpassen. Für jede dieser Optionen können Sie benutzerdefinierte Flags auf der entsprechenden Ebene festlegen. Wenn Sie alle Vorlagen transformieren und die Projektmappe erstellen, weisen Sie Fehlermeldungen auf Kommentare im generierten Code hin. In diesen Kommentaren werden die erforderlichen Angaben identifiziert.

 Im Komponentendiagrammbeispiel wurde der Verbindungs-Generator für die Domänenbeziehung "Verbindung" angepasst, um die zwischen Ports möglichen Verbindungen zu beschränken. Die folgende Abbildung zeigt, dass Sie nur Verbindungen von `OutPort`-Elementen mit `InPort`-Elementen herstellen können. Zudem können Sie Komponenten ineinander schachteln.

 **Eingehende Verbindung für "OutPort" aus einer geschachtelten Komponente**

 ![Verbindungsgenerator](../modeling/media/connectionbuilder_3.png)

 Daher könnten Sie angeben, dass eine Verbindung aus einer geschachtelten Komponente mit "OutPort" zulässig ist. Um eine solche Verbindung anzugeben, legen Sie im Fenster "DSL-Details" **benutzerdefinierte Annahme** für den **inporttyp** als Quell Rolle und den Typ **Outport** als Zielrolle im Fenster **DSL-Details** fest, wie in der folgenden Abbildung dargestellt:

 **Direktive für Linkverbindungen im DSL-Explorer**

 ![Verbindungsgenerator-Abbild](../modeling/media/connectionbuilder_4a.png)

 **Direktive für Linkverbindungen im Fenster "DSL-Details"**

 ![Link Verbindungs Direktive im Fenster "DSL-Details"](../modeling/media/connectionbuilder_4b.png)

 Dann müssen Sie die Methoden in der ConnectionBuilder-Klasse angeben:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [navigieren und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Sie können ähnlichen Code verwenden, um beispielsweise zu verhindern, dass die Benutzer Schleifen mit Links zwischen übergeordneten und untergeordneten Elementen erstellen. Diese Einschränkungen gelten als "harte" Einschränkungen, da Benutzer Sie nicht jederzeit verletzen können. Sie können auch "weiche" Validierungs Prüfungen erstellen, die Benutzer vorübergehend umgehen können, indem Sie ungültige Konfigurationen erstellen, die Sie nicht speichern können.

### <a name="good-practice-in-defining-connection-builders"></a>Empfehlungen für die Definition von Verbindungs-Generatoren
 Sie sollten einen Verbindungs-Generator definieren, um unterschiedliche Typen von Beziehungen zu erstellen, wenn sie konzeptionell verwandt sind. Im Beispiel des Aufgabenablaufs verwenden Sie einen Generator, um die Abläufe zwischen Aufgaben und zwischen Aufgaben und Objekten zu erstellen. Es kann jedoch verwirrend sein, den gleichen Generator für Beziehungen zwischen Kommentaren und Aufgaben zu verwenden.

 Wenn Sie einen Verbindungs-Generator für mehrere Typen von Beziehungen erstellen, sollten Sie sicherstellen, dass er nicht zu mehr als einem Typ eines Paars von Quell- und Zielobjekten passt. Andernfalls können sich unerwartete Ergebnisse ergeben.

 Mithilfe von benutzerdefiniertem Code können Sie "harte" Einschränkungen anwenden. Sie sollten jedoch berücksichtigen, ob Benutzer in der Lage sein sollen, vorübergehend ungültige Verbindungen herzustellen. In dem Fall können Sie die Beschränkungen so ändern, dass die Verbindungen erst überprüft werden, wenn die Benutzer die Änderungen speichern möchten.

## <a name="see-also"></a>Weitere Informationen

- [Anpassen der Elementerstellung und -verschiebung](../modeling/customizing-element-creation-and-movement.md)
- [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)
- [Gewusst wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Beispiel-DSL für Verbindungs Diagramme](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
