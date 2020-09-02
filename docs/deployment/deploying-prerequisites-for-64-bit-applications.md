---
title: Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c70b58577f8aa6e391215658afb7f8fa43c9bb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928886"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen
Die ClickOnce-Bereitstellung unterstützt die Installation von Anwendungen auf 64-Bit-Plattformen. Die Zielplattformen sind **x86** für 32-Bit-Plattformen, **x64** für Computer, die die Anweisungssets AMD64 und EM64T unterstützen, und **Itanium** für 64-Bit-Itanium-Prozessoren.

## <a name="prerequisites"></a>Voraussetzungen
 In der folgenden Tabelle sind die verteilbaren Komponenten aufgeführt, die Sie als erforderliche Komponenten für die Installation Ihrer 64-Bit-Anwendung verwenden können.

 Wenn Sie eine erforderliche Komponente auswählen, für die keine 64-Bit-Komponenten vorhanden sind, wird möglicherweise eine Warnung angezeigt, die darauf hinweist, dass die ausgewählten Pakete für die 64-Bit-Plattform nicht verfügbar sind.

| Verteilbare Komponente | x64-Unterstützung | IA64-Unterstützung |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Ja | Nein |
| Visual C++ 2010-Laufzeitbibliotheken (IA64) | Nein | Ja |
| Visual C++ 2010-Laufzeitbibliotheken (x64) | Ja | Nein |
| Microsoft .NET Framework 4 (x86 und x64) | Ja | |
| Microsoft .NET Framework 4 Client Profile (x86 und x64) | Ja | |

## <a name="see-also"></a>Weitere Informationen
- [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md)
- [Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [64-Bit-Anwendungen](/dotnet/framework/64-bit-apps)