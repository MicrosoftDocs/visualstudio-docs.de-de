---
title: VBA-Zugriff zum Erstellen/Öffnen eines VSTO-System Projekts
titleSuffix: ''
description: Erfahren Sie, wie Sie den Zugriff auf das Office VBA-Projekt System explizit aktivieren müssen, bevor Sie eine Visual Studio-Tools für das Office System-Projekt erstellen oder öffnen können.
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62477f7cd37a7d5a416e8f42fb7eb2d2a8e43828
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846128"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Aktivieren des Zugriffs auf VBA zum Erstellen oder Öffnen einer Visual Studio-Tools für das Microsoft Office System Projekt

Sie müssen den Zugriff auf das Visual Basic for Applications (VBA)-Projekt System in Microsoft Office explizit aktivieren, bevor Sie eine Visual Studio-Tools für das Microsoft Office System Projekt erstellen oder öffnen können.

 Microsoft Office Entwicklungsprojekte benötigen Zugriff auf das Visual Basic for Applications (VBA)-Projekt System in Microsoft Office Word und Microsoft Office Excel, auch wenn die Projekte Visual Basic for Applications nicht verwenden. Unterstützung der Steuerelemente in Visual Basic- und C#-Projekten zur Entwurfszeit ist vom Visual Basic for Applications-Projektsystem abhängig.

 Einige Microsoft Office-Makroviren versuchen das Visual Basic for Applications-Projektsystem als Mittel zur Selbstweitergabe zu automatisieren. Um den Zugriff auf das Visual Basic for Applications-Projektsystem zu aktivieren, entfernen Sie eine Schutzvorrichtung, mit der die Verbreitung von Makroviren verhindert werden kann. Die normale Makrosicherheit wird weiterhin aufrecht erhalten, sodass die Makrosicherheitsebene und die Liste der vertrauenswürdigen Herausgeber, die Sie für Ihre Office-Anwendungen verwalten, bestimmen, ob ein Makro auf Ihrem Computer ausgeführt wird.

> [!NOTE]
> Dies gilt nur für den Entwicklungscomputer. Für Endbenutzer Computer ist diese Option nicht aktiviert, um Office-Projektmappen auszuführen.

 Sie sollten beachten, dass die Deaktivierung des Zugriffs auf das Visual Basic for Applications-Projektsystem Sie nicht allein vor Viren schützt. Dadurch wird lediglich die Verbreitung einiger Viren auf andere Dokumente verhindert, wenn Ihr Computer mit einem Makrovirus infiziert werden sollte. Diese Option ist standardmäßig als zusätzliche Schutzstufe für Ihren Computer deaktiviert; die Aktivierung macht Ihren Computer nicht anfälliger für Viren, wenn Sie die Best Practices hinsichtlich der Sicherheit befolgen.

 Der beste Schutz vor Office-Makroviren besteht darin, Office mit hoher oder sehr hoher Sicherheitsstufe auszuführen, nur Makros von verifizierten, bekannten Quellen zu Vertrauen und mit Sicherheitspatches und Virenscanner auf dem neuesten Stand zu bleiben.

 Sie können die Option **Vertrauens Zugriff auf Visual Basic Projekt** manuell aktivieren oder deaktivieren.

 Sie können die Office-Installation reparieren, wenn VBA- oder COM-Fehler angezeigt werden.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>So aktivieren oder deaktivieren Sie den Zugriff auf Visual Basic Projekte

1. Klicken Sie auf die Registerkarte **Datei** .

2. Klicken Sie auf **Optionen**.

3. Klicken Sie auf **Trust Center**, und klicken Sie dann auf **Trust Center-Einstellungen**.

4. Klicken Sie im **Trust Center** auf **Makro Einstellungen**.

5. Aktivieren oder deaktivieren Sie **den Zugriff auf das VBA-Projekt Objektmodell** , um den Zugriff auf Visual Basic Projekte zu aktivieren bzw. zu deaktivieren.

6. Klicken Sie auf **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>So aktivieren oder deaktivieren Sie den Zugriff auf Visual Basic Projekte mit dem 2007 Microsoft Office System

1. Zeigen Sie **im Menü Extras** in Word oder Excel auf **Makro**, und klicken Sie dann auf **Sicherheit**.

2. Klicken Sie im Dialogfeld **Sicherheit** auf die Registerkarte **Vertrauenswürdige Herausgeber** .

3. Wählen Sie diese Option aus, um den **Zugriff auf Visual Basic Projekt** zu aktivieren oder zu deaktivieren.

4. Klicken Sie auf **OK**.

## <a name="to-set-your-office-macro-security-level"></a>So legen Sie die Office-Makrosicherheitsstufe fest

1. Klicken Sie auf die Registerkarte **Datei** .

2. Klicken Sie auf **Optionen**.

3. Klicken Sie auf **Trust Center**, und klicken Sie dann auf **Trust Center-Einstellungen**.

4. Klicken Sie im **Trust Center** auf **Makro Einstellungen**.

5. Wählen Sie im Abschnitt **Makro Einstellungen** die gewünschte Einstellung aus.

6. Klicken Sie auf **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>So legen Sie die Office-Makro Sicherheitsstufe mit dem 2007-Microsoft Office System fest

1. Zeigen Sie **im Menü Extras** in Word oder Excel auf **Makro**, und klicken Sie dann auf **Sicherheit**.

2. Wählen Sie auf der Registerkarte **Sicherheitsstufe** die gewünschte Einstellung aus.

    Die Registerkarte **Sicherheitsstufe** enthält Details zu den einzelnen Ebenen. Weitere Informationen finden Sie im Thema zu Makrosicherheitsstufen in der Office-Hilfe.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>So installieren Sie VBA mit dem Microsoft Office 2007-System

1. Führen **Sie** in der Systemsteuerung die Option Software oder **Programme und Funktionen** aus.

2. Wählen Sie in der Liste **Zurzeit installierte Programme** die Option Office aus.

3. Klicken Sie auf **Ändern**.

4. Wählen Sie **Features hinzufügen oder entfernen** aus, und klicken Sie dann auf **weiter**.

5. Wählen Sie **Erweiterte Anpassung der Anwendungen auswählen aus**, und klicken Sie dann auf **weiter**.

6. Erweitern Sie in der Liste **Update Optionen für Anwendungen und Tools auswählen die Option** frei **gegebene Office-Funktionen** .

7. Öffnen Sie das Dropdown Menü neben **Visual Basic for Applications**, und klicken Sie dann auf **aus Arbeitsplatz ausführen**.

8. Klicken Sie auf **Weiter**.

9. Klicken Sie auf **Schließen**.

## <a name="to-repair-your-installation-of-office"></a>So reparieren Sie Ihre Office-Installation

1. Führen **Sie** in der Systemsteuerung die Option Software oder **Programme und Funktionen** aus.

2. Wählen Sie in der Liste der **derzeit installierten Programme** Ihre Office-Version aus.

3. Klicken Sie auf **Ändern**.

4. Wählen Sie **neu installieren oder reparieren** aus, und klicken Sie dann auf **weiter**.

5. Wählen Sie **Fehler in meiner Office-Installation erkennen und reparieren aus**, und klicken Sie dann auf **Installieren**.

## <a name="see-also"></a>Siehe auch
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
