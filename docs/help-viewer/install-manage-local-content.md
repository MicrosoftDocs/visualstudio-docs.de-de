---
title: Installieren der lokalen Hilfedokumentation
description: Installieren und verwalten Sie die lokale Hilfe Dokumentation mithilfe der Microsoft Help Viewer. Hinzufügen, entfernen, aktualisieren und Verschieben von Hilfe Inhalten, die auf Ihrem Computer installiert sind.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 14091ecd5adc76762901c02c582c845aa0dbd513
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944120"
---
# <a name="install-and-manage-local-content"></a>Installieren und Verwalten von lokalen Inhalten

Durch Verwendung von Microsoft Help Viewer können Sie den Hilfeinhalt, der auf dem Computer installiert ist, hinzufügen, entfernen, aktualisieren oder verschieben, um ihn an die Softwareanforderungen anzupassen.

Sie müssen sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt, um Inhalt auf dem lokalen Computer zu verwalten. Außerdem können Sie möglicherweise keine lokalen Inhalte verwalten, wenn Sie in einer Unternehmensumgebung arbeiten, da diese Entscheidungen möglicherweise von Systemadministratoren für Ihre Organisation getroffen werden. Weitere Informationen finden Sie im [Help Viewer-Administratorleitfaden](../help-viewer/administrator-guide.md).

## <a name="change-the-content-installation-source"></a>Ändern der Installationsquelle für Inhalte

Standardmäßig installiert Help Viewer Inhalte, indem ein Microsoft-Onlinedienst als Quelle verwendet wird. Sie sollten die Inhaltsquelle im Allgemeinen nicht ändern, es sei denn, Sie arbeiten in einer Unternehmensumgebung, für die ein Systemadministrator bereits Inhalte an einem anderen Speicherort installiert hat.

### <a name="to-change-the-content-installation-source"></a>So ändern Sie die Inhaltsinstallationsquelle

1. Wählen Sie auf der Registerkarte **Inhalt verwalten** das Optionsfeld **Datenträger** aus.

    > [!NOTE]
    > Die Option **Datenträger** ist nicht verfügbar, wenn der Administrator keine Berechtigungen zum Ändern der Inhaltsinstallationsquelle erteilt hat. Weitere Informationen finden Sie im [Help Viewer-Administratorleitfaden](../help-viewer/administrator-guide.md).

2. Führen Sie einen der folgenden Schritte aus:

    - Geben Sie den Pfad einer *MSHA-Datei* oder die URL eines Dienstendpunkts ein.

    - Wählen Sie die Schaltfläche zum Durchsuchen (**...**) aus, um zu einer *MSHA* -Datei zu navigieren.

    - Wählen Sie in der Liste den zuletzt verwendeten Eintrag aus.

## <a name="download-and-install-content-locally"></a>Herunterladen und lokales Installieren von Inhalten

Sie können Themen ohne eine Internetverbindung anzeigen lassen, wenn Sie die Inhalte auf dem lokalen Computer herunterladen und installieren.

> [!IMPORTANT]
> Zum Installieren von Inhalt müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt.

> [!NOTE]
> Wenn die Visual Studio IDE auf eine andere Sprache als Englisch eingestellt ist, können Sie englische Inhalte, lokalisierte Inhalte oder beides installieren. Es werden jedoch keine Inhalte angezeigt, wenn Sie nur die englische Version installieren und im Dialogfeld **Viewer-Optionen** das Feld **Englische Inhalte in alle Navigationsregisterkarten und F1-Anforderungen einbeziehen** deaktivieren.

### <a name="to-download-and-install-content"></a>So laden Sie den Inhalt herunter und installieren diesen

1. Wählen Sie die Registerkarte **Inhalt verwalten** aus.

2. Wählen Sie in der Inhaltsliste den Link **Hinzufügen** aus, der sich neben dem bzw. neben den hinzufügenden Buch bzw. Büchern befindet, die Sie herunterladen und installieren möchten.

     Das Buch wird der Liste **Ausstehende Änderungen** hinzugefügt, und die geschätzte Größe des Buchs oder der Bücher, die Sie angegeben haben, wird unterhalb dieser Liste angezeigt. Da einige Bücher die gleichen Themen enthalten, kann die gesamte Downloadgröße mehrerer Bücher kleiner sein als das Ergebnis der summierten Größe für alle Bücher, die Sie angeben.

3. Wählen Sie die Schaltfläche **Aktualisieren**.

     Das Buch oder die Bücher, die Sie angegeben haben, werden mit allen Updates für Bücher installiert, die bereits auf dem Computer vorhanden sind. Installationszeiten schwanken, Sie können jedoch den Status auf der Statusleiste anzeigen.

## <a name="remove-local-content"></a>Entfernen von lokalen Inhalten

Sie können Speicherplatz sparen, indem Sie unerwünschten Inhalt vom Computer entfernen.

> [!IMPORTANT]
> Um Inhalte entfernen zu können, müssen Sie über Administratorberechtigungen verfügen.

> [!NOTE]
> Es wird kein Inhalt angezeigt, wenn die Sprache der Visual Studio-IDE nicht auf Englisch festgelegt ist, Sie lokalisierte Inhalte entfernen und das Feld **Englische Inhalte in alle Navigationsregisterkarten und F1-Anforderungen einbeziehen** im Dialogfeld **Viewer-Optionen** deaktiviert ist.

### <a name="to-remove-content"></a>So entfernen Sie Inhalte

1. Wählen Sie die Registerkarte **Inhalt verwalten** aus.

2. Wählen Sie in der Inhaltsliste den Link **Entfernen** aus, der sich neben dem bzw. neben den zu entfernenden Buch bzw. Büchern befindet.

     Das Buch wird der Liste **Ausstehende Änderungen** hinzugefügt.

3. Wählen Sie die Schaltfläche **Aktualisieren**.

     Das Buch oder die Bücher, die Sie angegeben haben, werden vom Computer entfernt.

## <a name="update-local-content"></a>Aktualisieren von lokalen Inhalten

Auf der Statusleiste wird angegeben, wann Updates für den installierten Inhalt verfügbar sind.

> [!IMPORTANT]
> Wenn Sie **Help Viewer** verwenden möchten, um automatisch nach Onlineupdates zu suchen, öffnen Sie das Dialogfeld **Viewer-Optionen**, und aktivieren Sie dann das Kontrollkästchen **Online Inhalte abrufen und nach Inhaltupdates suchen**.

### <a name="to-update-local-content"></a>So aktualisieren Sie lokale Inhalte

- Wählen Sie in der rechten unteren Ecke der Statusleiste den Link **Hier klicken, um den Download jetzt zu starten** aus.

Die Updatezeiten können variieren, aber Sie können den Aktualisierungsstatus in der Statusleiste anzeigen.

## <a name="move-local-content"></a>Verschieben von lokalen Inhalten

Sie können Speicherplatz sparen, indem Sie installierten Inhalt vom lokalen Computer in eine Netzwerkfreigabe oder in eine andere Partition auf dem lokalen Computer verschieben.

> [!IMPORTANT]
> Zum Verschieben von Inhalt müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt.

### <a name="to-move-local-content"></a>So verschieben Sie lokalen Inhalt

1. Wählen Sie auf der Registerkarte **Inhalt verwalten** unter **Lokaler Speicherpfad** die Schaltfläche **Verschieben** aus.

     Das Dialogfeld **Inhalt verschieben** wird geöffnet.

2. Geben Sie im Textfeld **Nach** einen anderen Speicherort für den Inhalt ein, und wählen Sie dann die Schaltfläche **OK** aus.

3. Klicken Sie auf die Schaltfläche **Schließen**, wenn die Inhalte verschoben wurden.

## <a name="see-also"></a>Weitere Informationen

- [Microsoft Help Viewer](../help-viewer/overview.md)