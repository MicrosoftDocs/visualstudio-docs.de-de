---
title: 'Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen'
description: Erfahren Sie, wie Sie einen Entwicklungs Computer so konfigurieren, dass Sie die Microsoft Office Entwicklertools in Visual Studio verwenden können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d6504ac9682c4cd4e7691c651f1ee5c2b3818bf2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844308"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen
  Um einen Entwicklungscomputer so zu konfigurieren, dass Sie die Microsoft Office Developer Tools in Visual Studio verwenden können, befolgen Sie die Anweisungen in diesem Thema. Sie müssen Administratorrechte auf dem Entwicklungscomputer besitzen, um diese Schritte auszuführen.

### <a name="to-configure-the-development-computer"></a>So konfigurieren Sie den Entwicklungscomputer

1. Installieren Sie eine Version von Visual Studio, in der die Office Developer Tools enthalten sind. Die Office Developer-Tools werden standardmäßig installiert. Wenn Sie die Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, stellen Sie sicher, dass **Microsoft Office Entwicklertools** während des Setups ausgewählt wird. Weitere Informationen zu den Versionen von Visual Studio, die die Office-Entwicklertools enthalten, finden [Sie unter Konfigurieren eines Computers zum Entwickeln von Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)-Projektmappen.

2. Installieren Sie eine Version von Office, die von den Office Developer Tools in Visual Studio unterstützt wird. Weitere Informationen finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)-Projektmappen.

     Stellen Sie sicher, dass Sie auch die PIAs für die installierte Office-Version installieren. Die PIAs werden standardmäßig mit Office installiert. Wenn Sie Office-Setup ändern, stellen Sie sicher, dass die Funktion **.net-Programmier Unterstützung** für die Anwendungen ausgewählt ist, auf die Sie abzielen möchten.

3. Wenn Sie über eine englische Version von Visual Studio verfügen, aber nicht englische Einstellungen für Windows verwenden, können Sie das [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Language Pack installieren, um [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Meldungen in derselben Sprache wie Windows anzuzeigen. Bei nicht englischen Versionen von Visual Studio wird automatisch das Sprachpaket installiert. Das Language Pack ist im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=54246)verfügbar.

## <a name="see-also"></a>Siehe auch

- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Vorgehensweise: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Gewusst wie: Installieren von primären Interop-Assemblys in Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
