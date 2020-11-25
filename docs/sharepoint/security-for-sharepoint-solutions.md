---
title: Sicherheit für SharePoint-Lösungen | Microsoft-Dokumentation
description: Entdecken Sie, welche Features Visual Studio integriert, um die Sicherheit von SharePoint-Anwendungen zu verbessern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e3290d603de124288a5b176dfe0d2e39f5c1377f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970444"
---
# <a name="security-for-sharepoint-solutions"></a>Sicherheit für SharePoint-Lösungen
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umfasst die folgenden Funktionen, um die Sicherheit von SharePoint-Anwendungen zu verbessern.

## <a name="safe-control-entries"></a>Einträge für sicheres Steuerelement
 Jedes SharePoint-Projekt Element, das in erstellt wurde [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] , verfügt über eine Eigenschaft für **sicheres Steuerelement Einträge** , die eine Auflistung sicherer Steuerelemente Mit Ihrer **sicheren** untergeordneten Eigenschaft können Sie die Steuerelemente angeben, die Sie als sicher betrachtet haben. Weitere Informationen finden Sie unter [Bereitstellen von Paket-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) und [Angeben von sicherem Webparts](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers-Attribut
 Standardmäßig können nur Anwendungen, denen das System zur Laufzeit-Code Zugriffssicherheit (CAS) voll vertrauenswürdig ist, auf eine freigegebene verwaltete Codeassembly zugreifen. Durch das Markieren einer voll vertrauenswürdigen Assembly mit dem allowpartiallytrust dcaller-Attribut können teilweise vertrauenswürdige Assemblys darauf zugreifen.

 Das allowpartiallytrust dcaller-Attribut wird jeder SharePoint-Projekt Mappe hinzugefügt, die nicht im globalen Assemblycache des Systems () bereitgestellt wird [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] . Dies schließt Sandkasten Lösungen oder Lösungen ein, die im SharePoint-Anwendungsverzeichnis "bin" bereitgestellt werden. Weitere Informationen finden Sie unter [Sicherheitsänderungen der Version 1 für das Microsoft .NET Framework](/previous-versions/msp-n-p/ff921345(v=pandp.10)) und Bereitstellen von [Webparts in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Sicherheit für Skript Eigenschaft
 *Skript Injektion* ist das Einfügen von potenziell bösartigem Code in Steuerelemente oder Webseiten. Zur Unterstützung des Schutzes von SharePoint 2010-Websites vor der Skript Injektion können Mitwirkende keine Webparts oder deren Eigenschaften standardmäßig anzeigen und bearbeiten. Dieses Verhalten wird von einem SafeControl-Attribut mit dem Namen "safeagainstscript" gesteuert. [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]Legen Sie dieses Attribut in für die untergeordnete Eigenschaft der **sicheren Steuerelement Einträge** eines Projekt Elements vor dem **Skript** fest. Weitere Informationen finden Sie unter [Bereitstellen von Paket-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) und Gewusst [wie: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Benutzerkontensteuerung für Vista und Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] enthalten ein Sicherheits Feature, das als Benutzerkontensteuerung (User Account Control, UAC) bezeichnet wird. Zum Entwickeln von SharePoint-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] muss [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aufgrund der Benutzerkontensteuerung als Systemadministrator ausgeführt werden. Öffnen Sie **im Startmenü das** Kontextmenü für [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , und wählen Sie dann **als Administrator ausführen** aus.

 Öffnen Sie das Kontext [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Menü, wählen Sie **Eigenschaften** aus, klicken Sie im Dialogfeld **Eigenschaften** auf die Schaltfläche **erweitert** , und aktivieren Sie dann das Kontrollkästchen **als Administrator ausführen** , um die Verknüpfung so zu konfigurieren, dass Sie immer als Administrator ausgeführt wird.

 Weitere Informationen finden Sie unter [verstehen und Konfigurieren der Benutzerkontensteuerung in Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). und [Windows 7-Benutzerkontensteuerung](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Überlegungen zu SharePoint-Berechtigungen
 Bei der Entwicklung von SharePoint-Lösungen benötigen Sie ausreichende Berechtigungen, um SharePoint-Lösungen auszuführen und zu debuggen. Bevor Sie eine SharePoint-Lösung testen können, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Sie über die erforderlichen Berechtigungen verfügen:

1. Fügen Sie Ihr Benutzerkonto als Administrator für das System hinzu.

2. Fügen Sie Ihr Benutzerkonto als Farmadministrator für den SharePoint-Server hinzu.

    1. Wählen Sie in der SharePoint 2010-zentral Administration den Link **Farm Administrator Gruppe verwalten** aus.

    2. Wählen Sie auf der Seite **Farm Administratoren** die Option **Neues** Menü aus.

3. Fügen Sie das Benutzerkonto zur Gruppe "WSS_ADMIN_WPG" hinzu.

## <a name="additional-security-resources"></a>Zusätzliche Sicherheitsressourcen
 Weitere Informationen zu Sicherheitsproblemen finden Sie in den folgenden Themen.

### <a name="visual-studio-security"></a>Visual Studio-Sicherheit

- [Sicherheit und Benutzerberechtigungen](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Sicherheit in systemeigenem Code und .NET Framework-Code](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Sicherheit in .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>SharePoint-Sicherheit

- [Verwaltung und Sicherheit von SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [SharePoint-Sicherheitsressourcen Center](/sharepoint/dev/)

- [Sichern von Webparts in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Verbessern der Webanwendungs Sicherheit: Bedrohungen und Gegenmaßnahmen](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Allgemeine Sicherheit

- [Lebenszyklus der MSDN-Sicherheitsentwicklung](https://www.microsoft.com/msrc?rtc=1)

- [Aufbauen von sicheren ASP.NET-Anwendungen: Authentifizierung, Autorisierung und sichere Kommunikation](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Weitere Informationen

- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)