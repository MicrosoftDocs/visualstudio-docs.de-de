---
title: Einrichten eines Subversion-Repositorys
description: Hier erfahren Sie, wie Sie Subversion als zentralisiertes Versionskontrollsystem in Visual Studio für Mac installieren und einrichten.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: b5230958fa1624acf7609d6cad7d885e43c013d0
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847077"
---
# <a name="set-up-a-subversion-repository"></a>Einrichten eines Subversion-Repositorys

Subversion ist ein zentralisiertes _Versionskontrollsystem_, was bedeutet, dass ein einzelner Server alle Dateien und Revisionen enthält, aus denen Benutzer eine beliebige Version einer beliebigen Datei auschecken können. Wenn Dateien aus einem Remoterepository von Subversion ausgecheckt werden, erhalten Benutzer eine Momentaufnahme des Repositorys.

Sie müssen Subversion auf Ihrem Computer installieren, damit Sie dieses System zur Versionskontrolle verwenden können. Verwenden Sie den folgenden Befehl im Terminal, wenn Sie überprüfen möchten, ob Subversion bereits auf Ihrem Computer installiert wurde:

```bash
svn --version
```

Dieser Befehl gibt die Versionsnummer zurück.

Wenn Subversion noch nicht installiert wurde, installieren Sie am besten die _Xcode-Befehlszeilentools_. Verwenden Sie den nachfolgenden Code, um die Xcode-Befehlszeilentools und Subversion zu installieren.

```bash
xcode-select --install
```

Sobald Sie Subversion auf Ihrem Computer installiert haben, führen Sie die folgenden Schritte aus, um Ihr Projekt in SVN zu veröffentlichen.

1. Erstellen Sie online ein kostenloses SVN-Repository. In diesem Beispiel wurde [Assembla](https://app.assembla.com/) verwendet. Sobald es erstellt ist, wird eine URL bereitgestellt, die zum Verbinden mit dem Repository verwendet wird:

    ![Die SVN-URL kopieren](media/version-control-subversion1-sml.png)

2. Öffnen oder erstellen Sie ein Projekt in Visual Studio für Mac.

3. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Version Control > Publish in Version Control...** (Versionskontrolle > In der Versionskontrolle veröffentlichen...):

    ![Beginnen mit der Veröffentlichung des Projekts](media/version-control-subversion2.png)

4. Klicken Sie in der Registerkarte **Mit Repository verbinden** im oberen Dropdownmenü auf **Subversion**.

5. Geben Sie die URL aus Schritt 1 ein. Sobald Sie die URL eingegeben haben, werden die anderen Felder standardmäßig aufgefüllt:

    ![Auswählen des Repositorys und Dialogfeld „Details eingeben“](media/version-control-subversion3.png)

7. Klicken Sie auf **OK** und bestätigen Sie den Vorgang, indem Sie auf **Publish** (Veröffentlichen) klicken.

7. Geben Sie, sofern Sie dazu aufgefordert werden, wie in der folgenden Abbildung dargestellt Ihre Anmeldeinformationen für die Website ein, auf der Sie das Repository erstellen:

    ![Anmeldeinformationen für das Subversion-Repository eingeben](media/version-control-subversion5.png)

8. Alle verfügbaren Befehle der Versionskontrolle sollten nun im Menü „Versionskontrolle“ sichtbar sein.

## <a name="see-also"></a>Weitere Informationen

- [Working with Subversion (Arbeiten mit Subversion)](working-with-subversion.md)