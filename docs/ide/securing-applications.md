---
title: Sicherheit
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e02900c96991a402d7ea7b789a47f8f2dea447c3
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91781016"
---
# <a name="secure-applications"></a>Sichern von Anwendungen

Sicherheitsüberlegungen sollten vom Entwurf bis zur Bereitstellung in alle Aspekte der Anwendungsentwicklung einfließen. Beginnen Sie damit, Visual Studio so sicher wie möglich auszuführen. Weitere Informationen finden Sie unter [Benutzerberechtigungen](../ide/user-permissions-and-visual-studio.md).

Damit Sie sichere Anwendungen effektiv entwickeln können, benötigen Sie grundlegende Kenntnisse über die Sicherheitskonzepte und Sicherheitsfunktionen der Plattformen, für die Anwendungen entwickelt werden. Außerdem sollten Kenntnisse im Bereich sicherer Codierungstechniken vorhanden sein.

## <a name="code-for-security"></a>Codieren im Hinblick auf Sicherheit

Die meisten Codierungsfehler, die Sicherheitsmängel verursachen, entstehen, weil Entwickler bei Benutzereingaben von falschen Voraussetzungen ausgehen oder nicht vollständig mit der Plattform vertraut sind, für die die Anwendung entwickelt wird.

- Unter [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines) werden die verschiedenen Methoden zum Entwerfen von Code beschrieben, damit dieser mit dem Sicherheitssystem funktioniert.
- Unter [Empfohlene Vorgehensweisen bezüglich der Sicherheit in C++](/cpp/top/security-best-practices-for-cpp) enthält Informationen über Sicherheitstools und bewährte Methoden für C++-Entwickler.

## <a name="build-for-security"></a>Erstellen im Hinblick auf Sicherheit

Die Sicherheit ist im Buildprozess auch ein wichtiger Aspekt. Einige zusätzliche Schritte können die Sicherheit einer bereitgestellten App verbessern und nicht autorisiertes Reverse Engineering, Spoofing oder andere Angriffe verhindern:

- [Dotfuscator](dotfuscator/index.md) ist kostenlos und schützt .NET-Assemblys vor Reverse Engineering und nicht autorisierter Verwendung (z.B. nicht autorisiertes Debuggen).
- Das [Signieren mit starkem Namen](managing-assembly-and-manifest-signing.md) kann zum eindeutigen Identifizieren von Softwarekomponenten verwendet werden kann und das Spoofing von Namen verhindern.

## <a name="see-also"></a>Weitere Informationen

- [Sicherheit in .NET](/dotnet/standard/security/index)
- [Azure-Sicherheit](/azure/security/)
- [Windows 10 Mobile security guide (Sicherheitshandbuch für Windows 10 Mobile)](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova platform security features (Sicherheitsfeatures für die Apache Cordova-Plattform)](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017&preserve-view=true)
- [ASP.NET Core-Sicherheit](/aspnet/core/security/?view=aspnetcore-2.1&preserve-view=true)
- [Sicherheit in Windows Forms](/dotnet/framework/winforms/windows-forms-security)
