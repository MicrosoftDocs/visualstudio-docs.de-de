---
title: Persönliche E-Mail-Adressen für Visual Studio-Abonnements in VLSC
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 10/28/2020
ms.topic: conceptual
description: Visual Studio-Abonnements – Warum sehe ich Hotmail- oder Gmail-Adressen für meine Abonnenten?
ms.openlocfilehash: fda7dab50c2151049e0feffa50609bf4c38e38cc
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2020
ms.locfileid: "92904261"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio-Abonnements: Warum werden persönliche Konten für meine Abonnenten angezeigt?
Nachdem Unternehmen vom Volume Licensing Service Center (VLSC) zum neuen [Abonnementverwaltungsportal](https://manage.visualstudio.com) von Visual Studio migriert haben, stellen Administratoren möglicherweise fest, dass als „Anmelde-E-Mail-Adresse“ für manche Abonnenten eine persönliche E-Mail-Adresse wie Hotmail oder Yahoo angezeigt wird.  

## <a name="cause"></a>Ursache
Grund für dieses Szenario sind Anmeldeprozesse, die mit dem älteren MSDN-Abonnentenprozess verknüpft waren. Benutzer wurden ohne Änderungen aus dem Volume Licensing-Servicecenter (VLSC) zum Verwaltungsportal für Visual Studio-Abonnements migriert. Den Administratoren war möglicherweise nicht bewusst, dass Benutzer persönliche Konten verwendet hatten, um auf ihre Abonnementvorteile zuzugreifen. Vor den Visual Studio-Abonnentenmigrationen, die 2016 abgeschlossen wurden, waren zur erfolgreichen Verwendung eines Visual Studio-Abonnements zwei Aktionen erforderlich:
1. Der Administrator musste das Abonnement einem einzelnen Abonnenten unter Verwendung seiner Geschäfts-, Schul- oder Uni-E-Mail-Adresse „zuweisen“.
2. Der Abonnent „aktivierte“ das Abonnement.

Während der Aktivierung des Abonnenten galt: Ein Microsoft-Konto (MSA) war zum Anmelden erforderlich. Wenn der Abonnent nicht versuchte, sein Geschäfts- oder Schulkonto (z.B. tasha@contoso.com) zu einem MSA zu machen, konnte er ein neues MSA erstellen oder ein vorhandenes nutzen. Dies führte dazu, dass seine „Anmelde-E-Mail-Adresse“ sich von seiner „‘Zugewiesen an‘-E-Mail-Adresse" unterschied.

> [!NOTE]
> Der moderne Abonnentenprozess in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) unterstützt sowohl Geschäfts-, Uni- und Schul- als auch Microsoft-Kontoidentitätstypen (MSA).

## <a name="solution"></a>Lösung
Sie können das Problem beheben, indem Sie auf die Schaltfläche **Connect Emails** (E-Mail-Adressen verknüpfen) klicken. Das System versucht dann, die Konten mit MSAs den vorhandenen Benutzern in der Azure Active Directory-Instanz Ihrer Organisation nach Vor- und Nachname zuzuordnen. Wenn dabei ein Fehler auftritt, können Sie Übereinstimmungen entfernen, indem Sie rechts davon auf das **X** klicken.  

Sehen Sie sich dieses Video an, oder lesen Sie weiter, um mehr über die Fehlerbehebung zu erfahren. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![Schaltfläche „Connect Emails“ (E-Mail-Adressen verknüpfen)](_img/connect-emails/connect-emails-button.png "Klicken Sie auf „Connect Emails“ (E-Mail-Adressen verbinden), um Ihre Benutzer mit Microsoft-Konten mit Ihrer Azure Active Directory-Instanz abzugleichen.")

Sie können auch die Option **Verzeichnis durchsuchen** nutzen, um Fehler zu beheben oder fehlende Informationen aus Azure AD einzufügen. Wenn die Übereinstimmungen korrekt aussehen, können Sie auf die Schaltfläche **Current identity** (Aktuelle Identität) klicken, um alle übereinstimmenden Einträge auf einmal anstatt einzeln auszuwählen.  

> [!div class="mx-imgBorder"]
> ![Flyout für „Connect Emails“ (E-Mail-Adressen verknüpfen)](_img/connect-emails/connect-emails-flyout.png "Wählen Sie aus, welche Abonnenten ihren Azure AD-Identitäten zugeordnet werden sollen, und klicken Sie auf „Weiter“.")

Klicken Sie auf **Weiter**. Hierdurch werden Sie zu einer Liste der anstehenden Änderungen weitergeleitet. Klicken Sie auf **Speichern** , wenn Sie mit diesen einverstanden sind. Die Änderungen werden anschließend umgesetzt. Ihre Abonnenten werden bei der nächsten Anmeldung bei ihrem Abonnement über die Änderung benachrichtigt.  Beachten Sie, dass nur die zwei Abonnenten, die in der Azure Active Directory-Instanz als übereinstimmend ermittelt wurden, in dieser Liste angezeigt werden.  Da Frederick in diesem Beispiel über keine Adresse in Azure AD verfügt, konnte sein Microsoft-Konto keinem Geschäftskonto zugeordnet werden. 

> [!div class="mx-imgBorder"]
> ![Bestätigung für „Connect Emails“ (E-Mail-Adressen verknüpfen)](_img/connect-emails/connect-emails-confirm.png "Klicken Sie auf „Weiter“, um die vorgeschlagenen Änderungen zu implementieren, und klicken Sie auf „Speichern“.") 

> [!NOTE]
> Wenn Sie die E-Mail-Adresse für die Anmeldung bearbeiten, wird nur die E-Mail-Adresse geändert, die der Abonnent für die Anmeldung beim Abonnement unter https://my.visualstudio.com verwendet. Wenn der Abonnent bereits Vorteile wie Azure oder Pluralsight mithilfe der anderen E-Mail-Adresse aktiviert hat, muss er diese E-Mail-Adresse weiterhin verwenden, um darauf zuzugreifen. Wenn Benutzer auf neue Vorteile zugreifen, sollten sie die neue E-Mail-Adresse verwenden. 

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

##  <a name="next-steps"></a>Nächste Schritte
- Wenn Sie die E-Mail-Adressen der Abonnenten aktualisiert haben, sollten Sie ihnen mitteilen, dass ihre Anmeldeinformationen geändert wurden.  Sie erhalten auch eine E-Mail mit den aktualisierten Informationen.
- Es kann hilfreich sein, die [Liste der Abonnenten in Ihrer Organisation zu filtern](search-license.md), um nach Anmelde-E-Mail-Adressen zu suchen, die möglicherweise geändert werden müssen.