---
title: Befehls Verträge in Interop-Assemblys | Microsoft-Dokumentation
description: Erfahren Sie mehr über den grundlegenden Vertrag für die Verarbeitung von Befehlen über die Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget-Schnittstelle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ed9435f4f0618ee0c0f4bc47cdb21e2cbf92f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940124"
---
# <a name="command-contracts-in-interop-assemblies"></a>Befehls Verträge in Interop-Assemblys
Der grundlegende Vertrag für die Handhabung von Befehlen über die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle besteht darin, dass die Umgebung die-Methode aufruft, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> um zu bestimmen, ob der Befehl unterstützt wird, und, falls unterstützt, seinen Zustand und Text zu bestimmen. Dann ruft die Umgebung die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode auf, um den Befehl auszuführen.

 Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode wird für alle Befehle identisch behandelt. Die weitere Kommunikation, falls erforderlich (z. b. mit Dropdown Listen), wird durch Aufrufen der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode mit den entsprechenden Parametern verwaltet. Die Interpretation dieser Parameter hängt von dem angegebenen Befehl ab.

 Wenn das Befehls Ziel Werte im Output-Parameter zurückgibt, ist der Aufrufer immer dafür verantwortlich, alle zugeordneten Ressourcen freizugeben. Da dieser Parameter eine Variante ist, werden die Ressourcen durch das Löschen der Variante freigegeben.

 In Fällen, in denen-Befehle innerhalb eines Hierarchie Fensters funktionieren müssen, muss die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle verwendet werden. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> -Schnittstelle verfügt über einen ähnlichen Vertrag mit ähnlichen Methoden: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehls Routing in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Befehls Implementierung](../../extensibility/internals/command-implementation.md)
