---
title: Wie weise ich Visual Studio-Abonnements zu?
description: Sie können Ihren Endbenutzern Abonnements entweder einzeln zuweisen oder das Feature zum Massenhinzufügen verwenden, um schnell und einfach eine größere...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 12/03/2020
ms.openlocfilehash: 5a12d59f90ee2a09002efcb99c78cfd563060006
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96584620"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Wie weise ich Visual Studio-Abonnements zu?

Sie können Ihren Endbenutzern Abonnements entweder einzeln zuweisen oder das Feature zum Massenhinzufügen verwenden, um schnell und einfach eine größere Anzahl von Abonnenten hochzuladen.

Gehen Sie wie folgt vor, um Abonnements einzeln zuzuweisen:

1. Klicken Sie unter [manage.visualstudio.com](https://manage.visualstudio.com) oben auf der Seite auf die [Registerkarte „Manage Subscribers“ (Abonnenten verwalten)](https://manage.visualstudio.com/subscribers).
2. Klicken Sie auf „Hinzufügen“, und tippen Sie den Namen und die E-Mail-Adresse des Benutzers ein, dem Sie ein Abonnement zuweisen möchten.
    1. Wenn Ihre Organisation Azure Active Directory verwendet, sucht das Namensfeld nach Personen in Ihrem aktuellen Verzeichnis. Sie können entweder eines der Suchergebnisse auswählen oder Personen manuell hinzufügen.
3. Wenn Sie möchten, dass der Abonnent Zugriff auf Softwaredownloads hat, wenn er sich beim [Visual Studio-Abonnements-Portal](https://my.visualstudio.com/) anmeldet, stellen Sie sicher, dass die Umschaltfläche „Downloads“ im Abschnitt „Download settings“ (Downloadeinstellungen) aktiviert ist.
4. Füllen Sie den Abschnitt „Communication Preferences“ (Kommunikationseinstellungen) aus, damit wir wissen, in welcher Sprache die Zuweisungs-E-Mail an Ihre Abonnenten gesendet werden soll.
5. Wenn Sie Hinweise in Zusammenhang mit der Zuweisung hinzufügen möchten, verwenden Sie hierfür den Abschnitt „Verweis“.
6. Klicken Sie im Flyoutbereich unten auf „Hinzufügen“, um das Zuweisen des Abonnements abzuschließen. Ihr Abonnent erhält eine E-Mail und kann sein Visual Studio-Abonnement sofort nutzen. (Es ist keine Aktivierung durch Ihren Abonnenten erforderlich.)

Gehen Sie bei einer Massenzuweisung von Abonnements wie folgt vor:

1. Klicken Sie unter [manage.visualstudio.com](https://manage.visualstudio.com) oben auf der Seite auf die [Registerkarte „Manage Subscribers“ (Abonnenten verwalten)](https://manage.visualstudio.com/subscribers).
2. Klicken Sie auf „Bulk add“ (Massenhinzufügen), laden Sie die Excel-Vorlage herunter, und speichern Sie eine lokale Kopie davon.
3. Bis auf das Feld „Reference“ (Verweis) sind alle Felder Pflichtfelder.
    1. Stellen Sie sicher, dass die Formularfelder keine Kommas enthalten.
    2. Entfernen Sie Leerzeichen vor und nach Formularfeldern.
    3. Stellen Sie sicher, dass Namen keine zusätzlichen Leerzeichen zwischen zweiteiligen Vor- und Nachnamen aufweisen (wenn z. B. eine Person über einen zweiteiligen Vornamen wie „Maggie May“ verfügt, sollte dieser als „MaggieMay“ eingegeben werden).
4. Kehren Sie zurück zu [manage.visualstudio.com](https://manage.visualstudio.com), klicken Sie auf „Bulk add“ (Massenhinzufügen), und laden Sie Ihre gespeicherte Kopie der Excel-Vorlage hoch.
5. Ist der Upload erfolgreich, so wird Ihnen eine Bestätigungsseite angezeigt, und Ihre neuen Abonnenten sind in der Abonnentenliste aufgeführt. Ihre Abonnenten erhalten eine E-Mail und können ihr Visual Studio-Abonnement sofort nutzen. (Es ist keine Aktivierung durch Ihre Abonnenten erforderlich.)

[Lesen Sie sich weitere Informationen](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) zum Zuweisen von Abonnements im Administratorportal für Visual Studio-Abonnements durch, um mehr darüber zu erfahren, wie Sie Abonnements schnell und einfach zuweisen können.  [Weitere Informationen](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) zur Verwaltung von Visual Studio-Abonnements mit GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>Wie funktioniert der Einrichtungsvorgang für GitHub Enterprise? 

GitHub Enterprise wird getrennt von Visual Studio-Abonnements eingerichtet und verwaltet. Nach dem Kauf eines Visual Studio-Abonnements mit GitHub Enterprise wird ein Einrichtungsvorgang für ein GitHub Enterprise-Konto parallel mit (aber getrennt von) der Festlegung einer Vereinbarung unter manage.visualstudio.com initiiert. Die Einrichtung dieses GitHub Enterprise-Kontos kann einige Zeit in Anspruch nehmen.  

Sobald Ihr Unternehmen ein GitHub Enterprise-Konto eingerichtet hat, erhalten Abonnenten, denen Visual Studio-Abonnements mit GitHub Enterprise zugewiesen wurden, eine E-Mail von GitHub, in der sie benachrichtigt werden, dass ihre Visual Studio-Abonnements verknüpft wurden. Sobald Abonnenten die E-Mail erhalten haben, können sie sich an den Administrator ihrer GitHub-Organisation wenden, um eine Einladung für die entsprechende Organisation anzufordern. 

[Weitere Informationen](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) zur Verwaltung von Visual Studio-Abonnements mit GitHub Enterprise. Lesen Sie die [Dokumentation für Abonnenten](https://docs.microsoft.com/visualstudio/subscriptions/access-github), um zusätzliche Details zum GitHub Enterprise-Einrichtungsprozess zu erhalten. 