---
title: Verwenden von Konten, die mehrstufige Authentifizierung erfordern
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Erfahren Sie, wie Visual Studio mit Konten verwendet wird, die mehrstufige Authentifizierung erfordern.
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 6b85d64d3f84bce34f2a9b30d9caf01127149abc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878486"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Verwenden von Visual Studio mit Konten, die mehrstufige Authentifizierung erfordern

Bei der Zusammenarbeit mit externen Gastbenutzern wird empfohlen, Ihre Apps mit Richtlinien für **bedingten Zugriff** zu schützen, etwa mit **mehrstufiger Authentifizierung (Multi-Factor Authentification, MFA)** .  

Nach der Aktivierung benötigen Gastbenutzer für den Zugriff auf Ihre Ressourcen mehr als nur einen Benutzernamen und ein Kennwort und müssen zusätzliche Sicherheitsanforderungen erfüllen. MFA-Richtlinien können auf Mandanten-, App- oder individueller Benutzerebene erzwungen werden, so wie sie auch für Mitglieder Ihrer eigenen Organisation aktiviert werden können. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Wie wird die Erfahrung mit Visual Studio durch MFA-Richtlinien beeinflusst?
Versionen von Visual Studio vor Version 16.6 können bei der Verwendung mit Konten, die Richtlinien für bedingten Zugriff wie MFA aktiviert haben und mit mindestens zwei Mandanten verknüpft sind, zu einer beeinträchtigten Authentifizierungserfahrung führen.

Diese Probleme können dazu führen, dass Ihre Visual Studio-Instanz eine erneute Authentifizierung mehrmals täglich anfordert. Möglicherweise müssen Sie Ihre Anmeldeinformationen für zuvor authentifizierte Mandanten erneut eingeben, und zwar selbst während der gleichen Visual Studio-Sitzung.

## <a name="using-visual-studio-with-mfa-policies"></a>Verwenden von Visual Studio mit MFA-Richtlinien
In Version 16.6 haben wir Visual Studio 2019 neue Funktionen hinzugefügt, mit denen Sie optimieren können, wie Benutzer auf Ressourcen zugreifen können, die über Richtlinien für bedingten Zugriff wie MFA geschützt sind. Um diesen verbesserten Workflow nutzen zu können, müssen Sie sich für die Verwendung des Standardwebbrowsers Ihres Systems als Mechanismus zum Hinzufügen und erneuten Authentifizieren von Visual Studio-Konten entscheiden.  

> [!WARNING]
> Wenn dieser Workflow nicht verwendet wird, kann dies zu einer beeinträchtigten Erfahrung führen, die beim Hinzufügen oder erneuten Authentifizieren von Visual Studio-Konten zu mehreren zusätzlichen Authentifizierungsaufforderungen führt. 

### <a name="enabling-system-web-browser"></a>Aktivieren des Systemwebbrowsers

> [!NOTE] 
> Wir empfehlen, die Daten des Standardwebbrowsers Ihres Systems zu löschen, bevor Sie mit diesem Workflow fortfahren. Wenn es darüber hinaus in Ihren Windows 10-Einstellungen unter **Auf Arbeits- oder Schulkonto zugreifen** Geschäfts-, Schul- oder Unikonten gibt, prüfen Sie außerdem, ob diese ordnungsgemäß authentifiziert sind.

Um diesen Workflow zu aktivieren, navigieren Sie zum Dialogfeld „Optionen“ von Visual Studio **(„Extras > Optionen...“)** , wählen Sie die Registerkarte **Konten** aus, und wählen Sie **Systemwebbrowser** unter der Dropdownliste **Konten hinzufügen und erneut authentifizieren mit:** aus. 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Auswählen des Systemwebbrowsers im Menü.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Anmelden bei zusätzlichen Konten mit MFA-Richtlinien 
Nachdem der Systemwebbrowser-Workflow aktiviert wurde, können Sie sich wie gewohnt über das Dialogfeld „Kontoeinstellungen“ **(Datei > Kontoeinstellungen...)** anmelden oder Visual Studio-Konten hinzufügen.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Hinzufügen eines neuen Personalisierungskontos zu Visual Studio." border="false":::

Mit dieser Aktion wird der Standardwebbrowser Ihres Systems geöffnet, Sie werden aufgefordert, sich bei Ihrem Konto anzumelden, und es werden alle erforderlichen MFA-Richtlinien überprüft.

Während des Anmeldevorgangs erhalten Sie möglicherweise eine zusätzliche Aufforderung, angemeldet zu bleiben. Diese Aufforderung wird wahrscheinlich angezeigt, wenn ein Konto zum zweiten Mal zum Anmelden verwendet wird. Um die Notwendigkeit der erneuten Eingabe Ihrer Anmeldeinformationen zu minimieren, sollten Sie **Ja** auswählen, da dadurch sichergestellt wird, dass Ihre Anmeldeinformationen über Browsersitzungen hinweg beibehalten werden.

:::image type="content" source="media/kmsi.png" alt-text="Angemeldet bleiben?":::

Je nach Ihren Entwicklungsaktivitäten und Ihrer Ressourcenkonfiguration werden Sie möglicherweise noch aufgefordert, Ihre Anmeldeinformationen während Ihrer Sitzung erneut einzugeben. Dies kann der Fall sein, wenn Sie eine neue Ressource hinzufügen oder versuchen, auf eine Ressource zuzugreifen, ohne zuvor deren Zertifizierungsstellen-/MFA-Autorisierungsanforderungen erfüllt zu haben.

## <a name="reauthenticating-an-account"></a>Erneutes Authentifizieren eines Kontos  
Wenn ein Problem mit Ihrem Konto vorliegt, werden Sie möglicherweise von Visual Studio aufgefordert, Ihre Kontoanmeldeinformationen erneut einzugeben.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Erneutes Authentifizieren Ihres Visual Studio-Kontos.":::

Wenn Sie auf **Anmeldeinformationen erneut eingeben** klicken, wird der Standardwebbrowser Ihres Systems geöffnet, und es wird versucht, Ihre Anmeldeinformationen automatisch zu aktualisieren. Wenn dies nicht erfolgreich ist, werden Sie aufgefordert, sich bei Ihrem Konto anzumelden und alle erforderlichen Zertifizierungsstellen-/MFA-Richtlinien zu überprüfen.

> [!NOTE] 
> Am besten lassen Sie Ihren Browser geöffnet, bis alle Zertifizierungsstellen-/MFA-Richtlinien für Ihre Ressourcen überprüft wurden. Das Schließen des Browsers kann dazu führen, dass der zuvor aufgebaute MFA-Status verloren geht und zusätzliche Autorisierungsaufforderungen angezeigt werden.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Ablehnen der Verwendung eines bestimmten Azure Active Directory-Mandanten in Visual Studio

Visual Studio 2019 Version 16.6 bietet die Flexibilität, bestimmte Mandanten herauszufiltern, die so in Visual Studio ausgeblendet werden. Durch das Filtern entfällt die Notwendigkeit, sich bei diesem Mandanten zu authentifizieren, aber es bedeutet auch, dass Sie nicht auf zugeordnete Ressourcen zugreifen können. 

Diese Funktion ist nützlich, wenn Sie über mehrere Mandanten verfügen, aber Ihre Entwicklungsumgebung optimieren möchten, indem Sie eine bestimmte Teilmenge als Ziel festlegen. Dies kann auch in Fällen hilfreich sein, in denen Sie eine bestimmte Richtlinie für bedingten Zugriff bzw. eine MFA-Richtlinie nicht überprüfen können, da Sie den störenden Mandanten herausfiltern können. 

### <a name="how-to-filter-out-a-tenant"></a>Herausfiltern eines Mandanten
Um Mandanten zu filtern, die Ihrem Visual Studio-Konto zugeordnet sind, öffnen Sie das Dialogfeld „Kontoeinstellungen“ **(Datei > Kontoeinstellungen...)** und klicken auf **Filter anwenden**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Anwenden eines Filters." border="false":::

Das Dialogfeld **Konto filtern** wird angezeigt, in dem Sie auswählen können, welche Mandanten Sie mit Ihrem Konto verwenden möchten. 

:::image type="content" source="media/select-filter-account.png" alt-text="Auswählen des zu filternden Kontos.":::

## <a name="see-also"></a>Siehe auch

- [Anmelden bei Visual Studio](signing-in-to-visual-studio.md)
- [Anmelden bei Visual Studio für Mac](/visualstudio/mac/signing-in)
- [Arbeiten mit mehreren Benutzerkonten](work-with-multiple-user-accounts.md)
