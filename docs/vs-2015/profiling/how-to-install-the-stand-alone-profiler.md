---
title: 'Vorgehensweise: Installieren des eigenständigen Profilers | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 026162a2c8334c7163f9c7853d2de30e58e5939a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476787"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Gewusst wie: Installieren des eigenständigen Profilers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bietet einen befehlszeilenbasierten, eigenständigen Profiler, der ohne eine Installation der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE ausgeführt werden kann. Diese Situation tritt auf, wenn auf einem Computer keine Entwicklungsumgebung installiert ist oder nicht installiert werden kann. Sie sollten beispielsweise keine Entwicklungsumgebung auf einem Produktionswebserver installieren.  
  
> [!NOTE]
> Wenn Sie den eigenständigen Profiler verwenden, um Leistungsdaten für die ASP.NET-Website zu erfassen, wird das [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)-Befehlszeilentool statt dem [VSPerfCmd](../profiling/vsperfcmd.md)-Tool empfohlen.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Installieren des eigenständigen Profilers  
  
1. Suchen Sie den Installer des eigenständigen Profilers („vs_profiler.exe“) auf den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Installationsmedien in dem Verzeichnis, das den Pfad „\Standalone Profiler“ enthält, und führen Sie diesen aus.  
  
2. Fügen Sie die Pfade für „vsintr.exe“ und „msdis150.dll“ zum Systempfad hinzu.  
  
    > [!NOTE]
    > In der Standardinstallation von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] befinden sich „vsintr.exe“ und „msdis150.dll“ unter \Programme\Visual Studio 10\Team Tools\Performance Tools.  
  
3. Geben Sie **VSInstr** in der Eingabeaufforderung ein.  
  
    > [!NOTE]
    > Wenn die Nutzungsinformationen für „vsinstr.exe“ angezeigt werden, ist alles ordnungsgemäß eingerichtet. Wenn Ihnen ein Fehler angezeigt wird, dass „vsinstr.exe“ oder eine der Abhängigkeiten nicht gefunden werden kann, stellen Sie sicher, dass Sie die Pfade wie in Schritt 2 beschrieben ordnungsgemäß eingerichtet haben.  
  
4. Richten Sie den Symbol Server ein, indem Sie die **_NT_SYMBOL_PATH** Variable auf festlegen. `symsrv*symsrv.dll*c:\localcache*https://msdl.microsoft.com/download/symbols`  
  
5. Nachdem Sie Ihren Symbolserver mithilfe der Umgebungsvariablen des Systems eingerichtet haben, führen Sie die Befehlszeilentools des Profilers über eine neue Eingabeaufforderung aus. Dadurch werden die neuen Umgebungsvariablen wirksam. Geben Sie im Fenster der Eingabeaufforderung folgenden Befehl ein:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    > Ausführliche Anweisungen zum Einrichten des Symbol Server Pakets finden Sie unter Gewusst [wie: verweisen auf Windows-Symbol Informationen](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Verwenden Sie das [VSPerfReport](../profiling/vsperfreport.md)-Tool, um Ihre Symbole in der Datei für Profilerstellungsdaten (VSP) zu serialisieren. Verwenden Sie die Schalter **VSPerfReport /summary:all /packsymbols**. Wenn Sie keine Symbole in Ihre Datendatei eingefügt haben, stellen Sie sicher, dass Sie die Umgebungsvariable _NT_SYMBOL_PATH festgelegt haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Sampling](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Instrumentation](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Gewusst wie: verweisen auf Windows-Symbol Informationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
