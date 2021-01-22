---
title: Analysieren der Datenbanknutzung für .NET Core-Objekte | Microsoft-Dokumentation
description: Verwenden Sie das Datenbanktool, um die Datenbankabfragen Ihrer App aufzuzeichnen, und analysieren Sie diese anschließend, um Möglichkeiten zur Leistungsverbesserung zu finden.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: a8518e3f43bec3a9d5f696a07613dee84829dbc2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205462"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Analysieren der Datenbankleistung mit dem Tool „Datenbank“

Mit dem Tool „Datenbank“ können Sie die Datenbankabfragen aufzeichnen, die Ihre App während einer Diagnosesitzung durchführt. Sie können anschließend Informationen zu einzelnen Abfragen analysieren, um Möglichkeiten zur Verbesserung der Leistung Ihrer App zu finden.

> [!NOTE]
> Das Tool „Datenbank“ erfordert mindestens Visual Studio 2019 Version 16.3 und ein .NET Core-Projekt unter Windows, das entweder mit [ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) oder [Entity Framework Core](/ef/core/) arbeitet.

## <a name="setup"></a>Setup

1. Öffnen Sie über **ALT+F2** den Leistungs-Profiler in Visual Studio.

1. Aktivieren Sie das Kontrollkästchen **Datenbank**.

   ![Ausgewähltes Tool „Datenbank“](./media/db-launch.png "Ausgewähltes Tool „Datenbank“")

   > [!NOTE]
   > Wenn das Tool nicht ausgewählt werden kann, deaktivieren Sie die Kontrollkästchen aller anderen Tools, da einige Tools allein ausgeführt werden müssen. Weitere Informationen über das gemeinsame Ausführen von Tools finden Sie unter [ Verwenden von Profilerstellungstools über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Wenn das Tool immer noch nicht verfügbar ist, überprüfen Sie, ob Ihr Projekt die zuvor genannten Anforderungen erfüllt. Vergewissern Sie sich, dass sich Ihr Projekt im Releasemodus befindet, um die Daten möglichst genau zu erfassen.

1. Klicken Sie auf die Schaltfläche **Start**, um das Tool auszuführen.

1. Gehen Sie nach dem Start des Tools das Szenario durch, für das Sie in Ihrer App ein Profil erstellen möchten. Klicken Sie dann auf **Sammlung beenden**, oder schließen Sie Ihre App, um die Daten anzuzeigen.

1. Nach Beendigung der Sammlung sehen Sie eine Tabelle mit den Abfragen, die während Ihrer Profilerstellungssitzung ausgeführt wurden.

   ![Beendetes Tool „Datenbank“](./media/db-after.png "Beendetes Tool „Datenbank“")

Die Abfragen sind chronologisch organisiert. Sie können sie jedoch anhand beliebiger Spalten sortieren. Sie können weitere Spalten anzeigen, indem Sie mit der rechten Maustaste auf die Spaltenüberschriften klicken. Durch Auswählen der Spalte **Dauer** werden die Abfragen von der längsten bis zur kürzesten Dauer angeordnet.

Wenn Sie eine Abfrage gefunden haben, die Sie untersuchen möchten, klicken Sie mit der rechten Maustaste darauf. Wählen Sie dann **Zur Quelldatei wechseln** aus, um zu prüfen, welcher Code für diese Abfrage verantwortlich ist.

![Ausgewählte Option „Zur Quelldatei wechseln“](./media/db-gotosource.png "Ausgewählte Option „Zur Quelldatei wechseln“")

Wenn Sie in einem Diagramm einen Zeitbereich auswählen, zeigt die Abfragetabelle nur Abfragen an, die in diesem Zeitbereich erfolgt sind. Dieses Verhalten ist besonders nützlich, wenn Sie auch das [Tool „CPU-Auslastung“](./cpu-usage.md?view=vs-2019&preserve-view=true) ausführen.

## <a name="see-also"></a>Siehe auch

- [Optimieren der Profilereinstellungen](../profiling/optimize-profiler-settings.md)