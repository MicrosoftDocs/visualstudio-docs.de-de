---
title: Programm zur Verbesserung der Benutzerfreundlichkeit
description: In diesem Artikel erfahren Sie mehr über die Datenschutzeinstellungen in Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eae7e4726f720b1c9974682525bbe2a28ee38d5f
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97667935"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio

Das Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio (VSCEIP) wurde dafür entwickelt, Microsoft bei der kontinuierlichen Verbesserung von Visual Studio zu unterstützen. Dieses Programm [sammelt Informationen zu Fehlern](../ide/diagnostic-data-collection.md), Computerhardware und der Verwendung von Visual Studio durch die Benutzer, ohne diese bei ihren Aufgaben am Computer zu unterbrechen. Durch die gesammelten Informationen kann Microsoft einfacher ermitteln, welche Features verbessert werden müssen. In diesem Dokument wird erläutert, wie VSCEIP aktiviert oder deaktiviert werden kann.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Einstellungen für das Aktivieren oder Deaktivieren von VSCEIP-Telemetrie gelten nicht für „Problem melden“ in Visual Studio. Beim Melden eines Problems werden nur dann Protokolle gesammelt und an Microsoft gesendet, wenn Sie durch Klicken auf „Übermitteln“ Ihre Genehmigung dafür erteilen. Wenn Sie Protokolle verwalten möchten, bevor Sie diese per „Problem melden“ übermitteln, finden Sie weitere Informationen unter [Datenschutz in der Developer Community](./developer-community-privacy.md).

## <a name="opt-in-or-out"></a>Aktivierung oder Deaktivierung

VSCEIP ist standardmäßig aktiviert. Sie können es deaktivieren oder erneut aktivieren, indem Sie folgende Anweisungen befolgen:

1. Wählen Sie in Visual Studio **Hilfe** > **Feedback senden** und dann **Einstellungen** aus.

   Das Dialogfeld **Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio** wird geöffnet.

1. Wählen Sie zum Deaktivieren das Optionsfeld **Nein, ich möchte nicht teilnehmen** aus, und klicken Sie auf **OK**. Wählen Sie zum Aktivieren das Optionsfeld **Ja, ich möchte teilnehmen (empfohlen)** aus, und klicken Sie auf **OK**.

   ![Dialogfeld „Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio“](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Registrierungseinstellungen

Wenn Sie die [Buildtools für Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017) installieren, müssen Sie die Registrierung aktualisieren, um VSCEIP zu konfigurieren. Enterprise-Kunden können durch Festlegen einer registrierungsbasierten Richtlinie eine Gruppenrichtlinie erstellen, um VSCEIP zu aktivieren oder zu deaktivieren.

Der entsprechende Registrierungsschlüssel und die entsprechenden Einstellungen lauten wie folgt:

::: moniker range="vs-2017"

- Schlüssel auf einem 64-Bit-Betriebssystem = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- Schlüssel auf einem 32-Bit-Betriebssystem = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Schlüssel bei aktivierter Gruppenrichtlinie = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- Schlüssel auf einem 64-Bit-Betriebssystem = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- Schlüssel auf einem 32-Bit-Betriebssystem = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Schlüssel bei aktivierter Gruppenrichtlinie = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Name = **OptIn**

Wert = (DWORD)

- **0** = deaktiviert (VSCEIP deaktivieren)
- **1** = aktiviert (VSCEIP aktivieren)

> [!CAUTION]
> Durch eine fehlerhafte Bearbeitung der Registrierung können schwerwiegende Schäden am System verursacht werden. Bevor Sie Änderungen an der Registrierung vornehmen, sollten Sie alle wichtigen Computerdaten sichern. Sie können auch die Startoption **Letzte als funktionierend bekannte Konfiguration** verwenden, wenn nach dem Übernehmen manueller Änderungen Probleme auftreten.

Weitere Informationen zu den durch VSCEIP gesammelten, verarbeiteten oder übertragenen Informationen finden Sie in der [Datenschutzerklärung von Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Weitere Informationen

* [Von Visual Studio gesammelte Diagnoseinformationen](diagnostic-data-collection.md)
* [Visual Studio-Feedbackoptionen](../ide/feedback-options.md)
* [Melden eines Problems mit Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8)
* [Datenschutzerklärung von Microsoft](https://privacy.microsoft.com/privacystatement)
