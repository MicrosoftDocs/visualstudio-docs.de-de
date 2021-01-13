---
title: Debuggen mit dem Just-In-Time-Debugger | Microsoft-Dokumentation
description: Debuggen mit dem Just-In-Time-Debugger in Visual Studio. Beim Just-In-Time-Debuggen kann Visual Studio automatisch gestartet werden, wenn Fehler oder ein Absturz in einer App auftreten.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a03afa64d19e3ccd0efbb170b4305049f6bfee30
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761341"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debuggen mit dem Just-In-Time-Debugger in Visual Studio

Beim Just-In-Time-Debuggen kann Visual Studio automatisch gestartet werden, wenn Fehler oder ein Absturz in einer App auftreten, die außerhalb von Visual Studio ausgeführt wird. Mit Just-in-Time-Debuggen können Sie Apps außerhalb von Visual Studio testen und Visual Studio öffnen, um mit dem Debuggen zu beginnen, wenn ein Problem auftritt.

Just-in-Time-Debuggen funktioniert für Windows-Desktop-Apps. Es funktioniert nicht für universelle Windows-Apps oder für verwalteten Code, der in einer nativen Anwendung gehostet wird, z. B. in Schnellansichten.

> [!TIP]
> Wenn das Dialogfeld „Just-in-Time-Debugger“ nicht mehr angezeigt werden soll, Visual Studio jedoch nicht installiert ist, finden Sie weitere Informationen unter [Deaktivieren des Just-in-Time-Debuggers](../debugger/just-in-time-debugging-in-visual-studio.md). Wenn Visual Studio deinstalliert wurde, müssen Sie möglicherweise [Just-in-Time-Debuggen über die Windows-Registrierung deaktivieren](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Aktivieren oder Deaktivieren von Just-In-Time-Debuggen in Visual Studio

>[!NOTE]
>Um Just-in-Time-Debuggen zu aktivieren oder zu deaktivieren, müssen Sie Visual Studio als Administrator ausführen. Beim Aktivieren oder Deaktivieren von Just-In-Time-Debuggen wird ein Registrierungsschlüssel festgelegt, und zum Ändern dieses Schlüssels sind möglicherweise Administratorrechte erforderlich. Um Visual Studio als Administrator zu öffnen, klicken Sie mit der rechten Maustaste auf die App „Visual Studio“, und wählen Sie **Als Administrator ausführen** aus.

Sie können Just-in-Time-Debuggen im Visual Studio-Dialogfeld **Extras** > **Optionen** (oder **Debuggen** > **Optionen**) konfigurieren.

**So aktivieren oder deaktivieren Sie Just-In-Time-Debuggen:**

1. Klicken Sie im Menü **Extras** oder **Debuggen** auf **Optionen** > **Debuggen** > **Just-In-Time**.

   ![Aktivieren oder Deaktivieren von JIT-Debuggen](../debugger/media/dbg-jit-enable-or-disable.png "Aktivieren oder Deaktivieren von JIT-Debuggen")

1. Wählen Sie im Feld **Just-in-Time-Debuggen für diese Codetypen aktivieren** die Codetypen aus, auf die Just-in-Time-Debuggen angewendet werden soll: **Verwaltet**, **Systemeigen** und/oder **Skript**.

1. Klicken Sie auf **OK**.

Wenn Sie den Just-in-Time-Debugger aktivieren, dieser jedoch nicht geöffnet wird, wenn eine App abstürzt oder Fehler in ihr auftreten, finden Sie weitere Informationen unter [Problembehandlung beim Just-in-Time-Debuggen](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Deaktivieren von Just-In-Time-Debuggen über die Windows-Registrierung

Just-In-Time-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist. Wenn Visual Studio nicht mehr installiert ist, können Sie Just-In-Time-Debuggen durch Bearbeiten der Windows-Registrierung deaktivieren.

**So deaktivieren Sie Just-In-Time-Debuggen durch Bearbeiten der Registrierung:**

1. Führen Sie im Windows-Menü **Start** den **Registrierungs-Editor** (*regedit.exe*) aus.

2. Suchen Sie im Fenster **Registrierungs-Editor** die folgenden Registrierungseinträge, und löschen Sie sie:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT-Registrierungsschlüssel](../debugger/media/dbg-jit-registry.png "JIT-Registrierungsschlüssel")

3. Wenn auf Ihrem Computer ein 64-Bit-Betriebssystem ausgeführt wird, löschen Sie auch die folgenden Registrierungseinträge:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Löschen oder ändern Sie keine anderen Registrierungsschlüssel.

5. Schließen Sie das Fenster **Registrierungs-Editor**.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Aktivieren von Just-In-Time-Debuggen für ein Windows Form

Standardmäßig verfügen Windows Forms-Apps über einen Ausnahmehandler der obersten Ebene, mit dem sich die App weiterhin ausführen lässt, wenn sie wiederhergestellt werden kann. Wenn eine Windows Forms-App eine nicht behandelte Ausnahme auslöst, wird das folgende Dialogfeld angezeigt:

![Nicht behandelte Windows Forms-Ausnahme](../debugger/media/windowsformsunhandledexception.png "Nicht behandelte Windows Forms-Ausnahme")

Um statt der standardmäßigen Windows Forms-Fehlerbehandlung Just-In-Time-Debuggen zu aktivieren, fügen Sie diese Einstellungen hinzu:

- Legen Sie im Abschnitt `system.windows.forms` der Datei *machine.config* oder *\<app name>.exe.config* den Wert `jitDebugging` auf `true` fest:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- In einer C++-Windows Forms-Anwendung muss auch `DebuggableAttribute` in einer *CONFIG*-Datei oder im Code auf `true` festgelegt werden. Bei der Kompilierung mit [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) und ohne [/Og](/cpp/build/reference/og-global-optimizations) wird dieses Attribut vom Compiler für Sie festgelegt. Wenn Sie jedoch einen nicht optimierten Releasebuild debuggen möchten, müssen Sie `DebuggableAttribute` festlegen, indem Sie in der Datei *AssemblyInfo.cpp* der App die folgende Zeile hinzufügen:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Verwenden von Just-In-Time-Debuggen
Dieses Beispiel führt Sie durch das Just-in-Time-Debuggen, wenn eine App einen Fehler auslöst.

- Zum Durchführen dieser Schritte muss Visual Studio installiert sein. Wenn Sie nicht über Visual Studio verfügen, können Sie die kostenlose [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15) herunterladen.

- Stellen Sie sicher, dass Just-In-Time-Debuggen in **Extras** > **Optionen** > **Debuggen** > **Just-In-Time** [aktiviert](#BKMK_Enabling) ist.

In diesem Beispiel erstellen Sie in Visual Studio eine C#-Konsolen-App, die eine [NullReferenceException](/dotnet/api/system.nullreferenceexception) auslöst.

1. Erstellen Sie in Visual Studio eine C#-Konsolen-App (**Datei** > **Neu** > **Projekt** > **Visual C#**  > **Konsolenanwendung**) mit dem Namen *ThrowsNullException*. Weitere Informationen zur Erstellung von Projekten finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../get-started/csharp/tutorial-wpf.md).

1. Wenn das Projekt in Visual Studio geöffnet wird, öffnen Sie die Datei *Program.cs*. Ersetzen Sie die Main()-Methode durch den folgenden Code, durch den eine Zeile in der Konsole ausgegeben und dann eine „NullReferenceException“ ausgelöst wird:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Wählen Sie zum Erstellen der Projektmappe entweder die Konfiguration **Debug** (Standard) oder **Release**, und wählen Sie dann **Build** > **Projektmappe neu erstellen** aus.

   > [!NOTE]
   > - Wählen Sie für vollständiges Debuggen die Konfiguration **Debug**.
   > - Wenn Sie die Konfiguration [Release](../debugger/how-to-set-debug-and-release-configurations.md) auswählen, müssen Sie [Nur eigenen Code](../debugger/just-my-code.md) deaktivieren. Deaktivieren Sie unter **Extras** > **Optionen** > **Debuggen** die Option **Nur meinen Code aktivieren**.

   Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

1. Öffnen Sie die erstellte App *ThrowsNullException.exe* im C#-Projektordner ( *...\ThrowsNullException\ThrowsNullException\bin\Debug* oder *...\ThrowsNullException\ThrowsNullException\bin\Release*).

   Folgendes Befehlsfenster sollte angezeigt werden:

   ![Screenshot der Konsole für „ThrowsNullException.exe“, die eine unbehandelte NULL-Verweis-Ausnahme auslöst (System.NullReferenceException).](../debugger/media/throwsnullexceptionconsole.png)

1. Das Dialogfeld **Just-in-Time-Debugger auswählen** wird geöffnet.

   ![Screenshot des Dialogfelds „Just-in-Time-Debugger auswählen“, das angezeigt wird, nachdem die Ausnahme im Konsolenfenster von „ThrowsNullException.exe“ angezeigt wurde.](../debugger/media/justintimedialog.png)

   Wählen Sie unter **Verfügbare Debugger** die Option **Neue Instanz von \<your preferred Visual Studio version/edition>** aus, sofern diese noch nicht ausgewählt war.

1. Klicken Sie auf **OK**.

   Das Projekt „ThrowsNullException“ wird in einer neuen Instanz von Visual Studio geöffnet, wobei die Ausführung in der Zeile angehalten wurde, die die Ausnahme ausgelöst hat:

   ![Screenshot des Projekts „ThrowsNullException“ in Visual Studio, wobei die Zeile im Quellcode hervorgehoben ist, die die Ausnahme ausgelöst hat.](../debugger/media/nullreferencesecondinstance.png)

Sie können an dieser Stelle mit dem Debuggen beginnen. Wenn Sie eine echte App debuggen, müssen Sie herausfinden, warum der Code die Ausnahme auslöst.

> [!CAUTION]
> Wenn die App nicht vertrauenswürdigen Code enthält, wird ein Dialogfeld mit einer Sicherheitswarnung angezeigt, sodass Sie entscheiden können, ob das Debuggen fortgesetzt werden soll. Bevor Sie mit dem Debuggen fortfahren, entscheiden Sie, ob Sie den Code als vertrauenswürdig einstufen. Haben Sie den Code selbst geschrieben? Wenn die Anwendung auf einem Remotecomputer ausgeführt wird, erkennen Sie den Namen des Prozesses? Wenn die App lokal ausgeführt wird, wägen Sie die Wahrscheinlichkeit ab, dass bösartiger Code auf Ihrem Computer ausgeführt wird. Wenn Sie den Code als vertrauenswürdig einstufen, wählen Sie **OK** aus. Wählen Sie andernfalls **Abbrechen** aus.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Problembehandlung beim Just-In-Time-Debuggen

Wenn beim Absturz einer App Just-In-Time-Debuggen nicht gestartet wird, obwohl es in Visual Studio aktiviert ist:

- Möglicherweise erfolgt die Fehlerbehandlung auf dem Computer durch die Windows-Fehlerberichterstattung.

  Um dieses Problem zu beheben, fügen Sie im Registrierungs-Editor den folgenden Registrierungsschlüsseln den auf **Deaktiviert** festgelegten **DWORD-Wert** mit auf **1** festgelegten **Wertdaten** hinzu:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Für 64-Bit-Computer): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Weitere Informationen finden Sie unter [.WER Settings](/windows/desktop/wer/wer-settings) (.WER-Einstellungen, in englischer Sprache).

- Ein bekanntes Windows-Problem kann dazu führen, dass der Just-In-Time-Debugger fehlschlägt.

  Sie beheben das Problem, indem Sie den folgenden Registrierungsschlüsseln einen auf **Auto** festgelegten **DWORD-Wert** mit auf **1** festgelegten **Wertdaten** hinzufügen:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Für 64-Bit-Computer): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Möglicherweise werden während des Just-In-Time-Debuggens die folgenden Fehlermeldungen angezeigt:

- **An den abstürzenden Prozess kann nicht angehängt werden. Das angegebene Programm ist keine MS-DOS- oder Windows-Anwendung.**

    Es wurde versucht, den Debugger mit einem Prozess zu verbinden, der unter einem anderen Benutzer ausgeführt wird.

    Um dieses Problem zu umgehen, öffnen Sie in Visual Studio **Debuggen** > **An den Prozess anhängen**, und suchen Sie in der Liste **Verfügbare Prozesse** den Prozess, den Sie debuggen möchten. Falls Sie den Namen des Prozesses nicht kennen, suchen Sie im Dialogfeld **Just-In-Time-Debugger von Visual Studio** die Prozess-ID. Wählen Sie den Prozess in der Liste **Verfügbare Prozesse** aus, und klicken Sie auf **Anfügen**. Wählen Sie **Nein** aus, um das Just-in-Time-Debugger-Dialogfeld zu schließen.

- **Der Debugger konnte nicht gestartet werden, da kein Benutzer angemeldet ist.**

    Da kein Benutzer bei der Konsole angemeldet ist, ist keine Benutzersitzung vorhanden, um das Dialogfeld für Just-In-Time-Debuggen anzuzeigen.

    Um dieses Problem zu beheben, melden Sie sich beim Computer an.

- **Die Klasse ist nicht registriert.**

    Der Debugger hat versucht, eine nicht registrierte COM-Klasse zu erstellen. Die Ursache ist wahrscheinlich ein Installationsproblem.

    Beheben Sie dieses Problem, indem Sie Visual Studio mithilfe des Visual Studio-Installers neu installieren oder reparieren.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Optionen, Debuggen, Dialogfeld „Just-In-Time“](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
