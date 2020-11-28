---
title: Diagnosedaten und vom System generierte Protokolle
description: Hier finden Sie Informationen zu systemgenerierten Visual Studio-Protokollen, den Typen der gesammelten Daten und deren Verwendung zum Lösen von Problemen und Verbessern der Produktqualität.
ms.custom: SEO-VS-2020
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93f450eab5879991f45f4a924338d4a277d13544
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95005924"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Vom System generierte Protokolle, die von Visual Studio gesammelt werden

Visual Studio sammelt vom System generierte Protokolle zum Beheben von Fehlern und Verbessern der Produktqualität mithilfe des [Programms zur Verbesserung der Benutzerfreundlichkeit von Visual Studio](visual-studio-experience-improvement-program.md). Dieser Artikel enthält Informationen über die gesammelten Arten von Daten, und wie sie verwendet werden. Außerdem enthält er Tipps dazu, wie Erweiterungsersteller die unbeabsichtigte Offenlegung von personenbezogenen und vertraulichen Informationen vermeiden können.

## <a name="types-of-collected-data"></a>Gesammelte Datentypen

Visual Studio sammelt vom System generierte Protokolle für Abstürze, nicht reagierende Benutzeroberflächen und hohe Auslastung der CPU oder des Arbeitsspeichers. Außerdem werden Informationen zu Fehlern gesammelt, die während der Installation oder Verwendung eines Produkts auftreten. Die gesammelten Daten variieren basierend auf dem Fehler und können Stapelüberwachungen, Speicherabbilder und Ausnahmeinformationen enthalten:

- Bei hoher CPU-Auslastung und Nichtreaktion werden Stapelüberwachungen von relevanten Visual Studio-Threads gesammelt.

- In Fällen, bei denen die Stapelüberwachungen mancher Threads nicht ausreichen, um die Ursache von Fehlern wie Abstürzen, nicht reagierenden Programmen oder hoher Arbeitsspeicherauslastung zu ermitteln, wird ein *Speicherabbild* gesammelt. Das Abbild stellt den Zustand des Prozesses zu dem Zeitpunkt dar, an dem der Fehler aufgetreten ist.

- Bei unerwarteten Fehlerbedingungen, z.B. einer Ausnahme beim Schreiben in eine Datei auf dem Datenträger, werden Informationen über die Ausnahme gesammelt. Die Informationen enthalten den Namen der Ausnahme, die Stapelüberwachung des Threads, in dem die Ausnahme aufgetreten ist, die der Ausnahme zugeordnete Meldung und weitere Informationen, die für die spezifische Ausnahme relevant sind.

   Das folgende Beispiel für gesammelte Daten zeigt den Namen einer Ausnahme, eine Stapelüberwachung und eine Ausnahmemeldung:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Wie vom System generierte Protokolle verwendet werden

Der Workflow zum Bestimmen der Fehlerursache variiert je nach Fehlertyp und Schweregrad.

### <a name="error-classification"></a>Fehlerklassifizierung

Fehler werden anhand der Protokolle klassifiziert und gezählt, um deren Untersuchung zu priorisieren. Beispielsweise wird ermittelt, dass „System.IO.\__Error.WinIOError“ in Version \<x> des Produkts mit 500-mal am häufigsten in „System.IO.FileStream.Init“ aufgetreten ist.

### <a name="work-items-for-tracking"></a>Arbeitselemente für die Nachverfolgung

Arbeitselemente für individuelle, priorisierte Fehler werden erstellt und Entwicklern zur Untersuchung zugewiesen. Diese Arbeitselemente enthalten in der Regel die Klassifizierung, Priorität und Diagnoseinformationen, die für den Fehlertyp relevant sind. Diese Informationen werden aus den gesammelten vom System generierten Protokollen zu dem Fehler abgeleitet. Ein Arbeitselement für einen Absturz kann z.B. die Stapelüberwachung enthalten, in der der Absturz auftritt.

### <a name="error-investigation"></a>Fehleruntersuchung

Entwickler verwenden die in einem Arbeitselement verfügbaren Informationen, um die Ursache des Fehlers zu ermitteln. In manchen Fällen benötigen sie mehr Informationen, als im Arbeitselement vorhanden ist. In diesem Fall beziehen sie sich auf das ursprüngliche vom System generierte Protokoll. Ein Entwickler kann beispielsweise ein Speicherabbild überprüfen, um den Absturz eines Produkts nachzuvollziehen.

## <a name="tips-for-extension-authors"></a>Tipps für Erweiterungsersteller

Erweiterungsersteller sollten die Offenlegung personenbezogener Informationen einschränken, indem sie keine personenbezogenen oder anderweitig vertraulichen Informationen im Namen ihrer Module, Typen und Methoden verwenden. Wenn ein Absturz oder eine ähnliche Fehlerbedingung mit dem Code auf dem Stapel auftritt, werden diese Informationen als Teil der vom System generierten Protokolle gesammelt.

## <a name="opt-out-of-data-collection"></a>Ablehnen der Datensammlung

Aufgrund des Zwecks der gesammelten Daten und deren Einschränkungen des Zugriffs und der Aufbewahrung, wird empfohlen, dass Sie die Standardeinstellungen für den Datenschutz für Visual Studio und Windows verwenden. Sie können das Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio jedoch [deaktivieren](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out). Informationen zum Deaktivieren der vom System generierten Protokollsammlung für alle Programme finden Sie unter [Diagnose, Feedback und Datenschutz unter Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Die Optionen variieren je nach der verwendeten Version von Windows.

## <a name="see-also"></a>Siehe auch

- [Programm zur Verbesserung der Visual Studio-Benutzerfreundlichkeit](visual-studio-experience-improvement-program.md)
- [Diagnose, Feedback und Datenschutz unter Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)