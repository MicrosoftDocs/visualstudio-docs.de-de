---
title: Dialogfeld „Optionen“
description: Hier erfahren Sie mehr über das Dialogfeld „Optionen“, dessen Layout sowie darüber, wie Visual Studio die von Ihnen ausgewählten Optionen auf Ihre Projekte und Projektmappen anwendet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abf435625cc9003dc569542e24e020e3801ec00
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189328"
---
# <a name="options-dialog-box-visual-studio"></a>Dialogfeld „Optionen“ (Visual Studio)

Mit dem Dialogfeld **Optionen** können Sie die integrierte Entwicklungsumgebung (IDE) Ihren Wünschen entsprechend konfigurieren. Sie können beispielsweise einen Standardspeicherort für Ihre Projekte festlegen, das Standardverhalten und-aussehen von Windows anpassen und Tastenkombinationen für häufig verwendete Befehle erstellen. Zudem gibt es Optionen, die für Ihre Entwicklungssprachen und -plattform spezifisch sind. Sie können über das Menü **Extras** auf die **Optionen** zugreifen.

## <a name="layout-of-the-options-dialog-box"></a>Layout des Dialogfelds „Optionen“

Das Dialogfeld **Optionen** ist in zwei Teile aufgeteilt: einen Navigationsbereich auf der linken Seite und einen Anzeigebereich rechts. Das Struktursteuerelement im Navigationsbereich enthält Ordnerknoten wie z.B. „Umgebung“, „Text-Editor“, „Projekte und Projektmappen“ und „Quellcodeverwaltung“. Erweitern Sie einen Ordnerknoten, um die Optionen, die er enthält, aufzulisten. Wenn Sie einen Knoten für eine bestimmte Seite ausgewählt haben, werden deren Optionen im Anzeigebereich angezeigt.

Die Optionen einer IDE-Funktion werden erst dann im Navigationsbereich angezeigt, wenn die Funktion in den Arbeitsspeicher geladen wird. Deshalb kann es sein, dass zu Beginn einer neuen Sitzung nicht die gleichen Optionen angezeigt werden wie am Ende der letzten. Wenn Sie ein Projekt erstellen oder einen Befehl ausführen, der eine bestimmte Anwendung verwendet, werden Knoten für wichtige Optionen dem Dialogfeld „Optionen“ hinzugefügt. Diese hinzugefügten Optionen bleiben dann solange verfügbar, wie die IDE-Funktion im Arbeitsspeicher vorhanden ist.

> [!NOTE]
> Einige Einstellungsauflistungen geben die Zahl an Seiten an, die im Navigationsbereich des Dialogfelds „Optionen“ angezeigt werden.

## <a name="how-options-are-applied"></a>So werden Optionen angewendet

Wenn Sie im Dialogfeld **Optionen** auf OK klicken, werden alle Einstellungen auf allen Seiten gespeichert. Wenn Sie auf einer beliebigen Seite auf „Abbrechen“ klicken, werden alle Änderungsanforderungen abgebrochen, auch Einstellungen, die gerade erst auf anderen **Optionsseiten** vorgenommen wurden. Einige Änderungen auf Optionsseiten, wie z.B. auf [Schriftarten und Farben, Umgebung, Dialogfeld „Optionen“](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), treten erst in Kraft, nachdem Visual Studio geschlossen und wieder geöffnet wurde.

## <a name="see-also"></a>Siehe auch

- [Anpassen des Editors](../how-to-change-text-case-in-the-editor.md)
