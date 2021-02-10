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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 575a55ae654ada9774abed510d66b94e4ce9d271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899530"
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
