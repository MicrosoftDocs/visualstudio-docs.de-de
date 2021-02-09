---
title: Geben Sie an, wo Dateien kopiert werden sollen. Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Eigenschaft Veröffentlichungsort für eine ClickOnce-Anwendung festlegen, die den Speicherort angibt, an dem die Anwendungs Dateien und das Manifest abgelegt werden.
ms.custom:
- SEO-VS-2020
- seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50f3e5d8500e57dd336919a5da58af094db97169
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887418"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Vorgehensweise: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert
Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden. Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP-Server handeln.

 Sie können die Eigenschaft `Publish Location` auf der Seite **Veröffentlichen** des **Projekt-Designers** oder mit dem Webpublishing-Assistenten festlegen. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.

### <a name="to-specify-a-publishing-location"></a>So legen Sie einen Veröffentlichungsort fest

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Geben Sie in das Feld **Ort der Veröffentlichung** den Ort für die Veröffentlichung in einem der folgenden Formate ein:

   - Geben Sie zum Veröffentlichen in einer Dateifreigabe oder einem Datenträger Pfad den Pfad entweder mithilfe eines UNC-Pfads (*\\ \server\applicationname*) oder eines Dateipfads (*c:\Deploy\ApplicationName*) ein.

   - Um auf einem FTP-Server zu veröffentlichen, geben Sie den Pfad im Format <em>FTP://FTP.Microsoft.com/ \<ApplicationName> </em>ein.

     Beachten Sie, dass im Feld **Veröffentlichungsort** der Text vorhanden sein muss, damit die Schaltfläche zum Durchsuchen (**..**.) funktioniert.

## <a name="see-also"></a>Weitere Informationen
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)