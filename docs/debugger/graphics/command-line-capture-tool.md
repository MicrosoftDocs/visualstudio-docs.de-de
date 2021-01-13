---
title: Befehlszeilen-Erfassungstool | Microsoft-Dokumentation
description: Erfahren Sie mehr über DXCap.exe, ein Befehlszeilentool für die Erfassung und Wiedergabe von Grafikdiagnosen, das Direct3D 10 bis Direct3D 12 auf allen Funktionsebenen unterstützt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3618c1d6e929d40108abd5fd0b0cc3a3361964bf
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727876"
---
# <a name="command-line-capture-tool"></a>Befehlszeilen-Erfassungs-Tool
DXCap.exe ist ein Befehlszeilenprogramm für die Aufzeichnung und Wiedergabe der Grafikdiagnose. Es unterstützt Direct3D 10 bis Direct3D 12 auf allen Funktionsebenen.

## <a name="syntax"></a>Syntax

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>Parameter
 `-file` `filename` Unter Aufnahmemodus (`-c`) gibt `filename` den Namen der Grafikprotokolldatei an, in der die Grafikinformationen aufgezeichnet werden. Wenn `filename` nicht angegeben ist, werden Grafikinformationen standardmäßig in der Datei `<appname>-<date>-<time>.vsglog` aufgezeichnet.

 Unter Gültigkeitsprüfung (-V)-Modus `filename` wird der Namen der zu prüfenden Grafikprotokolldatei angezeigt. Wenn `filename` nicht angegeben ist, wird das zuletzt überprüfte Grafikprotokoll erneut verwendet.

 `-frame` `frames` Unter dem Erfassungsmodus gibt `frames` die Frames an, die Sie erfassen möchten. Der erste Frame ist 1. Sie können mehrere Frames mithilfe von Kommas und Bereichen angeben. Wenn `frames` beispielsweise `2, 5, 7-9, 15` ist, werden die Frames `2`, `5`, `7`, `8`, `9` und `15` aufgezeichnet.

> [!TIP]
> Verwenden Sie `-frame` `manual`, um anzugeben, dass Bilder manuell durch Drücken der DRUCK-TASTE erfasst werden. Frames können erfasst werden, wenn die Anwendung gestartet wird; Um das Erfassen von Frames zu beenden, kehren Sie zur Befehlszeilen-Schnittstelle zurück und drücken Sie die EINGABETASTE.

 `-period` `periods` Im Erfassungsmodus legt `periods` die Bereiche für die Zeit in Sekunden fest, in denen Sie Frames erfassen möchten. Sie können mehrere Zeiträume mithilfe von Kommas und Bereichen angeben. Wenn `periods` beispielsweise `2.1-5, 7.0-9.3` ist, werden Frames erfasst, die zwischen `2.1` und `5` Sekunden sowie zwischen `7` und `9.3` Sekunden gerendert werden.

 `-c` `app` [`args...`] Aufzeichnungsmodus. Unter dem Aufnahmemodus gibt `app` den Namen der Anwendung an, aus der Sie Grafikinformationen aufzeichnen möchten; `args...` gibt zusätzliche Befehlszeilenparameter für diese Anwendung an.

 `-p` [`filename`] Wiedergabemodus (`-p`). Unter dem Wiedergabemodus gibt `filename` den Namen der Grafikprotokolldatei an, die wiedergegeben werden soll. Wenn `filename` nicht angegeben ist, wird das zuletzt wiedergegebene Grafikprotokoll erneut verwendet.

 `-debug` Im Wiedergabemodus gibt `-debug` an, dass die Wiedergabe mit aktivierter Direct3D-Debugebene erfolgen sollte.

 `-warp` Im Wiedergabemodus gibt `-warp` an, dass die Wiedergabe mit dem WARP-Softwarerenderer durchgeführt werden sollte.

 `-hw` Im Wiedergabemodus gibt `-hw` an, dass die Wiedergabe mit GPU-Hardware ausgeführt werden sollte.

 `-config` Im Wiedergabemodus zeigt `-config` alle Informationen zu dem Computer an, der zum Erfassen der Grafikprotokolldatei verwendet wurde.

 `-rawmode` Im Wiedergabemodus gibt `-rawmode` an, dass die Wiedergabe ohne Änderung der aufgezeichneten Ereignisse ausgeführt werden sollte. Unter normalen Bedingungen werden unter dem Wiedergabemodus möglicherweise geringfügige Änderungen an der Wiedergabe vorgenommen, um das Debuggen zu vereinfachen und die Wiedergabe zu beschleunigen. z. B. kann eine Swap-Ketten-Ausgabe anstelle der Ausführung von Swap-Kette Befehlen simuliert werden. Diese Wiedergabe ist in der Regel kein Problem, möglicherweise muss die Wiedergabe jedoch dem aufgezeichneten Ereignis besser entsprechen. Beispielsweise können Sie diese Option verwenden, um das Vollbild-Renderingverhalten für eine App wiederherzustellen, die während der Ausführung im Vollbildmodus aufgezeichnet wurde.

 `-toXML``xml_filename` Unter dem Wiedergabemodus gibt `xml_filename` den Namen der Datei an, in die eine XML-Darstellung der Wiedergabe geschrieben wird. Wenn `xml_filename` nicht angegeben ist, wird die XML-Darstellung in eine Datei mit demselben Namen der widergegebenen Datei geschrieben, erhält aber eine `.xml` Erweiterung.

 `-v` Validierungsmodus. Unter dem Validierungsmodus erfasste Frames werden sowohl auf Hardware als auch auf WARP wiedergegeben, und ihre Ergebnisse werden mithilfe einer Bildvergleichsfunktion verglichen. Dieses Feature können Sie verwenden, um Treiberprobleme schnell zu identifizieren, die sich auf das Rendering auswirken.

 `-examine` `events` Im Validierungsmodus gibt `events` die Grafikereignisse an, deren sofortige Ergebnisse verglichen werden. Beispielsweise beschränkt `-examine present,draw,copy,clear` den Vergleich auf die Ereignisse, die zu diesen Kategorien gehören.

> [!TIP]
> Es wird empfohlen, mit `-examine present,draw,copy,clear` zu beginnen, da auf diese Weise die meisten Probleme offengelegt werden, und zwar innerhalb einer wesentlich kürzeren Zeit als bei einer umfangreicheren Reihe von Ereignissen. Bei Bedarf können Sie eine größere oder andere Ereignismenge angeben, um diese Ereignisse zu prüfen und andere Arten von Problemen offenzulegen.

 `-haltonfail` Im Validierungsmodus wird mit `-haltonfail` die Validierung angehalten, wenn Unterschiede zwischen der Hardware und dem WARP-Renderer erkannt werden. Die Validierung wird fortgesetzt, wenn eine Taste gedrückt wird.

 `-exitonfail` Im Validierungsmodus wird mit `-exitonfail` die Validierung sofort beendet, wenn Unterschiede zwischen der Hardware und dem WARP-Renderer erkannt werden. Wird das Programm auf diese Weise beendet, wird `0` an die Umgebung zurückgegeben; andernfalls wird `1` zurückgegeben.

 `-showprogress` Im Validierungsmodus zeigt `-showprogress` Statusinformationen zur Validierungssitzung an. Der WARP-Fortschritt wird auf der linken Seite angezeigt; der Hardware-Status wird auf der rechten Seite angezeigt.

 `-e` `search_string` Listet die installierten UWP-Apps auf. Mithilfe dieser Informationen können Sie Befehlszeilenerfassungen mit UWP-Apps ausführen.

 `-info` Zeigt Informationen über den Computer und die Erfassung von DLLs an.

## <a name="remarks"></a>Hinweise
 DXCap.exe kann in drei verschiedenen Modi betrieben werden:

 Aufzeichnungsmodus (-c): Erfassen von Grafikinformationen aus einer ausgeführten Anwendung und Aufzeichnen dieser Informationen in einer Grafikprotokolldatei. Die Erfassungsfunktionen und das Dateiformat sind identisch mit denen in Visual Studio.

 Wiedergabemodus (-p): Wiedergeben von zuvor aufgezeichneten Grafikereignissen aus einer vorhandenen Grafikprotokolldatei. Standardgemäß erfolgt die Wiedergabe in einem Fenster, auch wenn die Grafikprotokolldatei aus einer Vollbild-Anwendung erfasst wurde. Die Wiedergabe erfolgt nur dann im Vollbildmodus, wenn die Grafikprotokolldatei von einer Vollbildanwendung aufgezeichnet und `-rawmode` angegeben wurde.

 Validierungsmodus (`-v`): Überprüfen des Renderingverhaltens durch Wiedergeben erfasster Frames sowohl auf Hardware als auch auf WARP und Vergleich der Ergebnisse mithilfe einer Bildvergleichsfunktion. Dieses Feature können Sie verwenden, um Treiberprobleme schnell zu identifizieren, die sich auf das Rendering auswirken.

 Zusätzlich zu diesen Modi führt dxcap.exe zwei weitere Funktionen aus, die keine Aufnahme oder Wiedergabe von Grafikinformationen durchführen.

 Aufzählungsfunktion (`-e`): Anzeigen von Details zu den auf dem Computer installierten UWP-Apps. Zu diesen Details zählen der Paketname und die Anwendungs-ID, die die ausführbare Datei in einer UWP-App identifizieren. Verwenden Sie zum Erfassen von Grafikinformationen aus einer Windows Store-Anwendung mit DXCap.exe den Paketnamen und die Anwendungs-ID anstelle der ausführbaren Datei, die verwendet wird, wenn Sie eine Desktop-Anwendung aufnehmen.

 Infofunktion (`-info)`): Anzeigen von Details zum Computer und den Aufzeichnungs-DLLs.

## <a name="examples"></a>Beispiele

### <a name="capture-graphics-information-from-a-desktop-app"></a>Erfassung von Grafikinformationen aus einer Desktopanwendung
 Mit `-c` geben Sie die App an, von der aus Sie Grafikinformationen aufzeichnen möchten.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 Standardmäßig werden Grafikinformationen in der Datei `<appname>-<date>-<time>.vsglog` erfasst. Mit `-file` geben Sie eine andere Datei zum Aufzeichnen an.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 Geben Sie zusätzliche Befehlszeilenparameter für die Anwendung, aus der Sie aufzeichnen an, indem sie sie nach dem Dateinamen der Anwendung einbeziehen.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 Der Befehl in dem obigen Beispiel zeichnet Grafikinformationen aus der Desktopversion von Internet Explorer auf, während die Webseite unter www.fishgl.com angezeigt wird. Diese verwendet die WebGL-API zum Rendern des 3-D-Inhalts.

> [!NOTE]
> Da die nach der App angezeigten Befehlszeilenargumente an sie übergeben werden, müssen Sie die für „DXCap.exe“ bestimmten Argumente vor der `-c`-Option angeben.

### <a name="capture-graphics-information-from-a-uwp-app"></a>Erfassen von Grafikinformationen aus einer UWP-App
 Sie können Grafikinformationen aus einer UWP-App aufzeichnen.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 Die Verwendung von „DXCap.exe“ zum Erfassen von einer UWP-App ähnelt dem Erfassen von einer Windows-Desktopanwendung, aber anstelle des Identifizierens nach Dateinamen identifizieren Sie eine UWP-App nach dem Paketnamen und dem Namen oder der ID der ausführbaren Datei in diesem Paket, aus der Sie die Erfassung durchführen möchten. Um auf Ihrem Computer installierte UWP-Apps einfacher zu identifizieren, verwenden Sie die Option `-e` mit „DXCap.exe“, um diese aufzulisten:

```cmd
DXCap.exe -e
```

 Sie können eine optionale Suchzeichenfolge angeben, um die Anwendung zu finden, die Sie suchen. Wenn die zu suchende Zeichenfolge angegeben ist, listet „DXCap.exe“ die UWP-Apps auf, deren Paketname, App-Name oder App-IDs der Suchzeichenfolge entsprechen. Die Groß- und Kleinschreibung wird bei der Suche nicht berücksichtigt.

```cmd
DXCap.exe -e map
```

 Der obige Befehl listet UWP-Apps auf, die mit „map“ übereinstimmen. Dies ist die Ausgabe:

 **Package "Microsoft.BingMaps":** **InstallDirectory : C:\Programme\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **FullName         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533** **Name             : Microsoft.BingMaps** **Publisher        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US** **Version          : 2.1.2914.1734** **Launchable Applications:** **Id: AppexMaps** **Exe: C:\Programme\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: No** **AppSpec (to launch): DXCap.exe -c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** Die letzte Zeile der Ausgabe für jede aufgeführte Anwendung zeigt den Befehl, den Sie verwenden können, um Grafikinformationen daraus zu erfassen.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Erfassen Sie bestimmte Bilder oder Bilder zwischen bestimmten Zeiten.
 Mit `-frame` legen Sie mithilfe von Kommas und Bereichen die Frames fest, die Sie erfassen möchten:

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 Sie können auch `-period` verwenden, um verschiedene Zeiträume anzugeben, in denen Frames erfasst werden. Zeiträume werden in Sekunden angegeben, und mehrere Bereiche können angegeben werden:

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>Erfassen Sie Frames interaktiv.
 Mit `-manual` erfassen Sie Frames interaktiv. Drücken Sie die EINGABETASTE, um die Aufnahme zu starten, und drücken Sie die EINGABETASTE, um zu stoppen.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>Wiedergeben einer Grafikprotokolldatei
 Mit `-p` können Sie eine zuvor aufgezeichnete Grafikprotokolldatei wiedergeben.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 Lassen Sie den Dateinamen aus, um das Grafikprotokoll wiederzugeben, das zuletzt aufgezeichnet wurde.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>Wiedergabe im raw-Modus
 Mit `-rawmode` können Sie aufgezeichnete Befehle genau so wiedergeben, wie sie aufgetreten sind. Unter einer normalen Wiedergabe werden bestimmte Befehle emuliert, z. B. wird eine Grafikprotokolldatei, die aus einer Vollbild-Anwendung erfasst wurde, in einem Fenster wiedergegeben; bei aktiviertem raw-Modus versucht die gleiche Datei diese im Vollbildmodus wiederzugeben.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>Wiedergabe mit WARP oder einem Hardwaregerät
 Vielleicht möchten Sie die Wiedergabe einer Grafikprotokolldatei erzwingen, die auf einem Hardwaregerät mit WARP aufgezeichnet wurde, oder Sie erzwingen die Wiedergabe eines Protokolls auf einem Hardwaregerät, das WARP verwendet. Verwenden Sie `-warp` für die Wiedergabe mit WARP.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 Verwenden Sie `-hw` für die Wiedergabe mithilfe der Hardware.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>Überprüfen einer Grafikprotokolldatei anhand von WARP
 Unter dem Validierungsmodus wird die Grafikprotokolldatei sowohl auf Hardware als auch WARP wiedergegeben und ihre Ergebnisse werden verglichen. Dadurch können Sie die Rendering-Fehler identifizieren, die vom Treiber verursacht werden. Verwenden Sie „-v“ zum Überprüfen des Verhaltens der Grafikhardware gegenüber WARP.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 Um das Vergleichsmaß zu verringern, können Sie eine Teilmenge der Befehle für die Validierung des Vergleichs angeben, und andere Befehle werden ignoriert. Verwenden Sie „-examine“, um die Befehle anzugeben, deren Ergebnisse Sie vergleichen möchten.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>Konvertieren einer Grafikprotokolldatei in PNG-Dateien
 Um Frames aus einer Grafikprotokolldatei anzuzeigen oder zu analysieren, können mit DXCap.exe erfasste Frames als PNG (Portable Network Graphics)-Bilddateien gespeichert werden. Mit `-screenshot` im Wiedergabemodus können Sie erfasste Frames als PNG-Dateien ausgeben.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 Verwenden Sie `-frame` mit `-screenshot`, um die Frames anzugeben, die Sie ausgeben möchten.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>Konvertieren einer Grafikprotokolldatei in XML-Dateien
 Um Grafikprotokolldateien mit vertrauten Tools wie FindStr oder XSLT zu verarbeiten und zu analysieren, kann DXCap.exe eine Grafikprotokolldatei in XML konvertiert werden. Mit `-toXML` im Wiedergabemodus können Sie das Protokoll in XML konvertieren, anstatt es wiederzugeben.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 Standardmäßig wird die XML-Ausgabe in eine Datei mit demselben Namen wie das Grafikprotokoll geschrieben, aber die Erweiterung .xml wurde zugewiesen. Im obigen Beispiel erhält die XML-Datei den Namen **regression_test_12.xml**. Um der XML-Datei einen anderen Namen zu geben, geben Sie ihn nach `-toXML` an.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 Die resultierende Datei enthält XML, die etwa so aussieht:

```xml
<Moment value="67"/>
<Method name="CreateDXGIFactory1" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />
</Method>

<Moment value="167"/>
<Method name="D3D11CreateDevice" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />
    <Parameter name="Software" type="HMODULE" value="pointer" />
    <Parameter name="Flags" type="UINT" value="0" />
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >
        <Element value="D3D_FEATURE_LEVEL_11_0" />
    </Parameter>
    <Parameter name="FeatureLevels" type="UINT" value="1" />
    <Parameter name="SDKVersion" type="UINT" value="7" />
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />
</Method>
```

## <a name="requirements"></a>Anforderungen