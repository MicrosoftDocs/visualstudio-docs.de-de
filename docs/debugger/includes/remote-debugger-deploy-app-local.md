---
title: Bereitstellen in einem lokalen Ordner
description: Bereitstellen einer App in einem lokalen Ordner
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1d049bc8b74b83028e04fe92e7ce96f45907d042
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97762603"
---
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen** (für Web Forms **Web-App veröffentlichen**) aus.

    Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil**.

1. Wählen Sie im Dialogfeld **Veröffentlichen** die Option **Ordner** aus, klicken Sie auf **Durchsuchen**, und erstellen Sie den neuen Ordner **C:\Publish**.

    ![Screenshot des Dialogfelds „Veröffentlichungsziel auswählen“ in Visual Studio mit als Veröffentlichungsziel ausgewähltem Ordner „bin\Release\Publish“.](../media/remotedbg_publish_local.png)

    Wählen Sie für eine Web Forms-App im Dialogfeld „Veröffentlichen“ **Benutzerdefiniert** aus, geben Sie einen Profilnamen ein, und wählen Sie **OK** aus.

1. Klicken Sie in der Dropdownliste auf **Profil erstellen** (der Standardwert lautet **Veröffentlichen**).

1. Klicken Sie im Dialogfeld **Veröffentlichen** auf den Link **Einstellungen**, und wählen Sie dann die Registerkarte **Einstellungen** aus.

1. Legen Sie die Konfiguration auf **Debuggen** fest, wählen Sie **Alle vorhandenen Dateien vor der Veröffentlichung löschen** aus, und klicken Sie dann auf **Speichern**.

    > [!NOTE]
    > Wenn Sie einen Releasebuild verwenden, deaktivieren Sie beim Veröffentlichen das Debuggen in der Datei „Web.config“.

1. Klicken Sie auf **Veröffentlichen**.

    ![Screenshot der Registerkarte „Einstellungen“ im Dialogfeld „Veröffentlichen“. Die „Konfiguration“ ist auf „Debuggen“ festgelegt, und die Schaltfläche „Veröffentlichen“ ist ausgewählt.](../media/remotedbg_publish_debug_config.png)

    Die Anwendung veröffentlicht eine **Debugkonfiguration** des Projekts im lokalen Ordner. Der Status wird im Fenster „Ausgabe“ angezeigt.

1. Kopieren Sie das ASP.NET-Projektverzeichnis vom Visual Studio-Computer in ein für die ASP.NET-App konfiguriertes lokales Verzeichnis (in diesem Beispiel **C:\Publish**) auf dem Windows Server-Computer. In diesem Tutorial wird davon ausgegangen, dass Sie den Kopiervorgang manuell durchführen, Sie können aber auch andere Tools wie PowerShell, XCopy oder Robocopy verwenden.

    > [!CAUTION]
    > Wenn Sie Änderungen am Code vornehmen müssen, müssen Sie die Veröffentlichung erneut ausführen und diesen Schritt wiederholen. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.    Wenn Sie dies nicht beachten, wird in Visual Studio beim Debuggen des Prozesses die Warnung `cannot find or open the PDB file` angezeigt.

1. Überprüfen Sie auf dem Windows-Server, ob Sie die App ordnungsgemäß ausführen können, indem Sie die App in Ihrem Browser öffnen.

    Wenn die App nicht ordnungsgemäß ausgeführt wird, liegt möglicherweise ein Konflikt zwischen der auf dem Server und der auf dem Visual Studio-Computer installierten ASP.NET-Version vor, oder es liegt ein Problem bei der IIS- oder Websitekonfiguration vor. Überprüfen Sie die vorherigen Schritte.
