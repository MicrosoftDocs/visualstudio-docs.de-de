---
title: Dokumentation für Offlinehilfe
description: Installieren und Anzeigen der Offline Hilfe Dokumentation für verschiedene Produkte und Technologien, wie z. b. Visual Studio und .net, mithilfe von Microsoft Help Viewer.
ms.date: 11/02/2017
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 339d424dd0b09404fc135a119606d47cf7570be3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944094"
---
# <a name="microsoft-help-viewer"></a>Microsoft Help Viewer

Sie können Inhalte für verschiedene Produkte und Technologien mithilfe von Microsoft Help Viewer auf einem lokalen Computer installieren und anzeigen. Diese Produkte enthalten Visual Studio, .NET, Sprachreferenzen, SQL Server und die Windows-Bereitstellung. Help Viewer bietet Ihnen folgende Möglichkeiten:

- Laden Sie Inhalte herunter, die auch als „Bücher“ bezeichnet werden. Dies kann nützlich sein, wenn Sie offline arbeiten müssen und dennoch Zugriff auf die Dokumentation benötigen.

- Sie können über eine Suche im Inhaltsverzeichnis Themen anhand von Überschriften finden

- Suchen Sie nach Themen im Index.

- Suchen Sie mithilfe der Volltextsuche nach Informationen.

- Zeigen Sie Themen an, versehen Sie Themen mit Lesezeichen, und drucken Sie Themen aus.

Informationen zum Installieren von Help Viewer finden Sie unter [Microsoft Help Viewer Installation](../help-viewer/installation.md). Wechseln Sie zum Menü **Hilfe** in Visual Studio, und klicken Sie auf **Hilfeeinstellungen festlegen** > **In Help Viewer starten**, um Hilfethemen nicht online, sondern in Help Viewer zu lesen.

> [!TIP]
> Sie können Inhalte ebenfalls lokal als PDF-Version herunterladen, um diese anzuzeigen, wenn Sie nicht über eine Internetverbindung verfügen. Viele Dokumentationen auf docs.microsoft.com enthalten einen Link unter dem Inhaltsverzeichnis, über den Sie eine PDF-Datei herunterladen können, die alle Artikel für dieses Inhaltsverzeichnis enthält.
>
> ![PDF für die Visual Studio-Dokumentation herunterladen](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Überblick über Help Viewer

Informationen finden Sie unter installierte Inhalte mithilfe der Navigations Registerkarten, Anzeigen installierter Inhalte auf der Registerkarte "Thema" oder Registerkarten und Verwalten von Inhalt mithilfe der Registerkarte " **Inhalt verwalten** ". Sie können auch zusätzliche Aufgaben ausführen, indem Sie die Schaltflächen auf der Symbolleiste verwenden und zusätzliche Informationen in der unteren rechten Ecke des Fensters Suchen.

### <a name="navigation-tabs"></a>Registerkarten für die Navigation

|Registerkarte|BESCHREIBUNG|
|---|-----------|
|Inhalte|Zeigt die installierten Inhalte hierarchisch an (Inhaltsverzeichnis). Sie können Kriterien festlegen, anhand derer Sie die angezeigten Titel filtern können.|
|Index|Zeigt eine alphabetische Liste der indizierten Begriffe an. Sie können den Index durchsuchen, Kriterien zum Filtern der Einträge angeben und festlegen, dass Indexeinträge entweder eine bestimmte Textzeichenfolge enthalten oder mit dieser beginnen.|
|Favoriten|Sie können "Favoriten"-Themen auswählen, indem Sie die Schaltfläche **zu Favoriten hinzufügen** auswählen und die Themen auf dieser Registerkarte angezeigt werden. Im Abschnitt **Verlauf** wird eine Liste der Themen angezeigt, die Sie in jüngster Zeit angezeigt haben.|
|Suchen,|Stellt ein Textfeld bereit, über das Sie überall, auch im Code und in den Themenüberschriften, nach Begriffen suchen können.|

### <a name="view-topics"></a>Anzeigen von Themen

Jedes Thema wird auf einer eigenen Registerkarte angezeigt. Sie können mehrere Themen gleichzeitig öffnen.

### <a name="manage-content"></a>Inhalt verwalten

Mithilfe der Registerkarte **Inhalt verwalten** können Sie Inhalte installieren, aktualisieren, verschieben und löschen. Am oberen Rand der Registerkarte können Sie mit der **Installations Quell** Code Verwaltung angeben, ob Bücher von einem Netzwerk Speicherort oder von einem Datenträger oder URI installiert werden sollen. Im Feld **Local store path** (Lokaler Speicherpfad) wird angezeigt, in welchem Verzeichnis die Bücher auf dem lokalen Computer installiert sind. Mit der Schaltfläche **Verschieben** können Sie die Bücher an einen anderen Speicherort verschieben.

In der Inhaltsliste wird angezeigt, welche Bücher Sie installieren können bzw. welche Bücher Sie bereits installiert haben, ob ein Update verfügbar ist und wie groß jedes Buch ist. Sie können ein oder mehrere Bücher mit den Links **Hinzufügen** oder **Entfernen** installieren oder entfernen und dann im Bereich **Ausstehende Änderungen** auf die Schaltfläche **Aktualisieren** klicken. Wenn Updates für bereits installierte Bücher verfügbar sind, können Sie diese Inhalte aktualisieren, indem Sie unten im Fenster auf **Hier klicken, um den Download jetzt zu starten** klicken. Darüber hinaus werden bei der Installation zusätzlicher Bücher alle bereits installierten aktualisiert, falls Updates verfügbar sind.

> [!NOTE]
> Die Funktionalität der Registerkarte **Inhalt verwalten** unterscheidet sich möglicherweise, wenn der Help Viewer-Administrator diese Features deaktiviert oder kein Internetzugang verfügbar ist.

### <a name="toolbar-buttons"></a>Schaltflächen auf der Symbolleiste

Die Symbolleiste im **Help Viewer-Fenster** enthält die folgenden Schaltflächen:

- Die Schaltfläche **Thema in Inhalten anzeigen** zeigt den Speicherort des Themas auf der Registerkarte **Inhalt** an.

- Mit der Schaltfläche **Zu Favoriten hinzufügen** wird das aktuelle Thema der Registerkarte **Favoriten** hinzugefügt.

- Mit der Schaltfläche **In Thema suchen** wird Suchtext im aktiven Thema hervorgehoben.

- Mit der Schaltfläche **Drucken** wird eine Vorschau des aktiven Themas gedruckt oder angezeigt.

- Mit der Schaltfläche **Viewer-Optionen** werden Einstellungen angezeigt, z.B. wie groß der Text angezeigt wird, wie viele Suchergebnisse zurückgegeben werden, wie viele Themen im Verlauf angezeigt werden und ob auf vorhandene Onlineupdates überprüft wird.

- Durch die Schaltfläche **Inhalt verwalten** wird die Registerkarte **Inhalt verwalten** aktiv.

- Das kleine Dreieck auf der rechten Seite öffnet eine Liste von Registerkarten, einschließlich Themen Registerkarten und der Registerkarte **Inhalt verwalten** . Sie können einen Registerkarten Namen auswählen, um ihn als aktive Registerkarte zu erstellen.

## <a name="see-also"></a>Weitere Informationen

- [Microsoft Help Viewer Installation](../help-viewer/installation.md)
- [Help Viewer-Administrator Handbuch](../help-viewer/administrator-guide.md)
- [Installieren und Verwalten von lokalen Inhalten](../help-viewer/install-manage-local-content.md)
