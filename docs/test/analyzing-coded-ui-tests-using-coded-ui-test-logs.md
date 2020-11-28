---
title: Analysieren von Tests der programmierten UI mithilfe der Testprotokolle der programmierten UI
description: Erfahren Sie mehr über Testprotokolle für die programmierte UI, die wichtige Informationen zu Testausführungen der programmierten UI filtern und aufzeichnen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 3dcbb1bdfd89ae13df5174b6502dc6e89437a468
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442494"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analysieren von Tests der programmierten UI mithilfe der Testprotokolle der programmierten UI

Testprotokolle für codierte UI filtern wichtige Informationen zum ausgeführten Test der codierten UI und zeichnen diese auf. Die Protokolle werden in einem Format dargestellt, mit dem sich Probleme schnell debuggen lassen.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Schritt 1: Aktivieren der Protokollierung

Verwenden Sie je nach Szenario eine der folgenden Methoden zur Aktivierung des Protokolls:

- Wenn keine *App.config*-Datei in Ihrem Testprojekt vorhanden ist, gehen Sie folgendermaßen vor:

   1. Ermitteln Sie, welcher *QTAgent\*.exe*-Prozess gestartet wird, wenn Sie den Test ausführen. Eine Möglichkeit hierzu ist beispielsweise die Beobachtung der Registerkarte **Details** im Windows-**Task-Manager**.

   2. Öffnen Sie die entsprechende *CONFIG*-Datei im Ordner *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE*. Wenn der ausgeführte Prozess beispielsweise *QTAgent_40.exe* ist, öffnen Sie die Datei *QTAgent_40.exe.config*.

   2. Ändern Sie den Wert für **EqtTraceLevel** auf die gewünschte Protokollierungsebene.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Speichern Sie die Datei.

- Wenn eine *App.config*-Datei in Ihrem Testprojekt vorhanden ist, gehen Sie folgendermaßen vor:

  - Öffnen Sie die Datei *App.config* im Projekt, und fügen Sie den folgenden Code unter dem Konfigurationsknoten hinzu:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Die Anmeldung aus dem Testcode selbst aktivieren:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Schritt 2: Den Test der programmierten UI ausführen und das Protokoll anzeigen

Wenn Sie einen Test der programmierten UI mit der modifizierten Datei *QTAgent\*.exe.config* ausführen, wird ein Ausgabelink in den Ergebnissen des **Test-Explorers** angezeigt. Protokolldateien werden nicht nur dann generiert, wenn beim Test ein Fehler auftritt, sondern auch bei erfolgreichen Tests, wenn die Ablaufverfolgungsebene auf **verbose** festgelegt ist.

1. Wählen Sie im Menü **Test** **Fenster** und dann **Test-Explorer** aus.

2. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**.

3. Wählen Sie im **Test-Explorer** den Test der programmierten Benutzeroberfläche aus, den Sie ausführen möchten. Öffnen Sie dessen Kontextmenü, und wählen Sie die Option **Ausgewählte Tests ausführen** aus.

     Die automatisierten Tests werden ausgeführt und geben an, wenn sie erfolgreich waren oder Fehler aufgetreten sind.

    > [!TIP]
    > Wählen Sie zum Anzeigen des **Test-Explorers** die Optionen **Test** > **Fenster** und anschließend **Test-Explorer** aus.

4. Wählen Sie den Link **Ausgabe** in den Ergebnissen des **Test-Explorers** aus.

     ![Ausgabelink im Test-Explorer](../test/media/cuit_htmlactionlog1.png)

     Damit wird die Ausgabe für den Test angezeigt, in der ein Link zum Aktionsprotokoll enthalten ist.

     ![Ergebnisse und Ausgabelinks aus Test der codierten UI](../test/media/cuit_htmlactionlog2.png)

5. Wählen Sie den Link *UITestActionLog.html* aus.

     Das Protokoll wird im Webbrowser angezeigt.

     ![Protokolldatei aus Test der codierten UI](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Weitere Informationen

- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
- [Vorgehensweise: Ausführen von Tests in Microsoft Visual Studio](/previous-versions/ms182470(v=vs.140))