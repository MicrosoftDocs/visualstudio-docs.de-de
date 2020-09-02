---
title: Erweiterte Einstellungen (Dialogfeld) (Parallelitätsschnellansicht) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 128327b956734f7d28e7ff88f3eb6c297544587c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849811"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Erweiterte Einstellungen (Dialogfeld) (Parallelitätsschnellansicht)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe des Dialogfelds **Erweiterte Einstellungen** in der Parallelitätsschnellansicht können Sie steuern, wie Ablaufverfolgungen erfasst werden.  Das Dialogfeld enthält Registerkarten für Symbole, „Nur eigenen Code“, Pufferung, Filterung, CLR-Ereignisse, Marker, Anbieter und Dateien.  
  
## <a name="symbols"></a>Symbole  
 Die Parallelitätsschnellansicht verwendet die gleichen Symboleinstellungen wie der Visual Studio Debugger. Die Parallelitätsschnellansicht verwendet die Einstellungen zum Auflösen von Aufruflisten, die Leistungsdaten zugeordnet sind.  Bei der Verarbeitung von Ablaufverfolgungen greift die Parallelitätsschnellansicht auf die Symbolserver zu, die auf der Einstellungenseite angegeben sind.  Wenn über ein Netzwerk auf diese Daten zugegriffen wird, wird die Verarbeitung der Ablaufverfolgung verlangsamt.  Um die Zeitspanne zu reduzieren, die erforderlich ist, um Symbole aufzulösen, können Sie Symbole lokal zwischenspeichern. Wenn Symbole heruntergeladen wurden, lädt Visual Studio sie aus dem lokalen Cache.  
  
## <a name="just-my-code"></a>Nur eigenen Code  
 „Nur eigenen Code“ ist standardmäßig der Satz von EXE- und DLL-Dateien, die der aktuellen Projektmappe in Visual Studio zugeordnet sind. Die Parallelitätsschnellansicht bewertet diesen Satz von Dateien, wenn Sie das Feature „Nur eigenen Code“ zum Filtern der Aufruflisten verwenden. Auf der Registerkarte „Nur eigenen Code“ können Sie Verzeichnisse, die EXE- und DLL-Dateien enthalten, den Speicherorten hinzufügen, die die Parallelitätsschnellansicht für „Nur eigenen Code“ verwendet.  
  
 Die Pfade der EXE- und DLL-Dateien werden in der Ablaufverfolgungsdatei gespeichert, wenn die Ablaufverfolgung erfasst wird.  Das Ändern dieser Einstellung wirkt sich nicht auf zuvor erfasste Ablaufverfolgungen aus.  
  
## <a name="buffering"></a>Pufferung  
 Die Parallelitätsschnellansicht verwendet die Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW), wenn sie eine Ablaufverfolgung erfasst.  ETW verwendet beim Speichern von Ereignissen verschiedene Puffer.  Die Standardeinstellungen für ETW-Puffer sind möglicherweise nicht in allen Fällen optimal und könnten in einigen Fällen Probleme wie z.B. den Verlust von Ereignissen verursachen.  Auf der Registerkarte Pufferung können Sie die ETW-Puffereinstellungen konfigurieren. Weitere Informationen finden Sie unter [Event Tracing](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) (Ereignisablaufverfolgung) und [EVENT_TRACE_PROPERTIES structure](https://msdn.microsoft.com/library/aa363784(VS.85).aspx) (EVENT_TRACE_PROPERTIES-Struktur).  
  
## <a name="filter"></a>Filter  
 Auf der Registerkarte „Filter“ können Sie den Satz der Ereignisse auswählen, die die Parallelitätsschnellansicht erfasst. Die Auswahl einer Teilmenge von Ereignissen schränkt die Typen der Daten ein, die in den Berichten angezeigt werden, reduziert die Größe der einzelnen Ablaufverfolgungen und die Zeit, die erforderlich ist, um Ablaufverfolgungen zu verarbeiten.  
  
### <a name="clr-events"></a>CLR-Ereignisse  
 Durch die Common Language Runtime (CLR) generierte Ereignisse ermöglichen der Parallelitätsschnellansicht, verwaltete Aufruflisten aufzulösen.  Wenn Sie das Erfassen von CLR-Ereignissen deaktivieren, wird die Größe der Ablaufverfolgung reduziert, aber einige Aufruflisten können nicht aufgelöst werden.  Infolge dessen könnte manche CPU-Threadaktivität falsch kategorisiert werden.  
  
### <a name="collect-for-native-processes"></a>Erfassen für native Prozesse  
 Standardmäßig werden CLR-Ereignisse nur erfasst, wenn ein verwalteter Prozess geprofilet wird, da sie normalerweise für native Prozesse nicht erforderlich sind.  In einigen Fällen (wenn z.B. ein nativer Prozess die CLR hostet) müssen Sie möglicherweise CLR-Ereignisse für einen nativen Prozess erfassen.  Wenn dies der Fall ist, aktivieren Sie das Kontrollkästchen **Für systemeigene Prozesse auflisten**.  
  
### <a name="disable-rundown-events"></a>Deaktivieren von Rundown-Ereignissen  
 Die CLR generiert Ereignisse von zwei Anbietern: Runtime und Rundown.  Wenn Sie CLR-Runtime-Ereignisse erfassen möchten, aber das Erfassen von Rundown-Ereignissen vermeiden möchten, aktivieren Sie das Kontrollkästchen **Rundown-Ereignisse deaktivieren**.  Dies reduziert die Größe der Ablaufverfolgungsdatei, die von der Erfassung generiert wird, aber einige Stapel können möglicherweise nicht aufgelöst werden. Weitere Informationen finden Sie unter [CLR-ETW-Anbieter](https://msdn.microsoft.com/library/0beafad4-b2c8-47f4-b342-83411d57a51f) .  
  
### <a name="sample-events"></a>Samplingereignisse  
 Sie können Samplingereignisse verwenden, um Aufruflisten zu erfassen, die der Threadausführung zugeordnet sind. Diese Ereignisse werden ungefähr einmal pro Millisekunde für Threads erfasst, die im aktuellen Prozess ausgeführt werden. Wenn Sie die Erfassung von Samplingereignissen deaktivieren, wird die Größe der erfassten Ablaufverfolgung reduziert, aber Sie können keine Aufruflisten anzeigen, die der Threadausführung zugeordnet sind.  
  
### <a name="gpu-events"></a>GPU-Ereignisse  
 GPU-Ereignisse werden von DirectX generiert. Wenn Sie die Erfassung der GPU-Ereignisse deaktivieren, wird die Größe der erfassten Ablaufverfolgung reduziert, aber Sie können weder GPU-Aktivität in der Auslastungsansicht noch DirectX-Engine-Aktivität in der Threadansicht anzeigen.  
  
### <a name="file-io-events"></a>Datei-E/A-Ereignisse  
 Datei-E/A-Ereignisse stellen Zugriffe auf den Datenträger durch den aktuellen Prozess dar.  Wenn Sie „Datei-E/A-Ereignisse“ deaktivieren, wird die Größe der Ablaufverfolgung reduziert, aber die Threadansicht meldet keine Informationen über Datenträgerkanäle oder Datenträgervorgänge.  
  
## <a name="markers"></a>Marker  
 Auf der Registerkarte „Marker“ können Sie den Satz von ETW-Anbietern konfigurieren, die als Marker in der Parallelitätsschnellansicht angezeigt werden.  Sie können die Markererfassung auch basierend auf Wichtigkeitsstufe und ETW-Kategorie filtern.  Bei Verwendung des [Parallelitätsschnellansichts-SDK](../profiling/concurrency-visualizer-sdk.md) und Ihres eigenen Markeranbieters können Sie ihn hier registrieren, damit er in der Threadansicht angezeigt wird.  
  
### <a name="adding-a-new-provider"></a>Hinzufügen eines neuen Anbieters  
 Wenn der Code das [SDK für die Parallelitätsschnellansicht](../profiling/concurrency-visualizer-sdk.md) oder generierte ETW-Ereignisse verwendet, die der Konvention <xref:System.Diagnostics.Tracing.EventSource> entsprechen, können Sie diese Ereignisse in der Parallelitätsschnellansicht anzeigen, indem Sie sie in diesem Dialogfeld registrieren.  
  
 Geben Sie im Feld „Name“ einen Namen ein, der die Typen von Ereignissen beschreibt, die vom Anbieter generiert werden.  Geben Sie im Feld „GUID“ die GUID ein, die diesem Anbieter zugeordnet ist. (Eine GUID ist jedem ETW-Anbieter zugeordnet.)  
  
 Optional können Sie angeben, ob Ereignisse von diesem Anbieter basierend auf Kategorie oder Wichtigkeitsstufe herausgefiltert werden.  Sie können mithilfe des Kategoriefelds auf Grundlage der Kategorien des Parallelitätsschnellansicht-SDK filtern.  Geben Sie zu diesem Zweck eine durch Kommas getrennte Zeichenfolge von Kategorien oder einen Bereich von Kategorien ein.  Hiermit geben Sie an, welche Kategorien von Ereignissen im aktuellen Anbieter angezeigt werden.  Wenn Sie einen <xref:System.Diagnostics.Tracing.EventSource>-Anbieter hinzufügen, können Sie das Kategoriefeld zum Filtern nach dem ETW-Schlüsselwort verwenden.  Da das Schlüsselwort eine Bitmaske ist, können Sie eine durch Kommas getrennte Zeichenfolge von ganzen Zahlen verwenden, um anzugeben, welche Bits in der Maske festgelegt sind. Mit „1,2“ legen Sie z.B. das erste und zweite Bit fest, und daraus ergibt sich 6 im Dezimalformat.  
  
 Mit dieser Wichtigkeitsstufenliste können Sie Ereignisse herausfiltern, deren Wichtigkeits- oder ETW-Stufe unter dem angegebenen Wert liegt.  
  
### <a name="configuring-an-existing-provider"></a>Konfigurieren eines vorhandenen Anbieters  
 Um Einstellungen zu bearbeiten, die einem vorhandenen Anbieter zugeordnet sind, wählen Sie sie in der Liste aus, und wählen Sie dann die Schaltfläche **Anbieter bearbeiten**.  Sie können Namen, GUID und Filterungseinstellungen ändern.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Herausfiltern von Markerdaten aus den Parallelitätsschnellansicht-Berichten  
 Wenn Sie nicht wünschen, dass die Daten für einen bestimmten Anbieter in zukünftigen Ablaufverfolgungen angezeigt werden, deaktivieren Sie das Kontrollkästchen neben dem Anbieter, den Sie entfernen möchten.  
  
## <a name="files"></a>Dateien  
 Auf der Registerkarte **Dateien** können Sie das Verzeichnis angeben, unter dem Ablaufverfolgungsdateien bei jedem Erfassen einer Ablaufverfolgung gespeichert werden.  Die Parallelitätsschnellansicht generiert vier Dateien für jede Ablaufverfolgung, die sie erfasst:  
  
- Eine Ereignisablaufverfolgungs-Protokolldatei (ETL) für den Kernelmodus (*.kernel.etl)  
  
- Eine Ereignisablaufverfolgungs-Protokolldatei (ETL) für den Benutzermodus (*.user.etl)  
  
- Eine Parallelitätsschnellansicht-Datendatei (*.CVData)  
  
- Eine Parallelitätsschnellansicht-Ablaufverfolgungsdatei (*.CVTrace)  
  
  Die zwei ETL-Dateien speichern die unformatierten Ablaufverfolgungsdaten, und die beiden Parallelitätsschnellansicht-Dateien speichern die verarbeiteten Daten.  Die unformatierten ETL-Dateien werden nach der Verarbeitung einer Ablaufverfolgung in der Regel nicht verwendet.  Durch Aktivieren des Kontrollkästchens **Ereignis Ablauf Verfolgungs Protokoll (ETL) nach der Analyse löschen** wird die Menge der Ablauf Verfolgungs Daten reduziert, die auf dem Datenträger gespeichert sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nur eigenen Code](../profiling/just-my-code-threads-view.md)   
 [Parallelitätsschnellansichtsmarker](../profiling/concurrency-visualizer-markers.md)
