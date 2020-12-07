---
title: Dokumente, Umgebung, Dialogfeld "Optionen"
description: Hier erfahren Sie, wie Sie die Seite „Umgebungen“ im Abschnitt „Dokumente“ verwenden, um die Anzeige von Dokumenten in der integrierten Entwicklungsumgebung (IDE) zu steuern und externe Änderungen an Dokumenten und Dateien zu verwalten.
ms.custom: SEO-VS-2020
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28b0e7920aca2ae8b789a37fad25509dbb8b4d7a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305483"
---
# <a name="options-dialog-box-environment--documents"></a>Dialogfeld „Optionen“: Umgebung \> Dokumente

Verwenden Sie diese Seite des Dialogfelds **Optionen**, um die Anzeige von Dokumenten in der integrierten Entwicklungsumgebung (IDE) zu steuern und externe Änderungen an Dokumenten und Dateien zu verwalten. Sie können auf dieses Dialogfeld zugreifen, indem Sie im Menü **Extras** auf **Optionen** klicken, und anschließend **Umgebung** > **Dokumente** auswählen.

**Ermitteln, ob Datei außerhalb der Umgebung geändert wird**

Wenn diese Option aktiviert ist, benachrichtigt Sie eine Meldung sofort über Änderungen einer geöffneten Datei, die von außerhalb der IDE vorgenommen wurden. Mit dieser Meldung können Sie die Datei aus dem Speicher erneut laden.

**Geänderte Dateien neu laden, sofern keine ungespeicherten Änderungen vorhanden sind**

Wenn die Datei **Gespeicherte Änderungen automatisch laden** aktiviert ist, und eine geöffnete Datei in der IDE außerhalb der IDE geändert wird, wird standardmäßig eine Warnmeldung generiert. Wenn diese Option aktiviert ist, erscheint keine Warnung, und das Dokument wird in der IDE erneut geladen, um die externen Änderungen zu übernehmen.

**Bearbeiten schreibgeschützter Dateien zulassen und bei Speicherversuch warnen**

Wenn die Option aktiviert ist, können Sie eine schreibgeschützte Datei öffnen und bearbeiten. Nach Abschluss der Bearbeitung müssen Sie den Befehl **Speichern unter** verwenden, um die Datei mit einem neuen Namen zu speichern, wenn Sie Ihre Änderungen speichern möchten.

**Datei mit Verzeichnis des aktuellen Dokuments öffnen**

Wenn diese Option aktiviert ist, gibt sie an, dass das Dialogfeld **Datei öffnen** das Verzeichnis des aktiven Dokuments anzeigt. Wenn diese Option deaktiviert ist, zeigt das Dialogfeld **Datei öffnen** das Verzeichnis an, das zuletzt zum Öffnen einer Datei verwendet wurde.

**Zeilenenden beim Laden auf Konsistenz überprüfen**

Aktivieren Sie diese Option, damit der Editor die Zeilenenden in einer Datei überprüft und ein Meldungsfenster anzeigt, wenn Inkonsistenzen bei der Formatierung der Zeilenenden entdeckt werden.

**Warnen, wenn bearbeitete Dateien durch globales Rückgängigmachen geändert werden**

Aktivieren Sie diese Option zum Anzeigen eines Meldungsfeldes, wenn der Befehl **Globales Rückgängigmachen** Änderungen zurücksetzt, die bei der Umgestaltung von Dateien getroffen wurden, die nach dem Umgestaltungsvorgang ebenfalls geändert wurden. Durch das Zurücksetzen einer Datei auf den Status vor der Umgestaltung können möglicherweise Änderungen verworfen werden, die in der Datei gemacht wurden.

**Sonstige Dateien im Projektmappen-Explorer anzeigen**

Aktivieren Sie diese Option, um den Knoten **Verschiedene Dateien** im **Projektmappen-Explorer** anzuzeigen. Verschiedene Dateien sind Dateien, die keinem Projekt oder keiner Projektmappe zugeordnet werden. Sie können aber auf Wunsch im **Projektmappen-Explorer** angezeigt werden.

> [!NOTE]
> Aktivieren Sie diese Option, um den Befehl **In Browser anzeigen** im Menü **Datei** für Webdokumente zu aktivieren, die nicht in der aktiven Webanwendung enthalten sind.

**im Projekt „Sonstige Dateien“ gespeicherte Elemente**

Gibt die Anzahl von Dateien an, die im Ordner **Sonstige Dateien** des **Projektmappen-Explorers** aufbewahrt werden sollen. Diese Dateien werden auch aufgelistet, wenn sie nicht mehr in einem Editor geöffnet sind. Sie können eine beliebige ganze Anzahl von 0 bis 256 angeben. Die Standardanzahl ist 0.

Wenn Sie z.B. diese Option auf 5 festlegen, und 10 verschiedene Dateien geöffnet sind, werden die ersten 5 Dateien trotzdem noch im Ordner **Verschiedene Dateien** angezeigt, wenn Sie alle 10 Dateien schließen.

**Dokumente als Unicode speichern, wenn Speichern der Daten in Codepage nicht möglich**

Aktivieren Sie diese Option, damit Dateien, die Informationen enthalten, die nicht mit dem ausgewählten Codepage-Standard kompatibel sind, standardmäßig als Unicode gespeichert werden.

## <a name="see-also"></a>Siehe auch

- [Sonstige Dateien](../../ide/reference/miscellaneous-files.md)
- [Suchen und Ersetzen von Text](../../ide/finding-and-replacing-text.md)
