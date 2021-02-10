---
title: Seite "veröffentlichen", Projekt-Designer (Office-Entwicklung)
description: Erfahren Sie, wie die Seite Veröffentlichen des Projekt-Designers in Visual Studio verwendet wird, um die Eigenschaften für die Bereitstellung zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bc80a71516f1de8f2a6943d9df7b02341ea786aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971725"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Seite "veröffentlichen", Projekt-Designer (Office-Entwicklung in Visual Studio)
  Die Seite **Veröffentlichen** des **Projekt-Designers** wird zur Konfiguration von Eigenschaften für die Bereitstellung verwendet.

 Wählen Sie zum Aufrufen der Seite das Projekt im **Projektmappen-Explorer** aus, und klicken Sie anschließend im Menü **Projekt** auf *Projektname* **Eigenschaften**. Wenn die Seite **Veröffentlichen** nicht angezeigt wird, wählen Sie die Registerkarte **Veröffentlichen** aus.

> [!NOTE]
> Sie können auch den Veröffentlichungsort im **Veröffentlichungs-Assistenten** festlegen. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer Office-Projekt Mappe mithilfe von ClickOnce](/previous-versions/bb386095(v=vs.110)).

## <a name="uielement-list"></a>UIElement-Liste
 **Speicherort des Veröffentlichungs Ordners (Website, FTP-Server oder Dateipfad)** Erforderlich.

 Der Speicherort des Veröffentlichungsordners ist das Verzeichnis, in das Visual Studio die Projektmappendateien kopiert, z. B. Manifeste, Assemblys und andere Dateien aus dem Build. Sie benötigen Schreibzugriff auf dieses Verzeichnis.

 Optionen umfassen den lokalen Computer, eine UNC-Dateifreigabe oder eine HTTP/HTTPS-Website. Der Pfad kann lokal (*c:\foldername\publishfolder*), relative (*Publish \\*) oder ein voll qualifizierter Speicherort (*\\ \servername\foldername* oder http://<em>Servername/FolderName</em>) sein.

 Standardmäßig ist der Veröffentlichungs Speicherort *http://localhost/projectname/* , wenn IIS installiert ist, oder das *Verzeichnis \\ veröffentlichen* , wenn IIS nicht installiert ist.

 **URL des Installations Ordners** Optionale.

 Die URL des Installationsordners ist das Verzeichnis, über das der Endbenutzer die Anpassung installiert. Hierbei handelt es sich ebenfalls um den Pfad, der von der Projektmappe für die Suche nach Updates verwendet wird. Als Pfad kann derselbe Pfad wie für den Speicherort des Veröffentlichungsordners verwendet werden, aber dies ist nicht unbedingt erforderlich.

 Optionen umfassen den lokalen Computer, eine UNC-Dateifreigabe oder eine HTTP/HTTPS-Website. Der Pfad kann lokal (*c:\foldername\publishfolder*), relative (*Publish \\*) oder ein voll qualifizierter Speicherort (*\\ \servername\foldername* oder http://<em>Servername/FolderName</em>) sein. Alle HTTP/HTTPS-Speicherorte müssen mit US-ASCII-Zeichen erstellt werden. Unicode-Zeichen werden nicht unterstützt.

 Wenn der Installationspfad festgelegt ist, müssen sich die Anpassungsdateien an diesem Speicherort befinden, damit Benutzer die Anpassung installieren können. Der Speicherort sollte nur festgelegt werden, wenn Sie den endgültigen Speicherort für die Bereitstellung kennen.

 Lassen Sie dieses Feld leer, wenn sich die Installationsdateien an einem Speicherort befinden, der relativ zum Dokument oder Setupprogramm angegeben ist, z. B. bei der Option „CD“.

 Dieser Wert kann später von einem Administrator zugewiesen werden. Weitere Informationen finden Sie unter Gewusst [wie: Ändern des Installations Pfads einer Office](/previous-versions/bb608626(v=vs.110))-Projekt Mappe.

  Erforderliche Komponenten Die Voraussetzungen können im Setup Programm enthalten sein oder bei Bedarf während der Installation heruntergeladen werden.

- **Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**: Mithilfe dieser Option können Sie die erforderlichen Komponenten bei Microsoft herunterladen.

- **Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**: Mithilfe dieser Option können Sie die erforderlichen Komponenten im Installationsprogramm verpacken. Das Einbeziehen der Dateien für die erforderlichen Komponenten in das Setupprogramm erhöht die Größe der Projektmappe.

- **Erforderliche Komponenten von folgendem Speicherort herunterladen**: Mithilfe dieser Option können Sie die erforderlichen Komponenten für Endbenutzer gesondert als weiteres Setupprogramm auf einer Webseite oder Netzwerkfreigabe zur Verfügung stellen.

  **Updates** Das Aktualisierungs Intervall bestimmt, wie oft die Projekt Mappe nach Updates sucht. Standardmäßig wird die Prüfung alle sieben Tage ausgeführt.

  Wenn bei jeder Anpassung auf Dokumentebene oder beim Laden eines VSTO-Add-Ins auf Updates geprüft wird, würde das System auf dem neuesten Stand bleiben, aber es würde ebenfalls die Leistung beim Start beeinträchtigen.

  Wenn Sie die Bereitstellung mithilfe einer CD oder eines Wechsellaufwerks vornehmen, legen Sie die Option **Nie nach Updates suchen** fest.

  **Optionen (Beschreibung)** Die Veröffentlichungs Optionen für die folgenden Eigenschaften können festgelegt werden:

- Sprache für Veröffentlichung: Das Gebietsschema der Office-Projektmappe.

- Herausgebername: Der Firmen- oder Entwicklername, wie er unter **Software** oder **Programme und Funktionen** angezeigt wird.

- Produktname: Der Name der Office-Projektmappe, wie er unter **Software** oder **Programme und Funktionen** angezeigt wird.

- Support-URL: Der Pfad für Endbenutzer, um sich an den technischen Support für die Office-Projektmappe zu wenden.

  **Optionen (Office-Einstellungen)** Die Veröffentlichungs Optionen für die folgenden Eigenschaften können festgelegt werden:

- Projektmappenname: Der Name der Office-Projektmappe, wie er in der Office-Anwendung angezeigt wird.

- Beschreibung: Die Beschreibung der Office-Projektmappe, wie sie in der Office-Anwendung angezeigt wird.

- VSTO-Add-In-Ladeverhalten.

  - Beim Start laden: Gibt an, dass das VSTO-Add-In beim Starten der Office-Anwendung geladen wird.

  - Bedarfsgesteuert laden: Gibt an, dass das VSTO-Add-In nur geladen wird, wenn es für die Anwendung erforderlich ist, wenn z. B. ein Benutzer auf ein Benutzeroberflächenelement klickt, das auf Funktionen im VSTO-Add-In zurückgreift.

  **Sprache veröffentlichen** Mit dieser Option wird die Sprache der Microsoft-Software-Lizenzbedingungen festgelegt, und die Sprachpakete in der Liste der erforderlichen Komponenten werden eingeschlossen. Sie wirkt sich nicht auf die Sprache der Anpassung aus. Die Sprache im Setupprogramm wird durch die installierten Sprachen von Visual Studio bestimmt.

  Weitere Informationen zum Ändern der **Veröffentlichungs Sprache** finden Sie unter Gewusst [wie: Ändern der Veröffentlichungs Sprache für eine ClickOnce-Anwendung](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Veröffentlichungs Version** Legt die Versionsnummer für die Anpassung fest. Wenn die Versionsnummer geändert wird, erfolgt die Veröffentlichung der Anwendung als Update. Für jede Version wird während des Buildprozesses ein neuer Ordner erstellt, um das Überschreiben der zuvor veröffentlichten Version zu verhindern. Jeder Teil der Veröffentlichungsversion (**Hauptversion**, **Nebenversion**, **Build**, **Revision**) kann bis zu fünf Ziffern umfassen.

  **Revision mit jeder Version automatisch erhöhen** Optionale. Wenn aktiviert (Standardeinstellung), wird der Teil **Revision** der Versionsnummer bei jeder Veröffentlichung der Anpassung um eins erhöht. Dies bewirkt, dass die Anpassung als Update veröffentlicht wird.

  **Jetzt veröffentlichen** Veröffentlicht die Anwendung mithilfe der aktuellen Einstellungen. Entspricht der Schaltfläche **Fertig stellen** im **Veröffentlichungs-Assistent**.

## <a name="see-also"></a>Weitere Informationen

- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Bereitstellen einer Office-Projekt Mappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office-Lösungs Voraussetzungen für die Bereitstellung](/previous-versions/bb608617(v=vs.110))