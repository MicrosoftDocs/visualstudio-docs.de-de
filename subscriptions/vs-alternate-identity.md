---
title: Identitäten für Visual Studio-Abonnenten
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 02/19/2021
ms.topic: conceptual
description: Hinzufügen einer alternativen Identität zu Ihrem Visual Studio-Abonnement, die für Azure DevOps und Azure verwendet werden kann
ms.openlocfilehash: 4d00e6808a71522f95d8580056556f5a502ecbde
ms.sourcegitcommit: 35fa920126b34c8d3839da53e3a4c2c6f509968f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2021
ms.locfileid: "102473308"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identitäten für Visual Studio-Abonnenten
Wenn Sie ein Visual Studio-Abonnement aktivieren, wird die Identität (oder das Konto) damit verknüpft, die Sie während der Aktivierung des Abonnements verwendet haben. Dadurch können Sie im [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs), in Azure DevOps und in Azure erkannt werden.

In Azure DevOps wird der Status Ihres Visual Studio-Abonnements bei jeder Anmeldung überprüft. Zudem werden Features automatisch in jeder Organisation zur Verfügung gestellt, in der Sie Mitglied sind.
Da diese Features in den Abonnementvorteilen enthalten sind, ist es kostenlos, Sie einer beliebigen Azure DevOps-Organisation als Mitglied hinzuzufügen, wenn Sie eine Identität verwenden, die mit Ihrem Visual Studio-Abonnement verknüpft ist.

In Azure wird der Status Ihres Visual Studio-Abonnements überprüft, wenn Sie Ihr [monatliches Einzelguthaben für Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) aktivieren, bei dem es sich um einen Vorteil für Abonnenten handelt.

Innerhalb des [Visual Studio-Portals für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) können Sie zusätzlich zu der Identität, die Sie für die Aktivierung verwendet haben, eine **alternative Identität** hinzufügen. Es ist möglich, eine alternative Identität hinzuzufügen, wenn Sie ein Microsoft-Konto verwendet haben, um Ihr Abonnement zu aktivieren. So können Sie auch ein Geschäfts-, Schul- oder Unikonto (das Sie zum Anmelden in Visual Studio, Microsoft 365 oder bei Ihrem Geschäfts-, Schul- oder Uninetzwerk verwenden) hinzufügen und auf Azure DevOps über Ihr persönliches sowie über Ihr Geschäfts-, Schul- oder Unikonto zugreifen.

## <a name="add-an-alternate-account-to-your-subscription"></a>Hinzufügen eines alternativen Kontos zu Ihrem Abonnement
Wenn Sie Ihrem Visual Studio-Abonnement ein alternatives Konto hinzufügen, haben Sie Zugriff auf bestimmte Abonnementvorteile wie Azure DevOps und Azure oder können sich bei der Visual Studio-IDE mit einer anderen Identität als die dem Abonnement zugewiesene anmelden. In der Vergangenheit war diese Funktion nur verfügbar, wenn Ihr Visual Studio-Konto einem Microsoft-Konto zugewiesen war. Jetzt wurde diese Funktion auf Geschäfts-, Schul- oder Unikonten in Azure Active Directory (Azure AD) erweitert.

> [!NOTE]
> Mit einer alternativen ID können Sie diese zweite ID nur verwenden, um Azure-Gutschriften und Azure DevOps zu aktivieren und sich bei der Visual Studio-IDE anzumelden.  Sie können eine alternative ID nicht verwenden, um sich unter <https://my.visualstudio.com> beim Abonnementportal anzumelden.  Sie müssen weiterhin die ID verwenden, der das Abonnement zugewiesen ist, um sich beim Portal anzumelden. 

Sie können für alle Abonnements ein Geschäfts-, Schul- oder Unikonto hinzufügen, damit Sie mit dem Konto alle Vorteile nutzen können, für die eine Anmeldung erforderlich ist (Visual Studio-IDE, Azure DevOps und Azure).

### <a name="add-the-alternate-account"></a>Hinzufügen des alternativen Kontos
1. Melden Sie sich mit Ihrem Microsoft-Konto (https://my.visualstudio.com) beim Abonnentenportal für Visual Studio an.
2. Wählen Sie die Registerkarte **Abonnements** aus.
3. Klicken Sie auf **Add alternate account** (Alternatives Konto hinzufügen).
4. Fügen Sie Ihr Geschäfts-, Schul- oder Unikonto hinzu.
    > [!div class="mx-imgBorder"]
    > ![Hinzufügen eines Geschäfts-, Schul- oder Unikontos](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png "Hinzufügen eines Geschäfts-, Schul- oder Unikontos als alternatives Konto in Ihrem Abonnement.")

5. Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto bei Azure DevOps an (https://{ihrkonto}.visualstudio.com).

Ihr alternatives Konto wird dem Visual Studio-Abonnement hinzugefügt, sodass beide Identitäten die Abonnementvorteile nutzen können, für die eine Anmeldung mit dem alternativen Konto erforderlich ist (IDE, Azure DevOps und Azure).

## <a name="faq"></a>FAQ

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Frage:  Warum erkennt Azure DevOps mich nicht als Visual Studio-Abonnent?

Antwort: Azure DevOps sollte Ihr Abonnement automatisch erkennen, wenn Sie sich mit Ihrer primären oder alternativen Identität anmelden. Wenn dies nicht der Fall ist, können Sie Folgendes ausprobieren:

* Überprüfen Sie, ob Sie über ein aktives Visual Studio-Abonnement verfügen, das [Azure DevOps](vs-azure-devops.md#eligibility) als Vorteil enthält.

* Vergewissern Sie sich, dass Sie ein Konto bzw. eine Identität verwenden, bei dem bzw. der es sich um die primäre oder alternative Identität für Ihr Visual Studio-Abonnement handelt.

* Besuchen Sie das [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) mindestens einmal, bevor Sie sich bei Azure DevOps anmelden.

Wenn Azure DevOps Ihr Abonnement weiterhin nicht erkennt, wenden Sie sich an den [Azure DevOps-Support](https://azure.microsoft.com/support/devops/).

## <a name="resources"></a>Ressourcen
[Support für Visual Studio-Abonnements](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte 
Weitere Informationen über die Verwendung von Azure, Azure DevOps oder der Visual Studio-IDE finden Sie unter den folgenden Ressourcen:
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)