---
title: Serialisieren von Symbolinformationen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Symbole serialisieren können, die Sie benötigen, um Ihre Anwendung zu analysieren, und wie die Symbolserialisierung Symbole zur VSP-Datei hinzufügt.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b7cdfa6e64380c966b62d6691f73719a3034e2d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722086"
---
# <a name="how-to-serialize-symbol-information"></a>Vorgehensweise: Serialisieren von Symbolinformationen
Sie können Symbole serialisieren, die zum Analysieren Ihrer Anwendung erforderlich sind. Die Serialisierung von Symbolen fügt Symbole in die *VSP-Datei* ein. Durch das Einfügen von Symbolinformationen in die *VSP-Datei* können andere Personen einen Leistungsbericht analysieren, ohne Zugriff auf die Originalsymbole zu haben. Wenn Symbole nicht serialisiert werden, müssen die instrumentierte *EXE-* und *PDB-Dateien* zum Analysieren der *VSP-Datei* vorhanden sein.

### <a name="to-automatically-serialize-symbol-information"></a>So serialisieren Sie automatisch Symbolinformationen

1. Klicken Sie im Menü **Extras** auf **Optionen**.

     Das Dialogfeld **Optionen** wird angezeigt.

2. Klicken Sie auf **Leistungstools**.

3. Wählen Sie unter **Allgemeine Einstellungen** **Symbolinformationen automatisch serialisieren** aus.

## <a name="see-also"></a>Siehe auch
- [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
- [How to: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)
- [How to: Speichern von analysierten Berichten](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
