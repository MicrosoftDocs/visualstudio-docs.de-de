---
title: Adressieren von dpi-Issues2 | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Probleme beim Programmieren für hochauflösende Bildschirme, wie z. b. zentrales hochskalieren von Inhalten, Layoutproblemen und Verwenden von dpi-APIs.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 455f144a95a41ae482c1f240e1d2f87b888763a5
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598457"
---
# <a name="address-dpi-issues"></a>Behandeln von dpi-Problemen
Eine zunehmende Anzahl von Geräten wird mit "hochauflösende" Bildschirmen ausgeliefert. Diese Bildschirme verfügen in der Regel über 200 Pixel pro Zoll (PPI). Beim Arbeiten mit einer Anwendung auf diesen Computern müssen Inhalte zentral hochskaliert werden, um den Anforderungen der Anzeige des Inhalts in der normalen Anzeige Entfernung für das Gerät gerecht zu werden. Ab 2014 ist das primäre Ziel für die Anzeige mit hoher Dichte Mobile Computergeräte (Tablets, Clamshell-Laptops und Telefone).

Windows 8.1 und höher enthält mehrere Features, mit denen diese Computer mit anzeigen und Umgebungen arbeiten können, in denen der Computer gleichzeitig an die Anzeige mit hoher Dichte und Standard Dichte angefügt ist.

- Mithilfe von Windows können Sie Inhalte auf dem Gerät mithilfe der Einstellung "Text und andere Elemente vergrößern oder verkleinern" (verfügbar seit Windows XP) skalieren.

- Windows 8.1 und höher skalieren Inhalte für die meisten Anwendungen automatisch so, dass Sie konsistent sind, wenn Sie zwischen den Anzeige unterschiedlicher Pixel dichten verschoben werden. Wenn die primäre Anzeige hohe Dichte aufweist (200%-Skalierung) und die sekundäre Anzeige Standard Dichte (100%) ist, skaliert Windows automatisch den Inhalt des Anwendungsfensters auf der sekundären Anzeige (1 Pixel wird für alle 4 Pixel angezeigt, die von der Anwendung gerendert werden).

- Windows wird standardmäßig auf die richtige Skalierung für die Pixeldichte und die Anzeige der Entfernung für die Anzeige (Windows 7 und höher, OEM-konfigurierbar) eingestellt.

- Der Inhalt von Windows kann auf neuen Geräten mit einer Größe von 280 ppi (ab Windows 8.1 S14) automatisch auf bis zu 250% skaliert werden.

  Mit Windows können Sie die Benutzeroberfläche zentral hochskalieren, um eine größere Anzahl von Pixeln zu nutzen. Eine Anwendung wird in diesem System durch Deklarieren von "System-dpi-fähig" unterstützt. Anwendungen, die dies nicht tun, werden vom System zentral hochskaliert. Dies kann zu einer "Fuzzy"-Benutzer Darstellung führen, bei der die gesamte Anwendung gleichmäßig Pixel gestreckt ist. Beispiel:

  ![DPI-Probleme unscharf](../extensibility/media/dpi-issues-fuzzy.png "DPI-Probleme unscharf")

  Visual Studio unterstützt die DPI-Skalierung und ist daher nicht "virtualisiert".

  Windows (und Visual Studio) nutzen mehrere UI-Technologien, die unterschiedliche Methoden zum Umgang mit Skalierungsfaktoren aufweisen, die vom System festgelegt werden. Beispiel:

- WPF misst Steuerelemente auf geräteunabhängige Weise (Einheiten, nicht Pixel). Die WPF-Benutzeroberfläche wird automatisch für den aktuellen dpi-Abschnitt skaliert

- Alle Textgrößen, unabhängig vom Benutzeroberflächen-Framework, werden in Punkten ausgedrückt und vom System als dpi-unabhängig behandelt. Der Text in Win32, WinForms und WPF wird bereits ordnungsgemäß hochskaliert, wenn er auf das Anzeigegerät gezeichnet wird.

- Win32/WinForms-Dialogfelder und Fenster verfügen über Möglichkeiten zum Aktivieren von Layout, das die Größe der Größe mit Text (z. b. durch Raster-, Fluss-und tabellenlayoutpanels) ändert. Diese ermöglichen die Vermeidung von hart codierten Pixel Standorten, die nicht skaliert werden, wenn die Schrift Grade vergrößert werden.

- Vom System bereitgestellte Symbole oder Ressourcen, die auf Systemmetriken basieren (z. b. SM_CXICON und SM_CXSMICON), werden bereits zentral hochskaliert.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Ältere Win32-(GDI-, GDI+) und auf WinForms basierende Benutzeroberfläche
Während WPF bereits hohe dpi-Werten unterstützt, wurde ein Großteil des Win32/GDI-basierten Codes ursprünglich nicht mit dpi-Informationen geschrieben. Windows hat APIs für die DPI-Skalierung bereitgestellt. Fehlerbehebungen für Win32-Probleme sollten diese konsistent über das gesamte Produkt hinweg verwenden. Visual Studio hat eine Hilfsklassen Bibliothek bereitgestellt, um das Duplizieren von Funktionen und die Gewährleistung der Konsistenz im gesamten Produkt zu vermeiden.

## <a name="high-resolution-images"></a>Hochauflösende Bilder
In diesem Abschnitt geht es hauptsächlich an Entwickler, die Visual Studio 2013 erweitern. Verwenden Sie für Visual Studio 2015 den Image Service, der in Visual Studio integriert ist. Möglicherweise stellen Sie auch fest, dass Sie viele Versionen von Visual Studio unterstützen müssen, und daher ist die Verwendung des Image-diensdienstanbieter in 2015 keine Option, da er in früheren Versionen nicht vorhanden ist. Dieser Abschnitt ist auch für Sie vorgesehen.

## <a name="scaling-up-images-that-are-too-small"></a>Zentrales hochskalieren von Images, die zu klein sind
Images, die zu klein sind, können mithilfe einiger gängiger Methoden auf GDI und WPF hochskaliert und gerendert werden. Verwaltete dpi-Hilfsklassen sind für interne und externe Visual Studio-Integratoren verfügbar, um das Skalieren von Symbolen, Bitmaps, imagestrips und imagelists zu beheben. Win32-basierte Native c/C + +-Hilfsprogramme sind zum Skalieren von HICON, HBITMAP, HIMAGELIST und vsui:: gdiplusimage verfügbar. Das Skalieren einer Bitmap erfordert in der Regel nur eine einzeilige Änderung, wenn ein Verweis auf die Hilfsbibliothek eingeschlossen wird. Beispiel:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Das Skalieren einer ImageList hängt davon ab, ob die ImageList zur Ladezeit vollständig ist oder zur Laufzeit angefügt wird. Wenn der Vorgang zur Ladezeit vollständig ist, können `LogicalToDeviceUnits()` Sie mit der ImageList wie eine Bitmap aufzurufen. Wenn der Code vor dem Verfassen der ImageList eine einzelne Bitmap laden muss, stellen Sie sicher, dass die Bildgröße der ImageList skaliert wird:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

In nativem Code können die Dimensionen beim Erstellen der ImageList wie folgt skaliert werden:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Funktionen in der Bibliothek ermöglichen die Angabe des Algorithmus zum Ändern der Größe. Stellen Sie beim Skalieren von Bildern, die in imagelists platziert werden sollen, sicher, dass Sie die Hintergrundfarbe angeben, die für Transparenz verwendet wird, oder verwenden Sie die Near estneighbor-Skalierung (was zu einer Verzerrung bei 125% und 150%) führt

Weitere Informationen finden Sie <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> in der Dokumentation zu MSDN.

In der folgenden Tabelle werden Beispiele für die Skalierung von Bildern mit den entsprechenden dpi-Skalierungsfaktoren gezeigt. Die in orange dargestellten Bilder bezeichnen unsere bewährte Vorgehensweise Visual Studio 2013 (100%-200% dpi-Skalierung):

![DPI-Probleme beim Skalieren](../extensibility/media/dpi-issues-scaling.png "DPI-Probleme beim Skalieren")

## <a name="layout-issues"></a>Layoutprobleme
Allgemeine Layoutprobleme können hauptsächlich vermieden werden, indem Punkte in der Benutzeroberfläche skaliert und relativ zueinander, nicht mithilfe absoluter Speicherorte (insbesondere in Pixel Einheiten), gespeichert werden. Beispiel:

- Layout-/Textpositionen müssen angepasst werden, um hochskalierte Images zu berücksichtigen.

- Für Spalten in Rastern müssen Breite für den horizontal skalierten Text angepasst werden.

- Hart codierte Größen oder Leerraum zwischen Elementen muss ebenfalls zentral hochskaliert werden. Größen, die nur auf Text Dimensionen basieren, sind in der Regel in Ordnung, da Schriftarten automatisch zentral hochskaliert werden.

  Hilfsfunktionen stehen in der- <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> Klasse zur Verfügung, um die Skalierung auf der X-und Y-Achse zuzulassen:

- Logicaldedeviceunizx/logicaldedeviceunity (Funktionen lassen die Skalierung auf der X/Y-Achse zu)

- int Space = dpihelper. logicaldedeviceunizx (10);

- int height = vsui::D pihelper:: logicaldedeviceunizy (5);

  Es sind logicaldedeviceunits-über Ladungen vorhanden, um das Skalieren von Objekten wie z. b. Rect, Point und Size zuzulassen.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Verwenden der dpihelper-Bibliothek/-Klasse zum Skalieren von Bildern und Layout
Die Visual Studio-dpi-Hilfsbibliothek ist in nativen und verwalteten Formularen verfügbar und kann von anderen Anwendungen außerhalb der Visual Studio-Shell verwendet werden.

Um die Bibliothek zu verwenden, navigieren Sie zu den [Visual Studio VSSDK-Erweiterbarkeits Beispielen](https://github.com/Microsoft/VSSDK-Extensibility-Samples) , und Klonen Sie das High-DPI_Images_Icons Beispiel.

Fügen Sie in den Quelldateien " *vsuidpihelper. h* " ein, und nennen Sie die statischen Funktionen der- `VsUI::DpiHelper` Klasse:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Verwenden Sie die Hilfsfunktionen nicht in statischen Variablen auf Modulebene oder auf Klassenebene. Die Bibliothek verwendet auch Statics für die Thread Synchronisierung, und möglicherweise treten Probleme mit der Reihenfolge Initialisierung auf. Konvertieren Sie diese Statics entweder in nicht statische Element Variablen, oder schließen Sie Sie in eine Funktion ein (damit Sie beim ersten Zugriff erstellt werden).

So greifen Sie über verwalteten Code, der in der Visual Studio-Umgebung ausgeführt wird, auf die dpi-Hilfsfunktionen zu:

- Das verbrauchende Projekt muss auf die neueste Version von shellmpf verweisen. Beispiel:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Stellen Sie sicher, dass das Projekt über Verweise auf **System. Windows. Forms**, **PresentationCore** und **presentationui** verfügt.

- Verwenden Sie im Code den **Microsoft. VisualStudio. PlatformUI** -Namespace, und nennen Sie statische Funktionen der dpihelper-Klasse. Bei unterstützten Typen (Punkten, Größen, Rechtecke usw.) werden Erweiterungsfunktionen bereitgestellt, die neue skalierte Objekte zurückgeben. Beispiel:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Umgang mit WPF-Bild-Fuzziness in der zoombaren Benutzeroberfläche
In WPF wird die Größe von Bitmaps automatisch von WPF für die aktuelle dpi-Zoomstufe mithilfe eines hochwertigen bikubischen Algorithmus (Standard) angepasst, der gut für Bilder oder große Screenshots geeignet ist, aber für Menü Element Symbole ungeeignet ist, da er wahrgenommene Fuzziness einführt.

Empfehlungen:

- Für Logo Bild-und Banner-Grafiken kann der Standardmodus für die <xref:System.Windows.Media.BitmapScalingMode> Größe der Größe verwendet werden.

- Für Menü Elemente und iconographie-Bilder <xref:System.Windows.Media.BitmapScalingMode> sollte verwendet werden, wenn keine weiteren zerstellungselemente bewirkt werden, dass Fuzziness (bei 200% und 300%) vermieden wird.

- Bei großen Zoomstufen und nicht Vielfachen von 100% (z. b. 250% oder 350%), wird das Skalieren von Ikonographie-Bildern mit bikubischen Elementen in einer fuzzyweise durch die Benutzeroberfläche Ein besseres Ergebnis erhalten Sie, wenn Sie das Image zuerst mit "NearestNeighbor" auf das größte Vielfache von 100% skalieren (z. b. 200% oder 300%). und von dort aus Skalieren mit Bikubisch. Weitere Informationen finden Sie unter Sonderfall: vorab Skalieren von WPF-Images für große dpi-Werte.

  Die dpihelper-Klasse im Microsoft. VisualStudio. PlatformUI-Namespace stellt einen Member bereit <xref:System.Windows.Media.BitmapScalingMode> , der für die Bindung verwendet werden kann. Dies ermöglicht es der Visual Studio-Shell, den Skalierungs Modus der Bitmap über das Produkt hinweg einheitlich zu steuern, je nach dem Faktor für die DPI-Skalierung.

  Um es in XAML zu verwenden, fügen Sie Folgendes hinzu:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Diese Eigenschaft wird von der Visual Studio-Shell bereits in Windows und Dialogfeldern der obersten Ebene festgelegt. Die auf WPF basierende Benutzeroberfläche, die in Visual Studio ausgeführt wird, erbt diese bereits. Wenn die Einstellung nicht an Ihre speziellen Elemente der Benutzeroberfläche weitergegeben wird, kann Sie für das Stamm Element der XAML/WPF-Benutzeroberfläche festgelegt werden. Zu den stellen, an denen dies geschieht, zählen Popups, Elemente mit Win32-übergeordneten Elementen und Designer Fenster, die Prozess bedingt ablaufen (z. b. Blend).

Einige Benutzeroberflächen können unabhängig von der System Satz-dpi-Zoomstufe skaliert werden, z. b. dem Visual Studio-Text-Editor und WPF-basierten Designern (WPF-Desktop und Windows Store). In diesen Fällen sollte dpihelper. BitmapScalingMode nicht verwendet werden. Um dieses Problem im Editor zu beheben, hat das IDE-Team eine benutzerdefinierte Eigenschaft mit dem Namen RenderOptions. BitmapScalingMode erstellt. Legen Sie diesen Eigenschafts Wert abhängig von der kombinierten Zoom Stufe des Systems und ihrer Benutzeroberfläche auf HighQuality oder NearestNeighbor fest.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Sonderfall: vorab Skalieren von WPF-Images für große dpi-Werte
Bei sehr großen Zoomstufen, bei denen es sich nicht um ein Vielfaches von 100% handelt (z. b. 250%, 350%, usw.), wird das Skalieren von Ikonographie-Bildern mit bikubischen Ergebnissen in der Benutzeroberfläche für fuzzyüber Der Eindruck dieser Bilder neben dem scharfen Text ähnelt fast der optischen Illusion. Die Bilder erscheinen in Bezug auf den Text eher in der Nähe des Auges. Das Skalierungs Ergebnis mit dieser vergrößerten Größe kann verbessert werden, indem zuerst das Image mit "NearestNeighbor" auf das größte Vielfache von 100% (z. b. 200% oder 300%) skaliert wird. und Skalierung mit bikubischem bis zum Rest (ein zusätzliches 50%).

Im folgenden finden Sie ein Beispiel für die Unterschiede in den Ergebnissen, bei denen das erste Bild mit dem verbesserten Algorithmus für die doppelte Skalierung 100%->200%->250% und der zweite mit der bikubischen 100%->250% skaliert wird.

![Beispiel für doppelte Skalierung bei dpi](../extensibility/media/dpi-issues-double-scaling-example.png "Beispiel für doppelte Skalierung bei dpi")

Damit die Benutzeroberfläche diese doppelte Skalierung verwenden kann, muss das XAML-Markup zum Anzeigen der einzelnen Bildelemente geändert werden. In den folgenden Beispielen wird gezeigt, wie die doppelte Skalierung in WPF in Visual Studio mithilfe der dpihelper-Bibliothek und Shell. 12/14 verwendet wird.

Schritt 1: vorab Skalieren des Images auf 200%, 300% usw. mit "NearestNeighbor".

Vorab Skalieren des Bilds entweder mithilfe eines Konverters, der auf eine Bindung angewendet wurde, oder mit einer XAML-Markup Erweiterung. Beispiel:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Wenn das Bild ebenfalls mit einem Design versehen werden muss (die meisten, wenn nicht alle), kann das Markup einen anderen Konverter verwenden, der zuerst die Darstellung des Bilds und dann die vorab Skalierung ausführt. <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> Abhängig von der gewünschten Konvertierungs Ausgabe kann das Markup entweder oder verwenden.

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

Schritt 2: Stellen Sie sicher, dass die endgültige Größe für den aktuellen dpi-Wert korrekt ist.

Da WPF die Benutzeroberfläche für den aktuellen dpi mithilfe der BitmapScalingMode-Eigenschaft skaliert, die für das UIElement festgelegt ist, wird ein Image-Steuerelement, das ein Bild eines vordefinierten Bilds als Quelle verwendet, zwei oder dreimal größer als das entsprechende aussehen. Im folgenden finden Sie eine Reihe von Möglichkeiten, diesen Effekt zu begegnen:

- Wenn Sie die Dimension des ursprünglichen Images bei 100% kennen, können Sie die genaue Größe des Image-Steuer Elements angeben. Diese Größen entsprechen der Größe der Benutzeroberfläche, bevor die Skalierung angewendet wird.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Wenn die Größe des ursprünglichen Bilds nicht bekannt ist, kann eine LayoutTransform zum horizontalen Herunterskalieren des endgültigen Bildobjekts verwendet werden. Beispiel:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Aktivieren der hdpi-Unterstützung für den WebOC
Standardmäßig aktivieren WebOC-Steuerelemente (z. b. das WebBrowser-Steuerelement in WPF oder die IWebBrowser2-Schnittstelle) keine hdpi-Erkennung und-Unterstützung. Das Ergebnis ist ein eingebettetes Steuerelement, bei dem der Inhalt angezeigt wird, der in einer hochauflösenden Anzeige zu klein ist. Im folgenden wird beschrieben, wie die Unterstützung für hohe dpi-Daten in einer bestimmten WebOC-Instanz aktiviert wird.

Implementieren Sie die IDocHostUIHandler-Schnittstelle (Weitere Informationen finden Sie im MSDN-Artikel zu [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

Optional können Sie die icustomdoc-Schnittstelle implementieren (Weitere Informationen finden Sie im MSDN-Artikel zu [icustomdoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Ordnen Sie die Klasse, die IDocHostUIHandler implementiert, dem Dokument von WebOC zu. Wenn Sie die oben aufgeführte icustomdoc-Schnittstelle implementiert haben, wandeln Sie Sie, sobald die Dokument Eigenschaft von WebOC gültig ist, in ein icustomdoc-Objekt um, und rufen Sie die setuihandler-Methode auf, und übergeben Sie dabei die Klasse, die IDocHostUIHandler implementiert.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Wenn Sie die icustomdoc-Schnittstelle nicht implementiert haben, müssen Sie, sobald die Dokument Eigenschaft von WebOC gültig ist, Sie in ein IOleObject umwandeln und die-Methode aufzurufen `SetClientSite` , indem Sie die Klasse übergeben, die IDocHostUIHandler implementiert. Legen Sie das DOCHOSTUIFLAG_DPI_AWARE-Flag für dochostuiinfo fest, das an den-Methoden Befehl weitergegeben wird `GetHostInfo` :

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

Dies sollte alles sein, was Sie benötigen, um das WebOC-Steuerelement für die Unterstützung von HPDI zu erhalten.

## <a name="tips"></a>Tipps

1. Wenn die Document-Eigenschaft des WebOC-Steuer Elements geändert wird, müssen Sie das Dokument möglicherweise der IDocHostUIHandler-Klasse zuordnen.

2. Wenn die oben genannte Funktion nicht funktioniert, liegt ein bekanntes Problem mit dem WebOC vor, das die Änderung am dpi-Flag nicht aufnimmt. Der zuverlässigste Weg, dies zu beheben, besteht darin, den optischen Zoom des WebOC zu wechseln, d. h. zwei Aufrufe mit zwei verschiedenen Werten für den Zoom Prozentsatz. Wenn diese Problem Umgehung erforderlich ist, kann es auch erforderlich sein, Sie bei jedem Navigate-Befehl auszuführen.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
