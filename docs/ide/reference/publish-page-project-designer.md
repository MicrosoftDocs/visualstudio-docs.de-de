---
title: Seite "Veröffentlichen", Projekt-Designer
description: Die Seite „Veröffentlichen“ des Projekt-Designers wird zum Konfigurieren von Eigenschaften für die ClickOnce-Bereitstellung verwendet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13edc1b2e2e235eaf5a475764a98067aa4b0150d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350282"
---
# <a name="publish-page-project-designer"></a>Seite "Veröffentlichen", Projekt-Designer

Die Seite **Veröffentlichen** des **Projekt-Designers** wird zur Konfiguration von Eigenschaften für die ClickOnce-Bereitstellung verwendet.

Wählen Sie zum Aufrufen der Seite **Veröffentlichen** im **Projektmappenexplorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen** .

> [!NOTE]
> Einige der hier beschriebenen ClickOnce-Eigenschaften können auch im **Veröffentlichungs-Assistent** festgelegt werden, der im Menü **Erstellen** verfügbar ist, oder durch Klicken auf die Schaltfläche **Veröffentlichungs-Assistent** auf dieser Seite.

## <a name="uielement-list"></a>UIElement-Liste

 **Pfad des Veröffentlichungsordners**

Gibt den Speicherort an, in dem die Anwendung veröffentlicht wird. Dies kann ein Pfad zum Laufwerk (`C:\deploy\myapplication`), eine Dateifreigabe (`\\server\myapplication`) oder ein FTP-Server (`ftp://ftp.microsoft.com/myapplication`) sein. Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen ( **...** ) funktioniert.

 **URL des Installationsordners**

Dies ist optional. Gibt eine Website an, auf die der Benutzer zugreift, um die Anwendung zu installieren. Dies ist nur erforderlich, wenn sie sich vom **Veröffentlichungsort** unterscheidet, wenn z.B. die Anwendung auf einem Stagingserver veröffentlicht wird.

 **Installationsmodus und -einstellungen**

Bestimmt, ob die Anwendung direkt auf dem **Veröffentlichungsort** ausgeführt wird (wenn **Anwendung ist nur online verfügbar** ausgewählt ist) oder installiert und auf dem Menü **Start** sowie dem Untermenü **Programme hinzufügen oder entfernen** der **Systemsteuerung** hinzugefügt wird (wenn **Die Anwendung ist auch offline verfügbar** ausgewählt ist).

Für WPF-Webbrowseranwendungen ist die Option **Anwendung ist auch offline verfügbar** deaktiviert, da Anwendungen dieser Art nur online verfügbar sind.

 **Anwendungsdateien**

Öffnet das Dialogfeld „Anwendungsdateien“, mit dem angegeben wird, wie und wo einzelne Dateien installiert sind

 **Voraussetzungen**

Öffnet das Dialogfeld „Erforderliche Komponenten“, mit dem erforderliche Komponenten wie das .NET Framework angegeben werden, die zusammen mit dieser Anwendung installiert werden

 **Updates**

Öffnet das Dialogfeld „Anwendungsupdates“, mit dem das Updateverhalten der Anwendung angegeben wird. Dieses Element ist nicht verfügbar, wenn **Anwendung ist nur online verfügbar** ausgewählt ist.

 **Optionen**

Öffnet das Dialogfeld „Veröffentlichungsoptionen“, mit dem zusätzliche erweiterte Veröffentlichungsoptionen angegeben werden

 **Veröffentlichungsversion**

Legt die Veröffentlichungsversionsnummer für die Anwendung fest. Wird die Versionsnummer geändert, wird die Anwendung als Update veröffentlicht. Jeder Teil der Veröffentlichungsversion (**Hauptversion**, **Nebenversion**, **Build**, **Revision**) kann den Maximalwert 65355 (<xref:System.UInt16.MaxValue>) haben, d.h. das von <xref:System.Version> zugelassene Maximum.

Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.

 **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen**

Dies ist optional. Wenn diese Option ausgewählt ist (Standardeinstellung), wird der Teil **Revision** der Veröffentlichungsversionsnummer bei jeder Veröffentlichung der Anwendung um eins erhöht. Dies bewirkt, dass die Anwendung als Update veröffentlicht wird.

 **Veröffentlichungs-Assistent**

Öffnet den Veröffentlichungs-Assistenten. Die Fertigstellung des Veröffentlichungs-Assistenten hat dieselbe Wirkung wie das Ausführen des Befehls **Veröffentlichen** im Menü **Erstellen** .

 **Jetzt veröffentlichen**

Veröffentlicht die Anwendung mithilfe der aktuellen Einstellungen. Entspricht der Schaltfläche **Fertigstellen** im **Veröffentlichungs-Assistenten**.

## <a name="see-also"></a>Siehe auch

- [Veröffentlichen von ClickOnce-Anwendungen](../../deployment/publishing-clickonce-applications.md)
- [How to: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Vorgehensweise: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Vorgehensweise: Angeben des Speicherorts für die Installation durch Endbenutzer](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [Vorgehensweise: Angeben eines Links für den technischen Support](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [Vorgehensweise: Angeben des Offline- oder Onlineinstallationsmodus von ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [Gewusst wie: Aktivieren von AutoStart für Installationen von CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [Gewusst wie: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Vorgehensweise: Angeben der mit ClickOnce veröffentlichten Dateien](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [How to: Verwalten von Aktualisierungen für eine ClickOnce-Anwendung](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [Vorgehensweise: Ändern der Veröffentlichungssprache einer ClickOnce-Anwendung](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [Vorgehensweise: Angeben eines Namens im Startmenü für eine ClickOnce-Anwendung](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [ClickOnce-Sicherheit und Bereitstellung](../../deployment/clickonce-security-and-deployment.md)
