---
title: Glossar für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699908"
---
# <a name="source-control-plug-in-glossary"></a>Glossar für das Quellcodeverwaltungs-Plug-In
Die folgenden hilfreichen Begriffe und Definitionen beziehen sich auf die SDK-Dokumentation für das Quellcodeverwaltungs-Plug-in.

## <a name="definitions"></a>Definitionen
 Wenn ein Benutzer Änderungen an einer funktionierenden Kopie vornimmt, muss er Änderungen von der Arbeitskopie an das zentrale Quellcodeverwaltungs-Repository senden. Dadurch wird eine neue Revision der Datei erstellt, die anderen Benutzern zur Verfügung steht. Dieser Vorgang wird als Eincheck Vorgang bezeichnet.

 Informieren Sie sich über das Anfordern einer Arbeitskopie aus dem Repository, und informieren Sie das Repository über ihre Absicht, es zu ändern. Eine Arbeitskopie gibt den Status des Projekts wieder, sobald es ausgecheckt ist.

 Client ein Programm, das das Quell Code Verwaltungssystem verwendet. Der Zweck dieser Dokumentation ist die Visual Studio-IDE.

 Kommentieren Sie eine Meldung aus, die die Änderungen beschreibt, die ein Benutzer an eine Revision anfügen kann, wenn ein Quell Code Verwaltungsvorgang ausgeführt wird.

 Ein Konflikt tritt auf, wenn zwei Benutzer versuchen, Änderungen in denselben Bereich derselben Datei einzuchecken. In der Regel muss ein Merge ausgeführt werden.

 Verzeichnis ein Client seitiger lokaler Ordner wird als Verzeichnis bezeichnet. Dies ist die Kopie, in der ein Benutzer tatsächlich Änderungen vornimmt. Es können viele Arbeitskopien eines bestimmten Projekts vorhanden sein. im allgemeinen verfügt jeder Entwickler über seine eigene Kopie.

 Wenn Sie einen Get-Vorgang abrufen, wird die Arbeitskopie des Benutzers auf dem neuesten Stand mit dem Repository kopiert. Anders als bei einem Auscheck Vorgang wird ein Get-Vorgang ausgeführt, wenn der Benutzer einfach die neueste Kopie benötigt, aber keine Änderungen vornehmen soll.

 Verlauf: Es handelt sich in der Regel um eine Zusammenfassung aller im Quellcodeverwaltungs-Repository ausgeführten Auscheck-, Eincheck-, Update-, Tags und Releases.

 IDE bezieht sich im Allgemeinen auf die integrierte Entwicklungsumgebung von Visual Studio. Es kann jedoch auch auf andere Client Umgebungen verweisen, die die Quellcodeverwaltungs-Plug-in-API erkennen.

 Mergen Sie den Prozess, in dem zwei oder mehr Quell Code Dateien kombiniert werden, um eine neue Datei zu erstellen, die alle Features aus früheren Dateien enthält. Dieses Konzept ist wichtig bei der Versionskontrolle, bei der zwei oder mehr Entwickler gleichzeitig an Dateien arbeiten.

 Project ein Quell Code Verwaltungs Ordner wird häufig als Projekt bezeichnet. Dies hat keine Beziehung zu Projekten oder Projektmappen in Visual Studio.

 Plug-in eine DLL-Datei, die Quell Code Verwaltungsfunktionen bereitstellt, indem die Quellcodeverwaltungs-Plug-in-API implementiert

 Repository die Master Kopie, in der ein Quell Code Verwaltungssystem den vollständigen Revisions Verlauf eines Projekts speichert. Jedes Projekt verfügt über genau ein Repository.

 Revision a hat Änderungen im Verlauf einer Datei oder einer Gruppe von Dateien geändert. Eine Revision ist eine Momentaufnahme in einem ständig ändernden Projekt.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
