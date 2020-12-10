---
title: Image-Dienst und-Katalog | Microsoft-Dokumentation
description: Dieser Artikel enthält Anleitungen und bewährte Methoden für die Übernahme von Visual Studio Image Service und Image catalog.
ms.custom: SEO-VS-2020
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41adcbe97f9d0779fbad465bac673a3f7cf086c7
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993535"
---
# <a name="image-service-and-catalog"></a>Image-Dienst und-Katalog
Dieses Cookbook enthält Anleitungen und bewährte Methoden für die Einführung von Visual Studio Image Service und Image Catalog, die in Visual Studio 2015 eingeführt wurden.

 Der in Visual Studio 2015 eingeführte Image Dienst ermöglicht Entwicklern das erzielen der besten Images für das Gerät und das ausgewählte Design des Benutzers, um das Bild anzuzeigen, einschließlich der korrekten Themen für den Kontext, in dem Sie angezeigt werden. Durch die Einführung des Image Service werden wichtige Probleme im Zusammenhang mit der Bestandsverwaltung, der hdpi-Skalierung und der Design Beseitigung vermieden.

|**Probleme heute**|**Lösungen**|
|-|-|
|Kombination von Hintergrundfarben|Integrierte Alpha Mischung|
|Design (einige) Bilder|Design Metadaten|
|hoher Kontrast Modus|Alternative hoher Kontrast Ressourcen|
|Benötigen Sie mehrere Ressourcen für verschiedene DPI-Modi.|Auswählbare Ressourcen mit Vektor basiertem Fall Back|
|Doppelte Bilder|Ein Bezeichner pro Bildkonzept|

 Gründe für die Übernahme des Image Service

- Immer das neueste "Pixel-perfekte" Image aus Visual Studio erhalten

- Sie können Ihre eigenen Images übermitteln und verwenden.

- Es ist nicht erforderlich, Ihre Images zu testen, wenn Windows eine neue DPI-Skalierung hinzufügt

- Behandeln von alten Architektur Hürden in ihren Implementierungen

  Die Visual Studio Shell-Symbolleiste vor und nach der Verwendung des Image Service:

  ![Bilddienst vorher und nachher](../extensibility/media/image-service-before-and-after.png "Bilddienst vorher und nachher")

## <a name="how-it-works"></a>Funktionsweise
 Der Image-Dienst kann ein für alle unterstützte Benutzeroberflächen Framework geeignetes Bitmapbild bereitstellen:

- WPF: BitmapSource

- WinForms: System. Drawing. Bitmap

- Win32: HBITMAP

  Bilddienst-Flussdiagramm

  ![Bilddienst-Flussdiagramm](../extensibility/media/image-service-flow-diagram.png "Bilddienst-Flussdiagramm")

  **Bilmoniker**

  Ein bilmoniker (oder ein Moniker für Short) ist ein GUID-/ID-Paar, das ein Image-oder Image Listen Medienobjekt in der Bildbibliothek eindeutig identifiziert.

  **Bekannte Moniker**

  Der Satz von bilmonikern, die im Visual Studio-Image Katalog enthalten sind und von jeder Visual Studio-Komponente oder-Erweiterung öffentlich genutzt werden.

  **Bild Manifest-Dateien**

  Bild Manifest-Dateien (*. imagemanifest*) sind XML-Dateien, die eine Gruppe von Image-Assets definieren, die Moniker, die diese Assets darstellen, und das echte Bild bzw. die einzelnen Bilder, die die einzelnen Assets darstellen. Bilmanifeste können eigenständige Images oder Bildlisten für die Legacy-Benutzeroberflächen Unterstützung definieren. Außerdem gibt es Attribute, die entweder für das Medienobjekt oder für die einzelnen Images hinter den einzelnen Assets festgelegt werden können, um zu ändern, wann und wie diese Objekte angezeigt werden.

  **Schema des Image Manifests**

  Ein umfassendes Bild Manifest sieht wie folgt aus:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
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
|Importieren|Importiert die Symbole der angegebenen Manifest-Datei zur Verwendung im aktuellen Manifest.|
|Guid|Das Symbol stellt eine GUID dar und muss mit der GUID-Formatierung identisch sein.|
|id|Das Symbol stellt eine ID dar und muss eine nicht negative ganze Zahl sein.|
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
|System|Der Ordner " *Windows\System32* "|
|WinDir|Der Wert der Umgebungsvariablen "% windir%".|

 **Bild**

 Das- \<Image> Element definiert ein Bild, auf das von einem Moniker verwiesen werden kann. Die GUID und die ID, die zusammen aus dem bilmoniker entnommen wurden. Der Moniker für das Bild muss in der gesamten Bildbibliothek eindeutig sein. Wenn mehr als ein Bild über einen angegebenen Moniker verfügt, ist der erste, der beim Aufbau der Bibliothek aufgetreten ist, der einzige, der beibehalten wird.

 Sie muss mindestens eine Quelle enthalten. Größen neutrale Quellen liefern die besten Ergebnisse für eine breite Palette von Größen, sind jedoch nicht erforderlich. Wenn der Dienst nach einem Image einer Größe gefragt wird, die nicht im \<Image> -Element definiert ist, und keine Größen neutrale Quelle vorhanden ist, wählt der Dienst die beste Größen spezifische Quelle aus und skaliert Sie auf die angeforderte Größe.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Attribut**|**Definition**|
|-|-|
|Guid|Benötigten Der GUID-Teil des bilmonikers.|
|id|Benötigten Der ID-Teil des bilmonikers.|
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
|Uri|Benötigten Ein URI, der definiert, wo das Image geladen werden kann. Folgende Werte sind möglich:<br /><br /> -Ein [Paket-URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) mit der Application:///-Autorität<br />-Einen absoluten Komponenten Ressourcen Verweis<br />-Ein Pfad zu einer Datei, die eine native Ressource enthält.|
|Hintergrund|Optionale Gibt an, welche Art von Hintergrund die Quelle verwendet werden soll.<br /><br /> Folgende Werte sind möglich:<br /><br /> *Hell:* Die Quelle kann auf einem hellen Hintergrund verwendet werden.<br /><br /> *Dunkel:* Die Quelle kann in einem dunklen Hintergrund verwendet werden.<br /><br /> *HighContrast:* Die Quelle kann in einem beliebigen Hintergrund im hoher Kontrast Modus verwendet werden.<br /><br /> *Highcontrastlight:* Die Quelle kann im hoher Kontrast Modus auf einem hellen Hintergrund verwendet werden.<br /><br /> *Highkontra stdark:* Die Quelle kann im hoher Kontrast Modus in einem dunklen Hintergrund verwendet werden.<br /><br /> Wenn das Background-Attribut weggelassen wird, kann die Quelle in jedem Hintergrund verwendet werden.<br /><br /> Wenn Background " *Light*", " *Dark*", " *highkontra stlight*" oder " *highkontra stdark*" ist, werden die Farben der Quelle nie invertiert. Wenn Background ausgelassen oder auf *HighContrast* festgelegt wird, wird die Inversion der Farben der Quelle durch das **allowcolorinversion** -Attribut des Bilds gesteuert.|

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
|id|Benötigten Der ganzzahlige ID-Teil der systemeigenen Ressource.|

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
|id|Benötigten Der ID-Teil des bilmonikers.|
|Extern|[Optional, Standard false] Gibt an, ob der bilmoniker auf ein Bild im aktuellen Manifest verweist.|

 Der Moniker für das enthaltene Bild muss nicht auf ein Bild verweisen, das im aktuellen Manifest definiert ist. Wenn das enthaltene Bild in der Bildbibliothek nicht gefunden werden kann, wird an seiner Stelle ein leeres Platzhalter Bild verwendet.

## <a name="using-the-image-service"></a>Verwenden des Image Service

### <a name="first-steps-managed"></a>Erste Schritte (verwaltet)
 Um den Image Dienst zu verwenden, müssen Sie Ihrem Projekt Verweise auf einige oder alle der folgenden Assemblys hinzufügen:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Erforderlich, wenn Sie den integrierten Image Katalog **knownmonikers** verwenden.

- *Microsoft.VisualStudio.Imaging.dll*

  - Erforderlich, wenn Sie " **crispimage** " und " **imagethemingutilities** " in der WPF-Benutzeroberfläche verwenden.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Erforderlich, wenn Sie die Typen **imagemoniker** und **imageattribute** verwenden.

  - **Embedinteroptypes** sollte auf true festgelegt werden.

- *Microsoft. VisualStudio. Shell. Interop. 14,0. designtime*

  - Erforderlich, wenn Sie den **IVsImageService2** -Typ verwenden.

  - **Embedinteroptypes** sollte auf true festgelegt werden.

- *Microsoft.VisualStudio.Utilities.dll*

  - Erforderlich, wenn Sie in der WPF-Benutzeroberfläche für " **imagethemingutilities. imagebackgroundcolor** " den Wert " **brushumcolorconverter** " verwenden.

- *Microsoft. VisualStudio. \<VSVersion> Shell. 1,0*

  - Erforderlich, wenn Sie den **ivsuiobject** -Typ verwenden.

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Erforderlich, wenn Sie die mit WinForms verknüpften UI-Hilfsprogramme verwenden.

  - **Embedinteroptypes** muss auf "true" festgelegt werden.

### <a name="first-steps-native"></a>Erste Schritte (nativ)
 Um den Image-Dienst zu verwenden, müssen Sie einige oder alle der folgenden Header in Ihr Projekt einschließen:

- **Knownimageids. h**

  - Erforderlich, wenn Sie den integrierten Image Katalog **knownmoniker** verwenden, aber den **imagemoniker** -Typ nicht verwenden können, z. b. beim Zurückgeben von Werten von **ivshierarchie getguidproperty** -oder **GetProperty** -aufrufen.

- **Knownmoniker. h**

  - Erforderlich, wenn Sie den integrierten Image Katalog **knownmonikers** verwenden.

- **ImageParameters140. h**

  - Erforderlich, wenn Sie die Typen **imagemoniker** und **imageattribute** verwenden.

- **VSShell140. h**

  - Erforderlich, wenn Sie den **IVsImageService2** -Typ verwenden.

- **Imagethemingutilities. h**

  - Erforderlich, wenn Sie den Image-Dienst nicht für Sie behandeln können.

  - Verwenden Sie diesen Header nicht, wenn der bilddienst Ihre Bildbearbeitung verarbeiten kann.

::: moniker range="vs-2017"
- **Vsuidpihelper. h**

  - Erforderlich, wenn Sie die dpi-Hilfsprogramme zum erhalten des aktuellen dpi verwenden.

::: moniker-end

::: moniker range=">=vs-2019"
- **Vsdpiawareness. h**

  - Erforderlich, wenn Sie die dpi-Informations Hilfen zum erhalten des aktuellen dpi verwenden.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Gewusst wie neue WPF-Benutzeroberfläche schreiben?

1. Beginnen Sie mit dem Hinzufügen der Assemblyverweise, die im Abschnitt Erste Schritte zum Projekt erforderlich sind. Sie müssen nicht alle Elemente hinzufügen. Fügen Sie also nur die benötigten Verweise hinzu. (Hinweis: Wenn Sie verwenden oder Zugriff auf **Farben** anstelle von **Pinsel** haben, können Sie den Verweis auf **Hilfsprogramme** überspringen, da Sie den Konverter nicht benötigen.)

2. Wählen Sie das gewünschte Bild aus, und erhalten Sie seinen Moniker. Verwenden Sie einen **knownmoniker**, oder verwenden Sie einen eigenen, wenn Sie über eigene benutzerdefinierte Images und Moniker verfügen.

3. Fügen Sie dem XAML-Code **knusprig Bilder** hinzu. (Siehe das folgende Beispiel.)

4. Legen Sie die **imagethemingutilities. imagebackgroundcolor** -Eigenschaft in der UI-Hierarchie fest. (Dieser Wert sollte an dem Speicherort festgelegt werden, an dem die Hintergrundfarbe bekannt ist, nicht notwendigerweise im **crispbild**.) (Siehe das folgende Beispiel.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Gewusst wie vorhandene WPF-Benutzeroberfläche aktualisieren?**

 Das Aktualisieren vorhandener WPF-Benutzeroberflächen ist ein relativ einfacher Prozess, der aus drei grundlegenden Schritten besteht:

1. Ersetzen \<Image> Sie alle Elemente in der Benutzeroberfläche durch- \<CrispImage> Elemente.

2. Alle Quell Attribute werden in monikerattribute geändert.

    - Wenn sich das Image nie ändert und Sie **knownmoniker** verwenden, binden Sie diese Eigenschaft statisch an den **knownmoniker**. (Siehe das obige Beispiel.)

    - Wenn sich das Image nie ändert und Sie Ihr eigenes benutzerdefiniertes Image verwenden, binden Sie statisch an Ihren eigenen Moniker.

    - Wenn das Image geändert werden kann, binden Sie das monikerattribut an eine Code Eigenschaft, die über Eigenschafts Änderungen benachrichtigt.

3. Legen Sie in der UI-Hierarchie den Wert **imagethemingutilities. imagebackgroundcolor** fest, um sicherzustellen, dass Color Inversion ordnungsgemäß funktioniert.

    - Hierfür ist möglicherweise die Verwendung der Klasse " **brushumcolorconverter** " erforderlich. (Siehe das obige Beispiel.)

## <a name="how-do-i-update-win32-ui"></a>Gewusst wie die Win32-Benutzeroberfläche aktualisieren?
 Fügen Sie dem Code nach Bedarf Folgendes hinzu, um das rohladen von Bildern zu ersetzen. Wechseln Sie bei Bedarf zum Zurückgeben von HBITMAPs im Vergleich zu hicons und HIMAGELIST.

 **Abbild Dienst**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Anfordern des Abbilds**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Gewusst wie Aktualisieren der WinForms-Benutzeroberfläche
 Fügen Sie dem Code nach Bedarf Folgendes hinzu, um das rohladen von Bildern zu ersetzen. Wechseln Sie nach Bedarf zum Zurückgeben von Bitmaps und Symbolen.

 **Hilfreiche using-Anweisung**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Abbild Dienst**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Anfordern des Abbilds**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Gewusst wie bilmoniker in einem neuen Tool Fenster verwenden?
 Die VSIX-Paket Projektvorlage wurde für Visual Studio 2015 aktualisiert. Um ein neues Tool Fenster zu erstellen, klicken Sie mit der rechten Maustaste auf das VSIX-Projekt, und wählen Sie   >  **Neues Element** hinzufügen (**STRG** + **UMSCHALT** + **a**) aus. Wählen Sie unter dem Knoten Erweiterbarkeit für die Projektsprache die Option **benutzerdefiniertes Tool Fenster** aus, geben Sie dem Tool Fenster einen Namen, und klicken Sie auf die Schaltfläche **Hinzufügen** .

 Dies sind die wichtigsten Orte für die Verwendung von Monikern in einem Tool Fenster. Befolgen Sie die folgenden Anweisungen:

1. Die Registerkarte "Tool Fenster", wenn die Registerkarten klein genug werden (auch im Fenster " **STRG** + **Tab** Fenster" verwendet).

    Fügen Sie diese Zeile zum Konstruktor für die Klasse hinzu, die vom **ToolWindowPane** -Typ abgeleitet wird:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Der Befehl zum Öffnen des Tool Fensters.

    Bearbeiten Sie in der *vsct* -Datei für das Paket die Befehls Schaltfläche des Tool Fensters:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Gewusst wie in einem vorhandenen Tool Fenster bilmoniker verwenden?**

   Das Aktualisieren eines vorhandenen Tool Fensters zur Verwendung von bilmonikern ähnelt den Schritten zum Erstellen eines neuen Tool Fensters.

   Dies sind die wichtigsten Orte für die Verwendung von Monikern in einem Tool Fenster. Befolgen Sie die folgenden Anweisungen:

3. Die Registerkarte "Tool Fenster", wenn die Registerkarten klein genug werden (auch im Fenster " **STRG** + **Tab** Fenster" verwendet).

   1. Entfernen Sie diese Zeilen (sofern vorhanden) im Konstruktor für die Klasse, die vom **ToolWindowPane** -Typ abgeleitet wird:

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Weitere Informationen finden Sie unterschritt #1 des "Gewusst wie verwenden Sie bildmoniker in einem neuen Tool Fenster". im oben stehenden Absatz.

4. Der Befehl zum Öffnen des Tool Fensters.

   - Weitere Informationen finden Sie unterschritt #2 des "Gewusst wie verwenden Sie bildmoniker in einem neuen Tool Fenster". im oben stehenden Absatz.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Gewusst wie verwenden Sie bildmoniker in einer vsct-Datei?
 Aktualisieren Sie die *vsct* -Datei, wie in den nachfolgenden nachfolgenden Zeilen angegeben:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **Was geschieht, wenn meine vsct-Datei auch von älteren Versionen von Visual Studio gelesen werden muss?**

 Ältere Versionen von Visual Studio erkennen das **iconismoniker** -Befehlsflag nicht. Sie können Images aus dem Image-Dienst in Versionen von Visual Studio verwenden, die es unterstützen, aber weiterhin alte Bilder in älteren Versionen von Visual Studio verwenden. Zu diesem Zweck können Sie die *vsct* -Datei unverändert lassen (und daher mit älteren Versionen von Visual Studio kompatibel sind) und eine CSV-Datei (durch Trennzeichen getrennte Werte) erstellen, die aus GUID/ID-Paaren, die im-Element der *vsct* -Datei definiert sind, \<Bitmaps> zu bilmoniker-GUID-/ID-Paaren zuordnet.

 Das Format der CSV-Datei für die Zuordnung lautet:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Die CSV-Datei wird mit dem Paket bereitgestellt, und der Speicherort wird durch die **iconmappingfilename** -Eigenschaft des **providemenuresource** -Paket Attributs angegeben:

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 Der **iconmappingfilename** ist entweder ein relativer Pfad, der implizit auf $PackageFolder $ (wie im obigen Beispiel) basiert, oder ein absoluter Pfad, der explizit in einem Verzeichnis liegt, das durch eine Umgebungsvariable definiert ist, wie z. b. *@ "% User Profile% \dir1\dir2\MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Gewusst wie portieren Sie ein Projekt System?
 **Bereitstellen von imagemonikern für ein Projekt**

1. Implementieren Sie **VSHPROPID_SupportsIconMonikers** für das **ivshierarchie** des Projekts, und geben Sie "true" zurück.

2. Implementieren Sie entweder **VSHPROPID_IconMonikerImageList** (bei Verwendung des ursprünglichen **Projekts VSHPROPID_IconImgList**) oder **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (wenn das ursprüngliche Projekt **VSHPROPID_IconHandle** und **VSHPROPID_OpenFolderIconHandle** verwendet hat).

3. Ändern Sie die Implementierung der ursprünglichen vshpropids für Symbole, um "Legacy"-Versionen der Symbole zu erstellen, wenn Sie von Erweiterungs Punkten angefordert werden. **IVsImageService2** bietet Funktionen, die zum erhalten dieser Symbole erforderlich sind.

   **Zusätzliche Anforderungen für VB/c#-Projektvarianten**

   Implementieren Sie nur **VSHPROPID_SupportsIconMonikers** , wenn Sie feststellen, dass Ihr Projekt der **äußerste** Typ ist. Andernfalls unterstützt der tatsächliche äußerste Typ möglicherweise keine bilmoniker in Wirklichkeit, und ihre Basiskonfiguration kann die benutzerdefinierten Images effektiv ausblenden.

   **Gewusst wie verwenden Sie bildmoniker in CPS?**

   Das Festlegen von benutzerdefinierten Images in CPS (Common Project System) kann manuell oder über eine Element Vorlage erfolgen, die das Project System Extensibility SDK enthält.

   **Verwenden des Project System Extensibility SDK**

   Befolgen Sie die Anweisungen unter [Bereitstellen von benutzerdefinierten Symbolen für den Projekttyp/Elementtyp](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) , um die CPS-Images anzupassen. Weitere Informationen zu CPS finden Sie in der [Dokumentation zum Visual Studio Project System Erweiterbarkeit](https://github.com/Microsoft/VSProjectSystem) .

   **Manuelles Verwenden von imagemonikers**

4. Implementieren und exportieren Sie die **iprojecttreemodifier** -Schnittstelle in Ihrem Projekt System.

5. Bestimmen Sie, welcher **knownmoniker** oder benutzerdefinierte bilmoniker Sie verwenden möchten.

6. Führen Sie in der **applymodifizierungsmethode** in der-Methode vor dem Zurückgeben der neuen Struktur die folgenden Schritte aus, ähnlich wie im folgenden Beispiel:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Wenn Sie eine neue Struktur erstellen, können Sie die benutzerdefinierten Images festlegen, indem Sie die gewünschten Moniker in die NewTree-Methode übergeben, ähnlich wie im folgenden Beispiel:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Gewusst wie von einem realen Bildstreifen in einen monikerbasierten Bildstreifen konvertieren?
 **Ich muss himagelists unterstützen.**

 Wenn ein bereits vorhandener Bildstreifen für den Code vorhanden ist, den Sie für die Verwendung des Image-dienplatzes aktualisieren möchten, Sie aber durch APIs eingeschränkt sind, die Bildlisten weiterleiten müssen, können Sie dennoch die Vorteile des Image Service nutzen. Um einen monikerbasierten Bildstreifen zu erstellen, führen Sie die folgenden Schritte aus, um ein Manifest aus vorhandenen Monikern zu erstellen.

1. Führen Sie das **ManifestFromResources** -Tool aus, und übergeben Sie dabei den Bildstreifen. Dadurch wird ein Manifest für den Strip generiert.

   - Empfohlen: Geben Sie einen nicht standardmäßigen Namen für das Manifest an, um seine Verwendung zu erfüllen.

2. Wenn Sie nur **knownmoniker** verwenden, gehen Sie folgendermaßen vor:

   - Ersetzen Sie den- \<Images> Abschnitt des Manifests durch \<Images/> .

   - Entfernen Sie alle subimage-IDs (alles mit \<imagestrip name> _ # #).

   - Empfohlen: benennen Sie das assetzguid-Symbol und das Image Strip-Symbol entsprechend der Verwendung um.

   - Ersetzen Sie jede **containedimage**-GUID durch $ (imagecatalogguid), ersetzen Sie jede **containedimage**-ID durch $ ( \<moniker> ), und fügen Sie jedem **containedimage** das Attribut extern = "true" hinzu.

       - \<moniker> muss durch den **knownmoniker** ersetzt werden, der mit dem Bild übereinstimmt, aber mit "knownmoniker". aus dem Namen entfernt.

   - Fügen Sie <Import Manifest = "$ (ManifestFolder) \\<relativen Installationsverzeichnis Pfad zu * \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest"/ \*> am Anfang des Abschnitts hinzu \<Symbols> .

       - Der relative Pfad wird von dem Bereitstellungsort bestimmt, der in der Setup Erstellung für das Manifest definiert ist.

3. Führen Sie das **ManifestToCode** -Tool aus, um Wrapper zu generieren, damit der vorhandene Code über einen Moniker verfügt, den er verwenden kann, um den Image-Dienst für den Bildstreifen abzufragen.

   - Empfohlen: Geben Sie nicht standardmäßige Namen für die Wrapper und Namespaces an, die für ihre Verwendung geeignet sind.

4. Nehmen Sie alle Hinzufügungen, Setup Erstellung/Bereitstellung und andere Codeänderungen vor, um mit dem Image-Dienst und den neuen Dateien zu arbeiten.

   Beispiel Manifest, das sowohl interne als auch externe Bilder enthält, um zu sehen, wie es aussehen sollte:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **Ich muss himagelists nicht unterstützen.**

1. Bestimmen Sie den Satz der **knownmoniker** , die den Bildern in Ihrem Bildstreifen entsprechen, oder erstellen Sie eigene Moniker für die Bilder in Ihrem Bildstreifen.

2. Aktualisieren Sie jede Zuordnung, die Sie verwendet haben, um das Image am erforderlichen Index im Bildstreifen zu erhalten, um die Moniker zu verwenden.

3. Aktualisieren Sie Ihren Code, um den Image-Dienst zum Anfordern von Monikern über die aktualisierte Zuordnung zu verwenden. (Dies kann bedeuten, dass Sie für verwalteten Code auf " **crispimages** " aktualisieren, HBITMAPs oder hicons aus dem Image-Dienst anfordern und Sie für nativen Code übergeben.)

## <a name="testing-your-images"></a>Testen von Images
 Mit dem Bildbibliothek-Viewer-Tool können Sie die bildmanifeste testen, um sicherzustellen, dass alles ordnungsgemäß erstellt wurde. Sie finden das Tool im [Visual Studio 2015 SDK](visual-studio-sdk.md). Dokumentation für dieses Tool und weitere Informationen finden Sie [hier](./internals/vssdk-utilities.md?view=vs-2015&preserve-view=true).

## <a name="additional-resources"></a>Zusätzliche Ressourcen

### <a name="samples"></a>Beispiele
 Einige der Visual Studio-Beispiele auf GitHub wurden aktualisiert, um zu veranschaulichen, wie Sie den Image Service als Teil verschiedener Visual Studio-Erweiterbarkeits Punkte verwenden können.

 [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples)Suchen Sie nach den neuesten Beispielen.

### <a name="tooling"></a>Tools
 Eine Reihe von Support Tools für den Image-Dienst wurde erstellt, um die Erstellung/Aktualisierung der Benutzeroberfläche zu unterstützen, die mit dem Image-Dienst funktioniert. Weitere Informationen zu den einzelnen Tools finden Sie in der Dokumentation, die in den Tools verfügbar ist. Die Tools sind als Teil des [Visual Studio 2015 SDK](visual-studio-sdk.md)enthalten.

 **ManifestFromResources**

 Das Manifest from Resources Tool verwendet eine Liste mit Bild Ressourcen (PNG oder XAML) und generiert eine Bild Manifest-Datei für die Verwendung dieser Images mit dem Image-Dienst.

 **ManifestToCode**

 Das Manifest to Code Tool nimmt eine bildmanifest-Datei an und generiert eine Wrapper Datei zum Verweisen auf die Manifestressourcen im Code (C++, c#, VB) oder *vsct* -Dateien.

 **Imagelibraryviewer**

 Das Bildbibliothek-Viewer-Tool kann Bild Manifeste laden und es dem Benutzer ermöglichen, diese auf die gleiche Weise zu manipulieren wie Visual Studio, um sicherzustellen, dass das Manifest ordnungsgemäß erstellt wurde. Der Benutzer kann Hintergrund, Größe, dpi-Einstellung, hoher Kontrast und andere Einstellungen ändern. Außerdem werden ladeinformationen angezeigt, um Fehler in den Manifesten zu finden, und die Quell Informationen für jedes Bild im Manifest werden angezeigt.

## <a name="faq"></a>Häufig gestellte Fragen

- Gibt es Abhängigkeiten, die Sie beim Laden einschließen müssen \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> ?

  - Legen Sie embedinteroptypes = "true" für alle Interop-DLLs fest.

- Gewusst wie ein Bild Manifest mit der Erweiterung bereitstellen?

  - Fügen Sie dem Projekt die *imagemanifest* -Datei hinzu.

  - Legen Sie "in VSIX einschließen" auf "true" fest.

- Ich aktualisiere mein CPS-Projekt System. Was ist mit **ImageName** und **stockiconservice** passiert?

  - Diese wurden entfernt, als CPS für die Verwendung von Monikern aktualisiert wurde. Sie müssen den **stockiconservice** nicht mehr aufrufen, sondern einfach den gewünschten **knownmoniker** an die Methode oder Eigenschaft übergeben, indem Sie die **toprojectsystemtype ()** -Erweiterungsmethode in den CPS-Hilfsprogramme verwenden. Eine Zuordnung von **ImageName** zu **knownmonikers** finden Sie unten:

    |**ImageName**|**Knownmoniker**|
    |-|-|
    |ImageName. offlinewebapp|Knownimageids. Web|
    |ImageName. WebReferencesFolder|Knownimageids. Web|
    |ImageName. openreferencefolder|Knownimageids. foldergeöffnet|
    |ImageName. referencefolder|Knownimageids. Reference|
    |ImageName. Reference|Knownimageids. Reference|
    |ImageName. sdlwebreferenzierung|Knownimageids. webreferencefolder|
    |ImageName. discowebreferenzierung|Knownimageids. DynamicDiscoveryDocument|
    |ImageName. Folder|Knownimageids. folderclosed|
    |ImageName. openfolder|Knownimageids. foldergeöffnet|
    |ImageName. excludfolder|Knownimageids. hiddenfolderclosed|
    |ImageName. openexcludfolder|Knownimageids. hiddenfoldergeöffnet|
    |ImageName. excludedfile|Knownimageids. hiddenfile|
    |ImageName. dependentfile|Knownimageids. generatefile|
    |ImageName. missingfile|KnownImageIds.Docvon "Umschlag Warnung"|
    |ImageName. WindowsForm|Knownimageids. WindowsForm|
    |ImageName. windowsusercontrol|Knownimageids. UserControl|
    |ImageName. windowscomponent|Knownimageids. componentfile|
    |ImageName.Xml-Schema|KnownImageIds.XML-Schema|
    |ImageName.XmlDatei|KnownImageIds.XMLDatei|
    |ImageName. Webform|Knownimageids. Web|
    |ImageName. WebService|Knownimageids. WebService|
    |ImageName. WebUserControl|Knownimageids. WebUserControl|
    |ImageName. webcustomusercontrol|Knownimageids. webcustomcontrol|
    |ImageName. asppage|Knownimageids. aspfile|
    |ImageName. globalapplicationclass|Knownimageids. SettingsFile|
    |ImageName. webConfig|KnownImageIds.Configurationfile|
    |ImageName.Htmlpage|KnownImageIds.HTMlfile|
    |ImageName. Stylesheet|Knownimageids. Stylesheet|
    |ImageName. scriptfile|KnownImageIds.JSSkript|
    |ImageName. Textfile|KnownImageIds.Doc-übergeordneten|
    |ImageName. SettingsFile|Knownimageids. Settings|
    |ImageName. Resources|KnownImageIds.Doc-Umschlag Gruppe|
    |ImageName. Bitmap|Knownimageids. Image|
    |ImageName. Icon|Knownimageids. IconFile|
    |ImageName. Image|Knownimageids. Image|
    |ImageName. ImageMap|Knownimageids. imagemapfile|
    |ImageName. XWORLD|"Knownimageids. xworldfile"|
    |ImageName. Audiodatei|Knownimageids. Sound|
    |ImageName. Video|Knownimageids. Media|
    |ImageName.Cab|KnownImageIds.CABProjekt|
    |ImageName. jar|Knownimageids. JarFile|
    |ImageName. DataEnvironment|Knownimageids. databel|
    |ImageName. previewfile|Knownimageids. Report|
    |ImageName. danglingreferenzierung|Knownimageids. referencewarning|
    |ImageName. XSLTFile|Knownimageids. XslTransform|
    |ImageName. Cursor|Knownimageids. Cursor Datei|
    |ImageName. appdesignerfolder|Knownimageids. Property|
    |ImageName. Data|Knownimageids. Database|
    |ImageName. Application|Knownimageids. Application|
    |ImageName. DataSet|Knownimageids. databasegroup|
    |ImageName. pfx|Knownimageids. Certificate|
    |ImageName. snk|Knownimageids. Rule|
    |ImageName. visualbasicproject|Knownimageids. vbprojectnode|
    |ImageName. csharpproject|Knownimageids. csprojectnode|
    |ImageName. Empty|Knownimageids. Blank|
    |ImageName. missingfolder|Knownimageids. folderoffline|
    |ImageName. sharedimportreferenzierung|Knownimageids. sharedproject|
    |ImageName. sharedprojectcs|Knownimageids. cssharedproject|
    |ImageName. sharedprojectvc|Knownimageids. cppsharedproject|
    |ImageName. sharedprojectjs|KnownImageIds.JSsharedproject|
    |ImageName. csharpcodefile|Knownimageids. CSFile Ode|
    |ImageName. visualbasiccodefile|Knownimageids. VBFile Ode|

  - Ich aktualisiere den Anbieter der Vervollständigungsliste. Welche **knownmoniker** entsprechen den alten Werten für **standardglyphgroup** und **standardglyph** ?

    |Name|Name|Name|
    |-|-|-|
    |Glyphgroupclass|Glyphitempublic|Classpublic|
    |Glyphgroupclass|Glyphiteminternal|Classinternal|
    |Glyphgroupclass|Glyphitemfriend|Classinternal|
    |Glyphgroupclass|Glyphitemprotected|Classprotehiert|
    |Glyphgroupclass|Glyphitemprivate|Classprivate|
    |Glyphgroupclass|Glyphitemshortcut|Classshortcut|
    |Glyphgroupconstant|Glyphitempublic|Constantpublic|
    |Glyphgroupconstant|Glyphiteminternal|Constantinternal|
    |Glyphgroupconstant|Glyphitemfriend|Constantinternal|
    |Glyphgroupconstant|Glyphitemprotected|Constantprotected|
    |Glyphgroupconstant|Glyphitemprivate|Constantprivate|
    |Glyphgroupconstant|Glyphitemshortcut|Constantshortcut|
    |Glyphgroupdelegat|Glyphitempublic|Delegatepublic|
    |Glyphgroupdelegat|Glyphiteminternal|Delegatein ternal|
    |Glyphgroupdelegat|Glyphitemfriend|Delegatein ternal|
    |Glyphgroupdelegat|Glyphitemprotected|Delegateprotected|
    |Glyphgroupdelegat|Glyphitemprivate|Delegateprivate|
    |Glyphgroupdelegat|Glyphitemshortcut|Delegateshortcut|
    |Glyphgroupum|Glyphitempublic|Enumerationpublic|
    |Glyphgroupum|Glyphiteminternal|Enumerationinternal|
    |Glyphgroupum|Glyphitemfriend|Enumerationinternal|
    |Glyphgroupum|Glyphitemprotected|Enumerationprotected|
    |Glyphgroupum|Glyphitemprivate|Enumerationprivate|
    |Glyphgroupum|Glyphitemshortcut|Enumerationshortcut|
    |Glyphgroupenummember|Glyphitempublic|Enumerationitempublic|
    |Glyphgroupenummember|Glyphiteminternal|Enumerationiteminternal|
    |Glyphgroupenummember|Glyphitemfriend|Enumerationiteminternal|
    |Glyphgroupenummember|Glyphitemprotected|Enumerationitemprotected|
    |Glyphgroupenummember|Glyphitemprivate|Enumerationitemprivate|
    |Glyphgroupenummember|Glyphitemshortcut|Enumerationitemshortcut|
    |Glyphgrouetvent|Glyphitempublic|Eventpublic|
    |Glyphgrouetvent|Glyphiteminternal|Eventinternal|
    |Glyphgrouetvent|Glyphitemfriend|Eventinternal|
    |Glyphgrouetvent|Glyphitemprotected|Eventprotected|
    |Glyphgrouetvent|Glyphitemprivate|Eventprivate|
    |Glyphgrouetvent|Glyphitemshortcut|Eventshortcut|
    |Glyphgroupexception|Glyphitempublic|Exceptionpublic|
    |Glyphgroupexception|Glyphiteminternal|Exceptioninternal|
    |Glyphgroupexception|Glyphitemfriend|Exceptioninternal|
    |Glyphgroupexception|Glyphitemprotected|Exceptionprotected|
    |Glyphgroupexception|Glyphitemprivate|Exceptionprivate|
    |Glyphgroupexception|Glyphitemshortcut|Exceptionshortcut|
    |Glyphgroupfield|Glyphitempublic|Fieldpublic|
    |Glyphgroupfield|Glyphiteminternal|Fieldinternal|
    |Glyphgroupfield|Glyphitemfriend|Fieldinternal|
    |Glyphgroupfield|Glyphitemprotected|Fieldprotected|
    |Glyphgroupfield|Glyphitemprivate|Fieldprivate|
    |Glyphgroupfield|Glyphitemshortcut|Fieldshortcut|
    |Glyphgroupinterface|Glyphitempublic|Interfacepublic|
    |Glyphgroupinterface|Glyphiteminternal|Interfakeiternal|
    |Glyphgroupinterface|Glyphitemfriend|Interfakeiternal|
    |Glyphgroupinterface|Glyphitemprotected|Interfaceprotected|
    |Glyphgroupinterface|Glyphitemprivate|Interfaceprivate|
    |Glyphgroupinterface|Glyphitemshortcut|Interfakeshortcut|
    |Glyphgroupmacro|Glyphitempublic|Makropublic|
    |Glyphgroupmacro|Glyphiteminternal|Makrointernal|
    |Glyphgroupmacro|Glyphitemfriend|Makrointernal|
    |Glyphgroupmacro|Glyphitemprotected|Makroprotected|
    |Glyphgroupmacro|Glyphitemprivate|Makroprivate|
    |Glyphgroupmacro|Glyphitemshortcut|Makroshortcut|
    |Glyphgroupmap|Glyphitempublic|Mappublic|
    |Glyphgroupmap|Glyphiteminternal|Mapinternal|
    |Glyphgroupmap|Glyphitemfriend|Mapinternal|
    |Glyphgroupmap|Glyphitemprotected|Mapprotected|
    |Glyphgroupmap|Glyphitemprivate|Mapprivate|
    |Glyphgroupmap|Glyphitemshortcut|Mapshortcut|
    |Glyphgroupmapitem|Glyphitempublic|Mapitempublic|
    |Glyphgroupmapitem|Glyphiteminternal|Mapiteminternal|
    |Glyphgroupmapitem|Glyphitemfriend|Mapiteminternal|
    |Glyphgroupmapitem|Glyphitemprotected|Mapitemprotected|
    |Glyphgroupmapitem|Glyphitemprivate|Mapitemprivate|
    |Glyphgroupmapitem|Glyphitemshortcut|Mapitemshortcut|
    |Glyphgroupmethod|Glyphitempublic|Methodpublic|
    |Glyphgroupmethod|Glyphiteminternal|Methodinternal|
    |Glyphgroupmethod|Glyphitemfriend|Methodinternal|
    |Glyphgroupmethod|Glyphitemprotected|MethodProtected|
    |Glyphgroupmethod|Glyphitemprivate|Methodprivate|
    |Glyphgroupmethod|Glyphitemshortcut|Methodshortcut|
    |Glyphgroupoverload|Glyphitempublic|Methodpublic|
    |Glyphgroupoverload|Glyphiteminternal|Methodinternal|
    |Glyphgroupoverload|Glyphitemfriend|Methodinternal|
    |Glyphgroupoverload|Glyphitemprotected|MethodProtected|
    |Glyphgroupoverload|Glyphitemprivate|Methodprivate|
    |Glyphgroupoverload|Glyphitemshortcut|Methodshortcut|
    |Glyphgroupmodule|Glyphitempublic|Modulepublic|
    |Glyphgroupmodule|Glyphiteminternal|Moduleinternal|
    |Glyphgroupmodule|Glyphitemfriend|Moduleinternal|
    |Glyphgroupmodule|Glyphitemprotected|Moduleprotected|
    |Glyphgroupmodule|Glyphitemprivate|Moduleprivate|
    |Glyphgroupmodule|Glyphitemshortcut|Moduleshortcut|
    |Glyphgroupnamespace|Glyphitempublic|Namespacepublic|
    |Glyphgroupnamespace|Glyphiteminternal|Namespacinternal|
    |Glyphgroupnamespace|Glyphitemfriend|Namespacinternal|
    |Glyphgroupnamespace|Glyphitemprotected|Namespaceprotected|
    |Glyphgroupnamespace|Glyphitemprivate|Namespaceprivate|
    |Glyphgroupnamespace|Glyphitemshortcut|Namespaceshortcut|
    |Glyphgroupoperator|Glyphitempublic|Operatorpublic|
    |Glyphgroupoperator|Glyphiteminternal|Operatorinternal|
    |Glyphgroupoperator|Glyphitemfriend|Operatorinternal|
    |Glyphgroupoperator|Glyphitemprotected|Operatorprotected|
    |Glyphgroupoperator|Glyphitemprivate|Operatorprivate|
    |Glyphgroupoperator|Glyphitemshortcut|Operatorshortcut|
    |Glyphgroupproperty|Glyphitempublic|Propertypublic|
    |Glyphgroupproperty|Glyphiteminternal|Propertyinternal|
    |Glyphgroupproperty|Glyphitemfriend|Propertyinternal|
    |Glyphgroupproperty|Glyphitemprotected|Propertyprotected|
    |Glyphgroupproperty|Glyphitemprivate|Propertyprivate|
    |Glyphgroupproperty|Glyphitemshortcut|Propertyshortcut|
    |Glyphgroupstruct|Glyphitempublic|Structurepublic|
    |Glyphgroupstruct|Glyphiteminternal|Structureinternal|
    |Glyphgroupstruct|Glyphitemfriend|Structureinternal|
    |Glyphgroupstruct|Glyphitemprotected|Structureprotected|
    |Glyphgroupstruct|Glyphitemprivate|Structureprivate|
    |Glyphgroupstruct|Glyphitemshortcut|Structureshortcut|
    |Glyphgrouptemplate|Glyphitempublic|Templatepublic|
    |Glyphgrouptemplate|Glyphiteminternal|Templateingeternal|
    |Glyphgrouptemplate|Glyphitemfriend|Templateingeternal|
    |Glyphgrouptemplate|Glyphitemprotected|Templateprotected|
    |Glyphgrouptemplate|Glyphitemprivate|Templateprivate|
    |Glyphgrouptemplate|Glyphitemshortcut|Templateshortcut|
    |Glyphgrouptypedef|Glyphitempublic|TypeDefinitionPublic|
    |Glyphgrouptypedef|Glyphiteminternal|TypeDefinitionInternal|
    |Glyphgrouptypedef|Glyphitemfriend|TypeDefinitionInternal|
    |Glyphgrouptypedef|Glyphitemprotected|TypeDefinitionProtected|
    |Glyphgrouptypedef|Glyphitemprivate|TypeDefinitionPrivate|
    |Glyphgrouptypedef|Glyphitemshortcut|TypeDefinitionShortcut|
    |Glyphgrouptype|Glyphitempublic|TypePublic|
    |Glyphgrouptype|Glyphiteminternal|Typeingabe|
    |Glyphgrouptype|Glyphitemfriend|Typeingabe|
    |Glyphgrouptype|Glyphitemprotected|Typeprotected|
    |Glyphgrouptype|Glyphitemprivate|Typeprivate|
    |Glyphgrouptype|Glyphitemshortcut|Typeshortcut|
    |Glyphgroupunion|Glyphitempublic|Unionpublic|
    |Glyphgroupunion|Glyphiteminternal|Unions intern|
    |Glyphgroupunion|Glyphitemfriend|Unions intern|
    |Glyphgroupunion|Glyphitemprotected|Unionprotected|
    |Glyphgroupunion|Glyphitemprivate|Unionprivate|
    |Glyphgroupunion|Glyphitemshortcut|Unionshortcut|
    |Glyphgroupvariable|Glyphitempublic|Fieldpublic|
    |Glyphgroupvariable|Glyphiteminternal|Fieldinternal|
    |Glyphgroupvariable|Glyphitemfriend|Fieldinternal|
    |Glyphgroupvariable|Glyphitemprotected|Fieldprotected|
    |Glyphgroupvariable|Glyphitemprivate|Fieldprivate|
    |Glyphgroupvariable|Glyphitemshortcut|Fieldshortcut|
    |Glyphgroupvaluetype|Glyphitempublic|Valuetypeer Public|
    |Glyphgroupvaluetype|Glyphiteminternal|Valuetypeingeternal|
    |Glyphgroupvaluetype|Glyphitemfriend|Valuetypeingeternal|
    |Glyphgroupvaluetype|Glyphitemprotected|Valuetypeer Protected|
    |Glyphgroupvaluetype|Glyphitemprivate|Valuetypeer private|
    |Glyphgroupvaluetype|Glyphitemshortcut|Valuetypeshortcut|
    |Glyphgroupintrinsisch|Glyphitempublic|Objectpublic|
    |Glyphgroupintrinsisch|Glyphiteminternal|Objectinternal|
    |Glyphgroupintrinsisch|Glyphitemfriend|Objectinternal|
    |Glyphgroupintrinsisch|Glyphitemprotected|Objectprotected|
    |Glyphgroupintrinsisch|Glyphitemprivate|Objectprivate|
    |Glyphgroupintrinsisch|Glyphitemshortcut|Objectshortcut|
    |Glyphgroupjsharpmethod|Glyphitempublic|Methodpublic|
    |Glyphgroupjsharpmethod|Glyphiteminternal|Methodinternal|
    |Glyphgroupjsharpmethod|Glyphitemfriend|Methodinternal|
    |Glyphgroupjsharpmethod|Glyphitemprotected|MethodProtected|
    |Glyphgroupjsharpmethod|Glyphitemprivate|Methodprivate|
    |Glyphgroupjsharpmethod|Glyphitemshortcut|Methodshortcut|
    |Glyphgroupjsharpfield|Glyphitempublic|Fieldpublic|
    |Glyphgroupjsharpfield|Glyphiteminternal|Fieldinternal|
    |Glyphgroupjsharpfield|Glyphitemfriend|Fieldinternal|
    |Glyphgroupjsharpfield|Glyphitemprotected|Fieldprotected|
    |Glyphgroupjsharpfield|Glyphitemprivate|Fieldprivate|
    |Glyphgroupjsharpfield|Glyphitemshortcut|Fieldshortcut|
    |Glyphgroupjsharpclass|Glyphitempublic|Classpublic|
    |Glyphgroupjsharpclass|Glyphiteminternal|Classinternal|
    |Glyphgroupjsharpclass|Glyphitemfriend|Classinternal|
    |Glyphgroupjsharpclass|Glyphitemprotected|Classprotehiert|
    |Glyphgroupjsharpclass|Glyphitemprivate|Classprivate|
    |Glyphgroupjsharpclass|Glyphitemshortcut|Classshortcut|
    |Glyphgroupjsharpnamespace|Glyphitempublic|Namespacepublic|
    |Glyphgroupjsharpnamespace|Glyphiteminternal|Namespacinternal|
    |Glyphgroupjsharpnamespace|Glyphitemfriend|Namespacinternal|
    |Glyphgroupjsharpnamespace|Glyphitemprotected|Namespaceprotected|
    |Glyphgroupjsharpnamespace|Glyphitemprivate|Namespaceprivate|
    |Glyphgroupjsharpnamespace|Glyphitemshortcut|Namespaceshortcut|
    |Glyphgroupjsharpinterface|Glyphitempublic|Interfacepublic|
    |Glyphgroupjsharpinterface|Glyphiteminternal|Interfakeiternal|
    |Glyphgroupjsharpinterface|Glyphitemfriend|Interfakeiternal|
    |Glyphgroupjsharpinterface|Glyphitemprotected|Interfaceprotected|
    |Glyphgroupjsharpinterface|Glyphitemprivate|Interfaceprivate|
    |Glyphgroupjsharpinterface|Glyphitemshortcut|Interfakeshortcut|
    |Glyphgrouperror||StatusError|
    |Glyphbscfile||Classfile|
    |Glyphassembly||Verweis|
    |Glyphlibrary||Bibliothek|
    |Glyphvbproject||Vbprojectnode|
    |Glyphcoolproject||Csprojectnode|
    |Glyphcppproject||Cppprojectnode|
    |Glyphdialogid||Dialog|
    |Glyphopenfolder||Foldergeöffnet|
    |Glyphclosedfolder||Folderclosed|
    |Glypharrow||GoToNext|
    |Glyphcsharpfile||CSFile Ode|
    |Glyphcsharp-Erweiterung||Codeausschnitt|
    |Glyphkeyword||Intellisenabschlüsselwort|
    |Glyphinformation||Statusinformation|
    |Glyphreference||Classmethodreferenzierung|
    |Glyphrecursion||Rekursion|
    |Glyphxmlitem||Tag|
    |Glyphjsharpproject||DocumentCollection|
    |Glyphjsharpdocument||Dokument|
    |Glyphforwardtype||GoToNext|
    |Glyphcallersgraph||Callto|
    |Glyphcallgraph||Callfrom|
    |Glyphwarning||StatusWarning|
    |Glyphmaybereferenzierung||Fragezeichen|
    |Glyphmaybecaller||Callto|
    |Glyphmaybecall||Callfrom|
    |Glyphextensionmethod||Extensionmethod|
    |Glyphextensionmethodinternal||Extensionmethod|
    |Glyphextensionmethodfriend||Extensionmethod|
    |Glyphextensionmethodprotected||Extensionmethod|
    |Glyphextensionmethodprivate||Extensionmethod|
    |Glyphextensionmethodshortcut||Extensionmethod|
    |Glyphxmlattribute||XmlAttribute|
    |Glyphxmlchild||XmlElement|
    |Glyphxmlnachfolger||Xmlnachfolger|
    |Glyphxmlnamespace||XmlNamespace|
    |Glyphxmlattributequestion||Xmlattributelowconfidence|
    |Glyphxmlattributecheck||Xmlattributehighconfidence|
    |Glyphxmlchildquestion||Xmlelementlowconfidence|
    |Glyphxmlchildcheck||XmlElementHighConfidence|
    |Glyphxmldescendantquestion||Xmldescendantlowconfidence|
    |Glyphxmldescendantcheck||Xmldescendanthighconfidence|
    |Glyphcompletionwarning||Intellisenabwarning|
