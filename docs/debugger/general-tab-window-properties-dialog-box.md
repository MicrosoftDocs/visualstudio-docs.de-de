---
title: Registerkarte „Allgemein“, Dialogfeld „Fenstereigenschaften“ | Microsoft-Dokumentation
description: Sehen Sie sich die Registerkarte „Allgemein“ an, um Informationen zu einem Fenster zu erhalten, einschließlich der Beschriftung, des Handles, des Rechtecks, des Anwendungsinstanzhandles, des Menühandles und der Benutzerdaten.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1aa19ad99629f5106ee89876f347dfafd7520d26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870505"
---
# <a name="general-tab-window-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Fenstereigenschaften"
Auf der Registerkarte **Allgemein** können Sie Informationen zum ausgewählten Fenster anzeigen. Verschieben Sie den Fokus auf das [Fensteransichtsfenster](../debugger/windows-view.md), um das [Dialogfeld „Fenstereigenschaften“](../debugger/window-properties-dialog-box.md) anzuzeigen. Wählen Sie einen beliebigen Fensterknoten in der Struktur aus, und klicken Sie anschließend im Menü **Ansicht** auf **Eigenschaften**.

 Auf der Registerkarte **Allgemein** sind folgende Einstellungen verfügbar:

|Eingabe|Beschreibung|
|-----------|-----------------|
|**Fensterbeschriftung**|Der Text in der Fensterbeschriftung oder Text in einem Fenster, wenn es sich um ein Steuerelement handelt.|
|**Fensterhandle**|Die eindeutige ID dieses Fensters. Die Nummern von Fensterhandles werden wiederverwendet. Sie identifizieren ein Fenster nur während dessen Lebensdauer.|
|**Fensterprozedur**|Die virtuelle Adresse der Fensterprozedurfunktion für das Fenster. Dieses Feld gibt auch an, ob es sich bei diesem Fenster um ein Unicode-Fenster handelt und ob es ein untergeordnetes Fenster ist.|
|**Rechteck**|Das umgebende Rechteck für das Fenster. Die Größe des Rechtecks wird ebenfalls angezeigt. Die Einheiten sind Pixel in Bildschirmkoordinaten.|
|**Wiederherg. Rechteck**|Das umgebende Rechteck für das wiederhergestellte Fenster. Die Größe des Rechtecks wird ebenfalls angezeigt. „Wiederherg. Rechteck“ unterscheidet sich von „Rechteck“ nur dann, wenn das Fenster maximiert oder minimiert ist. Die Einheiten sind Pixel in Bildschirmkoordinaten.|
|**Clientrechteck**|Das umgebende Rechteck für den Clientbereich des Fensters. Die Größe des Rechtecks wird ebenfalls angezeigt. Die Einheiten sind Pixel relativ zur oberen linken Ecke des Fensterclientbereichs.|
|**Instanzhandle**|Ein Instanzhandle der Anwendung. Instanzhandles sind nicht eindeutig.|
|**„Steuerelement-ID“ oder „Menühandle“**|Wenn das angezeigte Fenster ein untergeordnetes Fenster ist, wird die Bezeichnung „Steuerelement-ID“ angezeigt. „Steuerelement-ID“ ist eine ganze Zahl, die die Steuerelement-ID des untergeordneten Fensters angibt. Wenn das angezeigte Fenster kein untergeordnetes Fenster ist, wird die Bezeichnung „Menühandle“ angezeigt. „Menühandle“ ist eine ganze Zahl, die das Handle des Menüs angibt, das dem Fenster zugeordnet ist.|
|**Benutzerdaten**|Anwendungsspezifische Daten, die mit der Fensterstruktur verknüpft sind.|
|**Fensterbytes**|Die Anzahl zusätzlicher Bytes, die dem Fenster zugeordnet sind. Die Bedeutung dieser Bytes wird von der Anwendung bestimmt. Erweitern Sie das Listenfeld, um die Bytewerte im DWORD-Format anzuzeigen.|