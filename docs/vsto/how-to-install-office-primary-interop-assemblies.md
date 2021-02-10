---
title: 'Gewusst wie: Installieren von primären Interop-Assemblys in Office'
description: Erfahren Sie, wie Sie die Microsoft Office primären Interop-Assemblys (PIAs) bei der Installation von Office installieren.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 432b2a74eb7ea4753cd110956c9dc9313e1a5d6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934818"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Gewusst wie: Installieren von primären Interop-Assemblys in Office
  Installieren Sie die primären Interop-Assemblys (PIAs) für Microsoft Office bei der Installation von Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Zum Installieren der PIAs bei der Installation von Office

1. Stellen Sie sicher, dass Sie über eine Version von .NET Framework verfügen, die nicht älter als Version 2.0 ist.

2. Installieren Sie Microsoft Office, und stellen Sie sicher, dass die Funktion **.net-Programmier Unterstützung** für die Anwendungen ausgewählt ist, die Sie erweitern möchten (dieses Feature ist in der Standardinstallation enthalten).

    > [!WARNING]
    > In der Standardeinstellung werden die PIA in Ihre Lösung eingebettet, wenn Sie Sie erstellen, damit Sie PIAs nicht als Voraussetzung für die Verwendung des VSTO-Add-Ins oder der Anpassung an Benutzer verteilen müssen.

## <a name="see-also"></a>Weitere Informationen
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Gewusst wie: Ausrichten von Office-Anwendungen über primäre Interop-Assemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Vorgehensweise: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
