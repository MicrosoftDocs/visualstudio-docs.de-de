---
title: Verwalten von Testcontrollern und Test-Agents
description: Hier erfahren Sie, wie Testcontroller und Test-Agents verwaltet werden, nachdem diese zum ersten Mal installiert und konfiguriert wurden.
ms.custom: SEO-VS-2020
ms.date: 09/18/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9a416dc64a9d49d14e367a04023f067c7b595c
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329639"
---
# <a name="manage-test-controllers-and-test-agents"></a>Verwalten von Testcontrollern und Test-Agents

Wenn Sie Visual Studio verwenden möchten, um Tests remote auszuführen, Verteilen Sie Tests über mehrere Computer. Um Auslastungstests auszuführen, müssen Sie einen Testcontroller, Test-Agents und eine Testeinstellungsdatei konfigurieren. In diesem Thema wird beschrieben, wie Testcontroller und Test-Agents verwaltet werden, nachdem diese zum ersten Mal installiert und konfiguriert worden sind.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Wenn Sie mit Microsoft Test Manager Tests in der Laborumgebung ausführen, verwalten Sie Testcontroller und deren Agents, indem Sie den **Testcontroller-Manager** im **Lab-Center** für Microsoft Test Manager verwenden. Dieses Thema gilt nur, wenn Sie Visual Studio verwenden, um Tests auszuführen.
::: moniker-end

Weitere Informationen darüber, wie Testcontroller und Test-Agents installiert und konfiguriert werden, um Tests in Visual Studio auszuführen, finden Sie unter [Configure test agents and controllers (Konfigurieren von Test-Agents und Testcontrollern)](../test/configure-test-agents-and-controllers-for-load-tests.md).

Zum Konfigurieren und Überwachen des Testcontrollers und sämtlicher registrierter Agents müssen Sie über eine Testeinstellungsdatei in Ihrem Testprojekt verfügen, die die auszuführenden Tests umfasst. Öffnen Sie die Testeinstellungsdatei, und wählen Sie **Rolle** und **Testcontroller verwalten** aus dem Dropdownmenü für das Feld **Controller** aus.

Bei einem Auslastungstestprojekt können Sie auch **Testcontroller verwalten** aus dem Menü **Auslastungstest** auswählen.

## <a name="add-a-test-agent-to-a-test-controller"></a>Hinzufügen eines Test-Agents zu einem Testcontroller

Möglicherweise möchten Sie einen Test-Agent einem anderen Testcontroller hinzufügen, oder Sie müssen möglicherweise einem Testcontroller, den Sie eben installiert haben, einen Test-Agent hinzufügen.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>So fügen Sie einen Test-Agent einem Testcontroller hinzu

1. Klicken Sie auf **Start** > **Test Agent-Konfigurationstool**.

     Das Dialogfeld **Test-Agent konfigurieren** wird angezeigt.

    > [!NOTE]
    > Ein Test-Agent muss bereits installiert sein, um ihn einem Testcontroller hinzufügen zu können. Weitere Informationen zum Installieren eines Test-Agents finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

2. Ihnen werden zwei Optionen für die Ausführung des Test-Agents angezeigt:

   - **Dienst:** Wenn Sie keine automatisierten Tests ausführen müssen, die mit dem Desktop interagieren (z. B. Tests der programmierten UI oder Erstellung einer Videoaufzeichnung während der Testläufe), wählen Sie unter **Test-Agent ausführen als** die Option **Dienst** aus. Der Test-Agent wird als Dienst gestartet. Wählen Sie **Weiter** aus.

      Wenn der Test-Agent als Dienst gestartet wird, können Sie jetzt die Details zum Benutzer eingeben.

      1. Geben Sie in **Benutzername** den Namen ein.

      2. Geben Sie in **Kennwort** das Kennwort ein.

        |**Wichtige Benutzerkontoinformationen**|
        |-|
        |– NULL-Kennwörter werden für Benutzerkonten nicht unterstützt.|
        |– Wenn Sie den IntelliTrace-Sammler oder die Netzwerkemulation verwenden möchten, muss das Benutzerkonto Mitglied der Gruppe „Administratoren“ sein.|
        |– Wenn der Agent-Benutzername nicht im Agent-Dienst vorhanden ist, wird er hinzugefügt. Dafür sind Berechtigungen für den Testcontroller erforderlich.|
        |– Der Benutzer, der den Testcontroller verwenden möchte, muss im Benutzerkonto des Testcontrollers angemeldet sein. Andernfalls können die Tests nicht anhand des Controllers ausgeführt werden.|

   - **Interaktiver Prozess:** Wenn Sie automatisierte Tests ausführen möchten, die mit dem Desktop interagieren (z. B. Tests der programmierten UI oder Erstellung einer Videoaufzeichnung während der Testläufe), wählen Sie **Interaktiver Prozess** aus. Der Test-Agent wird nicht als Dienst, sondern als interaktiver Prozess gestartet.

      Wenn der Test-Agent als Prozess gestartet wird, können Sie auf der nächsten Seite die Details zum Benutzer eingeben und weitere Optionen festlegen.

      1. Geben Sie in **Benutzername** den Namen ein.

      2. Geben Sie in **Kennwort** das Kennwort ein.

        > [!NOTE]
        > Wenn Sie den Test-Agent mit einem anderen Benutzer (nicht der momentan aktive Benutzer) zur Ausführung als interaktiver Prozess konfigurieren, müssen Sie den Computer neu starten und sich als dieser andere Benutzer anmelden, um den Agent starten zu können. Zudem werden NULL-Kennwörter nicht für Benutzerkonten unterstützt. Wenn Sie den IntelliTrace-Sammler oder die Netzwerkemulation verwenden möchten, muss das Benutzerkonto Mitglied der Gruppe "Administratoren" sein.

      3. Um sicherzustellen, dass ein Computer mit einem Test-Agent nach dem Neustart Tests ausführen kann, können Sie den Computer für die automatische Anmeldung als Test-Agent-Benutzer einrichten. Klicken Sie auf **Automatisch anmelden**. Dadurch werden der Benutzername und das Kennwort in verschlüsselter Form in der Registrierung gespeichert.

      4. Um sicherzustellen, dass der Bildschirmschoner deaktiviert ist, wählen Sie **Sicherstellen, dass Bildschirmschoner deaktiviert ist** aus, da andernfalls automatisierte Tests, die mit dem Desktop interagieren müssen, behindert werden können.

        > [!WARNING]
        > Durch die automatische Anmeldung und das Deaktivieren des Bildschirmschoners entstehen Sicherheitsrisiken. Wenn Sie die automatische Anmeldung aktivieren, ermöglichen Sie es anderen Benutzern, den betreffenden Computer zu starten und das Konto zu verwenden, das automatisch angemeldet wird. Wenn Sie den Bildschirmschoner deaktivieren, wird der Benutzer möglicherweise nicht aufgefordert, sich anzumelden, um die Sperre des Computers aufzuheben. So kann jede Person mit physikalischem Zugang zum Computer auf den Computer zugreifen. Wenn Sie diese Funktionen auf einem Computer aktivieren, sollten Sie sicherstellen, dass der Computer physikalisch sicher ist. Ein solcher Computer befindet sich z. B. in einem physikalisch sicheren Labor. (Durch Deaktivieren des Kontrollkästchens **Sicherstellen, dass der Bildschirmschoner deaktiviert ist** wird der Bildschirmschoner nicht aktiviert.)

3. Klicken Sie auf **Mit Testcontroller registrieren**, um diesen Agent bei einem anderen Testcontroller zu registrieren. Geben Sie den Namen des Testcontrollers gefolgt von einem Doppelpunkt **:** und der Portnummer ein, die Sie in **Test-Agent mit dem folgenden Testcontroller registrieren** verwenden. Geben Sie beispielsweise **agent1:6901** ein.

    > [!NOTE]
    > Die Standardportnummer ist 6901.

4. Wählen Sie **Einstellungen übernehmen**, um die Änderungen zu speichern. Schließen Sie zunächst das Dialogfeld **Konfigurationszusammenfassung** und anschließend das **Test Agent-Konfigurationstool**.

> [!WARNING]
> Wenn der Agent derzeit für die Ausführung mit einem anderen Testcontroller konfiguriert ist, müssen Sie den Test-Agent aus diesem Controller entfernen.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Entfernen eines Test-Agents aus einem Testcontroller

Test-Agents können nur entfernt werden, wenn sie sich im Offlinezustand befinden.

::: moniker range="vs-2017"
> [!NOTE]
> Diese Vorgehensweise können Sie nicht zum Entfernen von Agents verwenden, die als Teil einer Laborumgebung bei einem Controller registriert sind. Um diese Agents von einem Controller zu entfernen, müssen Sie die Umgebung mithilfe von Microsoft Test Manager entfernen.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Diese Vorgehensweise können Sie nicht zum Entfernen von Agents verwenden, die als Teil einer Laborumgebung bei einem Controller registriert sind.
::: moniker-end

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>So entfernen Sie einen Test-Agent aus einem Testcontroller

::: moniker range=">=vs-2019"
In Visual Studio 2019 können Sie einen Test-Agent nicht entfernen, wenn der Testcontroller bei einem Projekt registriert ist.
::: moniker-end
Wenn der Testcontroller bei keinem Projekt registriert ist, führen Sie die folgenden Schritte aus.

1. Öffnen Sie die Testeinstellungsdatei in Visual Studio für Ihr Testprojekt, und wählen Sie **Rolle** und **Testcontroller verwalten** aus dem Dropdownmenü für das Feld **Controller** aus.

   Das Dialogfeld **Testcontroller verwalten** wird angezeigt.

2. Geben Sie in der Dropdownliste **Controller** den Namen des Computers ein, auf dem der Testcontroller eingerichtet wurde. Wenn Sie bereits einen bestimmten Testcontroller verwaltet haben, können Sie den Namen in der Liste auswählen.

3. Wählen Sie im Bereich **Agents** den Namen des Test-Agents aus. Wenn der Agent noch immer online ist, klicken Sie auf **Offline**. Klicken Sie auf **Entfernen**, um ihn zu entfernen.

   > [!NOTE]
   > Durch Entfernen eines Test-Agents wird nur die Zuordnung zum Testcontroller aufgehoben. Unter **Programme und Funktionen** auf dem Test-Agent-Computer können Sie den Test-Agent vollständig deinstallieren.

::: moniker range="vs-2017"
Wenn der Testcontroller bei einem Projekt registriert ist, entfernen Sie den Agent mithilfe von Microsoft Test Manager.
::: moniker-end

## <a name="change-the-settings-for-a-test-agent"></a>Ändern der Einstellungen für einen Test-Agent

Der Status des Test-Agents kann einen der folgenden Werte aufweisen:

|Status|Beschreibung|
|-|-----------------|
|Test wird ausgeführt|Ausführen von Tests|
|Bereit|Verfügbar zum Ausführen von Tests oder Sammeln von Daten und Diagnosen|
|Offline|Nicht verfügbar zum Ausführen von Tests und/oder Sammeln von Daten und Diagnosen|
|Verbindung getrennt|Test-Agent wurde nicht gestartet|

Mit dem folgenden Verfahren können Sie den Status und andere Einstellungen für einen Test-Agent ändern.

### <a name="to-change-the-settings-of-a-test-agent"></a>So ändern Sie die Einstellungen eines Test-Agents

::: moniker range="vs-2017"
> [!NOTE]
> Wenn der Test-Agent bei einem Testcontroller registriert ist, der bei einem Projekt registriert ist, ändern Sie die Einstellungen in Microsoft Test Manager.
::: moniker-end

1. Wählen Sie zum Konfigurieren und Überwachen des Testcontrollers und der registrierten Agents für einen Auslastungstest das Menü **Auslastungstest** in Visual Studio aus, und klicken Sie dann auf **Testcontroller verwalten**. Öffnen Sie für andere Test die Testeinstellungsdatei für Ihr Testprojekt in Visual Studio, und wählen Sie **Rolle** und **Testcontroller verwalten** aus dem Dropdownmenü für das Feld **Controller** aus.

   Das Dialogfeld **Testcontroller verwalten** wird geöffnet.

1. Wählen Sie in der Testcontrollerliste den Namen des Testcontrollers aus, dessen Test-Agents Sie ändern möchten. Wenn der Testcontroller nicht in der Liste angezeigt wird, überprüfen Sie, ob der Testcontroller ordnungsgemäß registriert wurde. Weitere Informationen finden Sie in der folgenden Prozedur zum Konfigurieren eines Testcontrollers.

1. (Optional) Wählen Sie Im Bereich **Test-Agents** den Test-Agent-Computer aus, dessen Eigenschaften Sie ändern möchten.

1. Klicken Sie auf **Eigenschaften**.

1. Ändern Sie die folgenden Test-Agent-Eigenschaften nach Bedarf:

|Test-Agent-Eigenschaft|Beschreibung|
|-|-----------------|
|**Gewichtung**|Wird bei Verwendung von Test-Agents mit unterschiedlicher Leistungsfähigkeit zum Verteilen der Last verwendet. Ein Test-Agent mit einer Gewichtung von 100 erhält beispielsweise doppelt so viel Last wie ein Test-Agent mit einer Gewichtung von 50.|
|**IP-Wechsel**|Wird zum Konfigurieren des IP-Wechsels verwendet. Durch IP-Wechsel kann ein Test-Agent für Anfragen an einen Server einen Bereich von IP-Adressen verwenden. Auf diese Weise werden Aufrufe von anderen Clientcomputern simuliert.<br /><br /> IP-Wechsel ist wichtig, wenn der Auslastungstest auf eine Webfarm zugreift. Die meisten Lastenausgleichsmodule etablieren die Zugehörigkeit zwischen einem Client und einem bestimmten Webserver über die IP-Adresse des Clients. Wenn alle Anfragen von einem einzigen Client zu kommen scheinen, wird die Auslastung vom Lastenausgleichsmodul nicht ausgeglichen. Um innerhalb der Webfarm einen guten Lastenausgleich zu erhalten, stellen Sie sicher, dass die Anfragen von mehreren IP-Adressen kommen. **Hinweis**:  Sie können entweder einen Netzwerkadapter angeben oder **(Keine zugewiesen)** verwenden, um automatisch einen derzeit nicht verwendeten Adapter auszuwählen. <br /><br /> Sie können die IP-Wechselfunktion nur verwenden, wenn der Visual Studio Test Agent-Dienst als Benutzer in der Administratorengruppe für diesen Agent-Computer ausgeführt wird. Dieser Benutzername wird während des Agent-Setups ausgewählt, kann jedoch durch Ändern der Diensteigenschaften und erneutes Starten des Diensts geändert werden.<br /><br /> Wenn Sie die ordnungsgemäße Funktion des IP-Wechsels überprüfen möchten, aktivieren Sie die IIS-Protokollierung auf dem Webserver, und überprüfen Sie mit der IIS-Protokollfunktion, ob die Anforderungen von den konfigurierten IP-Adressen kommen.|
|**Attribute**|Satz von Name-Wert-Paaren, die bei der Auswahl von Test-Agents verwendet werden können. Beispielsweise könnte ein Test ein bestimmtes Betriebssystem (OS) erfordern. Sie können Attribute auf der Registerkarte **Rollen** der Testeinstellungsdatei hinzufügen und sie verwenden, um einen Test-Agent auswählen, der über entsprechenden Attribute verfügt. Wenn Sie einen Test auf mehreren Computern ausführen möchten, erstellen Sie ein Attribut in der Testeinstellungsrolle, die konfiguriert wird, um die Tests auszuführen, und konfigurieren Sie anschließend ein entsprechendes Attribut für jeden Test-Agent, den Sie in dieser Rolle verwendet möchten. **Hinweis**:  Diese Einstellung ist nur für Test-Agents verfügbar, die bei einem Testcontroller registriert wurden, der bei keinem Projekt registriert ist, da diese Attribute nur in Testeinstellungen für Visual Studio verwendet werden.|

Änderungen der Test-Agent-Gewichtung und der Test-Agent-Attribute werden sofort wirksam, haben jedoch keine Auswirkungen auf laufende Tests. Änderungen des IP-Adressbereichs werden nach einem Neustart des Testcontrollers wirksam.

(Optional) Um den Status eines Test-Agents zu ändern, wählen Sie den Agent in der Liste aus, und wählen Sie dann je nach aktuellem Status des Agents in den verfügbaren Optionen die gewünschte Aktion aus.

> [!NOTE]
> Wenn der Test-Agent als Prozess ausgeführt wird, verwalten Sie dessen Status über das Infobereichssymbol auf dem Computer, auf dem dieser installiert ist. Darauf wird der Status des Test-Agents angezeigt. Sie können mit diesem Tool den Agent starten, beenden oder neu starten, wenn er als Prozess ausgeführt wird.

## <a name="configure-a-test-controller"></a>Konfigurieren eines Testcontrollers

Einen Testcontroller konfigurieren Sie im **Konfigurationstool für Team-Testcontroller**. Beim Konfigurieren des Testcontrollers können Sie diesen bei einer anderen Projektsammlung registrieren oder die Registrierung des Testcontrollers bei einer Projektsammlung aufheben.

Wenn Sie den Testcontroller bei Ihrer Team Foundation Server-Projektsammlung registrieren möchten, muss das für den Testcontrollerdienst verwendete Konto ein Mitglied der Gruppe „Testdienstkonten für Projektsammlung“ für die Projektsammlung sein, oder das zum Ausführen des Testcontroller-Konfigurationstools verwendete Konto muss ein Projektsammlungsadministrator sein.

> [!NOTE]
> Wenn Sie die Registrierung eines Testcontrollers bei einer Projektsammlung aufheben, die vorhandene Umgebungen in einer Projektsammlung besitzt, werden die Umgebungen nach wie vor beibehalten, wenn Sie diese Projektsammlung verschoben haben und erneut den Testcontroller für die verschobene Projektsammlung registrieren.

### <a name="to-configure-a-test-controller"></a>So konfigurieren Sie einen Testcontroller

1. Sie können den Testcontroller jederzeit neu konfigurieren. Klicken Sie dazu auf **Start** > **Test Controller-Konfigurationstool**.

     Das Dialogfeld **Testcontroller konfigurieren** wird angezeigt.

2. Wählen Sie den Benutzer aus, dessen Anmeldekonto für den Testcontrollerdienst verwendet werden soll.

    > [!NOTE]
    > NULL-Kennwörter werden für Benutzerkonten nicht unterstützt.

4. (Optional) Wenn Sie den Testcontroller nicht in einer Laborumgebung verwenden, sondern lediglich Tests in Visual Studio ausführen möchten, deaktivieren Sie **Testcontroller bei Teamprojektauflistung registrieren**.

5. (Optional) Wählen Sie zum Konfigurieren des Testcontrollers für Auslastungstests **Testcontroller für Auslastungstests konfigurieren** aus. Geben Sie dann die SQL Server-Instanz unter **Datenbank für Auslastungstestergebnisse in folgender SQL Server-Instanz erstellen** ein.

> [!NOTE]
> Weitere Informationen zur Problembehandlung finden Sie unter [Install and configure test agents (Installieren und Konfigurieren von Test-Agents)](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Verwalten des Agents beim Ausführen der Tests mit einem Testcontroller

Wenn Sie den Testeinstellungen für Visual Studio Rollen für die Anwendung hinzufügen, können Sie für jede der Rollen Agent-Eigenschaften hinzufügen. Damit bestimmen Sie, welche Test-Agents für diese Rolle verfügbar sind. Wenn Sie die Tests unter Verwendung dieser Testeinstellungen ausführen, bestimmt der für die Ausführung ausgewählte Testcontroller die Verfügbarkeit der erforderlichen Agents. Wenn die Verfügbarkeit von Agents bestimmt wird, können die folgenden Situationen auftreten:

- Für die Rolle, die die Tests ausführen muss, ist kein Agent verfügbar. Die Tests können nicht ausgeführt werden. Sie können eine der folgenden Aktionen ausführen und dann die Tests erneut ausführen:

  - Sie können warten, bis ein Agent für die Rolle zum Ausführen der Tests verfügbar ist.

  - Wenn Agents offline sind, die für die Rolle verwendet werden können, können Sie den Agent neu starten, damit er verfügbar ist.

  - Sie können dem Testcontroller einen weiteren Agent mit den richtigen Agent-Eigenschaften für diese Rolle hinzufügen.

  - Sie können die Agent-Eigenschaften für diese Rolle in den Testeinstellungen ändern, um weitere andere Agents zu aktivieren, die Sie verwenden möchten.

- Für eine oder mehrere Rollen, die Diagnosedatenadapter ausführen, ist kein Agent verfügbar. Die Tests können ausgeführt werden, der Diagnosedatenadapter kann jedoch nicht ausgeführt werden. Sie können die Tests ohne den Diagnosedatenadapter ausführen, oder Sie können eine der folgenden Aktionen ausführen und die Tests erneut ausführen:

  - Sie können warten, bis ein Agent für diese Rollen verfügbar ist.

  - Wenn für diese Rolle vorhandene Offline-Agents verwendet werden können, müssen Sie den Zustand des Agents im Menü **Test** unter **Testcontroller verwalten** in „Online“ ändern. Außerdem müssen Sie den Agent eventuell neu starten, wenn er vom Controller getrennt wurde.

  - Stellen Sie sicher, dass keiner der Agents, die Sie möglicherweise für diesen Testlauf benötigen, mit dem Ausführen von Tests ausgelastet ist. Sie können den Status aller Agents im Menü **Test** unter **Testcontroller verwalten** überprüfen.

  - Sie können dem Testcontroller einen weiteren Agent mit den richtigen Agent-Eigenschaften für die Rolle hinzufügen.

  - Sie können die Agent-Eigenschaften für die Rolle in den Testeinstellungen ändern, um weitere andere Agents zu aktivieren, die Sie verwenden möchten.

## <a name="load-tests-from-delay-signed-assemblies"></a>Laden von Tests von verzögert signierten Assemblys

Der Testcontroller und die Test-Agents können nur Testassemblys laden, bei denen es sich um stark signierte Assemblys oder nicht signierte Assemblys handelt. Einige Testassemblys sind verzögert signiert, da sie Zugriff auf Produktionsassemblys für die Anwendung benötigen. Diese Assemblys sind jedoch nicht stark signiert, da es sich dabei nur um Testassemblys handelt, die nicht verteilt werden. Diese Assemblys können nicht geladen werden, da sie verzögert signiert sind. Daher muss die Überprüfung von starken Namen für die Assemblys auf allen Computern deaktiviert werden, auf denen die Assembly einschließlich des Testcontrollercomputers geladen wird. Verwenden Sie *sn.exe* zum Deaktivieren der verzögert signierten Überprüfung. Das öffentliche Schlüsseltoken der verzögert signierten Assembly, für die die Überprüfung starker Namen übersprungen werden soll, muss möglicherweise ebenfalls eingeschlossen werden.

Verwenden Sie das Strong Name-Tool (*Sn.exe*) zum Deaktivieren der verzögert signierten Überprüfung.

Dadurch wird die Überprüfung starker Namen auf dem Computer, auf dem der Befehl ausgeführt wird, nur für die angegebene Assembly deaktiviert. Sie können den Befehl nur verwenden, wenn Sie über ausreichende Berechtigungen verfügen.

Aktivieren Sie die verzögert signierte Überprüfung nach dem Testlauf mit dem Befehl *SN.exe* erneut.

Es wird empfohlen, die Signaturüberprüfung mithilfe der *SN.exe*-Befehle in den Skripts zu deaktivieren und dann wieder zu aktivieren. Sie können die Überprüfung beispielsweise in einem Setupskript deaktivieren und in einem Bereinigungsskript wieder aktivieren.

## <a name="see-also"></a>Siehe auch

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
