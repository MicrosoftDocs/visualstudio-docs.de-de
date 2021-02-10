---
title: Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen
description: Lernen Sie, mit Testeinstellungen in Visual Studio zusätzliche Daten zu sammeln, während Sie Ihre Tests ausführen. Erfahren Sie mehr über verschiedene Adapter für diagnostische Daten.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 564d1598dd4458a902df5cf0ddcae37afbf9c423
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868152"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen

Sie können *Testeinstellungen* in Visual Studio verwenden, um zusätzliche Daten zu sammeln, während Sie Ihre Tests ausführen. Sie können z. B. ein Video bei der Testdurchführung aufzeichnen. Es gibt für folgende Zwecke Adapter für diagnostische Daten:

- Erfassen jedes Aktionsschritts auf der Benutzeroberfläche im Textformat

- Aufzeichnen jeder Aktion auf der Benutzeroberfläche zur Wiedergabe

- Erfassen von Systeminformationen

- Erfassen von Ereignisprotokolldaten

- Sammeln von IntelliTrace-Daten, um bei der Isolierung nicht reproduzierbarer Fehler zu helfen

Adapter für diagnostische Daten können auch verwendet werden, um das Verhalten eines Testcomputers zu ändern. So können Sie beispielsweise mit einer Testeinstellung in Visual Studio verschiedene Engpässe in der Netzwerktopologie emulieren, um die Leistung der Anwendung Ihres Teams auszuwerten.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Verwenden von Testeinstellungen mit Visual Studio

Um die Komponententests, Tests der codierten UI, Webleistungs- oder Auslastungstests mit Visual Studio auszuführen, können Sie die Testeinstellungen für Ihre Tests hinzufügen, konfigurieren und auswählen. Wenn Sie die Tests ausführen, Daten sammeln oder einen Testcomputer remote beeinflussen möchten, müssen Sie in den Testeinstellungen den zu verwendenden Testcontroller angeben. Der Testcontroller verfügt über Agents, die für die einzelnen Rollen in den Testeinstellungen verwendet werden können.

## <a name="diagnostic-data-adapter-details"></a>Details zum Adapter für diagnostische Daten

Die folgende Tabelle bietet eine Übersicht über die möglichen Konfigurationen der Adapter für diagnostische Daten für die Verwendung mit lokalen oder Remotecomputerrollen.

|In Testeinstellung verwendeter Adapter für diagnostische Daten|Manuelle Tests auf lokalem Computer|Automatisierte Tests|Manuelle Tests: Sammeln von Daten mit mehreren Rollen und einer Umgebung|Hinweise|
|-|-|-|-|-|
|**ASP.NET-Clientproxy für IntelliTrace und Testauswirkung:** Mit diesem Proxy können Sie Informationen zu HTTP-Aufrufen von einem Client an einen Webserver für die IntelliTrace- und Testauswirkungsadapter für diagnostische Daten erfassen.|Ja|Ja|Ja|Verwenden Sie diesen Proxy nur, wenn als Clientrolle der Diagnosedatenadapter IntelliTrace oder der Diagnosedatenadapter Testauswirkung ausgewählt ist.|
|**ASP.NET-Profiler:** Sie können eine Testeinstellung erstellen, die die ASP.NET-Profilerstellung umfasst, und so Leistungsdaten zu ASP.NET-Webanwendungen sammeln.|Nein|Ja (siehe Hinweise)|Nein|Dieser Adapter für diagnostische Daten wird nur bei der Ausführung von Auslastungstests mit Visual Studio unterstützt.|
|**Code Coverage**: Sie können eine Testeinstellung erstellen, die Informationen zur Code Coverage umfasst. Damit können Sie prüfen, welcher Anteil des Codes durch Tests abgedeckt wird.|Nein|Ja (siehe Hinweise)|Nein|Sie können die Code Coverage nur verwenden, wenn Sie einen automatisierten Test über Visual Studio oder *mstest.exe* ausführen, und nur auf dem Computer, auf dem der Test ausgeführt wird. Remoteauflistung wird nicht unterstützt.<br />Code Coverage-Daten können nicht gesammelt werden, wenn Sie auch die Testeinstellung zum Erfassen von IntelliTrace-Informationen konfiguriert haben. **Hinweis**:  Dieser Adapter für diagnostische Daten gilt nur für Visual Studio-Testeinstellungen. Er wird nicht für Testeinstellungen in Microsoft Test Manager verwendet (ab Visual Studio 2017). Außerdem ist dieser Adapter für Kompatibilitätszwecke mit Visual Studio 2010-Testprojekten vorgesehen. **Hinweis**:  Um Kompatibilität zu erreichen, gilt die Code Coverage dann, wenn automatisierte Tests von Microsoft Test Manager oder auf einem Remote-Test-Agent von Visual Studio mithilfe des älteren MSTest-Runners ausgeführt werden.|
|**Ereignisprotokoll:** Sie können eine Testeinstellung konfigurieren, um das Ereignisprotokoll zu erfassen und in die Testergebnisse aufzunehmen.|Ja|Ja|Ja||
|**IntelliTrace:** Sie können den Diagnosedatenadapter für *IntelliTrace* konfigurieren, um bestimmte Diagnoseablaufverfolgungs-Informationen zu erfassen, die das Isolieren von schwierig zu reproduzierenden Fehlern erleichtern. Hierdurch wird eine IntelliTrace-Datei erstellt, die diese Informationen enthält. Eine IntelliTrace-Datei hat die Erweiterung *.iTrace*. Bei Fehlschlagen eines Tests kann ein Fehler erstellt werden. Die IntelliTrace-Datei, die zusammen mit den Testergebnissen gespeichert wird, wird automatisch mit diesem Fehler verknüpft. Die in der IntelliTrace-Datei gesammelten Daten steigern die Debuggingproduktivität, da sie die Zeit für das Reproduzieren und Diagnostizieren eines Fehlers im Code verkürzen. Auf Basis dieser IntelliTrace-Datei kann die lokale Sitzung auf einem anderen Computer simuliert werden. So wird die Wahrscheinlichkeit verringert, dass ein Fehler nicht reproduziert werden kann.|Ja|Ja|Ja|Wenn Sie das Sammeln von IntelliTrace-Daten aktivieren, können keine Code Coverage-Daten gesammelt werden.<br />– Wenn Sie IntelliTrace für eine Webclientrolle verwenden, müssen Sie auch den Adapter für diagnostische Daten für den ASP.NET-Clientproxy für IntelliTrace und für die Testauswirkung auswählen.<br />– Nur die folgenden Versionen von IIS werden unterstützt: IIS 7.0, IIS 7.5 und IIS 8.0.|
|**Netzwerkemulation:** Mit einer Testeinstellung können Sie angeben, dass Sie eine künstliche Netzwerklast auf den Test anwenden möchten. Die Netzwerkemulation wirkt sich auf die Kommunikation vom und zum Computer aus, indem eine bestimmte Netzwerkverbindungsgeschwindigkeit, z. B. DFÜ, emuliert wird. |Nein|Ja (siehe Hinweise)|Nein|Sie können den Adapter für diagnostische Daten für die Netzwerkemulation für eine Client- oder Serverrolle verwenden. Sie müssen den Adapter nicht in diesen beiden Rollen verwenden, die miteinander kommunizieren. **Hinweis**:  Dieser Adapter für diagnostische Daten gilt nur für Visual Studio-Testeinstellungen. Er wird nicht für Testeinstellungen in Microsoft Test Manager verwendet (ab Visual Studio 2017). **Hinweis**:  Die Netzwerkemulation kann nicht verwendet werden, um die Netzwerkverbindungsgeschwindigkeit zu erhöhen. **Warnung:**  Wenn Sie den Adapter für diagnostische Daten für die Netzwerkemulation in die Testeinstellungen einschließen und beabsichtigen, den Adapter auf dem lokalen Computer zu verwenden, müssen Sie auch den Netzwerkemulationstreiber an einen Netzwerkadapter des Computers binden. Der Netzwerkemulationstreiber ist erforderlich, damit der Adapter für diagnostische Daten für die Netzwerkemulation funktioniert. Sie haben zwei Möglichkeiten, den Netzwerkemulationstreiber zu installieren und an den Adapter zu binden: <ul><li>**Netzwerkemulationstreiber, die mit dem Test-Agent von Microsoft Visual Studio installiert wurden:** Der Test-Agent von Visual Studio kann auf Remotecomputern und lokalen Computern verwendet werden. Wenn Sie Visual Studio Test Agent installieren, schließt der Installationsvorgang einen Konfigurationsschritt ein, bei dem der Netzwerkemulationstreiber an die Netzwerkkarte gebunden wird. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).</li><li>**Netzwerkemulationstreiber, die mit Microsoft Visual Studio Test Professional installiert wurden:** Wenn Sie die Netzwerkemulation zum ersten Mal verwenden, werden Sie aufgefordert, den Netzwerkemulationstreiber mit einer Netzwerkkarte zu verbinden.</li></ul> Sie können den Netzwerkemulationstreiber auch über die Befehlszeile auf dem lokalen Computer installieren, ohne den Visual Studio-Test-Agent zu installieren. Verwenden Sie hierzu folgenden Befehl: **VSTestConfig NETWORKEMULATION /install** **Warnung:**  Der Netzwerkemulationsadapter wird von Auslastungstests ignoriert. Stattdessen verwenden Auslastungstests die Einstellungen, die in der Netzwerkmischung des Auslastungstestszenarios angegeben sind.|
|**Systeminformationen:** Sie können eine Testeinstellung einrichten, um die Systeminformationen zum Computer einzuschließen, auf dem der Test ausgeführt wird.|Ja|Ja|Ja||
|**Testwirkungen:** Sie können Informationen zu den Methoden des Anwendungscodes erfassen, die beim Ausführen eines Testfalls verwendet wurden. Diese können zusammen mit von Entwicklern am Anwendungscode vorgenommenen Änderungen verwendet werden, um zu ermitteln, auf welche Tests sich diese Entwicklungsänderungen ausgewirkt haben.|Ja|Ja|Ja|– Wenn Sie Testauswirkungsdaten für eine Webclientrolle erfassen, müssen Sie auch den Diagnosedatenadapter ASP.NET-Clientproxy für IntelliTrace und Testauswirkung auswählen.<br />– Nur die folgenden Versionen von IIS werden unterstützt: IIS 7.0, IIS 7.5 und IIS 8.0.|
|**Videorekorder:** Sie können beim Ausführen eines Tests eine Videoaufzeichnung der Desktopsitzung erstellen. Das Video kann anderen Teammitgliedern helfen, Anwendungsprobleme zu isolieren, die schwer reproduzierbar sind.|Ja|Ja (siehe Hinweise)|Ja|Wenn Sie die Ausführung der Test-Agent-Software als Prozess statt als Dienst aktivieren, können Sie beim Ausführen von automatisierten Tests eine Videoaufzeichnung erstellen.|
