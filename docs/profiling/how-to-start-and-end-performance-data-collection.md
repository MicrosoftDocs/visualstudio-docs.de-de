---
title: Starten und Beenden der Sammlung von Leistungsdaten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4d1f22a09070aea8d2a63979c9d6d1bd267269cf
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851111"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Vorgehensweise: Starten und Beenden der Sammlung von Leistungsdaten
Sie müssen die Zielbinärdatei, für die Sie ein Profil erstellen möchten, vor Beginn der Profilerstellung zur Leistungssitzung hinzufügen. Klicken Sie mit der rechten Maustaste auf **Ziele** im **Leistungs-Explorer** und anschließend auf **Zielbinärdatei hinzufügen**, um ein Ziel hinzuzufügen. Wählen Sie im Dialogfeld **Zielbinärdatei hinzufügen** den Dateinamen aus und klicken Sie anschließend auf **Öffnen**. Es wird eine neue Binärdatei hinzugefügt.

### <a name="to-start-profiling"></a>So starten Sie die Profilerstellung

1. Klicken Sie mit der rechten Maustaste auf den Namen der Leistungssitzung im Fenster **Leistungs-Explorer** und wählen Sie eine der folgenden Optionen:

    - **Mit Profilerstellung starten** – die Anwendung wird gestartet und beginnt sofort mit der Profilerstellung.

    - **Mit angehaltener Profilerstellung starten** – die Anwendung wird gestartet, aber beginnt nicht mit der Profilerstellung. Sie können die Profilerstellung starten, indem Sie **Auflistung wiederaufnehmen** im Fenster **Steuerung der Datensammlung** auswählen. Weitere Informationen finden Sie unter [Vorgehensweise: Anhalten und Fortsetzen der Sammlung von Leistungsdaten](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>So beenden Sie die Profilerstellung

- Die bevorzugte Methode zum Beenden einer Profilerstellungssitzung ist das Beenden der Anwendung. Klicken Sie auf der Symbolleiste **Leistungs-Explorer** auf **Stop**, um die Profilerstellung sofort zu beenden.

## <a name="see-also"></a>Siehe auch
- [Steuerung der Datensammlung](../profiling/controlling-data-collection.md)
- [How to: Anhalten und Fortsetzen der Sammlung von Leistungsdaten](../profiling/how-to-pause-and-resume-performance-data-collection.md)
