---
title: Eigenschaftenfunktionen| Microsoft-Dokumentation
description: Erfahren Sie mehr über die Verwendung von Eigenschaftenfunktionen. Dies sind Aufrufe von .NET Framework-Methoden, die in MSBuild-Eigenschaftsdefinitionen verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c1e7a90d5d037865d9942ea1b91f33d7724706f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048819"
---
# <a name="property-functions"></a>Eigenschaftenfunktionen

Eigenschaftenfunktionen sind Aufrufe von .NET Framework-Methoden, die in MSBuild-Eigenschaftsdefinitionen erscheinen. Im Gegensatz zu Aufgaben können Eigenschaftenfunktionen außerhalb von Zielen verwendet werden, und sie werden ausgewertet, bevor Ziele ausgeführt werden.

Sie können die Systemzeit lesen, Zeichenfolgen vergleichen, reguläre Ausdrücke abgleichen und viele weitere Aktionen im Buildskript ausführen, ohne MSBuild-Aufgaben zu verwenden. MSBuild versucht, eine Zeichenfolge in eine Zahl und eine Zahl in eine Zeichenfolge zu konvertieren und nimmt je nach Bedarf andere Konvertierungen vor.

Zeichenfolgenwerte, die von Eigenschaftsfunktionen zurückgegeben werden, haben als [Sonderzeichen](msbuild-special-characters.md) ein Escapezeichen. Wenn Sie möchten, dass der Wert so behandelt wird, als wäre er direkt in der Projektdatei platziert, verwenden Sie `$([MSBuild]::Unescape())`, um die Sonderzeichen zu entfernen.

Eigenschaftenfunktionen sind in .NET Framework 4 und höher verfügbar.

## <a name="property-function-syntax"></a>Syntax einer Eigenschaftenfunktion

Nachfolgend sehen Sie drei Arten von Eigenschaftenfunktionen; jede Funktion hat eine andere Syntax:

- Zeichenfolgen-(Instanz-)Eigenschaftenfunktionen
- Statische Eigenschaftenfunktionen
- MSBuild-Eigenschaftenfunktionen

### <a name="string-property-functions"></a>Zeichenfolgen-Eigenschaftenfunktionen

Alle Buildeigenschaftswerte sind lediglich Zeichenfolgenwerte. Sie können Zeichenfolgen-(Instanz-)Methoden für beliebige Eigenschaftswerte verwenden. Sie können beispielsweise mithilfe des folgendes Codes den Laufwerksnamen (die ersten drei Buchstaben) aus einer Buildeigenschaft extrahieren, die einen vollständigen Pfad darstellt:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Statische Eigenschaftenfunktionen

In Ihrem Buildskript können Sie auf die statischen Eigenschaften und Methoden vieler Systemklassen zugreifen. Um den Wert einer statischen Eigenschaft abzurufen, verwenden Sie die folgende Syntax, wobei \<Class> der Name der Systemklasse und \<Property> der Name der Eigenschaft ist.

```
$([Class]::Property)
```

Sie können beispielsweise den folgenden Code verwenden, um eine Buildeigenschaft auf das aktuelle Datum und die aktuelle Uhrzeit festzulegen.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Um eine statische Methode aufzurufen, verwenden Sie die folgende Syntax, wobei \<Class> der Name der Systemklasse, \<Method> der Name der Methode und (\<Parameters>) die Parameterliste für die Methode ist:

```
$([Class]::Method(Parameters))
```

Verwenden Sie beispielsweise das folgende Skript, um eine Buildeigenschaft auf eine neu GUID festzulegen:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

In statischen Eigenschaftenfunktionen können Sie eine beliebige statische Methode oder Eigenschaft der folgenden Systemklassen verwenden:

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

Außerdem können Sie die folgenden statischen Methoden und Eigenschaften verwenden:

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System.Environment::GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System.IO.File::GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.IO.File::GetAttributes](xref:System.IO.File.GetAttributes*)
- [System.IO.File::GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System.IO.File::GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.IO.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Aufrufen von Instanzmethoden für statische Eigenschaften

Wenn Sie auf eine statische Eigenschaft zugreifen, die eine Objektinstanz zurückgibt, können Sie die Instanzmethoden dieses Objekts aufrufen. Um eine statische Methode aufzurufen, verwenden Sie die folgende Syntax, wobei \<Class> der Name der Systemklasse, \<Property> der Name der Eigenschaft, \<Method> der Name der Methode und (\<Parameters>) die Parameterliste für die Methode ist:

```
$([Class]::Property.Method(Parameters))
```

Der Name der Klasse muss mit dem Namespace vollqualifiziert sein.

Sie können beispielsweise den folgenden Code verwenden, um eine Buildeigenschaft auf das heutige Datum festzulegen.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild-Eigenschaftenfunktionen

In Ihrem Build kann auf mehrere statische Methoden zugegriffen werden, um Unterstützung für arithmetische, bitweise logische und Escapezeichen bereitzustellen. Um eine statische Methode aufzurufen, verwenden Sie die folgende Syntax, wobei \<Method> der Name der Methode und (\<Parameters>) die Parameterliste für die Methode ist.

```
$([MSBuild]::Method(Parameters))
```

Um beispielsweise zwei Eigenschaften mit numerischen Werten zu addieren, verwenden Sie den folgenden Code.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Nachfolgend finden Sie eine Liste mit MSBuild-Eigenschaftenfunktionen:

|Funktionssignatur|Beschreibung|
|------------------------|-----------------|
|double Add(double a, double b)|Addiert zwei double-Werte.|
|long Add(long a, long b)|Addiert zwei long-Werte.|
|double Subtract(double a, double b)|Subtrahiert zwei double-Werte.|
|long Subtract(long a, long b)|Subtrahiert zwei long-Werte.|
|double Multiply(double a, double b)|Multipliziert zwei double-Werte.|
|long Multiply(long a, long b)|Multipliziert zwei long-Werte.|
|double Divide(double a, double b)|Dividiert zwei double-Werte.|
|long Divide(long a, long b)|Dividiert zwei long-Werte.|
|double Modulo(double a, double b)|Modulo-Berechnung für zwei double-Werte.|
|long Modulo(long a, long b)|Modulo-Berechnung für zwei long-Werte.|
|string Escape(string unescaped)|Setzt gemäß den MSBuild-Escape-Regeln ein Escapezeichen vor die Zeichenfolge.|
|string Unescape(string escaped)|Entfernt gemäß den MSBuild-Escape-Regeln ein Escapezeichen vor der Zeichenfolge.|
|int BitwiseOr(int first, int second)|Führt einen bitweisen `OR`-Vorgang für das erste und zweite Element aus (first &#124; second).|
|int BitwiseAnd(int first, int second)|Führt einen bitweisen `AND`-Vorgang für das erste und zweite Element aus (first & second).|
|int BitwiseXor(int first, int second)|Führt einen bitweisen `XOR`-Vorgang für das erste und zweite Element aus (first ^ second).|
|int BitwiseNot(int first)|Führt einen bitweisen `NOT`-Vorgang aus (~first).|
|bool IsOsPlatform(string platformString)|Gibt an, ob die aktuelle Betriebssystemplattform `platformString` ist. `platformString` muss ein Mitglied von <xref:System.Runtime.InteropServices.OSPlatform> sein.|
|bool IsOSUnixLike()|„TRUE“, wenn das aktuelle Betriebssystem ein Unix-System ist.|
|string NormalizePath(params string[] path)|Ruft den vereinheitlichten vollständigen Pfad des bereitgestellten Pfads ab und stellt sicher, dass dieser die richtigen Verzeichnistrennzeichen für das aktuelle Betriebssystem enthält.|
|string NormalizeDirectory(params string[] path)|Ruft den vereinheitlichten vollständigen Pfad des bereitgestellten Verzeichnisses ab und stellt sicher, dass dieser die richtigen Verzeichnistrennzeichen für das aktuelle Betriebssystem und einen nachstehenden Schrägstrich enthält.|
|string EnsureTrailingSlash(string path)|Wenn der angegebene Pfad keinen nachgestellten Schrägstrich besitzt, fügen Sie einen hinzu. Wenn der Pfad eine leere Zeichenfolge ist, ändern Sie diesen nicht.|
|string GetPathOfFileAbove(string file, string startingDirectory)|Sucht in der Verzeichnisstruktur oberhalb des Speicherorts der aktuellen Builddatei oder basierend auf `startingDirectory` (sofern angegeben) nach einer Datei und gibt den vollständigen Pfad zu dieser Datei zurück.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Sucht entweder im angegebenen Verzeichnis oder an einem Speicherort in der Verzeichnisstruktur oberhalb dieses Verzeichnisses nach dem Verzeichnis einer Datei und gibt dieses zurück.|
|string MakeRelative(string basePath, string path)|Macht `path` relativ zu `basePath`. Bei `basePath` muss es sich um ein absolutes Verzeichnis handeln. Wenn `path` nicht relativ gemacht werden kann, wird dieses wörtlich zurückgegeben. Vergleichbar zu `Uri.MakeRelativeUri`.|
|string ValueOrDefault(string conditionValue, string defaultValue)|Geben Sie die Zeichenfolge im Parameter „DefaultValue“ nur zurück, wenn der Parameter „ConditionValue“ leer ist. Geben Sie ansonsten ist den Wert ConditionValue zurück.|

## <a name="nested-property-functions"></a>Geschachtelte Eigenschaftenfunktionen

Sie können Eigenschaftenfunktionen kombinieren, um komplexere Funktionen zu erstellen, wie das folgende Beispiel zeigt.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

In diesem Beispiel wird der Wert <xref:System.IO.FileAttributes>`Archive`-Bit (32 oder 0) der Datei, die durch den Pfad `tempFile` angegeben wird, zurückgegeben. Beachten Sie, dass Enumerationsdatenwerte innerhalb von Eigenschaftenfunktionen nicht nach Name angezeigt werden können. Stattdessen muss der numerische Wert (32) verwendet werden.

Metadaten können auch in geschachtelten Eigenschaftenfunktionen angezeigt werden. Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

Die `DoesTaskHostExist`-Eigenschaftenfunktion in MSBuild gibt zurück, ob derzeit ein Aufgabenhost für die angegebenen Laufzeit- und Architekturwerte installiert wird.

Diese Eigenschaftenfunktion hat die folgende Syntax:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

Die `EnsureTrailingSlash`-Eigenschaftenfunktion in MSBuild fügt einen nachgestellten Schrägstrich hinzu, wenn noch keiner vorhanden ist.

Diese Eigenschaftenfunktion hat die folgende Syntax:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

Die `GetDirectoryNameOfFileAbove`-Eigenschaftenfunktion in MSBuild sucht in den Verzeichnissen über dem aktuellen Verzeichnis im Pfad nach einer Datei.

 Diese Eigenschaftenfunktion hat die folgende Syntax:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Der folgende Code veranschaulicht diese Syntax beispielhaft.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

Die `GetPathOfFileAbove`-Eigenschaftenfunktion in MSBuild gibt den Pfad der angegebenen Datei zurück, wenn sie sich in der Verzeichnisstruktur oberhalb des aktuellen Verzeichnisses befindet. Sie ist zum Aufruf funktional äquivalent.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Diese Eigenschaftenfunktion hat die folgende Syntax:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

Die `GetRegistryValue`-Eigenschaftenfunktion in MSBuild gibt den Wert eines Registrierungsschlüssels zurück. Diese Funktion weist zwei Argumente auf, den Schlüsselnamen und den Wertnamen, und gibt den Wert aus der Registrierung zurück. Wenn Sie keinen Wertnamen angeben, wird der Standardwert zurückgegeben.

In den folgenden Beispielen wird veranschaulicht, wie diese Funktion verwendet wird:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

Die `GetRegistryValueFromView`-Eigenschaftenfunktion in MSBuild ruft Systemregistrierungsdaten anhand des Registrierungsschlüssels, des Werts und einer oder mehrerer geordneter Registrierungsansichten ab. Der Wert und der Schlüssel werden der Reihe nach in jeder Registrierungsansicht gesucht, bis sie gefunden wurden.

Die Syntax für diese Eigenschaftenfunktion ist wie folgt:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Das Windows-Betriebssystem mit 64 Bit speichert einen **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** -Registrierungsschlüssel, der eine **HKEY_LOCAL_MACHINE\SOFTWARE** -Registrierungsansicht für 32-Bit-Anwendungen darstellt.

Eine 32-Bit-Anwendung, die unter WOW64 ausgeführt wird, greift standardmäßig auf die 32-Bit-Registrierungsansicht zu, und eine 64-Bit-Anwendung greift auf die 64-Bit-Registrierungsansicht zu.

Die folgenden Registrierungsansichten sind verfügbar:

|Registrierungsansicht|Definition|
|-------------------|----------------|
|RegistryView.Registry32|Die Registrierungsansicht für 32-Bit-Anwendungen.|
|RegistryView.Registry64|Die Registrierungsansicht für 64-Bit-Anwendungen.|
|RegistryView.Default|Die Registrierungsansicht, die mit dem Prozess übereinstimmt, auf dem die Anwendung ausgeführt wird.|

Nachfolgend finden Sie ein Beispiel:

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

ruft die **SLRuntimeInstallPath** -Daten des **ReferenceAssemblies** -Schlüssels ab und sucht zuerst in der 64-Bit-Registrierungsansicht und dann in der 32-Bit-Registrierungsansicht.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

Die `MakeRelative`-Eigenschaftenfunktion in MSBuild gibt den relativen Pfad des zweiten Pfads relativ zum ersten Pfad an. Jeder Pfad kann eine Datei oder ein Ordner sein.

Diese Eigenschaftenfunktion hat die folgende Syntax:

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Der folgende Code veranschaulicht diese Syntax beispielhaft.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

Die `ValueOrDefault`-Eigenschaftenfunktion in MSBuild gibt das erste Argumente zurück, sofern dieses nicht Null oder leer ist. Wenn das erste Argument Null oder leer ist, gibt die Funktion das zweite Argument zurück.

In dem folgenden Beispiel wird veranschaulicht, wie diese Funktion verwendet wird.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="msbuild-condition-functions"></a>MSBuild-Bedingungsfunktionen

Die Funktionen `Exists` und `HasTrailingSlash` sind keine Eigenschaftenfunktionen. Sie können mit dem `Condition`-Attribut verwendet werden. Weitere Informationen finden Sie unter [MSBuild-Bedingungen](msbuild-conditions.md).

## <a name="see-also"></a>Siehe auch

- [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)

- [Übersicht über MSBuild](../msbuild/msbuild.md)
