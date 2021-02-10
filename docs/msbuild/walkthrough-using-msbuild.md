---
title: Verwenden von MSBuild
description: Hier erfahren Sie mehr über die verschiedenen Teile einer MSBuild-Projektdatei einschließlich der Elemente, Elementmetadaten, Eigenschaften, Ziele und Aufgaben.
ms.date: 10/19/2020
ms.topic: conceptual
ms.custom: contperf-fy21q2
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3b214452a2eb7a85b4a9baea5e4b4e80a1a71e63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933855"
---
# <a name="walkthrough-use-msbuild"></a>Exemplarische Vorgehensweise: Verwenden von MSBuild

MSBuild ist die Buildplattform für Microsoft und Visual Studio. In dieser exemplarischen Vorgehensweise machen Sie sich mit den Bausteinen von MSBuild vertraut, zudem wird erläutert, wie Sie MSBuild-Projekte erstellen, bearbeiten und debuggen. Zu folgenden Aspekten erfahren Sie mehr:

- Erstellen und Bearbeiten einer Projektdatei.

- Verwenden von Buildeigenschaften

- Verwenden von Buildelementen

Sie können MSBuild in Visual Studio oder im **Befehlsfenster** ausführen. In dieser exemplarischen Vorgehensweise erstellen Sie in Visual Studio eine MSBuild-Projektdatei. Sie bearbeiten die Projektdatei in Visual Studio, und im **Befehlsfenster** erstellen Sie das Projekt und untersuchen die Ergebnisse.

## <a name="install-msbuild"></a>Installieren von MSBuild

::: moniker range="vs-2017"

Wenn Sie über Visual Studio verfügen, ist MSBuild bereits installiert. Navigieren Sie zu [Visual Studio older downloads](https://visualstudio.microsoft.com/vs/older-downloads/) (Ältere Visual Studio-Downloads), erweitern Sie **Visual Studio 2017**, und klicken Sie auf die Schaltfläche **Download**, um MSBuild 15 auf einem System zu installieren, auf dem Visual Studio nicht installiert ist. Wenn Sie ein Visual Studio-Abonnement besitzen, melden Sie sich an, und suchen Sie den Link zum Herunterladen der neuesten Version der **Buildtools für Visual Studio 2017**. Wenn Sie noch nicht über ein Visual Studio-Abonnement verfügen, können Sie die neueste Version der Buildtools installieren. Verwenden Sie auf dieser Seite die Versionsauswahl, um auf der Seite zu Version 2019 zu wechseln, und befolgen Sie die Installationsanweisungen.
::: moniker-end

::: moniker range="vs-2019"
Wenn Sie über Visual Studio verfügen, ist MSBuild bereits installiert. Bei Visual Studio 2019 erfolgt die Installation im Installationsordner von Visual Studio. Bei einer typischen Standardinstallation unter Windows 10 befindet sich MSBuild.exe im Installationsordner *MSBuild\Current\Bin*.

Navigieren Sie zu [Visual Studio downloads](https://visualstudio.microsoft.com/downloads/) (Visual Studio-Downloads), scrollen Sie nach unten zu **All Downloads** (Alle Downloads), und erweitern Sie **Tools for Visual Studio 2019** (Tools für Visual Studio 2019), um MSBuild auf einem System zu installieren, auf dem Visual Studio nicht installiert ist. Installieren Sie **Build Tools for Visual Studio 2019** (Buildtools für Visual Studio 2019) (umfasst MSBuild) oder das [.NET Core SDK](/dotnet/core/sdk#acquiring-the-net-core-sdk).

Stellen Sie im Installationsprogramm sicher, dass die MSBuild-Tools für die verwendeten Arbeitsauslastungen ausgewählt sind, und klicken Sie auf **Installieren**.

![Installieren von MSBuild](media/walkthrough-using-msbuild/installation-msbuild-tools.png)

::: moniker-end

## <a name="create-an-msbuild-project"></a>Erstellen eines MSBuild-Projekts

 Das Visual Studio-Projektsystem beruht auf MSBuild. Auf diese Weise können in Visual Studio neue Projektdatei problemlos erstellt werden. In diesem Abschnitt erstellen Sie eine Visual C#-Projektdatei. Stattdessen können Sie auch eine Visual Basic-Projektdatei erstellen. Im Kontext dieser exemplarischen Vorgehensweise ist der Unterschied zwischen den zwei Projektdateien marginal.

**So erstellen Sie eine neue Projektdatei**

1. Öffnen Sie Visual Studio, und erstellen Sie ein Projekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG + Q** zum Öffnen des Suchfelds ein, geben Sie **winforms** ein, und wählen Sie dann **Neue Windows Forms-App (.NET Framework) erstellen** aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.

    Geben Sie im Feld **Name**`BuildApp`ein. Geben Sie einen **Speicherort** für die Projektmappe ein, z.B. *D:\\* . Übernehmen Sie die Standardwerte für **Lösung**, **Projektmappenname** (**BuildApp**) und **Framework**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#**  > **Windows Desktop**, und wählen Sie dann **Windows Forms-App (.NET Framework)** aus. Wählen Sie dann **OK** aus.

    Geben Sie im Feld **Name**`BuildApp`ein. Geben Sie einen **Speicherort** für die Projektmappe ein, z.B. *D:\\* . Übernehmen Sie die Standardwerte für **Projektmappenverzeichnis erstellen** (ausgewählt), **Zur Quellcodeverwaltung hinzufügen** (nicht ausgewählt) und **Projektmappenname** (**BuildApp**).
    ::: moniker-end

1. Klicken Sie auf **OK** oder **Erstellen**, um die Projektdatei zu erstellen.

## <a name="examine-the-project-file"></a>Überprüfen der Projektdatei

 Im vorherigen Abschnitt haben Sie in Visual Studio eine Visual C#-Projektdatei erstellt. Die Projektdatei wird im **Projektmappen-Explorer** durch den Projektknoten „BuildApp“ dargestellt. Sie können die Projektdatei im Visual Studio Code-Editor untersuchen.

**So überprüfen Sie die Projektdatei**

1. Klicken Sie im **Projektmappen-Explorer** auf den Projektknoten **BuildApp**.

1. Im **Eigenschaftenbrowser** wird als **Projektdatei**-Eigenschaft *BuildApp.csproj* angezeigt. Alle Projektdateien werden mit dem Suffix *PROJ* benannt. Wenn Sie ein Visual Basic-Projekt erstellt hätten, wäre der Projektdateiname *BuildApp.vbproj*.

1. Klicken Sie erneut mit der rechten Maustaste auf den Projektknoten, klicken Sie dann auf **BuildApp.csproj bearbeiten**. 

     Die Projektdatei wird im Code-Editor angezeigt.

>[!NOTE]
> Für einige Projekttypen, z. B. für C++-Projekte, müssen Sie das Projekt entladen, indem Sie mit der rechten Maustaste auf die Projektdatei klicken und **Projekt entladen** auswählen, bevor Sie die Projektdatei öffnen und bearbeiten können.

## <a name="targets-and-tasks"></a>Ziele und Aufgaben

Projektdateien sind Dateien im XML-Format und dem Stammknoten [Project](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Neuere .NET Core-Projekte (SDK-Format) enthalten ein `Sdk`-Attribut.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Wenn das Projekt nicht im SDK-Format aufgesetzt ist, müssen Sie den xmlns-Namespace im Project-Element angeben. Wenn `ToolsVersion` in einem neuen Projekt enthalten ist, muss es sich um die Version „15.0“ handeln.

Das Erstellen einer Anwendung wird mit dem [Target](../msbuild/target-element-msbuild.md)-Element und dem [Task](../msbuild/task-element-msbuild.md)-Element ausgeführt.

- Eine Aufgabe bildet die kleinste Arbeitseinheit, d. h. das „Atom“ eines Builds. Aufgaben sind unabhängige ausführbare Komponenten, die über Eingaben und Ausgaben verfügen können. Derzeit wird in der Projektdatei nicht auf Aufgaben verwiesen, und solche wurden nicht definiert. In den folgenden Abschnitten fügen Sie der Projektdatei Aufgaben hinzu. Weitere Informationen finden Sie im Thema [Aufgaben](../msbuild/msbuild-tasks.md).

- Als Ziel wird eine benannte Sequenz von Aufgaben bezeichnet. Weitere Informationen finden Sie im Thema [Ziele](../msbuild/msbuild-targets.md).
- Dabei kann es sich um eine benannte Tasksequenz handeln, aber im Wesentlichen ist es ein Element, das kompiliert oder fertiggestellt werden muss. Sie sollten es also zielorientiert definieren.

Das Standardziel ist nicht in der Projektdatei definiert. Stattdessen wird es in importierten Projekten angegeben. Das [Import](../msbuild/import-element-msbuild.md)-Element gibt importierte Projekte an. Beispielsweise wird in einem C#-Projekt das Standardziel aus der Datei *Microsoft.CSharp.targets* importiert.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Importierte Dateien werden letztlich in der Projektdatei eingefügt, in der sie mit Verweisen versehen werden.

Bei Projekten im SDK-Format wird dieses Importelement nicht angezeigt, da das SDK-Attribut bewirkt, dass diese Datei implizit importiert wird.

MSBuild verfolgt die Ziele eines Builds nach und garantiert, dass jedes Ziel nicht mehr als einmal erstellt wird.

## <a name="add-a-target-and-a-task"></a>Hinzufügen eines Ziels und einer Aufgabe

 Fügen Sie der Projektdatei ein Ziel hinzu. Fügen Sie dem Ziel eine Aufgabe hinzu, mit der eine Meldung gedruckt wird.

**So fügen Sie ein Ziel und eine Aufgabe hinzu**

1. Fügen Sie der Projektdatei, genau nach der Import-Anweisung, die folgenden Zeilen hinzu:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    So erstellen Sie das Ziel HelloWorld. Beachten Sie, dass beim Bearbeiten der Projektdatei IntelliSense unterstützt wird.

2. Fügen Sie dem Ziel HelloWorld Zeilen hinzu, sodass der daraufhin angezeigte Abschnitt wie folgt aussieht:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Speichern Sie die Projektdatei.

Die Message-Aufgabe ist eine der vielen Aufgaben, die im Lieferumfang von MSBuild enthalten sind. Eine vollständige Liste der verfügbaren Aufgaben sowie Nutzungsinformationen finden Sie unter [Aufgabenreferenz](../msbuild/msbuild-task-reference.md).

Der Message-Task akzeptiert den Zeichenfolgenwert des Text-Attributs als Eingabe und zeigt diesen auf dem Ausgabegerät an (oder schreibt ihn ggf. in Protokolle). Das HelloWorld-Ziel führt die Message-Aufgabe zweimal aus: zuerst wird "Hello" angezeigt, dann "World".

## <a name="build-the-target"></a>Erstellen des Ziels

Wenn Sie versuchen, dieses Projekt über Visual Studio zu kompilieren, wird das definierte Ziel nicht erstellt. Das liegt daran, dass Visual Studio das Standardziel auswählt, bei dem sich weiterhin um ein Element in der importierten *TARGETS-Datei* handelt.

Führen Sie MSBuild über die **Developer-Eingabeaufforderung** für Visual Studio aus, um das oben definierte Ziel „HelloWorld“ zu erstellen. Verwenden Sie den Befehlszeilenparameter -target oder -t, um das Ziel auszuwählen.

> [!NOTE]
> In den folgenden Abschnitten wird die **Developer-Eingabeaufforderung** als **Befehlsfenster** bezeichnet.

**So erstellen Sie das Ziel:**

1. Öffnen Sie das **Befehlsfenster**.

   (Windows 10) Geben Sie den Namen des Tools im Suchfeld auf der Taskleiste ein, z. B. `dev` oder `developer command prompt`. Dadurch wird eine Liste der installierten Apps angezeigt, die Ihrem Suchmuster entsprechen.

   Wenn Sie die Datei *LaunchDevCmd.bat* manuell suchen müssen, finden Sie sie im Ordner *<Visualstudio-Installationsordner\>\<version>\Common7\Tools*.

2. Navigieren Sie im Befehlsfenster zum Ordner mit der Projektdatei, in diesem Fall *D:\BuildApp\BuildApp*.

3. Führen Sie MSBuild mit dem Befehlsparameter `-t:HelloWorld` aus. Damit wird das Ziel HelloWorld ausgewählt und erstellt:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Untersuchen Sie die Ausgabe im **Befehlsfenster**. Die beiden Zeilen "Hello" und "World" sollten angezeigt werden:

    ```output
    Hello
    World
    ```

> [!NOTE]
> Wenn stattdessen `The target "HelloWorld" does not exist in the project` angezeigt wird, haben Sie wahrscheinlich vergessen, die Projektdatei im Code-Editor zu speichern. Speichern Sie die Datei, und versuchen Sie es erneut.

 Durch Wechsel zwischen Code-Editor und dem Befehlsfenster können Sie die Projektdatei ändern und die Ergebnisse schnell anzeigen.

## <a name="build-properties"></a>Buildeigenschaften

 Buildeigenschaften sind Name-Wert-Paare, anhand derer der Build ausgeführt wird. Am Anfang der Projektdatei sind bereits mehrere Buildeigenschaften definiert:

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 Alle Eigenschaften sind untergeordnete Elemente von PropertyGroup-Elementen. Der Name der Eigenschaft entspricht dem Namen des untergeordneten Elements, und der Wert der Eigenschaft entspricht dem Textelement des untergeordneten Elements. Ein auf ein Objekt angewendeter

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 definiert die Eigenschaft „TargetFrameworkVersion“ und weist dieser den Zeichenfolgenwert „v4.5“ zu.

 Buildeigenschaften können jederzeit neu definiert werden. If

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 später in der Projektdatei oder in einer später in die Projektdatei importierten Datei angegeben ist, nimmt TargetFrameworkVersion den neuen Wert "v3.5" an.

## <a name="examine-a-property-value"></a>Untersuchen eines Eigenschaftswerts

 Den Wert einer Eigenschaft rufen Sie mit der folgenden Syntax ab, wobei `PropertyName` den Namen der Eigenschaft darstellt:

```xml
$(PropertyName)
```

Verwenden Sie die folgende Syntax, um einige Eigenschaften in der Projektdatei zu untersuchen.

**So untersuchen Sie einen Eigenschaftswert**

1. Ersetzen Sie im Code-Editor das Ziel HelloWorld durch den folgenden Code:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. Speichern Sie die Projektdatei.

1. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Prüfen Sie die Ausgabe. Die folgenden beiden Zeilen sollten angezeigt werden (die Version von .NET Framework kann abweichen):

    ::: moniker range=">=vs-2019"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

### <a name="conditional-properties"></a>Bedingte Eigenschaften

Viele Eigenschaften, z. B. `Configuration`, werden bedingt definiert, das heißt, dass im Eigenschaftenelement das `Condition`-Attribut angezeigt wird. Bedingte Eigenschaften werden nur definiert oder erneut definiert, wenn die Bedingung "true" ergibt. Nicht definierten Eigenschaften wird der Standardwert, eine leere Zeichenfolge, zugewiesen. Ein auf ein Objekt angewendeter

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

bedeutet: "Wenn die Configuration-Eigenschaft noch nicht definiert wurde, definieren Sie diese, und weisen Sie ihr den Wert 'Debug' zu."

Fast alle MSBuild-Elemente können ein Condition-Attribut besitzen. Die Verwendung des Condition-Attributs wird unter [Bedingungen](../msbuild/msbuild-conditions.md) näher besprochen.

### <a name="reserved-properties"></a>Reservierte Eigenschaften

Einige Eigenschaftennamen werden von MSBuild reserviert, um Informationen zur Projektdatei und zu den Binärdateien von MSBuild zu speichern. Ein Beispiel für eine reservierte Eigenschaft ist "MSBuildToolsPath". Auf reservierte Eigenschaften wird wie auf jede andere Eigenschaft mit der $-Notation verwiesen. Weitere Informationen finden Sie unter [Vorgehensweise: Verweisen auf den Namen oder Speicherort der Projektdatei](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) und [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Umgebungsvariablen

Auf Umgebungsvariablen in Projektdateien kann auf die gleiche Weise verwiesen werden wie auf Buildeigenschaften. Um die PATH-Umgebungsvariable in der Projektdatei zu verwenden, verwenden Sie beispielsweise $(Path). Wenn das Projekt eine Eigenschaftendefinition enthält, die denselben Namen wie eine Umgebungsvariable hat, wird der Wert der Umgebungsvariablen von der Eigenschaft im Projekt überschrieben. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Festlegen von Eigenschaften in der Befehlszeile

Eigenschaften können an der Befehlszeile mit dem Befehlszeilenschalter -property oder -p definiert werden. Die in der Projektdatei und in Umgebungsvariablen festgelegten Eigenschaftswerte werden durch die Eigenschaftswerte überschrieben, die von der Befehlszeile empfangen werden.

**So legen Sie einen Eigenschaftswert über die Befehlszeile fest:**

1. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```output
    Configuration is Release.
    ```

MSBuild erstellt die Configuration-Eigenschaft und weist dieser den Wert "Release" zu.

## <a name="special-characters"></a>Sonderzeichen

Bestimmte Zeichen haben in MSBuild-Projektdateien eine besondere Bedeutung. Beispiele für solche Zeichen sind Semikolons (;) und Sternchen (*). Um diese Sonderzeichen als Literale in einer Projektdatei zu verwenden, müssen sie mit der Syntax %\<xx> angegeben werden, wobei \<xx> den ASCII-Hexadezimalwert des Zeichens darstellt.

Ändern Sie die Message-Aufgabe, um den Wert der Configuration-Eigenschaft mit Sonderzeichen anzuzeigen, um sie besser lesbar zu machen.

**So verwenden Sie Sonderzeichen im Message-Task:**

1. Ersetzen Sie im Code-Editor beide Message-Aufgaben durch folgende Zeile:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Speichern Sie die Projektdatei.

1. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```output
    $(Configuration) is "Debug"
    ```

Weitere Informationen finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Buildelemente

Als Element wird eine Information, in der Regel ein Dateiname, bezeichnet, die als Eingabe für das Buildsystem verwendet wird. Eine Auflistung von Elementen, die Quelldateien darstellen, kann beispielsweise an die Aufgabe Compile übergeben werden, um sie zu einer Assembly zu kompilieren.

Alle Elemente sind untergeordnete Elemente von ItemGroup-Elementen. Der Elementname entspricht dem Namen des untergeordneten Elements, und der Elementwert entspricht dem Wert des Include-Attributs für das untergeordnete Element. Die Werte von Elementen mit gleichem Namen werden in Elementtypen dieses Namens erfasst.  Ein auf ein Objekt angewendeter

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

definiert eine Elementgruppe mit zwei Elementen. Der Elementtyp „Compile“ verfügt über zwei Werte: *Program.cs* und *Properties\AssemblyInfo.cs*.

Mit folgendem Code wird der gleiche Elementtyp erstellt, indem die beiden durch ein Semikolon getrennten Dateien in einem Include-Attribut deklariert werden.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

> [!NOTE]
> Dateipfade sind relativ zum Ordner, der die MSBuild-Projektdatei enthält, auch wenn es sich bei der Projektdatei um eine importierte Projektdatei handelt. Es gibt einige Ausnahmen, z. B. bei Verwendung der Elemente [Import](import-element-msbuild.md) und [UsingTask](usingtask-element-msbuild.md).

## <a name="examine-item-type-values"></a>Untersuchen der Elementtypwerte

 Werte eines Elementtyps rufen Sie mit der folgenden Syntax ab, wobei ItemType den Name des Elementtyps darstellt:

```xml
@(ItemType)
```

Den Compile-Elementtyp in der Projektdatei untersuchen Sie mithilfe der folgenden Syntax.

**So untersuchen Sie Elementtypwerte:**

1. Ersetzen Sie im Code-Editor die Aufgabe für das Ziel HelloWorld durch den folgenden Code:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Speichern Sie die Projektdatei.

1. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Prüfen Sie die Ausgabe. Die folgende lange Zeile sollte angezeigt werden:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Die Werte eines Elementtyps werden standardmäßig durch Semikolons getrennt.

Wenn Sie das Trennzeichen für einen Elementtyp ändern möchten, verwenden Sie die folgende Syntax, wobei ItemType den Elementtyp und Separator eine Zeichenfolge aus einem oder mehreren Trennzeichen darstellt:

```xml
@(ItemType, Separator)
```

Ändern Sie die Message-Aufgabe, um Compile-Elemente mithilfe von Wagenrückläufen und Zeilenvorschüben (%0A%0D) auf jeweils eigenen Zeilen anzuzeigen.

**So zeigen Sie Elementtypwerte auf jeweils eigenen Zeilen an**

1. Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Speichern Sie die Projektdatei.

3. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prüfen Sie die Ausgabe. Die folgenden Zeilen sollten angezeigt werden:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Include, Exclude und Platzhalter

 Sie können mit dem Include-Attribut die Platzhalter „*“, „\*\*“ und „?“ verwenden, um einem Elementtyp Elemente hinzuzufügen. Ein auf ein Objekt angewendeter

```xml
<Photos Include="images\*.jpeg" />
```

 fügt alle Dateien mit der Dateierweiterung *JPEG* im Ordner *images* dem Photos-Elementtyp hinzu, während

```xml
<Photos Include="images\**\*.jpeg" />
```

 alle Dateien mit der Dateierweiterung *JPEG* im Ordner *images* und allen Unterordnern dem Photos-Elementtyp hinzufügt. Weitere Beispiele finden Sie unter [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).

 Beachten Sie, dass deklarierte Elemente sofort dem jeweiligen Elementtyp hinzugefügt werden. Ein auf ein Objekt angewendeter

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 erstellt den Elementtyp „Photo“ mit allen Dateien im Ordner *images*, die die Dateierweiterung *JPEG* oder *GIF* aufweisen. Dies entspricht der folgenden Zeile:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Mit dem Exclude-Attribut können Sie ein Element aus einem Elementtyp ausschließen. Ein auf ein Objekt angewendeter

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 fügt dem Compile-Elementtyp alle Dateien mit der Dateierweiterung *CS* hinzu, mit Ausnahme von Dateien, deren Namen die Zeichenfolge *Designer* enthalten. Weitere Beispiele finden Sie unter [Vorgehensweise: Ausschließen von Dateien aus dem Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md).

Das Exclude-Attribut wirkt sich nur auf die Elemente aus, die über das Include-Attribut in dem Elementelement hinzugefügt wurden, das beide enthält. Ein auf ein Objekt angewendeter

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

In diesem Beispiel wird die Datei *Form1.cs*, die im vorherigen Elementelement hinzugefügt wurde, nicht ausgeschlossen.

**So schließen Sie Elemente ein oder aus**

1. Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Fügen Sie diese Elementgruppe genau nach dem Import-Element hinzu:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Speichern Sie die Projektdatei.

4. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Elementmetadaten

 Zusätzlich zu den Informationen aus dem Include-Attribut und dem Exclude-Attribut können Elemente Metadaten enthalten. Diese Metadaten können von Aufgaben verwendet werden, die neben dem Elementwert weitere Informationen zu den Elementen erfordern.

 Elementmetadaten werden in der Projektdatei deklariert, indem ein Element mit dem Namen der Metadaten als untergeordnetes Element des Elements erstellt wird. Ein Element kann über 0 (null) oder mehr Metadatenwerte verfügen. Das folgende CSFile-Element weist z. B. Culture-Metadaten mit dem Wert "Fr" auf:

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Den Metadatenwert eines Elementtyps rufen Sie mit der folgenden Syntax ab, wobei ItemType den Namen des Elementtyps darstellt und MetaDataName den Namen der Metadaten:

```xml
%(ItemType.MetaDataName)
```

**So untersuchen Sie Elementmetadaten:**

1. Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Speichern Sie die Projektdatei.

3. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prüfen Sie die Ausgabe. Die folgenden Zeilen sollten angezeigt werden:

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Der Ausdruck "Compile.DependentUpon" wird mehrmals angezeigt. In dieser Syntax führt die Verwendung von Metadaten in einem Ziel zur "Batchverarbeitung". Batchverarbeitung bedeutet, dass die Aufgaben innerhalb des Ziels für jeden eindeutigen Metadatenwert einmal ausgeführt werden. Dies ist die MSBuild-Skriptentsprechung des häufig verwendeten Programmierkonstrukts "for-Schleife". Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Bekannte Metadaten

 Wenn einer Elementliste ein Element hinzugefügt wird, werden diesem Element stets bekannte Metadaten zugewiesen. Beispielsweise gibt %(Filename) den Dateinamen eines beliebigen Elements zurück. Eine vollständige Liste bekannter Metadaten finden Sie unter [Bekannte Elementmetadaten](../msbuild/msbuild-well-known-item-metadata.md).

**So untersuchen Sie bekannte Metadaten:**

1. Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Speichern Sie die Projektdatei.

3. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prüfen Sie die Ausgabe. Die folgenden Zeilen sollten angezeigt werden:

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Der Vergleich der beiden obigen Beispiele zeigt, dass zwar nicht jedes Element im Compile-Elementtyp DependentUpon-Metadaten aufweist, doch alle Elemente die bekannten Filename-Metadaten aufweisen.

### <a name="metadata-transformations"></a>Transformationen von Metadaten

 Elementlisten können in neue Elementlisten umgewandelt werden. Eine Elementliste transformieren Sie mit der folgenden Syntax, wobei \<ItemType> den Namen des Elementtyps darstellt und \<MetadataName> den Namen der Metadaten:

```xml
@(ItemType -> '%(MetadataName)')
```

Beispielsweise kann eine Elementliste von Quelldateien über einen Ausdruck, z. B. `@(SourceFiles -> '%(Filename).obj')`, in eine Auflistung von Objektdateien transformiert werden. Weitere Informationen finden Sie unter [Transformationen](../msbuild/msbuild-transforms.md).

**So transformieren Sie Elemente mit Metadaten:**

1. Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Speichern Sie die Projektdatei.

3. Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Beachten Sie, dass die in dieser Syntax ausgedrückten Metadaten keine Batchverarbeitung verursachen.

## <a name="next-steps"></a>Nächste Schritte

 Einzelne Schritte zum Erstellen einer einfachen Projektdatei finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Siehe auch

- [Übersicht über MSBuild](../msbuild/msbuild.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
