---
title: Anfügen an laufende Prozesse mit dem Debugger
description: Es wird beschrieben, wie Sie den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Remotecomputer anfügen.
ms.custom: SEO-VS-2020, seodec18
ms.date: 06/12/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fd1ff5ff0f8c7510185236c425ddd870f8b500f
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97760925"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger

Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. Nachdem der Prozess ausgeführt wird, wählen Sie **Debuggen** > **An den Prozess anhängen** aus, oder drücken Sie in Visual Studio **STRG**+**ALT**+**P**, und verwenden Sie das Dialogfeld **An den Prozess anhängen**, um den Debugger an den Prozess anzuhängen.

Sie können **An den Prozess anhängen** verwenden, um laufende Apps auf lokalen oder Remotecomputern zu debuggen, um mehrere Prozesse gleichzeitig zu debuggen, um Apps zu debuggen, die nicht in Visual Studio erstellt wurden, oder um Apps zu debuggen, die Sie nicht von Visual Studio aus mit dem angehängten Debugger gestartet haben. Wenn Sie z. B. eine App ohne den Debugger ausführen und eine Ausnahme auslösen, dann können Sie den Debugger an den Prozess anhängen, der die App ausführt, und mit dem Debuggen beginnen.

> [!TIP]
> Sind Sie nicht sicher, ob Sie **An den Prozess anhängen** für Ihr Debugszenario verwenden sollen? Weitere Informationen finden Sie unter [Allgemeine Debugszenarien](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Anhängen an einen laufenden Prozess auf dem lokalen Computer

Informationen zum schnellen erneuten Anhängen an einen Prozess, an den Sie zuvor angehängt haben, finden Sie unter [Erneutes Anhängen an einen Prozess](#BKMK_reattach).

**So hängen Sie einen Prozess auf dem lokalen Computer an**

1. Wählen Sie in Visual Studio **Debuggen** > **An den Prozess anhängen** aus (oder drücken Sie **STRG**+**ALT**+**P**), um das Dialogfeld **An den Prozess anhängen** zu öffnen.

1. Überprüfen Sie den **Verbindungstyp**.

   In den meisten Szenarien können Sie **Standard** verwenden. Für einige Szenarien ist möglicherweise ein anderer Verbindungstyp erforderlich. Weitere Informationen finden Sie in den anderen Abschnitten dieses Artikels oder unter [ Allgemeine Debugszenarien](#BKMK_Scenarios).

1. Legen Sie **Verbindungsziel** auf den Namen Ihres lokalen Computers fest.

   ![Screenshot: Dialogfeld „An den Prozess anhängen“ mit Festlegung des Verbindungsziels auf den Namen des lokalen Computers](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. Suchen und wählen Sie in der Liste **Verfügbare Prozesse** den Prozess oder die Prozesse aus, die Sie anhängen möchten.

   - Geben Sie zur schnellen Auswahl eines Prozesses seinen Namen oder den Anfangsbuchstaben in das Feld **Prozesse filtern** ein.

   - Wenn Sie den Prozessnamen nicht kennen, durchsuchen Sie die Liste, oder lesen Sie [Allgemeine Debugszenarien](#BKMK_Scenarios), um einige gängige Prozessnamen zu erhalten.

   >[!TIP]
   >Prozesse können im Hintergrund gestartet und beendet werden, während das Dialogfeld **An den Prozess anhängen** geöffnet ist, sodass die Liste der aktiven Prozesse möglicherweise nicht immer aktuell ist. Sie können jederzeit **Aktualisieren** auswählen, um die aktuelle Liste anzuzeigen.

1. Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des zu debuggenden Codes aufgeführt ist. Die Standardeinstellung **Automatisch** funktioniert für die meisten App-Typen.

   Wenn Sie den Verbindungstyp **Standard** verwenden, können Sie den Typ des Codes, den Sie anfügen möchten, manuell auswählen. Andernfalls ist die Option **Auswählen** möglicherweise deaktiviert.

   So wählen Sie Codetypen manuell aus
   1. Klicken Sie auf **Auswählen**.
   1. Wählen Sie im Dialogfeld **Codetyp auswählen** die Option **Diese Codetypen debuggen** aus.
      Wenn beim Versuch, einen Prozess in der Liste anzufügen, ein Fehler auftritt, können Sie das Dialogfeld [Codetyp auswählen](../debugger/select-code-type-dialog-box.md) verwenden, um die [Problembehandlung](#BKMK_Troubleshoot_attach_errors) zu erleichtern.
   1. Wählen Sie die zu debuggenden Codetypen aus.
   1. Klicken Sie auf **OK**.

1. Wählen Sie **Anfügen** aus.

>[!NOTE]
>Sie können zum Debuggen an mehrere Apps angefügt werden, aber jeweils nur eine App ist im Debugger aktiv. Sie können die aktive App auf der Visual Studio-Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anfügen an einen Prozess auf einem Remotecomputer

Sie können auch einen Remotecomputer im Dialogfeld **An den Prozess anhängen** auswählen, eine Liste verfügbarer Prozesse anzeigen, die auf diesem Computer ausgeführt werden, und an einen oder mehrere der Prozesse zum Debuggen anhängen. Der Remotedebugger (*msvsmon.exe*) muss auf dem Remotecomputer ausgeführt werden. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

Ausführlichere Anweisungen zum Debuggen von ASP.NET-Anwendungen, die für IIS bereitgestellt wurden, finden Sie unter [Remotedebuggen von ASP.NET auf einem IIS-Remotecomputer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**So fügen Sie an einen aktiven Prozess auf einem Remotecomputer an**

1. Wählen Sie in Visual Studio **Debuggen** > **An den Prozess anhängen** aus (oder drücken Sie **STRG**+**ALT**+**P**), um das Dialogfeld **An den Prozess anhängen** zu öffnen.

1. Überprüfen Sie den **Verbindungstyp**.

   In den meisten Szenarien können Sie **Standard** verwenden. Einige Szenarien wie das Debuggen von Linux oder einer Containeranwendung erfordern einen anderen Verbindungstyp. Weitere Informationen finden Sie in den anderen Abschnitten dieses Artikels oder unter [ Allgemeine Debugszenarien](#BKMK_Scenarios).

1. Wählen Sie im Feld **Verbindungsziel** den Remotecomputer mit einer der folgenden Methoden aus:

   - Wählen Sie den Dropdownpfeil neben **Verbindungsziel** und dann den Computernamen aus der Dropdownliste aus.
   - Geben Sie den Computernamen in das Feld **Verbindungsziel** ein, und drücken Sie die **EINGABETASTE**.

     Vergewissern Sie sich, dass Visual Studio den erforderlichen Port dem Computernamen hinzufügt, der im folgenden Format angezeigt wird: **\<remote computer name>:port**.

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Wenn Sie keine Verbindung über den Namen des Remotecomputers herstellen können, versuchen Sie es mit der IP- und Portadresse (z. B. `123.45.678.9:4022`). 4024 ist der Standardport für den Remotedebugger von Visual Studio 2019 x64. Weitere Informationen zu anderen Portzuweisungen des Remotedebuggers finden Sie unter [Remotedebugger – Portzuweisungen](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Wenn Sie keine Verbindung über den Namen des Remotecomputers herstellen können, versuchen Sie es mit der IP- und Portadresse (z. B. `123.45.678.9:4022`). 4022 ist der Standardport für den Remotedebugger von Visual Studio 2017 x64. Weitere Informationen zu anderen Portzuweisungen des Remotedebuggers finden Sie unter [Remotedebugger – Portzuweisungen](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Wählen Sie die Schaltfläche **Suchen** neben dem Feld **Verbindungsziel** aus, um das Dialogfeld **Remoteverbindungen** zu öffnen. Das Dialogfeld **Remoteverbindungen** listet alle Geräte auf, die sich in Ihrem lokalen Subnetz befinden oder direkt an Ihren Computer angefügt sind. Möglicherweise müssen Sie auf dem Server den [UDP-Port 3702 öffnen](../debugger/remote-debugger-port-assignments.md), um Remotegeräte zu erkennen. Wählen Sie den gewünschten Computer bzw. das gewünschte Gerät aus, und klicken Sie dann auf **Auswählen**.

   > [!NOTE]
   > Die Einstellung **Verbindungstyp** bleibt zwischen den Debugsitzungen bestehen. Die Einstellung **Verbindungsziel** bleibt zwischen Debugsitzungen nur dann bestehen, wenn eine erfolgreiche Debugverbindung mit diesem Ziel hergestellt wurde.

3. Klicken Sie auf **Aktualisieren**, um die Liste **Verfügbare Prozesse** zu füllen.

    >[!TIP]
    >Prozesse können im Hintergrund gestartet und beendet werden, während das Dialogfeld **An den Prozess anhängen** geöffnet ist, sodass die Liste der aktiven Prozesse möglicherweise nicht immer aktuell ist. Sie können jederzeit **Aktualisieren** auswählen, um die aktuelle Liste anzuzeigen.

4. Suchen und wählen Sie in der Liste **Verfügbare Prozesse** den Prozess oder die Prozesse aus, die Sie anhängen möchten.

   - Geben Sie zur schnellen Auswahl eines Prozesses seinen Namen oder den Anfangsbuchstaben in das Feld **Prozesse filtern** ein.

   - Wenn Sie den Prozessnamen nicht kennen, durchsuchen Sie die Liste, oder lesen Sie [Allgemeine Debugszenarien](#BKMK_Scenarios), um einige gängige Prozessnamen zu erhalten.

   - Aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzern anzeigen**, um Prozesse zu finden, die unter allen Benutzerkonten ausgeführt werden.

     >[!NOTE]
     >Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des zu debuggenden Codes aufgeführt ist. Die Standardeinstellung **Automatisch** funktioniert für die meisten App-Typen.

   Wenn Sie den Verbindungstyp **Standard** verwenden, können Sie den Typ des Codes, den Sie anfügen möchten, manuell auswählen. Andernfalls ist die Option **Auswählen** möglicherweise deaktiviert.

   So wählen Sie Codetypen manuell aus
   1. Klicken Sie auf **Auswählen**.
   1. Wählen Sie im Dialogfeld **Codetyp auswählen** die Option **Diese Codetypen debuggen** aus.
      Wenn beim Versuch, einen Prozess in der Liste anzufügen, ein Fehler auftritt, können Sie das Dialogfeld [Codetyp auswählen](../debugger/select-code-type-dialog-box.md) verwenden, um die [Problembehandlung](#BKMK_Troubleshoot_attach_errors) zu erleichtern.
   1. Klicken Sie auf **OK**.

6. Wählen Sie **Anfügen** aus.

>[!NOTE]
>Sie können zum Debuggen an mehrere Apps angefügt werden, aber jeweils nur eine App ist im Debugger aktiv. Sie können die aktive App auf der Visual Studio-Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen.

In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) in der Liste **Verfügbare Prozesse** nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer mit einem eingeschränkten Benutzerkonto ausführen, werden in der Liste **Verfügbare Prozesse** keine Prozesse angezeigt, die in Sitzung 0 ausgeführt werden. Sitzung 0 wird für Dienste und andere Serverprozesse verwendet, einschließlich *w3wp.exe*. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen.

Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p <ProcessId>` in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit *tlist.exe* ermittelt werden. Laden Sie die Debugtools für Windows unter [WDK and WinDbg downloads (Herunterladen von WDK und WinDbg)](/windows-hardware/drivers/download-the-wdk) herunter, um *tlist.exe* abzurufen.

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Anfügen an einen .NET Core-Prozess unter Linux mit SSH

Weitere Informationen finden Sie unter [Remotedebuggen von .NET Core unter Linux mit SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Anfügen an einen in einem Docker-Container ausgeführten Prozess

Ab Visual Studio 2019 können Sie den Visual Studio-Debugger an einen Prozess anfügen, der in einem Docker-Container ausgeführt wird. Weitere Informationen zum Linux-Docker-Container in .NET Core finden Sie unter [Anfügen an einen Prozess, der in einem Linux-Docker-Container ausgeführt wird](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container). Weitere Informationen zum Windows-Docker-Container finden Sie unter [Anfügen an einen Prozess, der in einem Windows-Docker-Container ausgeführt wird](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container).

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Erneutes Anfügen an einen Prozess

Mit **Debuggen** > **Erneut an den Prozess anhängen** (**UMSCHALT**+**ALT**+**P**) können Sie schnell erneut an Prozesse anhängen, an die Sie zuvor angefügt haben. Wenn Sie diesen Befehl auswählen, versucht der Debugger sofort, an die letzten Prozesse, an die Sie angehängt haben, anzuhängen, indem er zuerst versucht, die vorherige Prozess-ID und, falls das nicht erfolgreich ist, den vorherigen Prozessnamen abzugleichen. Wenn keine Übereinstimmungen gefunden werden oder wenn mehrere Prozesse denselben Namen aufweisen, wird das Dialogfeld **An den Prozess anhängen** geöffnet, damit Sie den richtigen Prozess auswählen können.

> [!NOTE]
> Der Befehl **Erneut an den Prozess anhängen** ist ab Visual Studio 2017 verfügbar.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Allgemeine Debugszenarien

Um Ihnen bei der Entscheidung zu helfen, ob Sie **An den Prozess anhängen** verwenden und an welchen Prozess Sie anhängen sollen, zeigt die folgende Tabelle einige gängige Debugszenarien mit Links zu weiteren Anweisungen, sofern verfügbar. (Die Liste ist nicht vollständig.)

Bei einigen Anwendungstypen, z. B. UWP-Apps (Universelle Windows-App), hängen Sie nicht direkt an einen Prozessnamen an, sondern verwenden stattdessen die Menüoption **Installiertes App-Paket debuggen** in Visual Studio (siehe Tabelle).

Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.

Für clientseitiges Skriptdebugging muss das Skriptdebuggen im Browser aktiviert sein. Zum Debuggen von clientseitigem Skript in Chrome wählen Sie **JavaScript (Chrome)** oder **JavaScript (Microsoft Edge – Chromium)** als Codetyp aus, und je nach App-Typ müssen Sie möglicherweise alle Chrome-Instanzen schließen und den Browser im Debugmodus starten (geben Sie `chrome.exe --remote-debugging-port=9222` von einer Befehlszeile aus ein). In früheren Versionen von Visual Studio war der Skriptdebugger für Chrome das **Webkit**.

Um schnell einen aktiven Prozess zum Anhängen auszuwählen, geben Sie in Visual Studio **STRG**+**ALT**+**P** und dann den ersten Buchstaben des Prozessnamens ein.

|Szenario|Debugmethode|Prozessname|Hinweise und Links|
|-|-|-|-|
|Remotedebuggen von ASP.NET 4 oder 4.5 auf einem IIS-Server|Verwenden von Remotetools und **An den Prozess anhängen**|*w3wp.exe*|Weitere Informationen finden Sie unter [Remotedebuggen von ASP.NET auf einem IIS-Remotecomputer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remotedebuggen von ASP.NET Core auf einem IIS-Server|Verwenden von Remotetools und **An den Prozess anhängen**|*w3wp.exe* oder *dotnet.exe*|Ab .NET Core 3 wird der Prozess *w3wp.exe* für das standardmäßige [In-App-Hostingmodell](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) verwendet. Informationen zur Bereitstellung von Apps finden Sie unter [Veröffentlichen in IIS](/aspnet/core/host-and-deploy/iis/). Ausführlichere Informationen finden Sie unter [Remotedebuggen von ASP.NET Core auf einem IIS-Remotecomputer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Debuggen clientseitiger Skripts auf einem lokalen IIS-Server, für unterstützte App-Typen |Verwenden von **An den Prozess anhängen**|*chrome.exe*, *MicrosoftEdgeCP.exe* oder *iexplore.exe*|Skriptdebugging muss aktiviert sein. Für Chrome müssen Sie Chrome auch im Debugmodus ausführen (geben Sie `chrome.exe --remote-debugging-port=9222` von der Befehlszeile aus ein) und **JavaScript (Chrome)** im Feld **Anfügen** auswählen.|
|Debuggen einer C#-, Visual Basic- oder C++-App auf dem lokalen Computer|Verwenden Sie entweder das Standarddebuggen (**F5**) oder **An den Prozess anhängen**.|*\<appname>.exe*|Verwenden Sie in den meisten Szenarien das Standarddebuggen und nicht **An den Prozess anhängen**.|
|Remotedebuggen einer Windows-Desktop-App|Remotetools|Nicht zutreffend| Weitere Informationen finden Sie unter [Remotedebuggen einer C#- oder Visual Basic-App](../debugger/remote-debugging-csharp.md) oder [Remotedebuggen einer C++-App](../debugger/remote-debugging-cpp.md).|
|Debuggen von .NET Core unter Linux|Verwenden von **An den Prozess anhängen**|*dotnet.exe* oder ein eindeutiger Prozessname|Weitere Informationen zur Verwendung von SSH finden Sie unter [Remotedebuggen von .NET Core unter Linux mit SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). Weitere Informationen zu containerisierten Apps finden Sie unter [Anfügen an einen in einem Docker-Container ausgeführten Prozess](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container).|
|Debuggen einer containerisierten App|*dotnet.exe* oder ein eindeutiger Prozessname|Weitere Informationen finden Sie unter [Anfügen an einen in einem Docker-Container ausgeführten Prozess](../debugger/attach-to-process-running-in-docker-container.md).|
|Remotedebuggen von Python unter Linux|Verwenden von **An den Prozess anhängen**|*debugpy*|Weitere Informationen finden Sie unter [Remoteanfügen über Python Tools](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools).|
|Debuggen einer ASP. NET-App auf dem lokalen Computer, nachdem Sie die App ohne den Debugger gestartet haben|Verwenden von **An den Prozess anhängen**|*iiexpress.exe*|Dies kann hilfreich sein, damit Ihre App schneller geladen wird, z. B. bei der Profilerstellung. |
|Debuggen anderer unterstützter App-Typen für einen Serverprozess|Wenn es sich um einen Remoteserver handelt, verwenden Sie Remotetools und **An den Prozess anhängen**.|*chrome.exe*, *iexplore.exe* oder andere Prozesse|Verwenden Sie bei Bedarf den Ressourcenmonitor, um den Prozess zu identifizieren. Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](../debugger/remote-debugging.md).|
|Remotedebuggen einer UWP- (Universelle Windows-App), OneCore-, HoloLens- oder IoT-App|Installiertes App-Paket debuggen|Nicht zutreffend|Weitere Informationen finden Sie unter [Debuggen eines installierten App-Pakets](debug-installed-app-package.md), anstatt **An den Prozess anhängen** zu verwenden.|
|Debuggen einer UWP- (Universelle Windows-App), OneCore-, HoloLens- oder IoT-App, die Sie nicht in Visual Studio gestartet haben|Installiertes App-Paket debuggen|Nicht zutreffend|Weitere Informationen finden Sie unter [Debuggen eines installierten App-Pakets](debug-installed-app-package.md), anstatt **An den Prozess anhängen** zu verwenden.|

## <a name="use-debugger-features"></a>Verwenden von Debuggerfeatures

Um die vollständigen Features des Visual Studio-Debuggers (wie das Erreichen von Haltepunkten) beim Anfügen an einen Prozess nutzen zu können, muss die App exakt mit Ihrer lokalen Quelle und den Symbolen übereinstimmen. Das bedeutet, dass der Debugger in der Lage sein muss, die richtigen [PDB-Symboldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) zu laden. Standardmäßig ist hierfür ein Debugbuild erforderlich.

Für Remotedebuggingszenarien müssen Sie den Quellcode (oder eine Kopie des Quellcodes) bereits in Visual Studio geöffnet haben. Die kompilierten Binärdateien der App auf dem Remotecomputer müssen vom gleichen Build wie auf dem lokalen Computer stammen.

In einigen lokalen Debugszenarien können Sie in Visual Studio ohne Zugriff auf die Quelle debuggen, wenn die richtigen Symboldateien für die App vorhanden sind. Standardmäßig ist hierfür ein Debugbuild erforderlich. Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Beheben von Fehlern beim Anfügen

In einigen Szenarien kann der Debugger Hilfe benötigen, um den Typ des zu debuggenden Codes ordnungsgemäß zu bestimmen. Wenn die Verbindungswerte zwar richtig festgelegt sind (Sie können den ordnungsgemäßen Prozess in der Liste **Verfügbare Prozesse** einsehen), der Debugger aber nicht angefügt werden kann, versuchen Sie, in der Liste **Verbindungstyp** den geeignetsten Verbindungstyp auszuwählen. Dies kann beispielsweise erforderlich sein, wenn Sie eine Linux- oder Python-App debuggen. Bei Verwendung des Verbindungstyps „Standard“ können Sie alternativ den spezifischen Typ des Codes auswählen, mit dem eine Verbindung hergestellt werden soll, wie weiter unten in diesem Abschnitt beschrieben.

Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld [Codetyp auswählen](../debugger/select-code-type-dialog-box.md) angezeigt und ausgewählt.

Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Dies tritt normalerweise in den folgenden Fällen auf:

- Sie versuchen das Anfügen an einen Prozess, der auf einem Remotecomputer läuft. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert.
- Sie versuchen, den Debugger zum direkten Datenbankdebuggen an mehr als einen Prozess anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.

Wenn der Debugger nur an bestimmte, nicht aber an alle Codetypen angefügt werden kann, wird eine Meldung mit den Typen angezeigt, die nicht angefügt werden konnten.

Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Der nicht angefügte Code im Prozess wird zwar weiterhin ausgeführt, doch Sie wären nicht in der Lage, Haltepunkte festzulegen, Daten anzuzeigen oder andere Debugoperationen für diesen Code durchzuführen.

Um weitere Informationen darüber zu erhalten, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie erneut, den Debugger nur an diesen Codetyp anzufügen.

**So erhalten Sie Informationen darüber, warum ein bestimmter Codetyp nicht angehängt werden konnte:**

1. Trennen Sie den Prozess. Wählen Sie im Menü **Debuggen** die Option **Alle trennen** aus.

1. Fügen Sie erneut an den Prozess an, wobei Sie nur den Codetyp auswählen, der nicht angefügt werden konnte.

    1. Wählen Sie im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** den entsprechenden Prozess aus.

    2. Wählen Sie **Auswählen**.

    3. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie anschließend den Codetyp aus, der nicht angefügt werden konnte. Deaktivieren Sie die anderen Codetypen.

    4. Klicken Sie auf **OK**.

    5. Wählen Sie im Dialogfeld **An den Prozess anhängen** die Option **Anfügen** aus.

    Dieses Mal schlägt das Anfügen komplett fehl, und Sie erhalten eine spezifische Fehlermeldung.

## <a name="see-also"></a>Siehe auch

- [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md)
- [Just-In-Time debugging (Just-In-Time-Debuggen)](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Remotedebuggen](../debugger/remote-debugging.md)
