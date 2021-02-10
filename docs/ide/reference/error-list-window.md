---
title: Fehlerliste (Fenster)
description: Hier erfahren Sie mehr über das Fenster „Fehlerliste“ und darüber, wie Sie damit Aufgaben im Zusammenhang mit der Behebung der angezeigten Fehler ausführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: df8d9545ce8179451530e2eb30bef7f98ba365d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907546"
---
# <a name="error-list-window"></a>Fehlerliste (Fenster)

> [!NOTE]
> In der **Fehlerliste** werden Informationen zu einer bestimmten Fehlermeldung angezeigt. Sie können die Fehlernummer oder den Fehlerzeichenfolgentext im **Ausgabe**-Fenster kopieren. Drücken Sie zum Anzeigen des **Ausgabe**-Fensters **STRG**+**ALT**+**O**. Siehe [Ausgabefenster](../../ide/reference/output-window.md).

Mit dem Fenster **Fehlerliste** können Sie die folgenden Aufgaben ausführen:

- Anzeigen von Fehlern, Warnungen und Meldungen, die beim Bearbeiten und Schreiben von Code ausgegeben werden.

- Suchen nach Syntaxfehlern, die von IntelliSense erkannt werden.

- Suchen nach Bereitstellungsfehlern, bestimmten Fehlern bei statischer Analyse sowie Fehlern, die bei der Anwendung von Enterprise-Vorlagenrichtinien gefunden werden.

- Doppelklicken auf eine beliebige Fehlermeldung, um die Datei, in der das Problem aufgetreten ist, zu öffnen und zur entsprechenden Stelle zu wechseln.

- Filtern der anzuzeigenden Einträge und der Informationsspalten, die für jeden Eintrag angezeigt werden.

- Suchen nach bestimmten Begriffen und Eingrenzen der Suche auf das aktuelle Projekt oder Dokument.

Zum Anzeigen der **Fehlerliste**, wählen Sie **Ansicht** > **Fehlerliste** aus, oder drücken Sie **STRG**+ **\\** +**E**.

Sie können zum Anzeigen von verschiedenen Informationen die Registerkarten **Fehler****Warnungen** und **Nachrichten** wählen.

Zum Sortieren der Liste klicken Sie auf einen beliebigen Spaltenheader. Halten Sie die **UMSCHALT**-Taste gedrückt, und klicken Sie auf eine andere Spaltenüberschrift, um erneut nach einer zusätzlichen Spalte zu sortieren. Um auszuwählen, welche Spalten angezeigt und welche ausgeblendet werden, wählen Sie im Kontextmenü die Option **Spalten einblenden** aus. Zum Ändern der Reihenfolge, in der Spalten angezeigt werden, ziehen Sie einen beliebigen Spaltenheader nach links oder rechts.

## <a name="error-list-filters"></a>Fehlerlistenfilter

Es gibt zwei Filtertypen in beiden Dropdownfeldern, einen auf der rechten Seite der Symbolleiste und einen auf der linken Seite der Symbolleiste. Die Dropdownliste auf der linken Seite der Symbolleiste gibt den zu verwendenden Satz von Codedateien an (**Gesamte Projektmappe**, **Geöffnete Dokumente**, **Aktuelles Projekt**, **Aktuelles Dokument**).

Sie können den Suchbereich einschränken, um Gruppen von Fehlern zu analysieren und zu behandeln. Beispielsweise sollten Sie sich auf Kernfehler konzentrieren, die das Kompilieren eines Projekts verhindern. Es gibt folgende Eingrenzungsoptionen:

1. **Geöffnete Dokumente**: Zeigt Fehler, Warnungen und Meldungen für die offenen Dokumente an.

2. **Aktuelles Projekt**: Zeigt Fehler, Warnungen und Meldungen aus dem Projekt des aktuell ausgewählten Dokuments im **Editor** oder dem ausgewählten Projekt im **Projektmappen-Explorer** an.

    > [!NOTE]
    > Die gefilterte Liste von Fehlern, Warnungen und Meldungen ändert sich, wenn das Projekt des aktuell ausgewählten Dokuments sich von dem im **Projektmappen-Explorer** ausgewählten Projekt unterscheidet.

3. **Aktuelles Dokument**: Zeigt Fehler, Warnungen und Meldungen für das aktuell ausgewählte Dokument im **Editor** oder **Projektmappen-Explorer** an.

Wenn aktuell ein Filter auf das Suchergebnis angewendet ist, wird der Name des Filters in der Titelleiste **Fehlerliste** angezeigt. Die Schaltflächen **Fehler**, **Warnungen** und **Meldungen** zeigen dann die Anzahl von gefilterten Elementen an, die zusammen mit der Gesamtanzahl von Elementen angezeigt werden. Beispielsweise zeigen die Schaltflächen „x von y Fehler“ an. Wenn kein Filter angewendet wird, wird auf der Titelleiste nur „Fehlerliste“ angezeigt.

Die Liste auf der rechten Seite der Symbolleiste gibt an, ob Fehler aus dem Build (beim Buildvorgang aufgetretene Fehler) oder aus IntelliSense (vor dem Build erkannte Fehler), oder beide angezeigt werden sollen.

## <a name="search"></a>Suchen

Verwenden Sie für die Suche nach bestimmten Fehlern in der Fehlerliste das Textfeld **Fehlerliste durchsuchen** auf der rechten Seite der Symbolleiste **Fehlerliste**. Sie können in jeder sichtbaren Spalte in der Fehlerliste suchen, und die Suchergebnisse werden immer basierend auf der Spalte sortiert, die Sortierpriorität hat, und nicht basierend auf der angewendeten Abfrage oder dem angewendeten Filter. Wenn Sie die **ESC**-TASTE drücken, während sich der Fokus in der **Fehlerliste** befindet, können Sie den Suchbegriff und die gefilterten Suchergebnisse löschen. Sie können auch auf das Symbol **X** auf der rechten Seite des Textfelds klicken, um dieses zu löschen.

## <a name="save"></a>Speichern

Sie können die Fehlerliste kopieren und in einer Datei speichern. Wählen Sie die Fehler aus, die Sie kopieren möchten, klicken Sie mit der rechten Maustaste auf die Auswahl, und wählen Sie anschließend im Kontextmenü **Kopieren** aus. Sie können die Fehler dann in eine Datei einfügen. Wenn Sie die Fehler in ein Excel-Arbeitsblatt einfügen, werden die Felder als unterschiedliche Spalten angezeigt.

## <a name="ui-element-list"></a>Liste der Elemente der Benutzeroberfläche

Schweregrad

Zeigt die verschiedenen Typen des Eintrags **Fehlerliste** an (**Fehler**, **Meldung**, **Warnung**, **Warnung (aktiv)**, **Warnung (inaktiv)**.

Code

Zeigt den Fehlercode an.

BESCHREIBUNG

Zeigt den Text des Eintrags an.

Projekt

Zeigt den Namen des aktuellen Projekts an.

Datei

Zeigt den Dateinamen an.

Zeile

Zeigt die Zeile an, in der das Problem aufgetreten ist.
