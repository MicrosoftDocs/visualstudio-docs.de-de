---
title: Vscoabwindowmanager-Objekt | Microsoft-Dokumentation
description: Erfahren Sie mehr über das vscoabwindowmanager-Objekt, das für die Verwaltung von Zusatzelementen zuständig ist, z. b. die Dropdown Leiste.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5c602a1cf46382e5a8b5c688501b2406e4a6d0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863995"
---
# <a name="vscodewindowmanager-object"></a>Vscoabwindowmanager-Objekt

Der Sprachdienst implementiert den Code Fenster-Manager und ist für die Verwaltung von Zusatzelementen zuständig (z. b. die Dropdown Leiste). Weitere Informationen finden Sie unter [Anpassen von Code Fenstern mit der Legacy-API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

In der folgenden Tabelle werden die Schnittstellen im- `VSCodeWindowManager` Objekt angezeigt.

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Ermöglicht das Hinzufügen oder Entfernen von Zusatzelemente (z. b. Dropdown leisten) zu einem Code Fenster.|