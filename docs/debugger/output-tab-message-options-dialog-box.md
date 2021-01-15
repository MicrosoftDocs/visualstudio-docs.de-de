---
title: Registerkarte „Ausgabe“, Dialogfeld „Meldungsoptionen“ | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie die Registerkarte „Ausgabe“ des Dialogfelds „Meldungsoptionen“ verwenden, um festzulegen, welche Meldungsdaten in der Ansicht „Meldungen“ angezeigt werden. Außerdem werden die verfügbaren Einstellungen beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Output
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4d965b92a30d8d8a5b998a27bea9651f8669c8f
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975081"
---
# <a name="output-tab-message-options-dialog-box"></a>Registerkarte "Ausgabe", Dialogfeld "Meldungsoptionen"
Auf der Registerkarte **Ausgabe** können Sie angeben, welche Daten aus den einzelnen Meldungen in der [Meldungsansicht](../debugger/messages-view.md) aufgelistet werden sollen. Um das [Dialogfeld „Meldungsoptionen“](../debugger/message-options-dialog-box.md) anzuzeigen, wählen Sie im Menü **Spy** die Option **Meldungen protokollieren** aus.

 Auf der Registerkarte **Ausgabe** sind folgende Einstellungen verfügbar:

 **Zeilennummern**: Zeigt die Zeilennummern an.

 **Message Nesting Level** (Meldungsschachtelungsebene): Geschachtelten Meldungen wird pro Ebene ein Punkt vorangestellt.

 **Nicht formatierte Meldungsparameter**: Zeigt die **wParam**- und **lParam**-Hexadezimalwerte an.

 **Decodierte Meldungsparameter**: Zeigt die Ergebnisse der meldungsspezifischen Decodierung der **wParam**- und **lParam**-Werte an.

 **Nicht formatierte Rückgabewerte**: Zeigt die **IResult**-Rückgabe als Hexadezimalwert an.

 **Decodierte Rückgabewerte**: Zeigt die Ergebnisse der meldungsspezifischen Decodierung des **IResult**-Rückgabewerts an.

 **Zeitpunkt der Meldungssendung**: Die seit dem Starten des Windows-Systems verstrichene Zeit (nur für gesendete Meldungen).

 **Meldungsmausposition**: Die Bildschirmkoordinaten der Maus, als die Meldung gesendet wurde (nur für gesendete Meldungen).

 **Zeilen maximal**: Beschränkt die Anzahl der Zeilen, die in der derzeit ausgewählten Meldungsansicht beibehalten werden.

 **Also Log Messages to File** (Meldungen auch in Datei protokollieren): Geben Sie eine Ausgabedatei für das Meldungsprotokoll an. Diese Ausgabedatei wird gleichzeitig mit dem Meldungsprotokollfenster geschrieben.

 **Als Voreinstellung speichern**: Speichert die vorherigen Einstellungen für neue Meldungsdatenstrom-Fenster. Diese Einstellungen werden gespeichert, wenn Sie Spy++ beenden.