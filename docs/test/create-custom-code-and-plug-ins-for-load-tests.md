---
title: Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c060dc9bd50c6dc49777e9114eadae4d6267d92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288675"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests

In einem benutzerdefinierten Plug-In wird Code verwendet, den Sie schreiben und an einen Auslastungs- oder Webleistungstest anfügen. Sie können die Auslastungstest-API und die Webleistungstest-API verwenden, um benutzerdefinierte Plug-Ins für Tests zu erstellen, die auf die integrierte Funktion erweitert werden sollen. Sie können dem Auslastungstest mehrere Plug-Ins hinzufügen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-|-----------------------|
|**Erstellen eines benutzerdefinierten Plug-Ins für den Auslastungstest:** Sie können mit der Auslastungstest-API ein benutzerdefiniertes Plug-In erstellen, um dem Auslastungstest weitere Testfunktionen hinzuzufügen.|-   [Vorgehensweise: Verwenden der Auslastungstest-API](../test/how-to-use-the-load-test-api.md)<br />-   [Vorgehensweise: Erstellen eines Auslastungstest-Plug-Ins](../test/how-to-create-a-load-test-plug-in.md)|
|**Erstellen eines benutzerdefinierten Plug-Ins für den Webleistungstest:** Sie können ein benutzerdefiniertes Plug-In mithilfe der Webleistungstest-API erstellen, um dem Webleistungstest weitere Testfunktionen hinzuzufügen (auch auf der Anforderungsebene). Sie können auch einen Webdiensttest erstellen.<br /><br /> Darüber hinaus können Sie ein Webaufzeichnungs-Plug-In erstellen, mit dem ein Webleistungstest nach der Aufzeichnung, aber vor dem Anzeigen im Webleistungstest-Ergebnisviewer geändert werden kann.|-   [Vorgehensweise: Verwenden der Webleistungstest-API](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Vorgehensweise: Erstellen eines Webleistungstest-Plug-Ins](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Vorgehensweise: Erstellen eines Anforderungsebenen-Plug-Ins](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Vorgehensweise: Erstellen eines Webdiensttests](../test/how-to-create-a-web-service-test.md)<br />-   [How to: Create a Recorder Plug-In (Vorgehensweise: Erstellen eines Aufzeichnungs-Plug-Ins)](../test/how-to-create-a-recorder-plug-in.md)|
|**Hinzufügen von Benutzeroberflächenfeatures zur Webleistungstest-Ergebnisansicht:** Sie können der Webleistungstest-Ergebnisansicht mithilfe eines Visual Studio-Add-Ins weitere Benutzeroberflächenfeatures hinzufügen.|-   [Vorgehensweise: Erstellen eines Visual Studio-Add-Ins für die Webleistungstest-Ergebnisansicht](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Erstellen eines benutzerdefinierten HTTP-Text-Editors:** Sie können einen benutzerdefinierten Editor zum Bearbeiten von binären oder zeichenfolgenbasierten HTTP-XML-Antworten eines Webdiensts erstellen.|-   [How to: Create a Custom HTTP Body Editor for the Web Performance Test Editor (Vorgehensweise: Erstellen eines benutzerdefinierten HTTP-Körper-Editors für den Webleistungstest-Editor)](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Verweis

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Weitere Informationen

- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generieren und Ausführen eines codierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md)
