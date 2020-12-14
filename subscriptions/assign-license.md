---
title: Zuweisen von Visual Studio-Abonnements zu Benutzern | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 09/21/2020
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren Abonnenten Lizenzen zuweisen können.
ms.openlocfilehash: dd80a14a3ff57100f210fd7ae1b882c0ab7a9faf
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915413"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Zuweisen von Lizenzen im Verwaltungsportal für Visual Studio-Abonnements
Als Administrator für Visual Studio-Abonnements können Sie das Verwaltungsportal verwenden, um einzelnen Benutzern und Benutzergruppen Abonnements zuzuweisen.

Für Benutzergruppen haben Sie die Wahl, wie Sie Abonnements zuweisen.  
- Sie können Abonnements entweder einzeln zuweisen, oder
- Sie laden mithilfe der Funktion [Massenhinzufügen](assign-license-bulk.md) Listen von Abonnenten und den zugehörigen Abonnementinformationen schnell und einfach hoch.
- Wenn Ihre Organisation Microsoft Azure Active Directory (Azure AD) verwendet, können Sie [Azure AD-Gruppen verwenden](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions), um Benutzergruppen Abonnements zuzuweisen.  


## <a name="add-a-single-subscriber"></a>Einzelnen Abonnenten hinzufügen
Sehen Sie sich das Video an, oder lesen Sie den Artikel, um zu erfahren, wie Sie einem neuen Benutzer ein Visual Studio-Abonnement zuweisen, damit dieser Zugriff auf die Abonnementvorteile hat.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Melden Sie sich beim [Verwaltungsportal](https://manage.visualstudio.com) an.
2. Um einem einzelnen Visual Studio-Abonnenten eine Lizenz zuzuweisen, wählen Sie im oberen Bereich der Tabelle die Option **Hinzufügen** aus und klicken auf **Einzelner Abonnent**.
   > [!div class="mx-imgBorder"]
   > ![Einzelnen Abonnenten hinzufügen](_img/assign-license-add/add-subscriber-individual.png "Wählen Sie „Hinzufügen“ und dann individuelle Abonnenten aus, denen ein Einzelabonnement zugewiesen werden soll.")
3. Geben Sie die Informationen in die Formularfelder für den neuen Abonnenten ein. Wenn Ihre Organisation Azure Active Directory verwendet, dient das Feld **Name** als Suchfunktion. Mit dieser Funktion können Sie Personen in Ihrem aktuellen Verzeichnis finden und aus den Suchergebnissen den richtigen Benutzer auswählen. Nach der Auswahl werden die E-Mail-Adressen der entsprechenden Person für die Anmeldung und die Benachrichtigung automatisch aufgefüllt.  Wenn der Abonnent nicht in Ihrer Organisation gefunden wird, wird die Benachrichtigungs-E-Mail-Adresse nicht automatisch eingefügt. Stattdessen können Sie manuell eine andere E-Mail-Adresse hinzufügen, an die abonnementbezogene E-Mails gesendet werden sollen.  Wenn Ihr E-Mail-Dienst eingehende E-Mails an die Anmelde-E-Mail-Adressen blockiert, ist es wichtig, eine andere Benachrichtigungs-E-Mail-Adresse anzugeben, damit Abonnenten und Administratoren wichtige abonnementbezogene E-Mails von Microsoft erhalten.
   > [!div class="mx-imgBorder"]
   > ![Details von Abonnenten](_img/assign-license-add/subscriber-details.png "Geben Sie den Abonnentennamen und andere Informationen ein, oder wählen Sie aus den Mandantenmitgliedern aus.")

    > [!NOTE]
    > Damit Mitglieder eines Azure Active Directory-Mandanten sichtbar sind, wenn Sie einen Abonnentennamen eingeben, muss der Administrator Mitglied des Mandanten sein. 


    Wenn Sie möchten, dass dieser Abonnent Zugriff auf Softwaredownloads hat, wenn er sich beim [Visual Studio-Abonnementsportal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmeldet, stellen Sie sicher, dass die Umschaltfläche „Downloads“ im Abschnitt **Downloadeinstellungen** aktiviert ist. Wenn Sie Downloads deaktivieren, hat der Benutzer keinen Zugriff auf Softwaredownloads.  Der Zugriff auf Product Keys wird ebenfalls deaktiviert.  Der Abonnent hat weiterhin Zugriff auf alle anderen Vorteile, die im Abonnement enthalten sind.
   > [!div class="mx-imgBorder"]
   > ![Zugriff auf Downloads](media/access-to-downloads.png "Wählen Sie „Zulassen“ aus, um dem Abonnenten Zugriff auf Softwaredownloads zu gewähren.")

    Wenn Sie Ihre eigenen Verweise zum Abonnement hinzufügen möchten, können Sie dies im Abschnitt **Verweis hinzufügen** machen.
   > [!div class="mx-imgBorder"]
   > ![Eigene Verweise zu den einzelnen Abonnements hinzufügen](media/add-subscriber-reference-notes.png "Verwenden Sie das Referenzfeld, um ggf. Notizen zu dem Abonnement aufzuzeichnen.")

    Wenn Sie die Auswahl von Optionen und die Eingabe von Daten für den Abonnenten abgeschlossen haben, wählen Sie im unteren Bereich des Flyouts **Abonnent hinzufügen** die Option **Hinzufügen** aus.
   > [!div class="mx-imgBorder"]
   > ![Schaltfläche „Hinzufügen“ auswählen](media/add-button.png "Wählen Sie „Hinzufügen“ aus, um die Informationen zu speichern und das Abonnement dem Abonnenten zuzuweisen.")

## <a name="why-use-a-different-notification-email-address"></a>Warum sollte eine andere Benachrichtigungs-E-Mail-Adresse verwendet werden?
Einige Organisationen richten ihre E-Mail-Dienste so ein, dass eingehende E-Mails aus anderen Domänen blockiert werden.  Das Blockieren eingehender E-Mails führt dazu, dass Abonnenten und Administratoren wichtige Mitteilungen nicht erhalten:
- Abonnenten erhalten keine Benachrichtigung, dass ihnen ein Abonnement zugewiesen wurde.  Dadurch können sie auch einige der enthaltenen Vorteile nicht aktivieren.  
- Abonnenten, denen Visual Studio-Abonnements mit GitHub Enterprise zugewiesen wurden, erhalten keine Einladung zum Beitritt zu Ihrer GitHub-Organisation und können die Einladung daher auch nicht annehmen. Sie **müssen die per E-Mail gesendete Einladung annehmen**, um Zugriff auf Ihre GitHub-Organisation zu erhalten. 
- Administratoren werden nicht benachrichtigt, wenn sie einer Vereinbarung hinzugefügt werden, erhalten keine monatlichen Aufstellungen für Administratoren und auch keine Benachrichtigungen über Featureänderungen, die sich auf ihre Verwaltung von Abonnements auswirken.

Mit einer Benachrichtigungs-E-Mail-Adresse können Sie Ihren Abonnenten das Erhalten wichtiger Mitteilungen zu ihren Abonnements ermöglichen, ohne die Funktionalität ihrer Anmelde-E-Mail-Adressen ändern zu müssen.  

## <a name="resend-assignment-emails"></a>Erneutes Senden von Zuweisungs-E-Mails
Nachdem Sie einen Abonnenten hinzugefügt haben, wird automatisch eine Zuweisungs-E-Mail mit weiteren Anweisungen an den neuen Abonnenten gesendet. Sie können die Zuweisungs-E-Mail jederzeit erneut senden, indem Sie den Abonnenten und dann im oberen Menü die Schaltfläche **Erneut senden** auswählen.  Um E-Mails an mehrere Benutzer erneut zu senden, halten Sie die Taste **STRG** gedrückt, während Sie die Abonnenten auswählen.  Wenn Sie die Schaltfläche **Erneut senden** auswählen, wird ein Dialogfeld angezeigt, in dem Sie bestätigen können, dass Sie die E-Mail an diese Abonnenten erneut senden möchten.  



## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Nächste Schritte
- Müssen Sie viele Benutzer hinzufügen?  Erfahren Sie, wie Sie [mehreren Abonnenten](assign-license-bulk.md) Abonnements zuweisen.
- Benötigen Sie Hilfe?  Wenden Sie sich an den [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs).