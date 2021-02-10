---
title: Konfigurieren der Windows-Firewall für das Remotedebuggen | Microsoft-Dokumentation
description: Konfigurieren Sie die Windows-Firewall für das Remotedebuggen. Konfigurieren Sie Ports für das Remotedebuggen. Beheben Sie Probleme mit der Remotedebugverbindung.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 959d015bd23c91ec2ba6215c7a5b42d13b37ee29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865825"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Konfigurieren der Windows-Firewall für das Remotedebuggen

In einem von der Windows-Firewall geschützten Netzwerk muss die Firewall entsprechend konfiguriert werden, damit Remotedebuggen zulässig ist. Visual Studio und die Remotedebugtools versuchen, bei der Installation oder beim Start die richtigen Firewallports zu öffnen. Möglicherweise müssen Sie aber auch manuell Ports öffnen oder Apps zulassen.

In diesem Thema wird beschrieben, wie Sie die Windows-Firewall konfigurieren, um das Remotedebuggen unter Windows 10, Windows 8 bzw. 8.1 und Windows 7 sowie auf Computern mit Windows Server 2012 R2, 2012 und 2008 R2 zu ermöglichen. Auf dem Visual Studio-Computer und dem Remotecomputer muss nicht das gleiche Betriebssystem ausgeführt werden. Zum Beispiel kann auf dem Visual Studio-Computer Windows 10 und auf dem Remotecomputer Windows Server 2012 R2 ausgeführt werden.

>[!NOTE]
>Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig bei den verschiedenen Betriebssystemen und älteren Windows-Versionen. In den Einstellungen für Windows 8/8.1, Windows 10 und Windows Server 2012 wird das Wort *App* verwendet, während Windows 7 und Windows Server 2008 den Begriff *Programm* verwenden.

## <a name="configure-ports-for-remote-debugging"></a>Konfigurieren von Ports für das Remotedebuggen

Visual Studio und der Remotedebugger versuchen, bei der Installation oder beim Start die richtigen Ports zu öffnen. In einigen Szenarien, z. B. bei einer Drittanbieter Firewall, müssen Sie Ports möglicherweise manuell öffnen.

**So öffnen Sie einen Port**

1. Suchen Sie im Windows-Menü **Start** nach **Windows-Firewall mit erweiterter Sicherheit**, und öffnen Sie diesen Eintrag. Unter Windows 10 heißt sie **Windows Defender Firewall mit erweiterter Sicherheit**.

1. Wählen Sie für einen neuen Eingangsport zuerst **Eingangsregeln** und dann **Neue Regel** aus. Bei einem Ausgangsport wählen Sie stattdessen **Ausgangsregeln** aus.

1. Wählen Sie im **Assistent für neue eingehende Regel** zuerst **Port** und dann **Weiter** aus.

1. Wählen Sie in Abhängigkeit von der Portnummer aus den folgenden Tabellen entweder **TCP** oder **UDP** aus.

1. Geben Sie unter **Bestimmte lokale Ports** eine Portnummer aus den folgenden Tabellen ein, und wählen Sie **Weiter** aus.

1. Wählen Sie **Verbindung zulassen** und dann **Weiter** aus.

1. Wählen Sie einen oder mehrere Netzwerktypen aus, die aktiviert werden sollen (darunter auch den Netzwerktyp für die Remoteverbindung), und wählen Sie dann **Weiter** aus.

1. Fügen Sie einen Namen für die Regel hinzu (z. B **msvsmon**, **IIS** oder **Web Deploy**), und wählen Sie dann **Fertigstellen** aus.

   Daraufhin sollte die neue Regel in der Liste **Eingangsregeln** bzw. **Ausgangsregeln** angezeigt werden und ausgewählt sein.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports auf dem Remotecomputer, die das Remotedebuggen ermöglichen

Für das Remotedebuggen müssen auf dem Remotecomputer die folgenden Ports geöffnet sein:

::: moniker range="vs-2017"

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|4022|Eingehend|TCP|Für VS 2017. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|4023|Eingehend|TCP|Für VS 2017. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Dieser Port wird nur zum Remotedebuggen eines 32-Bit-Prozesses von einer 64-Bit-Version des Remotedebuggers verwendet. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|3702|Ausgehend|UDP|(Optional) Erforderlich für die Ermittlung des Remotedebuggers.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|4024|Eingehend|TCP|Für VS 2019. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|4025|Eingehend|TCP|Für VS 2019. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Dieser Port wird nur zum Remotedebuggen eines 32-Bit-Prozesses von einer 64-Bit-Version des Remotedebuggers verwendet. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|3702|Ausgehend|UDP|(Optional) Erforderlich für die Ermittlung des Remotedebuggers.|

::: moniker-end

Wenn Sie **Verwalteten Kompatibilitätsmodus verwenden** unter **Tools** > **Optionen** > **Debugging** auswählen, öffnen Sie die folgenden zusätzlichen Remotedebuggerports. Mit dem verwalteten Kompatibilitätsmodus des Debuggers aktivieren Sie die ältere Visual Studio 2010-Version des Debuggers.

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|135, 139, 445|Ausgehend|TCP|Erforderlich.|
|137, 138|Ausgehend|UDP|Erforderlich.|

Wenn Ihre Domänenrichtlinie eine Netzwerkkommunikation über IPSec erfordert, müssen Sie auf dem Visual Studio- und dem Remotecomputer zusätzliche Ports öffnen. Zum Debuggen auf einem IIS-Remotewebserver öffnen Sie Port 80 auf dem Remotecomputer.

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|500, 4500|Ausgehend|UDP|Erforderlich, wenn die Domänenrichtlinie die Netzwerkkommunikation über IPSec vorschreibt.|
|80|Ausgehend|TCP|Erforderlich für das Webserverdebuggen.|

Informationen zum Zulassen bestimmter Apps über die Windows-Firewall finden Sie unter [Konfigurieren des Remotedebuggens über die Windows-Firewall](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Konfigurieren des Remotedebuggens über die Windows-Firewall

Sie können die Remotedebugtools auf dem Remotecomputer installieren oder sie aus einem freigegebenen Ordner ausführen. In beiden Fällen muss die Firewall des Remotecomputers ordnungsgemäß konfiguriert sein.

Auf einem Remotecomputer befinden sich die Remotedebugtools in folgendem Pfad:

*\<Visual Studio installation directory\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Zulassen und Konfigurieren des Remotedebuggers über die Windows-Firewall

1. Suchen Sie im Windows-Menü **Start** nach **Windows-Firewall** oder **Windows Defender Firewall**.

1. Wählen Sie **Apps über die Windows-Firewall kommunizieren lassen** aus.

1. Wenn unter **Zulässige Apps und Features** die Option **Remotedebugger** bzw. **Visual Studio-Remotedebugger** nicht angezeigt wird, wählen Sie **Einstellungen ändern** und dann **Andere App zulassen** aus.

1. Wenn die Remotedebugger-App weiterhin nicht im Dialogfeld **App hinzufügen** aufgeführt wird, klicken Sie auf **Durchsuchen**, und navigieren Sie abhängig von der entsprechenden Architektur Ihrer App zu *\<Visual Studio installation directory\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, or *Appx*\>. Wählen Sie *msvsmon.exe* und dann **Hinzufügen** aus.

1. Wählen Sie in der Liste **Apps** den **Remotedebugger** aus, den Sie soeben hinzugefügt haben. Wählen Sie **Netzwerktypen** aus, und wählen Sie dann einen oder mehrere Netzwerktypen aus, die aktiviert werden sollen, darunter auch den Netzwerktyp für die Remoteverbindung.

1. Klicken Sie auf **Hinzufügen** und dann auf **OK**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Problembehandlung der Remotedebugverbindung

Wenn Sie den Remotedebugger nicht an Ihre App anfügen können, stellen Sie sicher, dass Firewallports, Protokolle, Netzwerktypen und App-Einstellungen für das Remotedebuggen korrekt sind.

- Suchen Sie im Windows-Menü **Start** nach **Windows-Firewall**, öffnen Sie diese Option, und wählen Sie **Apps über die Windows-Firewall kommunizieren lassen** aus. Stellen Sie sicher, dass in der Liste **Zulässige Apps und Features** das Kontrollkästchen für **Remotedebugger** bzw. **Visual Studio-Remotedebugger** aktiviert ist und die richtigen Netzwerktypen ausgewählt sind. Andernfalls müssen Sie [die richtigen Apps und Einstellungen hinzufügen](#configure-remote-debugging-through-windows-firewall).

- Suchen Sie im Windows-Menü **Start** nach **Windows-Firewall mit erweiterter Sicherheit**, und öffnen Sie diesen Eintrag. Stellen Sie sicher, dass **Remotedebugger** bzw. **Visual Studio-Remotedebugger** unter **Eingangsregeln** (und optional unter **Ausgangsregeln**) mit einem grünen Häkchen versehen ist und alle Einstellungen richtig sind.

  - Um die Regeleinstellungen anzuzeigen oder zu ändern, klicken Sie in der Liste mit der rechten Maustaste auf die App **Remotedebugger**, und wählen Sie **Eigenschaften** aus. Verwenden Sie die Registerkarte **Eigenschaften**, um die Regel zu aktivieren oder zu deaktivieren, oder ändern Sie Portnummern, Protokolle oder Netzwerktypen.
  - Wenn die Remotedebugger-App in der Regelliste nicht angezeigt wird, müssen Sie [die richtigen Ports hinzufügen und konfigurieren](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Siehe auch

- [Remotedebuggen](../debugger/remote-debugging.md)
- [Visual Studio-Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
