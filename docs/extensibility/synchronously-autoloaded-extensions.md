---
title: Synchron automatisch geladene Erweiterungen
description: Erfahren Sie mehr über das Standardverhalten ab Visual Studio 2019, das synchron zu überlappenden Paketen aus einer beliebigen Erweiterung blockiert.
ms.custom: SEO-VS-2020
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 506c098f1f385ddf39c5d000f4571a8ee92c09fc
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715443"
---
# <a name="synchronously-autoloaded-extensions"></a>Synchron automatisch geladene Erweiterungen

Synchron authentifikaterte Erweiterungen haben eine negative Auswirkung auf die Leistung von Visual Studio und sollten stattdessen für die Verwendung von asynchroner AutoLoad konvertiert werden. Standardmäßig blockiert Visual Studio 2019 synchron authentifiziererte Pakete aus einer beliebigen Erweiterung und benachrichtigt den Benutzer.

![Warnung zur Erweiterungs Kompatibilität](media/extension-compatibility-warning-16-1.png.png)

Ihre Möglichkeiten:

- Klicken Sie auf **synchrone** automatische Authentifizierung zulassen, um Erweiterungen von AutoLoad zuzulassen. Um diese Einstellung in Visual Studio-Optionen zu ändern, klicken Sie auf Umgebung und dann auf Erweiterungen, und aktivieren Sie dann das Kontrollkästchen synchrone Authentifizierung von Erweiterungen zulassen. 

- Klicken Sie auf **Leistung verwalten** , um das Dialogfeld " [Performance Manager](#performance-manager-dialog) " zu öffnen, das Leistungsprobleme bei Erweiterungen und Tool Fenstern anzeigt.

- Klicken Sie auf **Diese Meldung für aktuelle Erweiterungen nicht anzeigen** , um die Benachrichtigung zu verwerfen und zukünftige Benachrichtigungen von vorhandenen installierten Erweiterungen zu verhindern. Wenn Sie eine neue Erweiterung hinzufügen, die synchron synchronisiert wird, wird diese Benachrichtigung erneut angezeigt. Sie erhalten weiterhin Benachrichtigungen zu anderen Visual Studio-Features.

## <a name="performance-manager-dialog"></a>Dialogfeld

![Dialogfeld](media/performance-manager.png)

Alle Erweiterungen, die alle Pakete in Benutzersitzungen synchron geladen haben, werden auf der Registerkarte **Veraltete APIs** angezeigt.

* Klicken Sie auf **Weitere Informationen zu diesem Problem** , um weitere Informationen zu den veralteten APIs zu erhalten.
* Wenden Sie sich für den Migrations Fortschritt an Ihre Erweiterungs Anbieter.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Angeben von synchronen AutoLoad-Einstellungen mithilfe von Gruppenrichtlinien

Administratoren können eine Gruppenrichtlinie aktivieren, um synchrone AutoLoad zuzulassen. Legen Sie hierzu eine registrierungsbasierte Richtlinie für den folgenden Schlüssel fest:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Eintrag = **zulässig**

Wert = (DWORD)
* **0** ist synchrone AutoLoad unzulässig.
* **1** ist synchrone AutoLoad zulässig

## <a name="extension-authors"></a>Erweiterungs Autoren
Erweiterungs Autoren finden Anweisungen zum Migrieren von Paketen zu asynchroner Authentifizierung bei der [Migration zu asyncpackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Weitere Informationen
Weitere Informationen zu synchronen AutoLoad-Einstellungen in Visual Studio 2019 finden Sie auf der Seite [synchrones Authentifizierungs Verhalten](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) .
