---
title: Debuggen eines WebView-Steuerelements (UWP) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die in einer Windows-Runtime-App verwendeten WebView-Steuerelemente überprüfen und debuggen. Hierfür können Sie DOM Explorer und das JavaScript-Konsolenfenster verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: c3876befa45904d21b5a1672ca6fcc72c51bf801
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865656"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Debuggen eines WebView-Steuerelements in einer UWP-App

 Um `WebView`-Steuerelemente in einer Windows-Runtime-App zu überprüfen und zu debuggen, können Sie Visual Studio so konfigurieren, dass es den Skriptdebugger anfügt, wenn Sie Ihre App starten. Sie haben zwei Möglichkeiten für die Interaktion mit den `WebView`-Steuerelementen bei Verwendung des Debuggers:

- Öffnen Sie [DOM Explorer](../debugger/quickstart-debug-html-and-css.md) für eine `WebView`-Instanz, und prüfen Sie DOM-Elemente, untersuchen Sie CSS-Formatvorlagenprobleme und testen Sie dynamisch gerenderte Änderungen an Formatvorlagen.

- Wählen Sie die Webseite oder den `iFrame`, die in der `WebView`-Instanz angezeigt werden, als Ziel im [JavaScript-Konsolenfenster](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true), und interagieren Sie dann über Konsolenbefehle mit der Webseite. Die Konsole bietet Zugriff auf den aktuellen Skriptausführungskontext.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Anfügen des Debuggers (C#, Visual Basic, C++)

1. In Visual Studio: Fügen Sie ein `WebView`-Steuerelement an Ihre Windows-Runtime-App an.

2. Im Projektmappen-Explorer: Öffnen Sie die Eigenschaften für das Projekt, indem Sie im Kontextmenü die Option **Eigenschaften** auswählen.

3. Wählen Sie **Debuggen** aus. Wählen Sie in der Liste **Anwendungsprozesse** die Option **Skript**.

     ![Anfügen des Skriptdebuggers](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. (Optional) Für Nicht-Express-Versionen von Visual Studio: Deaktivieren Sie das Just-in-time-Debuggen (JIT), indem Sie **Extras > Optionen > Debuggen > Just-In-Time** auswählen und dann das JIT-Debuggen für Skript deaktivieren.

    > [!NOTE]
    > Indem Sie das JIT-Debuggen deaktivieren, können Sie Dialogfelder für unbehandelte Ausnahmen ausblenden, die auf einigen Webseiten auftreten. In Visual Studio Express ist das JIT-Debuggen stets deaktiviert.

5. Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Verwenden des DOM Explorers, um ein WebView-Steuerelement zu untersuchen und zu debuggen

1. (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.

2. Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.

3. Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.

4. Öffnen Sie das DOM Explorer-Fenster für das `WebView`-Steuerelement, indem Sie **Debuggen**, **Fenster**, **DOM Explorer** und dann die URL des zu untersuchenden `WebView`-Elements auswählen.

     ![Öffnen von DOM Explorer](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     Der mit dem `WebView` verknüpfte DOM Explorer erscheint als neue Registerkarte in Visual Studio.

5. Zeigen Sie Live-DOM-Elemente und CSS-Formatvorlagen an, und ändern Sie diese wie unter [Debuggen von HTML und CSS in UWP-Apps in Visual Studio](quickstart-debug-html-and-css.md) beschrieben.

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Verwenden des JavaScript-Konsolenfensters, um ein WebView-Steuerelement zu untersuchen und zu debuggen

1. (C#, Visual Basic, C++) Fügen Sie den Skriptdebugger an Ihre App an. Die Anleitung dazu finden Sie im ersten Abschnitt.

2. Fügen Sie ein `WebView`-Steuerelement an Ihre App an, wenn Sie dies noch nicht getan haben, und drücken Sie F5, um mit dem Debuggen zu beginnen.

3. Öffnen Sie das JavaScript-Konsolenfenster für das `WebView`-Steuerelement, indem Sie **Debuggen**, **Fenster**, **JavaScript-Konsole** auswählen.

     Das JavaScript-Konsolenfenster wird angezeigt.

4. Navigieren Sie zu der Seite, die die `Webview`-Steuerelemente enthält.

5. Wählen Sie im Konsolenfenster die Webseite oder einen `iFrame`, der durch das `WebView`-Steuerelement in der Liste **Ziele** angezeigt wird.

     ![Zielauswahl im JavaScript-Konsolenfenster](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > Mithilfe der Konsole können Sie jeweils mit einem einzelnen `WebView`, `iFrame`, Freigabe-Vertrag oder Web-Worker interagieren. Jedes Element erfordert eine separate Instanz des Webplattform-Hosts (WWAHost.exe). Sie können jeweils mit einem Host interagieren.

6. Zeigen Sie Variablen in Ihrer App an, und ändern Sie diese, oder verwenden Sie Konsolenbefehle. Dies wird beschrieben unter [Debuggen von JavaScript mithilfe der Konsole in Visual Studio](../debugger/quickstart-debug-javascript-using-the-console.md) und [JavaScript-Konsolenbefehle in Visual Studio](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true).

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Debug HTML and CSS (Schnellstart: Debuggen von HTML und CSS)](../debugger/quickstart-debug-html-and-css.md)