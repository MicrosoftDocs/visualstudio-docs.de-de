---
title: Verwenden der WPF-Strukturschnellansicht | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie die WPF-Schnellansicht (Windows Presentation Foundation) verwenden, um die visuelle Struktur eines WPF-Objekts zu untersuchen und die WPF-Abhängigkeitseigenschaften in Visual Studio anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83b11ec1c091d2a63ed89cd3089bc3b507b0db8f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149026"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Vorgehensweise: Verwenden der WPF-Strukturschnellansicht
Sie können den WPF Tree visualizer (WPF-Strukturschnellansicht) verwenden, um die visuelle Struktur eines WPF-Objekts zu untersuchen und die WPF-Abhängigkeitseigenschaften für die Objekte anzuzeigen, die in dieser Struktur enthalten sind. Weitere Informationen zu visuellen Strukturen finden Sie unter [Strukturen in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Weitere Informationen zu Abhängigkeitseigenschaften finden Sie unter [Übersicht über Abhängigkeitseigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Wenn Sie die WPF-Strukturschnellansicht öffnen, werden zwei Bereiche angezeigt: **Visuelle Struktur** auf der linken und **Eigenschaften von** _Name_ **:** _Typ_ auf der rechten Seite. Wenn Sie im Bereich **Visuelle Struktur** auf ein Objekt klicken, wird der Bereich **Eigenschaften von** _Name_ **:** _Typ_ automatisch aktualisiert, und die Eigenschaften des ausgewählten Objekts werden angezeigt.

 > [!NOTE]
 > Sie können auch den [Explorer für visuelle Livestrukturen und Liveeigenschaften](../xaml-tools/inspect-xaml-properties-while-debugging.md) verwenden, um die visuelle Struktur von WPF-Objekten zu untersuchen. Die WPF-Strukturschnellansicht ist ein veraltetes Feature und befindet sich nicht in der aktiven Entwicklung.

### <a name="to-open-the-wpf-tree-visualizer"></a>So öffnen Sie die WPF-Strukturschnellansicht

1. Klicken Sie in einem DataTip, in einem **Überwachungsfenster**, im Fenster **Auto** oder im Fenster **Lokal** neben dem Namen des WPF-Objekts auf den Pfeil neben dem Lupensymbol.

     Eine Liste von Schnellansichten wird angezeigt.

2. Klicken Sie auf **WPF Tree Visualizer** (WPF-Strukturschnellansicht).

### <a name="to-search-the-visual-tree"></a>So durchsuchen Sie die visuelle Struktur

- Geben Sie im Bereich **Visuelle Struktur** im Feld **Suchen** die Zeichenfolge ein, die Sie suchen möchten.

  Der WPF Tree visualizer (WPF-Strukturschnellansicht) zeigt sofort das erste Objekt in der visuellen Struktur an, das zur Zeichenfolge passt, die Sie eingegeben haben. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.

  - Klicken Sie auf **Weiter**, um zur nächsten Übereinstimmung innerhalb der visuellen Struktur zu wechseln.

  - Klicken Sie auf **Zurück**, um zurück zur vorherigen Übereinstimmung zu wechseln.

  - Klicken Sie auf **Löschen**, um die Suchkriterien zu löschen.

### <a name="to-search-the-properties-list"></a>So durchsuchen Sie die Eigenschaftenliste

- Geben Sie im Bereich **Eigenschaften von**: _Name_ **:** _Typ_ in das Feld **Filter** die Zeichenfolge ein, die Sie suchen möchten.

  Die WPF-Strukturschnellansicht zeigt sofort die Eigenschaften an, die zur eingegebenen Zeichenfolge passen, und in der Liste werden nur die Eigenschaften angezeigt, die zur eingegebenen Zeichenfolge passen. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.

  - Klicken Sie auf **Löschen**, um die Suchkriterien zu löschen.

### <a name="to-close-the-visualizer"></a>So schließen Sie die Schnellansicht

- Klicken Sie rechts oben im Dialogfeld auf das Symbol **Schließen**.

## <a name="see-also"></a>Siehe auch
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Strukturen in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Übersicht über Abhängigkeitseigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview)
