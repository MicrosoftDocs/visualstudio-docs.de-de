---
title: Einrichten von Administratoren für Monatsabonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: how-to
description: Einrichten von Administratoren für Monatsabonnements
ms.openlocfilehash: fbb8d1f7a1519950e84c6f6fe726dd8f52ff29c5
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "91006110"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Einrichten von Administratoren für Visual Studio-Monatsabonnements

Visual Studio-Monatsabonnements werden von Administratoren verwaltet. Diese Personen können Abonnements zuweisen, Zuweisungen bearbeiten, Abonnements hinzufügen oder löschen und andere Verwaltungsaufgaben mit Abonnements ausführen.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Der Besitzer des Azure-Abonnements ist der erste Administrator

Wenn Sie Visual Studio-Monatsabonnements erwerben, werden Sie als Besitzer des für den Erwerb verwendeten Azure-Abonnements automatisch als Administrator für diese Abonnements eingerichtet.

Sie können Monatsabonnements über den [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) erwerben. Sie können sich dazu aber auch an einen Cloud Solution Provider wenden. Bei einem Kauf über den Visual Studio Marketplace wird Ihnen am Ende des Einkaufs eine Option zum Verwalten von Benutzern angeboten. Wenn Sie diese Option auswählen, gelangen Sie zum Verwaltungsportal für Visual Studio-Abonnements: [https://manage.visualstudio.com](https://manage.visualstudio.com).

Nachdem Sie die Abonnements erworben haben, können Sie das [Verwaltungsportal](https://manage.visualstudio.com) jederzeit aufrufen. Melden Sie sich einfach beim Portal an, und wählen Sie oben links das geeignete Azure-Abonnement aus.

Als Besitzer des Azure-Abonnements, mit dem die Monatsabonnements erworben wurden, können Sie auch weitere Administratoren zuweisen.

## <a name="add-administrators"></a>Hinzufügen von Administratoren

So fügen Sie Administratoren hinzu

1. Stellen Sie eine Verbindung mit dem Azure-Portal unter [portal.azure.com](https://portal.azure.com) her.
2. Melden Sie sich mit dem Konto an, das Sie verwendet haben, um die Visual Studio-Monatsabonnements zu erwerben.
3. Wählen Sie unter **Azure-Dienste** die Option **Kostenverwaltung + Abrechnung** aus.
   > [!div class="mx-imgBorder"]
   > ![Auswahl der Option „Kostenverwaltung + Abrechnung“ unter „Azure-Dienste“](_img/cloud-admin/azure-cost-billing.png "Auswählen von „Cost Management“ aus der Gruppe der Azure-Dienste")
4. Wählen Sie in der Liste **Meine Abonnements** das Azure-Abonnement aus, das Sie für den Kauf verwendet haben.
   > [!div class="mx-imgBorder"]
   > ![Auswählen des Abonnements](_img/cloud-admin/subscription-list.png "Wählen Sie das Azure-Abonnement aus, das Sie für den Kauf verwenden möchten.")
5. Klicken Sie im oberen Bereich der Liste im linken Navigationsbereich auf **Zugriffssteuerung (IAM)** .
6. Klicken Sie oben auf der Seite auf die Registerkarte **Hinzufügen** .
7. Klicken Sie auf **Rollenzuweisung hinzufügen** .
   > [!div class="mx-imgBorder"]
   > ![Auswahl der Option „Zugriffssteuerung > Hinzufügen > Rollenzuweisung hinzufügen“](_img/cloud-admin/access-control-add.png "Wählen Sie aus der Liste auf der linken Seite die Option „Zugriffssteuerung“ aus, und klicken Sie auf „Hinzufügen“.")
8. Klicken Sie oben rechts auf die Dropdownliste **Rolle** , scrollen Sie nach unten, und wählen Sie **Benutzerzugriffsadministrator** aus.
9. Scrollen Sie in der Benutzerliste zu dem Benutzer, den Sie als Administrator festlegen möchten, und wählen Sie ihn aus. 
   > [!div class="mx-imgBorder"]
   > ![Auswahl der Option „Rolle > Benutzerzugriffsadministrator“](_img/cloud-admin/add-role-user-access-admin.png "Wählen Sie „Rolle“ und „Benutzerzugriffsadministrator“ aus, und wählen Sie dann den Namen des Benutzers aus, um diesen zum Administrator zu machen.")
10. Klicken Sie auf **Speichern** .
11. Klicken Sie auf die Registerkarte **Rollenzuweisungen** , um zu überprüfen, ob der ausgewählte Benutzer nun als Benutzerzugriffsadministrator aufgeführt wird.

Der neue Administrator kann sich jetzt beim [Verwaltungsportal](https://manage.visualstudio.com) anmelden. Anschließend muss er oben links auf der Seite das Azure-Abonnement auswählen, das zum Kauf der Monatsabonnements verwendet wurde, und kann mit der Verwaltung der Abonnements beginnen.

> [!NOTE]
> Wenn Sie feststellen, dass Ihre Monatsabonnements von Benutzern bearbeitet werden können, die nicht von Ihnen als Administratoren eingerichtet wurden, sind diesen Benutzern möglicherweise Rollen im zugrunde liegenden Azure-Abonnement zugewiesen, die eine Abonnementverwaltung ermöglichen. Zu diesen Rollen gehören: Besitzer, Mitwirkender, Dienstadministrator oder Co-Admin. Weitere Informationen finden Sie unter [Hinzufügen von Rechnungs-Managern](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Weitere Informationen zu Visual Studio-Monatsabonnements finden Sie in der [Übersicht](vscloud-overview.md) unter „Erwerben von Abonnements“. Besuchen Sie den Visual Studio Marketplace unter [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription), um Visual Studio-Monatsabonnements zu erwerben.

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
In diesen Artikeln erhalten Sie weitere Informationen zum Verwalten von Visual Studio-Abonnements.
- [Zuweisen von Lizenzen im Verwaltungsportal für Visual Studio-Abonnements](assign-license.md)
- [Zuweisen von Abonnements zu mehreren Benutzern](assign-license-bulk.md)
- [Bearbeiten von Abonnements](edit-license.md)
- [Verwenden des Features „Maximum Usage“ (Maximale Auslastung) zur Übersicht der Anzahl zugewiesener Abonnements](maximum-usage.md)