---
title: Superadministrator- und Administratorrolle für Visual Studio-Abonnements
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 10/22/2020
ms.topic: conceptual
description: Erfahren Sie mehr über die Superadministrator- und Administratorrolle und das Zuweisen von Administratoren.
ms.openlocfilehash: 491a8de27477f68b4344ad17b860b80b4ca96aa9
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467374"
---
# <a name="super-admins-and-admins-for-visual-studio-subscription-agreements"></a>Superadministratoren und Administratoren für Visual Studio-Abonnementverträge

Im neuen Portal zur Verwaltung von Visual Studio-Abonnements für Kunden mit Volumenlizenzen gibt es zwei verschiedene Rollen. Diese entsprechen den Rollen „Primary/Notices Contact“ (Hauptkontakt) und „Subscriptions Manager“ (Abonnementverwalter), die früher im VLSC verfügbar waren.

**Superadministratoren:** Bei der Ersteinrichtung einer Organisation wird der Hauptkontakt standardmäßig zum Superadministrator. Der primäre Kontakt kann weitere Superadministratoren oder Administratoren zuweisen. Ein Superadministrator kann andere Administratoren sowie Abonnenten hinzufügen und entfernen. Wenn im System mehr als zwei Superadministratoren existieren, kann jeder Superadministrator alle anderen bis auf die letzten zwei löschen, da diese aus Sicherheitsgründen nicht gelöscht werden können.

**Administratoren:** Administratoren können nur von einem Superadministrator zugewiesen werden. Ein Administrator kann ausschließlich Abonnenten innerhalb der Verträge verwalten, die der Superadministrator diesem zuweist.

Sehen Sie sich eine Demonstration zum Verwalten von Administratoren an. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-admins"></a>Zuweisen von Administratoren
So weisen Sie neue Administratoren zu:
1. Melden Sie sich bei https://manage.visualstudio.com mit einer E-Mail-Adresse an, der die Rolle des Superadministrators entsprechend dem Vertrag zugewiesen ist, über den die Abonnements erworben wurden.
2. Klicken Sie auf die Registerkarte **Administratoren verwalten** .
3. Klicken Sie auf **Hinzufügen** .
   > [!div class="mx-imgBorder"]
   > ![Add admins (Administratoren hinzufügen)](_img/admin-roles/add-admins.png "Klicken Sie auf das Blatt „Administratoren verwalten“, und klicken Sie dann auf „Hinzufügen“, um neue Administratoren hinzuzufügen.")
4. Füllen Sie das Formular mit den Informationen des neuen Administrators aus.  
   > [!div class="mx-imgBorder"]
   > ![Formular zum Hinzufügen von Administratoren](_img/admin-roles/add-form.png "Geben Sie die Anmeldedaten für den neuen Administrator ein, und entscheiden Sie, ob dieser ein Superadministrator sein soll.  Klicken Sie anschließend auf „Hinzufügen“.")

   > [!NOTE]
   > Wenn dieser Administrator in der Lage sein soll, weitere Administratoren zuzuweisen, müssen Sie das Kontrollkästchen neben **Super Admin** (Superadministrator) aktivieren.

5. Klicken Sie auf **Hinzufügen** , um den neuen Administrator zuzuweisen. Dieser erhält dann eine E-Mail, in der er aufgefordert wird, sich beim Portal anzumelden.  

## <a name="resources"></a>Ressourcen
- [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Nächste Schritte
- Erfahren Sie, wie Sie [Abonnements zuweisen](assign-license.md).
- Erfahren Sie mehr über die unterschiedlichen [Abonnementvorteile](https://visualstudio.microsoft.com/vs/benefits/).
- [Festlegen von Vereinbarungseinstellungen](admin-prefs.md)