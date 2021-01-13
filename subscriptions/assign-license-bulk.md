---
title: Zuweisen von Lizenzen zu Benutzergruppen für Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 10/22/2020
ms.topic: how-to
description: Erfahren Sie, wie Administratoren Lizenzen über die Funktion zum Massenhinzufügen oder mithilfe von Microsoft Azure Active Directory-Gruppen mehreren Abonnenten zuweisen können.
ms.openlocfilehash: e9d4cd5c7e73cdc3b71768a498a7c02546d3e1fc
ms.sourcegitcommit: 74b67f102d243e3b74a93563e834f49df298e4b8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97696622"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Zuweisen von Abonnements zu mehreren Benutzern
Im Verwaltungsportal für Abonnements können Sie Benutzer einzeln oder in großen Gruppen hinzufügen.  Informationen zum Hinzufügen von einzelnen Benutzern finden Sie unter [Hinzufügen einzelner Benutzer](assign-license.md).

Um große Benutzergruppen hinzuzufügen, können Sie die Funktion zum Massenhinzufügen verwenden. Wenn Ihre Organisation Microsoft Azure Active Directory (Azure AD) verwendet, können Sie hierzu alternativ Azure AD-Gruppen verwenden. In diesem Artikel wird das Vorgehen für beide Optionen beschrieben.  Sehen Sie sich dieses Video an, oder lesen Sie weiter, um mehr über das Feature zum Hinzufügen im Massenvorgang zu erfahren. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Verwenden des Massenhinzufügens zum Zuweisen von Abonnements
1. Melden Sie sich unter <https://manage.visualstudio.com> beim Verwaltungsportal für Visual Studio-Abonnements an.

1. Navigieren Sie zur Registerkarte **Abonnenten verwalten**, um mehrere Abonnenten gleichzeitig hinzuzufügen. Klicken Sie auf die Registerkarte **Hinzufügen**, und wählen Sie im Dropdownmenü **Massenhinzufügen** aus.  

1. Die Funktion zum Massenhinzufügen verwendet eine Microsoft Excel-Vorlage zum Hochladen von Abonnenteninformationen. Wählen Sie im Dialogfeld „Upload Multiple Subscribers“ (Mehrere Abonnenten hochladen) **Herunterladen** aus, um die Vorlage herunterzuladen.
   > [!div class="mx-imgBorder"]
   > ![Excel-Vorlage zum Hochladen mehrerer Abonnenten herunterladen](media/download-template-upload-subscribers.png "Laden Sie die leere Excel-Vorlage herunter, um mit dem Massenzuweisungsprozess zu beginnen.")
   >
   > [!NOTE]
   > Laden sie stets die neueste Vorlagenversion herunter. Wenn Sie eine ältere Version herunterladen, schlägt Ihr Massenupload möglicherweise fehl.

1. Tragen Sie in die Felder der Excel-Tabelle die Informationen für die Personen ein, denen Sie Abonnements zuweisen möchten. (Das Ausfüllen des Felds *Verweis* ist optional.) Speichern Sie die Datei anschließend lokal.

    > [!NOTE]
    > Eines der Felder in der Vorlage ermöglicht Administratoren, die Möglichkeit zum Herunterladen von Software für Abonnenten zu aktivieren bzw. zu deaktivieren.  Durch das Deaktivieren von Downloads wird auch der Zugriff auf Product Keys deaktiviert.

   Beachten Sie die im Folgenden aufgelisteten bewährten Methoden, um einen fehlerfreien Upload zu gewährleisten:

    - Stellen Sie sicher, dass die Formularfelder keine Kommas enthalten.
    - Entfernen Sie Leerzeichen vor und nach Formularfeldern.
    - Stellen Sie sicher, dass Benutzernamen keine zusätzlichen Leerzeichen zwischen zweiteiligen Vor- und Nachnamen aufweisen (z.B. sollten zweiteilige Namen wie „Maggie May“ nicht mit doppelten Leerzeichen geschrieben werden („MaggieMay“), da das System die überflüssigen Leerzeichen nicht automatisch entfernt).
    - Stellen Sie sicher, dass alle erforderlichen Felder ausgefüllt sind. 
    - Überprüfen Sie die Spalte **Fehlermeldung**.  Falls Fehler aufgeführt werden, lösen Sie diese, bevor Sie die Datei hochladen. 

1. Kehren Sie zum Portal für die Verwaltung von Visual Studio-Abonnements zurück. Wählen Sie im Dialogfeld **Mehrere Abonnenten hochladen** die Option **Durchsuchen** aus.
   > [!div class="mx-imgBorder"]
   > ![Zum Hochladen mehrerer Abonnenten zur gespeicherten Vorlage navigieren](media/bulk-add-browse-saved-template.png "Sie können zum Dateispeicherort navigieren oder diesen per Drag and Drop in diesem Dialogfeld ablegen.")

1. Navigieren Sie zur Excel-Datei, die Sie gespeichert haben, und wählen Sie anschließend **OK** aus.
   > [!div class="mx-imgBorder"]
   > ![Excel-Vorlage zum Upload mehrerer Abonnenten hochladen](media/bulk-upload-subscribers.png "Hier wird die Vorlage mit Ihren Daten angezeigt.  Wählen Sie „OK“ aus, um den Uploadvorgang zu starten.")

    Es wird ein Statusdialogfeld zum Uploadprozess angezeigt.

    Wenn die Vorlage Fehler enthält, schlägt auch der Upload fehl, und die Fehler werden angezeigt, damit Sie die Vorlage korrigieren und einen neuen Versuch für den Massenupload starten können.
   > [!div class="mx-imgBorder"]
   > ![Fehlermeldung nach fehlgeschlagenem Upload mehrerer Abonnenten](_img/assign-license-bulk/bulk-add-upload-failure.png "Diese Meldung wird angezeigt, wenn die hochgeladene Datei Fehler enthält.  Beheben Sie die Fehler, und führen Sie den Vorgang zum Massenhinzufügen noch mal durch.")

   Befolgen Sie diese Schritte, wenn ein Fehler auftritt:
   1. Öffnen Sie die erstellte Excel-Datei, beheben Sie die Probleme, und speichern Sie die Datei.
   0. Kehren Sie zum Verwaltungsportal zurück, und schließen Sie die Fehlermeldung.
   0. Wählen Sie **Hinzufügen** aus.
   0. Klicken Sie auf **Massenhinzufügen**.
   0. Da Sie die Excel-Datei bereits gespeichert haben, müssen Sie die Vorlage nicht herunterladen.  Wählen Sie **Durchsuchen** aus, suchen Sie nach der gerade gespeicherten Datei, und wählen Sie dann **Öffnen** aus.
   0. Klicken Sie auf **OK**.


    Wenn der Upload erfolgreich ausgeführt wurde, wird Ihnen eine Liste mit den Abonnenten und eine Bestätigungsmeldung angezeigt.
   > [!div class="mx-imgBorder"]
   > ![Bestätigungsmeldung bei erfolgreichem Upload mehrerer Abonnenten](_img/assign-license-bulk/bulk-add-upload-success.png "Sobald Ihr Upload erfolgreich abgeschlossen wird, erhalten Sie eine Bestätigungsmeldung.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Verwenden von Azure Active Directory-Gruppen zum Zuweisen von Abonnements 
Durch die Verwendung dieser Funktion ist es einfacher, den Überblick über Ihre Abonnementzuweisungen zu behalten. Sie können Azure Active Directory-Sicherheitsgruppen im Portal für die Abonnementverwaltung hinzufügen, um sicherzustellen, dass allen Personen in der Gruppe ein Abonnement zugewiesen wird. Und wenn einzelne Personen Ihre Organisation verlassen und aus dem Azure Active Directory entfernt werden, kann ihnen auf diese Weise auch einfacher der Zugriff auf die Abonnements entzogen werden. 


> [!IMPORTANT]
>
> Für die Verwendung von Azure AD-Gruppen zum Hinzufügen von Abonnements gelten die folgenden Einschränkungen:
> - Der Administrator muss Mitglied des AAD-Mandanten sein, wenn dem Verwaltungsportal zunächst eine Gruppe hinzugefügt wird.  Nachdem die Gruppe hinzugefügt wurde, ist für Änderungen an der Mitgliedschaft der Gruppen kein Administratoreingriff erforderlich. 
> - Gruppen müssen mindestens ein Mitglied enthalten.  Leere Gruppen werden nicht unterstützt.
> - Gruppen müssen weniger als 1.000 Benutzer enthalten. 
> - Alle Benutzer müssen auf oberster Ebene der Gruppe enthalten sein.  Geschachtelte Gruppen werden nicht unterstützt.
> - Es werden nur vertrauenswürdige Vereinbarungen unterstützt. (Nur Vereinbarungen, die zu viele Abonnements zuordnen dürfen, sind vertrauenswürdig.)
> - Alle Mitglieder der Gruppe müssen über eine E-Mail-Adresse verfügen, die mit ihrem Azure AD-Konto verknüpft ist.
> - Separate E-Mail-Adressen für Benachrichtigungen werden für Abonnements nicht unterstützt, die über Azure AD-Gruppen hinzugefügt wurden.  

Sehen Sie sich dieses Video an, oder lesen Sie weiter, um mehr über das Hinzufügen von Abonnenten mithilfe des Azure Active Directory-Gruppenfeatures zu erfahren. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Melden Sie sich unter [https://manage.visualstudio.com](https://manage.visualstudio.com) beim Verwaltungsportal für Visual Studio-Abonnements an.

2. Navigieren Sie zur Registerkarte **Abonnenten verwalten**, um mehrere Abonnenten gleichzeitig hinzuzufügen.

3. Klicken Sie auf die Registerkarte **Hinzufügen**, und wählen Sie im Dropdownmenü die Option **Azure Active Directory-Gruppe** aus.  

   > [!div class="mx-imgBorder"]
   > ![Auswahl zum Massenhinzufügen über Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Wählen Sie „Massenhinzufügen“ mit dem Azure AD-Feature aus, um Abonnenten aus Ihrer Azure Active Directory-Gruppe abzurufen.")

4. Geben Sie im Formularfeld den Namen der Azure AD-Gruppe ein, die Sie hinzufügen möchten. Hierdurch wird nach den verfügbaren Azure AD-Gruppen innerhalb Ihrer Organisation gesucht. 

5. Wenn Sie die Gruppe auswählen, wird das Feld automatisch mit dem Gruppennamen aufgefüllt. Sie können die Benutzer in dieser Gruppe anzeigen, bevor Sie sie hinzufügen. Im nächsten Schritt können Sie die Abonnementebene, Downloadrechte und Kommunikationseinstellungen für die Gruppe auswählen. Sofern gewünscht, können Sie im Referenzfeld Detailinformationen hinzufügen. 

   > [!div class="mx-imgBorder"]
   > ![Auswählen Ihrer Azure AD-Gruppe](_img/assign-license-bulk/bulk-add-aad-details.png "Wählen Sie den Namen Ihrer Azure AD-Gruppe aus, um Abonnenten aus dieser Gruppe hinzuzufügen.")

6. Wählen Sie **Hinzufügen** und dann **Bestätigen** aus. 

7. Um die hinzugefügte Gruppe anzuzeigen, scrollen Sie zum Ende Ihrer Benutzerliste.  

8. Wählen Sie **Abonnenten anzeigen** aus, um die Mitglieder der Gruppe anzuzeigen. Sie können Details zu den Abonnenten in der Gruppe anzeigen, aber Sie können keine Änderungen an den Abonnenten oder den ihnen zugewiesenen Abonnements vornehmen.    

> [!NOTE]
> Wenn Sie Abonnements bereits einzeln Benutzern zugewiesen haben, die anschließend zu einer Azure-AD-Gruppe hinzugefügt werden, werden sie zur Gruppe hinzugefügt und nicht mehr einzeln aufgeführt. Wenn das individuelle Abonnement jedoch für eine andere Abonnements gilt, verfügen sie über zwei Abonnements.  Beispiel:  Wenn ein Benutzer über ein individuelles Visual Studio Professional-Abonnement verfügt und Mitglied einer Gruppe ist, der Sie Visual Studio Enterprise-Abonnements hinzufügen, verfügt er über beide Abonnements.  
>
> Wenn Sie einen Abonnenten aus einer Azure Active Directory-Gruppe entfernen, der Abonnements zugewiesen wurden, kann es bis zu 24 Stunden dauern, bis die Änderung im Verwaltungsportal sichtbar wird. 


## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Frage: Kann ich für die Zuweisung mehrere Abonnementebenen innerhalb einer Azure AD-Gruppe auswählen? 
Antwort: Nein. Jedes Mitglied in der Gruppe erhält dasselbe Abonnement. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Frage: Kann ich die Detailinformationen zu einzelnen Abonnenten bearbeiten, die in einer Azure AD-Gruppe hinzugefügt werden?  
Antwort: Nein. Wenn Sie die Informationen zu einem einzelnen Abonnenten ändern möchten, müssen Sie den Abonnenten aus der Azure AD-Sicherheitsgruppe entfernen und ihm individuell ein Abonnement zuweisen.  

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>Frage: Warum kann ich die Option zum Verwenden von Azure Active Directory-Gruppen zum Hinzufügen von Abonnenten nicht sehen?
Antwort: Die Funktion ist zurzeit nur für Organisationen mit vertrauenswürdigen Vereinbarungen verfügbar.  Wählen Sie die Schaltfläche **Details** aus, um Ihre Vereinbarungsinformationen anzuzeigen.

   > [!div class="mx-imgBorder"]
   > ![Klicken Sie auf die Schaltfläche „Details“.](_img/assign-license-bulk/bulk-add-agreement.png "Klicken Sie auf die Schaltfläche „Details“, um anzuzeigen, welche Art von Vereinbarung Sie haben.")

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Frage: Ich habe einen Benutzer zu meiner Azure AD-Sicherheitsgruppe hinzugefügt, dieser wird aber im Abonnementverwaltungsportal nicht als hinzugefügt angezeigt und hat kein Abonnement erhalten. Warum nicht?  
Antwort: Abhängig von der Azure AD-Konfiguration Ihrer Organisation kann es bis zu 24 Stunden dauern, bis der Benutzer hinzugefügt wird. Falls seit dem Hinzufügen mehr als 24 Stunden vergangen sind, [wenden Sie sich an den Support](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
- Müssen Sie nur ein oder zwei Abonnenten hinzufügen?  Informationen dazu finden Sie unter [Hinzufügen einzelner Benutzer](assign-license.md).
- Benötigen Sie Hilfe? Wenden Sie sich an den [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs).