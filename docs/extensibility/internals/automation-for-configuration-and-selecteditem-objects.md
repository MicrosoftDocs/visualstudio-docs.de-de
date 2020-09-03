---
title: Automatisierung für Konfigurations-und SelectedItem-Objekte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709968"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für Konfigurations-und SelectedItem-Objekte

Sie können die Prozesse Build und ausgewähltes Element in Visual Studio automatisieren.

## <a name="automation-for-builds"></a>Automatisierung für Builds

Build oder Konfiguration verfügt über ein Automatisierungs Modell, das bei der Implementierung von bereitgestellt wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Weitere Informationen finden Sie unter [Grundlagen der Buildkonfigurationen](../../ide/understanding-build-configurations.md).

Wenn Sie ein VSPackage erstellen und Konfigurationsoptionen steuern möchten, müssen Sie das Automatisierungs Modell verwenden.

## <a name="automation-for-selecteditem"></a>Automatisierung für SelectedItem

Sie müssen keine Implementierung für das-Objekt bereitstellen, `SelectedItem` da Visual Studio eine Standard Implementierung enthält. Es ist jedoch möglich, das-Objekt zu implementieren, `SelectedItem` Wenn Sie dies bevorzugen. Sie müssen ein-Objekt implementieren, das die `SelectedItem` -Schnittstelle enthält, und eine Antwort auf einen-aufrufbefehl zurückgeben, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> wobei `VSITEMID` auf __VSHPROPID festgelegt ist [. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Zum Automatisierungs Modell beitragen](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)
