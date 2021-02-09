---
title: Feedback an den Benutzer | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie dem Benutzer visuelles Feedback zu den verfügbaren Funktionen in der integrierten Entwicklungsumgebung (IDE) von Visual Studio bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33e52a277f621c80773518ae4b9606d7a2c222db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886989"
---
# <a name="feedback-to-the-user"></a>Feedback an den Benutzer
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) basiert das visuelle Feedback zu den verfügbaren Funktionen auf der aktuellen Auswahl des Benutzers und dem globalen Auswahl Kontext. In der folgenden Tabelle sind die Funktionen aufgelistet, die in unterschiedlichen Auswahl Kontexten verfügbar sind.

|Auswahl Kontext|Verfügbare Funktionen|
|-----------------------|-----------------------------|
|IDE|Global|
|Aktueller Produkt Satz|Produktspezifisch|
|Aktive Hierarchie|Hierarchietypen spezifisch|
|Aktives hierarchienelement|Hierarchienelementtyp spezifisch|
|Aktives Dokument|Dokumenttyp spezifisch|
|Fenster "TopMost Multiple Document Interface (MDI)"|Fenstertyp spezifisch|
|Aktueller Auswahl Kontext|Auswahl kontextspezifisch|

 Wenn Sie nur die Funktionalität Oberflächen, die Benutzer benötigen, und ständig konsistentes Feedback zur Auswahl und zum Kontext von Umgebungen bereitstellen, verringern Sie die Komplexität in der IDE. Die folgenden Regeln gelten, wenn ein Fenster in der IDE geöffnet wird:

- Wenn das Fenster seinen Auswahl Kontext ändert, wird im Fenster eindeutig das Auswahl Feedback angezeigt, und das **Dynamische Hilfe** Fenster wird, wenn es angezeigt wird, aktualisiert, um den aktuellen Kontext widerzuspiegeln.

- Wenn das Fenster den globalen Auswahl Kontext ändert, werden alle kontextspezifischen Menüs, das aktive Hierarchie Fenster und die Titelleiste der Anwendung aktualisiert, um den aktuellen Kontext widerzuspiegeln.

- Das Fenster sollte Eigenschaften für die aktuelle Auswahl im **Eigenschaften** Fenster und optional, sofern angezeigt, das Dialogfeld Eigenschaften **Seiten** anzeigen.

- Wenn das Fenster keine Eigenschaften anzeigt oder den globalen Auswahl Kontext ändert, sollte das Auswahl Feedback nicht im Fenster bleiben, wenn es nicht mehr das aktive Fenster in der IDE ist.

- Alle Dokument spezifischen Tool Fenster sollten ständig das aktive Dokument widerspiegeln.

- Menüs, Symbolleisten und die Titelleiste der Anwendung sollten das oberste MDI-Client Fenster (Multiple Document Interface) enthalten.

  Wenn z. b. die HTML-Ansicht eines **Webformulars** innerhalb eines Visual Basic Webanwendungs Projekts geöffnet wird und der Benutzer ein Tag auswählt `<td>` , wird das Feedback wie folgt bereitgestellt:

- Die Auswahl wird im aktiven Fenster angezeigt und im **Eigenschaften** Fenster angezeigt.

- Die Dokument spezifische **Toolbox** wird aktualisiert, um das aktive Dokument widerzuspiegeln.

- Die **Editor** -Symbolleiste und das Menü **Tabelle** werden angezeigt, und die Titelleiste wird aktualisiert, um das Webformular Fenster widerzuspiegeln.

- Das aktive Hierarchie Fenster, das in der Regel **Projektmappen-Explorer** ist, und das Update der Titelleiste, um den aktuellen Kontext widerzuspiegeln, und die kontextbezogenen **Project** -Menübefehle gelten jetzt für das aktive Webanwendungs Projekt.

## <a name="see-also"></a>Weitere Informationen
- [Auswahl und Währung in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Auswahl Kontext Objekte](../../extensibility/internals/selection-context-objects.md)
- [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)
