---
title: MSBuild-Eigenschaften | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe von Name/Wert-Eigenschaftenpaaren Werte an Aufgaben übergeben, Bedingungen auswerten und Werte speichern kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61cff0bfa1db43b196d7f6403b5140f9af2947ba
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046138"
---
# <a name="msbuild-properties"></a>MSBuild-Eigenschaften

Eigenschaften sind Name/Wert-Paare, die zur Konfiguration von Builds verwendet werden können. Sie sind hilfreich, um Werte an Aufgaben zu übergeben, Bedingungen auszuwerten und Werte zu speichern, auf die in der gesamten Projektdatei verwiesen wird.

## <a name="define-and-reference-properties-in-a-project-file"></a>Definieren von Eigenschaften und Verweisen auf Eigenschaften in einer Projektdatei

 Eigenschaften werden deklariert, indem ein Element mit dem Namen der jeweiligen Eigenschaft als untergeordnetes Element eines [PropertyGroup](../msbuild/propertygroup-element-msbuild.md)-Elements erstellt wird. Durch das folgende XML wird beispielsweise die Eigenschaft `BuildDir` mit dem Wert `Build` erstellt.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 In der gesamten Projektdatei wird mit der Syntax $(\<PropertyName>) auf Eigenschaften verwiesen. Beispielsweise wird mit $(BuildDir) auf die Eigenschaft im vorangehenden Beispiel verwiesen.

 Eigenschaftswerte können durch Neudefinieren der Eigenschaft geändert werden. Der Wert der Eigenschaft `BuildDir` kann mit folgendem XML geändert werden:

```xml
<PropertyGroup>
    <BuildDir>Alternate</BuildDir>
</PropertyGroup>
```

 Eigenschaften werden in der Reihenfolge ausgewertet, in der sie in der Projektdatei angezeigt werden. Der neue Wert für `BuildDir` muss deklariert werden, nachdem der alte Wert zugewiesen wurde.

## <a name="reserved-properties"></a>Reservierte Eigenschaften

 Einige Eigenschaftennamen werden von MSBuild reserviert, um Informationen zur Projektdatei und zu den Binärdateien von MSBuild zu speichern. Auf diese Eigenschaften wird wie auf jede andere Eigenschaft mit der $-Notation verwiesen. Beispielsweise gibt $(MSBuildProjectFile) den vollständigen Namen der Projektdatei einschließlich der Dateierweiterung zurück.

 Weitere Informationen finden Sie unter [Vorgehensweise: Verweisen auf den Namen oder Speicherort der Projektdatei](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) und [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="environment-properties"></a>Umgebungseigenschaften

 Auf Umgebungsvariablen in Projektdateien kann auf die gleiche Weise verwiesen werden wie auf reservierte Eigenschaften. Um die `PATH`-Umgebungsvariable in der Projektdatei zu verwenden, verwenden Sie beispielsweise $(Path). Wenn das Projekt eine Eigenschaftendefinition enthält, die denselben Namen wie eine Umgebungseigenschaft hat, wird der Wert der Umgebungsvariablen von der Eigenschaft im Projekt überschrieben.

 Jedes MSBuild-Projekt hat einen isolierten Umgebungsblock: Es sieht nur Lese- und Schreibvorgänge im eigenen Block.  MSBuild liest Umgebungsvariablen nur, wenn die Eigenschaftenauflistung vor der Auswertung oder Erstellung der Projektdatei initialisiert wird. Danach sind Umgebungseigenschaften statisch, d. h jedes generierte Tool beginnt mit denselben Namen und Werten.

 Verwenden Sie die [Eigenschaftenfunktionen](../msbuild/property-functions.md) „System.Environment.GetEnvironmentVariable“, um den aktuellen Wert von Umgebungsvariablen aus einem generierten Tool abzurufen. Die bevorzugte Methode ist jedoch, den Aufgabenparameter <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> zu verwenden. Die Umgebungseigenschaften, die in diesem Zeichenfolgenarray festgelegt sind, können an das generierte Tool übergeben werden, ohne die Systemumgebungsvariablen zu beeinflussen.

> [!TIP]
> Nicht alle Umgebungsvariablen werden gelesen, um sie zu anfänglichen Eigenschaften zu machen. Jede Umgebungsvariable, deren Name kein gültiger MSBuild-Eigenschaftenname ist (z.B. "386"), wird ignoriert.

 Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="registry-properties"></a>Registrierungseigenschaften

 Systemregistrierungswerte können mit der nachfolgend angegebenen Syntax gelesen werden. Dabei steht `Hive` für den Registrierungshive (z.B. **HKEY_LOCAL_MACHINE** ), `MyKey` steht für den Schlüsselnamen, `MySubKey` für den Unterschlüsselnamen, und `Value` ist der Wert des Unterschlüssels.

```xml
$(registry:Hive\MyKey\MySubKey@Value)
```

 Lassen Sie `Value` weg, um den Standardunterschlüsselwert abzurufen.

```xml
$(registry:Hive\MyKey\MySubKey)
```

 Mit diesem Registrierungswert kann eine Buildeigenschaft initialisiert werden. Beispielsweise können Sie mit dem folgenden Code eine Buildeigenschaft erstellen, die die Webbrowser-Homepage für Visual Studio darstellt:

```xml
<PropertyGroup>
  <VisualStudioWebBrowserHomePage>
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)
  </VisualStudioWebBrowserHomePage>
<PropertyGroup>
```

## <a name="global-properties"></a>Globale Eigenschaften

 Mit MSBuild können Sie die Eigenschaften in der Befehlszeile mithilfe des Schalters **-property** (oder **-p** ) festlegen. Diese globalen Eigenschaftswerte überschreiben Eigenschaftswerte, die in der Projektdatei festgelegt werden. Dies betrifft auch Umgebungseigenschaften, nicht jedoch reservierte Eigenschaften ein, die nicht geändert werden können.

 Im folgenden Beispiel wird die globale `Configuration`-Eigenschaft auf `DEBUG` festgelegt.

```cmd
msbuild.exe MyProj.proj -p:Configuration=DEBUG
```

 Globale Eigenschaften können auch für untergeordnete Projekte in einem Build mit mehreren Projekten festgelegt oder geändert werden, indem das `Properties`-Attribut der MSBuild-Aufgabe verwendet wird. Globale Eigenschaften werden auch an untergeordnete Projekte weitergeleitet, es sei denn, das `RemoveProperties`-Attribut des MSBuild-Tasks wird dafür verwendet, eine Liste von Eigenschaften anzugeben, die nicht weitergeleitet werden sollen. Weitere Informationen finden Sie unter [MSBuild-Aufgabe](../msbuild/msbuild-task.md).

 Wenn Sie eine Eigenschaft angeben, indem Sie das `TreatAsLocalProperty`-Attribut in einem Projekttag verwenden, überschreibt dieser globale Eigenschaftswert nicht den Eigenschaftswert, der in der Projektdatei festgelegt ist. Weitere Informationen finden Sie unter [Project-Element (MSBuild)](../msbuild/project-element-msbuild.md) und [Vorgehensweise: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](../msbuild/how-to-build-the-same-source-files-with-different-options.md).

## <a name="property-functions"></a>Eigenschaftenfunktionen

 Ab .NET Framework Version 4 können Sie Eigenschaftenfunktionen verwenden, um MSBuild-Skripts auszuwerten. Sie können die Systemzeit lesen, Zeichenfolgen vergleichen, reguläre Ausdrücke abgleichen und viele weitere Aktionen ohne MSBuild-Aufgaben im Buildskript ausführen.

 Sie können Zeichenfolgen-(Instanz-)Methoden für beliebige Eigenschaftswerte verwenden, und Sie können die statischen Methoden für zahlreiche Systemklassen aufrufen. Beispielsweise können Sie so eine Buildeigenschaft auf das heutige Datum festlegen:

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

 Weitere Informationen sowie eine Liste der verfügbaren Eigenschaftenfunktionen finden Sie unter [Eigenschaftenfunktionen](../msbuild/property-functions.md).

## <a name="create-properties-during-execution"></a>Erstellen von Eigenschaften während der Ausführung

 Eigenschaften außerhalb von `Target`-Elementen werden die Werte im Rahmen der Auswertungsphase eines Builds zugewiesen. Während der anschließenden Ausführungsphase können die Eigenschaften erstellt oder geändert werden, wie nachfolgend veranschaulicht:

- Eigenschaften können von einer beliebigen Aufgabe ausgegeben werden. Das [Task](../msbuild/task-element-msbuild.md)-Element muss über ein untergeordnetes [Output](../msbuild/output-element-msbuild.md)-Element mit einem `PropertyName`-Attribut verfügen, um eine Eigenschaft auszugeben.

- Eigenschaften lassen sich mithilfe der [CreateProperty](../msbuild/createproperty-task.md)-Aufgabe ausgeben. Diese Verwendung ist veraltet.

- Ab .NET Framework 3.5 können `Target`-Elemente mit Eigenschaftendeklarationen in `PropertyGroup`-Elementen enthalten sein.

## <a name="store-xml-in-properties"></a>Speichern von XML in Eigenschaften

 Eigenschaften können beliebigen XML-Code enthalten, um die Übergabe von Werten an Aufgaben oder das Anzeigen von Protokollierungsinformationen zu unterstützen. Im folgenden Beispiel wird die `ConfigTemplate`-Eigenschaft veranschaulicht, die über einen Wert verfügt, der XML- und andere Eigenschaftenverweise enthält. MSBuild ersetzt die Eigenschaftenverweise durch ihre jeweiligen Eigenschaftswerte. Eigenschaftswerte werden in der Reihenfolge zugewiesen, in der sie angezeigt werden. `$(MySupportedVersion)`, `$(MyRequiredVersion)` und `$(MySafeMode)` sollten in diesem Beispiel daher bereits definiert worden sein.

```xml
<PropertyGroup>
    <ConfigTemplate>
        <Configuration>
            <Startup>
                <SupportedRuntime
                    ImageVersion="$(MySupportedVersion)"
                    Version="$(MySupportedVersion)"/>
                <RequiredRuntime
                    ImageVersion="$(MyRequiredVersion)"
                    Version="$(MyRequiredVersion)"
                    SafeMode="$(MySafeMode)"/>
            </Startup>
        </Configuration>
    </ConfigTemplate>
</PropertyGroup>
```

## <a name="see-also"></a>Siehe auch

- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [How to: Verwenden von Umgebungsvariablen in einem Build](../msbuild/how-to-use-environment-variables-in-a-build.md)
- [How to: Verweisen auf den Namen oder Speicherort der Projektdatei](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)
- [How to: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
- [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
- [Property-Element (MSBuild)](../msbuild/property-element-msbuild.md)
