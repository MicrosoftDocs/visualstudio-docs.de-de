---
title: Bildbibliothek-Viewer | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Visual Studio-Bildbibliothek-Viewer-Tool, das Bild Manifeste lädt und durchsucht, sodass Sie Bildattribute anzeigen und bearbeiten können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae9090604a16196c43b80140395eb3401215d665
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761270"
---
# <a name="image-library-viewer"></a>Bildbibliotheks-Viewer
Das Visual Studio-Bildbibliothek-Viewer-Tool kann Bild Manifeste laden und Durchsuchen, sodass der Benutzer diese auf die gleiche Weise wie Visual Studio bearbeiten kann. Der Benutzer kann background, sizes, dpi, High Contrast und andere Einstellungen ändern. Das Tool zeigt außerdem ladeinformationen für jedes Bild Manifest an und zeigt Quell Informationen für jedes Bild im Bild Manifest an. Dieses Tool eignet sich für folgende Aktionen:

1. Fehlerdiagnose

2. Sicherstellen, dass Attribute in benutzerdefinierten Bild Manifesten richtig festgelegt

3. Suchen nach Bildern im Visual Studio-Image Katalog, damit eine Visual Studio-Erweiterung Bilder verwenden kann, die dem Stil von Visual Studio entsprechen

   ![Bildbibliotheks-Viewer-Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Bildbibliotheks-Viewer-Hero")

   **Bilmoniker**

   Ein bilmoniker (oder ein Moniker für Short) ist ein GUID: ID-Paar, das ein Image-oder Image Listen Medienobjekt in der Bildbibliothek eindeutig identifiziert.

   **Bild Manifest-Dateien**

   Bild Manifest-Dateien (. imagemanifest) sind XML-Dateien, die eine Gruppe von Image-Assets definieren, die Moniker, die diese Assets darstellen, und das echte Bild bzw. die einzelnen Bilder, die die einzelnen Assets darstellen. Bilmanifeste können eigenständige Images oder Bildlisten für die Legacy-Benutzeroberflächen Unterstützung definieren. Außerdem gibt es Attribute, die entweder für das Medienobjekt oder für die einzelnen Images hinter den einzelnen Assets festgelegt werden können, um zu ändern, wann und wie diese Objekte angezeigt werden.

   **Schema des Image Manifests**

   Ein umfassendes Bild Manifest sieht wie folgt aus:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symbols**

 Zur Unterstützung der Lesbarkeit und Wartung kann das Bild Manifest Symbole für Attributwerte verwenden. Symbole werden wie folgt definiert:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Unterelement**|**Definition**|
|-|-|
|Importieren|Importiert die Symbole der angegebenen Manifest-Datei für die Verwendung im aktuellen Manifest.|
|Guid|Das Symbol stellt eine GUID dar und muss mit der GUID-Formatierung identisch sein.|
|ID|Das Symbol stellt eine ID dar und muss eine nicht negative Ganzzahl sein.|
|String|Das Symbol stellt einen beliebigen Zeichen folgen Wert dar.|

 Bei Symbolen wird die Groß-/Kleinschreibung beachtet und mithilfe der Syntax $ (Symbol Name) auf Sie verwiesen:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Einige Symbole sind für alle Manifeste vordefiniert. Diese können im URI-Attribut des-Elements oder des-Elements verwendet werden \<Source> \<Import> , um auf Pfade auf dem lokalen Computer zu verweisen.

|**Symbol**|**Beschreibung**|
|-|-|
|CommonProgramFiles|Der Wert der Umgebungsvariablen "% COMMONPROGRAM Files%"|
|LocalAppData|Der Wert der Umgebungsvariablen "% LocalAppData%"|
|ManifestFolder|Der Ordner, der die Manifest-Datei enthält.|
|Ordner MyDocuments|Der vollständige Pfad des Ordners "eigene Dateien" des aktuellen Benutzers.|
|ProgramFiles|Der Wert der Umgebungsvariablen "% Program Files%"|
|System|Der Ordner "Windows\System32"|
|WinDir|Der Wert der Umgebungsvariablen "% windir%".|

 **Bild**

 Das- \<Image> Element definiert ein Bild, auf das von einem Moniker verwiesen werden kann. Die GUID und die ID, die zusammen aus dem bilmoniker entnommen wurden. Der Moniker für das Bild muss in der gesamten Bildbibliothek eindeutig sein. Wenn mehr als ein Bild über einen angegebenen Moniker verfügt, ist der erste, der beim Aufbau der Bibliothek aufgetreten ist, der einzige, der beibehalten wird.

 Sie muss mindestens eine Quelle enthalten. Obwohl Größen neutrale Quellen die besten Ergebnisse für eine breite Palette von Größen liefern, sind Sie nicht erforderlich. Wenn der Dienst nach einem Image einer Größe gefragt wird, die nicht im \<Image> -Element definiert ist, und keine Größen neutrale Quelle vorhanden ist, wählt der Dienst die beste Größen spezifische Quelle aus und skaliert Sie auf die angeforderte Größe.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Attribut**|**Definition**|
|-|-|
|Guid|Benötigten Der GUID-Teil des bilmonikers.|
|ID|Benötigten Der ID-Teil des bilmonikers.|
|Allowcolorinversion|[Optional, Standardwert true] Gibt an, ob das Bild seine Farben Programm gesteuert invertiert werden kann, wenn es in einem dunklen Hintergrund verwendet wird.|

 **Quelle**

 Das- \<Source> Element definiert ein einzelnes Bild Quell Medienobjekt (XAML und PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Attribut**|**Definition**|
|-|-|
|Uri|Benötigten Ein URI, der definiert, wo das Image geladen werden kann. Folgende Werte sind möglich:<br /><br /> -Ein [Paket-URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) mit der Application:///-Autorität<br /><br /> -Einen absoluten Komponenten Ressourcen Verweis<br /><br /> -Ein Pfad zu einer Datei, die eine native Ressource enthält.|
|Hintergrund|Optionale Gibt an, welche Art von Hintergrund die Quelle verwendet werden soll.<br /><br /> Folgende Werte sind möglich:<br /><br /> - *Light*: die Quelle kann auf einem hellen Hintergrund verwendet werden.<br /><br /> - *Dunkel*: die Quelle kann in einem dunklen Hintergrund verwendet werden.<br /><br /> - *HighContrast*: die Quelle kann in einem beliebigen Hintergrund im hoher Kontrast Modus verwendet werden.<br /><br /> - *Highkontra stlight*: die Quelle kann im hoher Kontrast Modus auf einem hellen Hintergrund verwendet werden.<br /><br /> -*Highkontra stdark*: die Quelle kann im hoher Kontrast Modus in einem dunklen Hintergrund verwendet werden.<br /><br /> Wenn das **Background** -Attribut weggelassen wird, kann die Quelle in jedem Hintergrund verwendet werden.<br /><br /> Wenn **Background** " *Light*", " *Dark*", " *highkontra stlight*" oder " *highkontra stdark*" ist, werden die Farben der Quelle nie invertiert. Wenn **Background** ausgelassen oder auf *HighContrast* festgelegt wird, wird die Inversion der Farben der Quelle durch das **allowcolorinversion** -Attribut des Bilds gesteuert.|

 Ein- \<Source> Element kann genau eines der folgenden optionalen unter Elemente aufweisen:

|**Element**|**Attribute (alle erforderlich)**|**Definition**|
|-|-|-|
|\<Size>|Wert|Die Quelle wird für Images der angegebenen Größe (in Geräte Einheiten) verwendet. Das Bild wird quadratisch.|
|\<SizeRange>|MinSize, MaxSize|Die Quelle wird für Images von MinSize bis MaxSize (in Geräte Einheiten) inklusive verwendet. Das Bild wird quadratisch.|
|\<Dimensions>|Width, Height|Die Quelle wird für Bilder mit der angegebenen Breite und Höhe (in Geräte Einheiten) verwendet.|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Die Quelle wird für Bilder von der minimalen Breite/Höhe bis zur maximalen Breite bzw. Höhe (in Geräte Einheiten) einschließlich der maximalen Breite/Höhe verwendet.|

 Ein- \<Source> Element kann auch über ein optionales Unterelement verfügen \<NativeResource> , das ein-Objekt definiert, \<Source> das aus einer nativen Assembly anstatt aus einer verwalteten Assembly geladen wird.

```xml
<NativeResource Type="type" ID="int" />
```

|**Attribut**|**Definition**|
|-|-|
|type|Benötigten Der Typ der systemeigenen Ressource, entweder XAML oder PNG|
|ID|Benötigten Der ganzzahlige ID-Teil der systemeigenen Ressource.|

 **ImageList**

 Das- \<ImageList> Element definiert eine Auflistung von Bildern, die in einem einzelnen Strip zurückgegeben werden können. Der Strip baut bei Bedarf Bedarfs gesteuert auf.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Attribut**|**Definition**|
|-|-|
|Guid|Benötigten Der GUID-Teil des bilmonikers.|
|ID|Benötigten Der ID-Teil des bilmonikers.|
|Extern|[Optional, Standard false] Gibt an, ob der bilmoniker auf ein Bild im aktuellen Manifest verweist.|

 Der Moniker für das enthaltene Bild muss nicht auf ein Bild verweisen, das im aktuellen Manifest definiert ist. Wenn das enthaltene Bild in der Bildbibliothek nicht gefunden werden kann, wird an seiner Stelle ein leeres Platzhalter Bild verwendet.

## <a name="how-to-use-the-tool"></a>Verwenden des Tools
 **Validieren eines benutzerdefinierten Bild Manifests**

 Zum Erstellen eines benutzerdefinierten Manifests sollten Sie das ManifestFromResources-Tool verwenden, um das Manifest automatisch zu generieren. Starten Sie zum Überprüfen des benutzerdefinierten Manifests den Bild Bibliotheks-Viewer, und wählen Sie Datei > Pfade festlegen... zum Öffnen des Dialog Felds "Verzeichnisse suchen". Das Tool verwendet die Such Verzeichnisse, um bildinmanifeste zu laden. es wird aber auch verwendet, um die DLL-Dateien zu suchen, die die Bilder in einem Manifest enthalten. Stellen Sie daher sicher, dass Sie das Manifest und die DLL-Verzeichnisse in diesem Dialogfeld einschließen.

 ![Bildbibliotheks-Viewer-Suche](../../extensibility/internals/media/image-library-viewer-search.png "Bildbibliotheks-Viewer-Suche")

 Klicken Sie auf **hinzufügen...** , um neue Such Verzeichnisse auszuwählen und nach Manifesten und den entsprechenden DLLs zu suchen. Das Tool speichert diese Such Verzeichnisse und kann aktiviert oder deaktiviert werden, indem ein Verzeichnis überprüft oder deaktiviert wird.

 Standardmäßig versucht das Tool, das Visual Studio-Installationsverzeichnis zu finden und diese Verzeichnisse der Liste der Such Verzeichnisse hinzuzufügen. Sie können manuell Verzeichnisse hinzufügen, die das Tool nicht findet.

 Nachdem alle Manifeste geladen wurden, kann das Tool verwendet werden, um **Hintergrund** Farben, **dpi**, **hoher Kontrast** oder **Graustufen** für die Bilder ein-und auszuschalten, damit ein Benutzer Bild Ressourcen visuell überprüfen kann, um sicherzustellen, dass Sie für verschiedene Einstellungen ordnungsgemäß gerendert werden.

 ![Bildbibliotheks-Viewer-Hintergrund](../../extensibility/internals/media/image-library-viewer-background.png "Bildbibliotheks-Viewer-Hintergrund")

 Die Hintergrundfarbe kann auf "Hell", "dunkel" oder einen benutzerdefinierten Wert festgelegt werden. Wenn Sie "benutzerdefinierte Farbe" auswählen, wird ein Farbauswahl Dialogfeld geöffnet, und diese benutzerdefinierte Farbe wird dem unteren Rand des Kombinations Felds für den Hintergrund hinzugefügt.

 ![Bildbibliotheks-Viewer, „Benutzerdefinierte Farbe“](../../extensibility/internals/media/image-library-viewer-custom-color.png "Bildbibliotheks-Viewer, „Benutzerdefinierte Farbe“")

 Wenn Sie einen bilmoniker auswählen, werden die Informationen zu jedem echten Bild hinter diesem Moniker im Bild Detailbereich auf der rechten Seite angezeigt. Der Bereich ermöglicht Benutzern auch das Kopieren eines Monikers anhand des Namens oder des Rohdaten-GUID: ID-Werts.

 ![Bildbibliotheks-Viewer-Bilddetails](../../extensibility/internals/media/image-library-viewer-image-details.png "Bildbibliotheks-Viewer-Bilddetails")

 Welche Informationen für die einzelnen Bildquellen angezeigt werden, enthält die Art des Hintergrunds, in dem Sie angezeigt wird, ob Sie das Design oder die Unterstützung von hoher Kontrast, die Größen, für die Sie gültig ist, oder ob Sie Größen neutral ist, und ob das Image aus einer nativen Assembly stammt.

 ![Bildbibliotheks-Viewer-Design „Dose“](../../extensibility/internals/media/image-library-viewer-can-theme.png "Bildbibliotheks-Viewer-Design „Dose“")

 Beim Validieren eines Bild Manifests wird empfohlen, dass Sie das Manifest und die Image-dll an ihren realen Standorten bereitstellen. Dadurch wird überprüft, ob alle relativen Pfade ordnungsgemäß funktionieren und ob die Bildbibliothek das Manifest und die Bild-dll finden und laden kann.

 **Suchen nach Image Catalog knownmonikers**

 Um die Visual Studio-Formatierung besser abzugleichen, kann eine Visual Studio-Erweiterung Bilder im Visual Studio-Image Katalog verwenden, anstatt Sie zu erstellen und zu verwenden. Dies hat den Vorteil, dass diese Images nicht beibehalten werden müssen, und es wird sichergestellt, dass das Image über ein High-dpi-Unterstützungs Bild verfügt, damit es in allen von Visual Studio unterstützten dpi-Einstellungen korrekt aussehen sollte.

 Der Bildbibliothek-Viewer ermöglicht das Durchsuchen eines Manifests, sodass ein Benutzer den Moniker finden kann, der ein imageasset darstellt, und diesen Moniker im Code verwendet. Um nach Bildern zu suchen, geben Sie den gewünschten Suchbegriff in das Suchfeld ein, und drücken Sie die EINGABETASTE. In der Statusleiste unten wird angezeigt, wie viele Übereinstimmungen aus den Gesamt Bildern in allen Manifesten gefunden wurden.

 ![Bildbibliotheks-Viewer-Filter](../../extensibility/internals/media/image-library-viewer-filter.png "Bildbibliotheks-Viewer-Filter")

 Bei der Suche nach bilmonikern in vorhandenen Manifesten wird empfohlen, nur die Moniker des Visual Studio-Bild Katalogs, andere absichtlich öffentlich zugängliche Moniker oder Ihre eigenen benutzerdefinierten Moniker zu suchen und zu verwenden. Wenn Sie nicht öffentliche Moniker verwenden, ist möglicherweise eine benutzerdefinierte Benutzeroberfläche beschädigt, oder die Images werden auf unerwartete Weise geändert, wenn oder wenn die nicht öffentlichen Moniker und Images geändert oder aktualisiert werden.

 Außerdem ist die Suche nach GUID möglich. Diese Art von Suche ist hilfreich, wenn die Liste in einem einzelnen Manifest oder in einem einzelnen unter Abschnitt eines Manifests gefiltert werden soll, wenn dieses Manifest mehrere GUIDs enthält.

 ![Bildbibliotheks-Viewer-Filter-GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Bildbibliotheks-Viewer-Filter-GUID")

 Zum Schluss ist auch das Suchen nach ID möglich.

 ![Bildbibliotheks-Viewer-Filter-ID](../../extensibility/internals/media/image-library-viewer-filter-id.png "Bildbibliotheks-Viewer-Filter-ID")

## <a name="notes"></a>Notizen

- Standardmäßig ruft das Tool mehrere Bild Manifeste im Visual Studio-Installationsverzeichnis ab. Das einzige, das über öffentlich verwendbare Moniker verfügt, ist das **Microsoft. VisualStudio. imagecatalog** -Manifest. GUID: ae27a6b0-E345-4288-96df-5eaf394ee369 (diese GUID **nicht** in einem benutzerdefinierten Manifest überschreiben): knownmoniker

- Das Tool versucht beim Start, alle gefundenen Bild Manifeste zu laden. Daher kann es einige Sekunden dauern, bis die Anwendung tatsächlich angezeigt wird. Beim Laden der Manifeste kann es auch langsam oder nicht reaktionsfähig sein.

## <a name="sample-output"></a>Beispielausgabe
 Dieses Tool generiert keine Ausgabe.
