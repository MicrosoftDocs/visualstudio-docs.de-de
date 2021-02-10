---
title: Erfassen von Ebeneninteraktionsdaten | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Informationen zur Ebenenprofilerstellung für Anwendungen mit mehreren Ebenen sammeln, die über ADO.NET-Dienste mit Datenbanken kommunizieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e2b20a403d2c56dd239ddaf81d2a32905ca4aed5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950233"
---
# <a name="collect-tier-interaction-data"></a>Erfassen von Ebeneninteraktionsdaten

Die Profilerstellung für Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten der Funktionen von Anwendungen mit mehreren Ebenen, die über ADO.NET-Dienste mit Datenbanken kommunizieren, bereit. Es werden nur Daten für synchrone Funktionsaufrufe gesammelt.

**Visual Studio-Editionen**

Profilerstellungsdaten für die Ebeneninteraktion können mit einer beliebigen Visual Studio-Edition erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in Visual Studio Enterprise angezeigt werden.

**Windows 8 und Windows Server 2012**

Um Ebeneninteraktionsdaten für Windows 8-Desktop-Apps und Windows Server 2012-Apps zu erfassen, müssen Sie die Instrumentierungsmethode verwenden. Sie können Ebeneninteraktionsdaten nicht für UWP-Apps erfassen. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Sie können Ebeneninteraktionsdaten in alle Profilerstellungsmethoden einer anderen unterstützten Version von Windows einschließen.

**Leistungs-Assistent**

Aufgrund eines Fehlers im Leistungs-Assistenten müssen Sie die Option zur Erfassung von Ebeneninteraktionsdaten einer Profilerstellung im Leistungs-Explorer hinzufügen. Sie müssen das Projekt, die ausführbare Datei oder die Website außerdem dem Zielknoten des Leistungs-Explorers hinzufügen.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>So fügen Sie einer Profilerstellung Ebeneninteraktionsdaten mithilfe der Eigenschaftenseiten der Leistungssitzung hinzu

1. Wählen Sie im Leistungs-Explorer im Kontextmenü **Eigenschaften** aus.

2. Wählen Sie die Seite **Ebeneninteraktionen** aus, und aktivieren Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren**.

3. Wählen Sie im Leistungs-Explorer den Knoten **Ziele** aus, und geben Sie das Projekt, die ausführbare Datei oder die Website an, für das/die Sie ein Profil erstellen möchten.

## <a name="see-also"></a>Weitere Informationen

[Ansicht „Ebeneninteraktionen“](../profiling/tier-interactions-view.md)
