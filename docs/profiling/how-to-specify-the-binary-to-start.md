---
title: Angeben der zu startenden Binärdatei | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Informationen im Dialogfeld <Target>-Eigenschaftenseiten eingeben, um die Profilerstellung für Binärdateien wie DLLs durchzuführen.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 715c92a26ae33a4e909ec737c866be1cdc15251e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721839"
---
# <a name="how-to-specify-the-binary-to-start"></a>Vorgehensweise: Angeben der zu startenden Binärdatei

Sie müssen Informationen im Dialogfeld **\<Target>-Eigenschaftenseiten** eingeben, um die Profilerstellung für Binärdateien durchzuführen. Diese Informationen geben an, wo das DLL-Projekt die aufrufende Anwendung finden kann.

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Zielbinärdatei und anschließend auf **Eigenschaften**.

2. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf die **Start**-Eigenschaften.

3. Wählen Sie das Kontrollkästchen **Projekteigenschaften überschreiben** aus.

4. Geben Sie m Textfeld **Zu startende ausführbare Datei** den Dateispeicherort an.

5. Geben Sie im **Argumente**-Textfeld Argumente an, die zum Starten der Anwendung erforderlich sind.

6. Geben Sie im **Arbeitsverzeichnis** den Speicherort für das Verzeichnis an.

7. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
