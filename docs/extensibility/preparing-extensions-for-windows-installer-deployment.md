---
title: Vorbereiten von Erweiterungen für Windows Installer Bereitstellung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Projekt vorbereiten, dessen Standardausgabe ein VSIX-Paket für die Einbindung in ein Setup-Projekt ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba494af91d3d40720493b27e7381660ece3fba69
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97862900"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Vorbereiten von Erweiterungen für Windows Installer Bereitstellung
Zum Bereitstellen eines VSIX-Pakets können Sie kein Windows Installer Paket (MSI) verwenden. Sie können jedoch den Inhalt eines VSIX-Pakets für die MSI-Bereitstellung extrahieren. In diesem Dokument wird gezeigt, wie ein Projekt vorbereitet wird, dessen Standardausgabe ein VSIX-Paket für die Einbindung in ein Setup-Projekt ist.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Vorbereiten eines Erweiterungsprojekts für die Windows Installer-Bereitstellung
 Führen Sie diese Schritte für neue Erweiterungsprojekte aus, bevor Sie Sie einem Setup-Projekt hinzufügen.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>So bereiten Sie ein Erweiterungsprojekt für Windows Installer Bereitstellung vor

1. Erstellen Sie ein VSPackage, eine MEF-Komponente, ein Editor-Adornment oder einen anderen Erweiterbarkeits Projekttyp, der ein VSIX-Manifest enthält.

2. Öffnen Sie im Code-Editor das VSIX-Manifest.

3. Legen Sie das- `InstalledByMsi` Element des VSIX-Manifests auf fest `true` . Weitere Informationen zum VSIX-Manifest finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Dadurch wird verhindert, dass der VSIX-Installer versucht, die Komponente zu installieren.

4. Klicken Sie mit der rechten Maustaste **Projektmappen-Explorer** auf das Projekt, und klicken Sie auf **Eigenschaften**

5. Wählen Sie die Registerkarte **VSIX** aus.

6. Aktivieren Sie das Kontrollkästchen **VSIX-Inhalt kopieren an den folgenden Speicherort,** und geben Sie den Pfad ein, in den die Dateien vom Setup-Projekt übernommen werden.

## <a name="extract-files-from-an-existing-vsix-package"></a>Dateien aus einem vorhandenen VSIX-Paket extrahieren
 Führen Sie diese Schritte aus, um den Inhalt eines vorhandenen VSIX-Pakets zu einem Setup-Projekt hinzuzufügen, wenn Sie nicht über die Quelldateien verfügen.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>So extrahieren Sie Dateien aus einem vorhandenen VSIX-Paket

1. Benennen Sie den um *. VSIX* -Datei, die die Erweiterung von *Dateiname. vsix* zum *filename.zip* enthält.

2. Kopieren Sie den Inhalt der *ZIP* -Datei in ein Verzeichnis.

3. Löschen Sie die Datei *[Content_Types]. XML* aus dem Verzeichnis.

4. Bearbeiten Sie das VSIX-Manifest, wie in der vorherigen Prozedur gezeigt.

5. Fügen Sie die verbleibenden Dateien dem Setup-Projekt hinzu.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Installer-Bereitstellung](/previous-versions/2kt85ked(v=vs.120))
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Aktion](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))