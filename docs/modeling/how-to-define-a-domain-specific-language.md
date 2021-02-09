---
title: So definieren Sie eine domänenspezifische Sprache
description: Erfahren Sie, wie Sie eine Visual Studio-Projekt Mappe aus einer Vorlage erstellen, um eine domänenspezifische Sprache (DSL) zu definieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 440d2f42fb7967ebbcb97433c3faa55e2d91ca0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903939"
---
# <a name="how-to-define-a-domain-specific-language"></a>So definieren Sie eine domänenspezifische Sprache
Um eine domänenspezifische Sprache (DSL) zu definieren, erstellen Sie eine Visual Studio-Projekt Mappe aus einer Vorlage. Der zentrale Bestandteil der Projektmappe ist das DSL-Definitionsdiagramm, das in "DslDefinition.dsl" gespeichert wird. Die DSL-Definition definiert die Klassen und Formen der DSL. Nachdem Sie diese Elemente geändert und weitere hinzugefügt haben, können Sie Programmcode hinzufügen, um die DSL weiter anzupassen.

Wenn Sie noch nicht mit DSLs vertraut sind, empfiehlt es sich, dass Sie über die **DSL Tools Lab** arbeiten, die Sie auf dieser Website finden: [Visualisierung und Modellierungs-SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) .

## <a name="selecting-a-template-solution"></a><a name="templates"></a> Auswählen einer Vorlagen Lösung

Zur Definition einer DSL müssen folgende Komponenten installiert sein:

- Visual Studio
- Visual Studio-Erweiterungs Entwicklung (enthält das Visual Studio SDK)
- Modellierungs-SDK (installieren Sie es als einzelne Komponente in Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Um eine neue domänenspezifische Sprache zu erstellen, erstellen Sie eine neue Visual Studio-Projekt Mappe mithilfe der Projektvorlage Domain-Specific-Sprache.

### <a name="to-create-a-dsl-solution"></a>So erstellen Sie eine DSL-Projektmappe

1. Erstellen Sie ein neues **Domänen spezifisches sprach** Projekt.

   ::: moniker range="vs-2017"

    ![Dialogfeld "DSL erstellen"](../modeling/media/create_dsldialog.png)

   ::: moniker-end

    Der **Assistent für die domänenspezifische Sprache** wird geöffnet und zeigt eine Liste der Vorlagen-DSL-Lösungen an.

2. Klicken Sie auf die einzelnen Vorlagen, um eine Beschreibung anzuzeigen. Wählen Sie die Projektmappe aus, die Ihren Vorstellungen am nächsten kommt.

    Jede DSL-Vorlage definiert eine grundlegende, funktionsfähige DSL. Sie bearbeiten diese DSL nach Ihren Anforderungen.

    Klicken Sie auf die Beispiele, um weitere Informationen anzuzeigen.

   - Wählen Sie **Aufgaben Fluss** aus, um eine DSL mit Verantwortlichkeits Bereichen zu erstellen. Verantwortlichkeitsbereiche sind vertikale oder horizontale Bereiche des Diagramms.

   - Wählen Sie **Komponentenmodelle** aus, um eine DSL mit Ports zu erstellen. Anschlüsse sind kleine Formen am Rand einer größeren Form.

   - Wählen Sie **Klassendiagramme** aus, um eine DSL mit Depot-Formen zu definieren. Depot-Formen enthalten Listen von Elementen.

   - Wählen Sie in anderen Fällen **minimale Sprache** aus, oder wenn Sie unsicher sind.

   - Wählen Sie **minimaler WinForm-Designer** oder **minimaler WPF-Designer** , um eine DSL zu erstellen, die auf einer Windows Forms-oder WPF-Oberfläche angezeigt wird. Sie müssen Code zur Definition des Editors schreiben. Weitere Informationen finden Sie unter den folgenden Themen:

        [Erstellen einer Windows Forms-basierten domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Erstellen einer WPF-basierten domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Geben Sie auf der entsprechenden Seite des Assistenten eine Dateinamenerweiterung für die DSL ein. Diese Erweiterung wird für Dateien mit Instanzen Ihrer DSL verwendet.

   - Wählen Sie eine Dateinamenerweiterung, die keiner Anwendung auf Ihrem Computer bzw. auf einem Computer, auf dem Sie die DSL installieren möchten, zugeordnet ist. **Docx** und **htm** sind z. b. unzulässige Dateinamen Erweiterungen.

   - Der Assistent warnt Sie, wenn die eingegebene Erweiterung bereits als DSL verwendet wird. Verwenden Sie nach Möglichkeit eine andere Dateinamenerweiterung. Sie können die experimentelle Instanz des Visual Studio SDK auch zurücksetzen, um alte experimentelle Designer zu löschen. Klicken Sie auf **Start**, auf **Alle Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und setzen Sie dann **die experimentelle Microsoft Visual Studio 2010-Instanz zurück**.

4. Auf den anderen Seiten können Sie Einstellungen anpassen oder die Standardwerte übernehmen.

5. Klicken Sie auf **Fertig stellen**.

    Der Assistent erstellt eine Projektmappe mit zwei oder drei Projekten und generiert Code aus der DSL-Definition.

   Die Benutzeroberfläche gleicht nun der folgenden Abbildung.

   ![DSL-Designer](../modeling/media/dsl_designer.png)

   Diese Projektmappe definiert eine domänenspezifische Sprache. Weitere Informationen finden Sie unter [Übersicht über die Benutzeroberfläche der Domain-Specific-Sprach Tools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testen der Projektmappe
 Die Vorlagenprojektmappe enthält eine funktionsfähige DSL, die Sie ändern oder direkt verwenden können.

 Drücken Sie F5 oder STRG+F5, um die Projektmappe zu testen. Eine neue Instanz von Visual Studio wird im experimentellen Modus geöffnet.

 Öffnen Sie in der neuen Instanz von Visual Studio in Projektmappen-Explorer die Beispieldatei. Sie wird als Diagramm mit einem Werkzeugkasten geöffnet.

 Wenn Sie eine Projekt Mappe ausführen, die Sie aus der Vorlage für **minimale Sprache** erstellt haben, ähnelt die experimentelle Visual Studio-Vorlage dem folgenden Beispiel:

 ![Beispiel Struktur für eine domänenspezifische Sprache in Visual Studio](../modeling/media/dsl_min.png)

 Experimentieren Sie mit den Werkzeugen. Erstellen Sie Elemente, und verbinden Sie sie.

 Schließen Sie die experimentelle Instanz von Visual Studio.

> [!NOTE]
> Wenn Sie die DSL geändert haben, können Sie die Formen in der "Sample"-Testdatei nicht mehr sehen. Sie können aber neue Elemente erstellen.

### <a name="modifying-the-template-dsl"></a>Ändern der Vorlagen-DSL
 Benennen Sie einige oder alle Domänenklassen und Formklassen der Vorlagen-DSL-Definition um, und behalten Sie sie bei. Die neuen Klassennamen sollten gültige CLR-Namen ohne Leerzeichen oder Interpunktionszeichen sein.

 Die Beibehaltung der folgenden Klassen ist besonders sinnvoll:

- Die Stamm Klasse wird links oben im DSL-Definitions Diagramm unter **Klassen und Beziehungen** angezeigt. Benennen Sie sie in einen von der DSL verschiedenen Namen um. Beispielsweise könnte eine DSL mit dem Namen " **musiclibrary** " eine Stamm Klasse mit dem Namen " **Music**" aufweisen.

- Die Diagramm Klasse wird in der Spalte **Diagramm Elemente** in der unteren rechten Ecke des DSL-Definitions Diagramms angezeigt. Möglicherweise müssen Sie einen Bildlauf nach rechts durchführen, um sie zu sehen. Sie wird in der Regel als _yourdsl_-**Diagramm** bezeichnet.

- Wenn Sie die **Task Fluss** Vorlage verwendet haben und Diagramme mit Verantwortlichkeits Bereichen erstellen möchten, müssen Sie die Actor-Domänen Klasse und die actorswimlane-Form beibehalten und umbenennen.

  Löschen Sie andere Klassen nach Bedarf, oder benennen Sie sie um.

## <a name="patterns-for-defining-a-dsl"></a><a name="patterns"></a> Muster zum Definieren einer DSL
 Es ist empfehlenswert, beim Entwickeln einer DSL nur jeweils ein oder zwei Features gleichzeitig hinzuzufügen bzw. anzupassen. Fügen Sie ein Feature hinzu, führen Sie die DSL aus und testen Sie sie. Fügen Sie dann ein oder zwei weitere Features hinzu. Ein typisches Feature Ihrer DSL könnte folgendermaßen aussehen:

- Eine Domänenklasse, die einbettende Beziehung, die das Element mit dem Modell verbindet, die erforderliche Form zum Anzeigen von Elementen der Klasse im Diagramm sowie das Elementwerkzeug, mit dem Benutzer Elemente erstellen können.

- Die Domäneneigenschaften einer Domänenklasse und die Decorator-Elemente, die sie in einer Form anzeigen.

- Eine Verweisbeziehung und der Konnektor, der sie im Diagramm anzeigt, sowie das Konnektorwerkzeug, mit dem Benutzer Verbindungen erstellen können.

- Eine Anpassung, die Programmcode erfordert, wie z. B. eine Validierungseinschränkung oder ein Menübefehl.

  In den folgenden Abschnitten wird die Erstellung der nützlichsten DSL-Features beschrieben. Es gibt viele andere Muster, nach denen eine DSL erstellt werden kann, aber die folgenden sind die gängigsten.

> [!NOTE]
> Wenn Sie ein Feature hinzugefügt haben, vergessen Sie nicht, auf **alle Vorlagen transformieren** in der Symbolleiste von Projektmappen-Explorer zu klicken, bevor Sie die DSL erstellen und ausführen.

 In der folgenden Abbildung sind die Klassen und Beziehungen der DSL dargestellt, die in diesem Thema als Beispiel verwendet wird.

 ![Einbetten von und Verweisen auf Beziehungen](../modeling/media/music_classes.png)

 Die nächste Abbildung zeigt ein Beispielmodell dieser DSL:

 ![Instanzmodell für generierte DSL](../modeling/media/music_instance.png)

> [!NOTE]
> "Modell" bezieht sich auf eine Instanz Ihrer DSL, die Benutzer erstellen. Sie wird üblicherweise als Diagramm dargestellt. In diesem Thema werden das DSL-Definitionsdiagramm und die Modelldiagramme erläutert, die bei Verwendung der DSL angezeigt werden.

## <a name="defining-domain-classes"></a><a name="classes"></a> Definieren von Domänen Klassen
 Domänenklassen stellen die Konzepte der DSL dar. Die Instanzen sind *Modellelemente*. Beispielsweise können Sie in einer **Musik von musiclibrary** Domänen Klassen mit dem Namen " **Album** " und " **Song**" haben.

 Wenn Sie eine Domänen Klasse erstellen möchten, können Sie Sie aus dem **benannten Domänen Klassen** Tool in das Diagramm ziehen und dann die Klasse umbenennen.

 Weitere Informationen finden Sie unter [Eigenschaften von Domänen Klassen](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Erstellen einer einbettenden Beziehung für jede Domänenklasse
 Jede Domänenklasse mit Ausnahme der Stammklasse muss Ziel mindestens einer einbettenden Beziehung sein, oder sie muss von einer Klasse erben, die Ziel einer einbettenden Beziehung ist.

 Jedes Modellelement in einem Modell ist ein Knoten in einer einzelnen Struktur einbettender Beziehungen. Quelle und Ziel einer einbettenden Beziehung werden häufig als übergeordnetes und untergeordnetes Element bezeichnet.

 Die Auswahl eines übergeordneten Elements für eine Domänenklasse hängt davon ab, wie die Lebensdauer ihrer Elemente von anderen Elementen abhängen soll. Wenn ein Knoten einer Struktur gelöscht wird, wird auch seine Unterstruktur gelöscht. Daher werden Klassen von Elementen, deren Existenz nicht von anderen abhängt, direkt unter der Stammklasse eingebettet.

 Wenn Sie ein Element innerhalb eines anderen Elements anzeigen, möchten Sie normalerweise eine Besitzerbeziehung darstellen. In diesem Fall wird als übergeordnete Klasse am besten die Klasse des Containers gewählt. Dies gilt jedoch nicht, wenn das in einem Container dargestellte Element tatsächlich nur ein Verweislink auf ein unabhängiges Element ist. In diesem Fall wird beim Löschen des Containers der Verweis gelöscht, aber nicht sein Ziel.

 In den hier beschriebenen DSL-Definitionsmustern wird vorausgesetzt, dass beim Löschen eines Containers die in dem Container dargestellten Elemente ebenfalls gelöscht werden. Komplexere Schemas können durch Definieren von Regeln erzielt werden.

|Darstellung des Elements|Übergeordnete (einbettende) Klasse|Beispiel in DSL-Projektmappenvorlage|
|-|-|-|
|Form im Diagramm<br /><br /> Verantwortlichkeitsbereich|Stammklasse der DSL|Minimale Sprache<br /><br /> Aufgabenfluss: Actor-Klasse|
|Form in Verantwortlichkeitsbereich|Domänenklasse von Elementen, die als Verantwortlichkeitsbereiche dargestellt werden.|Aufgabenfluss: Task-Klasse|
|Element in Liste in Form, das zusammen mit Container gelöscht wird.<br /><br /> Anschluss am Rand einer Form|Der Containerform zugeordnete Domänenklasse|Klassendiagramm: Attribute-Klasse<br /><br /> Komponentendiagramm: Port-Klasse|
|Element in Liste, nicht zusammen mit Container gelöscht|Stammklasse der DSL<br /><br /> Die Liste enthält Verweislinks.||
|Nicht direkt angezeigt|Die Klasse, von der es Bestandteil ist||

 Im Beispiel "Musikbibliothek" werden Alben als Rechtecke dargestellt, in denen die Titel von Songs aufgelistet sind. Daher ist das übergeordnete Element von "Album" die Stammklasse "Musik", und das übergeordnete Element von "Song" ist "Album".

 Wenn Sie eine Domänen Klasse und die zugehörige Einbettung gleichzeitig erstellen möchten, klicken Sie auf das Tool **Einbettungs Beziehung** , klicken Sie dann auf die übergeordnete Klasse, und klicken Sie dann auf einen leeren Bereich des Diagramms.

 In der Regel müssen Sie den Namen der einbettenden Beziehung und ihrer Rollen nicht anpassen, da automatisch die Klassennamen verwendet werden.

 Weitere Informationen finden Sie unter [Eigenschaften von Domänen Beziehungen](../modeling/properties-of-domain-relationships.md) und [Eigenschaften von Domänen Rollen](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Einbettung ist nicht identisch mit Vererbung. Die untergeordneten Elemente in einer einbettenden Beziehung erben keine Features von ihren übergeordneten Elementen.

### <a name="add-domain-properties-to-each-domain-class"></a>Hinzufügen von Domäneneigenschaften zu den einzelnen Domänenklassen
 In Domäneneigenschaften werden Werte gespeichert. Beispiele: Name, Titel, Veröffentlichungsdatum.

 Klicken Sie in der-Klasse auf **Domänen Eigenschaften** , drücken Sie die EINGABETASTE, und geben Sie dann den Namen einer Eigenschaft ein. Der Standardtyp einer Domäneneigenschaft lautet String. Wenn Sie den Typ ändern möchten, wählen Sie die Domänen Eigenschaft aus, und legen Sie den **Typ** im **Eigenschaften** Fenster fest. Wenn der gewünschte Typ nicht in der Dropdown Liste enthalten ist, finden Sie weitere Informationen unter [Hinzufügen von Eigenschafts Typen](#addTypes).

 **Legen Sie eine Eigenschaft als Elementnamen fest.**  Wählen Sie eine Domäneneigenschaft aus, mit der Elemente im Sprach-Explorer identifiziert werden können. Beispielsweise könnten Sie in der "Song"-Domänenklasse die "Titel"-Domäneneigenschaft auswählen. Legen Sie im **Eigenschaften** Fenster **is Element Name** auf fest `true` .

### <a name="create-derived-domain-classes"></a>Erstellen abgeleiteter Domänenklassen
 Soll eine Domänenklasse Varianten aufweisen, die ihre Eigenschaften und Beziehungen erben, erstellen Sie von der Domänenklasse abgeleitete Klassen. "Album" könnte z. B. die abgeleiteten Klassen WMA und MP3 haben.

 Erstellen Sie die abgeleitete Klasse mit dem **Domänen Klassen** Tool.

 Klicken Sie auf das **Vererbungs** Tool, klicken Sie auf die abgeleitete Klasse und dann auf die Basisklasse.

 Legen Sie den **Vererbungsmodifizierer** der Basisklasse auf **abstract** fest. Wenn Sie voraussichtlich Instanzen der Basisklasse benötigen, können Sie stattdessen eine gesonderte abgeleitete Klasse für diese erstellen.

 Abgeleitete Klassen erben die Eigenschaften und Rollen ihrer Basisklassen.

### <a name="tidy-the-dsl-definition-diagram"></a>Bereinigen des DSL-Definitionsdiagramms
 Wenn Sie Beziehungen hinzufügen, erscheinen einige Klassen an mehreren Stellen. Klicken Sie mit der rechten Maustaste auf die Zielklasse einer Beziehung, und klicken Sie dann **hier**, um die Anzahl der Vorkommen zu verringern und das Diagramm breiter zu machen. Um den umgekehrten Effekt zu erzielen, klicken Sie mit der rechten Maustaste auf die Zielklasse einer Beziehung, und klicken Sie auf Struktur **Teilen**. Wenn diese Menübefehle nicht angezeigt werden, vergewissern Sie sich, dass nur die Domänenklasse ausgewählt ist.

 Verwenden Sie STRG+NACH OBEN und STRG+NACH UNTEN, um Domänenklassen und Formklassen zu verschieben.

### <a name="test-the-domain-classes"></a>Testen der Domänenklassen

##### <a name="to-test-the-new-domain-classes"></a>So testen Sie die neuen Domänenklassen

1. Klicken Sie in der Symbolleiste von Projektmappen-Explorer auf **alle Vorlagen transformieren** , um den DSL-Designer-Code zu generieren. Dieser Schritt kann automatisiert werden. Weitere Informationen finden Sie unter [Automatisieren der Transformation für alle Vorlagen](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. **Erstellen Sie die DSL, und führen Sie sie aus.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im experimentellen Modus auszuführen. Öffnen oder erstellen Sie in der experimentellen Instanz von Visual Studio eine Datei mit der Dateinamenerweiterung ihrer DSL.

3. **Öffnen Sie den Explorer.** Am Rand des Diagramms befindet sich das Fenster "sprach-Explorer", das normalerweise den Namen " *YourLanguage* Explorer" trägt. Sollten Sie das Fenster nicht sehen, befindet es sich möglicherweise auf einer Registerkarte unter dem Projektmappen-Explorer. Wenn Sie es nicht finden, zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf *YourLanguage* - **Explorer**.

     Im Explorer wird eine Strukturansicht des Modells dargestellt.

4. **Erstellen Sie neue Elemente.** Klicken Sie mit der rechten Maustaste auf den Stamm Knoten, und klicken Sie dann auf neue _YourClass_ **Hinzufügen**.

     Im Sprach-Explorer wird eine neue Instanz Ihrer Klasse angezeigt.

5. Überprüfen Sie beim Erstellen neuer Instanzen, ob jede Instanz einen anderen Namen hat. Dies tritt nur dann auf, wenn Sie das Flag **is Element Name** für eine Domänen Eigenschaft festgelegt haben.

6. Über **prüfen Sie die Domänen Eigenschaften. Wenn eine Instanz der Klasse ausgewählt ist, überprüfen Sie** die Eigenschaftenfenster. Es sollte die Domäneneigenschaften zeigen, die Sie für die Domänenklasse definiert haben.

7. **Speichern Sie die Datei, schließen Sie Sie, und öffnen Sie Sie erneut**. Nachdem Sie die Knoten erweitert haben, sollten alle erstellten Instanzen im Explorer sichtbar sein.

## <a name="defining-shapes-on-the-diagram"></a><a name="shapes"></a> Definieren von Formen im Diagramm
 Sie können Klassen von Elementen definieren, die in einem Diagramm als Rechtecke, Ellipsen oder Symbole erscheinen.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>So definieren Sie eine Klasse von Elementen, die in einem Diagramm als Formen dargestellt werden

1. **Definieren und testen Sie eine Domänen Klasse, wie in**  [Definieren von Domänen Klassen](#classes) beschrieben **.**

   - Das übergeordnete Element der Klasse sollte die Stammklasse sein. Es sollte also eine einbettende Beziehung zwischen der Stammklasse und der neuen Domänenklasse bestehen.

   - Wenn das Diagramm Verantwortlichkeitsbereiche enthält, kann das übergeordnete Element die Domänenklasse sein, die einem Verantwortlichkeitsbereich zugeordnet ist. Bevor Sie mit diesem Verfahren fortfahren, finden Sie weitere Informationen unter [Definieren einer DSL](#swimlanes)mit Verantwortlichkeits Bereichen.

2. **Fügen Sie eine Shape-Klasse hinzu** , die die Elemente im Modell Diagramm darstellt. Ziehen Sie eines der folgenden Werkzeuge in das DSL-Definitionsdiagramm:

   - Die **Geometrie Form** bietet ein Rechteck oder eine Ellipse.

   - **Bild Form** zeigt ein Bild an, das Sie bereitstellen.

   - Die Depot- **Form** ist ein Rechteck, das mindestens eine Liste von Elementen enthält.

     Benennen Sie die Formklasse um, die rechts im DSL-Definitionsdiagramm unter "Formen und Konnektoren" angezeigt wird.

3. **Definieren Sie ein Bild, wenn Sie eine Bildform erstellt haben**.

   1. Erstellen Sie eine Bilddatei beliebiger Größe. Die Formate BMP, JPEG, GIF und EMF werden unterstützt.

   2. Fügen Sie die Datei im Projektmappen-Explorer der Projektmappe unter Dsl\Ressourcen hinzu.

   3. Kehren Sie zum DSL-Definitionsdiagramm zurück, und wählen Sie die neue Bild-Formklasse aus.

   4. Klicken Sie im Eigenschaftenfenster auf die **Image** -Eigenschaft.

   5. Klicken Sie im Dialogfeld **Bild auswählen** auf das Dropdown Menü unter **Dateiname**, und wählen Sie das Bild aus.

4. **Fügen Sie der Form Text-Decorator-Elemente hinzu, um die Domäneneigenschaften anzuzeigen.**

    Sie benötigen wahrscheinlich mindestens ein Text-Decorator-Element, um den Namen oder Titel des Modellelements anzuzeigen.

    Klicken Sie mit der rechten Maustaste auf den Header der Shape-Klasse, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Text Decorator**. Legen Sie den Namen des Decorators fest, und legen Sie im Eigenschaftenfenster seine **Position** fest.

5. **Verbinden Sie jede Form mit einer Diagramm Element Zuordnung mit der Domänen Klasse, die angezeigt werden soll**.

    Klicken Sie auf das **Diagramm Element Map** -Tool, und klicken Sie dann auf die Domänen Klasse und dann auf die Shape-Klasse.

6. **Ordnen Sie die Eigenschaften der Text-Decorator-Elemente zu.**

   1. Wählen Sie die graue Linie zwischen der Domänenklasse und der Formklasse aus, die die Diagrammelementzuordnung darstellt.

   2. Klicken Sie im Fenster **DSL-Details** auf die Registerkarte **Decorator** -Zuordnungen. Wenn das Fenster **DSL-Details** nicht angezeigt wird, zeigen Sie im Menü **Ansicht** auf **Weitere Fenster** , und klicken Sie dann auf DSL- **Details**. Häufig muss der obere Rand des Fensters angehoben werden, um den gesamten Inhalt anzuzeigen.

   3. Wählen Sie den Namen eines Decorator-Elements aus. Wählen Sie unter **Anzeige Eigenschaft** den Namen einer Eigenschaft der Domänen Klasse aus. Wiederholen Sie dies für jedes Decorator-Element.

       Wenn Sie eine Eigenschaft eines verknüpften Elements anzeigen möchten, klicken Sie auf den Dropdown-Struktur Navigator unter **Pfad zum Anzeigen der Eigenschaft**.

   4. Stellen Sie sicher, dass neben jedem Decorator-Namen ein Häkchen angezeigt wird.

      ![Formzuordnungen und DSL-Detailfenster](../modeling/media/dsldetailswindow.png)

7. **Erstellen Sie ein Werkzeugkastenelement zum Erstellen von Elementen der Domänenklasse.**

   1. Erweitern Sie im **DSL-Explorer** den Knoten **Editor** und alle zugehörigen untergeordneten Knoten.

   2. Klicken Sie mit der rechten Maustaste auf den Knoten unter **Toolbox-Registerkarten** mit dem gleichen Namen wie Ihre DSL, z. b. "musiclibrary". Klicken Sie auf **Element hinzufügen**.

       > [!NOTE]
       > Wenn Sie **mit der rechten** Maustaste auf den Knoten Extras klicken, wird das **Tool Add Element** nicht angezeigt. Klicken Sie stattdessen auf den übergeordneten Knoten.

   3. Legen Sie im Eigenschaftenfenster mit ausgewähltem Tool neues Element die **Klasse** auf die Domänen Klasse fest, die Sie kürzlich hinzugefügt haben.

   4. Legen  Sie Beschriftung **und** QuickInfo fest.

   5. Legen Sie **Toolbox Symbol** auf ein Symbol fest, das in der Toolbox angezeigt wird. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

        Um ein neues Symbol zu erstellen, öffnen Sie dsl\resources in **Projektmappen-Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

        Kehren Sie zum DSL-Definitions Diagramm zurück, wählen Sie das Tool aus, und klicken Sie in der Eigenschaftenfenster im **Toolbox Symbol** auf **[...]** . Wählen Sie im Dialogfeld **Bitmap auswählen** ihre aus. BMP-Datei aus dem Dropdown Menü.

   Weitere Informationen finden Sie unter [Eigenschaften von Geometrie Formen](../modeling/properties-of-geometry-shapes.md) und [Eigenschaften von Bildformen](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>So testen Sie Formen

1. Klicken Sie in der Symbolleiste von Projektmappen-Explorer auf **alle Vorlagen transformieren** , um den DSL-Designer-Code zu generieren.

2. **Erstellen Sie die DSL, und führen Sie sie aus.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im experimentellen Modus auszuführen. Öffnen oder erstellen Sie in der experimentellen Instanz von Visual Studio eine Datei mit der Dateinamenerweiterung ihrer DSL.

3. **Überprüfen Sie, ob die Elementwerkzeuge im Werkzeugkasten erscheinen.**

4. **Erstellen Sie Formen** , indem Sie Sie von einem Tool auf das Modell Diagramm ziehen.

5. Stellen Sie sicher, **dass die einzelnen Text-Decorator-Zeichen angezeigt werden** .

   1. Sie können Sie bearbeiten, es sei denn, Sie haben für die Domain-Eigenschaft das Flag **is UI Read Only** festgelegt.

   2. Wenn Sie die Eigenschaft im Eigenschaftenfenster oder im Decorator bearbeiten, wird die jeweils andere Ansicht aktualisiert.

   Nach dem ersten Test einer Form möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. Weitere Informationen finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-reference-relationships"></a><a name="references"></a> Definieren von Verweis Beziehungen
 Sie können eine Verweisbeziehung zwischen einer Quelldomänenklasse und einer Zieldomänenklasse definieren. Verweisbeziehungen werden in einem Diagramm üblicherweise als Konnektoren, also als Linien zwischen Formen, angezeigt.

 Wenn beispielsweise Alben und Interpreten als Formen in einem Diagramm dargestellt werden, könnten Sie eine Beziehung namens "ArtistsAppearedOnAlbums" definieren, die Interpreten mit den Alben verknüpft, an denen sie mitgewirkt haben. Siehe das Beispiel in der Abbildung.

 ![Instanzmodell für generierte DSL](../modeling/media/music_instance.png)

 Verweisbeziehungen können auch Elemente desselben Typs verbinden. So ist in einer DSL, die einen Familienstammbaum darstellt, die Beziehung zwischen Eltern und Kindern eine Verweisbeziehung von Person zu Person.

### <a name="define-a-reference-relationship"></a>Definieren einer Verweisbeziehung
 Klicken Sie auf das Werkzeug "Verweisbeziehung", auf die Quelldomänenklasse der Beziehung und dann auf die Zieldomänenklasse. Die Zielklasse kann mit der Quellklasse übereinstimmen.

 Jede Beziehung hat zwei Rollen, die durch die Linien auf beiden Seiten des Beziehungsfelds dargestellt werden. Sie können jede Rolle auswählen und ihre Eigenschaften im Eigenschaftenfenster festlegen.

 Sie **sollten die Rollen umbenennen**. In einer Beziehung zwischen Personen könnten Sie z. B. die Standardnamen in Eltern und Kinder, Manager und Mitarbeiter, Lehrer und Schüler usw. ändern.

 Passen Sie ggf. **die Multiplizitäten der einzelnen Rollen an**. Soll jede Person höchstens einen Manager haben, legen Sie die Multiplizität (unter der Beschriftung "Manager") im Diagramm auf 0..1 fest.

 **Fügen Sie der Beziehung Domäneneigenschaften hinzu.**  In der Abbildung hat die Beziehung zwischen Interpret und Album eine Eigenschaft "Rolle".

 **Legen Sie die Eigenschaft lässt Duplikate der Beziehung ein,** wenn mehrere Verknüpfungen derselben Klasse zwischen demselben paar von Modellelementen vorhanden sein können. Beispielsweise könnten Sie zulassen, dass ein Lehrer einen Schüler in mehreren Fächern unterrichtet.

 ![Formzuordnungen für Verbindungen](../modeling/media/music_connector.png)

 Weitere Informationen finden Sie unter [Eigenschaften von Domänen Beziehungen](../modeling/properties-of-domain-relationships.md) und [Eigenschaften von Domänen Rollen](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definieren eines Konnektors zur Darstellung der Beziehung
 Ein Konnektor stellt eine Linie zwischen zwei Formen im Modelldiagramm dar.

 Ziehen Sie das Tool **Connector** auf das DSL-Definitions Diagramm.

 Fügen Sie Text-Decorator-Elemente hinzu, falls Beschriftungen auf dem Konnektor angezeigt werden sollen. Legen Sie deren Positionen fest. Um dem Benutzer das Verschieben eines TextDecorator-Objekts zu gestatten, legen Sie die Eigenschaft **ist beweglicher Wert** fest.

 Verwenden Sie das **Diagramm Element Map** -Tool, um den Connector mit der Verweis Beziehung zu verknüpfen.

 Öffnen Sie bei ausgewähltem Diagramm Element Map das Fenster **DSL-Details** , und öffnen Sie die Registerkarte **Decorator** -Zuordnungen.

 Wählen Sie jeden **Decorator** aus, und legen Sie **Anzeige Eigenschaft** auf die richtige Domänen Eigenschaft fest.

 Stellen Sie sicher, dass neben jedem Element in der Liste **Decorators** ein Häkchen angezeigt wird.

### <a name="define-a-connection-builder-tool"></a>Definieren eines Werkzeugs "Verbindungs-Generator"
 Erweitern Sie im Fenster **DSL-Explorer** den Knoten **Editor** und alle zugehörigen untergeordneten Knoten.

 Klicken Sie mit der rechten Maustaste auf den Knoten, der denselben Namen wie Ihre DSL hat, und klicken Sie dann auf **Neues Verbindungs Tool hinzufügen**.

 Führen Sie, während das neue Werkzeug ausgewählt ist, im Eigenschaftenfenster Folgendes aus:

- Legen Sie **Beschriftung** und QuickInfo fest.

- Klicken Sie auf **Verbindungs** -Generator, und wählen Sie den entsprechenden Generator für die neue Beziehung aus.

- Legen Sie das Symbol " **Toolbox** " auf das Symbol fest, das in der Toolbox angezeigt werden soll. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

     Um ein neues Symbol zu erstellen, öffnen Sie dsl\resources in **Projektmappen-Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

     Kehren Sie zum DSL-Definitions Diagramm zurück, wählen Sie das Tool aus, und klicken Sie in der Eigenschaftenfenster im **Toolbox Symbol** auf **[...]** . Wählen Sie im Dialogfeld **Bitmap auswählen** ihre aus. BMP-Datei aus dem Dropdown Menü.

##### <a name="to-test-a-reference-relationship-and-connector"></a>So testen Sie eine Verweisbeziehung und einen Konnektor

1. Klicken Sie in der Symbolleiste von Projektmappen-Explorer auf **alle Vorlagen transformieren** , um den DSL-Designer-Code zu generieren.

2. **Erstellen Sie die DSL, und führen Sie sie aus.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im experimentellen Modus auszuführen. Öffnen oder erstellen Sie in der experimentellen Instanz von Visual Studio eine Datei mit der Dateinamenerweiterung ihrer DSL.

3. **Überprüfen Sie, ob das Verbindungswerkzeug im Werkzeugkasten erscheint.**

4. **Erstellen Sie Formen** , indem Sie Sie von einem Tool auf das Modell Diagramm ziehen.

5. **Erstellen Sie Verbindungen** zwischen den Formen. Klicken Sie auf das Konnektorwerkzeug, auf eine Form und dann auf eine andere Form.

6. **Überprüfen Sie, ob Sie keine Verbindungen zwischen ungeeigneten Klassen erstellen können.**  Besteht die Beziehung beispielsweise zwischen Alben und Interpreten, überprüfen Sie, ob Sie nicht Interpreten mit Interpreten verbinden können.

7. **Überprüfen Sie, ob die Multiplizitäten korrekt sind. Stellen Sie z. b. sicher, dass Sie eine Person nicht mit mehreren Vorgesetzten verbinden können.**

8. Stellen Sie sicher, **dass die einzelnen Text-Decorator-Zeichen angezeigt werden** .

   1. Sie können Sie bearbeiten, es sei denn, Sie haben für die Domain-Eigenschaft das Flag **is UI Read Only** festgelegt.

   2. Wenn Sie die Eigenschaft im Eigenschaftenfenster oder im Decorator bearbeiten, wird die jeweils andere Ansicht aktualisiert.

   Nach dem ersten Test eines Konnektors möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. Weitere Informationen finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-shapes-that-contain-lists-compartment-shapes"></a><a name="compartments"></a> Definieren von Formen, die Listen enthalten: Depot-Formen
 Eine Depot-Form enthält mindestens eine Liste von Elementen. In einer DSL für eine Musikbibliothek würden Sie z. B. Depot-Formen verwenden, um Musikalben darzustellen. Jedes Album enthält eine Liste von Songs.

 ![Depot-Form](../modeling/media/compartmentshape.png)

 Am einfachsten erzielen Sie diesen Effekt in einer DSL-Definition, indem Sie eine Domänenklasse für den Container und eine Domänenklasse für jede Liste definieren. Die Containerklasse wird der Depot-Form zugeordnet.

 ![Formzuordnung](../modeling/media/music_mapcomp.png)

 Weitere Informationen finden Sie unter [Eigenschaften von Depot Formen](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>So definieren Sie eine Depot-Form

1. **Erstellen Sie die Container Domänen Klasse**. Klicken Sie auf das Tool **Einbettungs Beziehung** , klicken Sie auf die Stamm Klasse des Modells, und klicken Sie dann auf einen leeren Teil des DSL-Definitions Diagramms. Dadurch wird in der Beispielabbildung die Domänenklasse namens "Album" erstellt.

     Alternativ können Sie den Container statt in die Stammklasse auch in eine Domänenklasse einbetten, die einem Verantwortlichkeitsbereich zugeordnet ist.

     Fügen Sie der Klasse eine Domänen Eigenschaft hinzu, z. b. Name, und legen Sie das Flag **ist Element Name** in der Eigenschaftenfenster fest.

2. **Erstellen Sie die Listenelement-Domänen Klasse**. Klicken Sie auf das Tool **Einbettungs Beziehung** , klicken Sie auf die Container Klasse (Album), und klicken Sie dann auf einen leeren Teil des Diagramms. Dadurch wird in der Beispielabbildung die Domänenklasse namens "Song" erstellt.

     Fügen Sie der Klasse eine Domänen Eigenschaft wie den Titel hinzu, und legen Sie das Flag **ist Element Name** fest.

     Fügen Sie weitere Domäneneigenschaften hinzu.

     Fügen Sie eine weitere Domänenklasse für Listenelemente jeder Liste hinzu, die Sie anzeigen möchten.

3. **Um mehrere Elementtypen in der Liste zu mischen**, erstellen Sie Klassen, die von der List-Klasse erben. Legen Sie den **Vererbungsmodifizierer** als abstrakte Klasse fest.

     Möchten Sie beispielsweise klassische Musik nach Komponisten statt nach Interpreten sortieren, könnten Sie zwei Unterklassen von Song erstellen: ClassicalSong und NonClassicalSong.

4. **Erstellen Sie die** Depot-Form. Ziehen Sie aus dem Depot- **Shape** -Tool auf das DSL-Definitions Diagramm.

     Fügen Sie ein Text-Decorator-Element hinzu, und legen Sie seinen Namen fest.

     Fügen Sie ein Depot hinzu, und legen Sie seinen Namen fest.

5. Damit der Benutzer die Listen Depots ausblenden kann, klicken Sie mit der rechten Maustaste auf die Depot-Shape-Klasse, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Decorator erweitern/** reduzieren. Legen Sie im Eigenschaftenfenster die Position des Decorator-Elements fest.

6. Klicken Sie auf das **Diagramm Element Map** -Tool, klicken Sie auf die Domänen Klasse Container, und klicken Sie dann auf die Depot-Form

7. Wählen Sie den Diagrammelementzuordnungs-Link zwischen der Domänenklasse und der Form aus. Im Fenster " **DSL-Details** ":

    1. Klicken Sie auf die Registerkarte **Decorators** . Klicken Sie auf den Namen des Decorator-Elements, und wählen Sie dann das entsprechende Element unter **Anzeige Eigenschaft** aus. Stellen Sie sicher, dass neben dem Namen des Decorator-Elements ein Häkchen angezeigt wird.

    2. Klicken Sie **auf die Register** Karte Depot Zuordnungen.

         Klicken Sie auf den Namen des Depots.

         Navigieren Sie unter **Angezeigter** Element Auflistungs Pfad zur List-Element Klasse (Song). Klicken Sie auf den Dropdownpfeil, um das Navigatorwerkzeug zu verwenden.

         Wählen Sie unter **Anzeige Eigenschaft** die Eigenschaft aus, die in der Liste angezeigt werden soll. Im Beispiel ist dies "Titel".

> [!NOTE]
> Mithilfe der Pfadfelder in der Decorator-Zuordnung und der Depot-Zuordnung können Sie komplexere Beziehungen zwischen der Domänenklasse und der Depot-Form erstellen.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>So definieren Sie ein Werkzeug zum Erstellen der Form

1. **Erstellen Sie ein Werkzeugkastenelement zum Erstellen von Elementen der Domänenklasse.**

2. Erweitern Sie im **DSL-Explorer** den Knoten **Editor** und alle zugehörigen untergeordneten Knoten.

3. Klicken Sie mit der rechten Maustaste auf den Knoten unter **Toolbox-Registerkarten** mit dem gleichen Namen wie Ihre DSL, z. b. "musiclibrary". Klicken Sie auf **Element hinzufügen**.

    > [!NOTE]
    > Wenn Sie **mit der rechten** Maustaste auf den Knoten Extras klicken, wird das **Tool Add Element** nicht angezeigt. Klicken Sie stattdessen auf den übergeordneten Knoten.

4. Legen Sie im Eigenschaftenfenster mit ausgewähltem Tool neues Element die **Klasse** auf die Domänen Klasse fest, die Sie kürzlich hinzugefügt haben.

5. Legen  Sie Beschriftung **und** QuickInfo fest.

6. Legen Sie **Toolbox Symbol** auf ein Symbol fest, das in der Toolbox angezeigt wird. Sie können ein neues Symbol oder ein bereits für ein anderes Werkzeug verwendetes Symbol angeben.

     Um ein neues Symbol zu erstellen, öffnen Sie dsl\resources in **Projektmappen-Explorer**. Kopieren Sie eine der vorhandenen BMP-Dateien für Elementwerkzeuge, und fügen Sie sie ein. Benennen Sie die eingefügte Kopie um, und doppelklicken Sie dann darauf, um sie zu öffnen.

     Kehren Sie zum DSL-Definitions Diagramm zurück, wählen Sie das Tool aus, und klicken Sie in der Eigenschaftenfenster im **Toolbox Symbol** auf **[...]** . Wählen Sie im Dialogfeld **Bitmap auswählen** ihre BMP-Datei aus dem Dropdown Menü aus.

#### <a name="to-test-a-compartment-shape"></a>So testen Sie eine Depot-Form

1. Klicken Sie in der Symbolleiste von Projektmappen-Explorer auf **alle Vorlagen transformieren** , um den DSL-Designer-Code zu generieren.

2. **Erstellen Sie die DSL, und führen Sie sie aus.** Drücken Sie F5 oder STRG + F5, um eine neue Instanz von Visual Studio im experimentellen Modus auszuführen. Öffnen oder erstellen Sie in der experimentellen Instanz von Visual Studio eine Datei mit der Dateinamenerweiterung ihrer DSL.

3. **Überprüfen Sie, ob das Werkzeug im Werkzeugkasten erscheint.**

4. Ziehen Sie das Werkzeug in das Modelldiagramm. Eine Form wird erstellt.

    Überprüfen Sie, ob der Name des Elements angezeigt und automatisch auf einen Standardwert festgelegt wird.

5. Klicken Sie mit der rechten Maustaste auf den Header der neuen Form, und klicken Sie dann auf *Listenelement* hinzufügen. Im Beispiel lautet der Befehl "Song hinzufügen".

    Überprüfen Sie, ob ein Element mit einem neuen Namen in der Liste erscheint.

6. Klicken Sie auf eines der Listenelemente, und betrachten Sie das Eigenschaftenfenster. Es sollten die Eigenschaften der Listenelemente angezeigt werden.

7. Öffnen Sie den Sprach-Explorer. Überprüfen Sie, ob die Containerknoten mit darin enthaltenen Listenelementknoten angezeigt werden.

   ![Generierter Explorer für DSL](../modeling/media/music_explorer.png)

   Nach dem ersten Test einer Depot-Form möchten Sie unter Umständen einige Eigenschaften anpassen und erweiterte Features hinzufügen. Weitere Informationen finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Anzeigen eines Verweislinks in einem Depot
 Normalerweise ist ein in einem Depot angezeigtes Element ein untergeordnetes Element des Elements, das durch die Depot-Form dargestellt wird. Aber manchmal soll ein Element angezeigt werden, das durch eine Verweisbeziehung damit verbunden ist.

 Wir könnten z. B. ein zweites Depot zu AlbumShape hinzufügen, in dem eine Liste der mit dem Album verbundenen Interpreten angezeigt wird.

 In diesem Fall sollte das Depot statt des Elements, auf das verwiesen wird, den Link anzeigen. Denn wenn der Benutzer das Element im Depot auswählt und ENTF drückt, soll der Link gelöscht werden und nicht das Element, auf das verwiesen wird.

 Dennoch kann der Name des Elements, auf das verwiesen wird, im Depot erscheinen.

 Im folgenden Verfahren wird vorausgesetzt, dass Sie bereits die Domänenklasse, die Verweisbeziehung, die Depot-Form und die Diagrammelementzuordnung erstellt haben, wie weiter oben in diesem Abschnitt beschrieben.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>So zeigen Sie einen Verweislink in einem Depot an

1. **Fügen Sie der Depot-Form ein Depot hinzu**. Klicken Sie im DSL-Definitions Diagramm mit der rechten Maustaste auf die Depot-Shape-Klasse, zeigen Sie auf **Hinzufügen**, **und klicken Sie dann auf Depot**.

2. Legen Sie den Auflistungs **Pfad für angezeigte Elemente** so fest, dass Sie zum Link anstatt zum Ziel Element navigieren. Klicken Sie auf das Dropdownmenü, und verwenden Sie die Strukturansicht, um die Verweisbeziehung statt ihres Ziels auszuwählen. Im Beispiel ist die Beziehung " **artistappearedonalbums**".

3. Legen **Sie Pfad zur Anzeige Eigenschaft** fest, um von der Verknüpfung zum Ziel Element zu navigieren. Im Beispiel ist dies " **Artist**".

4. Legen Sie **Anzeige Eigenschaft** auf die entsprechende Eigenschaft des Ziel Elements fest, z. b. " **Name**".

5. **Transformieren Sie alle Vorlagen**, erstellen Sie die DSL, und führen Sie Sie aus, und öffnen Sie ein Testmodell.

6. Erstellen Sie in dem Modelldiagramm die entsprechenden Formklassen, legen Sie ihre Namen fest, und erstellen Sie einen Link zwischen ihnen. In der Depot-Form sollten die Namen der verbundenen Elemente angezeigt werden.

7. Wählen Sie entweder den Link oder das Element in der Depot-Form aus. Sowohl der Link als auch das Element sollte angezeigt werden.

## <a name="defining-ports-on-the-boundary-of-another-shape"></a><a name="ports"></a> Definieren von Ports an der Grenze einer anderen Form
 Ein Anschluss ist eine Form, die sich am Rand einer anderen Form befindet.

 Anschlüsse können auch verwendet werden, um einen festen Verbindungspunkt an einer anderen Form bereitzustellen, zu dem der Benutzer Konnektoren zeichnen kann. In diesem Fall können Sie die Anschluss-Form transparent machen.

 Um ein Beispiel anzuzeigen, in dem Ports verwendet werden, wählen Sie die **Komponenten Diagramm** Vorlage aus, wenn Sie eine neue DSL-Projekt Mappe erstellen. Dieses Beispiel zeigt die wesentlichen Punkte, die Sie bei der Definition von Anschlüssen berücksichtigen können:

- Es gibt eine Domänenklasse, die den Container der Anschlüsse darstellt: `Component`.

- Es gibt eine Domänenklasse, die Anschlüsse darstellt. In diesem Beispiel `ComponentPort`.

- Es gibt eine einbettende Beziehung von der Container-Domänenklasse zur Anschluss-Domänenklasse. Weitere Informationen finden Sie unter [Definieren von Domänen Klassen](#classes).

- Wenn verschiedene Anschlusstypen in demselben Container gemischt werden sollen, können Sie Unterklassen der Anschluss-Domänenklasse erstellen. In dem Beispiel erben `InPort` und `OutPort` von `ComponentPort`.

- Die Container-Domänenklasse kann jeder beliebigen Form zugeordnet werden. Im Beispiel ist dies `ComponentShape`. Weitere Informationen finden Sie unter [Definieren von Formen](#shapes).

- Die Anschluss-Domänenklassen werden Anschluss-Formen zugeordnet. Sie können entweder die abgeleiteten Klassen verschiedenen Anschluss-Formklassen zuordnen oder die Basisklasse einer Anschluss-Formklasse zuordnen.

  In anderen Hinsicht verhalten sich Port Formen wie unter [Definieren von Formen](#shapes)beschrieben.

  Weitere Informationen finden Sie unter [Eigenschaften von Port Formen](../modeling/properties-of-port-shapes.md).

## <a name="defining-a-dsl-that-has-swimlanes"></a><a name="swimlanes"></a> Definieren einer DSL mit Verantwortlichkeits Bereichen
 Verantwortlichkeitsbereiche sind vertikale oder horizontale Bereiche eines Diagramms. Jeder Verantwortlichkeitsbereich entspricht einem Modellelement. Ihre DSL-Definition muss eine Domänenklasse für die Verantwortlichkeitsbereich-Elemente enthalten.

 Am besten lässt sich eine DSL mit Verantwortlichkeitsbereichen erstellen, indem Sie eine neue DSL-Projektmappe erstellen und die Projektmappenvorlage "Aufgabenfluss" auswählen. In der DSL-Definition ist die Actor-Klasse die Domänenklasse, die dem Verantwortlichkeitsbereich zugeordnet wird. Benennen Sie diese und die anderen Klassen nach den Anforderungen Ihres Projekts um.

 Um eine Klasse hinzuzufügen, die als Form innerhalb eines Verantwortlichkeitsbereichs angezeigt wird, erstellen Sie eine einbettende Beziehung zwischen der Klasse des Verantwortlichkeitsbereichs und Ihrer neuen Klasse. Benutzer können Elemente von einem Verantwortlichkeitsbereich in einen anderen ziehen, aber jedes Element befindet sich immer innerhalb eines bestimmten Verantwortlichkeitsbereichs. In der Projektmappenvorlage "Aufgabenfluss" ist "FlowElement" ein untergeordnetes Element der Verantwortlichkeitsbereich-Klasse.

 Um eine Klasse hinzuzufügen, die als Form unabhängig von Verantwortlichkeitsbereichen angezeigt wird, erstellen Sie eine einbettende Beziehung zwischen der Stammklasse und Ihrer neuen Klasse. Benutzer können diese Formen beliebig im Diagramm platzieren, auch über die Grenzen von Verantwortlichkeitsbereichen hinweg und außerhalb von Verantwortlichkeitsbereichen. In der Projektmappenvorlage "Aufgabenfluss" ist "Comment" ein untergeordnetes Element der Stammklasse.

 Weitere Informationen finden Sie unter [Eigenschaften von Swimlanes](../modeling/properties-of-swimlanes.md).

## <a name="adding-property-types"></a><a name="addTypes"></a> Hinzufügen von Eigenschaften Typen

### <a name="domain-enumerations-and-literals"></a>Domänenenumerationen und Literale
 Eine Domänenenumeration ist ein Typ mit mehreren Literalwerten.

 Um eine Domänen Enumeration hinzuzufügen, klicken Sie im **DSL-Explorer** mit der rechten Maustaste auf den Stamm des Modells, und klicken Sie dann auf **neue Domänen Enumeration hinzufügen**. Das-Element wird im **DSL-Explorer** unter dem Knoten **Domänen Typen** angezeigt. Das Element erscheint nicht im Diagramm.

 Um der Domänen Enumeration enumerationsliterale hinzuzufügen, klicken Sie mit der rechten Maustaste auf die Domänen Enumeration im **DSL-Explorer** , und klicken Sie dann auf **Neues** enumerationsliteralelement

 Eine Eigenschaft, die einen Enumerationstyp besitzt, kann standardmäßig jeweils nur auf einen Wert der Enumeration festgelegt werden. Wenn Sie möchten, dass Benutzer und Programmierer eine beliebige Kombination von Werten festlegen können (ein "Bitfeld"), legen Sie die **isFlags** -Eigenschaft der Enumeration fest.

### <a name="external-types"></a>Externe Typen
 Wenn Sie den Typ einer Domänen Eigenschaft festlegen und den gewünschten Typ nicht in der Dropdown Liste **Typ** finden, können Sie einen externen Typ hinzufügen. Beispielsweise können Sie den Typ " **System. Drawing. Color** " der Liste hinzufügen.

 Um einen Typ hinzuzufügen, klicken Sie im DSL-Explorer mit der rechten Maustaste auf den Stamm des Modells, und klicken Sie dann auf **neuen externen Typ hinzufügen**. Legen Sie in der Eigenschaftenfenster den Namen auf " **Color** " und den Namespace auf " **System. Drawing**" fest. Dieser Typ wird jetzt im DSL-Explorer unter **Domänen Typen** angezeigt. Sie können ihn immer auswählen, wenn Sie den Typ einer Domäneneigenschaft festlegen.

## <a name="customizing-the-dsl"></a><a name="custom"></a> Anpassen der DSL
 Mit den hier beschriebenen Verfahren können Sie schnell eine DSL mit einer Diagrammdarstellung, einem lesbaren XML-Format und den grundlegenden Tools erstellen, mit denen Code und andere Artefakte generiert werden.

 Die DSL-Definition kann auf zwei Arten erweitert werden:

1. Optimieren Sie die DSL, indem Sie weitere Features in der DSL-Definition verwenden. Sie können beispielsweise ein einzelnes Konnektorwerkzeug erstellen, das verschiedene Typen von Konnektoren generieren kann, und Sie können die Regeln steuern, nach denen beim Löschen eines Elements auch verwandte Elemente gelöscht werden. Diese Verfahren bestehen meist im Festlegen von Werten in der DSL-Definition. Manche erfordern auch einige Zeilen Programmcode.

     Weitere Informationen finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Erweitern Sie Ihre Modellierungstools mit Programmcode, um kompliziertere Effekte zu erzielen. So können Sie z. B. Menübefehle erstellen, die das Modell ändern, und Sie können Tools erstellen, in denen zwei oder mehr DSLs integriert sind. VMSDK wurde speziell dafür entwickelt, die Integration Ihrer Erweiterungen in den Code zu vereinfachen, der aus der DSL-Definition generiert wird.  Weitere Informationen finden Sie unter [Schreiben von Code zum Anpassen einer Domain-Specific Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Ändern der DSL-Definition
 Wenn Sie ein Element in einer DSL-Definition erstellen, werden viele Standardwerte automatisch festgelegt. Diese Werte können Sie anschließend ändern. Dies vereinfacht die Entwicklung einer DSL und ermöglicht gleichzeitig wirkungsvolle Anpassungen.

 Wenn Sie beispielsweise eine Form einem Element zuordnen, wird der Pfad des übergeordneten Elements der Zuordnung automatisch entsprechend der einbettenden Beziehung der Domänenklasse festgelegt. Wenn Sie die einbettende Beziehung später ändern, wird der Pfad des übergeordneten Elements nicht automatisch geändert.

 Daher sollten Sie damit rechnen, dass nach einer Änderung von Beziehungen in der DSL-Definition häufig Fehler gemeldet werden, wenn Sie die Definition speichern oder "Alle Vorlagen transformieren" verwenden. Die meisten dieser Fehler sind leicht zu beheben. Doppelklicken Sie auf den Fehlerbericht, um den Ort des Fehlers zu ermitteln.

 Weitere Informationen finden Sie unter Vorgehens [Weise: Ändern des Namespace einer Domain-Specific Sprache](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="troubleshooting"></a><a name="trouble"></a> Problembehandlung
 In der folgenden Tabelle sind einige der häufigsten Probleme, die beim Entwurf einer DSL auftreten, zusammen mit ihrer Lösung aufgeführt. Weitere Ratschläge finden Sie im [Erweiterbarkeits Forum für Visualisierungs Tools](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

| Problem | Vorschlag |
|-|-|
| Die Änderungen, die ich an der DSL-Definition vorgenommen habe, wirken sich nicht aus. | Klicken Sie Projektmappen-Explorer oben in der Symbolleiste auf **alle Vorlagen transformieren** , und erstellen Sie die Projekt Mappe neu. |
| Formen zeigen statt des Eigenschaftenwerts den Namen eines Decorator-Elements an. | Richten Sie die Decorator-Zuordnung ein. Klicken Sie im DSL-Definitionsdiagramm auf die Diagrammelementzuordnung (die graue Linie zwischen der Domänenklasse und der Formklasse).<br /><br /> Öffnen Sie das Fenster **DSL-Details** . Wenn diese Option nicht angezeigt wird, zeigen Sie im Menü Ansicht auf **Weitere Fenster**, und klicken Sie dann auf **DSL-Details**.<br /><br /> Klicken Sie auf die Registerkarte **Decorator** -Zuordnungen. Wählen Sie den Namen des Decorators aus. Vergewissern Sie sich, dass das Kontrollkästchen daneben aktiviert ist. Wählen Sie unter **Anzeige Eigenschaft** den Namen einer Domänen Eigenschaft aus.<br /><br /> Weitere Informationen finden Sie [in den Formen im Diagramm](#shapes). |
| Ich kann in DSL-Explorer keine Auflistung hinzufügen. Zum Beispiel gibt es beim Rechtsklick auf "Werkzeuge" keinen "Tool hinzufügen"-Befehl im Menü.<br /><br /> Ich kann im Explorer für meine DSL kein Element zu einer Liste hinzufügen. | Klicken Sie mit der rechten Maustaste auf das Element über dem Knoten, den Sie testen. Wenn Sie etwas zu einer Liste hinzufügen möchten, befindet sich der Befehl zum Hinzufügen nicht im Listenknoten, sondern in seinem Besitzer. |
| Ich habe eine Domänenklasse erstellt, aber ich kann im Explorer der Sprache keine Instanzen erstellen. | Jede Domänenklasse mit Ausnahme des Stamms muss Ziel einer einbettenden Beziehung sein. |
| Im Explorer für meine DSL werden die Elemente nur mit ihren Typennamen angezeigt. | Wählen Sie in der DSL-Definition eine Domänen Eigenschaft der-Klasse aus, und legen Sie in der Eigenschaftenfenster den Wert **Element Name** auf true fest. |
| Meine DSL wird immer im XML-Editor geöffnet. | Das kann an einem Fehler beim Lesen der Datei liegen. Nachdem Sie den Fehler behoben haben, müssen Sie den Editor explizit als Ihren DSL-Designer zurücksetzen.<br /><br /> Klicken Sie mit der rechten Maustaste auf das Projekt Element, klicken Sie auf **Öffnen mit** , und wählen Sie * YourLanguage ***Designer (Standard)**. |
| Der Werkzeugkasten meiner DSL wird nicht angezeigt, nachdem ich die Assemblynamen geändert habe. | Weitere Informationen finden Sie unter Überprüfen und Aktualisieren von **dslpackage\generatedcode\package.tt** . Weitere Informationen finden Sie unter Vorgehens [Weise: Ändern des Namespace einer Domain-Specific Sprache](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md). |
| Der Werkzeugkasten meiner DSL wird nicht angezeigt, obwohl ich die Assemblynamen nicht geändert habe.<br /><br /> Oder es wird in einem Meldungsfeld gemeldet, dass eine Erweiterung nicht geladen werden konnte. | Setzen Sie die experimentelle Instanz zurück, und erstellen Sie die Projektmappe neu.<br /><br /> 1. Klicken Sie im Windows-Startmenü unter **Alle Programme** auf [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] , dann auf Extras, und klicken Sie dann auf **Microsoft Visual Studio experimentelle Instanz zurücksetzen**.<br />2. Klicken Sie im Menü **Erstellen** auf Projekt Mappe **neu erstellen**. |

## <a name="see-also"></a>Weitere Informationen

- [Erste Schritte mit domänenspezifischen Sprachen](../modeling/getting-started-with-domain-specific-languages.md)
- [Erstellen einer Windows Forms-basierten domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Erstellen einer WPF-basierten domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md)
