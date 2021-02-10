---
title: Behandeln von Problemen mit der Sicherheit von Office
description: Hier finden Sie einige Tipps zum Lösen allgemeiner Probleme, die auftreten können, wenn Sie mit dem Sichern von Microsoft Office Lösungen arbeiten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04b68a8207dad1edf83462a8284a69c73c668006
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969203"
---
# <a name="troubleshoot-office-solution-security"></a>Behandeln von Problemen mit der Sicherheit von Office
  Dieses Thema enthält Tipps zum Lösen allgemeiner Probleme, die bei der Arbeit mit dem Sichern von Office-Lösungen auftreten können.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Vertrauenswürdige Lösungen können nicht von eingeschränkten Sites installiert werden.
 Benutzer können eine Lösung nicht von einem Webspeicherort installieren, wenn die Website in der Zone Eingeschränkte Sites von Internet Explorer aufgeführt ist. Dies gilt auch, wenn die Lösung mit einem vertrauenswürdigen Zertifikat signiert ist.

 Die URL des Bereitstellungs Manifests kann in eine von fünf Zonen kategorisiert werden:

- Arbeitsplatz

- Internet

- Lokales Intranet

- Vertrauenswürdige Sites

- Eingeschränkte Websites

  Wenn der Speicherort des Bereitstellungs Manifests der Zone der eingeschränkten Sites zugewiesen wurde, wird [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] die Lösung von nicht installiert. Wenn der Speicherort bekannt ist und als vertrauenswürdig eingestuft werden kann, kann der Benutzer den Speicherort aus der Zone der eingeschränkten Sites entfernen und die Lösung installieren. Informationen zum Verwalten von Zonen finden Sie unter [Konfigurieren von ClickOnce-vertrauenswürdigen Verlegern](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Lösungen können nicht von Netzwerkdatei Freigaben oder webstandorten aus installiert werden, wenn die verstärkte Sicherheitskonfiguration für Internet Explorer oder Internet Explorer 7 installiert ist.
 Durch die verstärkte Sicherheitskonfiguration für Internet Explorer (IEESC) in Windows Server 2003 und höher sowie Internet Explorer 7 und höher wird die Möglichkeit der Benutzer das Durchsuchen des Internets erheblich eingeschränkt. Wenn Benutzer versuchen, Office-Projektmappen über eine Netzwerkdatei Freigabe oder einen Webspeicherort zu installieren, erhalten Sie möglicherweise die folgende Fehlermeldung: "die angepasste Funktionalität in dieser Anwendung funktioniert nicht, da das zum Signieren des Bereitstellungs Manifests für *SolutionName* verwendete Zertifikat nicht vertrauenswürdig ist. Wenden Sie sich für weitere Unterstützung an Ihren Administrator. "

 Wenn bei IEESC und Internet Explorer 7 und höher die URL des Bereitstellungs Manifests in der Zone "Internet" kategorisiert wird, muss das Manifest über ein Zertifikat von einem vertrauenswürdigen Herausgeber verfügen, oder die Lösung kann nicht installiert werden. Ohne IEESC ist das Standardverhalten, den Endbenutzer aufzufordern, eine Vertrauens Entscheidung zu treffen.

 Um die Auswirkungen von IEESC und Internet Explorer 7 und höher zu verwalten, identifizieren Sie Websites und UNC-Pfade (Universal Naming Convention), denen Sie Vertrauen, und fügen Sie Sie einer vertrauenswürdigen Sicherheitszone (Lokales Intranet oder Vertrauenswürdige Sites) hinzu. Weitere Informationen zum Verwalten von Zonen finden Sie unter [Konfigurieren von ClickOnce-vertrauenswürdigen Verlegern](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Weitere Informationen
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Problembehandlung für Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
