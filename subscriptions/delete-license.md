---
title: Löschen von Visual Studio-Abonnementzuweisungen im Abonnementverwaltungsportal | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 10/26/2020
ms.topic: how-to
description: Hier erfahren Sie, wie Administratoren Abonnementzuweisungen im Verwaltungsportal für Visual Studio-Abonnements löschen können.
ms.openlocfilehash: 22a1c55bcaef436d1a29eb84b93a57f407114a1e
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904480"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Löschen von Zuweisungen in Visual Studio-Abonnements
Wenn ein Abonnent kein Visual Studio-Abonnement mehr benötigt (wenn er z.B. ein Unternehmen verlässt, ein Projekt abgeschlossen ist, oder wenn er eine neue Rolle übernimmt), können Sie das entsprechende Abonnement entfernen und es einem anderen Benutzer zuweisen. Beachten Sie, dass bei der Neuzuweisung eines Abonnements nicht alle Abonnementvorteile zurückgesetzt werden.  Der neue Benutzer kann noch nicht in Anspruch genommene Schlüssel in Anspruch nehmen und sich bereits in Anspruch genommene Schlüssel ansehen. Anspruchseinschränkungen werden **nicht** zurückgesetzt.  Für Organisationen mit Enterprise Agreements (EA) werden jegliche Vorteile zurückgesetzt, die der ursprüngliche Benutzer genutzt hat, wie z.B. Pluralsight-Schulung. 

Sehen Sie sich das folgende Video an, oder lesen Sie weiter, um zu erfahren, wie Sie Zuweisungen löschen.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Löschen einer Abonnementzuweisung
1. Klicken Sie auf den Namen des zu entfernenden Abonnenten. Um mehrere Abonnenten zum Entfernen auszuwählen, können Sie auf den Kreis links neben dem Namen des Abonnenten klicken und jeden Abonnenten einzeln auszuwählen.  Alternativ können Sie die **STRG** -Taste gedrückt halten und auf jeden Abonnenten klicken, den Sie entfernen möchten. Um einen Bereich von Abonnenten zu entfernen, klicken Sie auf den ersten, drücken die **UMSCHALTTASTE** und klicken auf den letzten.  Drücken Sie **STRG+A** , um alle Abonnenten auszuwählen und zu entfernen. In diesem Beispiel werden die drei Abonnenten Amber, Kai und Madison gelöscht. 
2. Klicken Sie auf **Löschen** , um den ausgewählten Abonnenten bzw. die ausgewählten Abonnenten zu löschen.
3. Bestätigen Sie den Löschvorgang mit **OK**.
   > [!div class="mx-imgBorder"]
   > ![Abonnenten löschen](_img/delete-license/delete-subscribers.png "Wählen Sie die Benutzer aus, die Sie löschen möchten, und klicken Sie auf „Löschen“. Sie können die STRG- und die UMSCHALT-Taste verwenden, um mehrere Abonnenten auszuwählen.")

   > [!NOTE]
   > Eine Massenlöschung unter Verwendung einer Vorlage ist nicht verfügbar. 
   >
   > Wenn Sie Abonnementzuweisungen über Azure Active Directory-Sicherheitsgruppen hinzugefügt haben, kann es bis zu 24 Stunden dauern, bis der Löschvorgang im Verwaltungsportal abgeschlossen ist.  Weitere Informationen zum Verwenden von Azure Active Directory-Gruppen für die Verwaltung von Abonnements finden Sie in [unserem Artikel](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions). 

## <a name="see-also"></a>Weitere Informationen
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
- Müssen Sie ein Abonnement ändern, ohne es zu löschen?  Erfahren Sie mehr über das [Bearbeiten von Abonnements](edit-license.md).
- Um ein bestimmtes Abonnement zu finden, informieren Sie sich unter [Suchen nach einem Abonnement](search-license.md).
- Müssen Sie eine Liste all Ihrer Abonnements erstellen?  Informationen dazu finden Sie unter [Exportieren von Abonnements](exporting-subscriptions.md).