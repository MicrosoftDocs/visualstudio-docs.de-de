---
title: Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 10/22/2020
ms.topic: conceptual
description: Mögliche Fehler beim Anmelden, wenn Aliase oder Anzeigenamen verwendet werden.
ms.openlocfilehash: 4d9b3194cf7636106740e35b230cc02aaab7eded
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467608"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen
Abhängig vom für die Anmeldung verwendeten Kontotyp werden verfügbare Abonnements möglicherweise nicht ordnungsgemäß angezeigt, wenn Benutzer sich bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmelden. Eine mögliche Ursache ist die Verwendung von „Aliasen“ oder „Anzeigenamen“ anstelle der Anmeldeidentität, der das Abonnement zugewiesen ist. Dieser Vorgang wird als „Aliasing“ bezeichnet.

## <a name="what-is-aliasing"></a>Was ist Aliasing?
Der Begriff „Aliasing“ bezieht sich auf Benutzer, die über verschiedene Identitäten für die Anmeldung bei Windows (oder Ihrem Active Directory) und den Zugriff auf E-Mails verfügen.

Aliasing kann auftreten, wenn ein Unternehmen über einen Microsoft Online-Dienst für die Verzeichnisanmeldung verfügt (z. B. JohnD@contoso.com), aber Benutzer auf ihre E-Mail-Konten über Aliase oder Anzeigenamen (z. B. John.Doe@contoso.com) zugreifen. Sorgen Sie dafür, dass sich Ihre Benutzer die Anmelde-E-Mail-Adressen verwenden, um auf ihre Abonnements zuzugreifen. Diese Adressen sind im Verwaltungsportal unter https://manage.visualstudio.com aufgeführt. 

## <a name="what-are-the-potential-issues"></a>Welche möglichen Probleme können auftreten?

Je nach Kontotyp des Abonnenten kann eines von zwei Problemen auftreten. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Fehler bei fehlender Übereinstimmung des UPN von Geschäfts-, Schul- oder Unikonto 
Wenn in einem Unternehmen Active Directory eingerichtet ist und der Benutzerprinzipalname (UPN) nicht mit der primären SMTP-Adresse identisch ist, kann es zu einem UPN-Konflikt kommen. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>So können Sie feststellen, ob für Ihre Anmeldeadresse ein UPN-Konflikt vorliegt 

1. Melden Sie sich unter Verwendung der Anmelde-E-Mail-Adresse bei https://my.visualstudio.com/subscriptions an, die in der E-Mail mit Ihrer Abonnementzuweisung genannt ist.

2. Klicken Sie in der oberen rechten Ecke der Seite auf Ihren Namen.  Hiermit wird Ihr Profil geöffnet.  Stellen Sie sicher, dass die Anmelde-E-Mail-Adresse in Ihrem Profil mit der Adresse übereinstimmt, die Sie zur Anmeldung verwendet haben.  Andernfalls liegt ein UPN-Konflikt vor, und Sie sind nicht in der Lage, Ihr Abonnement anzuzeigen. 

> [!div class="mx-imgBorder"]
> ![Anmelde-E-Mail-Adresse](_img//aliasing/sign-in-email.png "Stellen Sie sicher, dass die E-Mail-Adresse in Ihrem Profil mit jener übereinstimmt, die Sie zum Anmelden verwenden.")

#### <a name="how-to-fix-a-upn-mismatch"></a>Beheben eines UPN-Konflikts

1. Rufen Sie das Visual Studio-Verwaltungsportal ([https://manage.visualstudio.com](https://manage.visualstudio.com)) auf. 

2. Suchen Sie nach dem Abonnenten, für den der UPN-Konflikt vorliegt. (Das [Filter](search-license.md)-Feature kann die Suche nach einem Abonnenten vereinfachen.)

3. Ändern Sie die Anmelde-E-Mail-Adresse in den UPN des Abonnenten. 

0. Speichern der Änderungen 

0. Informieren Sie den Abonnenten, sich vom Abonnentenportal abzumelden und sich unter Verwendung des Benutzerprinzipalnamens erneut anzumelden. 

### <a name="personal-account-aliasing-issue"></a>Aliasingprobleme bei persönlichen Konten

Bei persönlichen Abonnementkonten können ebenfalls Probleme auftreten, wenn die zur Anmeldung beim Visual Studio-Abonnementportal verwendete E-Mail-Adresse nicht mit der E-Mail-Adresse übereinstimmt, die mit dem Abonnement verknüpft ist. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>So stellen Sie fest, ob Ihr persönliches Abonnementkonto von einem Aliasingproblem betroffen ist

1. Melden Sie sich bei [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions) an.

0. Stellen Sie sicher, dass die Anmelde-E-Mail-Adresse oben rechts auf der Seite mit der Adresse übereinstimmt, die Sie zur Anmeldung verwendet haben.  Wenn die E-Mail-Adresse, mit der Sie angemeldet sind, nicht identisch mit der E-Mail-Adresse ist, mit der auf die Website zugegriffen wurde, kommt es zu einem Konflikt zwischen Ihrem Konto und dem Alias.

#### <a name="how-to-fix-an-alias-issue"></a>Beheben eines Aliasproblems

Die Visual Studio-Plattform priorisiert den primären Alias, um Abonnementdetails anzuzeigen. 

1. Navigieren Sie zu **Anmeldung bei Microsoft verwalten** . Melden Sie sich in Ihrem Microsoft-Konto an, wenn Sie dazu aufgefordert werden. 

2. Klicken Sie unter Kontoaliase neben der E-Mail-Adresse, die für die Zuweisung des Abonnements verwendet wurde, auf die Option **Als primär festlegen** . 

> [!div class="mx-imgBorder"]
> ![Festlegen der primären E-Mail-Adresse](_img//aliasing/account-aliases.png "Verwenden Sie den Link „Als primär festlegen“, um den primären Alias für Ihre Abonnements auszuwählen.")

3. Melden Sie sich vom Visual Studio-Abonnementportal ab (https://my.visualstudio.com). 

4. Melden Sie sich erneut an. Verwenden Sie hierbei das Konto, das für die Zuweisung des Abonnements verwendet wurde und nun als primärer Alias konfiguriert werden soll. 

## <a name="preventing-aliasing-issues"></a>Verhindern von Aliasingproblemen

Als Administrator haben Sie zwei Möglichkeiten, um sicherzustellen, dass die Anmeldung Ihrer Abonnenten bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) problemlos möglich ist.
- Die erste Option (empfohlen) ist die Verwendung des Verzeichniskontos zur Anmeldung beim Visual Studio-Abonnementportal unter https://my.visualstudio.com.  
- Die zweite Option (weniger sicher) besteht darin, Abonnenten die Anmeldung mit einer anderen E-Mail-Adresse als ihrer Verzeichnis-E-Mailadresse zu gestatten.

Beide Option werden im Administratorportal konfiguriert, indem die folgenden Schritte ausgeführt werden:  
1. Melden Sie sich bei [https://manage.visualstudio.com](https://manage.visualstudio.com) an. 

0. Wenn Sie Änderungen für einen einzelnen Benutzer vornehmen möchten, wählen Sie diesen Benutzer in der Tabelle aus, und klicken Sie für das Bearbeiten mit der rechten Maustaste auf ihn. Dadurch wird ein Panel geöffnet, in dem Sie die E-Mail-Adresse für die Anmeldung ändern können. Nehmen Sie im Feld für die E-Mail-Adresse für die Anmeldung die erforderlichen Änderungen vor. Klicken Sie auf „Speichern“, und die Änderungen werden umgesetzt.  

0. Wenn Sie Änderungen an mehreren Benutzern gleichzeitig vornehmen möchten, können Sie das Feature für die Massenbearbeitung verwenden. Weitere Informationen erhalten Sie im Artikel [Bearbeiten mehrerer Abonnenten mithilfe der Massenbearbeitung](./edit-license.md#edit-multiple-subscribers-using-bulk-edit).

> [!NOTE]
> Sowohl bei Einzel- als auch bei Massenänderungen werden die Abonnenten per E-Mail darüber informiert, dass sich ihre Anmelde-E-Mail-Adresse geändert hat und sie sich mit der aktualisierten E-Mail-Adresse anmelden müssen. Beachten Sie außerdem Folgendes: Hat der Abonnent zuvor Vorteile mit der anderen Anmeldeadresse aktiviert, muss er zum Zugriff auf diese weiterhin die andere Anmeldeadresse verwenden.  

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