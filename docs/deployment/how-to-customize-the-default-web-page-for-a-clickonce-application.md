---
title: Anpassen der Standard Webseite für die ClickOnce-Anwendung
description: Erfahren Sie mehr über die Webseite, die generiert wird, wenn Sie eine ClickOnce-Anwendung im Web veröffentlichen, die den Namen der Anwendung und weitere Informationen enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbda4558622c2e244071a218d3d5e42196460113
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351205"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Vorgehensweise: Anpassen der Standardwebseite für eine ClickOnce-Anwendung
Wenn eine ClickOnce-Anwendung im Web veröffentlicht wird, wird automatisch eine Webseite generiert und zusammen mit der Anwendung veröffentlicht. Die Standardseite enthält den Namen der Anwendung und Links zum Installieren der Anwendung, Installieren der erforderlichen Komponenten oder zugreifen auf die Hilfe auf MSDN.

> [!NOTE]
> Die tatsächlichen Links, die auf der Seite angezeigt werden, hängen von dem Computer ab, auf dem die Seite angezeigt wird, und von den Voraussetzungen, die Sie einschließen.

 Der Standardname für die Webseite ist *Publish.htm*. der Name kann im **Projekt-Designer** geändert werden. Weitere Informationen finden Sie unter Gewusst [wie: Angeben einer Veröffentlichungs Seite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Die *Publish.htm* Webseite wird nur veröffentlicht, wenn eine neuere Version erkannt wird.

> [!NOTE]
> Änderungen, die Sie an Ihren **Veröffentlichungs** Einstellungen vornehmen, wirken sich nicht auf die *Publish.htm* Seite aus, mit einer Ausnahme: Wenn Sie nach der ersten Veröffentlichung erforderliche Komponenten hinzufügen oder entfernen, ist die Liste der Voraussetzungen nicht mehr korrekt. Sie müssen den Text für den erforderlichen Link bearbeiten, um die Änderungen widerzuspiegeln.

### <a name="to-customize-the-publish-web-page"></a>So passen Sie die Webseite zum Veröffentlichen an

1. Veröffentlichen Sie Ihre ClickOnce-Anwendung an einem Webspeicherort. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Öffnen Sie auf dem Webserver die Datei *Publish.htm* im Visual Web Designer oder einem anderen HTML-Editor.

3. Passen Sie die Seite wie gewünscht an, und speichern Sie Sie.

4. Optional. Um zu verhindern, dass Visual Studio die angepasste Veröffentlichungs Webseite überschreibt, deaktivieren Sie im Dialogfeld **Veröffentlichungs Optionen die Option** **Bereitstellung automatisch generieren nach jeder Veröffentlichung** .

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)