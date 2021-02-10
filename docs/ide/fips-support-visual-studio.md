---
title: Visual Studio-Unterstützung für FIPS
titleSuffix: ''
description: Erfahren Sie, wie Visual Studio den Betriebsmodus für Windows, Azure und .NET gemäß Federal Information Processing Standard Publication 140-2 unterstützt.
ms.custom: SEO-VS-2020
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d6cb0d2bbcb1ec1d13f5916a7c2b1cd97824fb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945538"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Visual Studio-Unterstützung des FIPS 140-2-konformen Betriebsmodus

Ab [Version 16.4](/visualstudio/releases/2019/release-notes-v16.4/) unterstützt Visual Studio 2019 den Betriebsmodus für Windows, Azure und .NET gemäß FIPS 140-2 (Federal Information Processing Standard). Ab [Version 16.5](/visualstudio/releases/2019/release-notes-archive-v16.5) unterstützt Visual Studio den Betriebsmodus gemäß FIPS 140-2 auch bei der Entwicklung von [C++-Anwendungen für Linux-Remotesysteme](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

[Installieren Sie .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48), und aktivieren Sie die Gruppenrichtlinieneinstellung **Systemkryptografie: FIPS-konformen Algorithmus für Verschlüsselung, Hashing und Signatur verwenden**, um den FIPS 140-2-konformen Betriebsmodus für Visual Studio zu konfigurieren.

Weitere Informationen über der den FIPS 140-2-konformen Betriebsmodus und dessen Aktivierung finden Sie unter [FIPS 140-2-Validierung](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Die Tools, die Sie zum Entwickeln von Apps für nicht von Microsoft stammende Plattformen wie iOS oder Android verwenden würden, nutzen möglicherweise keine FIPS-konformen Algorithmen. In Visual Studio oder Erweiterungen enthaltene Software von Drittanbietern, die Sie möglicherweise installieren, nutzen möglicherweise auch keine FIPS-konformen Algorithmen. Bei der Entwicklung von [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/)-Lösungen wird der FIPS 140-2-konforme Betriebsmodus nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über den FIPS 140-2-konformen Betriebsmodus für Visual Studio und andere Produkte und Dienste von Microsoft finden Sie unter folgenden Links:

- [Visual Studio: Einrichten einer FIPS-konformen sicheren Linux-Remoteentwicklung mit C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Systemkryptografie und Verwenden FIPS-konformer Algorithmen für Verschlüsselung, Hashing und Signierung](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: FIPS-Konformität](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Siehe auch

[Sichern von Anwendungen](securing-applications.md)