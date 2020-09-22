---
title: Festlegen von benutzerdefinierten Berechtigungen (ClickOnce-APP)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c9952573be69299e14dc87f345febb14cdef0ec
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809715"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Vorgehensweise: Festlegen von benutzerdefinierten Berechtigungen für eine ClickOnce-Anwendung
Sie können eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung bereitstellen, die Standardberechtigungen für die Zonen „Internet“ oder „Lokales Intranet“ verwendet. Alternativ können Sie eine benutzerdefinierte Zone für die spezifischen Berechtigungen erstellen, die die Anwendung benötigt. Diese Berechtigungen können Sie erstellen, indem Sie die Sicherheitsberechtigungen auf der Seite **Sicherheit** des **Projekt-Designers**anpassen.

### <a name="to-customize-a-permission"></a>So passen Sie eine Berechtigung an

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Sicherheit** .

3. Aktivieren Sie das Kontrollkästchen **ClickOnce-Sicherheitseinstellungen aktivieren** .

4. Wählen Sie das Optionsfeld **Teilweise vertrauenswürdige Anwendung** aus.

     Die Steuerelemente im Abschnitt **ClickOnce-Sicherheitsberechtigungen** sind aktiviert.

5. Klicken Sie in der Dropdownliste **Zone, aus der die Anwendung installiert wird** auf **(Benutzerdefiniert)**.

6. Klicken Sie auf **Berechtigungs-XML bearbeiten**.

     Die Datei *app.manifest* wird im XML-Editor geöffnet.

7. Fügen Sie vor dem `</applicationRequestMinimum>` -Element den XML-Code für Berechtigungen hinzu, den Ihre Anwendung benötigt.

    > [!NOTE]
    > Sie können die `ToXml` -Methode einer Berechtigung verwenden, die zum Generieren des XML-Codes für das Anwendungsmanifest festgelegt wurde. Rufen Sie z.B. zum Generieren des XML-Codes für die <xref:System.Security.Permissions.EnvironmentPermission> -Berechtigung die <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> -Methode auf.

## <a name="see-also"></a>Siehe auch
- [Sichere ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)
