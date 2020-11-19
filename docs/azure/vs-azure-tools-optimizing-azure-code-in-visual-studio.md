---
title: Optimieren Ihres Azure-Codes
description: Erfahren Sie, wie Sie Azure-Tools zur Codeoptimierung in Visual Studio nutzen können, um Ihren Code robuster und leistungsstärker zu machen.
author: ghogen
manager: jillfra
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 5ae141c4ecdf5cfe1819ba2f47aac45f1763fa34
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902297"
---
# <a name="optimizing-your-azure-code"></a>Optimieren des Azure-Codes
Wenn Sie Apps programmieren, für die Microsoft Azure verwendet wird, sollten Sie einige Hinweise zur Codeerstellung beachten. So vermeiden Sie Probleme mit der Skalierbarkeit, dem Verhalten und der Leistung von Apps in einer Cloudumgebung. Microsoft stellt ein Azure-Tool für die Codeanalyse bereit, mit dem mehrere dieser häufig auftretenden Probleme erkannt und behoben werden können. Sie können das Tool in Visual Studio über NuGet herunterladen.

## <a name="azure-code-analysis-rules"></a>Regeln für die Azure-Codeanalyse
Im Azure-Tool für die Codeanalyse werden die folgenden Regeln verwendet, um den Azure-Code automatisch zu kennzeichnen, wenn bekannte Probleme erkannt werden, die sich auf die Leistung auswirken. Erkannte Probleme werden als Warnungen oder Compilerfehler angezeigt. Codefehlerbehebungen oder Vorschläge zur Lösung der Warnung oder des Fehlers werden häufig durch das Glühbirnen-Symbol angegeben.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Vermeiden der Verwendung des standardmäßigen Sitzungszustandsmodus (In Bearbeitung)
### <a name="id"></a>id
AP0000

### <a name="description"></a>BESCHREIBUNG
Wenn Sie den standardmäßigen Sitzungszustandsmodus (In Bearbeitung) für Cloudanwendungen verwenden, können Sie den Sitzungszustand verlieren.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Standardmäßig lautet der in der Datei „web.config“ angegebene Sitzungszustandsmodus „In Bearbeitung“. Außerdem wird der Sitzungszustandsmodus automatisch auf „In Bearbeitung“ festgelegt, wenn in der Konfigurationsdatei kein Eintrag angegeben ist. Im Modus „In Bearbeitung“ werden Sitzungszustände im Arbeitsspeicher auf dem Webserver gespeichert. Wenn eine Instanz neu gestartet wird oder eine neue Instanz für den Lastenausgleich oder die Failoverunterstützung verwendet wird, wird der im Arbeitsspeicher auf dem Webserver befindliche Sitzungszustand nicht gespeichert. Diese Situation verhindert, dass die Anwendung in der Cloud skalierbar ist.

Der ASP.NET-Sitzungszustand unterstützt mehrere unterschiedliche Speicheroptionen für Sitzungszustandsdaten: „InProc“, „StateServer“, „SQLServer“, „Custom“ und „Off“. Es wird empfohlen, den benutzerdefinierten Modus (Custom) zum Hosten von Daten in einem externen Sitzungszustandsspeicher zu verwenden, z.B. [Azure-Sitzungszustandsanbieter für Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/).

### <a name="solution"></a>Lösung
Eine empfohlene Lösung ist das Speichern des Sitzungszustands unter einem Managed Cache Service. Informieren Sie sich, wie Sie [Azure-Sitzungszustandsanbieter für Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) zum Speichern des Sitzungszustands verwenden. Sie können den Sitzungszustand auch an anderen Orten speichern, um sicherzustellen, dass die Anwendung in der Cloud skalierbar ist. Weitere Informationen zu alternativen Lösungen finden Sie unter [Sitzungszustandsmodi](/previous-versions/ms178586(v=vs.140)).

## <a name="run-method-should-not-be-async"></a>Run-Methode sollte nicht asynchron sein
### <a name="id"></a>id
AP1000

### <a name="description"></a>BESCHREIBUNG
Erstellen Sie asynchrone Methoden (z.B. [await](/dotnet/csharp/language-reference/operators/await)) außerhalb der [Run()](/previous-versions/azure/reference/ee772746(v=azure.100))-Methode, und rufen Sie dann die asynchronen Methoden aus [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) auf. Wenn Sie die [[Run()](/previous-versions/azure/reference/ee772746(v=azure.100))](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)-Methode als asynchron deklarieren, wird die Workerrolle in eine Neustartschleife versetzt.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Wenn Sie asynchrone Methoden in der [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) -Methode aufrufen, recycelt die Clouddienst-Runtime die Workerrolle. Wenn eine Workerrolle gestartet wird, wird die gesamte Programmausführung innerhalb der [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) -Methode durchgeführt. Wenn Sie die Run-Methode beenden, wird die workerrolle neu gestartet. Wenn die Workerrollen-Runtime auf die asynchrone Methode trifft, werden alle Vorgänge nach der asynchronen Methode abgearbeitet, und dann wird zum Anfang zurückgekehrt. Dies bewirkt, dass die workerrolle von der Run-Methode beendet und neu gestartet wird. Beim nächsten Durchlauf der Ausführung trifft die Workerrolle erneut auf die asynchrone Methode und wird neu gestartet, sodass auch die Workerrolle erneut recycelt wird.

### <a name="solution"></a>Lösung
Ordnen Sie alle asynchronen Vorgänge außerhalb der [Run()](/previous-versions/azure/reference/ee772746(v=azure.100))-Methode an. Anschließend können Sie die umgestaltete asynchrone Methode in der Run-Methode aufrufen, z. b. runasync (). Wait. Das Azure-Tool für die Codeanalyse ist hilfreich, um dieses Problem zu beheben.

Der folgende Codeausschnitt veranschaulicht die Codefehlerbehebung für dieses Problem:

```csharp
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("https://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Verwenden der Authentifizierung „Service Bus Shared Access Signature“
### <a name="id"></a>id
AP2000

### <a name="description"></a>BESCHREIBUNG
Verwenden Sie Shared Access Signature (SAS) für die Authentifizierung. Access Control Service (ACS) gilt für die Service Bus-Authentifizierung als veraltet.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Aus Sicherheitsgründen wird die ACS-Authentifizierung für Azure Active Directory durch die SAS-Authentifizierung ersetzt. Informationen zum Übergangsplan finden Sie unter [Azure Active Directory ist die Zukunft von ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) (in englischer Sprache).

### <a name="solution"></a>Lösung
Verwenden Sie die SAS-Authentifizierung in Ihren Apps. Das folgende Beispiel zeigt, wie Sie ein vorhandenes SAS-Token zum Zugreifen auf einen Service Bus-Namespace oder eine Entität verwenden.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Weitere Informationen finden Sie in den folgenden Themen.

* Eine Übersicht hierzu finden Sie unter [SAS-Authentifizierung (Shared Access Signature) mit Service Bus](/azure/service-bus-messaging/service-bus-sas)
* [Verwenden von SAS-Authentifizierung (Shared Access Signature) mit Service Bus](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Erwägen der Verwendung der OnMessage-Methode zum Vermeiden einer „Empfangsschleife“
### <a name="id"></a>id
AP2002

### <a name="description"></a>BESCHREIBUNG
Um das Auftreten einer „Empfangsschleife“ zu vermeiden, ist das Aufrufen der **OnMessage**-Methode eine bessere Lösung für das Empfangen von Nachrichten als das Aufrufen der **Receive**-Methode. Wenn Sie die **Receive** -Methode verwenden müssen und nicht die Standardeinstellung für die Serverwartezeit festlegen, sollten Sie sicherstellen, dass die Serverwartezeit mehr als eine Minute beträgt.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Beim Aufrufen von **OnMessage** startet der Client einen internen Nachrichtensystemvorgang, bei dem die Warteschlange bzw. das Abonnement ständig abgefragt werden. Dieses Nachrichtensystem enthält eine Endlosschleife, die einen Aufruf zum Empfangen von Nachrichten ausgibt. Wenn die Zeitüberschreitung für den Aufruf erreicht ist, wird ein neuer Aufruf ausgegeben. Das Timeoutintervall wird vom Wert der [OperationTimeout](/dotnet/api/microsoft.servicebus.messaging.messagingfactorysettings)-Eigenschaft des verwendeten [MessagingFactory](/dotnet/api/microsoft.servicebus.messaging.messagingfactory)-Elements bestimmt.

Der Vorteil der Verwendung von **OnMessage** gegenüber **Receive** besteht darin, dass Benutzer die folgende Schritte nicht ausführen müssen: manuelles Abfragen von Nachrichten, Behandeln von Ausnahmen, paralleles Verarbeiten mehrerer Nachrichten und Abschließen der Nachrichten.

Wenn Sie **Receive** ohne Verwendung des Standardwerts aufrufen, sollten Sie sicherstellen, dass der Wert *ServerWaitTime* mehr als eine Minute beträgt. Mit dem Festlegen von *ServerWaitTime* auf mehr als eine Minute wird verhindert, dass für den Server eine Zeitüberschreitung auftritt, bevor die Nachricht vollständig empfangen wurde.

### <a name="solution"></a>Lösung
Die empfohlene Verwendung wird in den folgenden Codebeispielen veranschaulicht. Weitere Informationen finden Sie unter [QueueClient.OnMessage-Methode (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) und [QueueClient.Receive-Methode (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient).

Sehen Sie sich die Informationen zum Entwurfsmuster unter [Einführung in asynchrone Nachrichten](/previous-versions/msp-n-p/dn589781(v=pandp.10))an, um die Leistung der Azure-Messaginginfrastruktur zu verbessern.

Im Folgenden finden Sie ein Beispiel für die Verwendung von **OnMessage** zum Empfangen von Nachrichten.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Im Folgenden finden Sie ein Beispiel für die Verwendung von **Receive** mit der standardmäßigen Serverwartezeit.

```csharp
string connectionString =
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)
{
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Im Folgenden finden Sie ein Beispiel für die Verwendung von **Receive** mit einer nicht standardmäßigen Serverwartezeit.

```csharp
while (true)
{
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```

## <a name="consider-using-asynchronous-service-bus-methods"></a>Verwenden asynchroner Service Bus-Methoden
### <a name="id"></a>id
AP2003

### <a name="description"></a>BESCHREIBUNG
Verwenden Sie asynchrone Service Bus-Methoden zur Verbesserung der Leistung beim Brokermessaging.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Die Verwendung asynchroner Methoden ermöglicht die Parallelität von Anwendungsprogrammen, da die Ausführung der einzelnen Aufrufe keine Blockierung des Hauptthreads bewirkt. Beim Verwenden von Service Bus-Messagingmethoden nimmt das Durchführen eines Vorgangs (Senden, Empfangen, Löschen usw.) Zeit in Anspruch. Dieser Zeitraum umfasst die Verarbeitung des Vorgangs durch den Service Bus-Dienst sowie die Latenz der Anforderung und der Antwort. Die Vorgänge müssen parallel ausgeführt werden, um die Anzahl von Vorgängen pro Zeitraum zu erhöhen. Weitere Informationen finden Sie unter [Best Practices für Leistungsoptimierungen mithilfe von Service Bus-Brokermessaging](/previous-versions/azure/hh528527(v=azure.100)).

### <a name="solution"></a>Lösung
Informationen zur Verwendung der empfohlenen asynchronen Methode finden Sie unter [QueueClient-Klasse (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) .

Sehen Sie sich die Informationen zum Entwurfsmuster unter [Einführung in asynchrone Nachrichten](/previous-versions/msp-n-p/dn589781(v=pandp.10))an, um die Leistung der Azure-Messaginginfrastruktur zu verbessern.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Partitionieren von Service Bus-Warteschlangen und -Themen
### <a name="id"></a>id
AP2004

### <a name="description"></a>BESCHREIBUNG
Partitionieren Sie Service Bus-Warteschlangen und -Themen, um eine bessere Leistung in Verbindung mit dem Service Bus-Messaging zu erzielen.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Die Partitionierung von Service Bus-Warteschlangen und -Themen führt zu einer Erhöhung von Leistungsdurchsatz und Dienstverfügbarkeit, da der Gesamtdurchsatz einer partitionierten Warteschlange oder eines Themas nicht mehr durch die Leistung eines einzelnen Nachrichtenbrokers oder Nachrichtenspeichers beschränkt wird. Außerdem führt ein vorübergehender Ausfall eines Nachrichtenspeichers nicht dazu, dass eine partitionierte Warteschlange oder ein Thema nicht verfügbar ist. Weitere Informationen finden Sie unter [Partitionieren von Nachrichtenentitäten](/previous-versions/azure/dn520246(v=azure.100)).

### <a name="solution"></a>Lösung
Der folgende Codeausschnitt veranschaulicht die Partitionierung von Nachrichtenentitäten.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Weitere Informationen finden Sie unter [Partitionierte Service Bus-Warteschlangen und -Themen | Microsoft Azure-Blog](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/). Sehen Sie sich außerdem das Beispiel [Microsoft Azure Service Bus – Partitionierte Warteschlange](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) an.

## <a name="do-not-set-sharedaccessstarttime"></a>Vermeiden des Festlegens von SharedAccessStartTime
### <a name="id"></a>id
AP3001

### <a name="description"></a>BESCHREIBUNG
Sie sollten das Verwenden von SharedAccessStartTimeset zum Angeben der aktuellen Zeit vermeiden, um die Shared Access-Richtlinie sofort zu starten. Sie müssen diese Eigenschaft nur festlegen, wenn Sie die Shared Access-Richtlinie zu einem späteren Zeitpunkt starten möchten.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Die Uhrsynchronisierung verursacht einen leichten Zeitunterschied zwischen Rechenzentren. Es erscheint beispielsweise logisch, dass das Festlegen der Startzeit einer SAS-Speicherrichtlinie auf die aktuelle Uhrzeit per „DateTime.Now“ oder mit einer ähnlichen Methode dazu führt, dass die SAS-Richtlinie sofort wirksam wird. Die leichten Zeitunterschiede zwischen Rechenzentren können hierbei aber zu Problemen führen, da einige Rechenzentrumzeiten etwas zurückhinken, während andere bereits leicht voraus sind. Daher läuft die SAS-Richtlinie unter Umständen schnell ab (oder sogar sofort), wenn die Lebensdauer der Richtlinie zu kurz ist.

Eine ausführliche Anleitung zur Verwendung von Shared Access Signature für Azure-Speicher finden Sie unter [Einführung in Tabellen-SAS (Shared Access Signature), Warteschlangen-SAS und Blob-SAS-Update – Microsoft Azure Storage-Teamblog – Homepage der Website – MSDN-Blogs](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)(in englischer Sprache).

### <a name="solution"></a>Lösung
Entfernen Sie die Anweisung, mit der die Startzeit der Shared Access-Richtlinie festgelegt wird. Das Codeanalysetool von Azure enthält eine Lösung für dieses Problem. Weitere Informationen zur Sicherheitsverwaltung finden Sie unter dem Entwurfsmuster [Valet-Schlüsselmuster](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

Der folgende Codeausschnitt veranschaulicht die Codefehlerbehebung für dieses Problem:

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Ablaufzeit der SAS-Richtlinie muss mehr als fünf Minuten betragen
### <a name="id"></a>id
AP3002

### <a name="description"></a>BESCHREIBUNG
Für Uhren zwischen Rechenzentren an verschiedenen Standorten können aufgrund einer Bedingung, die als Uhrabweichung (Clock Skew) bezeichnet wird, bis zu fünf Minuten Unterschied herrschen. Um zu verhindern, dass das SAS-Richtlinientoken früher als geplant abläuft, sollten Sie die Ablaufzeit auf mehr als fünf Minuten festlegen.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Die Rechenzentren an verschiedenen Standorten weltweit werden mithilfe eines Uhrsignals synchronisiert. Da es einige Zeit dauert, bis das Uhrsignal die unterschiedlichen Standorte erreicht hat, kann es zu einer Zeitvarianz zwischen Rechenzentren an den einzelnen geografischen Orten kommen, obwohl scheinbar alles synchronisiert ist. Der Zeitunterschied kann sich auf die Startzeit und das Ablaufintervall der Shared Access-Richtlinie auswirken. Geben Sie daher die Startzeit nicht an, um sicherzustellen, dass die Shared Access-Richtlinie sofort wirksam wird. Stellen Sie außerdem sicher, dass die Ablaufzeit mehr als fünf Minuten lang ist, um eine frühe Zeitüberschreitung zu verhindern.

Weitere Informationen zur Verwendung von Shared Access Signature für Azure-Speicher finden Sie unter [Einführung in Tabellen-SAS (Shared Access Signature), Warteschlangen-SAS und Blob-SAS-Update – Microsoft Azure Storage-Teamblog – Homepage der Website – MSDN-Blogs](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)(in englischer Sprache).

### <a name="solution"></a>Lösung
Weitere Informationen zur Sicherheitsverwaltung finden Sie unter dem Entwurfsmuster [Valet-Schlüsselmuster](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

Im folgenden Beispiel wird keine Startzeit für die Shared Access-Richtlinie angegeben.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Im folgenden Beispiel wird die Startzeit für eine Shared Access-Richtlinie mit einer Richtlinienablaufdauer angegeben, die größer als fünf Minuten ist.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Weitere Informationen finden Sie unter [Konfigurieren des anonymen öffentlichen Lesezugriffs für Container und Blobs](/azure/storage/blobs/anonymous-read-access-configure?tabs=portal).

## <a name="use-cloudconfigurationmanager"></a>Verwenden von CloudConfigurationManager
### <a name="id"></a>id
AP4000

### <a name="description"></a>BESCHREIBUNG
Durch die Verwendung der [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx)-Klasse für Projekte, z.B. Azure Website und Azure Mobile Services, ergeben sich keine Laufzeitprobleme. Es ist jedoch eine bewährte Methode, Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) als einheitliches Verfahren zum Verwalten von Konfigurationen für alle Azure-Cloudanwendungen zu verwenden.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
CloudConfigurationManager liest die für die Anwendungsumgebung passende Konfigurationsdatei.

[CloudConfigurationManager](/previous-versions/azure/)

### <a name="solution"></a>Lösung
Gestalten Sie Ihren Code so um, dass die [CloudConfigurationManager-Klasse](/previous-versions/azure/reference/mt634650(v=azure.100))verwendet wird. Eine Codebehebung für dieses Problem ist mit dem Codeanalysetool von Azure möglich.

Der folgende Codeausschnitt veranschaulicht die Codefehlerbehebung für dieses Problem: Replace

`var settings = ConfigurationManager.AppSettings["mySettings"];`

durch

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Hier ist ein Beispiel dafür angegeben, wie Sie die Konfigurationseinstellung in einer App.config- oder Web.config-Datei speichern. Fügen Sie die Einstellungen dem appSettings-Abschnitt der Konfigurationsdatei hinzu. Unten ist die Datei „Web.config“ zum vorherigen Codebeispiel angegeben.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Vermeiden der Verwendung von hartcodierten Verbindungszeichenfolgen
### <a name="id"></a>id
AP4001

### <a name="description"></a>BESCHREIBUNG
Wenn Sie hartcodierte Verbindungszeichenfolgen verwenden und diese später aktualisieren möchten, müssen Sie Änderungen an Ihrem Quellcode vornehmen und die Anwendung neu kompilieren. Falls Sie Ihre Verbindungszeichenfolgen in einer Konfigurationsdatei speichern, können Sie diese später aber ändern, indem Sie einfach die Konfigurationsdatei aktualisieren.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Das Hartcodieren von Verbindungszeichenfolgen ist keine bewährte Methode, da dies zu Problemen führt, wenn Verbindungszeichenfolgen schnell geändert werden müssen. Wenn das Projekt in die Quellcodeverwaltung eingecheckt sein muss, führen hartcodierte Verbindungszeichenfolgen außerdem zu Schwachstellen in Bezug auf die Sicherheit, da die Zeichenfolgen im Quellcode angezeigt werden können.

### <a name="solution"></a>Lösung
Speichern Sie Verbindungszeichenfolgen in den Konfigurationsdateien oder in Azure-Umgebungen.

* Verwenden Sie für eigenständige Anwendungen die Datei „app.config“, um die Einstellungen für die Verbindungszeichenfolge zu speichern.
* Verwenden Sie für IIS-gehostete Webanwendungen die Datei „web.config“ zum Speichern der Verbindungszeichenfolgen.
* Verwenden Sie für ASP.NET vNext-Anwendungen die Datei „configuration.json“ zum Speichern der Verbindungszeichenfolgen.

Informationen zur Verwendung von Konfigurationsdateien wie „web.config“ oder „app.config“ finden Sie unter [ASP.NET-Webkonfigurationsrichtlinien](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Weitere Informationen zur Funktionsweise von Azure-Umgebungsvariablen finden Sie unter [Azure-Websites: Funktionsweise von Anwendungs- und Verbindungszeichenfolgen](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Informationen zum Speichern der Verbindungszeichenfolge in der Quellcodeverwaltung finden Sie unter [Vermeiden des Einfügens von vertraulichen Informationen (z. B. Verbindungszeichenfolgen) in Dateien, die im Quellcode-Repository gespeichert werden](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Verwenden der Konfigurationsdatei für die Diagnose
### <a name="id"></a>id
AP5000

### <a name="description"></a>BESCHREIBUNG
Anstatt Diagnoseeinstellungen in Ihrem Code zu konfigurieren, z. B. mithilfe der Microsoft.WindowsAzure.Diagnostics-Programmier-API, sollten Sie die Diagnoseeinstellungen in der Datei „diagnostics.wadcfg“ konfigurieren. (Oder in „diagnostics.wadcfgx“, wenn Sie Azure SDK 2.5 verwenden.) Auf diese Weise können Sie Diagnoseeinstellungen ändern, ohne den Code neu kompilieren zu müssen.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
Vor der Veröffentlichung von Azure SDK 2.5 (mit Verwendung von Azure Diagnostics 1.3) konnte Azure Diagnostics (WAD) mit mehreren unterschiedlichen Methoden konfiguriert werden: durch das Hinzufügen zum Konfigurations-Blob im Speicher, per imperativem Code, per deklarativer Konfiguration oder über die Standardkonfiguration. Allerdings ist die bevorzugte Methode zum Konfigurieren der Diagnose die Verwendung einer XML-Konfigurationsdatei („diagnostics.wadcfg“ oder „diagnostics.wadcfgx“ für SDK 2.5 und höher) im Anwendungsprojekt. Bei diesem Ansatz wird die Konfiguration vollständig über die Datei „diagnostics.wadcfg“ definiert und kann je nach Bedarf aktualisiert und neu bereitgestellt werden. Das Mischen der Konfigurationsdatei „diagnostics.wadcfg“ mit den programmgesteuerten Methoden der Konfigurationsfestlegung mithilfe der Klassen [DiagnosticMonitor](/previous-versions/azure/reference/ee758597(v=azure.100)) oder [RoleInstanceDiagnosticManager](/previous-versions/azure/reference/ee773157(v=azure.100)) kann zu Verwirrung führen. Weitere Informationen finden Sie unter [Initialisieren oder Ändern der Azure-Diagnosekonfiguration](/previous-versions/azure/hh411537(v=azure.100)) .

Ab WAD 1.3 (Teil von Azure SDK 2.5) ist es nicht mehr möglich, Code zum Konfigurieren der Diagnose zu verwenden. Sie können die Konfiguration daher nur angeben, wenn Sie die Diagnoseerweiterung anwenden oder aktualisieren.

### <a name="solution"></a>Lösung
Verwenden Sie den Designer für die Diagnosekonfiguration, um die Diagnoseeinstellungen in die Diagnosekonfigurationsdatei zu verschieben („diagnostics.wadcfg“ oder „diagnostics.wadcfgx“ für SDK 2.5 und höher). Es wird empfohlen, [Azure SDK 2.5](https://social.msdn.microsoft.com/Forums/en-US/home) zu installieren und die aktuelle Diagnosefunktion zu verwenden.

1. Wählen Sie im Kontextmenü für die Rolle, die Sie konfigurieren möchten, die Option „Eigenschaften“ und dann die Registerkarte „Konfiguration“.
2. Im Abschnitt **Diagnose** muss das Kontrollkästchen **Diagnose aktivieren** aktiviert sein.
3. Klicken Sie auf die Schaltfläche **Konfigurieren**.

   ![Zugreifen auf die Option „Diagnose aktivieren“](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Weitere Informationen finden Sie unter [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) .

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Vermeiden der Deklaration von DbContext-Objekten als „statisch“
### <a name="id"></a>id
AP6000

### <a name="description"></a>BESCHREIBUNG
Vermeiden Sie die Deklaration von DBContext-Objekten als „statisch“, um Arbeitsspeicher zu sparen.

Ihre Ideen und Feedback hierzu können Sie uns unter [Feedback zur Azure-Codeanalyse](https://social.msdn.microsoft.com/Forums/en-US/home)gern mitteilen.

### <a name="reason"></a>`Reason`
DBContext-Objekte enthalten die Abfrageergebnisse für jeden Aufruf. Statische DBContext-Objekte werden erst verworfen, wenn die Anwendungsdomäne entladen wird. Aus diesem Grund kann ein statisches DBContext-Objekt große Mengen an Arbeitsspeicher belegen.

### <a name="solution"></a>Lösung
Deklarieren Sie DBContext als lokale Variable oder nicht statisches Instanzenfeld, verwenden Sie es für eine Aufgabe, und lassen Sie es dann zu, dass es nach der Verwendung verworfen wird.

Im folgenden Beispiel wird anhand der MVC-Controller-Klasse veranschaulicht, wie das DBContext-Objekt verwendet wird.

```csharp
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zur Optimierung und Problembehandlung von Azure-Apps finden Sie unter [Behandeln von Problemen bei Web-Apps in Azure App Service in Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
