---
title: Schnelle Website-Profilerstellung mit VSPerfASPNETCmd | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit dem Befehlszeilentool VSPerfASPNETCmd ganz leicht ASP.NET-Webanwendungen profilen können.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a08604b95f49f55a5fea254447046d305d8feff9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720422"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Schnelle Websiteprofilerstellung mit VSPerfASPNETCmd

Mit dem Befehlszeilentool **VSPerfASPNETCmd** können Sie problemlos [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen profilen. Verglichen mit dem [VSPerfCmd](../profiling/vsperfcmd.md)-Befehlszeilentool stehen weniger Optionen zur Verfügung, müssen keine Umgebungsvariablen festgelegt werden und ein Neustart des Computers ist nicht erforderlich. Die Verwendung von **VSPerfASPNETCmd** ist die bevorzugte Methode für die Profilerstellung mit dem eigenständigen Profiler. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren des eigenständigen Profilers](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Weitere Informationen finden Sie unter [Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 In einigen Szenarios, z.B. beim Sammeln von Parallelitätsdaten oder Anhalten und Fortsetzen von Profilerstellungen, ist **VSPerfCmd** die bevorzugte Profilerstellungsmethode.

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

## <a name="profile-an-aspnet-application"></a>Profilen einer ASP.NET-Anwendung

Geben Sie zum Profilen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung einen der in den folgenden Abschnitten beschriebenen Befehle ein. Die Website wird gestartet, und die Datensammlung durch den Profiler beginnt. Verwenden Sie die Anwendung, und schließen Sie den Browser. Drücken Sie die **EINGABETASTE** im Eingabeaufforderungsfenster, um die Profilerstellung zu beenden.

> [!NOTE]
> In der Standardeinstellung wird die Eingabeaufforderung nach einem **vsperfaspnetcmd**-Befehl nicht zurückgeben. Sie können die Option **/nowait** nutzen, um die Rückgabe der Befehlsaufforderung zu erzwingen. Siehe [Verwenden der /NoWait-Option](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Zum Sammeln von Anwendungsstatistiken mithilfe der Samplingmethode
 Das Sampling ist die standardmäßige Profilerstellungsmethode des Tools **VSPerfASPNETCmd** und muss nicht in der Befehlszeile angegeben werden. Mit der folgenden Befehlszeile werden Anwendungsstatistiken über die angegebene Webanwendung gesammelt:

 **vsperfaspnetcmd**  *websiteUrl*

 Ein Beispiel für eine auf einem lokalen Server gehostete *websiteurl* ist *http://localhost/MySite/default.aspx*. Ein Beispiel für eine externe Website ist *http://www.contoso.com* . Weitere Informationen finden Sie in den Beispiel-URLs in [Profilerstellung für eine Website ohne das Öffnen eines Projekts in Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Sammeln von ausführlichen Zeitsteuerungsdaten mit der Instrumentierungsmethode

Verwenden Sie die folgende Befehlszeile zum Sammeln ausführlicher Zeitsteuerungsdaten über eine dynamisch kompilierte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung:

**vsperfaspnetcmd /trace**  *websiteUrl*

Wenn Sie statisch kompilierte *DLL*-Dateien in Ihrer Webanwendung profilen möchten, müssen Sie die Dateien mithilfe des Befehlszeilentools [VSInstr](../profiling/vsinstr.md) instrumentieren. Der Vsperfaspnetcmd/Trace-Befehl wird Daten aus den instrumentierten Dateien enthalten.

## <a name="to-collect-net-memory-data"></a>Sammeln von NET-Speicherdaten

Die **/Memory**-Option sammelt Daten zur Zuordnung von Objekten im .NET- Speicher und kann Daten über die Lebensdauer dieser Objekte sammeln. Sammeln von Speicherbelegungsdaten ist der Standardmodus der **/Memory**-Datenoption und muss nicht in der Befehlszeile angegeben werden.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Verwenden der **Lebensdauer**-Parameter zum Sammeln von Objektlebensdauerdaten zusätzlich zu den Speicherbelegungsdaten:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 Sie können auch die **/Trace**-Option verwenden, um ausführliche Zeitsteuerungsinformationen in die .NET-Speicherdaten einzuschließen:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Erfassen von Ebeneninteraktionsdaten

> [!WARNING]
> Profilerstellungsdaten für die Ebeneninteraktion (Tier Interaction Profiling, TIP) können mit einer beliebigen Visual Studio-Edition erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in Visual Studio Enterprise angezeigt werden.
>
> Sie müssen zum Erfassen von TIP-Daten auf Windows 8 oder Windows Server 2012 die Instrumentierungsoption (**/trace**) verwenden.

Erfassen von Ebeneninteraktionsdaten mit Samplingdaten:

**vsperfaspnetcmd /tip** `websiteUrl`

Sammeln von Ebeneninteraktionsdaten mit Instrumentationsdaten:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Sammeln von Ebeneninteraktionsdaten mit .NET-Speicherdaten:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Verwenden der /NoWait-Option

In der Standardeinstellung wird die Eingabeaufforderung nach einem **vsperfaspnetcmd**-Befehl nicht zurückgeben. Sie können die folgende Syntaxoption verwenden, um die Rückgabe des Befehls zu erzwingen. Sie können dann andere Vorgänge im Eingabeaufforderungsfenster ausführen. Verwenden Sie zum Beenden der Profilerstellung die **/shutdown**-Option in einem separaten **vsperfaspnetcmd**-Befehl.

So beginnen Sie mit der Profilerstellung:

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

So beenden Sie die Profilerstellung:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Zusätzliche Optionen

Sie können eine der folgenden Optionen zu den weiter oben in diesem Abschnitt aufgelisteten Befehlen hinzufügen, mit Ausnahme des Befehls **vsperfaspnetcmd/shutdown**.

|Option|Beschreibung|
|------------|-----------------|
|**/Output:** `VspFile`|Standardmäßig wird die Profilerstellungsdatendatei (*VSP*) im aktuellen Verzeichnis mit dem Dateinamen **PerformanceReport.vsp** erstellt. Verwenden Sie die Option /Output, um einen anderen Speicherort, Dateinamen oder beides anzugeben.|
|**/PackSymbols:Off**|Standardmäßig bettet VsPerfASPNETCmd Symbole (Funktionsnamen, Parameternamen usw.) in die *VSP*-Datei ein. Das Einbetten der Symbole kann die Profilerstellungsdatendatei sehr groß werden lassen. Wenn Sie auf die *PDB*-Dateien zugreifen können, die die Symbole enthalten, wenn Sie die Daten analysieren, verwenden Sie die Option „/packsymbols:off“, um die Einbettung der Symbole zu deaktivieren.|
