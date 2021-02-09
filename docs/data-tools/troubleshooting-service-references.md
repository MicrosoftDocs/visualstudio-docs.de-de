---
title: Problembehandlung bei Dienstverweisen
description: Überprüfen Sie häufige Probleme, die auftreten können, wenn Sie mit Windows Communication Foundation (WCF) oder WCF Data Services verweisen in Visual Studio arbeiten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 909291e3f9762593a58df93a9ccc7fe2e82b7952
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866358"
---
# <a name="troubleshoot-service-references"></a>Problembehandlung bei Dienstverweisen

In diesem Thema werden häufige Probleme aufgelistet, die auftreten können, wenn Sie mit Windows Communication Foundation (WCF) oder WCF Data Services verweisen in Visual Studio arbeiten.

## <a name="error-returning-data-from-a-service"></a>Fehler beim Zurückgeben von Daten aus einem Dienst.

Wenn Sie einen `DataSet` oder `DataTable` von einem Dienst zurückgeben, erhalten Sie möglicherweise die Ausnahme "das Kontingent für die maximale Größe für eingehende Nachrichten wurde überschritten". Standardmäßig ist die- `MaxReceivedMessageSize` Eigenschaft für einige Bindungen auf einen relativ kleinen Wert festgelegt, um das Risiko von Denial-of-Service-Angriffen einzuschränken. Sie können diesen Wert erhöhen, um die Ausnahme zu verhindern. Weitere Informationen finden Sie unter <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

So beheben Sie diesen Fehler

1. Doppelklicken Sie in **Projektmappen-Explorer** auf die *app.config* Datei, um Sie zu öffnen.

2. Suchen `MaxReceivedMessageSize` Sie die-Eigenschaft, und ändern Sie Sie in einen größeren Wert.

## <a name="cannot-find-a-service-in-my-solution"></a>In meiner Projekt Mappe wurde kein Dienst gefunden.

Wenn Sie im Dialogfeld **Dienst Verweise hinzufügen** auf die Schaltfläche **ermitteln** klicken, wird mindestens ein WCF-Dienst Bibliotheksprojekt in der Projekt Mappe nicht in der Liste der Dienste angezeigt. Dies kann vorkommen, wenn der Projekt Mappe eine Dienst Bibliothek hinzugefügt wurde, die jedoch noch nicht kompiliert wurde.

So beheben Sie diesen Fehler

- Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das WCF-Dienst Bibliotheksprojekt, und klicken Sie auf **Erstellen**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Fehler beim Zugriff auf einen Dienst über einen Remote Desktop.

Wenn ein Benutzer über eine Remote Desktop Verbindung auf einen im Internet gehosteten WCF-Dienst zugreift und der Benutzer nicht über Administrator Berechtigungen verfügt, wird die NTLM-Authentifizierung verwendet. Wenn der Benutzer nicht über Administrator Berechtigungen verfügt, erhält der Benutzer möglicherweise die folgende Fehlermeldung: "die HTTP-Anforderung ist mit dem Client Authentifizierungsschema ' anonymous ' nicht autorisiert. Der vom Server empfangene Authentifizierungs Header war ' NTLM '. "

So beheben Sie diesen Fehler

1. Öffnen Sie im Website Projekt die **Eigenschaften** Seiten.

2. Deaktivieren Sie auf der Registerkarte **Start Optionen** das Kontrollkästchen **NTLM-Authentifizierung** .

    > [!NOTE]
    > Sie sollten die NTLM-Authentifizierung nur für Websites deaktivieren, die ausschließlich WCF-Dienste enthalten. Die Sicherheit für WCF-Dienste wird durch die Konfiguration in der *web.config* -Datei verwaltet. Dadurch ist die NTLM-Authentifizierung unnötig.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Die Einstellung für die Zugriffsebene für generierte Klassen hat keine Auswirkungen.

Das Festlegen der Option **Zugriffsebene für generierte Klassen** im Dialogfeld **Dienst Verweise konfigurieren** auf **intern** oder **Friend** funktioniert möglicherweise nicht immer. Obwohl die-Option im Dialogfeld festgelegt werden muss, werden die resultierenden Unterstützungs Klassen mit der Zugriffsebene generiert `Public` .

Dies ist eine bekannte Einschränkung für bestimmte Typen, z. b. solche, die mithilfe von serialisiert werden <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="error-debugging-service-code"></a>Fehler beim Debugging von Dienst Code

Wenn Sie den Code für einen WCF-Dienst aus dem Client Code in Einzelschritten ausführen, erhalten Sie möglicherweise einen Fehler im Zusammenhang mit fehlenden Symbolen. Dies kann vorkommen, wenn ein Dienst, der Teil der Projekt Mappe war, verschoben oder aus der Projekt Mappe entfernt wurde.

Beim ersten Hinzufügen eines Verweises auf einen WCF-Dienst, der Teil der aktuellen Projekt Mappe ist, wird zwischen dem Dienstprojekt und dem Dienst Client Projekt eine explizite Buildabhängigkeit hinzugefügt. Dadurch wird sichergestellt, dass der Client immer auf aktuelle Dienst Binärdateien zugreift. Dies ist besonders wichtig für das Debuggen von Szenarien wie das Ausführen von Client Code in den Dienst Code.

Wenn das Dienstprojekt aus der Projekt Mappe entfernt wird, wird diese explizite Buildabhängigkeit als ungültig erklärt. Visual Studio kann nicht mehr garantieren, dass das Dienstprojekt bei Bedarf neu erstellt wird.

Um diesen Fehler zu beheben, müssen Sie das Dienstprojekt manuell neu erstellen:

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie im Dialogfeld **Optionen** den Eintrag **Projekte und Projekt** Mappen, und wählen Sie dann **Allgemein** aus.

3. Stellen Sie sicher, dass das Kontrollkästchen **Erweiterte Buildkonfigurationen anzeigen** aktiviert ist, und klicken Sie dann auf **OK**.

4. Laden Sie das WCF-Dienstprojekt.

5. Legen Sie im Dialogfeld **Configuration Manager** die aktive Projektmappenkonfiguration auf **Debuggen** fest.  Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).

6. Wählen Sie in **Projektmappen-Explorer** das WCF-Dienstprojekt aus.

7. Klicken Sie im Menü **Erstellen** auf **neu erstellen** , um das WCF-Dienstprojekt neu zu erstellen.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services nicht im Browser angezeigt.

Wenn versucht wird, eine XML-Darstellung von Daten in einem anzuzeigen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , interpretiert Internet Explorer die Daten möglicherweise nicht als RSS-Feed. Stellen Sie sicher, dass die Option zum Anzeigen von RSS-Feeds deaktiviert ist.

Deaktivieren Sie RSS-Feeds, um diesen Fehler zu beheben:

1. Klicken Sie in Internet Explorer im Menü **Extras** auf **Internetoptionen**.

2. Klicken Sie auf der Registerkarte **Inhalt** im Abschnitt **Feeds** auf **Einstellungen**.

3. Deaktivieren Sie im Dialogfeld **Feed-Einstellungen** das Kontrollkästchen **Feed-Leseansicht** aktivieren, und klicken Sie dann auf **OK**.

4. Klicken Sie auf **OK** , um das Dialogfeld **Internet Optionen** zu schließen.

## <a name="see-also"></a>Weitere Informationen

- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
