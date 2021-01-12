---
title: Durchsuchen des Speichers zum Hochladen von Daten
description: Hier erfahren Sie, wie Sie den gesamten Speicher auf dem Remotecomputer oder der Azure-Dateifreigabe durchsuchen können, um das Hochladen von Daten oder das Herunterladen von Modellen und Protokollen zu ermöglichen.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: b145c4acf4047356b8996d09d746679900314f1b
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726565"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Durchsuchen des Speichers, um Daten hochzuladen oder Modelle und Protokolle herunterzuladen

Sie können den gesamten Speicher auf dem Remotecomputer oder der Azure-Dateifreigabe durchsuchen, um das Hochladen von Daten oder das Herunterladen von Modellen und Protokollen zu ermöglichen. Wenn Sie alternativ auf Protokolle und Auftragsausgaben für einen bestimmten Auftrag zugreifen möchten, können Sie dies auch im Auftragsbrowser tun.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>So greifen Sie auf alle Daten auf dem Remotecomputer oder der Dateifreigabe zu

1. Öffnen Sie den **Server-Explorer**.
2. Erweitern Sie den Remotecomputer oder den Computekontext „Batch AI“.
3. Klicken Sie mit der rechten Maustaste auf **Speicher** und dann auf **Durchsuchen**.

    ![Screenshot: Server-Explorer mit erweitertem Ordner für Remotecomputer, hervorgehobenem Speicher in der Ordnerstruktur und der ausgewählten Option „Durchsuchen“ im Kontextmenü](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>So greifen Sie auf auftragsspezifische Daten auf dem Remotecomputer oder der Dateifreigabe zu

1. Öffnen Sie den [Auftragsverlauf](job-details.md).
2. Wählen Sie den Auftrag aus.
3. Klicken Sie auf **Arbeitsordner** oder auf **StdOut/Stderr**, um schnell auf diese wichtigen Protokolldateien zuzugreifen.

    ![Screenshot: Auftragsbrowserfenster im Server-Explorer mit ausgewähltem Auftrag „train_mnist“ und ausgewähltem Link „Arbeitsordner“ unter „Auftragsdetails“](media/manage-storage/job-workingfolder.png)
