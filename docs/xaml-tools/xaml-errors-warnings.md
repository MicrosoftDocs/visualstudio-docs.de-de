---
title: XAML-Fehler und -Warnungen
description: Erfahren Sie mehr über XAML-Fehler und-Warnungen in Visual Studio, einschließlich der Kategorisierung von Fehlern, Informationen zum Abrufen von Fehlerinformationen und zum Auffinden von Optionen für deren Behebung.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a68273f4fbb2f66986c18c692b91b6e1829a4c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049224"
---
# <a name="xaml-errors-and-warnings"></a>XAML-Fehler und -Warnungen

Bei der Erstellung von XAML analysiert Visual Studio den Code während Sie tippen. Wenn ein Fehler erkannt wird, erscheint eine Wellenlinie in der Codezeile. Wenn Sie mit der Maus auf die Wellenlinie zeigen, erhalten Sie Informationen zu dem Fehler bzw. der Warnung. Bei einigen Fehlern und Warnungen wird eine Glühbirne für schnell Aktionen angezeigt, und Sie verwenden die **STRG** -Taste + **.** werden die Optionen zum Beheben des Problems angezeigt.

## <a name="error-types"></a>Fehlertypen

Im Hintergrund analysieren mehrere Tools gleichzeitig die XAML. XAML-Fehler werden in einen der folgenden drei Typen unterteilt, je nach Tool, mit dem der Fehler erkannt wurde:

|**Fehler erkannt von**|**Fehlercodeformat**|**Visual Studio-Version**|
| - |-----------------| - |
|XAML-Sprachdienst (XAML-Editor)|XLSxxxx| Alle Versionen |
|XAML-Designer|XDGxxxx| Alle Versionen | 
|XAML – Bearbeiten und Fortfahren|XECxxxx| Visual Studio 2019 Version 16,1 oder früher |
|Neuladen von XAML im laufenden Betrieb | Xhrxxxx | Visual Studio 2019 Version 16,2 oder höher |

Weitere Informationen zum erneuten Branding der XAML-Bearbeitung & als XAML-Hot-Upload fortsetzen, finden Sie in den Anmerkungen zu dieser [Version](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling) .

> [!Note]
> Nicht alle Fehler oder Warnungen verfügen über einen entsprechenden Code. Solche Fehler sind in der Regel Fehler des XAML-Designers.

## <a name="suppress-xaml-designer-errors"></a>Unterdrücken von XAML-Designer-Fehlern

Öffnen Sie das Dialogfeld **Optionen** , indem Sie **Extras > Optionen** und dann **Text-Editor > XAML > Sonstiges** auswählen.

Deaktivieren Sie das Kontrollkästchen **Show errors detected by the XAML designer** (Fehler anzeigen, die vom XAML-Designer erkannt wurden).

![Unterdrücken von XAML-Designer-Fehlern](media/suppress_xaml_designer_errors.png)
