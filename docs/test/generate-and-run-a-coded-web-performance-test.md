---
title: Codierte Webleistungstests
description: Erfahren Sie, wie ein Webleistungstest in ein codebasiertes Skript konvertiert werden kann, das Sie bearbeiten und anpassen können.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20c55c2a2d9b77662170cde24c2b98368240a4af
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442637"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generieren und Ausführen eines codierten Webleistungstests

Webleistungstests werden aufgezeichnet, indem die Web-App durchsucht wird. Die Tests sind in Auslastungstests enthalten, um die Leistung der Webanwendung unter der Last mehrerer Benutzer zu messen. Ein Webleistungstest kann in ein codebasiertes Skript konvertiert werden, das Sie wie jeden anderen Quellcode bearbeiten und anpassen können. Beispielsweise können Sie Schleifen- und Branchkonstrukte hinzufügen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generieren eines codierten Webleistungstests

1. Wenn Sie keinen Webleistungstest erstellt haben, finden Sie weitere Informationen unter [Record a web performance test (Aufzeichnen eines Webleistungstests)](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Generieren Sie den codierten Test.

     ![Generieren eines codierten Webleistungstests](../test/media/web_test_coded_generate.png)

3. Geben Sie dem Test einen Namen.

     ![Einen Namen für den codierten Webleistungstest eingeben](../test/media/web_test_coded_generate_nametest.png)

     Der neue codierte Test wird im Code-Editor geöffnet.

     In Abhängigkeit davon, welche Webleistungs- und Auslastungstest-Projektvorlage Sie zu Ihrer Projektmappe hinzugefügt haben, wird der Code entweder in Visual Basic oder Visual C# generiert.

     ![Der neue codierte Test wird im Code-Editor geöffnet](../test/media/web_test_coded_generate_opencodeeditor.png)

     Im Code können Sie sehen, dass die GetRequestEnumerator()-Methode in C# bzw. die Run()-Methode in Visual Basic jede Validierungsregel und jede Webanforderung enthält, die im umcodierten Test enthalten war.

4. Um zu demonstrieren, wie einfacher Code hinzugefügt wird, führen Sie einen Bildlauf zum Ende der Methode durch, und fügen Sie nach dem Code für die letzte Webanforderung folgenden Code hinzu:

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. Erstellen Sie die Projektmappe, um sicherzustellen, dass der benutzerdefinierte Code kompiliert werden kann.

6. Führen Sie den Test aus.

     ![Ausführung des codierten Webleistungstests](../test/media/web_test_coded_generate_run.png)

     Und da der Tag, am dem dies ausgeführt wurde, ein Mittwoch war...

     ![Ergebnisse des codierten Webleistungstests](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Fragen und Antworten

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Frage: Kann ich mehrere Tests gleichzeitig durchführen?
**Antwort:** Ja. Verwenden Sie das Kontextmenü im **Projektmappen-Explorer**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Frage: Sollte ich eine Datenquelle vor oder nach der Generierung eines codierten Tests hinzufügen?
**Antwort:** Es ist einfacher, eine [Datenquelle](../test/add-a-data-source-to-a-web-performance-test.md) hinzuzufügen, bevor Sie den codierten Test generieren, da der Code automatisch für Sie generiert wird.

Wenn Sie einen codierten Test mit einer Datenquelle ausführen, wird möglicherweise folgende Fehlermeldung angezeigt:

**Could not run test \<Test Name> on agent \<Computer Name> (Der Test <Name des Tests> konnte auf dem Agent <Name des Computers> nicht ausgeführt werden): Object reference not set to an instance of an object. (Der Test „<Testname>“ konnte auf dem Agent „<Computername>“ nicht ausgeführt werden: Der Objektverweis ist nicht auf eine Objektinstanz festgelegt.)**

Dieser Fehler kann auftreten, wenn Sie für die Testklasse ein DataSourceAttribute ohne ein zugehöriges DataBindingAttribute definiert haben. Um diesen Fehler zu beheben, fügen Sie ein entsprechendes DataBindingAttribute hinzu, löschen es oder kommentieren es aus dem Code aus.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Frage: Sollte ich Validierungs- und Extraktionsregeln vor oder nach der Generierung eines codierten Tests hinzufügen?
**Antwort:** Es ist einfacher, Validierungs- und Extraktionsregeln hinzuzufügen, bevor Sie den codierten Test generieren. Zu Validierungszwecken sollten Sie jedoch [Tests für codierte UI](../test/use-ui-automation-to-test-your-code.md) verwenden.
