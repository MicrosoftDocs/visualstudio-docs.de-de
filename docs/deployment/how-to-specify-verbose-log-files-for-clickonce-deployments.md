---
title: Angeben ausführlicher Protokolldateien (ClickOnce-bereit Stellungen)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54c90f6a544607e78dd8f294bfc307bc87377b70
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808710"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Vorgehensweise: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwaltet Aktivitätsprotokoll Dateien für alle bereit Stellungen. Diese Protokolle enthalten Dokument Details zum Installieren, initialisieren, aktualisieren und Deinstallieren einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. Um die Details zu erhöhen, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in diese Protokolldateien geschrieben werden, verwenden Sie den Registrierungs-Editor (*regedit.exe*), um den ausführlichkeits Grad anzugeben.

> [!CAUTION]
> Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, kann dies zu schwerwiegenden Problemen führen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich machen. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.

 Im folgenden Verfahren wird beschrieben, wie Sie den ausführlichkeits Grad für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Protokolldateien für den aktuellen Benutzer angeben. Entfernen Sie diesen Registrierungs Wert, um den ausführlichkeits Grad zu verringern.

### <a name="to-specify-verbose-log-files"></a>So geben Sie ausführliche Protokolldateien an

1. Öffnen Sie *Regedit.exe*.

2. Navigieren Sie zum Knoten **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment**.

3. Erstellen Sie ggf. einen neuen Zeichen folgen Wert mit dem Namen `LogVerbosityLevel` .

4. Legen Sie den Wert `LogVerbosityLevel` auf `1` fest.

## <a name="see-also"></a>Siehe auch
- [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)