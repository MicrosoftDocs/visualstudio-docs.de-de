---
title: Bewährte Methoden für die Sicherheit in VSPackages | Microsoft-Dokumentation
description: Erfahren Sie mehr über die bewährten Methoden für die Sicherheit in einem VSPackage, die grundlegende Einheit der Sicherheit und Bereitstellung für eine Visual Studio-Anwendung.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4e706a115e8cec3b13ef58cf6cdef61912f5810
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905992"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bewährte Methoden für die Sicherheit in VSPackages
Um das auf dem Computer zu installieren [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , müssen Sie in einem Kontext mit Administrator Anmelde Informationen ausgeführt werden. Die grundlegende Einheit der Sicherheit und Bereitstellung einer- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anwendung ist das [VSPackage](../../extensibility/internals/vspackages.md). Ein VSPackage muss mithilfe von registriert werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , wofür auch administrative Anmelde Informationen erforderlich sind.

 Administratoren verfügen über vollständige Berechtigungen zum Schreiben in die Registrierung und das Dateisystem sowie zum Ausführen von Code. Sie müssen über diese Berechtigungen verfügen, um ein VSPackage zu entwickeln, bereitzustellen oder zu installieren.

 Sobald Sie installiert ist, wird ein VSPackage als voll vertrauenswürdig eingestuft. Aufgrund dieses hohen Berechtigungs Niveaus, das einem VSPackage zugeordnet ist, ist es möglich, versehentlich ein VSPackage mit böswilliger Absicht zu installieren.

 Benutzer sollten sicherstellen, dass Sie VSPackages nur aus vertrauenswürdigen Quellen installieren. Unternehmen, die VSPackages entwickeln, sollten diese stark benennen und signieren, um dem Benutzer zu gewährleisten, dass Manipulationen verhindert werden. Unternehmen, die VSPackages entwickeln, sollten Ihre externen Abhängigkeiten (z. b. Webdienste und Remote Installation) untersuchen, um Sicherheitsprobleme auszuwerten und zu beheben.

 Weitere Informationen finden Sie unter [Richtlinien für sicheres Programmieren für die .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Weitere Informationen
- [Add-in-Sicherheit](/previous-versions/1326zbk3(v=vs.140))
- [DDEX-Sicherheit](/previous-versions/bb163703(v=vs.140))