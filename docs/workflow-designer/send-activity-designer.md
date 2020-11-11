---
title: Workflow-Designer Send-Aktivitäts Designer
description: Erfahren Sie mehr über die Send-Aktivität und die Verwendung des Send-Aktivitäts Designers, um eine Send-Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78925411f911f9c0dfc0c2cfff891deca0e91e3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434050"
---
# <a name="send-activity-designer"></a>Send-Aktivitätsdesigner

Der **Send** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.ServiceModel.Activities.Send> .

## <a name="the-send-activity"></a>Die Send-Aktivität

 Eine <xref:System.ServiceModel.Activities.Send>-Aktivität wird verwendet, um eine Nachricht an einen Dienst zu senden. Eine <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität kann an eine <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden werden, die eine Nachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Client empfängt.

### <a name="using-the-send-activity-designer"></a>Verwenden des Send-Aktivitätsdesigners

Greifen Sie auf den **Send** -Aktivitäts Designer in der Kategorie **Messaging** der **Toolbox** zu. Der **Send** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Daraufhin wird eine <xref:System.ServiceModel.Activities.Send>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert Send erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **Send** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

Um eine <xref:System.ServiceModel.Activities.ReceiveReply> -Aktivität zu erstellen und an die ausgewählte Aktivität zu binden, klicken Sie mit der <xref:System.ServiceModel.Activities.Send> rechten Maustaste auf den **Send** -Aktivitäts Designer, klicken Sie im Kontextmenü auf das Element **receivereply erstellen** , und der **receivereplyforsend** -Designer wird unterhalb des **Send** -Designers angezeigt. Die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität ist eine Aktivität, die eine Nachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Client empfängt. Sie kann mit dem **receivereplyforsend** -Designer konfiguriert werden.

Alternativ kann der **sendandreceivereply** -Vorlagen Designer in der Kategorie **Messaging** der **Toolbox** verwendet werden, um ein paar vorkonfigurierter-und-Aktivitäten zu erstellen <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Weitere Informationen zur Verwendung der Vorlagen **sendandreceivereply** und **receivereplyforsend** finden Sie im Thema [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) .

### <a name="the-send-activity-properties"></a>Die Eigenschaften der Send-Aktivität

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.Send>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster oder auf Workflow-Designer-Oberfläche bearbeitet werden.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | FALSE | Der Anzeigename der <xref:System.ServiceModel.Activities.Send>-Aktivität. Der Standardwert lautet Send. Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Wahr | Der Name des Dienstvorgangs, der von dieser <xref:System.ServiceModel.Activities.Send>-Aktivität aufgerufen wurde. Diese Eigenschaft wird verwendet, um den Standardwert für die **Action** -Eigenschaft zu erstellen, wenn die **Action** -Eigenschaft nicht explizit festgelegt ist. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Wahr | Der Name des Dienstvertrags, der von dem aufzurufenden Dienst implementiert wird. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | FALSE | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie die Schaltfläche mit den Auslassungs Punkten neben dem Feld **Inhalt** im Eigenschaften Raster auswählen oder auf der Oberfläche des **Empfangs** Aktivitäts Designers auf die Schaltfläche **definieren...** neben der **Inhalts** Bezeichnung klicken. Beide zeigen das Dialogfeld **Inhalts Definition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Inhalts Definition (Dialog Feld](../workflow-designer/content-definition-dialog-box.md) ). |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | FALSE | Gibt den <xref:System.ServiceModel.Activities.CorrelationHandle> an, der verwendet wurde, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.<br /><br /> Klicken Sie im Eigenschaften Raster neben der-Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> , um das Dialogfeld **Ausdrucks-Editor** zu öffnen. Weitere Informationen zur Verwendung dieses Dialog Felds finden Sie im Thema Gewusst [wie: Verwenden des Ausdrucks-Editors](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | FALSE | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Send>-Aktivität im Workflow konfigurieren. Klicken Sie im Eigenschaften Raster neben der Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> , um das Dialogfeld **korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialog Feld "correlationinitializers hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) ". |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | FALSE | Eine Auflistung bekannter Typen für den von dieser <xref:System.ServiceModel.Activities.Send>-Aktivität aufzurufenden Dienstvorgang. Diese Eigenschaft muss in Verbindung mit der <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>-Eigenschaft verwendet werden, die auf <xref:System.Runtime.Serialization.DataContractSerializer> festgelegt wurde. Sie wird ignoriert, wenn der <xref:System.Xml.Serialization.XmlSerializer> verwendet wird.<br /><br /> Wählen Sie im Eigenschaften Raster neben dem Feld **KnownTypes** die Schaltfläche mit den Auslassungs Zeichen, um das Dialogfeld typauflistungs- **Editor** anzuzeigen, dem Sie relevante Typen hinzufügen können<br /><br /> Wählen Sie im Eigenschaften Raster neben dem Feld **KnownTypes** die Schaltfläche mit den Auslassungs Zeichen, um das Dialogfeld typauflistungs- **Editor** anzuzeigen, mit dem Sie relevante Typen hinzufügen können Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema zum typauflistungs- [Editor (Dialog Feld](../workflow-designer/type-collection-editor-dialog-box.md) ). |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Wahr | Gibt die <xref:System.Net.Security.ProtectionLevel>-Einstellung für die Nachricht an.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> bedeutet nur Authentifizierung.<br />2.  <xref:System.Net.Security.ProtectionLevel> bedeutet das Signieren von Daten, um die Integrität der übertragenen Daten sicherzustellen.<br />3.  <xref:System.Net.Security.ProtectionLevel> bedeutet, dass Daten verschlüsselt und signiert werden, um die Vertraulichkeit und Integrität der übertragenen Daten sicherzustellen. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Wahr | Das Serialisierungsprogramm, das für den Dienstvorgang verwendet werden soll, der von der <xref:System.ServiceModel.Activities.Send>-Aktivität aufgerufen werden soll. Der Standardwert lautet <xref:System.Runtime.Serialization.DataContractSerializer>, der unter Verwendung eines angegebenen Datenvertrags eine Instanz eines Typs in einen XML-Datenstrom oder ein Dokument serialisiert und daraus deserialisiert. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | FALSE | Gibt den Aktionsheader der Nachricht an. Wenn Sie nicht explizit festgelegt ist, wird der Wert standardmäßig auf festgelegt `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . Bei Festlegung für eine <xref:System.ServiceModel.Activities.Send>-Aktivität muss die <xref:System.ServiceModel.Activities.Receive>-Aktivität, die die Nachricht empfängt, über den gleichen Wert verfügen, damit die Nachricht ordnungsgemäß übermittelt werden kann. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | Die für den Empfänger der Nachricht zulässige <xref:System.Security.Principal.TokenImpersonationLevel>-Instanz. Er definiert Sicherheits Identitätswechsel Ebenen, die Steuern, in welchem Umfang ein Server Prozess im Auftrag eines Client Prozesses agieren kann.<xref:System.Security.Principal.TokenImpersonationLevel>  gibt an, dass keine Identitätswechselebene zugeordnet ist. <xref:System.Security.Principal.TokenImpersonationLevel> Gibt an, dass der Server Prozess keine Identifikationsinformationen zum Client abrufen kann und nicht die Identität des Clients annehmen kann. <xref:System.Security.Principal.TokenImpersonationLevel> Gibt an, dass der Server Prozessinformationen zum Client abrufen kann (z. b. Sicherheits-IDs und Berechtigungen), aber nicht die Identität des Clients annehmen kann. Dies ist nützlich für Server, die eigene Objekte exportieren (z. B. Datenbankprodukte, von denen Tabellen und Ansichten exportiert werden). Mit den abgerufenen Informationen zur Clientsicherheit können vom Server Entscheidungen im Rahmen der Zugriffsvalidierung getroffen werden, ohne dass andere Dienste verwendet werden können, die den Sicherheitskontext des Clients verwenden. <xref:System.Security.Principal.TokenImpersonationLevel> Gibt an, dass der Server Prozess den Sicherheitskontext des Clients auf seinem lokalen System annehmen kann. Der Server kann den Client auf Remotesystemen nicht imitieren. <xref:System.Security.Principal.TokenImpersonationLevel> Gibt an, dass der Server Prozess den Sicherheitskontext des Clients auf Remote Systemen annehmen kann. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | Das <xref:System.ServiceModel.Endpoint>-Objekt, an das die <xref:System.ServiceModel.Activities.Send>-Aktivität eine Nachricht sendet. Wenn diese Eigenschaft festgelegt ist, sollte die- <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> Eigenschaft **null** sein. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Das <xref:System.ServiceModel.EndpointAddress>-Objekt, an das die Meldung gesendet wird. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Der Name der Endpunktkonfiguration. Diese Eigenschaft wird beim Konfigurieren eines Endpunkts in einer Konfigurationsdatei festgelegt. Diese Eigenschaft sollte auf den Namen festgelegt werden, der im- **\<endpoint>** Element in der Konfigurationsdatei angegeben ist. Wenn diese Eigenschaft festgelegt ist, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> sollte die-Eigenschaft **null** sein. |

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Medizinisch](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)