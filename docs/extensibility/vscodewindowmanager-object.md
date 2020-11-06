---
title: Vscoabwindowmanager-Objekt | Microsoft-Dokumentation
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
ms.openlocfilehash: e88885d339e55b7c3df1312b4a72c59d2959bbcc
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414344"
---
# <a name="vscodewindowmanager-object"></a>Vscoabwindowmanager-Objekt

Der Sprachdienst implementiert den Code Fenster-Manager und ist für die Verwaltung von Zusatzelementen zuständig (z. b. die Dropdown Leiste). Weitere Informationen finden Sie unter [Anpassen von Code Fenstern mit der Legacy-API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

In der folgenden Tabelle werden die Schnittstellen im- `VSCodeWindowManager` Objekt angezeigt.

|Schnittstelle|Beschreibung|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Ermöglicht das Hinzufügen oder Entfernen von Zusatzelemente (z. b. Dropdown leisten) zu einem Code Fenster.|