---
title: Workflow-Designer-Receive-Aktivitäts Designer
description: Erfahren Sie mehr über die Receive-Aktivität und die Verwendung des Receive-Aktivitäts Designers, um eine Empfangs Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6414d92cea867a1235d73a39b6415ab884651ec
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434193"
---
# <a name="receive-activity-designer"></a>Receive-Aktivitätsdesigner

Der **Receive** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.ServiceModel.Activities.Receive> . Eine <xref:System.ServiceModel.Activities.Receive>-Aktivität ist eine Aktivität, die eine Nachricht empfängt, die entweder ein integrierter Datentyp, etwa ein <xref:System.ServiceModel.Channels.Message>-, <xref:System.IO.Stream>- oder ein <xref:System.Xml.Linq.XElement>-Typ sein kann oder ein anwendungsdefinierter Datenvertrag, ein Nachrichtenvertrag oder eine XML-Klasse, die serialisiert werden kann.

## <a name="the-receive-activity"></a>Die Receive-Aktivität

Die <xref:System.ServiceModel.Activities.Receive>-Aktivität kann abhängig vom Typ des verwendeten Empfangsinhalts ein einzelnes Element oder mehrere Elemente empfangen. Eine <xref:System.ServiceModel.Activities.SendReply>-Aktivität kann an eine <xref:System.ServiceModel.Activities.Receive>-Aktivität gebunden werden, die eine Nachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters des Dienstes empfängt.

### <a name="using-the-receive-activity-designer"></a>Verwenden des Receive-Aktivitätsdesigners

Greifen Sie auf den **Receive** -Aktivitäts Designer in der Kategorie **Messaging** der **Toolbox** zu. Der **Receive** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **Receive** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

Um eine <xref:System.ServiceModel.Activities.SendReply> -Aktivität zu erstellen und an die ausgewählte Aktivität zu binden, klicken Sie mit der <xref:System.ServiceModel.Activities.Receive> rechten Maustaste auf den **Receive** -Aktivitäts Designer, und klicken Sie im Kontextmenü auf das Element **SendReply erstellen** , und der **sendreplytor eceive** -Designer wird unter dem **Empfangs** -Designer angezeigt. Die <xref:System.ServiceModel.Activities.SendReply>-Aktivität ist eine Aktivität, die die Antwortnachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters des Dienstes sendet. Sie kann mit dem **sendreplytor eceive** -Designer konfiguriert werden.

Alternativ kann der **receiveandsendreply** -Vorlagen Designer in der Kategorie **Messaging** der **Toolbox** verwendet werden, um ein paar vorkonfigurierter- <xref:System.ServiceModel.Activities.Receive> Aktivität und-Aktivität zu erstellen <xref:System.ServiceModel.Activities.SendReply> . Weitere Informationen zur Verwendung der Vorlage " **receiveandsendreply** " und " **sendreplytor eceive** " finden Sie im Thema " [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md) ".

### <a name="the-receive-activity-properties"></a>Die Receive-Aktivitätseigenschaften

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.Receive>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster oder auf der Workflow-Designer-Oberfläche bearbeitet werden. Die einzige erforderliche Eigenschaft ist die <xref:System.ServiceModel.Activities.Receive.OperationName%2A>-Eigenschaft.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | FALSE | Gibt den benutzerfreundlichen Namen der <xref:System.ServiceModel.Activities.Receive>-Aktivität an. Der Standardwert lautet Receive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Wahr | Gibt den Namen des von dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität implementierten Dienstvorgangs an. Diese Eigenschaft wird verwendet, um den Standardwert für die **Action** -Eigenschaft zu erstellen, wenn die **Action** -Eigenschaft nicht explizit festgelegt ist. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | FALSE | Gibt den Namen des Dienstvertrags an. Diese Eigenschaft wird verwendet, um Dienstvorgänge in einzelne Dienstverträge zu gruppieren. Alle <xref:System.ServiceModel.Activities.Receive>-Aktivitäten, die über den gleichen <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> verfügen, werden in den gleichen Dienstvertrag (WSDL-Anschlusstyp) gruppiert. Der Standardwert ist der voll qualifizierte CLR-Name der Aktivität der obersten Ebene (root). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | FALSE | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie die Schaltfläche mit den Auslassungs Punkten neben dem Feld **Inhalt** im Eigenschaften Raster auswählen oder auf der Oberfläche des **Empfangs** Aktivitäts Designers auf die Schaltfläche **definieren...** neben der **Inhalts** Bezeichnung klicken. Beide zeigen das Dialogfeld **Inhalts Definition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Inhalts Definition (Dialog Feld](../workflow-designer/content-definition-dialog-box.md) ). |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | FALSE | Gibt die Korrelationen zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten in Dienstvorgängen eines Workflows mit einem <xref:System.ServiceModel.MessageQuerySet>-Objekt an. Klicken Sie im Eigenschaften Raster neben der-Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> , um das Dialogfeld **CorrelatesOn-Definition** zu öffnen. Weitere Informationen zur Verwendung dieses Dialog Felds finden Sie im Thema [Inhalts Definition (Dialogfeld](../workflow-designer/content-definition-dialog-box.md) ). |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | FALSE | Gibt den <xref:System.ServiceModel.Activities.CorrelationHandle> an, der verwendet wurde, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.<br /><br /> Klicken Sie im Eigenschaften Raster neben der-Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> , um das Dialogfeld **Ausdrucks-Editor** zu öffnen. Weitere Informationen zur Verwendung dieses Dialog Felds finden Sie im Thema Gewusst [wie: Verwenden des Ausdrucks-Editors](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | FALSE | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie im Eigenschaften Raster neben der Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> , um das Dialogfeld **korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialog Feld "correlationinitializers hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) ". |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | FALSE | Gibt einen Wert an, der bestimmt, ob eine neue Workflowinstanz zur Verarbeitung der Nachricht erstellt wird, wenn die Nachricht keiner vorhandenen Workflowinstanz entspricht. Wenn der Wert auf **true** festgelegt ist, wird eine neue Workflow Instanz erstellt, um die Nachricht zu verarbeiten, wenn die Nachricht nicht mit einer vorhandenen Workflow Instanz korreliert wird. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | FALSE | Gibt eine Auflistung bekannter Typen für den von dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität implementierten Dienstvorgang an. Diese Eigenschaft muss in Verbindung mit der <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>-Eigenschaft verwendet werden, die auf <xref:System.Runtime.Serialization.DataContractSerializer> festgelegt wurde. Sie wird ignoriert, wenn der <xref:System.Xml.Serialization.XmlSerializer> verwendet wird.<br /><br /> Wählen Sie im Eigenschaften Raster neben dem Feld **KnownTypes** die Schaltfläche mit den Auslassungs Zeichen, um das Dialogfeld typauflistungs- **Editor** anzuzeigen, mit dem Sie relevante Typen hinzufügen können Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema zum typauflistungs- [Editor (Dialog Feld](../workflow-designer/type-collection-editor-dialog-box.md) ). |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | FALSE | Gibt die <xref:System.Net.Security.ProtectionLevel>-Einstellung für die Nachricht an.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> bedeutet nur Authentifizierung.<br />2.  <xref:System.Net.Security.ProtectionLevel> bedeutet das Signieren von Daten, um die Integrität der übertragenen Daten sicherzustellen.<br />3.  <xref:System.Net.Security.ProtectionLevel> bedeutet, dass Daten verschlüsselt und signiert werden, um die Vertraulichkeit und Integrität der übertragenen Daten sicherzustellen. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | FALSE | Gibt den Typ des Serialisierungsprogramms an, das für den von der <xref:System.ServiceModel.Activities.Receive>-Aktivität implementierten Dienstvorgang verwendet werden soll. Der Standardwert ist <xref:System.Runtime.Serialization.DataContractSerializer>, der eine Instanz eines Typs, der einen angegebenen Datenvertrag verwendet, in einen XML-Datenstrom oder ein Dokument serialisiert und deserialisiert. Der <xref:System.Xml.Serialization.XmlSerializer> kann auch verwendet werden, wenn eine genauere Kontrolle des XML-Codes erforderlich ist. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | FALSE | Gibt den Aktionsheader der Nachricht an. Wenn Sie nicht explizit festgelegt ist, wird der Wert standardmäßig auf festgelegt `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
