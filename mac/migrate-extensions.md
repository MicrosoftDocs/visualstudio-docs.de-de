---
title: 'Problembehandlung: Wie veröffentliche ich eine neue Version meiner vorhandenen Erweiterung?'
description: Eine Anleitung zum Aktualisieren vorhandener Erweiterungen über den Veröffentlichungsworkflow.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488542"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Problembehandlung: Wie veröffentliche ich eine neue Version meiner vorhandenen Erweiterung?

> [!IMPORTANT]
> Derzeit wird das Erstellen neuer Erweiterungen in Visual Studio 2019 für Mac nicht offiziell unterstützt.

Der Visual Studio für Mac-Erweiterungsrepositoryserver wird am 15. Januar 2021 verschoben. Diese Verschiebung wirkt sich nicht auf Benutzer aus, die Ihre Erweiterung bereits heruntergeladen haben, ändert jedoch die Art und Weise, wie Sie neue Releases ihrer Erweiterung nach diesem Datum veröffentlichen.

Als Autor einer vorhandenen Erweiterung müssen Sie einen anderen Workflow befolgen, um weitere Updates zu veröffentlichen. Dieser Vorgang besteht aus folgenden Schritten:
- Einrichten eines öffentlichen GitHub-Repositorys für jede Erweiterung
- Freigeben der Repository-URL für das Visual Studio für Mac-Team über die [Adressenliste für Erweiterungsveröffentlichung](mailto:vsmextpub@microsoft.com)
- Aktualisieren Ihrer Erweiterung mithilfe des Releasesfeatures in GitHub


## <a name="initial-setup"></a>Erste Einrichtung 

Um die Veröffentlichung von Updates für Ihre Erweiterungen fortzusetzen, müssen Sie ein öffentliches GitHub-Repository erstellen. Wenn Sie mehrere Erweiterungen veröffentlichen, benötigen Sie ein separates Repository für jede Erweiterung, es sei denn, Sie versehen sie immer zusammen mit Versionsnummern und veröffentlichen sie gemeinsam. In diesem Fall können Sie ein einzelnes Repository verwenden.

> [!NOTE]
> Das GitHub-Repository für Ihre Erweiterung muss öffentlich sein, Sie müssen dort jedoch keinen Code hosten. Wenn Sie diesen Prozess befolgen, benötigen Sie keinen Code in GitHub.


## <a name="share-the-location-of-your-repository"></a>Freigeben des Speicherorts Ihres Repositorys

Nachdem Sie das Repository eingerichtet haben, senden Sie eine E-Mail mit der URL an die [Adressenliste für Erweiterungsveröffentlichung](mailto:vsmextpub@microsoft.com).


## <a name="release-a-new-version"></a>Veröffentlichen einer neuen Version

Sie verwenden den Link „Create a new release“ (Neues Release erstellen) auf der Hauptseite des Repositorys, um die Aktualisierung ihrer Erweiterung zu starten. Nachdem Sie diesen Link ausgewählt haben, führen Sie die folgenden Schritte aus:

1. Fügen Sie der **Tagversion** des Release im folgenden Format Informationen hinzu.

    > v\<releaseVersion>\-vsm\<targetVersion>

    Hierbei gilt:
     - **&lt;releaseVersion&gt;** ist die Versionsnummer Ihrer Erweiterung.
     - **&lt;targetVersion&gt;** ist die Mindestversion von Visual Studio für Mac, auf die die Erweiterung abzielt.

2. (Optional) In die Felder **title** (Titel) und **description** (Beschreibung) können Sie beliebige Informationen eingeben. Dieser Workflow verwendet die Informationen in diesen Feldern nicht.

3. Vergewissern Sie sich, dass das Kontrollkästchen **pre-release** (Vorabversion) deaktiviert ist. Wenn es aktiviert ist, wird das Release von diesem Veröffentlichungsprozess nicht verwendet.

4. Fügen Sie die **MPACK**-Dateien im Abschnitt **binaries** (Binärdateien) an, die Ihre Erweiterung implementieren. Es ist möglich, mehrere **. MPACK**-Dateien in einem Release anzufügen.

In Visual Studio für Mac wird die neueste Version der Erweiterung angezeigt, die mit der Visual Studio für Mac-Installation kompatibel ist, die für den Zugriff auf das Erweiterungsrepository verwendet wurde.

Solange Sie Ihr GitHub-Repository beim Visual Studio für Mac-Team registriert haben, wird das Erweiterungsrelease innerhalb von 24 Stunden von Visual Studio für Mac abgerufen.

## <a name="additional-information"></a>Zusätzliche Informationen

- Releases, die den oben beschriebenen Anforderungen nicht entsprechen, werden nicht veröffentlicht. 
- Nach dem 15. Januar 2021 werden Erweiterungsupdates nur in Visual Studio für Mac 8.0 oder neuer angezeigt.
- Vorhandene Erweiterungen sind für Benutzer von Visual Studio für Mac ohne irgendeine Aktion Ihrerseits weiterhin verfügbar. Sie müssen die Anweisungen in diesem Leitfaden nur befolgen, wenn Sie eine neue Version nach dem 15. Januar 2021 veröffentlichen.
