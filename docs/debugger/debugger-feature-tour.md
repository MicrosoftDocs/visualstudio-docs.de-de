---
title: Erster Einblick in den Debugger
description: Erste Schritte beim Debuggen von Anwendungen mithilfe des Visual Studio-Debuggers
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6d451735042374f0e3c6fb2154cd54520a069fc
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761432"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Ein erster Blick auf den Visual Studio-Debugger

Dieser Artikel stellt eine Einführung in die Debuggertools dar, die in Visual Studio enthalten sind. Wenn Sie *Ihre App in Visual Studio debuggen*, bedeutet dies in der Regel, dass Sie Ihre Anwendung mit dem angefügten Debugger (also im Debugmodus) ausführen. Wenn Sie dies machen, bietet der Debugger viele Möglichkeiten zum Ermitteln des Status Ihres Codes während der Ausführung. Sie können Ihren Code schrittweise durchlaufen und die Werte prüfen, die in Variablen gespeichert sind, Sie können die Überwachung von Variablen festlegen, um zu sehen, wenn sich Werte ändern, und Sie können unter anderem den Ausführungspfad Ihres Codes prüfen. Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) lesen, bevor Sie diesen Artikel durchgehen.

Die hier beschriebenen Features gelten für C#, C++, Visual Basic, JavaScript und andere von Visual Studio unterstützten Programmiersprachen (sofern nicht anderweitig angegeben).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Breakpoints und Starten des Debuggers

Sie müssen Ihre App mit dem an den App-Prozess angefügten Debugger starten, um diese zu debuggen. Am häufigsten wird hierfür die Taste **F5** (alternativ: **Debuggen > Debuggen starten**) verwendet. Bisher haben Sie jedoch wahrscheinlich noch keine Breakpoints für die Untersuchung Ihres App-Codes festgelegt, deshalb werden Sie dies tun, bevor Sie mit dem Debuggen beginnen. Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

Wenn Sie eine Datei im Code-Editor geöffnet haben, können Sie einen Breakpoint festlegen, indem Sie auf den Rand links neben einer Codezeile klicken.

![Haltepunkt festlegen](../debugger/media/dbg-tour-set-a-breakpoint.gif "Haltepunkt festlegen")

Drücken Sie die Taste **F5** (**Debuggen > Debuggen starten**), oder klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Debuggen starten**![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten"). Der Debugger wird anschließend bis zum ersten Haltepunkt ausgeführt. Wenn die App noch nicht ausgeführt wird, kann der Debugger durch Drücken der Taste F5 gestartet werden und hält am ersten Breakpoint an.

Breakpoints sind eine nützliche Funktion, wenn Ihnen die Codezeile oder der Codeabschnitt bekannt ist, die bzw. den Sie genauer untersuchen möchten.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Navigieren durch Code im Debugger mithilfe von Schrittbefehlen

Für die meisten Befehle gibt es Tastenkombinationen, da Sie mit diesen schneller durch den Code Ihrer App navigieren können. (Die entsprechenden Befehle, z.B. Menübefehle, werden in Klammern angegeben.)

Drücken Sie **F11** (**Debuggen > Einzelschritt**), um Ihre App mit angefügtem Debugger zu starten. Durch Drücken der Taste F11 wird der Befehl **Einzelschritt** ausgeführt, und die App wird Anweisung für Anweisung ausgeführt. Wenn Sie die App mit F11 starten, hält der Debugger bei der ersten Anweisung an, die ausgeführt wird.

![Schrittweise ausführen (F11)](../debugger/media/dbg-tour-f11.png "Schrittweise ausführen (F11)")

Der gelbe Pfeil stellt die Anweisung dar, an der der Debugger angehalten hat. An der gleichen Stelle wird auch die Ausführung der App unterbrochen (diese Anweisung wurde noch nicht ausgeführt).

Das Drücken der Taste F11 bietet eine gute Möglichkeit, den Ausführungsablauf am ausführlichsten zu überprüfen. (Es werden auch einige andere Optionen vorgestellt, mit denen Sie den Code schneller durchlaufen können.) Standardmäßig überspringt der Debugger Nichtbenutzercode (weitere Einzelheiten hierzu finden Sie unter [Nur eigenen Code](../debugger/just-my-code.md)).

>[!NOTE]
> In verwaltetem Code wird ein Dialogfeld angezeigt, in dem Sie auswählen können, ob Sie benachrichtigt werden, wenn Eigenschaften und Operatoren automatisch übersprungen werden (Standardverhalten). Wenn Sie diese Einstellung im Nachhinein ändern möchten, deaktivieren Sie die Einstellung **Eigenschaften und Operatoren überspringen** im Menü **Extras > Optionen** unter **Debuggen**.

## <a name="step-over-code-to-skip-functions"></a>Prozedurschritt im Code zum Überspringen von Funktionen

In einer Codezeile, die eine Funktion oder einen Methodenaufruf enthält, können Sie **F10** (**Debuggen > Prozedurschritt**) anstelle von F11 verwenden.

Durch Drücken der Taste F10 fährt der Debugger in Ihrem App-Code fort, ohne dass Funktionen oder Methoden schrittweise ausgeführt werden (der Code wird immer noch ausgeführt). Sie können Code überspringen, der für Sie nicht relevant ist, indem Sie F10 drücken. Dadurch gelangen Sie schnell zum relevanten Code.

## <a name="step-into-a-property"></a>Einzelschritt zu einer Eigenschaft

Wie zuvor erwähnt überspringt der Debugger standardmäßig verwaltete Eigenschaften und Felder. Mit dem Befehl **Einzelschritt in Angabe** können Sie dieses Verhalten jedoch außer Kraft setzen.

Klicken Sie mit der rechten Maustaste auf eine Eigenschaft oder ein Feld, klicken Sie auf **Einzelschritt in Angabe**, und wählen Sie eine der verfügbaren Optionen aus.

![Screenshot des Visual Studio-Debuggers mit einer hervorgehobenen Codezeile. Die Option „Einzelschritt in Angabe“ ist im Kontextmenü ausgewählt sowie die Path.set-Methode.](../debugger/media/dbg-tour-step-into-specific.png)

In diesem Beispiel springt **Einzelschritt in Angabe** zum Code für `Path.set`.

![Screenshot des Visual Studio-Debuggers mit dem Code für Path.set. Die Klammern, die die set-Funktion umschließen, sind gelb hervorgehoben.](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Schnelles Ausführen bis zu einer bestimmten Stelle im Code mithilfe der Maus

Zeigen Sie auf eine Codezeile, während der Debugger ausgeführt wird, bis die Schaltfläche **Ausführung bis Klick** (Ausführung bis hier ausführen) ![Screenshot der Schaltfläche „Ausführung bis Klick“ des Visual Studio-Debuggers. Die Schaltfläche zeigt an, dass die Ausführung bis zu der Zeile ausgeführt werden soll, in der die Schaltfläche platziert ist.](../debugger/media/dbg-tour-run-to-click.png) links davon angezeigt wird.

![Screenshot des Visual Studio-Debuggers mit der Schaltfläche „Ausführen bis Klick“, die gerade links von dem Aufruf der Update-Funktion angezeigt wird.](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> Die Schaltfläche für die Aktion **Ausführung bis Klick** (Ausführung bis hier ausführen) ist ab [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] verfügbar.

Klicken Sie auf die Schaltfläche **Ausführung bis Klick** (Ausführung bis hier ausführen). Der Debugger wechselt zu der Codezeile, auf die Sie geklickt haben.

Die Verwendung dieser Schaltfläche ist mit dem Festlegen eines temporären Breakpoints vergleichbar. Dieser Befehl ist zudem nützlich, wenn Sie eine sichtbare Region Ihres App-Codes schnell durchlaufen möchten. Sie können **Ausführung bis Klick** in jeder geöffneten Datei verwenden.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Fortsetzen des Debuggers außerhalb der aktuellen Funktion

In einigen Fällen möchten Sie Ihre Debugsitzung fortsetzen, der Debugger soll die aktuelle Funktion jedoch durchlaufen.

Drücken Sie **UMSCHALT + F11** (alternativ: **Debuggen > Ausführen bis Rücksprung**).

Mit diesem Befehl wird die Ausführung der App so lange fortgesetzt (und der Debugger weiter ausgeführt), bis die aktuelle Funktion wieder ausgeführt wird.

## <a name="run-to-cursor"></a>Ausführen bis Cursor

Wenn Sie Code bearbeiten (anstatt ihn im Debugger anzuhalten), klicken Sie mit der rechten Maustaste auf eine Codezeile in Ihrer App, und wählen Sie dann **Ausführen bis Cursor** aus. Dadurch wird das Debuggen gestartet und ein temporärer Breakpoint in der aktuellen Codezeile festgelegt.

![Ausführen bis Cursor](../debugger/media/dbg-tour-run-to-cursor.png "Ausführen bis Cursor")

Wenn Sie Breakpoints festgelegt haben, hält der Debugger am ersten Breakpoint an, den er erreicht.

Drücken Sie **F5**, bis Sie die Codezeile erreichen, für die Sie **Ausführen bis Cursor** festgelegt haben.

Dieser Befehl ist nützlich, wenn Sie Code bearbeiten und schnell einen temporären Breakpoint festlegen möchten, während gleichzeitig der Debugger gestartet wird.

> [!NOTE]
> Sie können **Ausführen bis Cursor** während des Debuggens im Fenster **Aufrufliste** verwenden.

## <a name="restart-your-app-quickly"></a>Schnelles Neustarten Ihrer App

Klicken Sie in der Symbolleiste „Debuggen“ auf **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "App neu starten") (**STRG + UMSCHALT + F5**).

Durch das Klicken auf **Neu starten** sparen Sie im Vergleich zum Beenden der App und dem erneuten Starten des Debuggers Zeit. Der Debugger hält am ersten Breakpoint an, der bei der Codeausführung erreicht wird.

Wenn Sie den Debugger beenden und zum Code-Editor zurückgehen möchten, können Sie anstelle von **Neu starten** auf die rote Schaltfläche „Beenden“ ![Debuggen beenden](../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") drücken.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Bearbeiten des Codes und Fortsetzen des Debuggens (C#, Visual Basic, C++, YAML)

In den meisten Sprachen, die von Visual Studio unterstützt werden, können Sie den Code während einer Debugsitzung bearbeiten und das Debuggen fortsetzen. Wenn Sie dieses Feature verwenden möchten, klicken Sie mit dem Cursor auf den Code, während dieser im Debugger angehalten wurde, und bearbeiten Sie diesen. Drücken Sie **F5**, **F10** oder **F11**, um das Debuggen fortzusetzen.

![Bearbeiten und Fortsetzen des Debuggens](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Weitere Informationen zur Verwendung des Features finden Sie unter [Bearbeiten und Fortsetzen](../debugger/edit-and-continue.md).

Weitere Informationen zum Ändern von XAML-Code während einer Debugsitzung finden Sie unter [Schreiben und Debuggen von ausgeführtem XAML-Code durch Neuladen von XAML im laufenden Betrieb](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Untersuchen von Variablen mithilfe von Datentipps

Da Sie sich nun ein wenig auskennen, können Sie damit beginnen, den Zustand Ihrer App (Variablen) mit dem Debugger zu überprüfen. Die Features, mit denen Sie Variablen untersuchen können, zählen zu den nützlichsten Einsatzgebieten des Debuggers. Es gibt verschiedene Möglichkeiten, Variablen zu untersuchen. Beim Debuggen eines Problems müssen Sie häufig herausfinden, ob Variablen die Werte speichern, die diese bei einem bestimmten App-Zustand aufweisen sollten.

Zeigen Sie mit der Maus auf ein Objekt, während der Debugger pausiert ist, um den Standardeigenschaftswert anzuzeigen. In diesem Beispiel ist der Dateiname `market 031.jpg` der Standardeigenschaftswert.

![Einen Datentipp anzeigen](../debugger/media/dbg-tour-data-tips.gif "Einen Datentipp anzeigen")

Erweitern Sie das Objekt, um alle Eigenschaften anzuzeigen (wie z.B. die Eigenschaft `FullPath`).

Beim Debuggen möchten Sie die Eigenschaftswerte für Objekte häufig schnell überprüfen. Die Datentipps stellen eine gute Methode hierfür dar.

> [!TIP]
> In den meisten unterstützten Sprachen können Sie Code während einer Debugsitzung bearbeiten. Weitere Informationen hierzu finden Sie unter [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Untersuchen von Variablen über die Fenster „Auto“ und „Lokal“

Sehen Sie sich das Fenster **Auto** während des Debuggens unten im Code-Editor an.

![Fenster „Auto“](../debugger/media/dbg-tour-autos-window.png "Fenster")

Im Fenster **Auto** werden Ihnen Variablen, deren Typ und der aktuelle Wert angezeigt. Im Fenster **Auto** werden sämtliche Variablen angezeigt, die in der aktuellen Zeile oder der vorangehenden Zeile verwendet werden (in C++ werden in den vorangehenden drei Codezeilen Variablen angezeigt. In der Dokumentation finden Sie Informationen zum sprachspezifischen Verhalten).

> [!NOTE]
> In JavaScript wird das Fenster **Lokal** nicht unterstützt, das Fenster **Auto** jedoch schon.

Sehen Sie sich als Nächstes das Fenster **Lokal** an. Im Fenster **Lokal** werden Ihnen die Variablen angezeigt, die sich derzeit im Gültigkeitsbereich befinden.

![Fenster „Lokal“](../debugger/media/dbg-tour-locals-window.png "Lokalfenster")

In diesem Beispiel befinden sich die Objekte `this` und `f` im Gültigkeitsbereich. Weitere Informationen finden Sie unter [Inspect Variables in the Autos and Locals Windows (Überprüfen von Variablen in den Fenstern „Auto“ und „Lokal“)](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Festlegen von Überwachung

Sie können über das Fenster **Überwachung** eine Variable (oder einen Ausdruck) angeben, die Sie im Auge behalten möchten.

Klicken Sie während des Debuggens mit der rechten Maustaste auf ein Objekt, und wählen Sie **Überwachung hinzufügen** aus.

![Fenster „Überwachung“](../debugger/media/dbg-tour-watch-window.png "Überwachungsfenster")

In diesem Beispiel wurde festgelegt, dass das Objekt `f` überwacht werden soll, und Sie können seine Wertänderung sehen, wenn Sie durch den Debugger navigieren. Im Gegensatz zu den anderen Variablenfenstern werden im Fenster **Überwachung** immer die Variablen angezeigt, die von Ihnen überwacht werden (wenn sie außerhalb des gültigen Bereichs liegen, sind sie ausgegraut).

Weitere Informationen finden Sie unter [Set a Watch using the Watch and QuickWatch Windows (Festlegen einer Überwachung mithilfe der Fenster „Überwachung“ und „Schnellüberwachung“)](../debugger/watch-and-quickwatch-windows.md).

## <a name="examine-the-call-stack"></a>Überprüfen der Aufrufliste

Klicken Sie während des Debuggens auf das Fenster **Aufrufliste**. Dieses Fenster ist standardmäßig im unteren rechten Bereich geöffnet.

![Untersuchen der Aufrufliste](../debugger/media/dbg-tour-call-stack.png "Überprüfen der Aufrufliste")

Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. In der obersten Zeile wird die aktuelle Funktion (in diesem Beispiel die `Update`-Methode) angezeigt. In der zweiten Zeile wird angezeigt, dass `Update` über die `Path.set`-Eigenschaft aufgerufen wurde usw. Die Aufrufliste bietet eine nützliche Möglichkeit zum Untersuchen und Verstehen des Ausführungsablaufs einer App.

> [!NOTE]
> Das Fenster **Aufrufliste** ist mit der Debugperspektive in einigen IDEs wie Eclipse vergleichbar.

Sie können auf eine Codezeile doppelklicken, um den Quellcode anzuzeigen. Dadurch wird auch der aktuelle Bereich geändert, der vom Debugger untersucht wird. Dadurch wird der Debugger nicht weiter ausgeführt.

Sie können auch über die Kontextmenüs im Fenster **Aufrufliste** weitere Aktionen ausführen. So können Sie beispielsweise Breakpoints in bestimmte Funktionen einfügen, Ihre App mithilfe von **Ausführen bis Cursor** neu starten und Quellcode untersuchen. Weitere Informationen finden Sie unter [How to: Examine the Call Stack (Vorgehensweise: Untersuchen der Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a> Untersuchen einer Ausnahme

Wenn Ihre App eine Ausnahme auslöst, springt der Debugger in die Codezeile, die diese verursacht hat.

![Ausnahmen-Hilfe](../debugger/media/dbg-tour-exception-helper.png "Ausnahmen-Hilfe")

In diesem Beispiel zeigt die **Ausnahmen-Hilfe** eine `System.Argument`-Ausnahme und eine Fehlermeldung an, die besagt, dass der Pfad in einem ungültigen Format vorliegt. Es ist also bekannt, dass der Fehler bei einer Methode oder einem Funktionsargument aufgetreten ist.

In diesem Beispiel hat der `DirectoryInfo`-Aufruf den Fehler für eine leere Zeichenfolge zurückgegeben, die in der `value`-Variable gespeichert ist.

Die Ausnahmen-Hilfe ist beim Debuggen von Fehlern sehr nützlich. Sie können zusätzlich Fehlerdetails anzeigen und eine Überwachung über die Ausnahmen-Hilfe hinzufügen. Bei Bedarf können Sie die Bedingungen ändern, die zum Auslösen einer bestimmten Ausnahme führen. Weitere Informationen zum Behandeln von Ausnahmen in Ihrem Code finden Sie unter [Debugging techniques and tools (Debugverfahren und Tools)](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> Der Ausnahmenassistent wurde in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] durch die Ausnahmenhilfe ersetzt.

Erweitern Sie den Knoten **Ausnahmeeinstellungen**, um weitere Optionen zu diesem Ausnahmetyp anzuzeigen. Für dieses Tutorial müssen Sie dort jedoch keine Änderungen vornehmen.

## <a name="configure-debugging"></a>Konfigurieren des Debuggens

Sie können Ihr Projekt so konfigurieren, dass es als [Debug- oder Releasekonfiguration](../debugger/how-to-set-debug-and-release-configurations.md) erstellt wird, Projekteigenschaften für das Debuggen oder [allgemeine Einstellungen ](../debugger/how-to-specify-debugger-settings.md) für das Debuggen konfigurieren. Außerdem können Sie den Debugger so konfigurieren, dass benutzerdefinierte Informationen mithilfe von Features wie dem [DebuggerDisplay](using-the-debuggerdisplay-attribute.md)-Attribut oder, für C/C++, dem [NatVis-Framework](create-custom-views-of-native-objects.md) angezeigt werden.

Debuggingeigenschaften sind für jeden Projekttyp spezifisch. Beispielsweise können Sie ein Argument angeben, das beim Start an die Anwendung übergeben werden soll. Auf diese Konfigurationseinstellungen können Sie zugreifen, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt klicken und **Eigenschaften** auswählen. Debuggingeigenschaften werden in der Regel abhängig vom jeweiligen Projekttyp auf der Registerkarte **Erstellen** oder **Debuggen** angezeigt.

![Projekteigenschaften](../debugger/media/dbg-tour-project-properties.png "Projekteigenschaften")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debuggen von ASP.NET-Live-Apps in Azure App Service

Der **Momentaufnahmedebugger** erstellt eine Momentaufnahme Ihrer Apps, die sich in der Produktion befinden, wenn Code ausgeführt wird, der für Sie relevant ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

![Starten des Momentaufnahmedebuggers](../debugger/media/snapshot-launch.png "Starten des Momentaufnahmedebuggers")

Die Momentaufnahmensammlung ist für ASP.NET-Apps verfügbar, die in Azure App Service ausgeführt werden. ASP.NET-Apps müssen mit .NET Framework 4.6.1 oder höher ausgeführt werden, und ASP.NET Core-Apps müssen unter Windows mit .NET Core 2.0 oder höher ausgeführt werden.

Weitere Informationen finden Sie unter [Debug live ASP.NET apps using the Snapshot Debugger (Debuggen von ASP.NET-Live-Apps mithilfe des Momentaufnahmedebuggers)](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Anzeigen von Momentaufnahmen mit dem IntelliTrace-Feature „Schritt zurück“ (Visual Studio Enterprise)

Das **IntelliTrace-Feature „Schritt zurück“** erstellt bei jedem Breakpoint und Debuggerschritt automatisch eine Momentaufnahme Ihrer Anwendung. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vor** in der Debugsymbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden.

![Schaltflächen „Schritt zurück“ und „Schritt vorwärts“](../debugger/media/intellitrace-step-back-icons-description.png  "Schaltflächen „Schritt zurück“ und „Schritt vorwärts“")

Weitere Informationen finden Sie auf der Seite [Inspect previous app states using IntelliTrace (Untersuchen vorheriger App-Zustände mithilfe von IntelliTrace)](../debugger/view-historical-application-state.md).

## <a name="debug-performance-issues"></a>Debuggen von Leistungsproblemen

Wenn Ihre App langsam ausgeführt wird oder zu viel Arbeitsspeicher nutzt, müssen Sie Ihre App möglicherweise frühzeitig mit den Profilerstellungstools testen. Weitere Informationen über Profilerstellungstools wie das CPU-Auslastungstool und des Arbeitsspeicheranalyzer finden Sie in der [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie einen ersten Einblick in die zahlreichen Features des Debuggers erhalten. Vielleicht sollten Sie sich eines dieser Features genauer ansehen, z. B. Breakpoints.

> [!div class="nextstepaction"]
> [Learn to use breakpoints (Verwenden von Breakpoints)](../debugger/using-breakpoints.md)
