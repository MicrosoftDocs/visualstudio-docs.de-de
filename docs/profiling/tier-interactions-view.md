---
title: Ansicht „Ebeneninteraktionen“ | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Profilerstellung für die Ebeneninteraktion. Diese bietet weitere Informationen zu den Ausführungszeiten in Funktionen von Anwendungen mit mehreren Ebenen, die mit Datenbanken kommunizieren.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9021f814f093151c6d65beaececc0fa99a662d44
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722515"
---
# <a name="tier-interactions-view"></a>Ebeneninteraktionen (Ansicht)

Die Profilerstellung für die Ebeneninteraktion bietet weitere Informationen zu den Ausführungszeiten in Funktionen von Anwendungen mit mehreren Ebenen, die über [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] mit Datenbanken kommunizieren. Es werden nur Daten für synchrone Funktionsaufrufe gesammelt.

**Anforderungen**

- Visual Studio Enterprise

Die Ansicht „Ebeneninteraktionen“ zeigt Ebeneninteraktionsdaten in zwei Bereichen an:

- Der Masterbereich ist eine hierarchische Struktur. Die oberste Zeile enthält aggregierte Daten für die Datenbankverbindungen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Seite oder eines Prozesses. Untergeordnete Knoten enthalten aggregierte Daten für die Datenbankverbindungen des übergeordneten Elements.

- Wenn Sie im Masterbereich auf einen Datenbankaufrufknoten klicken, werden Daten für die Instanz des Datenbankaufrufs im Detailbereich angezeigt.

  Die Zeit wird in Millisekunden oder in CPU-Takten angezeigt. Um die angezeigte Zeiteinheit zu ändern, klicken Sie auf das Menü **Extras**, dann auf **Optionen**, und wählen Sie eine der Optionen für **Uhrzeitwerte anzeigen in**.

## <a name="master-pane"></a>Masterbereich

|Spalte|Beschreibung|
|------------|-----------------|
|**Name**|– Bei einer Zeile der obersten Ebene ist es der Name des profilierten Prozesses oder der Webseite.<br />– Bei einer Datenbankverbindungszeile ist dies der Name des Servers, der die Datenbank hostet.|
|**Datenbank**|Der Name der Datenbank (nur Datenbankverbindungszeilen).|
|**Anzahl**|Die Gesamtanzahl der Anforderungen, die vom Prozess, der Webseite oder der Datenbankverbindung generiert werden.|
|**Verstrichene Zeit insgesamt**|Die Gesamtzeit, die für die Ausführung einer Anforderung vom Prozess, der Webseite oder der Datenbankverbindung aufgewendet wurde.|
|**Maximal verstrichene Zeit**|Die maximale Zeit, die für die Ausführung einer Anforderung vom Prozess, der Webseite oder der Datenbankverbindung aufgewendet wurde.|
|**Minimal verstrichene Zeit**|Die minimale Zeit, die für die Ausführung einer Anforderung vom Prozess, der Webseite oder der Datenbankverbindung aufgewendet wurde.|
|**Durchschnittlich abgelaufene Zeit**|Die durchschnittliche Zeit, die für die Ausführung einer Anforderung vom Prozess, einer Webseite oder der Datenbankverbindung aufgewendet wurde.|

## <a name="database-connection-details-pane"></a>Detailbereich für die Datenbankverbindung

|Spalte|Beschreibung|
|------------|-----------------|
|**Befehlstext**|Die SQL-Abfrage der Anforderung.|
|**Abfrageanzahl**|Die Anzahl, wie oft die Abfrage ausgeführt wurde.|
|**Verstrichene Zeit insgesamt**|Die Gesamtzeit, die für das Ausführen der Instanzen der Abfrage aufgewendet wurde.|
|**Maximal verstrichene Zeit**|Die maximale Zeit, die für das Ausführen einer Instanz der Abfrage aufgewendet wurde.|
|**Minimal verstrichene Zeit**|Die minimale Zeit, die für das Ausführen einer Instanz der Abfrage aufgewendet wurde.|
|**Durchschnittlich abgelaufene Zeit**|Die durchschnittliche Zeit, die für das Ausführen einer Instanz der Abfrage aufgewendet wurde.|
