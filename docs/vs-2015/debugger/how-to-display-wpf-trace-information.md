---
title: 'Vorgehensweise: Anzeigen von WPF-Überwachungsinformationen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c9642902bf334ce83f95a9113059683f183c6116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537958"
---
# <a name="how-to-display-wpf-trace-information"></a>Vorgehensweise: Anzeigen von WPF-Ablaufverfolgungsinformationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] kann Debugablaufverfolgungs-Informationen in WPF-Anwendungen empfangen und diese Informationen im **Ausgabefenster** anzeigen. Zum Anzeigen von Debugablaufverfolgungs-Informationen muss die WPF-Ablaufverfolgung aktiviert werden.  
  
 Sie können WPF-Ablaufverfolgung in der Datei "App.Config" oder programmgesteuert mit der <xref:System.Diagnostics.PresentationTraceSources>-Klasse aktivieren. Eine einfachere Möglichkeit, WPF-Ablaufverfolgung zu aktivieren, besteht in der Verwendung des Fensters **Optionen**. Die WPF-Ablaufverfolgung für Webanwendungen wird nicht unterstützt.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>So aktivieren Sie WPF-Ablaufverfolgungsinformationen oder passen diese an  
  
1. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2. Öffnen Sie im Dialogfeld **Optionen** im Feld links den Knoten **Debuggen**.  
  
3. Klicken Sie unter **Debuggen** auf **Ausgabefenster**.  
  
4. Wählen Sie unter **Allgemeine Ausgabeeinstellungen** die Option **Gesamte Debugausgabe** aus.  
  
5. Suchen Sie im Feld rechts die Option **WPF-Ablaufverfolgungseinstellungen**.  
  
6. Öffnen Sie den Knoten **WPF-Ablaufverfolgungseinstellungen**.  
  
7. Klicken Sie unter **WPF-Ablaufverfolgungseinstellungen** auf die Kategorie der Einstellungen, die Sie aktivieren möchten (z.B. **Datenbindung**).  
  
     Ein Dropdownlisten-Steuerelement wird in der Spalte „Einstellungen“ neben **Datenbindung** oder der Kategorie, auf die geklickt wurde, angezeigt.  
  
8. Klicken Sie auf die Dropdownliste, und wählen Sie den Überwachungsinformationstyp aus, der angezeigt werden soll: **Alle**, **Kritisch**, **Fehler**, **Warnung**, **Informationen**, **Ausführlich** oder **Aktivitätsablaufverfolgung**.  
  
     **Kritisch** ermöglich nur die Verfolgung von kritischen Ereignissen.  
  
     **Fehler** ermöglicht die Verfolgung von kritischen und fehlerbezogenen Ereignissen.  
  
     **Warnung** ermöglicht die Verfolgung von kritischen, fehler- und warnungsbezogenen Ereignissen.  
  
     **Informationen** ermöglicht die Verfolgung von kritischen, fehler-, warnungs- und informationsbezogenen Ereignissen.  
  
     **Ausführlich** ermöglicht die Verfolgung von kritischen, warnungs- und informationsbezogenen sowie von ausführlichen Ereignissen.  
  
     **ActivityTracing** ermöglicht die Verfolgung von Ereignissen vom Typ „Beenden“, „Starten“, „Anhalten“, „Übertragen“ und „Fortsetzen“.  
  
     Weitere Informationen zur Bedeutung der Ablaufverfolgungs-Informationsebenen finden Sie unter <xref:System.Diagnostics.SourceLevels>.  
  
9. Klicken Sie auf **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>So deaktivieren Sie WPF-Ablaufverfolgungsinformationen  
  
1. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2. Öffnen Sie im Dialogfeld **Optionen** im Feld links den Knoten **Debuggen**.  
  
3. Klicken Sie unter **Debuggen** auf **Ausgabefenster**.  
  
4. Suchen Sie im Feld rechts die Option **WPF-Ablaufverfolgungseinstellungen**.  
  
5. Öffnen Sie den Knoten **WPF-Ablaufverfolgungseinstellungen**.  
  
6. Klicken Sie unter **WPF-Ablaufverfolgungseinstellungen** auf die Kategorie der Einstellungen, die Sie aktivieren möchten (z.B. **Datenbindung**).  
  
     Ein Dropdownlisten-Steuerelement wird in der Spalte „Einstellungen“ neben **Datenbindung** oder der Kategorie, auf die geklickt wurde, angezeigt.  
  
7. Klicken Sie auf die Dropdownliste, und wählen Sie **Aus** aus.  
  
8. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von WPF](../debugger/debugging-wpf.md)
