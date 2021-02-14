---
title: 'Microsoft Fakes: Generieren und Kompilieren von Code; Namenskonventionen'
description: In diesem Thema werden Optionen und Probleme der Fakes-Codegenerierung und -Codekompilierung inklusive der Namenskonventionen der von Fakes generierten Typen, Member und Parameter beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ecba59e633bf6d456f16e6098f47719e052ac0de
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006354"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Codegenerierung, Kompilierung und Benennungskonventionen in Microsoft Fakes

In diesem Artikel werden Optionen und Probleme der Fakes-Codegenerierung und -Codekompilierung sowie die Namenskonventionen der von Fakes generierten Typen, Member und Parameter beschrieben.

**Anforderungen**

- Visual Studio Enterprise
- Ein .NET Framework-Projekt
::: moniker range=">=vs-2019"
- Die Unterstützung von Projekten im .NET Core-, .NET 5.0- und SDK-Format ist in Visual Studio 2019 Update 6 als Vorschaufeature enthalten und in Update 8 standardmäßig aktiviert. Weitere Informationen finden Sie unter [Microsoft Fakes für .NET Core- und SDK-Projekte](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

## <a name="code-generation-and-compilation"></a>Codegenerierung und -kompilierung

### <a name="configure-code-generation-of-stubs"></a>Konfigurieren der Codegenerierung von Stubs

Die Generierung von Stub-Typen wird in einer XML-Datei mit der Erweiterung *.fakes* konfiguriert. Das Fakes-Framework wird durch benutzerdefinierte MSBuild-Aufgaben in den Buildprozess integriert und erkennt diese Dateien zur Buildzeit. Der Fakes-Code-Generator kompiliert die Stub-Typen in eine Assembly und fügt dem Projekt den Verweis hinzu.

Das folgende Beispiel veranschaulicht Stub-Typen, die in *FileSystem.dll* definiert werden:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Typfilterung

Es können Filter in der *FAKES*-Datei festgelegt werden, um die Typen einzuschränken, für die ein Stub ausgeführt werden soll. Sie können unter dem StubGeneration-Element eine unbegrenzte Anzahl von "Löschen"-, "Hinzufügen"- und "Entfernen"-Elementen hinzufügen, um die Liste der ausgewählten Typen zu erstellen.

Beispielsweise werden durch die folgende *FAKES*-Datei Stubs für Typen unter dem System- und dem System.IO-Namespace generiert, aber alle Typen ausgeschlossen, in deren System „Handle“ enthalten ist:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

Von den Filterzeichenfolgen wird eine einfache Grammatik verwendet, um zu definieren, wie der Abgleich ausgeführt werden soll:

- Bei Filtern wird standardmäßig die Groß-/Kleinschreibung nicht berücksichtigt. Filter führen einen Abgleich untergeordneter Zeichenfolgen aus:

     `el` findet "hello"

- Durch das Hinzufügen von `!` am Ende des Filters wird die Groß-/Kleinschreibung genau beachtet:

     `el!` findet "hello" nicht

     `hello!` findet "hello"

- Durch das Hinzufügen von `*` am Ende des Filters wird das Präfix der Zeichenfolge berücksichtigt:

     `el*` findet "hello" nicht

     `he*` findet "hello"

- Mehrere Filter in einer durch Semikolons getrennten Liste werden als eine Disjunktion kombiniert:

     `el;wo` findet "hello" und "world"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Ausführen eines Stubs für konkrete Klassen und virtuelle Methoden

Standardmäßig werden Stub-Typen für alle nicht versiegelte Klassen generiert. Es besteht die Möglichkeit, die Stub-Typen durch die *FAKES*-Konfigurationsdatei auf abstrakte Klassen einzuschränken:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="internal-types"></a>Interne Typen

Der Fakes-Code-Generator generiert Shim-Typen und Stub-Typen für Typen, die für die generierte Fakes-Assembly sichtbar sind. Um interne Typen einer Shim-Assembly für die Fakes-Assembly und Ihre Testassembly sichtbar zu machen, fügen Sie dem Shim-Assemblycode <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>-Attribute hinzu, durch die die Sichtbarkeit für die generierte Fakes-Assembly und die Testassembly hergestellt wird. Hier sehen Sie ein Beispiel:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Interne Typen in Assemblys mit starkem Namen**

Wenn die Shim-Assembly einen starken Namen hat und auf interne Typen der Assembly zugegriffen werden soll:

- Es müssen sowohl die Testassembly als auch die Fakes-Assembly einen starken Namen haben.

- Fügen Sie den **InternalsVisibleToAttribute**-Attributen in den Shim-Assemblys die öffentlichen Schlüssel der Testassembly und der Fakes-Assembly hinzu. Im Folgenden wird gezeigt, wie die Beispielattribute im Shim-Assemblycode bei einer Shim-Assembly mit einem starken Namen aussehen würden:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Wenn die Shim-Assembly einen starken Namen hat, wird die generierte Fakes-Assembly automatisch durch das Fakes-Framework stark signiert. Die Testassembly muss von Ihnen stark signiert werden. Weitere Informationen finden Sie unter [Assemblys mit starkem Namen](/dotnet/framework/app-domains/strong-named-assemblies).

Das Fakes-Framework verwendet den gleichen Schlüssel, um alle generierten Assemblys zu signieren, sodass Sie diesen Ausschnitt als Ausgangspunkt verwenden können, um dem Shim-Assemblycode das **InternalsVisibleTo**-Attribut für die Fakes-Assembly hinzuzufügen.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Sie können einen anderen öffentlichen Schlüssel für die Fakes-Assembly angeben, beispielsweise einen Schlüssel, den Sie für die Shim-Assembly erstellt haben, indem Sie den vollständigen Pfad der *SNK*-Datei angeben, die den alternativen Schlüssel als `KeyFile`-Attributwert im `Fakes`\\`Compilation`-Element der *FAKES*-Datei enthält. Beispiel:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Sie müssen dann im Shim-Assemblycode den öffentlichen Schlüssel der alternativen *SNK*-Datei als zweiten Parameter des InternalVisibleTo-Attributs für die Fakes-Assembly verwenden:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

Im obigen Beispiel können die Werte `Alternate_public_key` und `Test_assembly_public_key` gleich sein.

### <a name="optimize-build-times"></a>Optimieren von Buildzeiten

Die Kompilierung von Fakes-Assemblys kann die Buildzeit erheblich verlängern. Sie können die Buildzeit minimieren, indem Sie die Fakes-Assemblys für .NET-Systemassemblys und Assemblys von Drittanbietern in einem zentralisierten separaten Projekt generieren. Da diese Assemblys auf dem Computer kaum verändert werden, können Sie die generierten Fakes-Assemblys in anderen Projekten wiederverwenden.

Fügen Sie in den Komponententestprojekten einen Verweis auf die kompilierten Fakes-Assemblys hinzu, die sich im Projektordner unter „FakesAssemblies“ befinden.

1. Erstellen Sie eine neue Klassenbibliothek mit der .NET-Laufzeitversion, die mit Ihren Testprojekten übereinstimmt. Nennen wir sie „Fakes.Prebuild“. Entfernen Sie die Datei *class1.cs* aus dem Projekt, da diese nicht benötigt wird.

2. Fügen Sie Verweise auf alle Systemassemblys und Assemblys von Drittanbietern hinzu, für die Sie Fakes benötigen.

3. Fügen Sie jeder Assembly und jedem Build eine *FAKES*-Datei hinzu.

4. Aus dem Testprojekt

    - Stellen Sie sicher, dass es einen Verweis auf die Fakes-Runtime-DLL gibt:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Fügen Sie für jede Assembly, für die Sie Fakes erstellt haben, einen Verweis auf die entsprechende DLL-Datei im Ordner *Fakes.Prebuild\FakesAssemblies* des Projekts hinzu.

### <a name="avoid-assembly-name-clashing"></a>Vermeiden von Konflikten bei Assemblynamen

In einer Team Build-Umgebung werden alle Buildausgaben in ein Verzeichnis zusammengeführt. Bei mehreren Projekten, die Fakes verwenden, kann es möglicherweise vorkommen, dass sich Fakes-Assemblys aus verschiedenen Versionen gegenseitig überschreiben. Beispielsweise würden sich beide *mscorlib.dll*-Fakes, sowohl für TestProject1 von .NET Framework 2.0 als auch für TestProject2 von .NET Framework 4, aus einer *mscorlib.Fakes.dll*-Fakes-Assembly ergeben.

Wenn Sie dieses Problem vermeiden möchten, sollte Fakes beim Hinzufügen der *FAKES*-Dateien automatisch qualifizierte Versionen der Fakes-Assemblynamen für Verweise erstellen, die sich nicht auf das Projekt beziehen. In einen Fakes-Assemblynamen mit qualifizierter Version wird eine Versionsnummer eingebettet, wenn der Fakes-Assemblyname erstellt wird:

Bei einer Assembly mit dem Namen "MyAssembly" und der Version "1.2.3.4" ist der Fakes-Assemblyname "MyAssembly.1.2.3.4.Fakes".

Sie können diese Version durch die Bearbeitung des Versionsattributs des Assemblyelements in der *FAKES*-Datei ändern oder entfernen:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Fakes-Namenskonventionen

### <a name="shim-type-and-stub-type-naming-conventions"></a>Namenskonventionen für Shim-Typ und Stub-Typ

**Namespaces**

- Das Suffix ".Fakes" wird dem Namespace hinzugefügt.

   Beispielsweise enthält `System.Fakes`-Namespace die Shim-Typen des System-Namespace.

- Global.Fakes enthält den Shim-Typ des leeren Namespace.

  **Typnamen**

- Der Präfix "Shim" wird dem Typnamen hinzugefügt, um den Shim-Typnamen zu erstellen.

   Beispielsweise ist ShimExample der Shim-Typ des Beispieltyps.

- Der Präfix "Stub" wird dem Typnamen hinzugefügt, um den Stub-Typnamen zu erstellen.

   Beispielsweise ist StubIExample der Stub-Typ des IExample-Typs.

  **Typargumente und Strukturen des geschachtelten Typs**

- Generische Typargumente werden kopiert.

- Struktur des geschachtelten Typs wird für Shim-Typen kopiert.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Namenskonventionen für Shim-Delegateigenschaften oder Stub-Delegatfelder

**Grundregeln** für Feldbenennung, beginnend mit einem leeren Namen:

- Der Methodenname ist angefügt.

- Wenn der Methodenname eine explizite Schnittstellenimplementierung ist, sind die Punkte entfernt.

- Wenn die Methode generisch ist, wird `Of`*n* angefügt, wobei *n* für die Anzahl der generischen Methodenargumente steht.

  **Spezielle Methodennamen**, wie beispielsweise Eigenschaften-Getter oder -Setter, werden wie in der folgenden Tabelle beschrieben behandelt:

|Wenn die Methode Folgendes ist...|Beispiel|Methodenname angefügt|
|-|-|-|
|Ein **Konstruktor**|`.ctor`|`Constructor`|
|Ein statischer **Konstruktor**|`.cctor`|`StaticConstructor`|
|Eine **Zugriffsmethode** mit einem Methodennamen, der aus zwei durch „_“ getrennten Teilen besteht (z.B. Eigenschaftengetter)|*kind_name* (kommt häufig vor, wird aber durch ECMA nicht erzwungen)|*NameKind*, in dem beide Teile groß geschrieben und vertauscht werden|
||Getter der Eigenschaft `Prop`|`PropGet`|
||Setter der Eigenschaft `Prop`|`PropSet`|
||Ereignisadder|`Add`|
||Ereignisentferner|`Remove`|
|Aus zwei Teilen bestehender **Operator**|`op_name`|`NameOp`|
|Beispiel für einen Operator mit einer Hinzufügung|`op_Add`|`AddOp`|
|Für einen **Konvertierungsoperator** wird der Rückgabetyp angefügt.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Getter und Setter von Indexern** werden auf ähnliche Weise wie die Eigenschaft behandelt. Der Standardname für einen Indexer ist `Item`.
> - Namen für den **Parametertyp** werden umgewandelt und verkettet.
> - **Rückgabetyp** wird ignoriert, wenn es keine Überladungsmehrdeutigkeit gibt. Bei einer Überladungsmehrdeutigkeit wird der Rückgabetyp am Ende des Namens angefügt.

### <a name="parameter-type-naming-conventions"></a>Namenskonventionen für Parametertypen

|Vorgabe|Angefügte Zeichenfolge ist...|
|-|-|
|Ein **Typ**`T`|T<br /><br /> Der Namespace, die geschachtelte Struktur und die generischen Tics werden verworfen.|
|Ein **out-Parameter**`out T`|`TOut`|
|Ein **ref-Parameter** `ref T`|`TRef`|
|Ein **Arraytyp** `T[]`|`TArray`|
|Ein **mehrdimensionales Array**, Typ `T[ , , ]`|`T3`|
|Ein **Zeiger**, Typ `T*`|`TPtr`|
|Ein **generischer Typ**`T<R1, ...>`|`TOfR1`|
|Ein **generisches Typargument**`!i` des Typs `C<TType>`|`Ti`|
|Ein **generisches Methodenargument**`!!i` der `M<MMethod>`-Methode|`Mi`|
|Ein **geschachtelter Typ**`N.T`|`N` und dann `T` werden angefügt.|

### <a name="recursive-rules"></a>Rekursive Regeln

Die folgenden Regeln werden rekursiv angewendet:

- Da Fakes C# zur Generierung der Fakes-Assemblys verwendet, wird jedes Zeichen, das ein ungültiges C#-Token erzeugen würde, mit einem "_" (Unterstrich) versehen.

- Wenn ein resultierender Name einen Konflikt mit einem Mitglied des deklarierenden Typs verursacht, wird ein Nummerierungsschema verwendet, indem ein zweistelliger Indikator angefügt wird, der mit „01“ beginnt.

## <a name="see-also"></a>Weitere Informationen

- [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
