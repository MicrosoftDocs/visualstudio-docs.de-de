---
title: Anonymisierung von Daten der Visual Studio-Abonnenten | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 02/20/2020
ms.topic: conceptual
description: Erfahren Sie, wie Abonnentendaten anonymisiert werden, wenn der Zugriff auf Abonnements verloren gegangen ist.
ms.openlocfilehash: b65673d2fe61f62bf9e7731d20763bcd8c6f74bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80232736"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonymisierung von Informationen der Visual Studio-Abonnenten
Wenn ein Ereignis eintritt, durch das die Verwendung eines Abonnements durch einen Abonnenten blockiert wird, z.B. der Ablauf eines Abonnements oder die Löschung des Anmeldekontos eines Abonnenten, werden die persönlichen Informationen des Benutzers wie Name und Anmeldekonto so verschlüsselt, dass sie unbrauchbar werden.  Dies geschieht, um die persönlichen Informationen des Abonnenten zu schützen.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Wann kommt es zur Anonymisierung?
Ereignisse, die ein Abonnement für einen Abonnenten unbenutzbar machen, lösen eine Anonymisierung aus.  Wie schnell die Anonymisierung erfolgt, hängt von der Art des Abonnements und dem auslösenden Ereignis ab. Weitere Informationen finden Sie in der folgenden Tabelle.

| Abonnementtyp                                                                                                                       | Ereignis, das die Anonymisierung auslöst                                                                                                     | Wann es zur Anonymisierung kommt |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Der Abonnent kündigt das Programm oder akzeptiert die Nutzungsbedingungen nicht                                    | 30 Tage               |
| Visual Studio-Abonnements, die über den Microsoft Store erworben wurden (Einzelhandel)                                                                      | Das Abonnement läuft ab oder wird nicht aktiviert                                                                   | 360 Tage                  |
| Visual Studio-Abonnements, die über Volumenlizenz, Visual Studio Marketplace (Cloud-Abonnements) oder Programme wie MPN erworben wurden | Das Abonnement läuft ab oder wird keinem Benutzer zugewiesen                                                          | 180 Tage                  |
| Alle Abonnements                                                                                                                       | Ein Azure Active Directory-Konto oder ein Microsoft-Konto (MSA), das für die Anmeldung beim Abonnement verwendet wird, wird geschlossen | Sofort               |
| Alle Abonnements                                                                                                                       | Ein Abonnent wird aus dem Mandanten entfernt, der mit dem Azure Active Directory-Konto verknüpft ist                                | Sofort               |

## <a name="faq"></a>FAQ
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Frage:  Führt die Anonymisierung der persönlichen Informationen des Abonnenten dazu, dass er den Zugriff auf das Abonnement verliert?
Antwort:  Nein.  Die Anonymisierung ist eine Reaktion auf ein Ereignis, durch das der Zugriff auf das Abonnement verloren geht, aber nicht die Ursache für den Verlust des Zugriffs.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Frage:  Ich bin ein Administrator für die Abonnements meiner Organisation.  Wenn die Informationen eines meiner Abonnenten anonymisiert werden, kann dieses Abonnement dann einem anderen Benutzer zugewiesen werden?
Antwort:  Ja, solange das Abonnement nicht abgelaufen ist, kann es einem anderen Abonnenten zugewiesen werden.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>Frage: Wie kann ich verhindern, dass die Anonymisierung durch Löschen einer E-Mail-Adresse für die Anmeldung verursacht wird?
Antwort:  Es gibt zwei Möglichkeiten, das Problem zu verhindern:
- Stellen Sie ein einziges Identitätsverwaltungssystem bereit – entweder MSA oder AAD, aber nicht beide.  
- Ordnen Sie die AAD- und MSA-Identitäten über den Mandanten zu. 

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie, wie Sie die Anonymisierung durch [Verbinden von MSA- und AAD-Identitäten](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator) verhindern.


