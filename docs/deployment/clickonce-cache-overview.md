---
title: Übersicht über den ClickOnce-Cache | Microsoft-Dokumentation
description: Erfahren Sie mehr über den ClickOnce-Anwendungscache, der verborgene Verzeichnisse auf einem Client Computer einschließt, auf dem ClickOnce-Anwendungen gespeichert werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 12c14850717688b17caed2fbe7feb546e0ebdb6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936170"
---
# <a name="clickonce-cache-overview"></a>Übersicht über den ClickOnce-Cache
Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, unabhängig davon, ob Sie lokal installiert oder online gehostet werden, werden auf dem Client Computer in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs *Cache* gespeichert. Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Cache ist eine Familie versteckter Verzeichnisse im Verzeichnis "lokale Einstellungen" des Ordners "Dokumente und Einstellungen" des aktuellen Benutzers. Dieser Cache enthält alle Dateien der Anwendung, einschließlich der Assemblys, Konfigurationsdateien, Anwendungs-und Benutzereinstellungen und Datenverzeichnis. Der Cache ist auch dafür verantwortlich, das Datenverzeichnis der Anwendung auf die neueste Version zu migrieren. Weitere Informationen zur Datenmigration finden Sie unter [zugreifen auf lokale und Remote Daten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Durch die Bereitstellung eines einzelnen Speicher Orts für den Anwendungs Speicher [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] übernimmt die Aufgabe der Verwaltung der physischen Installation einer Anwendung vom Benutzer. Der Cache unterstützt auch das Isolieren von Anwendungen, indem die Assemblys und Datendateien für alle Anwendungen und ihre unterschiedlichen Versionen voneinander getrennt bleiben. Wenn Sie z. b. eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung aktualisieren, werden diese Version und ihre Datenressourcen mit ihren eigenen Verzeichnissen im Cache bereitgestellt.

## <a name="cache-storage-quota"></a>Cache Speicher Kontingent
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die online gehostet werden, werden in dem Umfang des Speicherplatzes beschränkt, den Sie durch ein Kontingent belegen können, das die Größe des [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Caches einschränkt. Die Cache Größe gilt für alle Online Anwendungen des Benutzers. eine einzelne teilweise vertrauenswürdige Online Anwendung ist darauf beschränkt, die Hälfte des Kontingent Platzes zu belegen. Installierte Anwendungen werden nicht durch die Cache Größe beschränkt und nicht für das Cache Limit gezählt. Für alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen behält der Cache nur die aktuelle Version und die zuvor installierte Version bei.

 Standardmäßig haben Client Computer 250 MB Speicher für Online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen. Datendateien werden nicht in Bezug auf diesen Grenzwert gezählt. Ein Systemadministrator kann dieses Kontingent auf einem bestimmten Client Computer vergrößern oder verkleinern, indem er den Registrierungsschlüssel **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB**. dabei handelt es sich um einen DWORD-Wert, der die Cache Größe in Kilobyte ausdrückt. Um z. b. die Cache Größe auf 50 MB zu reduzieren, ändern Sie diesen Wert in 51200.

## <a name="see-also"></a>Weitere Informationen
- [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)