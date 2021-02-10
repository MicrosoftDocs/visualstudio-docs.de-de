---
title: Ausgabefenster
description: Hier erfahren Sie mehr über das Fenster „Ausgabe“ sowie darüber, wie dort Statusmeldungen für verschiedene Features in der IDE angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0bdbaf79a3700a1ba1c0574e345093af25608e39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932045"
---
# <a name="output-window"></a>Ausgabefenster

Das **Ausgabefenster** zeigt die Statusmeldungen für verschiedene Features in der integrierten Entwicklungsumgebung (IDE) an. Klicken Sie auf der Menüleiste auf **Ansicht** > **Ausgabe**, oder drücken Sie **STRG**+**ALT**+**O**, um das **Ausgabefenster** zu öffnen.

## <a name="toolbar"></a>Symbolleiste

Folgende Steuerelemente werden in der Symbolleiste des **Ausgabefensters** angezeigt.

### <a name="show-output-from"></a>Ausgabe anzeigen von

Zeigt einen oder mehrere Ausgabebereiche zur Ansicht an. Je nachdem, welche Tools in der IDE Benutzermeldungen im Fenster **Ausgabe** ausgegeben haben, stehen mehrere Informationsbereiche zur Verfügung.

### <a name="find-message-in-code"></a>Suchen der Meldung im Code

Verschiebt die Einfügemarke im Code-Editor in die Zeile, die den ausgewählten Buildfehler enthält.

### <a name="go-to-previous-message"></a>Gehe zur vorherigen Meldung

Verschiebt den Fokus im Fenster **Ausgabe** zum vorherigen Buildfehler und positioniert die Einfügemarke im Code-Editor in der Zeile mit dem Buildfehler.

### <a name="go-to-next-message"></a>Gehe zur nächsten Meldung

Verschiebt den Fokus im Fenster **Ausgabe** zum nächsten Buildfehler und positioniert die Einfügemarke im Code-Editor in der Zeile mit dem Buildfehler.

### <a name="clear-all"></a>Alle löschen

Löscht den gesamten Text aus dem Bereich **Ausgabe**.

### <a name="toggle-word-wrap"></a>Umschalten des Zeilenumbruchs

Schaltet die Zeilenumbruchfunktion im Bereich **Ausgabe** ein und aus. Wenn die Zeilenumbruchfunktion aktiviert ist, wird Text in längeren Einträgen, der über den Anzeigebereich hinausgeht, in der nächsten Zeile angezeigt.

## <a name="output-pane"></a>Ausgabebereich

In dem in der Liste **Ausgabe anzeigen von** ausgewählten Bereich **Ausgabe** werden Ausgabedaten aus der angegebenen Quelle angezeigt.

## <a name="route-messages-to-the-output-window"></a>Weiterleiten von Meldungen an das Ausgabefenster

Wählen Sie im Dialogfeld **Optionen** auf der Seite **Projekte und Projektmappen** > **Allgemein** die Option **Ausgabefenster bei Buildbeginn anzeigen** aus, um das **Ausgabefenster** beim Erstellen eines Projekts anzuzeigen. Klicken Sie dann, während eine Codedatei zur Bearbeitung geöffnet ist, auf der Symbolleiste des Fensters **Ausgabe** auf **Gehe zur nächsten Meldung** oder **Gehe zur vorherigen Meldung**, um Einträge im Bereich **Ausgabe** auszuwählen. Währenddessen wird die Einfügemarke im Code-Editor in die Codezeile verschoben, in der das jeweilige Problem auftritt.

Bei bestimmten im [Befehlsfenster](../../ide/reference/command-window.md) aufgerufenen Features und Befehlen der IDE erfolgt die Ausgabe im **Ausgabefenster**. Ausgaben von externen Tools, z.B. *BAT*- und *COM*-Dateien, die normalerweise im Eingabeaufforderungsfenster angezeigt werden, werden an einen **Ausgabebereich** geroutet, wenn Sie die Option **Ausgabefenster verwenden** in [Verwalten externer Tools](../../ide/managing-external-tools.md) auswählen. Viele weitere Meldungstypen können ebenfalls in **Ausgabe**-Bereichen angezeigt werden. Wenn beispielsweise Transact-SQL-Syntax in einer gespeicherten Prozedur anhand einer Zieldatenbank überprüft wird, werden die Ergebnisse im Fenster **Ausgabe** angezeigt.

Sie können auch eigene Anwendungen so programmieren, dass sie Diagnosemeldungen zur Laufzeit in einen **Ausgabe**-Bereich ausgeben. Verwenden Sie dazu Member der <xref:System.Diagnostics.Debug>-Klasse oder der <xref:System.Diagnostics.Trace>-Klasse im <xref:System.Diagnostics>-Namespace der .NET-API. Wenn Sie Debugkonfigurationen von einer Projektmappe oder einem Projekt erstellen, wird die Ausgabe von Membern der <xref:System.Diagnostics.Debug>-Klasse angezeigt. Beim Erstellen einer Debug- oder Releasekonfiguration wird die Ausgabe von Membern der <xref:System.Diagnostics.Trace>-Klasse angezeigt. Weitere Informationen finden Sie unter [Diagnosemeldungen im Ausgabefenster](../../debugger/diagnostic-messages-in-the-output-window.md).

In C++ können Sie benutzerdefinierte Buildschritte und Buildereignisse erstellen, deren Warnungen und Fehler im Bereich **Ausgabe** angezeigt und gezählt werden. Durch Drücken von **F1** in einer Ausgabezeile wird ein entsprechendes Hilfethema angezeigt. Weitere Informationen finden Sie unter [Formatieren der Ausgabe eines benutzerdefinierten Buildschritts](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Scrollverhalten

Wenn Sie den automatischen Bildlauf im **Ausgabefenster** verwenden und dann navigieren, indem Sie die Maus oder Pfeiltasten verwenden, wird der automatische Bildlauf beendet. Wenn Sie den automatischen Bildlauf fortsetzen möchten, drücken Sie **STRG**+**ENDE**.

## <a name="see-also"></a>Weitere Informationen

- [Diagnosemeldungen im Ausgabefenster](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Vorgehensweise: Steuern des Ausgabefensters](/previous-versions/ht6z4e28(v=vs.140))
- [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)
- [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)
- [Übersicht über die Klassenbibliothek](/dotnet/standard/class-library-overview)