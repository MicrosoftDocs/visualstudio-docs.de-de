---
title: Verwalten von VSPackages | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Verwalten von VSPackages, damit Sie wissen, wann Sie einfach die von Visual Studio bereitgestellte Standard Verwaltung von VSPackage verwenden können und wie und wann Sie angepasst werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a040777671a5d6a4378e9b2ad68b2ffa2fabaeb
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615739"
---
# <a name="manage-vspackages"></a>Verwalten von VSPackages
In den meisten Fällen müssen Sie sich keine Gedanken über die Verwaltung von VSPackages machen, da die Projekt-und Element Vorlagen das Paket automatisch registrieren und laden. In einigen Fällen müssen Sie jedoch vielleicht etwas mehr lernen, um das Paket zu verwalten.

## <a name="use-the-experimental-instance"></a>Verwenden Sie die experimentelle Instanz.
 Weitere Informationen über die experimentelle Instanz finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrieren und Aufheben der Registrierung von VSPackages
 Informationen zum Registrieren und Aufheben der Registrierung von VSPackages und anderen Erweiterungs Typen finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>VSPackage laden
 VSPackages können auf "AutoLoad" festgelegt werden, wenn eine bestimmte cmduicontext-GUID aktiviert ist. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Verwenden von asyncpackage zum Laden von VSPackages im Hintergrund
 Die- `AsyncPackage` Klasse ermöglicht das Laden von Paketen in einem Hintergrund Thread für eine bessere Reaktionsfähigkeit der Benutzeroberfläche in Visual Studio. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von asyncpackage zum Laden von VSPackages im Hintergrund](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Regelbasierter UI-Kontext für Erweiterungen
 Mithilfe von regelbasierten UI-Kontexten können Erweiterungs Autoren die genauen Bedingungen definieren, unter denen ein UI-Kontext aktiviert und zugeordnete VSPackages geladen werden. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des regelbasierten UI-Kontexts für Visual Studio-Erweiterungen](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Leistung der Diagnoseerweiterung
Erweiterungen können sich auf das Starten und die Leistung der Projekt Mappe auswirken. Erfahren Sie, wie die Auswirkungen auf die Visual Studio-Erweiterung berechnet werden und wie Sie lokal analysiert werden kann, um zu testen, ob eine Erweiterung als Leistungs Beeinträchtigung der Erweiterung angezeigt wird. Weitere Informationen finden Sie unter Gewusst [wie: Diagnostizieren der Erweiterungs Leistung](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Problembehandlung bei VSPackages
 Hier finden Sie die Techniken zur Problembehandlung von VSPackages, die nicht geladen werden oder Fehler auftreten: Problembehandlung für [VSPackages](../extensibility/troubleshooting-vspackages.md) .

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
