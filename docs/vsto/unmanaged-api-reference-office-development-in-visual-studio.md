---
title: Referenz zur nicht verwalteten API (Office-Entwicklung in Visual Studio)
description: Die Referenz zur nicht verwalteten API wird zur Unterstützung von laden verwalteten VSTO-Add-Ins verwendet. Sie können auch eine eigene VSTO-Add-in-Lade Komponente erstellen, indem Sie diese Schnittstelle implementieren.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cac9e2d01b47e0088543aeabcaeff30853314157
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908555"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referenz zur nicht verwalteten API (Office-Entwicklung in Visual Studio)

Ab dem 2007-Microsoft Office System verwenden Office-Anwendungen die [Schnittstelle IManagedAddin Interface](../vsto/imanagedaddin-interface.md) , um eine VSTO-Add-in-Lade Komponente aufzurufen, die im Lieferumfang von enthalten ist [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Diese Komponente wird zur Unterstützung von laden verwalteten VSTO-Add-Ins verwendet. Sie können eine eigene VSTO-Add-in-Lade Komponente erstellen, indem Sie diese Schnittstelle implementieren.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>In diesem Abschnitt

[IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md)

Eine COM-Schnittstelle, die Sie implementieren können, um verwaltete VSTO-Add-Ins in Office-Anwendungen zu laden und zu entladen.
