---
title: Fehler bei Remoteanmeldung von Arbeitsgruppe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f56c8d8e0113b400e9d9cd072ba16f304cd6192
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870843"
---
# <a name="error-workgroup-remote-logon-failure"></a>Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe
Inhalt dieses Fehlers:

 Fehler bei der Anmeldung: Unbekannter Benutzername oder ungültiges Kennwort.

 **Ursache**

 Dieser Fehler kann auftreten, wenn Sie von einem Computer in einer Arbeitsgruppe debuggen und versuchen, eine Verbindung mit einem Remotecomputer herzustellen. Mögliche Ursachen sind:

- Es gibt kein Konto auf dem Remotecomputer mit übereinstimmendem Namen und Kennwort.

- Wenn der Visual Studio-Computer und der Remotecomputer sich beide in Arbeitsgruppen befinden, wird dieser Fehler u.U. aufgrund der Standardeinstellung für die **Lokale Sicherheitsrichtlinie** auf dem Remotecomputer ausgelöst. Die Standardeinstellung für die **Lokale Sicherheitsrichtlinie** ist **Nur Gast – lokale Benutzer authentifizieren sich als Gast**. Um in diesem Setup zu debuggen, müssen Sie die Einstellung auf dem Remotecomputer in **Klassisch – lokale Benutzer authentifizieren sich als sie selbst** ändern.

> [!NOTE]
> Sie müssen Administrator sein, um die folgenden Aufgaben ausführen zu können.

### <a name="to-open-the-local-security-policy-window"></a>So öffnen Sie das Fenster "Lokale Sicherheitsrichtlinie"

1. Starten Sie das Microsoft Management Console-Snap-In **secpol.msc**. Geben Sie "secpol.msc" in die Windows-Suche, das Windows-Ausführungsfeld oder in einer Eingabeaufforderung ein.

### <a name="to-add-user-rights-assignments"></a>So fügen Sie Benutzerrechtezuordnungen hinzu

1. Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.

2. Erweitern Sie den Ordner **Lokale Richtlinien**.

3. Klicken Sie auf **Zuweisen von Benutzerrechten**.

4. Doppelklicken Sie in der Spalte **Richtlinie** auf **Debuggen von Programmen**, um die aktuell zugewiesenen Richtlinien der lokalen Gruppe im Dialogfeld **Lokale Sicherheitsrichtlinieneinstellung** anzuzeigen.

     ![Benutzerrechte für Richtlinie zur lokalen Sicherheit](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. Klicken Sie auf die Schaltfläche **Benutzer oder Gruppe hinzufügen**, um neue Benutzer hinzuzufügen.

### <a name="to-change-the-sharing-and-security-model"></a>So ändern Sie das Modell für gemeinsame Nutzung und das Sicherheitsmodell

1. Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.

2. Erweitern Sie den Ordner **Lokale Richtlinien**.

3. Klicken Sie auf **Sicherheitsoptionen**.

4. Doppelklicken Sie in der Spalte **Richtlinie** auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.

5. Ändern Sie im Dialogfeld **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** den Wert in **Klassisch – lokale Benutzer authentifizieren sich als sie selbst**, und klicken Sie auf **Übernehmen**.

     ![Sicherheitsoptionen für Richtlinie zur lokalen Sicherheit](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)