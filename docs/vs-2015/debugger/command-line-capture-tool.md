---
title: Befehlszeilen-Erfassungstool | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 208ff7f9bbfc2d07669a8b485edffc8dfc4cd54f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841091"
---
# <a name="command-line-capture-tool"></a>Befehlszeilen-Erfassungs-Tool
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe ist ein Befehlszeilenprogramm für die Aufzeichnung und Wiedergabe der Grafikdiagnose. Es unterstützt Direct3D 10 bis Direct3D 12 auf allen Funktionsebenen.  
  
## <a name="syntax"></a>Syntax  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### <a name="parameters"></a>Parameter  
 `-file` `filename`  
  Unter Aufnahmemodus (`-c`) gibt `filename` den Namen der Grafikprotokolldatei an, in der die Grafikinformationen aufgezeichnet werden. Wenn `filename` nicht angegeben ist, werden Grafik Informationen in einer Datei `<appname>-<date>-<time>.vsglog` mit dem Namen standardmäßig aufgezeichnet.  
  
 Unter Gültigkeitsprüfung (-V)-Modus `filename` wird der Namen der zu prüfenden Grafikprotokolldatei angezeigt. Wenn `filename` nicht angegeben ist, wird das Graphics-Protokoll, das zuletzt geprüft wurde, erneut verwendet.  
  
 `-frame` `frames`  
 Unter dem Erfassungsmodus gibt `frames` die Frames an, die Sie erfassen möchten. Der erste Frame ist 1. Sie können mehrere Frames mithilfe von Kommas und Bereichen angeben. Wenn `frames` beispielsweise `2, 5, 7-9, 15` ist, werden die Frames `2`, `5`, `7`, `8`, `9` und `15` aufgezeichnet.  
  
 `-period` `periods`  
 Unter dem Erfassungsmodus legt `periods` die Bereiche für die Zeit in Sekunden fest, in denen Sie Frames erfassen möchten. Sie können mehrere Perioden mithilfe von Kommas und Bereichen angeben. Wenn `periods` beispielsweise `2.1-5, 7.0-9.3` ist, werden Frames erfasst, die zwischen `2.1` und `5` Sekunden sowie zwischen `7` und `9.3` Sekunden gerendert werden.  
  
 `-manual`  
 Im Aufzeichnungsmodus `-manual` gibt an, dass Frames durch Drücken der druckbildschirm Taste manuell aufgezeichnet werden. Frames können erfasst werden, wenn die Anwendung gestartet wird; Um das Erfassen von Frames zu beenden, kehren Sie zur Befehlszeilen-Schnittstelle zurück und drücken Sie die EINGABETASTE.  
  
 `-c` `app` [`args...`]  
 Aufnahme-Modus. Unter dem Aufnahmemodus gibt `app` den Namen der Anwendung an, aus der Sie Grafikinformationen aufzeichnen möchten; `args...` gibt zusätzliche Befehlszeilenparameter für diese Anwendung an.  
  
 `-p` [`filename`]  
 Wiedergabemodus ( `-p` ). Unter dem Wiedergabemodus gibt `filename` den Namen der Grafikprotokolldatei an, die wiedergegeben werden soll. Wenn `filename` nicht angegeben ist, wird das Grafikprotokoll, das zuletzt wiedergegeben wurde, erneut verwendet.  
  
 `-debug`  
 Im Wiedergabemodus `-debug` gibt an, dass die Wiedergabe mit aktivierter Direct3D Debug-Ebene ausgeführt werden soll.  
  
 `-warp`  
 Unter dem Wiedergabemodus `-warp` gibt an, dass die Wiedergabe mit dem Warp Software-Renderer ausgeführt werden soll.  
  
 `-hw`  
 Im Wiedergabemodus gibt an, `-hw` dass die Wiedergabe mithilfe von GPU-Hardware ausgeführt werden soll.  
  
 `-config`  
 Im Wiedergabemodus zeigt Informationen zum Computer an, der `-config` zum Erfassen der Grafik Protokolldatei verwendet wurde, wenn diese Informationen im Protokoll aufgezeichnet wurden.  
  
 `-rawmode`  
  Im Wiedergabemodus gibt `-rawmode` an, dass die Wiedergabe ohne Änderung der aufgezeichneten Ereignisse ausgeführt werden sollte. Unter normalen Bedingungen werden unter dem Wiedergabemodus möglicherweise geringfügige Änderungen an der Wiedergabe vorgenommen, um das Debuggen zu vereinfachen und die Wiedergabe zu beschleunigen. z. B. kann eine Swap-Ketten-Ausgabe anstelle der Ausführung von Swap-Kette Befehlen simuliert werden. Dies ist normalerweise kein Problem, aber möglicherweise muss die Wiedergabe auf eine Weise erfolgen, die für die aufgezeichneten Ereignisse zuverlässiger ist; Sie können mithilfe dieser Option das Full-Screen-Rendering-Verhalten auf einer Anwendung wiederherstellen, die während der Ausführung im Vollbildmodus erfasst wurde.  
  
 `-toXML` [`xml_filename`]  
 Unter dem Wiedergabemodus gibt `xml_filename` den Namen der Datei an, in die eine XML-Darstellung der Wiedergabe geschrieben wird. Wenn `xml_filename` nicht angegeben ist, wird die XML-Darstellung in eine Datei mit demselben Namen der widergegebenen Datei geschrieben, erhält aber eine `.xml` Erweiterung.  
  
 `-v`  
 Validierungsmodus Unter dem Validierungsmodus erfasste Frames werden sowohl auf Hardware als auch auf WARP wiedergegeben, und ihre Ergebnisse werden mithilfe einer Bildvergleichsfunktion verglichen. Dieses Feature können Sie verwenden, um Treiberprobleme schnell zu identifizieren, die sich auf das Rendering auswirken.  
  
 `-examine` `events`  
 Unter dem Validierungsmodus gibt `events` den Grafikereignissatz an, dessen sofortige Ergebnisse verglichen werden. Beispielsweise beschränkt `-examine present,draw,copy,clear` den Vergleich auf die Ereignisse, die zu diesen Kategorien gehören.  
  
> [!TIP]
> Es wird empfohlen, mit `-examine present,draw,copy,clear` zu beginnen, da auf diese Weise die meisten Probleme offengelegt werden, und zwar innerhalb einer wesentlich kürzeren Zeit als bei einer umfangreicheren Reihe von Ereignissen. Bei Bedarf können Sie eine größere oder andere Ereignismenge angeben, um diese Ereignisse zu prüfen und andere Arten von Problemen offenzulegen.  
  
 `-haltonfail`  
  Im Validierungsmodus wird mit `-haltonfail` die Validierung angehalten, wenn Unterschiede zwischen der Hardware und dem WARP-Renderer erkannt werden. Die Validierung wird fortgesetzt, wenn eine Taste gedrückt wird.  
  
 `-exitonfail`  
  Im Validierungsmodus wird mit `-exitonfail` die Validierung sofort beendet, wenn Unterschiede zwischen der Hardware und dem WARP-Renderer erkannt werden. Wird das Programm auf diese Weise beendet, wird `0` an die Umgebung zurückgegeben; andernfalls wird `1` zurückgegeben.  
  
 `-showprogress`  
  Im Validierungsmodus zeigt `-showprogress` Statusinformationen zur Validierungssitzung an. Der WARP-Fortschritt wird auf der linken Seite angezeigt; der Hardware-Status wird auf der rechten Seite angezeigt.  
  
 `-e` `search_string`  
 Listet die Windows Store-Anwendungen auf, die installiert werden. Sie können mithilfe dieser Informationen Befehlszeilen-Snapshots mit Windows Store-Anwendungen ausführen.  
  
 `-info`  
 Zeigt Informationen über den Computer und Erfassung von DLLs an.  
  
## <a name="remarks"></a>Hinweise  
 DXCap.exe kann in drei verschiedenen Modi betrieben werden:  
  
 Aufnahme-Modus (-c)  
 Erfassung von Grafikinformationen aus einer ausgeführten Anwendung und Aufzeichnung dieser Informationen in einer Grafikprotokolldatei. Die Erfassungsfunktionen und das Dateiformat sind identisch mit denen in Visual Studio.  
  
 Wiedergabemodus (-p).  
 Wiedergabe von Grafiken zuvor aufgezeichneter Ereignisse aus einer vorhandenen Grafikprotokolldatei. Standardgemäß erfolgt die Wiedergabe in einem Fenster, auch wenn die Grafikprotokolldatei aus einer Vollbild-Anwendung erfasst wurde. Die Wiedergabe erfolgt nur dann im Vollbildmodus, wenn die Grafikprotokolldatei von einer Vollbildanwendung aufgezeichnet und `–rawmode` angegeben wurde.  
  
 Validierungsmodus (`-v`)  
 Überprüfen des Renderingverhaltens durch die Wiedergabe erfasster Frames sowohl auf Hardware und als auch auf WARP und Vergleich ihrer Ergebnisse mithilfe einer Bildvergleichsfunktion. Dieses Feature können Sie verwenden, um Treiberprobleme schnell zu identifizieren, die sich auf das Rendering auswirken.  
  
 Zusätzlich zu diesen Modi führt dxcap.exe zwei weitere Funktionen aus, die keine Aufnahme oder Wiedergabe von Grafikinformationen durchführen.  
  
 Enumerationsfunktion ( `-e` )  
 Zeigt Details über die Windows Store-Anwendungen an, die auf dem Computer installiert sind. Zu diesen Details zählen der Paketname und die Anwendungs-ID, die die ausführbare Datei in einer Windows Store-Anwendung identifizieren. Verwenden Sie zum Erfassen von Grafikinformationen aus einer Windows Store-Anwendung mit DXCap.exe den Paketnamen und die Anwendungs-ID anstelle der ausführbaren Datei, die verwendet wird, wenn Sie eine Desktop-Anwendung aufnehmen.  
  
 Info-Funktion (`-info)`  
 Zeigt Details über den Computer und Erfassung von DLLs an.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Erfassung von Grafikinformationen aus einer Desktopanwendung  
 Mit `–c` geben Sie die App an, von der aus Sie Grafikinformationen aufzeichnen möchten.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 Standardmäßig werden Grafikinformationen in der Datei `<appname>-<date>-<time>.vsglog` erfasst. Mit `–file` geben Sie eine andere Datei zum Aufzeichnen an.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Geben Sie zusätzliche Befehlszeilenparameter für die Anwendung, aus der Sie aufzeichnen an, indem sie sie nach dem Dateinamen der Anwendung einbeziehen.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Der Befehl in dem obigen Beispiel zeichnet Grafikinformationen aus der Desktopversion von Internet Explorer auf, während die Webseite unter www.fishgl.com angezeigt wird. Diese verwendet die WebGL-API zum Rendern des 3-D-Inhalts.  
  
> [!NOTE]
> Da die nach der App angezeigten Befehlszeilenargumente an sie übergeben werden, müssen Sie die für „DXCap.exe“ bestimmten Argumente vor der `–c`-Option angeben.  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Erfassen Sie Grafikinformationen aus einer Windows Store-Anwendung.  
 Sie können Grafikinformationen aus einer Windows Store-Anwendung aufzeichnen.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Die Verwendung der DXCap.exe zum Erfassen von Windows Store-Anwendungen ähnelt der Erfassung von einer Windows-Desktopanwendung, aber statt der Identifizierung nach Dateinamen identifizieren Sie eine Windows Store-Anwendung nach ihrem Paketnamen und dem Namen oder der ID der ausführbaren Datei in diesem Paket, aus der Sie erfassen möchten. Damit Sie leichter erkennen können, wie Sie Windows Store-Apps identifizieren, die auf Ihrem Computer installiert sind, verwenden `–e` Sie die Option mit DXCap.exe, um Sie aufzulisten:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Sie können eine optionale Suchzeichenfolge angeben, um die Anwendung zu finden, die Sie suchen. Wenn die zu suchende Zeichenfolge angegeben wird, werden DXCap.exe der Windows Store-Anwendungen aufgelistet, deren Paketname, Anwendungsname oder Anwendungs-IDs der Suchzeichenfolge entsprechen. Die Groß- und Kleinschreibung wird bei der Suche nicht berücksichtigt.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 Der obige Befehl listet Windows Store-Anwendungen auf, die mit "Map" übereinstimmen; hier ist die Ausgabe:  
  
 **Package "Microsoft.BingMaps":**  
 **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **Voller Name         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Name             : Microsoft.BingMaps**  
 **Herausgeber        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US**  
 **Version          : 2.1.2914.1734**  
 **Ausführbare Anwendungen:**  
 **ID: AppexMaps**  
 **Exe: C:\Programme\Microsoft Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: No**  
 **Appspec (zum Starten): DXCap.exe-c Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe, appexmaps** Die letzte Zeile der Ausgabe für jede aufgelistete APP zeigt den Befehl an, den Sie zum Erfassen von Grafik Informationen verwenden können.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Erfassen Sie bestimmte Bilder oder Bilder zwischen bestimmten Zeiten.  
 Mit `–frame` legen Sie mithilfe von Kommas und Bereichen die Frames fest, die Sie erfassen möchten:  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 Sie können auch `–period` verwenden, um verschiedene Zeiträume anzugeben, in denen Frames erfasst werden. Zeiträume werden in Sekunden angegeben, und mehrere Bereiche können angegeben werden:  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Erfassen Sie Frames interaktiv.  
 Mit `–manual` erfassen Sie Frames interaktiv. Drücken Sie die EINGABETASTE, um die Aufnahme zu starten, und drücken Sie die EINGABETASTE, um zu stoppen.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Wiedergeben einer Grafikprotokolldatei  
 Mit `-p` können Sie eine zuvor aufgezeichnete Grafikprotokolldatei wiedergeben.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 Lassen Sie den Dateinamen aus, um das Grafikprotokoll wiederzugeben, das zuletzt aufgezeichnet wurde.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Wiedergabe im raw-Modus  
 Mit `-rawmode` können Sie aufgezeichnete Befehle genau so wiedergeben, wie sie aufgetreten sind. Unter einer normalen Wiedergabe werden bestimmte Befehle emuliert, z. B. wird eine Grafikprotokolldatei, die aus einer Vollbild-Anwendung erfasst wurde, in einem Fenster wiedergegeben; bei aktiviertem raw-Modus versucht die gleiche Datei diese im Vollbildmodus wiederzugeben.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Wiedergabe mit WARP oder einem Hardwaregerät  
 Vielleicht möchten Sie die Wiedergabe einer Grafikprotokolldatei erzwingen, die auf einem Hardwaregerät mit WARP aufgezeichnet wurde, oder Sie erzwingen die Wiedergabe eines Protokolls auf einem Hardwaregerät, das WARP verwendet. Verwenden Sie `-warp` für die Wiedergabe mit WARP.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 Verwenden Sie `-hw` für die Wiedergabe mithilfe der Hardware.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Überprüfen einer Grafikprotokolldatei anhand von WARP  
 Unter dem Validierungsmodus wird die Grafikprotokolldatei sowohl auf Hardware als auch WARP wiedergegeben und ihre Ergebnisse werden verglichen. Dadurch können Sie die Rendering-Fehler identifizieren, die vom Treiber verursacht werden. Verwenden Sie -v zum Überprüfen des Verhaltens der Grafikhardware gegenüber WARP.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Um das Vergleichsmaß zu verringern, können Sie eine Teilmenge der Befehle für die Validierung des Vergleichs angeben, und andere Befehle werden ignoriert. Verwenden Sie -examine, um die Befehle anzugeben, deren Ergebnisse Sie vergleichen möchten.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Konvertieren einer Grafikprotokolldatei in PNG-Dateien  
 Um Frames aus einer Grafikprotokolldatei anzuzeigen oder zu analysieren, können mit DXCap.exe erfasste Frames als PNG (Portable Network Graphics)-Bilddateien gespeichert werden. Mit `-screenshot` im Wiedergabemodus können Sie erfasste Frames als PNG-Dateien ausgeben.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Verwenden Sie `–frame` mit `–screenshot`, um die Frames anzugeben, die Sie ausgeben möchten.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Konvertieren einer Grafikprotokolldatei in XML-Dateien  
 Um Grafikprotokolldateien mit vertrauten Tools wie FindStr oder XSLT zu verarbeiten und zu analysieren, kann DXCap.exe eine Grafikprotokolldatei in XML konvertiert werden. Mit `-toXML` im Wiedergabemodus können Sie das Protokoll in XML konvertieren, anstatt es wiederzugeben.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 Standardmäßig wird die XML-Ausgabe in eine Datei mit demselben Namen wie das Grafikprotokoll geschrieben, aber die Erweiterung .xml wurde zugewiesen. Im obigen Beispiel erhält die XML-Datei den Namen **regression_test_12.xml**. Um der XML-Datei einen anderen Namen zu geben, geben Sie ihn nach `-toXML` an.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
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
