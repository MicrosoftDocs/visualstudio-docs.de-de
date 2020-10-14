---
title: Bildschirm- und Stimmaufzeichnung während der Testausführung
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2366e77b0b66e2a31ce17e1aefb9240e4f45df2d
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928644"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Vorgehensweise: Einschließen von Bildschirm- und Stimmenaufzeichnungen während der Tests mit Testeinstellungen

Im Konfigurations-Editor in Visual Studio können Sie den Adapter für diagnostische Daten konfigurieren, der den Bildschirm und die Stimme des Benutzers aufzeichnet, der den Test ausführt. Dieser Adapter für diagnostische Daten speichert eine Bildschirm- und Stimmenaufzeichnung der Desktopsitzung während des Tests. Die Aufzeichnung wird mit dem Testergebnis gespeichert, oder sie kann einem Fehler angefügt werden. Andere Teammitglieder können die Videoaufzeichnungen verwenden, um schwer zu reproduzierende Anwendungsfehler zu isolieren.

> [!WARNING]
> Bei der Bildschirm- und Stimmenaufzeichnung werden Konfigurationen mit mehreren Monitoren nicht unterstützt.

Die Bildschirm- und Stimmenaufzeichnung kann sowohl für manuelle als auch für automatisierte Tests verwendet werden. Wenn Sie beispielsweise einen Test der codierten UI remote ausführen, können Sie den Desktop aufzeichnen, um die Ausführung des Tests der codierten UI anzuzeigen. Weitere Informationen zum Erstellen von Bildschirm- und Stimmenaufzeichnung über eine Remoteverbindung finden Sie unter [Vorgehensweise: Einrichten Ihres Test-Agents, um Tests auszuführen, die mit dem Desktopcomputer interagieren](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>So konfigurieren Sie Bildschirm- und Stimmenaufzeichnung für Ihre Testeinstellungen

1. Öffnen Sie die Testeinstellungen, die Sie für die Bildschirm- und Stimmenaufzeichnung konfigurieren möchten. Weitere Informationen finden Sie unter [Collect diagnostic data while testing (Azure Test Plans) (Sammeln von Diagnosedaten beim Testen (Azure Test Plans))](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) oder [Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md).

2. Wählen Sie in den Testeinstellungen die **Rolle** aus, die für die Bildschirm- und Stimmaufzeichnung verwendet werden soll.

    > [!NOTE]
    > Bei manuellen und automatisierten Tests ist dies der Computer, auf dem die Tests ausgeführt werden.

3. Wählen Sie den **Bildschirm- und Sprachrecorder** aus, und klicken Sie dann auf **Konfigurieren**.

     Das Dialogfeld **Configure Diagnostic Data Adapter – Screen and Voice Recorder** (Adapter für diagnostische Daten konfigurieren – Bildschirm- und Sprachrecorder) wird angezeigt.

     ![Videokonfiguration](../test/media/testsettingvideoconfiggdr.png)

4. Optional: Klicken Sie auf **Stimmaufzeichnung aktivieren**, um Audioinhalte aufzuzeichnen.

5. Optional: Aktivieren Sie das Kontrollkästchen neben **Bei erfolgreichem Testfall Aufzeichnung speichern**, um festzulegen, dass die Bildschirm- und Stimmaufzeichnung sowohl für fehlgeschlagene als auch für erfolgreiche Tests gespeichert wird.

    > [!WARNING]
    > Wenn Sie **Bei erfolgreichem Testfall Aufzeichnung speichern** aktivieren, wird die Aufzeichnung zusammen mit den Testergebnissen gespeichert, wodurch Speicherplatz auf dem Server belegt wird. Sie können das **Test Attachment Cleaner**-Tool verwenden, um diese Anhänge zu löschen.

6. Konfigurieren Sie unter **Qualität der Bildschirmaufzeichnung** die folgenden Dropdownlistenoptionen:

    1. **Bildfrequenz:** Geben Sie an, wie viele Frames pro Sekunde in der Bildschirm- und Stimmenaufzeichnung verwendet werden sollen. Der Standardwert ist 4 Frames pro Sekunde. Werte zwischen 2 und 20 sind zulässig.

    2. **Bitrate:** Geben Sie an, wie viele Kilobyte pro Sekunde in der Bildschirm- und Stimmenaufzeichnung verwendet werden sollen. Der Standardwert ist 512. Werte zwischen 512 und 10.000 sind zulässig.

    3. **Qualität (1 bis 100):** Sie können die Qualität der Bildschirm- und Stimmaufzeichnung angeben, indem Sie einen Bereich zwischen 1 und 100 auswählen. Der Standardwert ist 50 (mittlerer Bereich).

7. Klicken Sie auf **OK**. Die Einstellungen für Diagnoseablaufverfolgungs-Sammler werden jetzt konfiguriert und für die Testeinstellungen gespeichert.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Um die Konfiguration dieses Adapter für diagnostische Daten zurückzusetzen, wählen Sie **Auf Standardkonfiguration zurücksetzen** für Visual Studio und **Standard wiederherstellen** für Microsoft Test Manager aus.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Klicken Sie in Visual Studio auf **Auf Standardkonfiguration zurücksetzen**, um die Konfiguration für diesen Adapter für diagnostische Daten zurückzusetzen.
    ::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Collect diagnostic data while testing (Azure Test Plans) (Sammeln von Diagnosedaten beim Testen (Azure Test Plans))](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Collect diagnostic data in manual tests (Azure Test Plans) (Sammeln von Diagnosedaten in manuellen Tests (Azure Test Plans))](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md)
- [Ausführen manueller Tests (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)