---
title: Fenster (Registerkarte ), Fenstereigenschaften (Dialogfeld ) | Microsoft-Dokumentation
description: Mithilfe der Registerkarte „Fenster“ der Windows-Eigenschaften können Sie Informationen zu den Fenstern anzeigen, die zu dem ausgewählten Fenster gehören. Informationen zu den Einstellungen finden Sie in diesem Artikel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03cbcee265855c0e3ee26f75d5937315d64661a2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205397"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Registerkarte "Fenster", Dialogfeld "Fenstereigenschaften"
Mit der Registerkarte **Fenster** können Sie Informationen zu Fenstern anzeigen, die mit dem ausgewählten Fenster in Zusammenhang stehen. Verschieben Sie den Fokus auf das [Fensteransichtsfenster](../debugger/windows-view.md), um das [Dialogfeld „Fenstereigenschaften“](../debugger/window-properties-dialog-box.md) anzuzeigen. Wählen Sie einen beliebigen Fensterknoten in der Struktur aus, und klicken Sie anschließend im Menü **Ansicht** auf **Eigenschaften**.

 Auf der Registerkarte **Fenster** sind folgende Einstellungen verfügbar:

|Eingabe|Beschreibung|
|-----------|-----------------|
|**Nächstes Fenster**|Das Handle des nächsten gleichgeordneten Fensters in derselben Sequenz (Z-Reihenfolge), das in der Fensterstrukturansicht angezeigt wird („Keins“, wenn kein nächstes Fenster vorhanden ist). Wählen Sie diesen Eintrag aus, um die Eigenschaften des nächsten Fensters anzuzeigen.|
|**Vorheriges Fenster**|Das Handle des vorherigen gleichgeordneten Fensters in derselben Sequenz (Z-Reihenfolge), das in der Fensterstrukturansicht angezeigt wird („Keins“, wenn kein vorheriges Fenster vorhanden ist). Wählen Sie diesen Eintrag aus, um die Eigenschaften des vorherigen Fensters anzuzeigen.|
|**Übergeordnetes Fenster**|Das Handle des übergeordneten Fensters dieses Fensters („Keins“, wenn kein übergeordnetes Fenster vorhanden ist). Wählen Sie diesen Eintrag aus, um die Eigenschaften des übergeordneten Fensters anzuzeigen.|
|**Erstes untergeordnetes Fenster**|Das Handle des ersten untergeordneten Fensters dieses Fensters in der Sequenz (Z-Reihenfolge), das in der Fensterstrukturansicht angezeigt wird („Keins“, wenn kein vorheriges Fenster vorhanden ist). Wählen Sie diesen Wert aus, um die Eigenschaften des ersten untergeordneten Fensters anzuzeigen.|
|**Besitzerfenster**|Das Handle des Fensters, das Besitzer dieses Fensters ist. Das Hauptfenster einer Anwendung besitzt in der Regel die systemmodalen Dialogfenster, z. B. („Keins“, wenn kein Besitzer vorhanden ist). Wählen Sie diesen Eintrag aus, um die Eigenschaften des Besitzerfensters anzuzeigen.|