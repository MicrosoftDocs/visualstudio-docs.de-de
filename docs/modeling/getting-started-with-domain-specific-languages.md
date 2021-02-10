---
title: Erste Schritte mit domänenspezifischen Sprachen
description: Erfahren Sie mehr über die grundlegenden Konzepte zum Definieren und Verwenden einer domänenspezifischen Sprache (DSL), die mit dem Modellierungs-SDK für Visual Studio erstellt wurde.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fe531b127d657228ed68fa79358ef5df69ff17c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941488"
---
# <a name="get-started-with-domain-specific-languages"></a>Erste Schritte mit domänenspezifischen Sprachen

In diesem Thema werden die grundlegenden Konzepte zum Definieren und Verwenden einer domänenspezifischen Sprache (DSL) erläutert, die mit dem Modellierungs-SDK für Visual Studio erstellt wurde.

> [!NOTE]
> Das Text Template Transformation SDK und das Visual Studio-Modellierungs-SDK werden automatisch installiert, wenn Sie bestimmte Features von Visual Studio installieren. Weitere Informationen finden Sie in [diesem Blogbeitrag](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Wenn Sie noch nicht mit DSLs vertraut sind, empfiehlt es sich, dass Sie über die **DSL Tools Lab** arbeiten, die Sie auf dieser Website finden: [Visualisierung und Modellierungs-SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) .

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Was können Sie mit einer Domain-Specific Sprache tun?

Bei einer domänenspezifischen Sprache handelt es sich in der Regel um eine grafische Notation, die für einen bestimmten Zweck entwickelt wurde. Im Gegensatz dazu sind Sprachen wie UML universell. In einer DSL können Sie die Typen von Modellelement und deren Beziehungen definieren und angeben, wie diese auf dem Bildschirm angezeigt werden.

Wenn Sie eine DSL entworfen haben, können Sie Sie als Teil eines Visual Studio-Integrations Erweiterungspakets (VSIX) verteilen. Benutzer arbeiten mit der DSL in Visual Studio:

![Stammstrukturdiagramm, Toolbox und Explorer](../modeling/media/familyt_instance.png)

Die Notation ist nur Teil einer DSL. In Verbindung mit der Notation enthält das VSIX-Paket Tools, die Benutzer anwenden können, um Sie beim Bearbeiten und Generieren von Material aus Ihren Modellen zu unterstützen.

Eine der Prinzipal Anwendungen von DSLs besteht darin, Programmcode, Konfigurationsdateien und andere Artefakte zu generieren. Vor allem bei großen Projekten und Produktlinien, in denen mehrere Varianten eines Produkts erstellt werden, kann das Erstellen vieler der Variablen Aspekte aus DSLs eine hohe Steigerung der Zuverlässigkeit und eine sehr schnelle Reaktion auf Anforderungsänderungen zur Folge haben.

Der Rest dieser Übersicht ist eine exemplarische Vorgehensweise, in der die grundlegenden Vorgänge zum Erstellen und Verwenden einer domänenspezifischen Sprache in Visual Studio vorgestellt werden.

## <a name="prerequisites"></a>Voraussetzungen

Zur Definition einer DSL müssen folgende Komponenten installiert sein:

| Komponente | Link |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Modellierungs-SDK für Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Erstellen einer DSL-Lösung

Um eine neue domänenspezifische Sprache zu erstellen, erstellen Sie eine neue Visual Studio-Projekt Mappe, indem Sie die Projektvorlage Domain-Specific-Sprache verwenden.

1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

2. Erweitern Sie unter **Projekttypen** den Knoten **andere Projekttypen** , und klicken Sie auf **Erweiterbarkeit**.

3. Klicken Sie auf **Domänen spezifischer sprach-Designer**.

     ![Dialogfeld "DSL erstellen"](../modeling/media/create_dsldialog.png)

4. Geben Sie im Feld **Name den Namen** **FamilyTree** ein. Klicken Sie auf **OK**.

     Der **Assistent für die domänenspezifische Sprache** wird geöffnet und zeigt eine Liste der Vorlagen-DSL-Lösungen an.

     Klicken Sie auf jede Vorlage, um eine Beschreibung anzuzeigen.

     Die Vorlagen sind nützliche Ausgangspunkte. Jede dieser Komponenten bietet eine komplette funktionierende DSL, die Sie entsprechend Ihren Anforderungen bearbeiten können. Normalerweise würden Sie die Vorlage auswählen, die der nächstgelegenen ist, den Sie erstellen möchten.

5. Wählen Sie für diese exemplarische Vorgehensweise die Vorlage **minimale Sprache** aus.

6. Geben Sie auf der entsprechenden Seite des Assistenten eine Dateinamenerweiterung für die DSL ein. Diese Erweiterung wird für Dateien mit Instanzen Ihrer DSL verwendet.

    - Wählen Sie eine Erweiterung aus, die keiner Anwendung auf dem Computer zugeordnet ist, oder auf einem Computer, auf dem Sie die DSL installieren möchten. **Docx** und **htm** sind z. b. unzulässige Dateinamen Erweiterungen.

    - Der Assistent warnt Sie, wenn die eingegebene Erweiterung bereits als DSL verwendet wird. Verwenden Sie nach Möglichkeit eine andere Dateinamenerweiterung. Sie können die experimentelle Instanz des Visual Studio SDK auch zurücksetzen, um alte experimentelle Designer zu löschen. Klicken Sie auf **Start**, auf **Alle Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und setzen Sie dann **die experimentelle Microsoft Visual Studio 2010-Instanz zurück**.

7. Prüfen Sie die anderen Seiten, und klicken Sie dann auf **Fertig** stellen.

     Eine Projekt Mappe, die zwei Projekte enthält, wird generiert. Sie werden als "DSL" und "dslpackage" bezeichnet. Eine Diagramm Datei mit dem Namen "DslDefinition. DSL" wird geöffnet.

    > [!NOTE]
    > Der größte Teil des Codes, den Sie in den Ordnern der beiden Projekte sehen können, wird aus "DslDefinition. DSL" generiert. Aus diesem Grund werden die meisten Änderungen an ihrer DSL in dieser Datei vorgenommen.

Die Benutzeroberfläche gleicht nun der folgenden Abbildung.

![DSL-Designer](../modeling/media/dsl_designer.png)

Diese Projektmappe definiert eine domänenspezifische Sprache. Weitere Informationen finden Sie unter [Übersicht über die Benutzeroberfläche der Domain-Specific-Sprach Tools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Wichtige Teile der DSL-Lösung

Beachten Sie die folgenden Aspekte der neuen Lösung:

- **Dsl\DslDefinition.DSL** Dies ist die Datei, die Sie beim Erstellen einer DSL-Lösung sehen. Fast der gesamte Code in der Lösung wird aus dieser Datei generiert, und die meisten Änderungen, die Sie an einer DSL-Definition vornehmen, werden hier vorgenommen. Weitere Informationen finden Sie unter Arbeiten mit dem [DSL-Definitions Diagramm](../modeling/working-with-the-dsl-definition-diagram.md).

- **DSL-Projekt** Dieses Projekt enthält Code, der die domänenspezifische Sprache definiert.

- **Dslpackage-Projekt** Dieses Projekt enthält Code, mit dem Instanzen der DSL in Visual Studio geöffnet und bearbeitet werden können.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Ausführen der DSL

Sie können die DSL-Lösung ausführen, sobald Sie Sie erstellt haben. Später können Sie die DSL-Definition schrittweise ändern, indem Sie die Lösung nach jeder Änderung erneut ausführen.

### <a name="to-experiment-with-the-dsl"></a>So experimentieren Sie mit der DSL

1. Klicken Sie in der Symbolleiste **Projektmappen-Explorer** auf **alle Vorlagen transformieren** . Dadurch wird der größte Teil des Quellcodes aus "DslDefinition. DSL" erneut generiert.

    > [!NOTE]
    > Wenn Sie " *DslDefinition. DSL*" ändern, müssen Sie auf **alle Vorlagen transformieren** klicken, bevor Sie die Projekt Mappe neu erstellen. Dieser Schritt kann automatisiert werden. Weitere Informationen finden Sie unter [Automatisieren der Transformation für alle Vorlagen](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. Drücken Sie **F5**, oder klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

     Die DSL erstellt und wird in der experimentellen Instanz von Visual Studio installiert.

     Eine experimentelle Instanz von Visual Studio wird gestartet. Die experimentelle Instanz übernimmt ihre Einstellungen aus einer separaten Unterstruktur der Registrierung, in der Visual Studio-Erweiterungen zu Debuggingzwecken registriert werden. Normale Instanzen von Visual Studio haben keinen Zugriff auf die dort registrierten Erweiterungen.

3. Öffnen Sie in der experimentellen Instanz von Visual Studio die Modelldatei mit dem Namen **Test** aus **Projektmappen-Explorer**.

     \- oder -

     Klicken Sie mit der rechten Maustaste auf das Projekt Debugging, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Element** Wählen Sie im Dialogfeld **Element hinzufügen** den Dateityp Ihrer DSL aus.

     Die Modelldatei wird als leeres Diagramm geöffnet.

     Die Toolbox wird geöffnet und zeigt Tools an, die für den Diagrammtyp geeignet sind.

4. Verwenden Sie die Tools, um Formen und Connectors im Diagramm zu erstellen.

    1. Um Formen zu erstellen, ziehen Sie aus dem Beispiel Formenwerkzeug auf das Diagramm.

    2. Um zwei Formen zu verbinden, klicken Sie auf das Beispiel-Connector-Tool, klicken Sie auf die erste Form, und klicken Sie dann auf die zweite Form.

5. Klicken Sie auf die Bezeichnungen der Formen, um Sie zu ändern.

Das experimentelle Visual Studio ähnelt dem folgenden Beispiel:

![Beispiel Struktur für eine domänenspezifische Sprache in Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Der Inhalt eines Modells.

Der Inhalt einer Datei, die eine Instanz einer DSL ist, wird als *Modell* bezeichnet. Das Modell enthält *Modell* <em>Elemente</em> und *Links* zwischen den Elementen. Die DSL-Definition gibt an, welche Typen von Modellelementen und Verknüpfungen im Modell vorhanden sein können. Beispielsweise gibt es in einer DSL, die aus der Vorlage mit minimaler Sprache erstellt wurde, einen Typ von Modellelement und einen Linktyp.

Die DSL-Definition kann angeben, wie das Modell in einem Diagramm angezeigt wird. Sie können aus einer Vielzahl von Formen und Connectors auswählen. Sie können angeben, dass einige Formen in anderen Formen angezeigt werden.

Sie können ein Modell als Baumstruktur in der **Explorer** -Ansicht anzeigen, während Sie ein Modell bearbeiten. Wenn Sie dem Diagramm Formen hinzufügen, werden die Modellelemente auch im Explorer angezeigt. Der Explorer kann auch dann verwendet werden, wenn kein Diagramm vorhanden ist.

Wenn der Explorer in der debugginginstanz von Visual Studio nicht angezeigt wird, zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf *\<Your Language>* **Explorer**.

### <a name="the-api-of-your-dsl"></a>Die API ihrer DSL

Ihre DSL generiert eine API, mit der Sie Modelle lesen und aktualisieren können, bei denen es sich um Instanzen der DSL handelt. Eine Anwendung der API besteht darin, Textdateien aus einem Modell zu generieren. Weitere Informationen finden Sie unter [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Öffnen Sie in der Projekt Mappe Debuggen die Vorlagen Dateien mit der Erweiterung ". tt". Diese Beispiele veranschaulichen, wie Sie Text aus Modellen generieren können, und Sie können die API ihrer DSL testen. Eines der Beispiele ist in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , das andere in, geschrieben [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

Unter jeder Vorlagen Datei befindet sich die Datei, die Sie generiert. Erweitern Sie die Vorlagen Datei in Projektmappen-Explorer, und öffnen Sie die generierte Datei.

Die Vorlagen Datei enthält ein kurzes Codesegment, das alle Elemente im Modell auflistet.

Die generierte Datei enthält das Ergebnis.

Wenn Sie eine Modelldatei ändern, werden nach dem erneuten Generieren der Dateien entsprechende Änderungen in generierten Dateien angezeigt.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>So generieren Sie Textdateien nach dem Ändern der Modelldatei erneut

1. Speichern Sie in der experimentellen Instanz von Visual Studio die Modelldatei.

2. Stellen Sie sicher, dass sich der Dateiname-Parameter in jeder Tt-Datei auf die Modelldatei bezieht, die Sie für Experimente verwenden. Speichern Sie die TT-Datei.

3. Klicken Sie in der Symbolleiste von **Projektmappen-Explorer** auf **alle Vorlagen transformieren** .

     \- oder -

     Klicken Sie mit der rechten Maustaste auf die zu generierenden Vorlagen, und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**

Sie können einem Projekt beliebig viele Textvorlagen Dateien hinzufügen. Jede Vorlage generiert eine Ergebnisdatei.

> [!NOTE]
> Wenn Sie die DSL-Definition ändern, funktioniert der Code der Beispiel Textvorlage nicht, es sei denn, Sie aktualisieren ihn.

Weitere Informationen finden Sie unter [Erstellen von Code aus einer Domain-Specific Sprache](../modeling/generating-code-from-a-domain-specific-language.md) und [Schreiben von Code zum Anpassen einer Domain-Specific Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>Anpassen der DSL

Wenn Sie die DSL-Definition ändern möchten, schließen Sie die experimentelle Instanz, und aktualisieren Sie die Definition in der Visual Studio-Haupt Instanz.

> [!NOTE]
> Nachdem Sie die DSL-Definition geändert haben, verlieren Sie möglicherweise Informationen in den Testmodellen, die Sie mit früheren Versionen erstellt haben.  Die Projekt Mappe zum Debuggen enthält z. b. eine Datei mit dem Namen Sample, die einige Formen und Connectors enthält. Nachdem Sie mit der Entwicklung ihrer DSL-Definition begonnen haben, sind Sie nicht sichtbar, und Sie gehen verloren, wenn Sie die Datei speichern.

Sie können eine Vielzahl von Erweiterungen für Ihre DSL erstellen. In den folgenden Beispielen erhalten Sie einen Eindruck von den Möglichkeiten.

Speichern Sie nach jeder Änderung die DSL-Definition, klicken Sie in **Projektmappen-Explorer** auf **alle Vorlagen transformieren** , und drücken Sie dann **F5** , um mit der geänderten DSL zu experimentieren.

### <a name="rename-the-types-and-tools"></a>Umbenennen von Typen und Tools

Umbenennen der vorhandenen Domänen Klassen und-Beziehungen. Beispielsweise können Sie mit einer DSL-Definition, die aus der Vorlage für minimale Sprache erstellt wurde, die folgenden Umbenennungs Vorgänge durchführen, um die DSL als Familienstrukturen darzustellen.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>So benennen Sie Domänen Klassen, Beziehungen und Tools um

1. Benennen Sie im DslDefinition-Diagramm **examplemodel** in **familytreemodel**, **ExampleElement** in **Person**, **Targets** to **Parents** und **Sources** to **Children** um. Sie können auf jede Bezeichnung klicken, um Sie zu ändern.

     ![DSL-Definitions Diagramm &#45; Familienstruktur Modell](../modeling/media/familyt_person.png)

2. Benennen Sie das Element und die Connector-Tools um.

    1. Öffnen Sie das Fenster DSL-Explorer, indem Sie auf die Registerkarte unter Projektmappen-Explorer klicken. Wenn diese Option nicht angezeigt wird, zeigen Sie im Menü **Ansicht** auf **Weitere Fenster** , und klicken Sie dann auf **DSL-Explorer**. Der DSL-Explorer ist nur sichtbar, wenn das DSL-Definitions Diagramm das aktive Fenster ist.

    2. Öffnen Sie die Eigenschaftenfenster, und positionieren Sie Sie, damit Sie den DSL-Explorer und die Eigenschaften gleichzeitig sehen können.

    3. Erweitern Sie im DSL-Explorer **Editor**, **Toolbox-Registerkarten**, *\<your DSL>* und dann **Tools**.

    4. Klicken Sie auf **ExampleElement**. Dies ist das Toolbox Element, das verwendet wird, um-Elemente zu erstellen.

    5. Ändern Sie im Eigenschaftenfenster die Eigenschaft **Name** in **Person**.

         Beachten Sie, dass sich auch die **Caption** -Eigenschaft ändert.

    6. Ändern Sie auf dieselbe Weise den Namen des Tools **exampleconnector** in " **parameentlink**". Ändern Sie die **Caption** -Eigenschaft so, dass es sich nicht um eine Kopie der Name-Eigenschaft handelt. Geben Sie z. b. den über **geordneten Link** ein.

3. Erstellen Sie die DSL neu.

    1. Speichern Sie die DSL-Definitionsdatei.

    2. Klicken Sie in der Symbolleiste von auf **alle Vorlagen transformieren** Projektmappen-Explorer

    3. Drücken Sie F5. Warten Sie, bis die experimentelle Instanz von Visual Studio angezeigt wird.

4. Öffnen Sie in der Projekt Mappe Debuggen in der experimentellen Instanz von Visual Studio eine Testmodell Datei. Ziehen Sie Elemente aus der Toolbox auf die Datei. Beachten Sie, dass sich die Tool Beschriftungen und die Typnamen im DSL-Explorer geändert haben.

5. Speichern Sie die Modelldatei.

6. Öffnen Sie eine TT-Datei, und ersetzen Sie die Vorkommen der alten Typen-und Eigenschaftsnamen durch die neuen Namen.

7. Stellen Sie sicher, dass der Dateiname, der in der TT-Datei angegeben ist, das Testmodell angibt.

8. Speichern Sie die TT-Datei. Öffnen Sie die generierte Datei, um das Ergebnis der Ausführung des Codes in der TT-Datei anzuzeigen. Vergewissern Sie sich, dass es korrekt ist.

### <a name="add-domain-properties-to-classes"></a>Hinzufügen von Domänen Eigenschaften zu Klassen
 Hinzufügen von Eigenschaften zu einer Domänen Klasse, z. b. um die Jahre der Geburt und den Tod einer Person darzustellen.

 Um die neuen Eigenschaften im Diagramm sichtbar zu machen, müssen Sie der Form, in der das Modellelement angezeigt wird, *Decorator* hinzufügen. Außerdem müssen Sie die Eigenschaften den Decorators zuordnen.

##### <a name="to-add-properties-and-display-them"></a>So fügen Sie Eigenschaften hinzu und zeigen Sie an

1. Fügen Sie die Eigenschaften hinzu.

   1. Klicken Sie im DSL-Definitions Diagramm mit der rechten Maustaste auf die Domänen Klasse **Person** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Domänen Eigenschaft**.

   2. Geben Sie eine Liste von neuen Eigenschaften Namen ein, z. b. **Geburts** -und **sterbe** Namen. Drücken **Sie** nach jeder Eingabe die EINGABETASTE.

2. Fügen Sie Decorator hinzu, die die Eigenschaften in der Form anzeigen.

   1. Befolgen Sie die graue Linie, die sich von der Person-Domänen Klasse bis zur anderen Seite des Diagramms erstreckt. Dies ist eine Diagramm Element Zuordnung. Die Domänen Klasse wird mit einer Shape-Klasse verknüpft.

   2. Klicken Sie mit der rechten Maustaste auf diese Form Klasse, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Text Decorator**

   3. Fügen Sie zwei Decorator mit Namen wie **birthdecorator** und **deathdecorator** hinzu.

   4. Wählen Sie jeden neuen Decorator aus, und legen Sie im Eigenschaftenfenster das **Positions** Feld fest. Dadurch wird bestimmt, wo der Domänen Eigenschafts Wert in der Form angezeigt wird. Legen Sie z. b. **InnerBottomLeft** und **InnerBottomRight** fest.

        ![Definition einer Depot-Form](../modeling/media/familyt_compartment.png)

3. Ordnen Sie die Decorator den Eigenschaften zu.

   1. Öffnen Sie das Fenster DSL-Details. Sie befindet sich normalerweise auf einer Registerkarte neben dem Ausgabefenster. Wenn diese Option nicht angezeigt wird, zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **DSL-Details**.

   2. Klicken Sie im DSL-Definitions Diagramm auf die Linie, die die **Person** -Domänen Klasse mit der Shape-Klasse verbindet.

   3. Klicken Sie in **DSL-Details** auf der Registerkarte **Decorator** -Zuordnungen auf das Kontrollkästchen für einen nicht zugeordneten Decorator. Wählen Sie unter **Anzeige Eigenschaft** die Domänen Eigenschaft aus, der Sie zugeordnet werden soll. Ordnen Sie z. b. **birthdecorator** der **Geburts** Datei zu.

4. Speichern Sie die DSL, klicken Sie auf alle Vorlagen transformieren, und drücken Sie F5.

5. Überprüfen Sie in einem Beispielmodell Diagramm, ob Sie nun auf die gewählten Positionen klicken und Werte in diese eingeben können. Wenn Sie eine Form vom Typ **Person** auswählen, werden die neuen Eigenschaften im Eigenschaftenfenster angezeigt.

6. In einer TT-Datei können Sie Code hinzufügen, der die Eigenschaften jeder Person abruft.

   ![Stammstrukturdiagramm, Toolbox und Explorer](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definieren neuer Klassen
 Sie können Domänen Klassen und Beziehungen einem Modell hinzufügen. Sie können z. b. eine neue Klasse erstellen, um Städte darzustellen, und eine neue Beziehung darstellen, die darstellt, dass eine Person in einer Stadt gelebt hat.

 Um die unterschiedlichen Typen in einem Modell Diagramm zu unterscheiden, können Sie die Domänen Klassen verschiedenen Arten von Formen oder Formen mit unterschiedlichen Geometrie und Farben zuordnen.

##### <a name="to-add-and-display-a-new-domain-class"></a>So können Sie eine neue Domänen Klasse hinzufügen und anzeigen

1. Fügen Sie eine Domänen Klasse hinzu, und machen Sie Sie zu einem untergeordneten Modell Stamm.

    1. Klicken Sie im DSL-Definitions Diagramm auf das Tool **Einbettungs Beziehung** , klicken Sie auf die Stamm Klasse **familytreemodel**, und klicken Sie dann auf einen leeren Teil des Diagramms.

         Eine neue Domänen Klasse wird angezeigt, die mit dem familytreemodel mit einem Embedding Relationship verbunden ist.

         Legen Sie seinen Namen fest, z. b. **Stadt**.

        > [!NOTE]
        > Jede Domänen Klasse mit Ausnahme des Stamm des Modells muss das Ziel mindestens eines Embedding Relationship sein, oder Sie muss von einer Klasse erben, die das Ziel einer Einbettung ist. Aus diesem Grund ist es häufig sinnvoll, mit dem Einbettungs Beziehungs Tool eine Domänen Klasse zu erstellen.

    2. Fügen Sie der neuen Klasse eine Domänen Eigenschaft hinzu, z. b. " **Name**".

2. Fügen Sie eine Verweis Beziehung zwischen Person und Stadt hinzu.

    1. Klicken Sie auf das Tool **Verweis Beziehung** , klicken Sie auf Person und dann auf Stadt.

         ![DSL-Definitionsfragment: Stammbaumstamm](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Verweis Beziehungen stellen Querverweise von einem Teil der Modellstruktur zu einem anderen dar.

3. Fügen Sie eine Form hinzu, um Städte in den Modell Diagrammen darzustellen.

    1. Ziehen Sie eine **Form Geometrie** aus der Toolbox in das Diagramm, und benennen Sie Sie um, z. b. **townshape**.

    2. Legen Sie im Eigenschaftenfenster die Darstellungs Felder der neuen Form fest, z. b. Füllfarbe und Geometrie.

    3. Fügen Sie einen Decorator hinzu, um den Namen der Stadt anzuzeigen, und benennen Sie ihn namedecorator um. Legen Sie die Positions Eigenschaft fest.

4. Ordnen Sie die Domänen Klasse Stadt dem townshape zu.

    1. Klicken Sie auf das **Diagramm Element Map** -Tool, und klicken Sie dann auf die Domänen Klasse Town und dann auf die Form Klasse townform.

    2. Aktivieren Sie auf der Registerkarte **Decorator** -Zuordnungen des Fensters **DSL-Details** mit ausgewähltem Karten-Connector die Option namedecorator, und legen Sie **Anzeige Eigenschaft** auf Name fest.

5. Erstellen Sie einen Connector, um die Beziehung zwischen Personen und Städten anzuzeigen.

    1. Ziehen Sie einen Connector aus der Toolbox in das Diagramm. Benennen Sie Sie um, und legen Sie die Darstellungs Eigenschaften

    2. Verwenden Sie das **Diagramm Element Map** -Tool, um den neuen Connector mit der Beziehung zwischen "Person" und "Stadt" zu verknüpfen.

         ![Stammbaumdefinition mit Formzuordnung](../modeling/media/familyt_shapemap.png)

6. Erstellen Sie ein Element Tool zum Erstellen einer neuen Stadt.

    1. Erweitern Sie im **DSL-Explorer** den Bereich **Editor** und dann **Registerkarten**.

    2. Klicken Sie mit der rechten Maustaste, *\<your DSL>* und klicken Sie dann auf **Add New Element Tool**

    3. Legen Sie die **Name** -Eigenschaft des neuen Tools fest, und legen Sie die zugehörige **Class** -Eigenschaft auf Town fest.

    4. Legen Sie die **Toolbox Icon** -Eigenschaft fest. Klicken Sie auf **[...]** , und wählen Sie im Feld **Dateiname** eine Symbol Datei aus.

7. Erstellen Sie ein Connector-Tool, um eine Verknüpfung zwischen Städten und Personen herzustellen.

    1. Klicken Sie mit der rechten Maustaste, *\<your DSL>* und klicken Sie dann auf **Add New Connector Tool**

    2. Legen Sie die Name-Eigenschaft des neuen Tools fest.

    3. Wählen Sie in der **connectionbuilder** -Eigenschaft den Generator aus, der den Namen der Person-Town Beziehung enthält.

    4. Legen Sie das **Toolbox Symbol** fest.

8. Speichern Sie die DSL-Definition, klicken Sie auf **alle Vorlagen transformieren**, und drücken Sie dann **F5**.

9. Öffnen Sie in der experimentellen Instanz von Visual Studio eine Testmodell Datei. Mit den neuen Tools können Sie Städte und Verknüpfungen zwischen Städten und Personen erstellen. Beachten Sie, dass Sie nur Links zwischen den richtigen Elementtypen erstellen können.

10. Erstellen Sie Code, der die Stadt auflistet, in der sich die einzelnen Personen befinden. Text Vorlagen sind eine der Orte, an denen Sie diesen Code ausführen können. Beispielsweise können Sie die vorhandene Sample.tt-Datei in der debugginglösung ändern, sodass Sie den folgenden Code enthält:

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     Beim Speichern der TT-Datei wird eine untergeordnete Datei erstellt, die die Liste der Personen und deren Wohnsitz enthält. Weitere Informationen finden Sie unter [Erstellen von Code aus einer Domain-Specific Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Validierung und Befehle
 Sie können diese DSL weiterentwickeln, indem Sie Validierungs Einschränkungen hinzufügen. Diese Einschränkungen sind Methoden, die Sie definieren können, um sicherzustellen, dass sich das Modell in einem ordnungsgemäßen Zustand befindet. Sie können z. b. eine Einschränkung definieren, um sicherzustellen, dass das Geburtsdatum eines untergeordneten Elements höher als das der übergeordneten Elemente ist. Das Validierungs Feature zeigt eine Warnung an, wenn der DSL-Benutzer versucht, ein Modell zu speichern, das eine der Einschränkungen unterbricht. Weitere Informationen finden Sie unter [Validierung in einer Domain-Specific Sprache](../modeling/validation-in-a-domain-specific-language.md).

 Sie können auch Menübefehle definieren, die der Benutzer aufrufen kann. Befehle können das Modell ändern. Sie können auch mit anderen Modellen in Visual Studio und externen Ressourcen interagieren. Weitere Informationen finden Sie unter Gewusst [wie: Ändern eines Standard Menübefehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Bereitstellen der DSL
 Um anderen Benutzern die Verwendung der domänenspezifischen Sprache zu gestatten, verteilen Sie eine Visual Studio-Erweiterungs Datei (VSIX). Diese wird erstellt, wenn Sie die DSL-Projekt Mappe erstellen.

 Suchen Sie die vsix-Datei im Ordner "bin" der Projekt Mappe. Kopieren Sie die Datei auf den Computer, auf dem Sie Sie installieren möchten. Doppelklicken Sie auf diesem Computer auf die vsix-Datei. Die DSL kann in allen Instanzen von Visual Studio auf diesem Computer verwendet werden.

 Sie können das gleiche Verfahren verwenden, um die DSL auf Ihrem eigenen Computer zu installieren, sodass Sie die experimentelle Instanz von Visual Studio nicht verwenden müssen.

 Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Alte experimentelle DSLs entfernen
 Wenn Sie experimentelle DSLs erstellt haben, die Sie nicht mehr möchten, können Sie Sie von Ihrem Computer entfernen, indem Sie die experimentelle Instanz von Visual Studio zurücksetzen.

 Hierdurch werden alle experimentellen DSLs und anderen experimentellen Visual Studio-Erweiterungen von Ihrem Computer entfernt. Dabei handelt es sich um Erweiterungen, die im Debugmodus ausgeführt wurden.

 Diese Prozedur entfernt keine DSLs oder anderen Visual Studio-Erweiterungen, die durch Ausführen der VSIX-Datei vollständig installiert wurden.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>So setzen Sie die experimentelle Instanz von Visual Studio zurück

1. Klicken Sie auf **Start**, auf **Alle Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und setzen Sie dann **die experimentelle Microsoft Visual Studio 2010-Instanz zurück**.

2. Erstellen Sie beliebige experimentelle DSLs oder andere experimentelle Visual Studio-Erweiterungen neu, die Sie weiterhin verwenden möchten.

## <a name="see-also"></a>Weitere Informationen

- [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)
- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
