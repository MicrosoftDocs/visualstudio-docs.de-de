---
title: Debuggen eines Webformulars | Microsoft-Dokumentation
description: In diesem Artikel finden Sie eine exemplarische Vorgehensweise zum Debuggen einer ASP.NET-Webanwendung (Web Forms), die sich auch mit dem Festlegen von Breakpoints und dem Untersuchen von Variablen befasst.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007a63ea16ab044292f451d8d9c427f4358e3f13
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148220"
---
# <a name="walkthrough-debugging-a-web-form"></a>Exemplarische Vorgehensweise: Debuggen eines Webformulars
Die Schritte in dieser exemplarischen Vorgehensweise enthalten eine Anleitung zum Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen (auch bekannt als Web Forms). Darin wird dargestellt, wie die Ausführung gestartet und beendet wird, wie Haltepunkte festgelegt und Variablen im Fenster **Überwachen** überprüft werden.

> [!NOTE]
> Um diese exemplarische Vorgehensweise vollständig durchzuarbeiten, müssen Sie auf dem Servercomputer über Administratorrechte verfügen. Standardmäßig wird der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess (entweder aspnet_wp.exe oder w3wp.exe) als [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess ausgeführt. Sie müssen zum Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] auf dem Computer, auf dem es von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ausgeführt wird, über Administratorrechte verfügen. Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).

Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="to-create-the-web-form"></a>So erstellen Sie das Web Form

1. Falls Sie bereits eine Projektmappe geöffnet haben, schließen Sie sie.

2. Klicken Sie im Menü **Datei** auf **Neu**, und klicken Sie anschließend auf **Website**.

    Das Dialogfeld **Neue Website** wird angezeigt.

3. Klicken Sie im Bereich **Vorlagen** auf **ASP.NET-Website**.

4. Klicken Sie in der Liste in der Zeile **Speicherort** auf die Option **HTTP**, und geben Sie **http://localhost/WebSite** in das Textfeld ein.

5. Klicken Sie in der Liste **Sprache** auf **Visual C#** oder **Visual Basic**.

6. Klicken Sie auf **OK**.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt ein neues Projekt und zeigt den HTML-Standardquellcode an. Außerdem wird unter der **Standardwebsite** von IIS ein neues virtuelles Verzeichnis mit dem Namen **WebSite** erstellt.

7. Klicken Sie am unteren Rand auf die Registerkarte **Entwurf**.

8. Klicken Sie am linken Rand auf die Registerkarte **Toolbox**, oder wählen Sie sie im Menü **Ansicht** aus.

    Die **Toolbox** wird geöffnet.

9. Klicken Sie in der **Toolbox** auf das Steuerelement **Button**, und fügen Sie es der Hauptentwurfsoberfläche (Default.aspx) hinzu.

10. Klicken Sie in der **Toolbox** auf das Steuerelement **Textbox**, und ziehen Sie es auf die Entwurfsoberfläche (Default.aspx).

11. Doppelklicken Sie auf das abgelegte Button-Steuerelement.

     Dadurch gelangen Sie auf die Codepage: „Default.aspx.cs“ für C# oder „default.aspx.vb“ für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Der Cursor sollte sich in der `Button1_Click`-Funktion befinden.

12. Fügen Sie folgenden Code in die `Button1_Click`-Funktion ein:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Das Projekt wird fehlerfrei erstellt.

     Jetzt können Sie mit dem Debuggen beginnen.

## <a name="to-debug-the-web-form"></a>So debuggen Sie das Web Form

1. Klicken Sie im Fenster Default.aspx.cs oder Default.aspx.vb auf den linken Rand der Zeile, der Sie Text hinzugefügt haben:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Ein roter Punkt wird angezeigt, und der Text der Zeile wird rot hervorgehoben. Der rote Punkt steht für einen Haltepunkt. Wenn Sie die Anwendung unter dem Debugger ausführen, hält dieser die Ausführung an der Stelle mit dem Haltepunkt an. Dadurch erhalten Sie die Möglichkeit, den Status der Anwendung zu überprüfen und diese zu debuggen. Weitere Informationen finden Sie unter [Breakpoints (Haltepunkte)](/previous-versions/ktf38f66(v=vs.100)).

2. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

3. Das Dialogfeld **Debuggen nicht aktiviert** wird angezeigt. Wählen Sie die Option **Modify the Web.config file to enable debugging** (Zum Aktivieren von Debugging die Web.config-Datei ändern) aus, und klicken Sie auf **OK**.

    Internet Explorer wird gestartet, und die zuvor entworfene Seite wird angezeigt.

4. Klicken Sie im Internet Explorer auf die erstellte Schaltfläche.

    In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gelangen Sie damit in die Zeile, in der Sie den Haltepunkt auf der Codepage Default.aspx.cs oder Default.aspx.vb festlegen. Diese Zeile sollte gelb markiert sein. Jetzt können Sie die Variablen der Anwendung anzeigen und die Ausführung der Anwendung steuern. Die Ausführung der Anwendung wird angehalten, und der Debugger wartet auf einen Befehl.

5. Klicken Sie im Menü **Debuggen** auf **Fenster**, klicken Sie dann auf **Überwachen** und anschließend auf **Watch1** (Überwachen1).

6. Geben Sie **TextBox1.Text** im Fenster **Überwachen** ein.

    Der Wert der Variablen `TextBox1.Text` wird im Fenster **Überwachen** angezeigt:

   '""'

7. Klicken Sie im Menü **Debuggen** auf **Prozedurschritt**.

    Der Wert von `TextBox1.Text` ändert sich im Fenster **Überwachen** in:

   `"Button was clicked!"`

8. Klicken Sie im Menü **Debuggen** auf **Weiter**.

9. Klicken Sie im Internet Explorer erneut auf die erstellte Schaltfläche.

     Die Ausführung hält wieder am Haltepunkt an.

10. Klicken Sie im Fenster Default.aspx.cs bzw. Default.aspx.vb im linken Rand auf den roten Punkt.

     Dadurch wird der Haltpunkt entfernt.

11. Klicken Sie im Menü **Debuggen** auf **Debuggen beenden**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>So stellen Sie zum Debuggen eine Verbindung mit dem Web Form her

1. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] können Sie den Debugger an einen laufenden Prozess anfügen. Für möglichst effektives Debuggen kompilieren Sie die ausführbare Datei als Debugversion mit Symboldateien (.pdb).

2. Klicken Sie im Fenster Default.aspx.cs bzw. Default.aspx.vb auf den linken Rand der Zeile, um erneut einen Haltepunkt in der hinzugefügten Zeile festzulegen:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.

    Das Web Form wird in Internet Explorer gestartet, der Debugger ist jedoch nicht angehängt.

4. Fügen Sie den Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess an. Weitere Informationen finden Sie unter [Debuggen von bereitgestellten Webanwendungen](../debugger/debugging-deployed-web-applications.md).

5. Klicken Sie im Internet Explorer auf die Schaltfläche im Formular.

    In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sollten Sie den Haltepunkt in Default.aspx.cs, Default.aspx.vb oder Default.aspx erreichen.

6. Wenn der Debugvorgang abgeschlossen ist, klicken Sie im Menü **Debuggen** auf **Debuggen beenden**.

## <a name="see-also"></a>Siehe auch

- [Debug ASP.NET Applications (Debuggen von ASP.NET-Anwendungen)](../debugger/how-to-enable-debugging-for-aspnet-applications.md)