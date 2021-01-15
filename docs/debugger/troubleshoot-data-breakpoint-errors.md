---
title: Datenhaltepunkt kann nicht festgelegt werden | Microsoft-Dokumentation
description: In diesem Artikel finden Sie Erläuterungen, Lösungen und Problemumgehungen für die Fehlermeldung „Unable to set data breakpoint“ (Datenhaltepunkt kann nicht festgelegt werden), die bei Verwendung von „Bei Wertänderungen unterbrechen“ auftreten.
ms.custom: SEO-VS-2020
ms.date: 12/3/2019
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 4e90c3d4af8e568f1bb2e6987c66c7fbc0856c57
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150456"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Problembehandlung bei Fehlern mit Datenhaltepunkten
Auf dieser Seite wird Schritt für Schritt beschrieben, wie Sie häufige Fehler bei Verwendung von „Bei Wertänderungen unterbrechen“ beheben.

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnostizieren von Fehlern vom Typ „Datenhaltepunkt kann nicht festgelegt werden“
> [!IMPORTANT]
> Verwaltete Datenhaltepunkte (Breakpoints) werden in .NET Core 3.0 und höher unterstützt. Sie können die aktuelle Version [hier](https://dotnet.microsoft.com/download) herunterladen.

Unten ist eine Liste mit Fehlern angegeben, die auftreten können, wenn Sie verwaltete Datenhaltepunkte nutzen. Die Liste enthält zusätzliche Beschreibungen, warum der Fehler auftritt, und mögliche Lösungen oder Problemumgehungen zur Fehlerbehebung.

- *„Die vom Zielprozess verwendete .NET-Version unterstützt keine Datenhaltepunkte. Für Datenhaltepunkte ist .NET Core 3.0 oder höher mit Ausführung auf x86 oder x64 erforderlich.“*

  - Die Unterstützung für verwaltete Datenhaltepunkte hat ab .NET Core 3.0 begonnen. Für .NET Framework oder frühere .NET Core-Versionen als 3.0 ist derzeit keine Unterstützung vorhanden. 
    
  - **Lösung**: Die Lösung besteht hierbei darin, Ihr Projekt auf .NET Core 3.0 zu aktualisieren.

- *„Der Wert wurde auf dem verwalteten Heap nicht gefunden und kann nicht nachverfolgt werden.“*
  - Die Variable wird im Stapel deklariert.
    - Es ist keine Unterstützung für das Festlegen von Datenhaltepunkten für Variablen vorhanden, die im Stapel erstellt werden. Der Grund ist, dass diese Variable ungültig ist, nachdem die Funktion beendet wurde.
    - **Problemumgehung:** Legen Sie Haltepunkte für Zeilen fest, in denen die Variable verwendet wird.

  - Verwenden Sie „Bei Wertänderungen unterbrechen“ für eine Variable, die nicht über eine Dropdownliste erweitert wird.
    - Der Debugger muss intern das Objekt kennen, in dem das nachzuverfolgende Feld enthalten ist. Unter Umständen verschiebt der Garbage Collector Ihr Objekt im Heap. Daher muss der Debugger wissen, in welchem Objekt die nachzuverfolgende Variable enthalten ist. 
    - **Problemumgehung:** Gehen Sie wie folgt vor, wenn Sie sich in einer Methode des Objekts befinden, für das Sie einen Datenhaltepunkt festlegen möchten: Navigieren Sie einen Frame nach oben, und verwenden Sie das Fenster `locals/autos/watch`, um das Objekt zu erweitern, und legen Sie dann einen Datenhaltepunkt für das gewünschte Feld fest.

- *„Datenhaltepunkte werden für statische Felder oder statische Eigenschaften nicht unterstützt.“*
    
  - Statische Felder und Eigenschaften werden derzeit nicht unterstützt. Senden Sie uns [Feedback](#provide-feedback), falls Sie an diesem Feature interessiert sind.

- *„Felder und Eigenschaften von Strukturen können nicht nachverfolgt werden.“*

  - Felder und Eigenschaften von Strukturen werden derzeit nicht unterstützt. Senden Sie uns [Feedback](#provide-feedback), falls Sie an diesem Feature interessiert sind.

- *„Der Eigenschaftswert wurde geändert und kann nicht mehr nachverfolgt werden.“*

  - Mit einer Eigenschaft kann geändert werden, wie die Berechnung zur Laufzeit erfolgt. Wenn dies passiert, erhöht sich die Anzahl von Variablen, von denen die Eigenschaft abhängig ist, und dies kann zu einer Überschreitung der Hardwarebeschränkung führen. Weitere Informationen finden Sie bei `"The property is dependent on more memory than can be tracked by the hardware."` weiter unten.

- *„Die Eigenschaft ist von mehr Arbeitsspeicher abhängig, als von der Hardware nachverfolgt werden kann.“*
    
  - Jede Architektur verfügt über eine bestimmte Anzahl von Bytes und Hardware-Datenhaltepunkten, die unterstützt werden können. Für die Eigenschaft, für die Sie einen Datenhaltepunkt festlegen möchten, wurde dieser Grenzwert überschritten. Die Tabelle [Hardwarebeschränkungen für Datenhaltepunkte](#data-breakpoint-hardware-limitations) enthält Informationen dazu, wie viele von der Hardware unterstützte Datenhaltepunkte und Bytes für die von Ihnen verwendete Architektur verfügbar sind. 
  - **Problemumgehung:** Legen Sie einen Datenhaltepunkt für einen Wert fest, der sich in der Eigenschaft ändern kann.

- *„Datenhaltepunkte werden nicht unterstützt, wenn die Legacy-C#-Ausdrucksauswertung verwendet wird.“*

  - Datenhaltepunkte werden nur für die neue C#-Ausdrucksauswertung unterstützt. 
  - **Lösung**: Sie deaktivieren die Legacy-C#-Ausdrucksauswertung, indem Sie zu `Debug -> Options` navigieren und dann unter `Debugging -> General` die Option `"Use the legacy C# and VB expression evaluators"` deaktivieren.

## <a name="data-breakpoint-hardware-limitations"></a>Hardwarebeschränkungen für Datenhaltepunkte

Die Architektur (Plattformkonfiguration), auf der Ihr Programm ausgeführt wird, verfügt über eine begrenzte Anzahl von Hardware-Datenhaltepunkten, die genutzt werden können. In der folgenden Tabelle ist angegeben, wie viele Register pro Architektur genutzt werden können.

| Architektur | Anzahl der von der Hardware unterstützten Datenhaltepunkte | Maximale Bytegröße|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Feedback bereitstellen

Wenn Sie uns Informationen zu Problemen oder Vorschläge zu diesem Feature zukommen lassen möchten, können Sie in der IDE „Hilfe“ > „Feedback senden“ > [Problem melden](../ide/how-to-report-a-problem-with-visual-studio.md) auswählen oder die [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8) nutzen.

## <a name="see-also"></a>Siehe auch

- [Verwenden von „Bei Wertänderungen unterbrechen“ in .NET Core 3.0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog: Bei Wertänderungen unterbrechen: Datenhaltepunkte für .NET Core in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
