---
title: Festlegen von Vertragseinstellungen im Verwaltungsportal
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 10/22/2020
ms.topic: conceptual
description: Erfahren Sie, wie Sie die Einstellungen u. a. für Sprachen, Kontakte und die Abonnementebene im Verwaltungsportal festlegen.
ms.openlocfilehash: e044db92a318114cd2f159b859843db354fac6c7
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467439"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Festlegen der Vertragseinstellungen im Verwaltungsportal
Superadministratoren können bestimmte Einstellungen im Verwaltungsportal festlegen, die global auf alle Verträge angewendet werden.  Diese Einstellungen füllen automatisch die Abonnementdaten für Ihre Administratoren aus, wenn diese Abonnenten hinzufügen, und können ausschließlich von Superadministratoren global geändert werden.  

## <a name="access-preferences"></a>Zugriffseinstellungen
Wenn Sie sich die Einstellungen anzeigen lassen oder diese ändern möchten, müssen Sie beim [Verwaltungsportal](https://manage.visualstudio.com) mit einer ID angemeldet sein, der Superadministratorberechtigungen entsprechend dem Vertrag zugewiesen sind.  

So legen Sie Ihre Einstellungen fest:
1. Melden Sie sich beim Verwaltungsportal mit einer ID an, der Superadministratorberechtigungen zugewiesen sind.
2. Klicken Sie im linken Bereich auf das Einstellungssymbol.
   > [!div class="mx-imgBorder"]
   > ![Schaltfläche für Administratoreinstellungen](_img/admin-prefs/admin-prefs-button.png "Klicken Sie auf „Administratoren verwalten“ und dann auf „Agreement Preferences“ (Vereinbarungseinstellungen), um die Einstellungen anzuzeigen.")

3. Klicken Sie auf **Agreement Preferences** (Vertragseinstellungen).
Auf der linken Seite wird ein Bereich angezeigt, in dem die verfügbaren Einstellungen aufgeführt sind. 

   > [!div class="mx-imgBorder"]
   > ![Flyoutdialogfeld für Administratoreinstellungen](_img/admin-prefs/admin-prefs-flyout.png "Legen Sie die gewünschten Einstellungen fest, und klicken Sie dann auf „Speichern“.")

## <a name="set-your-preferences"></a>Festlegen der Einstellungen
Im Folgenden werden die jeweiligen Einstellungen und ihre Auswirkungen beschrieben. 

### <a name="agreement"></a>„Agreement“ (Vertrag)
Wenn Sie über mehrere Verträge verfügen, in denen Sie als Superadministrator festgelegt sind, können Sie den gewünschten Vertrag über die Dropdownliste rechts neben dem erweiterten Einstellungsbereich auswählen.  Die von Ihnen festgelegten Einstellungen gelten nur für diesen Vertrag.  Einige dieser Einstellungen können in manchen Fällen von einzelnen Administratoren bei der Zuweisung von Abonnements überschrieben werden. 

Wenn nur ein Vertrag mit der E-Mail-Adresse verknüpft ist, mit der Sie sich angemeldet haben, wird dieser Vertrag rechts neben dem erweiterten Einstellungsbereich angezeigt, und die Dropdownliste wird deaktiviert. 

### <a name="contact-email-address"></a>„Contact email address“ (E-Mail-Adresse des Kontakts)
Mit dieser Einstellung und der Schaltfläche **Contact my Admin** (Administrator kontaktieren) auf der [Abonnementseite](https://my.visualstudio.com/subscriptions) im Verwaltungsportal können Abonnenten einen Administrator kontaktieren.  Wenn diese Einstellung nicht angegeben wird, werden Abonnentennachrichten an alle Administratoren und Superadministratoren weitergeleitet, die im Vertrag festgelegt sind.  Es wird empfohlen, einen E-Mail-Alias für eine Gruppe oder eine Sicherheitsgruppe zu verwenden, damit Nachrichten nur an die E-Mail-Adresse der gewünschten Zielgruppe weitergeleitet werden. Bei Bedarf können Sie auch die E-Mail-Adresse einer Einzelperson eingeben.

> [!NOTE]
> Die E-Mail-Adresse, die Sie mit dieser Einstellung festlegen, wird den Abonnenten NICHT mitgeteilt.  Wenn ein Abonnent mit dem Feature **Contact my Admin** (Administrator kontaktieren) eine Anfrage im Abonnentenportal stellt, wird die Nachricht an den Alias weitergeleitet. Dieser ist für den Abonnenten nicht sichtbar. 

### <a name="default-subscription-level"></a>„Default subscription level“ (Standardabonnementebene)
Mit dieser Einstellung können Sie festlegen, welche Abonnementebenen, die in Ihrem Vertrag festgelegt sind, standardmäßig ausgewählt werden, wenn ein Abonnement einem Benutzer zugewiesen wird.  Administratoren können diese Einstellung anpassen und dabei jede Abonnementebene Ihres Vertrags auswählen. Dadurch wird verhindert, dass Sie die am häufigsten verwendete Einstellung mehrfach angeben müssen. 

### <a name="default-communication-preferences"></a>„Default communication preferences“ (Standardeinstellungen für Kommunikation)
Wenn Sie eine Standardsprache und ein Standardgebietsschema für die Kommunikation festlegen, können Sie das Zuweisen von Abonnements optimieren.  Wenn sich beispielsweise Ihr Entwicklungsteam in einem anderen Land als Ihr Administratorteam befindet, können Sie die Einstellungen festlegen, die für den Standort der Abonnenten am geeignetsten sind. Diese Einstellungen können weiterhin von allen Administratoren für einzelne Abonnenten geändert werden. 

### <a name="default-external-subscribers-setting"></a>„Default external subscribers setting“ (Standardeinstellung für externe Abonnenten)
Mit dieser Einstellung legen Sie fest, ob Administratoren Abonnenten hinzufügen können, die sich außerhalb des Mandanten oder des Verzeichnisses Ihrer Organisation befinden.  Wenn Sie diese Einstellung deaktivieren, sind keine externen Abonnenten zulässig.  Wenn Sie die Einstellung aktivieren und ein Administrator versucht, einen externen Abonnenten hinzuzufügen, wird dieser Administrator aufgefordert, die Aktion zu bestätigen. Anschließend kann er das Abonnent zuweisen. Administratoren können diese Einstellung nicht überschreiben. 

### <a name="default-downloads-setting"></a>„Default downloads setting“ (Standardeinstellung für Downloads)
Wenn Sie diese Einstellung aktivieren (was der Standardeinstellung entspricht), können Abonnenten auf Downloads zugreifen, wenn Administratoren neue Abonnements erstellen.  Administratoren können Downloads aber weiterhin für einzelne Abonnements deaktivieren.  Durch das Deaktivieren des Zugriffs auf Downloads wird auch der Zugriff auf Product Keys deaktiviert.  


## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>Frage:  Kann ich die Einstellung **Contact email address** (E-Mail-Adresse des Kontakts) deaktivieren, damit Abonnenten keine Administratoren kontaktieren können?
Antwort:  Nein. Sie können zwar mit einer Sicherheitsgruppe, einem E-Mail-Alias für eine Gruppe oder mit einer einzelnen E-Mail-Adresse festlegen, welche Administratoren kontaktiert werden, das Feature können Sie jedoch nicht deaktivieren.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>Frage: Können Abonnenten, deren E-Mail ich beantworte, meine E-Mail-Adresse sehen?
Antwort:  Da Ihre Antwort von einem bestimmten E-Mail-Client gesendet wird, wird dem Abonnenten auch Ihre verwendete E-Mail-Adresse in der Antwort angezeigt.  Wenn Sie für Ihre Antwort einen Gruppenalias nutzen, wird den Abonnenten dieser angezeigt.  Wenn Sie Ihre eigene E-Mail-Adresse für die Antwort verwenden, wird diese Adresse angezeigt.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>Frage: Wo finde ich weitere Informationen zum Feature **Contact my Admin** (Administrator kontaktieren) im Abonnentenportal?
Antwort:  Weitere Informationen finden Sie im Artikel [Anfordern von Unterstützung durch einen Abonnementadministrator](contact-my-admin.md). 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Frage: An wen werden Anfragen gesendet, wenn für die Einstellung **Contact email address** (E-Mail-Adresse des Kontakts) keine Adresse festgelegt wird und ein Abonnent das Feature **Contact my Admin** (Administrator kontaktieren) verwendet?
Antwort:  Wenn keine E-Mail-Adresse für die Einstellung **Contact email address** (E-Mail-Adresse des Kontakts) festgelegt wird, erhalten alle Administratoren, die im Vertrag festgehalten sind, die Anfrage. 

## <a name="resources"></a>Ressourcen
- [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs)

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