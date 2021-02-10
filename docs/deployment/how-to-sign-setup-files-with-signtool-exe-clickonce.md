---
title: Signieren von Setupdateien mit „SignTool.exe“ (ClickOnce)
description: Erfahren Sie, wie Sie SignTool.exe zum Signieren eines Setup Programms für ClickOnce-Anwendungen verwenden. Dadurch wird sichergestellt, dass nicht manipulierte Dateien installiert sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdfdabf66c48a875f3b4316ac22e1911c141275c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940526"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Vorgehensweise: Signieren von Setupdateien mit SignTool.exe (ClickOnce)
Sie können mit *SignTool.exe* ein Setupprogramm (*setup.exe*) signieren. Durch diesen Prozess können Sie sicherstellen, dass manipulierte Dateien nicht auf den Computern von Endbenutzern installiert werden.

 Standardmäßig verfügt ClickOnce über signierte Manifeste und ein signiertes Setupprogramm. Wenn Sie jedoch später die Parameter des Setupprogramms ändern möchten, müssen Sie das Setupprogramm später signieren. Wenn Sie die Parameter nach dem Signieren des Setupprogramms ändern, wird die Signatur beschädigt.

 Mit dem folgenden Verfahren werden nicht signierte Manifeste und ein nicht signiertes Setupprogramm erstellt. Dann wird das Signieren mit ClickOnce in Visual Studio aktiviert, um signierte Manifeste zu generieren. Das Setupprogramm bleibt nicht signiert, damit der Kunde die ausführbare Datei mit einem eigenen Zertifikat signieren kann.

### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>So generieren Sie ein nicht signiertes Setupprogramm und signieren es später

1. Installieren Sie das Zertifikat, mit dem Sie das Manifest signieren möchten, auf dem Entwicklungscomputer.

2. Wählen Sie das Projekt im **Projektmappen-Explorer** aus.

3. Klicken Sie im Menü **Projekt** auf **Eigenschaften** von *ProjectName* .

4. Deaktivieren Sie auf der Seite **Signieren** das Kontrollkästchen **ClickOnce-Manifeste signieren**.

5. Klicken Sie auf der Seite **Veröffentlichen** auf **Erforderliche Komponenten**.

6. Überprüfen Sie, ob alle erforderlichen Komponenten ausgewählt sind, und klicken Sie dann auf **OK**.

7. Überprüfen Sie auf der Seite **Veröffentlichen** die Einstellungen für die Veröffentlichung, und klicken Sie dann auf **Jetzt veröffentlichen**.

     Die Projektmappe veröffentlicht das nicht signierte Anwendungsmanifest, das nicht signierte Bereitstellungsmanifest, versionsspezifische Dateien und das nicht signierte Setupprogramm im Pfad des Veröffentlichungsordners.

8. Klicken Sie auf der Seite **Veröffentlichen** auf **Erforderliche Komponenten**.

9. Deaktivieren Sie im Dialogfeld **Erforderliche Komponenten** das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen**.

10. Überprüfen Sie auf der Seite **Veröffentlichen** die Einstellungen für die Veröffentlichung, und klicken Sie dann auf **Jetzt veröffentlichen**.

     Die Projektmappe veröffentlicht das signierte Anwendungsmanifest, das signierte Bereitstellungsmanifest und versionsspezifische Dateien im Pfad des Veröffentlichungsordners. Das nicht signierte Setupprogramm wird durch die Veröffentlichung nicht überschrieben.

11. Öffnen Sie auf der Kundenwebsite eine Eingabeaufforderung.

12. Wechseln Sie in das Verzeichnis, das die *exe* -Datei enthält.

13. Signieren Sie die *exe* -Datei mit dem folgenden Befehl:

    ```cmd
    signtool sign /sha1 CertificateHash Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

     Verwenden Sie beispielsweise einen der folgenden Befehle, um das Setupprogramm zu signieren:

    ```cmd
    signtool sign /sha1 CCB... Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
