---
title: Erfassen einer ETL-Ablaufverfolgung mit PerfView
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 6f0696a24f04d2cba52994c86a3475f56d3e7947
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970711"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Erfassen einer ETL-Ablaufverfolgung mit PerfView

PerfView ist ein Tool, das basierend auf der [Ereignisablaufverfolgung für Windows](/windows/desktop/ETW/event-tracing-portal) ETL-Dateien (Event Trace Log, Ereignisablaufverfolgungs-Protokoll) erstellt, die bei der Behandlung bestimmter Probleme mit Visual Studio hilfreich sein können. Wenn Sie ein Problem melden, werden Sie möglicherweise vom Produktteam gebeten, PerfView zum Erfassen zusätzlicher Informationen auszuführen.

## <a name="install-perfview"></a>Installieren von PerfView

Laden Sie PerfView aus [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md) herunter.

## <a name="run-perfview"></a>Ausführen von PerfView

1. Klicken Sie im Windows-Explorer mit der rechten Maustaste auf **PerfView.exe**, und wählen Sie **Als Administrator ausführen** aus.
1. Wählen Sie im Menü „Collect“ (Erfassen) die Option **Collect** aus.
1. Aktivieren Sie **Zip**, **Merge** und **ThreadTime**.
1. Erhöhen Sie **Circular MB** (MB für Umlaufprotokoll) auf 1000.
1. Ändern Sie **Current Dir** (Aktuelles Verzeichnis), um die ETL-Ablaufverfolgungen in einem angegebenen Ordner zu speichern, und „Data File“ (Datendatei), wenn Sie beabsichtigen, den Vorgang mehrmals durchzuführen.
1. Wählen Sie zum Starten der Datenaufzeichnung die Schaltfläche **Start Collection** (Sammlung starten).
1. Wählen Sie zum Beenden der Datenaufzeichnung die Schaltfläche **Stop Collection** (Sammlung beenden). Die Datei „PrefView.etl.zip“ wird im angegebenen Verzeichnis gespeichert.

PerfView kann nur die neuesten Daten speichern, die in den Puffer passen. Versuchen Sie daher, die Sammlung so bald wie möglich zu beenden, nachdem Visual Studio einzufrieren oder langsamer zu werden beginnt. Die Sammlung sollte nicht länger als 30 Sekunden durchgeführt werden, nachdem ein Problem aufgetreten ist.

Weitere Informationen erhalten Sie im [PerfView-Tutorial in Channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
