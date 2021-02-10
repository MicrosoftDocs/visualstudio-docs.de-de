---
title: Anpassen und Erweitern einer domänenspezifischen Sprache
description: Erfahren Sie, wie das Visual Studio-Modellierungs-und-Visualisierungs-SDK (vmsdk) mehrere Ebenen bereitstellt, mit denen Sie Modellierungstools definieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9cfa8a3cda3f6bb2f564efe745a11863cf4d0e8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945304"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Anpassen und Erweitern einer domänenspezifischen Sprache

Das Visual Studio-Modellierungs-und-Visualisierungs-SDK (vmsdk) bietet mehrere Ebenen, auf denen Sie Modellierungstools definieren können:

1. Definieren Sie eine domänenspezifische Sprache (DSL) mithilfe des DSL-Definitions Diagramms. Sie können schnell eine DSL mit einer diagrammatischen Notation, einem lesbaren XML-Formular und den grundlegenden Tools erstellen, die zum Generieren von Code und anderen Artefakten erforderlich sind. Weitere Informationen finden Sie unter Vorgehens [Weise beim Definieren einer Domain-Specific Sprache](../modeling/how-to-define-a-domain-specific-language.md).

2. Optimieren Sie die DSL mithilfe erweiterter Funktionen der DSL-Definition. Beispielsweise können Sie zusätzliche Links anzeigen, wenn der Benutzer ein Element erstellt. Diese Techniken werden größtenteils in der DSL-Definition erzielt, und einige erfordern einige Zeilen Programmcode.

3. Erweitern Sie die Modellierungstools mithilfe von Programmcode. VMSDK wurde speziell dafür entwickelt, die Integration Ihrer Erweiterungen in den Code zu vereinfachen, der aus der DSL-Definition generiert wird. Weitere Informationen finden Sie unter [Schreiben von Code zum Anpassen einer Domain-Specific Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Wenn Sie die DSL-Definitions Datei aktualisiert haben, vergessen Sie nicht, auf **alle Vorlagen transformieren** in der Symbolleiste von **Projektmappen-Explorer** zu klicken, bevor Sie die Projekt Mappe neu erstellen.

## <a name="article-reference"></a>Artikelreferenz

|So erreichen Sie diesen Effekt|Informationen finden Sie in diesem Thema.|
|-|-|
|Ermöglicht dem Benutzer das Festlegen der Farb-und Stileigenschaften einer Form.|Klicken Sie mit der rechten Maustaste auf die Form oder die Klasse Connector, zeigen Sie auf verfügbar machen, und klicken **Sie auf ein** Element.|
|Verschiedene Klassen des Modell Elements sehen im Diagramm ähnlich aus, wie z. b. anfängliche Höhe und Breite, Farbe und Quick Infos.|Verwenden Sie die Vererbung zwischen Formen oder Connector-Klassen. Zuordnungen zwischen abgeleiteten Formen und abgeleiteten Domänen Klassen erben die Mappingdetails der übergeordneten Elemente.<br /><br /> Oder ordnen Sie verschiedene Domänen Klassen derselben Shape-Klasse zu.|
|Eine Klasse des Modell Elements wird in verschiedenen Formen Kontexten angezeigt.|Ordnen Sie mehrere Shape-Klassen derselben Domänen Klasse zu. Wenn Sie die Projekt Mappe erstellen, befolgen Sie den Fehlerbericht und geben den angeforderten Code an, um zu entscheiden, welche Form verwendet werden soll.|
|Shape-Farbe oder andere Funktionen, wie z. b. Schriftart, zeigen den aktuellen Zustand|Weitere Informationen finden [Sie unter Aktualisieren von Formen und Connectors für das Modell](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Erstellen Sie eine Regel, mit der die verfügbar gemachten Eigenschaften aktualisiert werden. Siehe [Regeln weitergeben von Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Oder verwenden Sie onassociatedpropertychanged (), um nicht verfügbar gemachte Features wie z. b. Verknüpfungs Pfeile oder Schriftart zu aktualisieren.|
|Symbol bei Formänderungen, um den Status anzugeben.|Festlegen der Sichtbarkeit der decoratorzuordnung im Fenster "DSL-Details". Suchen Sie mehrere Bild-Decorator-Zeichen an der gleichen Position. Weitere Informationen finden  [Sie unter Aktualisieren von Formen und Connectors für das Modell](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Oder überschreiben `ImageField.GetDisplayImage()` . Siehe Beispiel in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Festlegen eines Hintergrund Bilds für beliebige Formen|Überschreiben Sie initializeingestanceresources (), um ein verankertes ImageField hinzuzufügen.|
|Formen in beliebiger tiefe schachteln|Richten Sie einen rekursiven Einbettungs Baum ein. Definiert boundsrules, um die Formen zu enthalten.|
|Anfügen von Connectors an festem Punkt an der Grenze eines Elements.|Definieren Sie eingebettete Terminal Elemente, die durch kleine Ports im Diagramm dargestellt werden. Verwenden Sie boundsrules, um die Ports zu korrigieren. Weitere Informationen finden Sie im Beispiel für das Verbindungs Diagramm unter [Visualisierung und modellieren von SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|
|Textfeld zeigt einen Wert an, der von anderen Werten abgeleitet ist.|Ordnen Sie den Text Decorator einer berechneten oder benutzerdefinierten Speicher Domänen Eigenschaft zu. Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speicher Eigenschaften](../modeling/calculated-and-custom-storage-properties.md).|
|Weitergeben von Änderungen zwischen Modellelementen oder zwischen Formen|Weitere Informationen finden Sie [unter Validierung in einer Domain-Specific Sprache](../modeling/validation-in-a-domain-specific-language.md).|
|Weitergeben von Änderungen an Ressourcen, z. b. anderen Visual Studio-Erweiterungen außerhalb des Stores.|Weitere Informationen finden Sie [unter Ereignishandler weitergeben von Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Im Eigenschaften Fenster werden Eigenschaften eines verknüpften Elements angezeigt.|Einrichten der Eigenschaften Weiterleitung. Weitere Informationen finden Sie [unter Anpassen des Fensters "Eigenschaften](../modeling/customizing-the-properties-window.md)".|
|Eigenschaften Kategorien|Das Fenster Eigenschaften ist in Abschnitte unterteilt, die als Kategorien bezeichnet werden. Legen Sie die **Kategorie** ihrer Domänen Eigenschaften fest. Eigenschaften mit dem gleichen Kategorienamen werden im gleichen Abschnitt angezeigt. Sie können auch die **Kategorie** einer Beziehungs Rolle festlegen.|
|Steuern des Benutzer Zugriffs auf Domänen Eigenschaften|Set **ist Browsable** false, um zu verhindern, dass eine Domänen Eigenschaft zur Laufzeit im Eigenschaftenfenster angezeigt wird. Sie können Sie dennoch Text-Decorators zuordnen.<br /><br /> **Ist UI** -schreibgeschützt verhindert, dass Benutzer eine Domänen Eigenschaft ändern.<br /><br /> Der Programm Zugriff auf die Domänen Eigenschaft ist nicht betroffen.|
|Ändern Sie den Namen, das Symbol und die Sichtbarkeit der Knoten im Modell-Explorer von DSL.|Weitere Informationen finden Sie [unter Anpassen des Modell-Explorers](../modeling/customizing-the-model-explorer.md).|
|Kopieren, Ausschneiden und Einfügen aktivieren|Legen Sie die Eigenschaft **Kopiervorgang aktivieren** des Knotens **Editor** im DSL-Explorer fest.|
|Kopieren Sie Verweis Links und ihre Ziele, wenn ein Element kopiert wird. Kopieren Sie beispielsweise Kommentare, die an ein Element angefügt sind.|Legen Sie die Eigenschaft für die Weiterleitungs **Kopie** der Quell Rolle fest (dargestellt durch die Linie auf einer Seite der Domänen Beziehung im DSL-Definitions Diagramm).<br /><br /> Schreiben Sie Code, um processoncopy zu überschreiben, um komplexere Effekte zu erzielen.<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Kopier Verhaltens](../modeling/customizing-copy-behavior.md).|
|Löschen, wiederherstellen oder Verknüpfen verwandter Elemente, wenn ein Element gelöscht wird.|Legen Sie den Wert " **Delete** " für eine Beziehungs Rolle fest. Bei komplexeren Effekten überschreiben Sie `ShouldVisitRelationship` `ShouldVisitRolePlayer` die Methoden und in der `MyDslDeleteClosure` Klasse, die in **DomainModel.cs** definiert sind.|
|Behalten Sie das Layout und die Darstellung von Formen beim Kopieren und ziehen-ablegen bei.|Fügen Sie die Formen und Connectors der kopierten hinzu `ElementGroupPrototype` . Die einfachste Methode zum Überschreiben ist `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Kopier Verhaltens](../modeling/customizing-copy-behavior.md).|
|Fügen Sie Formen an einer ausgewählten Stelle ein, beispielsweise an der aktuelle Cursorposition.|Außer Kraft setzen `ClipboardCommandSet.ProcessOnCopy()` , um die standortspezifische Version von zu verwenden, finden Sie unter `ElementOperations.Merge().` Anpassen des [Kopier Verhaltens](../modeling/customizing-copy-behavior.md).|
|Zusätzliche Verknüpfungen beim Einfügen erstellen|Überschreiben von clipboardcommandset. processonpastecommand ()|
|Aktivieren von Drag & Drop aus diesem Diagramm, anderen DSLs-und Windows-Elementen|Weitere Informationen finden [Sie unter Gewusst wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md) .|
|Ermöglicht das Ziehen einer Form oder eines Tools auf eine untergeordnete Form (z. b. einen Port), als ob Sie auf das übergeordnete Element gezogen würde.|Definieren Sie eine elementmergedirektive für die Zielobjekt Klasse, um das gelöschte Objekt an das übergeordnete Objekt weiterzuleiten. Siehe [Anpassen der Element Erstellung und-](../modeling/customizing-element-creation-and-movement.md)Verschiebung.|
|Ermöglicht, dass eine Form oder ein Tool auf eine Form gezogen wird und zusätzliche Verknüpfungen oder Objekte erstellt werden. Beispielsweise, um zuzulassen, dass ein Kommentar auf einem Element abgelegt wird, mit dem es verknüpft werden soll.|Definieren Sie eine elementmergedirektive für die Zieldomänen Klasse, und definieren Sie die zu generierenden Verknüpfungen. In komplexen Fällen können Sie benutzerdefinierten Code hinzufügen. Siehe [Anpassen der Element Erstellung und-](../modeling/customizing-element-creation-and-movement.md)Verschiebung.|
|Erstellen Sie eine Gruppe von Elementen mit einem Tool. Beispielsweise eine Komponente mit einer festgelegten Anzahl von Ports.|Überschreiben Sie die Toolbox Initialisierungs Methode in ToolboxHelper.cs. Erstellen Sie einen Element Gruppen Prototyp (EGP), der die Elemente und deren Beziehungslinks enthält. Weitere Informationen finden Sie [unter Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Fügen Sie die Formen "Principal" und "Port" im EGP ein, oder definieren Sie boundsrules, um die Port Formen zu positionieren, wenn die EGP-Instanz instanziiert wird.|
|Verwenden Sie ein Verbindungs Tool, um mehrere Beziehungstypen zu instanziieren.|Fügen Sie dem Verbindungs-Generator, der vom Tool aufgerufen wird, Link Verbindungs Direktiven (LCD) hinzu. Die LCDs bestimmen den Beziehungstyp aus den Typen der beiden Elemente. Um dies abhängig von den Zuständen der Elemente zu machen, können Sie benutzerdefinierten Code hinzufügen. Weitere Informationen finden Sie [unter Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).|
|Kurzinfo-Tools: der Benutzer kann auf ein beliebiges Tool doppelklicken, um viele Formen oder Connectors nacheinander zu erstellen.|Wählen Sie im DSL-Explorer den `Editor` Knoten aus. In der Eigenschaftenfenster werden in der Festlegung die **Elemente der kurztoolbox verwendet**.|
|Menübefehle definieren|Weitere Informationen finden [Sie unter Gewusst wie: Ändern eines Standard Menübefehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md) .|
|Einschränken des Modells mit Validierungsregeln|Siehe [Validierung in einer Domain-Specific Sprache](../modeling/validation-in-a-domain-specific-language.md)|
|Generieren von Code, Konfigurationsdateien oder Dokumenten aus einer DSL.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|
|Passen Sie an, wie Modelle in einer Datei gespeichert werden.|Siehe [Anpassen von File Storage und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Speichern von Modellen in Datenbanken oder anderen Medien.|Docdata für *YourLanguage* außer Kraft setzen<br /><br /> Siehe [Anpassen von File Storage und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integrieren Sie mehrere DSLs, damit Sie als Teil einer Anwendung funktionieren.|Weitere Informationen finden [Sie unter Integrieren von Modellen mit Visual Studio-ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Erlauben Sie, dass Ihre DSL von Drittanbietern erweitert wird, und Steuern Sie die Erweiterung.|[Erweitern von DSL mittels MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Weitere Informationen

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Schreiben von Code zum Anpassen einer Domain-Specific Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
