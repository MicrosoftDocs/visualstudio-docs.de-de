---
title: Festlegen von benutzerdefinierten Berechtigungen (ClickOnce-APP)
description: Erfahren Sie, wie Sie eine ClickOnce-Anwendung bereitstellen, die Standard Berechtigungen verwendet, oder eine benutzerdefinierte Zone für die spezifischen Berechtigungen erstellen, die die Anwendung benötigt.
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
ms.openlocfilehash: d5d0348b882a3327c02fca6db0628822c0deffeb
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350997"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Vorgehensweise: Festlegen von benutzerdefinierten Berechtigungen für eine ClickOnce-Anwendung
Sie können eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung bereitstellen, die Standardberechtigungen für die Zonen „Internet“ oder „Lokales Intranet“ verwendet. Alternativ können Sie eine benutzerdefinierte Zone für die spezifischen Berechtigungen erstellen, die die Anwendung benötigt. Diese Berechtigungen können Sie erstellen, indem Sie die Sicherheitsberechtigungen auf der Seite **Sicherheit** des **Projekt-Designers** anpassen.

### <a name="to-customize-a-permission"></a>So passen Sie eine Berechtigung an

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

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

## <a name="see-also"></a>Weitere Informationen
- [Sichere ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)
