---
title: Öffnen und Speichern von Projekt Elementen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die verschiedenen Ansätze zum Öffnen und Speichern von Dateien für den neuen Projekttyp in der Visual Studio-IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df851f304cd6c62e1447f791a23618a6de5cb0bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895595"
---
# <a name="opening-and-saving-project-items"></a>Öffnen und Speichern von Projektelementen
Wenn Sie einen neuen Projekttyp hinzufügen, müssen Sie das Öffnen und Speichern Ihrer Projektdateien in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) verwalten. In den folgenden Themen werden die verschiedenen Ansätze zum Öffnen und Speichern von Dateien erörtert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Anzeigen von Dateien mit dem Befehl „Datei öffnen“](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Bietet eine schrittweise Erläuterung dazu, wie die IDE den Befehl " **Open File** " und die Rolle von Projekten behandelt, die auf diesen Befehl reagieren.

- [Anzeigen von Dateien mit dem Befehl „Öffnen mit“](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Bietet eine ausführliche schrittweise Erläuterung, wie die IDE den Befehl " **Öffnen mit** " behandelt, um das Öffnen einer Datei mit einer Auswahl von Standard-Editoren aufzurufen.

- [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)

 Enthält Schritt-für-Schritt-Anleitungen für die Angabe, dass Dateien eines bestimmten Typs im Projekt mit einem projektspezifischen Editor geöffnet werden sollen.

- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)

 Enthält Schritt-für-Schritt-Anleitungen zum angeben, wie die IDE aktiviert werden soll, um einen Standard Editor für Dateien im Projekttyp zu öffnen.

- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)

 Enthält Schritt-für-Schritt-Anweisungen zum Öffnen eines projektspezifischen Editors für eine geöffnete Datei.

- [Speichern eines Standarddokuments](../../extensibility/internals/saving-a-standard-document.md)

 Bietet eine ausführliche Erläuterung dazu, wie die IDE die Befehle " **Speichern**", " **Speichern** unter" und " **Alle speichern** " für ein Dokument verarbeitet, das in einem Standard-Editor geöffnet ist.

- [Speichern eines benutzerdefinierten Dokuments](../../extensibility/internals/saving-a-custom-document.md)

 Enthält ein Diagramm und eine ausführliche Erläuterung der Behandlung der Befehle **Speichern**, **Speichern** unter und **alle** Befehle für Dokumente, die in einem benutzerdefinierten Editor geöffnet werden.

- [Bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Erläutert den Prozess, den die IDE befolgt, um den entsprechenden Editor oder Designer für eine Datei auszuwählen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md)

 Listet die vier Typen von Editoren auf, die von der IDE gehostet werden können, und enthält Beschreibungen der einzelnen Editor.

- [Projekttypen](../../extensibility/internals/project-types.md)

 Erläutert, wie-Projekte die Art und Weise steuern, wie Code kompiliert und erstellt wird, wie Editoren geöffnet werden und wie Projekt Elemente formatiert werden.
