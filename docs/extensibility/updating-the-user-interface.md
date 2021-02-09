---
title: Aktualisieren der Benutzeroberfläche | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Code hinzufügen, um die Benutzeroberfläche zu aktualisieren, nachdem Sie einen neuen Befehl in Ihrem VSPackage implementiert haben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fd088d6887e7c7b60ea5a4101de050149583c5a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893450"
---
# <a name="updating-the-user-interface"></a>Aktualisieren der Benutzeroberfläche
Nachdem Sie einen Befehl implementiert haben, können Sie Code hinzufügen, um die Benutzeroberfläche mit dem Zustand ihrer neuen Befehle zu aktualisieren.

 In einer typischen Win32-Anwendung kann der Befehlssatz fortlaufend abgepolgt werden, und der Zustand einzelner Befehle kann angepasst werden, wenn Sie vom Benutzer angezeigt werden. Da die Shell jedoch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine unbegrenzte Anzahl von VSPackages hosten kann, kann das umfangreiche abrufen die Reaktionsfähigkeit verringern, insbesondere das Abrufen von Interop-Assemblys zwischen verwaltetem Code und com.

### <a name="to-update-the-ui"></a>So aktualisieren Sie die Benutzeroberfläche

1. Führen Sie einen der folgenden Schritte aus:

    - Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> -Methode auf.

         Eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle kann <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> wie folgt vom Dienst abgerufen werden.

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         Wenn der-Parameter von ungleich <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 0 (NULL `TRUE` ) ist, wird das Update synchron und sofort durchgeführt. Es wird empfohlen, NULL ( `FALSE` ) für diesen Parameter zu übergeben, um eine gute Leistung zu gewährleisten. Wenn Sie das Caching vermeiden möchten, wenden Sie das- `DontCache` Flag an, wenn Sie den Befehl in der vsct-Datei erstellen. Verwenden Sie das Flag trotzdem vorsichtig, oder die Leistung kann abnehmen. Weitere Informationen zu Befehlsflags finden Sie in der Dokumentation zum [Befehlsflag](../extensibility/command-flag-element.md) .

    - In VSPackages, die ein ActiveX-Steuerelement mithilfe des direkten Aktivierungs Modells in einem Fenster hosten, ist es möglicherweise bequemer, die-Methode zu verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> . Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> -Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> -Schnittstelle und die- <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> Methode in der- <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Schnittstelle sind funktional äquivalent. Beide bewirken, dass die Umgebung den Status aller Befehle erneut abfragt. In der Regel wird ein Update nicht sofort ausgeführt. Stattdessen wird ein Update bis zur Leerlaufzeit verzögert. Die Shell speichert den Befehls Zustand zwischen, um eine gute Leistung zu gewährleisten. Wenn Sie das Caching vermeiden möchten, wenden Sie das- `DontCache` Flag an, wenn Sie den Befehl in der vsct-Datei erstellen. Verwenden Sie das Flag trotzdem vorsichtig, da sich die Leistung möglicherweise verringert.

         Beachten Sie, dass Sie die-Schnittstelle abrufen können, <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> indem Sie die- `QueryInterface` Methode für ein <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> Objekt aufrufen oder indem Sie die-Schnittstelle vom <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> Dienst abrufen.

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementierung](../extensibility/internals/command-implementation.md)
