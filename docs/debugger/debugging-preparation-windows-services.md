---
title: Vorbereiten des Debuggens von Windows-Diensten | Microsoft-Dokumentation
description: Bereiten Sie das Debuggen von Windows-Diensten vor. Dabei handelt es sich um Programme, die unter Windows in Visual Studio im Hintergrund ausgeführt werden.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdf82b708440cb3201c5d05bd936c7f7d9c30729
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872390"
---
# <a name="debugging-preparation-windows-services"></a>Vorbereitung des Debugvorgangs: Windows-Dienste
Ein Windows-Dienst ist ein Programm, das unter Microsoft Windows im Hintergrund ausgeführt wird. Beispiele hierfür sind der Telnet-Dienst und der Windows-Zeitdienst, durch den die auf dem Computer angezeigte Systemuhrzeit aktualisiert wird. Da ein Windows-Dienst innerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht lauffähig ist, muss er im Kontext des Dienststeuerungs-Managers ausgeführt werden. Weitere Informationen finden Sie unter [Erstellen von Windows-Diensten](/dotnet/framework/windows-services/how-to-create-windows-services), [Debuggen von Windows-Dienstanwendungen](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) und [Entwickeln von Windows-Dienstanwendungen](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Projekteinstellungen für C#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to: Debuggen der OnStart-Methode](../debugger/how-to-debug-the-onstart-method.md)