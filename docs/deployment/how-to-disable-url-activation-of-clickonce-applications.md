---
title: Deaktivieren der URL-Aktivierung von ClickOnce-apps
description: Erfahren Sie, wie Sie den automatischen Start bei der Installation für Ihre ClickOnce-Anwendung deaktivieren, falls Sie möchten, dass Benutzer die Anwendung über das Startmenü starten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46e46278f5465de029aa9536744f51843397d743
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351231"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers

In der Regel wird eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Anwendung automatisch gestartet, sobald sie von einem Webserver installiert wurde. Aus Gründen der Sicherheit könnten Sie dieses Verhalten deaktivieren und Benutzer dazu auffordern, die Anwendung stattdessen über das Menü **Start** zu öffnen. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.

Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Es kann nicht für reine Onlineanwendungen verwendet werden, die nur über ihre URL gestartet werden können. Weitere Informationen zu den Unterschieden zwischen reinen Onlineanwendungen und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).

In diesem Verfahren wird das Windows Software Development Kit (SDK)-Tool MageUI.exe verwendet. Weitere Informationen zu diesem Tool finden Sie unter [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Sie können dieses Verfahren auch mit Visual Studio ausführen.

## <a name="procedure"></a>Vorgehensweise

### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung

1. Öffnen Sie Ihr Bereitstellungsmanifest in „MageUI.exe“. Wenn Sie noch keinen erstellt haben, führen Sie die Schritte in Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)aus.

2. Wählen Sie die Registerkarte **Bereitstellungsoptionen** aus.

3. Deaktivieren Sie das Kontrollkästchen **Anwendung nach dem Installieren automatisch ausführen**.

4. Speichern und signieren Sie das Manifest.

## <a name="see-also"></a>Weitere Informationen

- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)