---
title: Visual Studio-Abonnements in MPSA | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 09/03/2020
ms.topic: conceptual
description: Erfahren Sie mehr über Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA).
ms.openlocfilehash: 388c847ce19ca7136efb7757fbc87bffdc35a673
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903798"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA)
Wenn Sie Visual Studio-Abonnements über das MPSA-Programm erworben haben, müssen Sie einige Dinge beachten, bevor Sie Administrator von Visual Studio-Abonnements werden und Ihren Benutzern Abonnements zuweisen können. Wenn Sie bereits Administratorrechte besitzen, können Sie direkt zum [Verwaltungsportal](https://manage.visualstudio.com/) für Visual Studio-Abonnements wechseln.

MPSA-Kunden verwalten ihre per MPSA erworbenen Ressourcen in einem Portal namens [Business Center](https://businessaccount.microsoft.com/Customer), das ähnliche Funktionen unterstützt wie das Volume Licensing Service Center (VLSC). Dazu gehören die Anzeige Ihrer Lizenzzusammenfassung, Aufträge, Downloads, Schlüssel, Benutzer usw. Visual Studio-Abonnements in MPSA verhalten sich jedoch ähnlich wie Clouddienste. Das Business Center verwendet zudem Geschäftskonten statt Microsoft-Konten (MSA) zur Anmeldung. Wenn Ihre Organisation Clouddienste wie Office 365 oder Azure Active Directory verwendet und Ihre E-Mail-Adresse Teil eines dieser beiden Dienste ist, ist es bereits ein Geschäftskonto. Dadurch können Sie sich mit Ihrem vorhandenen Kennwort beim Business Center registrieren. Wenn Ihre Organisation keine Clouddienste verwendet und Ihre E-Mail-Adresse kein Geschäftskonto ist, können Sie die Adresse dennoch für die Registrierung beim Business Center verwenden.

Darüber hinaus weisen Sie Abonnements im [Verwaltungsportal](https://manage.visualstudio.com/) für Visual Studio-Abonnements zu, sobald Sie Administrator für Visual Studio-Abonnements sind. In MPSA müssen Visual Studio-Abonnements in ihrem jeweiligen Verwaltungsportal bereitgestellt werden, also im Verwaltungsportal für Visual Studio-Abonnements. Zu diesem Zweck müssen Sie Ihr Einkaufskonto einem Mandanten zuordnen (z.B. „contoso.onmicrosoft.com“).

Beachten Sie, dass es zwei Arten von Mandanten gibt: verwaltete und nicht verwaltete Mandanten. Der Begriff „verwalteter Mandant“ bezieht sich auf einen Mandanten, der bereits von internen Administratoren der Organisation verwaltet wird.

Ein nicht verwalteter Mandant ist ein Mandant ohne zugewiesene Administratoren und kann nicht für Onlinedienste wie Office 365 verwendet werden. Nicht verwaltete Mandanten werden auch erstellt, wenn die Registrierung beim Business Center mit einer E-Mail-Adresse durchgeführt wird, die kein Geschäftskonto ist. Wenn Sie während der Registrierung beim Business Center aufgefordert wurden, ein Kennwort zu erstellen, bedeutet dies, dass Ihre E-Mail-Adresse kein Geschäftskonto war und ein nicht verwalteter Mandant erstellt wurde.

Im Folgenden finden Sie einige Anforderungen/Schritte, die erforderlich sind, um Administrator für Visual Studio-Abonnements zu werden, bevor die Mandantenzuordnung abgeschlossen werden kann.

## <a name="pre-tenant-association-managed-tenant"></a>Vorabzuordnung des Mandanten (verwalteter Mandant)
- Sie müssen ein bei Business Center registrierter Benutzer sein.
- Sie müssen ein Benutzeradministrator (mindestens) oder ein globaler Administrator innerhalb des Mandanten sein, dem Sie angehören. (Dies gilt, wenn Ihr Unternehmen bereits Clouddienste verwendet). Die Rollen müssen Administratoren für Visual Studio-Abonnements sein.
- Sie müssen ein globaler Administrator des Mandanten sein, dem Sie angehören, um Ihr Einkaufskonto Ihrem Mandanten zuordnen zu können.
- Sie müssen ein Kontoadministrator oder Konto-Manager in Business Center sein.
- Das Feld „Land oder Region“ in Ihrem Benutzerprofil (sowie für alle anderen Benutzer) in [Azure](https://portal.azure.com/) muss abhängig von Ihrer Region (z.B. USA, Kanada usw.) ausgefüllt sein. 

> [!NOTE]
> Benutzer, die Sie zu Administratoren für Visual Studio-Abonnements machen möchten, müssen keine Benutzer im Business Center sein, da sie nur die Kriterien 2 und 5 erfüllen müssen.

Sobald Sie die oben genannten Kriterien erfüllen, können Sie damit fortfahren, Ihr Einkaufskonto Ihrem Mandanten zuzuordnen. Führen Sie dazu die folgenden Schritte aus.
1. Melden Sie sich bei [Business Center](https://businessaccount.microsoft.com/Customer) an.
2. Klicken Sie auf die Registerkarte **Konto** , und wählen Sie **Domänen zuordnen** aus.
3. Wählen Sie Ihr **Einkaufskonto** aus (falls mehrere vorhanden sind).
4. Wählen Sie Ihren **Mandanten** aus (z.B. „contoso.onmicrosoft.com“).
5. Klicken Sie auf **Domäne zuordnen**.

Nach der Zuordnung werden alle Benutzer, die die Kriterien erfüllen, in der Regel innerhalb weniger Minuten als Administratoren für Visual Studio Abonnements bereitgestellt. Manchmal kann es allerdings bis zu 24 Stunden dauern. Nach der Bereitstellung des Mandanten können Sie auf das Verwaltungsportal für Visual Studio-Abonnements zugreifen. Wenden Sie sich folgendermaßen an den MPSA-Support, wenn der Vorgang länger als 24 Stunden dauert:
1. Rufen Sie <https://www.microsoft.com/licensing/mpsa/default> auf.
2. Klicken Sie oben auf der Seite auf die das Menü **Mehr**. 
3. Klicken Sie auf **Hilfe**.
4. Wählen Sie die Option für **Hilfe bei der Lizenzierung** aus.
5. Wählen Sie nun die Hilfeoption aus, die Ihren Anforderungen am besten entspricht: 

> [!NOTE]
> Wenn es sich um neue Benutzer handelt, die (nach der Zuweisung) die Kriterien in den Schritten 2 und 5 erfüllen, müssen Sie sich an den MPSA-Support wenden. Der MPSA-Support bietet Unterstützung für die Bereitstellung der neuen Administratoren für Visual Studio-Abonnements.

## <a name="tenant-association-unmanaged"></a>Mandantenzuordnung (nicht verwaltet)
Wenn Sie sich beim Business Center mit einer E-Mail-Adresse registriert haben, die kein Geschäftskonto war (nicht in Azure Active Directory registriert), wie oben erläutert, verläuft die Mandantenzuordnung etwas anders. Sie müssen eine sogenannte „Domänenübernahme“ ausführen. Während dieses Vorgangs machen Sie sich selbst zum globalen Administrator. Dadurch wird Ihr Mandant von einem nicht verwalteten zu einem verwalteten Mandanten.

Eine ausführlichere Erläuterung dieses Prozesses finden Sie in den [Schnellstartanleitungen](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Laden Sie das Handbuch *Setup and Use Your Online Services* (Einrichten und Verwenden Ihrer Onlinedienste) herunter, das Ihnen bei der Domänenübernahme hilft. Anschließend wird Ihr Einkaufskonto Ihrem Mandanten zugeordnet.

> [!NOTE]
> Nach der Domänenübernahme müssen Sie die Kriterien aus den fünf Schritten im Abschnitt „Vorabzuordnung des Mandanten (verwalteter Mandant)“ befolgen. Wenn die Kriterien erfüllt sind, müssen Sie sich nur an den MPSA-Support wenden, um weitere Administratoren für Visual Studio-Abonnements bereitzustellen.

## <a name="see-also"></a>Weitere Informationen
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
In diesen Artikeln erhalten Sie weitere Informationen zum Verwalten von Visual Studio-Abonnements.
- [Zuweisen von Lizenzen im Verwaltungsportal für Visual Studio-Abonnements](assign-license.md)
- [Zuweisen von Abonnements zu mehreren Benutzern](assign-license-bulk.md)
- [Bearbeiten von Abonnements](edit-license.md)
- [Löschen von Abonnements](delete-license.md)
- [Verwenden des Features „Maximum Usage“ (Maximale Auslastung) zur Übersicht der Anzahl zugewiesener Abonnements](maximum-usage.md)