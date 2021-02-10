---
title: Erstellen benutzerdefinierter Ansichten von C++-Objekten
description: Verwenden des Natvis-Frameworks zum Anpassen der Art und Weise, in der Visual Studio native Typen im Debugger anzeigt
ms.date: 03/02/2020
ms.topic: how-to
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 5a219ae5257bce2a84dc17556939a44ecb02dcce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857739"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Erstellen benutzerdefinierter Ansichten von C++-Objekten im Debugger mit dem Natvis-Framework

Das Visual Studio *Natvis*-Framework passt die Art und Weise an, wie native Typen in Variablenfenstern des Debuggers, z. B. in den Fenstern **Lokal** und **Überwachen** sowie in **DataTips**, angezeigt werden. Natvis-Visualisierungen können dazu beitragen, die von Ihnen erstellten Typen während des Debuggens besser sichtbar zu gestalten.

Natvis ersetzt die Datei *autoexp.dat*, die in früheren Versionen von Visual Studio verwendet wurde, durch XML-Syntax, bessere Diagnosefunktionen, eine bessere Versionskontrolle und Unterstützung mehrerer Dateien.

> [!NOTE]
> Natvis-Anpassungen arbeiten mit Klassen und Strukturen, jedoch nicht mit Typedefs.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Natvis-Visualisierungen

Sie verwenden das Natvis-Framework zum Erstellen von Visualisierungsregeln für Typen, die Sie erstellen, damit sie von Entwicklern beim Debuggen einfacher angezeigt werden können.

Die folgende Abbildung zeigt z. B. eine Variable vom Typ [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) in einem Debuggerfenster ohne angewandte benutzerdefinierte Visualisierungen.

![TextBox-Standardvisualisierung](../debugger/media/dbg_natvis_textbox_default.png "TextBox-Standardvisualisierung")

Die hervorgehobene Zeile zeigt die `Text` -Eigenschaft der `TextBox` -Klasse. Die komplexe Klassenhierarchie gestaltet es schwierig, diese Eigenschaft zu finden. Der Debugger weiß nicht, wie der benutzerdefinierte Zeichenfolgentyp zu interpretieren ist, sodass Sie die im Textfeld enthaltene Zeichenfolge nicht sehen können.

Das gleiche `TextBox`-Objekt sieht im Variablenfenster viel einfacher aus, wenn die benutzerdefinierten Natvis-Visualisierungsregeln angewendet werden. Die wichtigen Member der Klasse werden gemeinsam angezeigt, und der Debugger zeigt den zugrunde liegenden Zeichenfolgenwert des benutzerdefinierten Zeichenfolgentyps an.

![TextBox-Daten mit Schnellansicht](../debugger/media/dbg_natvis_textbox_visualizer.png "TextBox-Daten mit Schnellansicht")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Verwenden von NATVIS-Dateien in C++-Projekten

Natvis verwendet *NATVIS*-Dateien zur Angabe von Visualisierungsregeln. Eine *NATVIS*-Datei ist einfach eine XML-Datei mit der *NATVIS*-Erweiterung. Das Natvis-Schema wird in *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd* definiert.

Die grundlegende Struktur einer *NATVIS*-Datei besteht aus einem oder mehreren `Type`-Elementen, die Visualisierungseinträge darstellen. Der vollqualifizierte Name der einzelnen `Type`-Elemente wird in Ihrem `Name`-Attribut angegeben.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio stellt im Ordner *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* einige *NATVIS*-Dateien bereit. Diese Dateien enthalten Visualisierungsregeln für viele allgemeine Typen und können als Beispiele für das Schreiben von Visualisierungen für neue Typen dienen.

### <a name="add-a-natvis-file-to-a-c-project"></a>Hinzufügen einer NATVIS-Datei zu einem C++-Projekt

Sie können *NATVIS*-Dateien zu jedem C++-Projekt hinzufügen.

**So fügen Sie eine neue *NATVIS*-Datei hinzu**

1. Wählen Sie den C++-Projektknoten im **Projektmappen-Explorer** und dann **Projekt** > **Neues Element hinzufügen** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen** > **Neues Element** aus.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Visual C++**  > **Dienstprogramm** > **Debugger-Visualisierungsdatei (.natvis)** aus.

1. Benennen Sie die Datei, und wählen Sie **Hinzufügen** aus.

   Die neue Datei wird im **Projektmappen-Explorer** hinzugefügt und im Dokumentbereich von Visual Studio geöffnet.

Der Visual Studio-Debugger lädt *NATVIS*-Dateien in C++-Projekte automatisch und schließt sie standardmäßig auch in die *PDB*-Datei ein, wenn das Projekt erstellt wird. Wenn Sie die erstellte App debuggen, lädt der Debugger die *NATVIS*-Datei aus der *PDB*-Datei, auch wenn Sie das Projekt nicht geöffnet haben. Wenn Sie nicht möchten, dass die *NATVIS*-Datei in der *PDB* enthalten ist, können Sie sie aus der erstellten *PDB*-Datei ausschließen.

**So schließen Sie eine *NATVIS*-Datei aus einer *PDB*-Datei aus**

1. Wählen Sie die *NATVIS*-Datei im **Projektmappen-Explorer** und dann das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie anschließend **Eigenschaften** aus.

1. Verwenden Sie den Dropdownpfeil neben **Vom Build ausgeschlossen**, und wählen Sie dann **Ja** und anschließend **OK** aus.

>[!NOTE]
>Verwenden Sie zum Debuggen von ausführbaren Projekten die Projektmappenelemente, um alle *NATVIS*-Dateien hinzuzufügen, die sich nicht in der *PDB*-Datei befinden, da kein C++-Projekt verfügbar ist.

>[!NOTE]
>Natvis-Regeln, die aus einer *PDB*-Datei geladen werden, gelten nur für die Typen in den Modulen, auf die sich die *PDB*-Datei bezieht. Wenn z. B. *Module1.pdb* einen Natvis-Eintrag für einen Typ namens `Test` enthält, gilt er nur für die Klasse `Test` in *Module1.dll*. Wenn ein anderes Modul ebenfalls eine Klasse mit dem Namen `Test` definiert, gilt der Natvis-Eintrag in der Datei *Module1.pdb* hierfür nicht.

**So installieren und registrieren Sie eine *NATVIS*-Datei über ein VSIX-Paket**

Mit einem VSIX-Paket können *NATVIS*-Dateien installiert und registriert werden. Unabhängig davon, wo Sie installiert sind, werden alle registrierten *NATVIS*-Dateien beim Debuggen automatisch abgeholt.

1. Schließen Sie die *NATVIS*-Datei in das VSIX-Paket ein. Beispielsweise für die folgende Projektdatei:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registrieren Sie die *NATVIS*-Datei in der Datei *source.extension.vsixmanifest*:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Speicherorte der NATVIS-Datei

Sie können *NATVIS*-Dateien zu Ihrem Benutzerverzeichnis oder einem Systemverzeichnis hinzufügen, wenn sie für mehrere Projekte gelten sollen.

Die *NATVIS*-Dateien werden in der folgenden Reihenfolge ausgewertet:

1. Jede *NATVIS*-Datei, die in eine *PDB*-Datei eingebettet ist, die Sie debuggen, sofern keine Datei mit demselben Namen in dem geladenen Projekt vorhanden ist.

2. Alle *NATVIS*-Dateien, die sich in einem geladenen C++-Projekt oder in einer Projektmappe der obersten Ebene befinden. Diese Gruppe enthält alle geladenen C++-Projekte, einschließlich Klassenbibliotheken, aber keine Projekte in anderen Sprachen.

3. Alle *NATVIS*-Dateien, die über ein VSIX-Paket installiert und registriert werden.

::: moniker range="vs-2017"

4. Das benutzerspezifische Natvis-Verzeichnis (z. B. *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Das benutzerspezifische Natvis-Verzeichnis (z. B. *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. Das systemweite Natvis-Verzeichnis ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Dieses Verzeichnis enthält die *NATVIS*-Dateien, die mit Visual Studio installiert werden. Wenn Sie über Administratorrechte verfügen, können Sie Dateien zu diesem Verzeichnis hinzufügen.

## <a name="modify-natvis-files-while-debugging"></a>Ändern von NATVIS-Dateien beim Debuggen

Sie können eine *NATVIS*-Datei in der integrierten Entwicklungsumgebung (IDE) ändern, während Sie ihr Projekt debuggen. Öffnen Sie die Datei in derselben Instanz von Visual Studio, mit der Sie debuggen, ändern Sie sie, und speichern Sie sie anschließend. Nach dem Speichern der Datei werden die Fenster **Überwachen** und **Lokal** aktualisiert, um die Änderung zu übernehmen.

Sie können *NATVIS*-Dateien zudem in einer Projektmappe, die Sie debuggen, hinzufügen oder aus ihr löschen. Visual Studio fügt die relevanten Visualisierungen hinzu bzw. entfernt sie.

Sie können *NATVIS*-Dateien, die in *PDB*-Dateien eingebettet sind, während des Debuggens nicht aktualisieren.

Wenn Sie die *NATVIS*-Datei außerhalb von Visual Studio ändern, werden die Änderungen nicht automatisch wirksam. Zum Aktualisieren der Debuggerfenster können Sie den Befehl **.natvisreload** im Fenster **Direkt** neu auswerten. Dann treten die Änderungen in Kraft, ohne dass die Debugsitzung neu gestartet werden muss.

Verwenden Sie auch den Befehl **.natvisreload**, um ein Upgrade der *NATVIS*-Datei auf eine neuere Version durchzuführen. Die *NATVIS*-Datei kann z. B. in die Quellcodeverwaltung eingecheckt werden, und Sie möchten die letzten Änderungen übernehmen, die jemand anderes vorgenommen hat.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Ausdrücke und Formatierung
Natvis-Visualisierungen verwenden C++-Ausdrücke, um anzuzeigende Datenelementen anzugeben. Zusätzlich zu den Erweiterungen und Einschränkungen von C++-Ausdrücken im Debugger, die in [Kontextoperator (C++)](../debugger/context-operator-cpp.md) beschrieben sind, sollten Sie Folgendes beachten:

- Natvis-Ausdrücke werden im Kontext des Objekts ausgewertet, das in der Schnellansicht und nicht im aktuellen Stapelrahmen angezeigt wird. So bezieht sich `x` in einem Natvis-Ausdruck z. B. auf das Feld namens **x** in dem zu visualisierenden Objekt, nicht auf eine lokale Variable namens **x** in der aktuellen Funktion. Sie können nicht auf lokale Variablen in Natvis-Ausdrücken zugreifen, obwohl Sie auf globale Variablen zugreifen können.

- Natvis-Ausdrücke lassen keine Funktionsauswertung oder Nebeneffekte zu. Funktionsaufrufe und Zuweisungsoperatoren werden ignoriert. Da [systeminterne Debuggerfunktionen](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) keine Nebeneffekte haben, können sie beliebig von jedem Natvis-Ausdruck aufgerufen werden, obwohl andere Funktionsaufrufe nicht zulässig sind.

- Sie können die Anzeige eines Ausdrucks steuern, indem Sie einen der unter [Formatbezeichner in C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) beschriebenen Formatbezeichner verwenden. Formatbezeichner werden ignoriert, wenn der Eintrag intern von Natvis verwendet wird, z. B. der `Size`-Ausdruck in einer [ArrayItems-Erweiterung](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

>[!NOTE]
> Da es sich bei dem NATVIS-Dokument um ein XML-Dokument handelt, können Sie in Ihren Ausdrücken die Operatoren kaufmännisches Und, Größer-als-Zeichen, Kleiner-als-Zeichen und Schiebeoperatoren nicht direkt verwenden. Sie müssen für diese Zeichen sowohl im Elementtext als auch in den Bedingungsanweisungen Escapezeichen verwenden. Beispiel:<br>
> \<Item Name="HiByte"\>(byte)(_flags \&gt;\&gt; 24),x\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) == 0"\>"None"\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) != 0"\>"Some"\</Item\>

## <a name="natvis-views"></a>Natvis-Ansichten

Sie können verschiedene Natvis-Ansichten definieren, um Typen auf unterschiedliche Weise anzuzeigen. Hier ist z. B. eine Visualisierung von `std::vector`, die eine vereinfachte Ansicht namens `simple` definiert. Die `DisplayString`- und `ArrayItems`-Elemente werden in der Standardansicht und der `simple`-Ansicht angezeigt, während die `[size]`- und `[capacity]`-Elemente in der `simple`-Ansicht nicht angezeigt werden.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Verwenden Sie im Fenster **Überwachen** den Formatbezeichner **,view**, um eine alternative Ansicht anzugeben. Die einfache Ansicht wird als **vec,view(simple)** angezeigt:

![Überwachungsfenster mit einfacher Ansicht](../debugger/media/watch-simpleview.png "Überwachungsfenster mit einfacher Ansicht")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis-Fehler

Wenn der Debugger Fehler in einem Visualisierungseintrag erkennt, werden diese ignoriert. Der Typ wird entweder in der unformatierter Form angezeigt, oder es wird eine andere geeignete Visualisierung ausgewählt. Sie können die Natvis-Diagnose verwenden, um zu verstehen, warum der Debugger einen Visualisierungseintrag ignoriert hat, und um zugrunde liegende Syntax- und Analysefehler anzuzeigen.

**So aktivieren Sie die Natvis-Diagnose**

- Legen Sie unter **Extras** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debugging** > **Ausgabefenster** die **Natvis-Diagnosemeldungen (nur C++)** auf **Fehler**, **Warnung** oder **Ausführlich** fest, und wählen Sie dann **OK** aus.

Die Fehler werden im Fenster **Ausgabe** angezeigt.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis-Syntaxverweis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> AutoVisualizer-Element
Bei dem `AutoVisualizer`-Element handelt es sich um den Stammknoten der *NATVIS*-Datei, der das `xmlns:`-Attribut für den Namespace enthält.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Das `AutoVisualizer`-Element kann folgende untergeordnete Elemente aufweisen: [Typ](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer) und [CustomVisualizer](#BKMK_CustomVisualizer).

### <a name="type-element"></a><a name="BKMK_Type"></a> Type-Element

Ein grundlegender `Type` sieht wie dieses Beispiel aus:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Das `Type`-Element gibt Folgendes an:

1. Für welchen Typ die Visualisierung verwendet werden soll (das `Name`-Attribut).

2. Wie der Wert eines Objekts dieses Typs aussehen soll (das `DisplayString` -Element).

3. Wie die Member des Typs aussehen sollen, wenn der Benutzer den Typ in einem variablen Fenster erweitert (der `Expand`-Knoten).

#### <a name="templated-classes"></a>Auf Vorlagen basierende Klassen
Für das `Name`-Attribut des `Type`-Elements kann ein Sternchen (`*`) als Platzhalterzeichen für vorlagenbasierte Klassennamen verwendet werden.

Im folgenden Beispiel wird die gleiche Visualisierung verwendet, unabhängig davon, ob das Objekt `CAtlArray<int>` oder `CAtlArray<float>` ist. Wenn es einen bestimmten Visualisierungseintrag für `CAtlArray<float>` gibt, hat er Vorrang vor dem generischen Objekt.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Sie können auf Vorlagenparameter im Visualisierungseintrag verweisen, indem Sie die Makros „$T1“, „$T2“ usw. verwenden. Beispiele zu diesen Makros finden Sie in den *NATVIS*-Dateien, die in Visual Studio bereitgestellt werden.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Typenabgleich in der Schnellansicht
Wenn ein Visualisierungseintrag nicht überprüft werden kann, wird die nächste verfügbare Visualisierung verwendet.

#### <a name="inheritable-attribute"></a>Inheritable-Attribut
Mit dem optionalen Attribut `Inheritable` wird angegeben, ob eine Visualisierung nur auf einen Basistyp oder auf einen Basistyp und alle abgeleiteten Typen angewendet werden soll. Der Standardwert von `Inheritable` ist `true`.

Im folgenden Beispiel wird die Visualisierung nur auf den `BaseClass`-Typ angewendet:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority-Attribut

Das optionale Attribut `Priority` gibt die Reihenfolge an, in der alternative Definitionen verwendet werden, wenn beim Analysieren einer Definition Fehler auftreten. Die möglichen Werte von `Priority` sind: `Low`, `MediumLow`, `Medium`, `MediumHigh` und `High`. Der Standardwert ist `Medium`. Das `Priority`-Attribut unterscheidet nur zwischen Prioritäten innerhalb derselben *NATVIS*-Datei.

Im folgenden Beispiel wird zunächst der Eintrag analysiert, der mit der 2015 STL übereinstimmt. Wenn beim Analysieren Fehler auftreten, wird der alternative Eintrag für die Version 2013 der STL verwendet:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Optional-Attribut
Sie können ein `Optional`-Attribut für jeden beliebigen Knoten festlegen. Wenn ein Teilausdruck innerhalb eines optionalen Knotens nicht analysiert werden kann, ignoriert der Debugger diesen Knoten, wendet aber die restlichen `Type`-Regeln an. Im folgenden Typ ist `[State]` nicht optional, während `[Exception]` jedoch optional ist.  Wenn `MyNamespace::MyClass` ein Feld namens _`M_exceptionHolder` aufweist, werden sowohl der `[State]`-Knoten als auch der `[Exception]`-Knoten angezeigt, aber wenn es kein `_M_exceptionHolder`-Feld gibt, wird nur der `[State]`-Knoten angezeigt.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Condition-Attribut

Das optionale `Condition` -Attribut ist für viele Visualisierungselemente verfügbar und gibt an, wann eine Visualisierungsregel verwendet werden soll. Wenn der Ausdruck innerhalb des Condition-Attributs in `false` aufgelöst wird, wird die Visualisierungsregel nicht angewendet. Wenn er zu `true` ausgewertet wird oder kein `Condition`-Attribut vorhanden ist, wird die Visualisierung angewendet. Sie können dieses Attribut für die „if-else“-Logik in den Visualisierungseinträgen verwenden.

Beispielsweise weist die folgende Visualisierung zwei `DisplayString`-Elemente für einen intelligenten Zeigertyp auf. Wenn der `_Myptr`-Member leer ist, wird die Bedingung des ersten `DisplayString`-Elements in `true` aufgelöst, wodurch diese Form angezeigt wird. Wenn der `_Myptr`-Member nicht leer ist, wird die Bedingung als `false` ausgewertet, und das zweite `DisplayString`-Element wird angezeigt.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView- und ExcludeView-Attribute

Die Attribute `IncludeView` und `ExcludeView` geben Elemente an, die in bestimmten Ansichten angezeigt oder nicht angezeigt werden sollen. In der folgenden Natvis-Spezifikation von `std::vector` werden in der `simple`-Ansicht die Elemente `[size]` und `[capacity]` nicht angezeigt.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Sie können die Attribute `IncludeView` und `ExcludeView` für Typen und einzelne Member verwenden.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Version-Element
Das `Version`-Element umfasst einen Visualisierungseintrag zu einem bestimmten Modul und einer bestimmten Version. Das `Version`-Element trägt dazu bei, Namenskonflikte zu vermeiden, reduziert unbeabsichtigte Übereinstimmungen und ermöglicht unterschiedliche Visualisierungen für verschiedene Typversionen.

Wenn eine gemeinsame Headerdatei, die von verschiedenen Modulen verwendet wird, einen Typ definiert, wird die versionierte Visualisierung nur angezeigt, wenn der Typ in der angegebenen Modulversion vorliegt.

Im folgenden Beispiel gilt die Visualisierung nur für den `DirectUI::Border`-Typ, der sich in `Windows.UI.Xaml.dll` von Version 1.0 bis 1.5 befindet.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Sie benötigen nicht sowohl `Min` als auch `Max`. Sie sind optionale Attribute. Platzhalterzeichen werden nicht unterstützt.

Das Attribut `Name` hat das Format *filename.ext*, z. B. *hello.exe* oder *some.dll*. Es sind keine Pfadnamen zulässig.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> DisplayString-Element
Das `DisplayString`-Element gibt eine Zeichenfolge an, die als Wert einer Variablen angezeigt werden soll. Beliebige Zeichenfolgen können mit Ausdrücken gemischt werden. Sämtliche Inhalte innerhalb von geschweiften Klammern werden als ein Ausdruck interpretiert. Beispielsweise der folgende `DisplayString`-Eintrag:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Bedeutet, dass Variablen vom Typ `CPoint` wie in dieser Abbildung angezeigt werden:

 ![Verwenden eines DisplayString-Elements](../debugger/media/dbg_natvis_cpoint_displaystring.png "Verwenden eines DisplayString-Elements")

Im `DisplayString`-Ausdruck befinden sich `x` und `y`, die Member von `CPoint` sind, in geschweiften Klammern, sodass ihre Werte ausgewertet werden. Das Beispiel zeigt auch, wie eine geschweifte Klammer mit doppelten geschweiften Klammern (`{{` oder `}}`) mit Escapezeichen versehen werden kann.

> [!NOTE]
> Das `DisplayString` -Element ist das einzige Element, das beliebige Zeichenfolgen und die Syntax mit geschweiften Klammern akzeptiert. Alle anderen Visualisierungselemente akzeptieren nur Ausdrücke, die vom Debugger ausgewertet werden können.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> StringView-Element

Das `StringView`-Element definiert einen Wert, den der Debugger an die integrierte Text-Schnellansicht senden kann. Angenommen, es gibt z. B. die folgende Visualisierung für den `ATL::CStringT`-Typ:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Das `CStringT`-Objekt wird in einem Variablenfenster wie im folgenden Beispiel angezeigt:

![CStringT-DisplayString-Element](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT-DisplayString-Element")

Wenn Sie ein `StringView`-Element hinzufügen, wird dem Debugger mitgeteilt, dass der Wert als Textvisualisierung angezeigt werden kann.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Während des Debuggens können Sie das Lupensymbol neben der Variablen und dann die Option **Text-Schnellansicht** auswählen, um die Zeichenfolge anzuzeigen, auf die **m_pszData** verweist.

 ![CStringT-Daten mit StringView-Schnellansicht](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT-Daten mit StringView-Schnellansicht")

Der `{m_pszData,su}`-Ausdruck enthält den C++-Formatbezeichner **su**, um den Wert als Unicode-Zeichenfolge anzuzeigen. Weitere Informationen finden Sie unter [Formatbezeichner in C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Erweitern eines Elements

Der optionale Knoten `Expand` passt die untergeordneten Elemente eines visualisierten Typs an, wenn Sie den Typ in einem Variablenfenster erweitern. Der Knoten `Expand` akzeptiert eine Liste untergeordneter Knoten, die die untergeordneten Elemente definieren.

- Wenn ein `Expand`-Knoten nicht in einem Visualisierungseintrag angegeben ist, verwenden die untergeordneten Knoten die standardmäßigen Erweiterungsregeln.

- Wenn ein `Expand`-Knoten ohne untergeordnete Knoten angegeben wird, kann der Typ in den Debuggerfenstern nicht erweitert werden.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Item-Erweiterung

 Das `Item`-Element ist das grundlegendste und häufigste Element in einem `Expand`-Knoten. Das`Item` -Element definiert ein einzelnes untergeordnetes Element. Eine `CRect`-Klasse mit den Feldern `top`, `left`, `right` und `bottom` verfügt z. B. über den folgenden Visualisierungseintrag:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Im Debuggerfenster sieht der `CRect`-Typ wie im folgenden Beispiel aus:

![CRect mit Item-Element-Erweiterung](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect mit Item-Elementerweiterung")

Der Debugger wertet die in den `Width`- und `Height`-Elementen angegebenen Ausdrücke aus und zeigt die Werte in der Spalte **Wert** des Variablenfensters an.

Der Debugger erstellt für jede benutzerdefinierte Erweiterung automatisch den **[Raw View]** -Knoten. Der vorhergehende Screenshot zeigt den Knoten **[Raw View]** erweitert an, um zu veranschaulichen, wie sich die standardmäßige Rohdatenansicht des Objekts von seiner Natvis-Visualisierung unterscheidet. Mit der Standarderweiterung werden eine Teilstruktur für die Basisklasse erstellt und alle Datenmember der Basisklasse als untergeordnete Elemente aufgeführt.

> [!NOTE]
> Wenn der Ausdruck des Item-Elements auf einen komplexen Typ weist, ist der **Item** -Knoten selbst erweiterbar.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Verwenden Sie den `ArrayItems` -Knoten, damit der Visual Studio-Debugger den Typ als Array interpretieren und die einzelnen Elemente anzeigen kann. Die Visualisierung für `std::vector` ist ein gutes Beispiel:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

Im `std::vector` -Knoten werden die einzelnen Elemente angezeigt, wenn sie im Variablenfenster erweitert werden:

![std::vector mit ArrayItems-Erweiterung](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector mit ArrayItems-Erweiterung")

Der `ArrayItems`-Knoten muss Folgendes aufweisen:

- Einen `Size`-Ausdruck (der als ganze Zahl ausgewertet werden muss), damit der Debugger die Länge des Arrays kennt.
- Einen `ValuePointer`-Ausdruck, der auf das erste Element verweist (das ein Zeiger eines Elementtyps sein muss, der nicht `void*` ist).

Der Standardwert mit der Arrayuntergrenze lautet „0“. Verwenden Sie ein `LowerBound`-Element, um den Wert außer Kraft zu setzen. Die mit Visual Studio ausgelieferten *NATVIS*-Dateien enthalten Beispiele.

>[!NOTE]
>Sie können den Operator `[]`, z. B. `vector[i]`, mit jeder eindimensionalen Arrayvisualisierung verwenden, die `ArrayItems` verwendet, auch wenn der Typ selbst (z. B. `CATLArray`) diesen Operator nicht zulässt.

Sie können auch mehrdimensionale Arrays angeben. In diesem Fall benötigt der Debugger etwas mehr Informationen, um untergeordnete Elemente ordnungsgemäß anzuzeigen:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction` gibt an, ob das Array in zeilengerichteter oder spaltengerichteter Reihenfolge angegeben ist.
- `Rank` gibt den Rang des Arrays an.
- Das `Size`-Element akzeptiert den impliziten `$i`-Parameter, der durch den Dimensionsindex ersetzt wird, um die Länge des Arrays in dieser Dimension festzustellen. Im vorherigen Beispiel sollte über den `_M_extent.M_base[0]`-Ausdruck die Länge der nullten Dimension, über `_M_extent._M_base[1]` die Länge der ersten Dimension usw. angegeben werden.

Im Folgenden wird gezeigt, wie ein zweidimensionales `Concurrency::array`-Objekt im Debuggerfenster dargestellt wird:

![Zweidimensionales Array mit ArrayItems-Erweiterung](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Zweidimensionales Array mit ArrayItems-Erweiterung")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems-Erweiterung

Sie können die `ArrayItems`-Erweiterung nur dann verwenden, wenn die Arrayelemente im Arbeitsspeicher zusammenhängend angeordnet sind. Der Debugger erreicht das nächste Element, indem einfach der Zeiger erhöht wird. Wenn Sie den Index für den Wertknoten ändern müssen, verwenden Sie `IndexListItems`-Knoten. Hier finden Sie eine Visualisierung mit einem `IndexListItems`-Knoten:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

Der einzige Unterschied zwischen `ArrayItems` und `IndexListItems` ist `ValueNode`, das den vollständigen Ausdruck für das i<sup>te</sup>-Element mit dem impliziten `$i`-Parameter erwartet.

>[!NOTE]
>Sie können den Operator `[]`, z. B. `vector[i]`, mit jeder eindimensionalen Arrayvisualisierung verwenden, die `IndexListItems` verwendet, auch wenn der Typ selbst (z. B. `CATLArray`) diesen Operator nicht zulässt.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems-Erweiterung

Wenn der Schnellansichtstyp eine verknüpfte Liste darstellt, kann der Debugger die untergeordneten Elemente mithilfe eines `LinkedListItems` -Knotens anzeigen. Die folgende Visualisierung für den `CAtlList`-Typ verwendet `LinkedListItems`:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

Das `Size` -Element bezieht sich auf die Länge der Liste. `HeadPointer` zeigt auf das erste Element, `NextPointer` bezieht sich auf das nächste Element, und `ValueNode` verweist auf den Wert des Elements.

Der Debugger wertet die Ausdrücke `NextPointer` und `ValueNode` im Kontext des `LinkedListItems`-Knotenelements und nicht im Kontext des übergeordneten Listentyps aus. Im vorhergehenden Beispiel besitzt `CAtlList` die `CNode`-Klasse (gefunden in `atlcoll.h`), die ein Knoten der verknüpften Liste ist. `m_pNext` und `m_element` sind Felder dieser `CNode`-Klasse und nicht der `CAtlList`-Klasse.

`ValueNode` kann leer gelassen werden, oder verwenden Sie `this`, um auf den `LinkedListItems`-Knoten selbst zu verweisen.

#### <a name="customlistitems-expansion"></a>CustomListItems-Erweiterung

Die `CustomListItems` -Erweiterung ermöglicht Ihnen das Schreiben von benutzerdefinierter Logik für das Traversieren einer Datenstruktur, beispielsweise einer Hashtabelle. Verwenden Sie `CustomListItems`, um Datenstrukturen zu visualisieren, die C++-Ausdrücke für alles verwenden können, was Sie zur Auswertung benötigen, die aber nicht ganz in die Form für `ArrayItems`, `IndexListItems` oder `LinkedListItems` passen.

Sie können `Exec` verwenden, um Code innerhalb einer `CustomListItems`-Erweiterung unter Verwendung der in der Erweiterung definierten Variablen und Objekte auszuführen. Sie können logische Operatoren, arithmetische Operatoren und Zuweisungsoperatoren mit `Exec` verwenden. Sie können `Exec` nicht zum Auswerten von Funktionen verwenden, außer für [systeminterne Debuggerfunktionen](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state), die von der C++-Ausdrucksauswertung unterstützt werden.

Die folgende Schnellansicht für `CAtlMap` ist ein tolles Beispiel dafür, in welchen Fällen `CustomListItems` angemessen ist.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> TreeItems-Erweiterung
 Wenn der Schnellansichtstyp eine Struktur darstellt, kann der Debugger die Struktur durchlaufen und seine untergeordneten Elemente mithilfe eines `TreeItems` -Knotens anzeigen. Im Folgenden ist die Visualisierung für den `std::map`-Typ angegeben, wobei ein `TreeItems`-Knoten verwendet wird:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

Die Syntax ist dem `LinkedListItems`-Knoten ähnlich. `LeftPointer`, `RightPointer` und `ValueNode` werden unter dem Kontext der Strukturknotenklasse ausgewertet. `ValueNode` kann leer gelassen werden, oder verwenden Sie `this`, um auf den `TreeItems`-Knoten selbst zu verweisen.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem-Erweiterung
 Das `ExpandedItem`-Element generiert eine aggregierte untergeordnete Ansicht, indem die Eigenschaften von Basisklassen oder Datenmembern so angezeigt werden, als ob sie untergeordnete Elemente des Schnellansichtstyps wären. Der Debugger wertet den angegebenen Ausdruck aus und fügt die untergeordneten Knoten des Ergebnisses an die untergeordnete Liste des visualisierten Typs an.

Der intelligente Zeigertyp `auto_ptr<vector<int>>` wird z. B. in der Regel wie folgt angezeigt:

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; Standarderweiterung](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Standarderweiterung")

 Um die Werte des Vektors anzuzeigen, müssen Sie im Variablenfenster einen Drilldown über zwei Ebenen durch den `_Myptr`-Member ausführen. Durch Hinzufügen eines `ExpandedItem`-Elements können Sie die `_Myptr`-Variable aus der Hierarchie ausschließen und die Vektorelemente direkt anzeigen:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; ExpandedItem-Erweiterung](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem-Erweiterung")

Im folgenden Beispiel wird dargestellt, wie Eigenschaften der Basisklasse in einer abgeleiteten Klasse zusammengefasst werden. Angenommen, die `CPanel` -Klasse wird von `CFrameworkElement`abgeleitet. Anstatt die Eigenschaften zu wiederholen, die von der `CFrameworkElement`-Basisklasse stammen, fügt die `ExpandedItem`-Knotenvisualisierung diese Eigenschaften an die untergeordnete Liste der `CPanel`-Klasse an.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Der **nd**-Formatbezeichner, mit dem die Visualisierungsabstimmung für die abgeleitete Klasse deaktiviert wird, ist hier erforderlich. Andernfalls würde der `*(CFrameworkElement*)this`-Ausdruck dazu führen, dass die `CPanel`-Visualisierung erneut angewendet wird, da sie von den Standardregeln für die Visualisierungstypenabstimmung als geeignetste angesehen wird. Weisen Sie den Debugger mit dem **nd**-Formatbezeichner an, die Basisklassenvisualisierung oder aber die Standarderweiterung zu verwenden, wenn die Basisklasse keine Visualisierung aufweist.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Synthetische Elementerweiterung
 Während das `ExpandedItem`-Element eine flachere Datenansicht durch die Beseitigung von Hierarchien bereitstellt, bewirkt der `Synthetic`-Knoten das Gegenteil. Es ermöglicht Ihnen, ein künstliches untergeordnetes Element zu erstellen, das nicht das Ergebnis eines Ausdrucks ist. Das künstliche Element kann eigene untergeordnete Elemente aufweisen. Im folgenden Beispiel verwendet die Visualisierung für den `Concurrency::array` -Typ einen `Synthetic` -Knoten, um dem Benutzer eine Diagnosemeldung anzuzeigen:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concurrency::Array mit Synthetic-Elementerweiterung](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array mit Synthetic-Elementerweiterung")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> HResult-Element
 Mit dem `HResult`-Element können Sie die für ein **HRESULT** in Debuggerfenstern angezeigten Informationen anpassen. Das `HRValue`-Element muss den 32-Bit-Wert des anzupassenden **HRESULT**-Elements enthalten. Das `HRDescription`-Element enthält die Informationen, die im Debuggerfenster angezeigt werden sollen.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer-Element
Ein `UIVisualizer` -Element registriert ein grafisches Schnellansichts-Plug-In mit dem Debugger. Eine grafische Schnellansicht erstellt ein Dialogfeld oder eine andere Schnittstelle, die eine Variable oder ein Objekt in einer Weise anzeigt, die mit ihrem Datentyp konsistent ist. Das Schnellansichts-Plug-In muss als [VSPackage](../extensibility/internals/vspackages.md) erstellt sein und einen Dienst bereitstellen, den der Debugger nutzen kann. Die *NATVIS*-Datei enthält Registrierungsinformationen für das Plug-In, z. B. den Namen, die GUID des verfügbar gemachten Diensts und die Typen, die sie visualisieren kann.

Im Folgenden ist ein Beispiel eines UIVisualizer-Elements angegeben:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- Ein `ServiceId` - `Id`-Attributpaar identifiziert ein `UIVisualizer`. Die `ServiceId` ist die GUID des Diensts, den das Schnellansichtspaket verfügbar macht. `Id` ist ein eindeutiger Bezeichner, der Schnellansichten unterscheidet, wenn von einem Dienst mehrere bereitgestellt werden. Im vorhergehenden Beispiel stellt derselbe Schnellansichtsdienst zwei Schnellansichten zur Verfügung.

- Das Attribut `MenuName` definiert einen Schnellansichtsnamen, der im Debugger in der Dropdownliste neben dem Lupensymbol angezeigt wird. Zum Beispiel:

  ![Kontextmenü des UIVisualizer-Menüs](../debugger/media/dbg_natvis_vectorvisualizer.png "Kontextmenü des UIVisualizer-Menüs")

Alle Typen, die in der *NATVIS*-Datei definiert sind, müssen explizit alle Benutzeroberflächenschnellansichten auflisten, die sie anzeigen können. Der Debugger passt die Schnellansichtsverweise in den Typeinträgen mit den registrierten Schnellansichten an. Der folgende Typeintrag für `std::vector` verweist z. B. auf das `UIVisualizer` im vorherigen Beispiel.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Ein Beispiel für ein `UIVisualizer` finden Sie in der [Image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance)-Erweiterung, die zum Anzeigen von In-Memory-Bitmaps verwendet wird.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer-Element
 `CustomVisualizer` ist ein Erweiterungspunkt. Er gibt eine VSIX-Erweiterung an, die Sie schreiben können, um Visualisierungen in Visual Studio-Code zu steuern. Weitere Informationen zum Schreiben von VSIX-Erweiterungen finden Sie im [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Es ist viel aufwendiger, eine benutzerdefinierte Visualisierung zu schreiben als eine XML-Natvis-Definition. Sie sind jedoch nicht an Beschränkungen gebunden, wenn es darum geht, was Natvis unterstützt und was nicht. Benutzerdefinierte Schnellansichten verfügen über Zugriff auf den vollständigen Satz der Debugger-Erweiterbarkeits-APIs. Diese können zum Abfragen und Ändern des debuggenden Prozesses oder zum Kommunizieren mit anderen Bestandteilen von Visual Studio verwendet werden.

 Sie können die Attribute `Condition`, `IncludeView` und `ExcludeView` für `CustomVisualizer`-Elemente verwenden.

## <a name="limitations"></a>Einschränkungen

Natvis-Anpassungen arbeiten mit Klassen und Strukturen, jedoch nicht mit Typedefs.

Natvis unterstützt keine Schnellansichten für einfache Typen (z. B. `int`, `bool`) oder für Zeiger auf einfache Typen. In diesem Szenario besteht eine Möglichkeit darin, den für Ihren Anwendungsfall geeigneten [Formatbezeichner](../debugger/format-specifiers-in-cpp.md) zu verwenden. Wenn Sie z. B. `double* mydoublearray` in Ihrem Code verwenden, können Sie im Fenster **Überwachen** des Debuggers einen Arrayformatspezifizierer verwenden, z. B. den Ausdruck `mydoublearray, [100]`, der die ersten 100 Elemente anzeigt.
