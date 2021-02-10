---
title: Erstellen und Konfigurieren von Typmembern (Klassen-Designer)
description: Lernen Sie, Member Typen in einem Klassendiagramm hinzuzufügen und diese Member im Fenster „Klassendetails“ zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 897001a5ac10e8a8e1eef96feca4113afa5e1ebf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880566"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Erstellen und Konfigurieren von Typmembern im Klassen-Designer

Sie können diese Member zu Typen in einem Klassendiagramm hinzufügen und diese Member im Fenster **Klassendetails** konfigurieren:

|**Type**|**Member, die der Typ enthalten kann**|
|--------------| - |
|Klasse|Methode, Eigenschaft (bei C# und Visual Basic), Feld, Ereignis (bei C# und Visual Basic), Konstruktor (Methode), Destruktor (Methode), Konstante|
|Enum|Member|
|Interface|Methode, Eigenschaft, Ereignis (bei C# und Visual Basic)|
|Abstrakte Klasse|Methode, Eigenschaft (bei C# und Visual Basic), Feld, Ereignis (bei C# und Visual Basic), Konstruktor (Methode), Destruktor (Methode), Konstante|
|Struktur (Struct in C#)|Methode, Eigenschaft (bei C# und Visual Basic), Feld, Ereignis (bei C# und Visual Basic), Konstruktor (Methode), Konstante|
|delegate|-Parameter von|
|Modul (nur VB)|Methode, Eigenschaft, Feld, Ereignis, Konstruktor, Konstante|

> [!NOTE]
> Erhöhen Sie die Präzision von Eigenschaftsdeklarationen durch automatisch implementierte Eigenschaften (nur C#), wenn in den Get- und Set-Zugriffsmethoden der Eigenschaft keine zusätzliche Logik erforderlich ist. Klicken Sie im Menü **Klassendiagramm** auf **Memberformat ändern** > **Vollständige Signatur anzeigen**, um die vollständige Signatur anzuzeigen. Weitere Informationen über automatisch implementierte Eigenschaften finden Sie unter [Automatisch implementierte Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Unterstützender Inhalt|
|----------| - |
|**Erste Schritte:** Bevor Sie Typmember erstellen und konfigurieren, müssen Sie das Fenster **Klassendetails** öffnen.|- [Öffnen des Fensters „Klassendetails“](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Hinweise zur Verwendung von Klassendetails](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Anzeigen von schreibgeschützten Informationen](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Tastenkombinationen und Mausaktionen im Klassendiagramm und im Fenster „Klassendetails“](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Erstellen und Ändern von Typmembern:** Mithilfe des Fensters **Klassendetails** können Sie neue Member erstellen, Member ändern und einer Methode Parameter hinzufügen.|- [Erstellen von Membern](creating-and-configuring-type-members.md#create-members)<br />- [Ändern von Typmembern](creating-and-configuring-type-members.md#modify-type-members)<br />- [Hinzufügen von Parametern zu Methoden](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Öffnen des Fensters „Klassendetails“

Standardmäßig wird das Fenster **Klassendetails** automatisch angezeigt, wenn Sie ein neues Klassendiagramm öffnen. Weitere Informationen finden Sie unter [How to: Add Class Diagrams to Projects (Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten)](how-to-add-class-diagrams-to-projects.md). Sie können das Fenster **Klassendetails** jedoch auch über die folgenden Methoden öffnen:

- Klicken Sie mit der rechten Maustaste auf eine Klasse im Diagramm, um ein Kontextmenü anzuzeigen, und klicken Sie anschließend auf **Klassendetails**.

- Klicken Sie in der Menüleiste auf **Ansicht** > **Weitere Fenster** > **Klassendetails**.

## <a name="create-members"></a>Erstellen von Membern

Sie können einen Member mit einem der folgenden Tools erstellen:

- **Klassen-Designer**

- Symbolleiste des Fensters **Klassendetails**

- Fenster **Klassendetails**

> [!NOTE]
> Mit den in diesem Abschnitt beschriebenen Verfahren können Sie außerdem Konstruktoren und Destruktoren erstellen. Beachten Sie, dass es sich bei Konstruktoren und Destruktoren um spezielle Methoden handelt, die in Form von Klassendiagrammen im Depot **Methoden** und im Raster des Fensters **Klassendetails** im Abschnitt **Methoden** angezeigt werden.

> [!NOTE]
> Der Parameter ist die einzige Entität, die Sie einem Delegaten hinzufügen können. Beachten Sie, dass das Verfahren „So erstellen Sie einen Member mithilfe der Symbolleiste des Fensters **Klassendetails**“ für diese Aktion nicht angewendet werden kann.

### <a name="create-a-member-using-class-designer"></a>Erstellen eines Members mit dem Klassen-Designer

1. Klicken Sie mit der rechten Maustaste auf den Typ, dem Sie einen Member hinzufügen möchten, zeigen Sie auf **Hinzufügen**, und wählen Sie dann den hinzuzufügenden Membertyp aus.

     Daraufhin wird eine neue Membersignatur erstellt und dem Typ hinzugefügt. Der Signatur wird ein Standardname zugewiesen, den Sie im **Klassen-Designer**, im Fenster **Klassendetails** oder im Fenster **Eigenschaften** ändern können.

2. Wahlweise können Sie weitere Memberdetails angeben, z. B. den Typ.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Erstellen eines Members mithilfe der Symbolleiste des Fensters „Klassendetails“

1. Wählen Sie auf der Diagrammoberfläche den Typ aus, dem Sie einen Member hinzufügen möchten.

     Der Typ erhält den Fokus, und sein Inhalt wird im Fenster **Klassendetails** angezeigt.

2. Klicken Sie auf der Symbolleiste des Fensters **Klassendetails** auf das obere Symbol, und wählen Sie **Neuer \<member>** aus der Dropdownliste aus.

     Der Cursor wird in das Feld **Name** in einer Zeile für die gewünschte Art von Member verschoben. Wenn Sie z.B. auf **Neue Eigenschaft** klicken, wird der Cursor in eine neue Zeile im Abschnitt **Eigenschaften** des Fensters **Klassendetails** verschoben.

3. Geben Sie den Namen des zu erstellenden Members ein, und drücken Sie die EINGABETASTE (oder verschieben Sie den Fokus, z. B. durch Drücken der TAB-TASTE).

     Daraufhin wird eine neue Membersignatur erstellt und dem Typ hinzugefügt. Der Member ist nun im Code vorhanden und wird im **Klassen-Designer**, im Fenster **Klassendetails** und im Eigenschaftenfenster angezeigt.

4. Wahlweise können Sie weitere Memberdetails angeben, z. B. den Typ.

### <a name="create-a-member-using-the-class-details-window"></a>Erstellen eines Members mithilfe des Fensters „Klassendetails“

1. Wählen Sie auf der Diagrammoberfläche den Typ aus, dem Sie einen Member hinzufügen möchten.

     Der Typ erhält den Fokus, und sein Inhalt wird im Fenster **Klassendetails** angezeigt.

2. Klicken Sie im Fenster **Klassendetails** in dem Abschnitt, der die Art von Member enthält, die hinzugefügt werden soll, auf **\<add member>** . Wenn Sie z. B. ein Feld hinzufügen möchten, klicken Sie auf **\<add field>** .

3. Geben Sie den Namen des zu erstellenden Members ein, und drücken Sie die EINGABETASTE.

     Daraufhin wird eine neue Membersignatur erstellt und dem Typ hinzugefügt. Der Member ist nun im Code vorhanden und wird im **Klassen-Designer**, im Fenster **Klassendetails** und im Eigenschaftenfenster angezeigt.

4. Wahlweise können Sie weitere Memberdetails angeben, z. B. den Typ.

    > [!NOTE]
    > Sie können Member auch mithilfe von Tastenkombinationen erstellen. Weitere Informationen finden Sie unter [Tastenkombinationen und Mausaktionen im Klassendiagramm und Fenster „Klassendetails“ (Klassen-Designer)](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Ändern von Typmembern

Mit dem Klassen-Designer können Sie die Member der Typen ändern, die im Diagramm angezeigt werden. Sie können die Member jedes nicht schreibgeschützten Typs ändern, die in einem Klassendiagramm angezeigt werden. Ändern Sie Typmembers, indem Sie die direkte Bearbeitung auf der Entwurfsoberfläche, im Eigenschaftenfenster und im Fenster **Klassendetails** verwenden.

Alle im Fenster **Klassendetails** angezeigten Members stellen die Members der Typen im Klassendiagramm dar. Es gibt vier Arten von Membern: Methoden, Eigenschaften, Felder und Ereignisse.

Alle Memberzeilen werden unter Überschriften anzeigt, mit denen die Member nach Typ gruppiert werden. So werden beispielsweise alle Eigenschaften unter der Überschrift **Eigenschaften** angezeigt. Diese kann als Knoten im Raster reduziert oder erweitert werden.

In jeder Memberzeile werden die folgenden Elemente angezeigt:

- **Membersymbol**

     Jede Memberart wird mit einem besonderen Symbol dargestellt. Zeigen Sie mit der Maus auf das Membersymbol, um die Signatur des Members einzublenden. Klicken Sie auf das Membersymbol oder in den Leerraum links neben dem Membersymbol, um die Zeile auszuwählen.

- **Membername**

     In der Spalte **Name** in einer Memberzeile wird der Name des Members angezeigt. Dieser Name wird auch im Eigenschaftenfenster in der Eigenschaft **Name** angezeigt. Verwenden Sie diese Zelle, um den Namen eines beliebigen nicht schreibgeschützten Members zu ändern.

     Zeigen Sie mit dem Mauszeiger auf den Namen des Members, um ihn vollständig anzuzeigen, wenn die Spalte **Name** nicht breit genug ist.

- **Memberart**

     In der Zelle **Membertyp** wird IntelliSense verwendet. Sie können daher einen Typ aus der Liste aller Typen auswählen, die im aktuellen Projekt oder in Projekten, auf die verwiesen wird, verfügbar sind.

- **Membermodifizierer**

     Ändern Sie den Sichtbarkeitsmodifizierer eines Members in `Public` (`public`), `Private` (`private`), `Friend` (`internal`), `Protected` (`protected`), `Protected Friend` (`protected internal`) oder `Default`.

- **\<add member>**

     Die letzte Zeile des Fensters **Klassendetails** enthält in der Zelle **Name** den Text **\<add member>** . Wenn Sie auf diese Zelle klicken, können Sie einen neuen Member erstellen. Weitere Informationen finden Sie unter [Erstellen von Membern](creating-and-configuring-type-members.md#create-members).

- **Membereigenschaften im Eigenschaftenfenster**

     Im Fenster **Klassendetails** wird eine Teilmenge der im Eigenschaftenfenster angezeigten Membereigenschaften angezeigt. Nach einer Änderung einer Eigenschaft an einem Ort wird der Wert der Eigenschaft global aktualisiert. Dies bedeutet u. a., dass ihr Wert auch am anderen Ort angezeigt wird.

- **Zusammenfassung**

     In der Zelle **Zusammenfassung** ist eine Zusammenfassung der Informationen zum Member verfügbar. Klicken Sie in der Zelle **Zusammenfassung** auf die Auslassungszeichen, um die Informationen **Zusammenfassung**, **Rückgabetyp** und **Hinweise** für den Member anzuzeigen und zu bearbeiten.

- **Ausblenden**

     Wenn das Kontrollkästchen **Ausblenden** aktiviert ist, wird der Member im Typ nicht angezeigt.

### <a name="to-modify-a-type-member"></a>So ändern Sie einen Typmember

1. Wählen Sie mit dem Klassen-Designer einen Typ aus.

2. Wenn das Fenster **Klassendetails** nicht angezeigt wird, klicken Sie auf der Symbolleiste des Klassen-Designers auf die Schaltfläche **Klassendetails**.

3. Bearbeiten Sie die Werte in den Feldern des Rasters im Fenster **Klassendetails**. Drücken Sie nach jeder Änderung die EINGABETASTE, oder aktivieren Sie auf andere Weise ein anderes Feld, z. B. durch Drücken der TAB-TASTE. Die Änderungen sind im Code sofort sichtbar.

    > [!NOTE]
    > Wenn Sie nur den Namen eines Members ändern möchten, können Sie dafür die direkte Bearbeitung verwenden.

## <a name="add-parameters-to-methods"></a>Hinzufügen von Parametern zu Methoden

Fügen Sie Methoden Parameter hinzu, indem Sie das Fenster **Klassendetails** verwenden. Parameter können als erforderlich oder optional konfiguriert werden. Wenn ein Wert für die Eigenschaft **Optional Default** angegeben wird, wird der Designer angewiesen, Code als optionalen Parameter zu generieren.

Parameterzeilen enthalten die folgenden Elemente:

- **Name**

     In der Spalte **Name** in einer Parameterzeile wird der Name des Parameters angezeigt. Dieser Name wird auch im Eigenschaftenfenster in der Eigenschaft **Name** angezeigt. In dieser Zelle können Sie den Namen eines nicht schreibgeschützten Parameters ändern.

     Zeigen Sie auf den Parameternamen, um ihn anzuzeigen, wenn die Spalte **Name** nicht breit genug ist, um den Namen vollständig anzuzeigen.

- **Type**

     In der Zelle **Parametertyp** wird IntelliSense verwendet, d.h., Sie können einen Typ aus einer Liste aller im aktuellen Projekt oder in Projekten, auf die verwiesen wird, verfügbaren Typen auswählen.

- **Modifizierer**

     In der Zelle **Modifizierer** in einer Parameterzeile kann ein neuer Modifizierer für den Parameter eingegeben und angezeigt werden. Wenn Sie einen neuen Parametermodifizierer eingeben möchten, verwenden Sie das Dropdown-Listenfeld, um in C# zwischen **None**, **ref**, **out** oder **params** und in VB zwischen **ByVal**, **ByRef** oder **ParamArray** zu wählen.

- **Zusammenfassung**

     In der Zelle **Zusammenfassung** in einer Parameterzeile können Sie Codekommentare eingeben, die in IntelliSense angezeigt werden, wenn Sie den Parameter in den Code-Editor eingeben.

- **\<add parameter>**

     Die letzte Parameterzeile eines Members enthält im Feld **Name** den Text **<Parameter hinzufügen\>** . Klicken Sie in die Zelle, um einen neuen Parameter zu erstellen. Weitere Informationen finden Sie unter [So fügen Sie einer Methode einen Parameter hinzu](creating-and-configuring-type-members.md#add-parameters-to-methods).

Im Fenster **Eigenschaften** werden die gleichen Parametereigenschaften angezeigt wie im Fenster **Klassendetails**: **Name**, **Typ**, **Modifizierer**, **Zusammenfassung** sowie die Eigenschaft **Optional Default** (Optionaler Standard). Wenn Sie eine Eigenschaft in einem der beiden Fenster ändern, wird der Wert der Eigenschaft global aktualisiert, d. h. auch die Anzeige des zugehörigen Werts im jeweils anderen Fenster.

> [!NOTE]
> Informationen zum Hinzufügen eines Parameters zu einem Delegaten finden Sie unter [Erstellen von Membern](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Ein Destruktor ist zwar eine Methode, kann jedoch nicht über Parameter verfügen.

### <a name="to-add-a-parameter-to-a-method"></a>So fügen Sie einer Methode einen Parameter hinzu

1. Klicken Sie auf der Diagrammoberfläche auf den Typ, der die Methode enthält, der Sie einen Parameter hinzufügen möchten.

     Der Typ erhält den Fokus, und sein Inhalt wird im Fenster **Klassendetails** angezeigt.

2. Erweitern Sie im Fenster **Klassendetails** die Zeile der Methode, der Sie einen Parameter hinzufügen möchten.

     Es wird eine eingerückte Parameterzeile angezeigt, die nur ein Klammernpaar und die Wörter **\<add parameter>** enthält.

3. Klicken Sie auf **\<add parameter>** , geben Sie den Namen des neuen Parameters ein, und drücken Sie die **EINGABETASTE**.

     Der neue Parameter wird der Methode und dem Code der Methode hinzugefügt. Er wird im Fenster **Klassendetails** und im Eigenschaftenfenster angezeigt.

4. Wahlweise können Sie weitere Parameterdetails angeben, z. B. den Typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>So fügen Sie einer Methode einen optionalen Parameter hinzu

1. Klicken Sie auf der Diagrammoberfläche auf den Typ, der die Methode enthält, der Sie einen optionalen Parameter hinzufügen möchten.

     Der Typ erhält den Fokus, und sein Inhalt wird im Fenster **Klassendetails** angezeigt.

2. Erweitern Sie im Fenster **Klassendetails** die Zeile der Methode, der Sie einen optionalen Parameter hinzufügen möchten.

     Es wird eine eingerückte Parameterzeile angezeigt, die nur ein Klammernpaar und die Wörter **\<add parameter>** enthält.

3. Klicken Sie auf **\<add parameter>** , geben Sie den Namen des neuen Parameters ein, und drücken Sie die **EINGABETASTE**.

     Der neue Parameter wird der Methode und dem Code der Methode hinzugefügt. Er wird im Fenster **Klassendetails** und im Eigenschaftenfenster angezeigt.

4. Geben Sie im Eigenschaftenfenster einen Wert für die Eigenschaft **Optional Default** ein. Wenn Sie die "Optional Default"-Eigenschaft eines Parameters festlegen, wird dieser Parameter optional.

    > [!NOTE]
    > Optionale Parameter müssen in der Parameterliste die letzten Parameter sein.

## <a name="class-details-usage-notes"></a>Hinweise zur Verwendung von Klassendetails

Beachten Sie folgende Tipps zur Verwendung des Fensters **Klassendetails**.

### <a name="editable-and-non-editable-cells"></a>Bearbeitbare und nicht bearbeitbare Zellen

Alle Zellen im Fenster **Klassendetails** sind bis auf einige Ausnahmen bearbeitbar:

- Wenn ein Typ sich z.B. in einer Assembly befindet, auf die verwiesen wird, ist der gesamte Typ schreibgeschützt. Wenn Sie die Form im Klassen-Designer auswählen, werden die entsprechenden Details im Fenster **Klassendetails** schreibgeschützt angezeigt.

- Für Indexer ist der Name schreibgeschützt, der Rest (Typ, Modifizierer, Zusammenfassung) ist jedoch bearbeitbar.

- Alle Generics weisen im Fenster **Klassendetails** schreibgeschützte Parameter auf. Um einen generischen Parameter zu ändern, bearbeiten Sie den entsprechenden Quellcode.

- Der Name des für einen generischen Typ definierten Typparameters ist schreibgeschützt.

- Wenn der Code eines Typs fehlerhaft (nicht analysierbar) ist, wird der Inhalt des Typs im Fenster **Klassendetails** schreibgeschützt angezeigt.

### <a name="the-class-details-window-and-source-code"></a>Quellcode und das Fenster „Klassendetails“

- Klicken Sie zum Anzeigen von Quellcode im Fenster **Klassendetails** (oder im Klassen-Designer) mit der rechten Maustaste auf eine Form, und klicken Sie anschließend auf „Code anzeigen“. Die Quellcodedatei wird geöffnet, und es wird ein Bildlauf zum ausgewählten Element durchgeführt.

- Jede Änderung des Quellcodes wird sofort durch die Anzeige von Signaturinformationen im Klassen-Designer und im Fenster **Klassendetails** sichtbar. Falls das Fenster **Klassendetails** zu diesem Zeitpunkt geschlossen ist, werden die neuen Informationen beim nächsten Öffnen des Fensters sichtbar.

- Wenn der Code eines Typs fehlerhaft (nicht analysierbar) ist, wird der Inhalt des Typs im Fenster **Klassendetails** schreibgeschützt angezeigt.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Zwischenablagefunktion im Fenster „Klassendetails“

Sie können Felder oder Zeilen im Fenster **Klassendetails** kopieren oder ausschneiden und in einen anderen Typ einfügen. Es können nur Zeilen ausgeschnitten werden, die nicht schreibgeschützt sind. Wenn Sie die Zeile einfügen, wird zur Vermeidung eines Konflikts im Fenster **Klassendetails** ein neuer (vom Namen der kopierten Zeile abgeleiteter) Name zugewiesen.

## <a name="display-of-read-only-information"></a>Anzeigen von schreibgeschützten Informationen

Im Klassen-Designer und im Fenster **Klassendetails** können die Typen (und Members der Typen) für folgende Elemente angezeigt werden:

- ein Projekt, das ein Klassendiagramm enthält

- ein Projekt, auf das von einem Projekt verwiesen wird, das ein Klassendiagramm enthält

- eine Assembly, auf die von einem Projekt verwiesen wird, das ein Klassendiagramm enthält

In den beiden letzten Fällen ist die Entität (ein Typ oder Member), auf die verwiesen wird, im entsprechenden Klassendiagramm schreibgeschützt.

Ein gesamtes Projekt oder Projektteile, z. B. einzelne Dateien, können schreibgeschützt sein. Ein Projekt oder eine zugehörige Datei ist in der Regel dann schreibgeschützt, wenn die Quellcodeverwaltung verwendet wird (und das Projekt nicht ausgecheckt wurde), das Projekt oder die Datei in einer externen Assembly enthalten ist oder das Betriebssystem die Dateien als schreibgeschützt festlegt.

**Quellcodeverwaltung**

Da ein Klassendiagramm in einem Projekt als Datei gespeichert wird, müssen Sie das Projekt auschecken, damit im Klassen-Designer oder im Fenster **Klassendetails** vorgenommene Änderungen übernommen werden.

**Schreibgeschützte Projekte**

Das Projekt ist möglicherweise nicht aufgrund der Quellcodeverwaltung, sondern aus einem anderen Grund schreibgeschützt. Wenn Sie das Projekt schließen, wird ein Dialogfeld mit der Frage angezeigt, ob die Projektdatei überschrieben werden soll, Änderungen verworfen werden sollen oder der Vorgang abgebrochen werden soll. Wenn Sie festlegen, dass die Projektdatei überschrieben werden soll, werden die Projektdateien überschrieben und mit Lese- und Schreibzugriff versehen. Die neue Klassendiagrammdatei wird hinzugefügt.

**Schreibgeschützte Typen**

Wenn Sie versuchen, ein Projekt zu speichern, das einen Typ enthält, dessen Quellcodedatei schreibgeschützt ist, wird das Dialogfeld **Schreibgeschützte Datei speichern** angezeigt. Hier haben Sie die Möglichkeit, die Datei unter einem neuen Namen und/oder an einem neuen Speicherort zu speichern oder die schreibgeschützte Datei zu überschreiben. Wenn Sie die Datei überschreiben, ist die Datei nicht mehr schreibgeschützt.

Weist eine Codedatei einen Syntaxfehler auf, werden die Formen, die den Code in der Datei anzeigen, so lange mit Schreibschutz versehen, bis der Syntaxfehler behoben wird. Formen in diesem Zustand zeigen roten Text und ein rotes Symbol mit der Quickinfo "Die Quellcodedatei enthält einen Analysefehler" an.

Ein Typ, auf den verwiesen wird (z.B. ein .NET-Typ) und der in einem anderen Projektknoten oder in dem Knoten einer referenzierten Assembly vorhanden ist, wird auf der Entwurfsoberfläche des Klassen-Designers als schreibgeschützt angezeigt. Ein lokaler Typ im geöffneten Projekt ist mit Lese- und Schreibzugriff versehen, und seine Form wird auf der Entwurfsoberfläche des Klassen-Designers entsprechend angegeben.

Indexer sind im Code und im Fenster **Klassendetails** mit Lese- und Schreibzugriff versehen. Der Indexername hingegen ist schreibgeschützt.

Partielle Methoden können nicht mithilfe des Klassen-Designers oder des Fenster **Klassendetails** bearbeitet werden. Verwenden Sie hierfür den Code-Editor.

Nativer C++-Code kann nicht mithilfe des Klassen-Designers oder des Fenster **Klassendetails** bearbeitet werden. Verwenden Sie hierfür den Code-Editor.

## <a name="see-also"></a>Siehe auch

- [Anzeigen von Typen und Beziehungen](designing-and-viewing-classes-and-types.md)
- [Refactoring von Klassen und Typen](refactoring-classes-and-types.md)
