---
title: Konfigurieren der Netzwerkemulation mithilfe von Testeinstellungen
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27de590cc40808eb3bebf18857c0ba4b254c39d1
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928657"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Vorgehensweise: Konfigurieren der Netzwerkemulation mithilfe von Testeinstellungen in Visual Studio

Sie können den Adapter für diagnostische Daten für das Testen einer Anwendung in verschiedenen Netzwerkumgebungen von Visual Studio konfigurieren. Er kann auch so konfiguriert werden, dass eine künstliche Netzwerklast oder ein Engpass beim Ausführen der Tests getestet wird.

> [!WARNING]
> Wenn Sie die Tests auf einem realen Netzwerk ausführen, das langsamer ist als das Netzwerk, das Sie emulieren, wird der Test weiterhin mit der langsameren Netzwerkgeschwindigkeit ausgeführt. Die Emulation kann die Netzwerkumgebung nur verlangsamen, sie jedoch nicht schneller machen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Im folgenden Verfahren wird beschrieben, wie die Netzwerkemulation über den Konfigurations-Editor konfiguriert wird. Diese Schritte gelten für den Konfigurations-Editor in Microsoft Test Manager und Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Im folgenden Verfahren wird beschrieben, wie die Netzwerkemulation über den Konfigurations-Editor konfiguriert wird. Diese Schritte gelten für den Konfigurations-Editor in Visual Studio.
::: moniker-end

> [!NOTE]
> Der Adapter für diagnostische Daten für die Netzwerkemulation gilt nur für Visual Studio-Testeinstellungen. Er wird nicht für Testeinstellungen in Microsoft Test Manager verwendet (ab Visual Studio 2017).

::: moniker range="vs-2017"
Für die Netzwerkemulation muss ein Konto mit Administratorrechten verwendet werden. Wenn Sie die Netzwerkemulation für eine lokale Rolle ausgewählt haben, mit der manuelle Tests ausgeführt werden, müssen Sie Microsoft Test Manager mit Administratorrechten starten. Wenn Sie Netzwerkemulation für eine beliebige andere Rolle ausgewählt haben, müssen Sie überprüfen, ob der Test-Agent auf dem Computer für diese Rolle ein Benutzerkonto verwendet, das Mitglied der Administratorgruppe ist. Weitere Informationen über das Einrichten des Kontos für Ihren Test-Agent finden Sie unter[Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).
::: moniker-end

> [!NOTE]
> Das Netzwerkdienstkonto, das das Standardkonto für den Test-Agent ist, ist kein Mitglied der Administratorgruppe.

**Wahre Netzwerkemulation**

Visual Studio verwendet softwarebasierte wahre Netzwerkemulation für alle Testtypen. Das gilt auch für Auslastungstests. Wahre Netzwerkemulation simuliert Netzwerkbedingungen durch direkte Bearbeitung der Netzwerkpakete. Der wahre Netzwerkemulator kann das Verhalten von Kabel- und Funknetzwerken mit einem zuverlässigen physischen Kanal (z. B. einem Ethernet) emulieren. Die folgenden Netzwerkattribute werden in wahre Netzwerkemulation integriert:

- Roundtripzeit für das Netzwerk (Wartezeit)

- Die Menge an verfügbarer Bandbreite

- Warteschlangenverhalten

- Paketverlust

- Neuanordnung von Paketen

- Fehlerweitergabe

Wahre Netzwerkemulation bietet auch Flexibilität beim Filtern von Netzwerkpaketen auf Grundlage von IP-Adressen oder Protokollen, z. B. TCP, UDP und ICMP.

Wahre Netzwerkemulation kann von netzwerkbasierten Entwicklern und Testern dazu verwendet werden, eine gewünschte Testumgebung zu emulieren, die Leistung zu bewerten, die Auswirkungen auf Änderung zu prognostizieren oder Entscheidungen zur Technologieoptimierung zu treffen. Im Vergleich zu Hardwareprüfständen ist wahre Netzwerkemulation eine weitaus günstigere und flexiblere Lösung.

## <a name="configure-network-emulation-for-your-test-settings"></a>Konfigurieren der Netzwerkemulation für die Testeinstellungen

Bevor Sie die Schritte in diesem Verfahren ausführen, müssen Sie die Testeinstellungen in Visual Studio öffnen und dann die Seite **Daten und Diagnose** auswählen.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>So konfigurieren Sie die Netzwerkemulation für die Testeinstellungen

1. Wählen Sie die Rolle aus, die für das Emulieren eines bestimmten Netzwerks verwendet werden soll.

    > [!NOTE]
    > Sie müssen den Netzwerkemulationsadapter nur entweder für die Clientrolle oder die Serverrolle konfigurieren. Sie müssen den Adapter nicht bei beiden Rollen verwenden. Der Adapter emuliert Netzwerkrauschen, das sich auf die Kommunikation zwischen beiden Rollen auswirkt. Daher muss der Adapter nicht bei beiden Rollen verwendet werden. Sofern dies nicht notwendig ist, sollten Sie eine Clientrolle für den Netzwerkemulationsadapter auswählen, um Mehraufwand bei der Serverrolle zu vermeiden.

2. Klicken Sie auf **Netzwerkemulation** und dann auf **Konfigurieren**.

     Das Dialogfeld zum Konfigurieren der Netzwerkemulation wird angezeigt.

3. Klicken Sie auf den Pfeil neben **Zu verwendendes Netzwerkprofil auswählen**, und wählen Sie den Netzwerktyp aus, den Sie beim Ausführen eines Tests emulieren möchten (z.B. **Kabel/DSL mit 768 KBit/s**).

    > [!WARNING]
    > Wenn Sie die Tests auf einem realen Netzwerk ausführen, das langsamer ist als das Netzwerk, das Sie emulieren, wird der Test mit der langsameren Netzwerkgeschwindigkeit ausgeführt. Die Emulation kann die Netzwerkumgebung nur verlangsamen, sie jedoch nicht schneller machen.

4. Wenn Sie den Adapter für diagnostische Daten für die Netzwerkemulation in die Testeinstellungen einschließen und beabsichtigen, den Adapter auf dem lokalen Computer zu verwenden, müssen Sie auch den Netzwerkemulationstreiber an einen Netzwerkadapter des Computers binden. Der Netzwerkemulationstreiber ist erforderlich, damit der Adapter für diagnostische Daten für die Netzwerkemulation funktioniert. Sie haben zwei Möglichkeiten, den Netzwerkemulationstreiber zu installieren und an den Adapter zu binden:

    - **Netzwerkemulationstreiber, die mit dem Test-Agent von Microsoft Visual Studio installiert wurden:** Der Test-Agent von Microsoft Visual Studio kann auf Remotecomputern und lokalen Computern verwendet werden. Wenn Sie Visual Studio Test Agent installieren, schließt der Installationsvorgang einen Konfigurationsschritt ein, bei dem der Netzwerkemulationstreiber an die Netzwerkkarte gebunden wird. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

    - **Netzwerkemulationstreiber, die mit Microsoft Visual Studio Test Professional installiert wurden:** Wenn Sie die Netzwerkemulation zum ersten Mal verwenden, werden Sie aufgefordert, den Netzwerkemulationstreiber mit einer Netzwerkkarte zu verbinden.

    > [!TIP]
    > Sie können den Netzwerkemulationstreiber auch über die Befehlszeile auf dem lokalen Computer installieren, ohne den Visual Studio-Test-Agent zu installieren. Verwenden Sie hierzu folgenden Befehl: **VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>Siehe auch

- [Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md)
- [Ausführen manueller Tests (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)
