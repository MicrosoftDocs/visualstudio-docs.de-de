---
title: Anmelden bei Visual Studio-Abonnements mit einem GitHub-Konto | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 12/02/2020
ms.topic: conceptual
description: Hier erfahren Sie, wie Sie sich mit einem GitHub-Konto bei Ihrem/Ihren Visual Studio-Abonnement(s) anmelden.
ms.openlocfilehash: 52f67afdf8a4056063cdefef618be5b895dbb960
ms.sourcegitcommit: 29099741fcf94a5aef2655ee16605728b8b9a0ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96537993"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Anmelden bei Visual Studio-Abonnement(s) mit einem GitHub-Konto 

Die Schritte zum Anmelden bei Ihrem Visual Studio-Abonnement richten sich nach der Art des Kontos, das Sie verwenden. Beispielsweise können Sie ein Microsoft-Konto (MSA) oder eine von Ihrem Arbeitgeber oder Ihrer Schule bereitgestellte E-Mail-Adresse verwenden. Seit Januar 2019 können Sie sich auch über Ihr GitHub-Konto bei einigen Abonnements anmelden. 

In diesem Artikel werden die Schritte zum Anmelden mit Ihrem GitHub-Konto beschrieben.

## <a name="signing-in-with-your-github-account"></a>Anmelden mit Ihrem GitHub-Konto

Mit der GitHub-Identitätsunterstützung für GitHub können Sie Ihr vorhandenes GitHub-Konto zum Anmelden bei einem neuen oder vorhandenen Microsoft-Konto verwenden, in dem Ihr GitHub-Konto mit Ihrem Microsoft-Konto verbinden. 

Wenn Sie sich bei GitHub anmelden, überprüft Microsoft, ob E-Mail-Adressen, die mit Ihrem GitHub-Konto verknüpft sind, auch einem vorhandenen privaten oder geschäftlichen Microsoft-Konto zugeordnet sind. Wenn die Adresse mit Ihrem Unternehmenskonto übereinstimmt, werden Sie zur Anmeldung bei diesem Konto aufgefordert. Wenn die Adresse mit einem privaten Konto übereinstimmt, fügen wir diesem privaten Konto Ihr GitHub-Konto als Anmeldemethode hinzu.

Wenn Sie Ihre Anmeldedaten für Ihre GitHub- und Microsoft-Konten verbinden, können Sie diese einmalige Anmeldung überall verwenden, wo private Microsoft-Konten verwendet werden können, z. B. bei Azure Websites, Office-Apps und Xbox. Sie können diese Konten auch für Azure Active Directory-Gastanmeldungen als Microsoft-Konto verwenden, sofern die Einladung auch an diese E-Mail-Adresse gesendet wurde.

> [!NOTE]
> Durch das Verknüpfen einer GitHub-Identität mit einem Microsoft-Konto erhält Microsoft keinen Zugriff auf Codes. Wenn Apps wie Azure DevOps und Visual Studio Zugriff auf Ihre Coderepositorys benötigen, werden Sie dazu aufgefordert, diesen Zugriff zu gewähren. 

### <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
Nachfolgend finden Sie häufig gestellte Fragen zur Verwendung von GitHub-Anmeldeinformationen für die Anmeldung bei Visual Studio-Abonnements.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>Frage: Ich habe mein GitHub-Kennwort vergessen.  Wie kann ich jetzt auf mein Konto zugreifen?
Antwort:  Sie können Ihr GitHub-Konto wiederherstellen, indem Sie Ihr [Kennwort zurücksetzen](https://github.com/password_reset). Sie können Ihr mit GitHub verknüpftes Microsoft-Konto auch wiederherstellen, indem Sie die E-Mail-Adresse GitHub-Kontos unter [Konto wiederherstellen](https://account.live.com/password/reset) eingeben.

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>Frage: Ich habe mein GitHub-Konto gelöscht.  Wie kann ich jetzt auf mein Microsoft-Konto (MSA) zugreifen?
Antwort: Wenn Sie nicht über weitere Anmeldeinformationen für Ihr MSA (z. B. ein Kennwort, eine Authentifikator-App oder einen Sicherheitsschlüssel) verfügen, können Sie Ihr Microsoft-Konto über die damit verbundene E-Mail-Adresse wiederherstellen. Informationen dazu finden Sie unter [Konto wiederherstellen](https://account.live.com/password/reset). Sie müssen Ihrem Konto ein Kennwort hinzufügen, mit dem Sie sich später anmelden möchten. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>Frage: Auf der Anmeldeseite wird keine Option für die Anmeldung mit GitHub angezeigt.  Wie kann ich meine GitHub-Anmeldeinformationen für die Anmeldung verwenden?
Antwort:  Geben Sie die E-Mail-Adresse für Ihr GitHub Konto ein, die Sie beim Erstellen Ihres mit GitHub-verknüpften Microsoft-Kontos ausgewählt haben. Wir leiten Sie zur Anmeldung bei GitHub weiter. Wenn auf der Anmeldeseite ein Link mit Anmeldeoptionen angezeigt wird, wählen Sie die Schaltfläche **Mit GitHub anmelden**, die angezeigt wird, nachdem Sie auf den Link geklickt haben. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>Frage: Ich kann mich mit GitHub bei einigen meiner Apps und Produkte nicht anmelden.  Warum?
Antwort:  Nicht alle Microsoft-Produkte können über ihre Anmeldeseite auf GitHub.com zugreifen, z. B. Xbox-Konsolen. Wenn Sie stattdessen die E-Mail-Adresse in Ihrem verknüpften GitHub-Konto eingeben, senden wir einen Code an diese Adresse, damit wir Ihre Identität überprüfen können. Sie melden sich immer noch mit dem gleichen Konto an, nur über eine andere Methode. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>Frage:  Ich habe ein Kennwort für das Microsoft-Konto hinzugefügt, das ich mit meinem GitHub-Konto verbunden habe.  Kann das Probleme verursachen?
Antwort:  Nein. Dadurch ändern Sie nicht Ihr GitHub-Kennwort. Sie erhalten nur eine weitere Möglichkeit zur Anmeldung bei Ihrem Microsoft-Konto. Bei jeder Anmeldung mit Ihrer E-Mail-Adresse können Sie wählen, ob Sie sich mit dem Kennwort für Ihr Microsoft-Konto anmelden oder die Anmeldung über GitHub durchführen möchten. Wenn Sie ein Kennwort hinzufügen möchten, müssen Sie sicherstellen, dass sich das Kennwort von den Kennwort für Ihr GitHub-Konto unterscheidet.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>Frage: Ich möchte die Authenticator-App für das Konto hinzufügen, die ich mit GitHub erstellt habe.  Ist das möglich?
Antwort:  Kein Problem. Sie müssen lediglich die App herunterladen und sich mit Ihrer E-Mail-Adresse anmelden. Wenn Sie sich mit Ihrer E-Mail-Adresse anmelden, können Sie zwischen der Anmeldung über die [Authenticator-App](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) oder GitHub wählen.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>Frage: Ich habe die zweistufige Authentifizierung für meine GitHub- und -Microsoft-Konten (MSA) aktiviert. Wenn ich mich bei meinem MSA anmelde, muss ich trotzdem doppelt authentifizieren.  Warum?
Antwort: Aufgrund von Sicherheitsbeschränkungen zählt Microsoft Anmeldevorgänge mit GitHub als einstufige Überprüfung, auch wenn Sie dort die zweistufige Überprüfung aktiviert haben. Aus diesem Grund müssen Sie sich erneut für Ihr Microsoft-Konto authentifizieren. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>Frage:  Woran erkenne ich, dass meine Microsoft- und GitHub-Konten verknüpft sind?
Antwort:  Wenn Sie sich mit Ihrem Kontoalias (E-Mail-Adresse, Telefonnummer, Skype-Name) anmelden, zeigen wir Ihnen alle Anmeldemethoden für Ihr Konto an. Wenn GitHub dort nicht angezeigt wird, haben Sie diese Option noch nicht eingerichtet.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>Frage:  Wie kann ich die Verknüpfung meiner Microsoft- und GitHub-Konten aufheben? 
Antwort:  Klicken Sie auf der Registerkarte [Sicherheit](https://account.microsoft.com/security) auf account.microsoft.com auf die Option für **weitere Sicherheitsoptionen** um die Verknüpfung Ihres GitHub-Kontos aufzuheben. Wenn Sie die Verknüpfung Ihres GitHub-Konto als Anmeldemethode aufheben, entfernen Sie den Zugriff auf alle GitHub-Repositorys in Visual Studio. Andere Microsoft-Produkte haben den Zugriff auf Ihr GitHub-Konto möglicherweise separat angefordert. In diesem Fall wird der Zugriff möglicherweise nicht in allen Produkten entfernt. Widerrufen Sie in den [Anwendungsberechtigungen](https://github.com/settings/applications) in Ihrem GitHub-Profil die Zustimmung für die Apps auf der Seite.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>Frage:  Ich möchte mich über mein GitHub-Konto anmelden, aber ich werde aufgefordert, mich über eine bereits vorhandene Microsoft-Identität anzumelden.  Woran liegt das?
Antwort:  Wenn Sie eine Azure Active Directory E-Mail-Adresse in Ihrem GitHub-Konto gespeichert haben, verfügen Sie bereits über eine Microsoft-Identität, die auf Azure zugreifen und CI-Pipelines mit Ihrem GitHub-Code ausführen kann. Mit diesem Konto stellen Sie sicher, dass Ihre Azure-Ressourcen und Buildpipelines innerhalb Ihrer Organisationsgrenzen bleiben. Verwenden Sie für private Aufgaben eine persönliche E-Mail-Adresse in Ihrem GitHub-Konto, damit Sie immer darauf zugreifen können. Melden Sie sich erneut an, und wählen Sie **Andere E-Mail-Adresse verwenden**, wenn Sie zur Anmeldung mit Ihrem Geschäfts-, Schul- oder Unikonto aufgefordert werden. Dann können Sie ein neues Microsoft-Konto mit dieser privaten E-Mail-Adresse erstellen.

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
Nach erfolgreicher Anmeldung beim Abonnementportal empfiehlt es sich, über https://my.visualstudio.com/benefits die Seite „Vorteile“ zu besuchen und die Tools, Dienste und Angebote zu entdecken, die Ihnen zur Verfügung stehen.