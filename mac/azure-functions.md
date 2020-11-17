---
title: Einführung in Azure Functions
description: Erste Schritte mit Azure Functions in Visual Studio für Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: 69ecab4f4d3dd7d99821b384dbda0c8986297282
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492840"
---
# <a name="introduction-to-azure-functions"></a>Einführung in Azure Functions

Mithilfe von Azure Functions können Sie ereignisgesteuerte Codeausschnitte – Funktionen – in einer Cloud erstellen und ausführen, ohne Infrastruktur bereitstellen und verwalten zu müssen. Weitere Informationen zu Azure Functions finden Sie in der [Dokumentation zu Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Anforderungen

Die Azure Function-Tools sind im Lieferumfang von **Visual Studio für Mac 7.5** und höheren Versionen enthalten.

Sie benötigen zum Erstellen und Bereitstellen von Funktionen außerdem ein Azure-Abonnement. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich noch heute kostenlos registrieren und 12 Monate lang kostenlos beliebte Dienste nutzen. Außerdem erhalten Sie eine Gutschrift über 200 USD und Zugang zu mehr als 25 Diensten, die immer kostenlos sind: [https://azure.com/free](https://azure.com/free/dotnet).

## <a name="creating-your-first-azure-functions-project"></a>Erstellen Ihres ersten Azure Functions-Projekts

1. Klicken Sie in Visual Studio für Mac auf **Datei > Neue Projektmappe**.
2. Klicken Sie im Dialogfeld „Neues Projekt“ unter **Cloud > Allgemein** auf eine Azure Functions-Vorlage, und klicken Sie auf **Weiter**:

    ![Dialogfeld „Neues Projekt“, in dem die Option „Azure Functions“ angezeigt wird](media/azure-functions-image1.png)

3. Wählen Sie die anfängliche Azure Functions-Vorlage, die Sie verwenden möchten, geben den Funktionsnamen ein, und klicken Sie auf **Weiter**.

    ![Dialogfeld „Neues Projekt“ mit Azure Functions-Vorlagen](media/azure-functions-image2.png)

    > [!TIP]
    > Obwohl die gebündelte Azure Functions-Runtime und die Vorlagen (CLI) so aktuell wie möglich gehalten werden, veralten sie unvermeidlich. Bei der Erstellung eines neuen Projekts in Azure Functions, überprüft Visual Studio für Mac, ob CLI-Updates vorhanden sind, und informiert Sie gegebenenfalls (siehe Bild unten). Klicken Sie einfach auf die Schaltfläche, um die aktualisierten Vorlagen herunterzuladen.
    > ![Dialogfeld „Neues Projekt“ mit dem Hinweis, dass Azure Functions-Updates verfügbar sind](media/azure-functions-update.png)

    Abhängig vom Typ der von Ihnen gewählten Funktion werden Sie auf der nächsten Seite aufgefordert, Details wie beispielsweise Zugriffsrechte einzugeben, wie im folgenden Bild dargestellt:

    ![Dialogfeld „Neues Projekt“ mit zusätzlicher Option](media/azure-functions-image3.png)

    Weitere Informationen zu den verschiedenen Typen von Azure Functions-Vorlagen und den Bindungseigenschaften, die zur Konfiguration der einzelnen Vorlagen erforderlich sind, finden Sie im Abschnitt [Verfügbare Funktionsvorlagen](#available-function-templates). In diesem Beispiel wird ein HTTP-Trigger mit Zugriffsrechten verwendet, die auf anonym gesetzt sind.

4. Nachdem Sie die Parameter festgelegt haben, wählen Sie den Speicherort für das Projekt, und klicken Sie auf **Erstellen**.

Visual Studio für Mac erstellt ein .NET Standard-Projekt mit einer Standardfunktion. Außerdem sind NuGet-Verweise auf eine Vielzahl von **Azure WebJobs**-Paketen sowie das Paket **Newtonsoft.Json** im Lieferumfang enthalten.

![Visual Studio für Mac-Editor, in dem eine ganz neue Azure-Funktion aus einer Vorlage angezeigt wird](media/azure-functions-newproj.png)

Das neue Projekt enthält die folgenden Dateien:

* **Ihr-Funktionsname.cs**: Diese Klasse enthält Codebeispiele für die Funktion, die Sie ausgewählt haben. Außerdem enthält sie ein **FunctionName**-Attribute mit dem Funktionsnamen und dem Triggerattribut, das den Auslöser der Funktion (z.B. eine HTTP-Anforderung) angibt. Weitere Informationen zur Funktionsmethode finden Sie in dem Artikel [C#-Entwicklerreferenz zu Azure Functions](/azure/azure-functions/functions-dotnet-class-library).
* **host.json**: Diese Datei beschreibt die globalen Konfigurationsoptionen für den Functions-Host. Eine Beispieldatei und Informationen zu den für diese Datei verfügbaren Einstellungen finden Sie unter [host.json-Referenz für Azure Functions](/azure/azure-functions/functions-host-json).
* **local.settings.json**: Diese Datei enthält alle Einstellungen zur lokalen Ausführung von Funktionen. Diese Einstellungen werden von den Azure Functions Core-Tools verwendet. Weitere Informationen finden Sie in der [Datei für lokale Einstellungen](/azure/azure-functions/functions-run-local#local-settings-file) im Artikel „Azure Functions Core-Tools“.

Wenn Sie jetzt ein neues Azure Functions-Projekt in Visual Studio für Mac erstellt haben, können Sie nun über Ihren lokalen Computer die von HTTP ausgelöste Standardfunktion testen.

## <a name="testing-the-function-locally"></a>Lokales Testen der Funktion

Mit der Azure Functions-Unterstützung in Visual Studio für Mac können Sie Ihre Funktion auf dem lokalen Entwicklungscomputer testen und debuggen.

1. Wenn Sie Ihre Funktion lokal testen möchten, drücken Sie auf die Schaltfläche **Ausführen** in Visual Studio für Mac:

    ![Schaltfläche zum Starten des Debugvorgangs in Visual Studio für Mac](media/azure-functions-run.png)

1. Wenn Sie das Projekt ausführen, wird der lokale Debugvorgang für die Azure-Funktion ausgeführt und ein neues Terminalfenster geöffnet (s. folgende Abbildung):

    ![Terminalfenster, das die Ausgabe der Funktion anzeigt](media/azure-functions-terminal.png)

    Kopieren Sie die URL aus der Ausgabe.

3. Fügen Sie die URL zu der HTTP-Anforderung in die Adressleiste Ihres Browsers ein. Fügen Sie die Abfragezeichenfolge `?name=<yourname>` an das Ende der URL ein, und führen Sie die Anforderung aus. Im folgenden Bild wird die Antwort auf die lokale GET-Anforderung im Browser angezeigt, die von der Funktion zurückgegeben wird:

    ![HTTP-Anforderung im Browser](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Hinzufügen einer weiteren Funktion zu Ihrem Projekt

Mithilfe von Funktionsvorlagen können Sie schnell mithilfe der am häufigsten verwendeten Trigger und Vorlagen neue Funktionen erstellen. Gehen Sie wie folgt vor, wenn Sie einen anderen Funktionstyp erstellen möchten:

1. Wenn Sie eine neue Funktion hinzufügen möchten, klicken Sie erst mit der rechten Maustaste auf den Projektnamen und dann mit der linken auf **Hinzufügen > Funktion hinzufügen...** :

    ![Kontextaktion zum Hinzufügen einer neuen Funktion](media/azure-functions-addnew.png)

2. Wählen Sie über das Dialogfeld **Neue Azure-Funktion** die Funktion aus, die Sie benötigen:

    ![Dialogfeld „Neue Azure-Funktion“](media/azure-functions-image4.png)

    Im Abschnitt [Verfügbare Funktionsvorlagen](#available-function-templates) finden Sie eine Liste der Azure Function-Vorlagen.

Mit der obigen Vorgehensweise können Sie weitere Funktionen zu Ihrem Funktions-App-Projekt hinzufügen. Jede Funktion im Projekt kann über einen anderen Trigger verfügen, aber einer Funktion muss genau ein Trigger zugeordnet sein. Weitere Informationen finden Sie unter [Konzepte für Azure Functions-Trigger und -Bindungen](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Veröffentlichen in Azure

1. Klicken Sie mit der rechten Maustaste auf den Projektnamen, und wählen Sie dann **Veröffentlichen > In Azure veröffentlichen** aus:  ![Kontextmenü, in dem „Veröffentlichen“ > „In Azure veröffentlichen...“ hervorgehoben ist](media/azure-functions-image5.png)
2. Wenn Sie Ihr Azure-Konto bereits mit Visual Studio für Mac verbunden haben, wird eine Liste der verfügbaren App-Dienste angezeigt. Wenn Sie sich nicht angemeldet haben, werden Sie dazu aufgefordert.
3. Im Dialogfeld **In Azure App Service veröffentlichen** können Sie entweder einen vorhandenen App-Dienst auswählen oder einen neuen erstellen, indem Sie auf **Neu** klicken.
4. Geben Sie Ihre Einstellungen im Dialogfeld **Neuen App-Dienst erstellen** ein:  ![Dialogfeld „Neuer App Service“ mit Feldern für den Dienstnamen, das Abonnement, die Ressourcengruppe und die Dienstplaneinstellungen](media/azure-functions-image7.png)

    |Einstellung  |Beschreibung  |
    |---------|---------|
    |**App Service-Name**|Ein global eindeutiger Name, der Ihre neue Funktions-App identifiziert.|
    |**Abonnement**|Das zu verwendende Azure-Abonnement|
    |**[Ressourcengruppe](/azure/azure-resource-manager/resource-group-overview)**|Der Name der Ressourcengruppe, in der Ihre Funktions-App erstellt werden soll. Wählen Sie **+** aus, um eine neue Ressourcengruppe zu erstellen.|
    |**[Serviceplan](/azure/azure-functions/functions-scale)**|Wählen Sie einen vorhandenen Plan aus, oder erstellen Sie einen benutzerdefinierten Plan. Wählen Sie einen Speicherort in einer Region in Ihrer Nähe oder in der Nähe anderer Dienste, auf die Ihre Funktionen zugreifen.|

5. Klicken Sie auf **Weiter**, um ein Speicherkonto zu erstellen. Für die Functions-Laufzeit ist ein Azure-Speicherkonto erforderlich. Klicken Sie auf **Benutzerdefiniert**, um ein allgemeines Speicherkonto zu erstellen oder eine bereits vorhandenes Speicherkonto zu verwenden:

    ![Dialogfeld „Neuer App Service“ mit der Eingabeaufforderung für den Namen eines Speicherkontos](media/azure-functions-image8.png)

6. Klicken Sie auf **Erstellen**, um mit diesen Einstellungen eine Funktions-App und zugehörige Ressourcen in Azure zu erstellen und Ihren Funktionsprojektcode bereitzustellen.

7. Während der Veröffentlichung werden Sie möglicherweise in einem Dialogfeld aufgefordert, damit Sie Ihre „Functions-Version in Azure aktualisieren“. Klicken Sie auf **Ja**:

    ![Eingabeaufforderung „Update Azure application settings to match local Functions version?“ (Möchten Sie die Azure-Anwendungseinstellungen so aktualisieren, dass sie der lokalen Version von Functions entsprechen?) mit den Optionen „Ja“ und „Nein“](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Einstellungen für Funktions-Apps

Alle Einstellungen, die Sie in der Datei local.settings.json hinzugefügt haben, müssen auch der Funktions-App in Azure hinzugefügt werden. Diese Einstellungen werden nicht automatisch hochgeladen, wenn Sie das Projekt veröffentlichen.

Wenn Sie auf Ihre App-Einstellungen zugreifen möchten, wechseln Sie zum Azure-Portal unter [https://ms.portal.azure.com/](https://ms.portal.azure.com/). Wählen Sie unter **Funktions-Apps** die Option **Funktions-Apps** aus, und markieren Sie Ihren Funktionsnamen:

![Azure Functions-Menü](media/azure-functions-image9.png)

Wählen Sie auf der Registerkarte **Übersicht** unter **Konfigurierte Features** die Option **Anwendungseinstellungen** aus:

![Azure Functions-Registerkarte „Übersicht“](media/azure-functions-image10.png)

Von hier aus können Sie Anwendungseinstellungen für die Funktions-App festlegen, d.h. neue Anwendungseinstellungen hinzufügen oder bestehende ändern:

![Screenshot: Bereich für Anwendungseinstellungen im Azure-Portal](media/azure-functions-image11.png)

Eine wichtige Einstellung, die Sie möglicherweise vornehmen müssen, ist `FUNCTIONS_EXTENSION_VERSION`. Beim Veröffentlichen aus Visual Studio für Mac sollte dieser Wert auf **beta** gesetzt sein.

## <a name="available-function-templates"></a>Verfügbare Funktionsvorlagen

- **GitHub Trigger**: Antworten Sie auf Ereignisse, die in Ihren GitHub-Repositorys auftreten. Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch einen GitHub-Webhook ausgelöst wird](/azure/azure-functions/functions-create-github-webhook-triggered-function).
  - GitHub commenter: eine Funktion, die immer dann ausgeführt wird und einen Kommentar hinzufügt, wenn sie einen GitHub-Webhook für ein Problem oder einen Pull Request empfängt.
  - GitHub WebHook: Diese Funktion wird ausgeführt, wenn sie einen GitHub-Webhook empfängt.

- **HTTP**: Lösen Sie die Ausführung Ihres Codes über eine HTTP-Anforderung aus. Es gibt explizite Vorlagen für die folgenden HTTP-Trigger:
  - HTTP-Trigger
  - Http GET CRUD
  - Http POST CRUD
  - HTTP-Trigger mit Parametern

- **Timer**: Führen Sie eine Bereinigung oder andere Stapelaufgaben für einen vordefinierten Zeitplan aus. Diese Vorlage beinhaltet zwei Felder: ein Name und ein Zeitplan, bei dem es sich um einen CRON-Ausdruck handelt, der aus sechs Feldern besteht. Weitere Informationen finden Sie unter [Erstellen einer Funktion in Azure, die von einem Timer ausgelöst wird](/azure/azure-functions/functions-create-scheduled-function).

- **Queue Trigger**: eine Funktion, die auf Meldungen antwortet, wenn diese in die Azure Storage-Warteschlange aufgenommen werden. Neben dem Funktionsnamen beinhaltet diese Vorlage einen **Pfad** (den Namen der Warteschlange, aus der die Meldung gelesen wird) und die Speicherkonto-**Verbindung** (der Name der App-Einstellung mit der Verbindungszeichenfolge des Speicherkontos). Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch Azure Queue Storage ausgelöst wird](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Blob Trigger**: eine Funktion, die Azure Storage-Blobs verarbeitet, wenn diese zu einem Container hinzugefügt werden. Neben dem Funktionsnamen beinhaltet diese Vorlage auch eine Pfad- und eine Verbindungseigenschaft. Die Pfadeigenschaft ist der Pfad innerhalb Ihres Speicherkontos, der vom Trigger überwacht wird. Das Verbindungskonto ist der Name der App-Einstellung, die die Verbindungszeichenfolge für Ihr Speicherkonto enthält. Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch Azure Blob Storage ausgelöst wird](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Generic WebHook**: eine einfache Funktion, die immer dann ausgeführt wird, wenn eine Anforderung von einem Dienst empfangen wird, der Webhooks unterstützt. Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch einen generischen Webhook ausgelöst wird](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Durable functions orchestration**: Mithilfe von Durable Functions können Sie zustandsbehaftete Funktionen in einer Umgebung ohne Server schreiben. Die Erweiterung verwaltet den Status, Prüfpunkte und führt einen Neustart durch. Weitere Informationen finden Sie in den Leitfäden zu Azure Functions unter [Übersicht zu Durable Functions](/azure/azure-functions/durable-functions-overview).

- **Image Resizer**: eine Funktion, die Images mit geänderter Größe erstellt, wenn einem Container ein Blob hinzugefügt wird. Diese Vorlage beinhaltet einen Pfad und eine Verbindungszeichenfolge für den Trigger, eine kleine Imageausgabe und eine mittelgroße Imageausgabe.

- **SAS Token**: eine Funktion, die ein SAS-Token für einen angegebenen Azure Storage-Container und einen Blobnamen generiert. Neben dem Funktionsnamen beinhaltet diese Vorlage auch eine Pfad- und eine Verbindungseigenschaft. Die Pfadeigenschaft ist der Pfad innerhalb Ihres Speicherkontos, der vom Trigger überwacht wird. Das Verbindungskonto ist der Name der App-Einstellung, die die Verbindungszeichenfolge für Ihr Speicherkonto enthält. Die **Zugriffsrechte** müssen ebenfalls festgelegt werden. Die Autorisierungsebene kontrolliert, ob die Funktion einen API-Schlüssel erfordert und welcher Schlüssel verwendet werden soll. „Function“ verwendet einen Funktionsschlüssel, „Admin“ Ihren Kontozugriffsschlüssel. Weitere Informationen finden Sie in dem Beispiel [C# Azure Function for generating SAS tokens (Azure-Funktion in C# zum Generieren von SAS-Token)](https://github.com/Azure-Samples/functions-dotnet-sas-token/).
