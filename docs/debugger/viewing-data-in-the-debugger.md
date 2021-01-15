---
title: Erstellen benutzerdefinierter Datenansichten im Debugger | Microsoft-Dokumentation
description: In diesem Artikel werden verschiedene Methoden zum Untersuchen und Anpassen des Programmzustands im Visual Studio-Debugger vorgestellt. Dazu gehören die Fenster „Auto“ und „Überwachen“, DataTips und Schnellansichten.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5acac83a6d461f6b7301ff2bfe89d92dc78d00ee
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149910"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Erstellen benutzerdefinierter Datenansichten im Visual Studio-Debugger (C#, Visual Basic, C++)

Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger bietet viele Tools zum Überprüfen und Ändern der Programmeigenschaften. Die meisten dieser Tools funktionieren nur im Unterbrechungsmodus.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Erstellen benutzerdefinierter Datenansichten in Variablenfenstern und Datentipps

 In vielen [Debuggerfenstern](../debugger/debugger-windows.md) wie **Auto** und **Überwachen** können Sie Variablen prüfen. Sie können anpassen, wie C++-Typen, verwaltete Objekte und eigene Typen in den Variablenfenstern des Debuggers und in [Datentipps](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) angezeigt werden. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Ansichten von C++-Objekten](../debugger/create-custom-views-of-native-objects.md) und [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Erstellen benutzerdefinierter Schnellansichten

 Mit Schnellansichten können Sie den Inhalt von Objekten oder Variablen übersichtlich anzeigen. Im Visual Studio-Debugger verweist eine Schnellansicht auf die unterschiedlichen Fenster, die Sie über das Lupensymbol ![Schnellansicht-Symbol](../debugger/media/dbg-tips-visualizer-icon.png "Symbol der Schnellansicht") öffnen können. Mit HTML-Schnellansichten können Sie beispielsweise eine HTML-Zeichenfolge so anzeigen, wie ein Browser sie interpretieren und anzeigen würde. Schnellansichten sind über Datentipps und die Fenster **Überwachen**, **Auto** und **Lokal** erreichbar. Das Dialogfeld **Schnellüberwachung** bietet ebenfalls eine Schnellansicht. Weitere Informationen finden Sie unter [Create Custom Visualizers (Erstellen benutzerdefinierter Schnellansichten)](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Siehe auch

- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Befehlsfenster](../ide/reference/command-window.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
