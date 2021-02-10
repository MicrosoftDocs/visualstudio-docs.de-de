---
title: Optionen, Text-Editor, XML, Sonstiges
description: Hier erfahren Sie, wie Sie mit der Seite „Sonstiges“ im XAML-Abschnitt die Einstellungen des XML-Editors für die automatische Vervollständigung und das Schema ändern.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: d3451a2a8d64edbf0f9000c9e58387704ed815ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932267"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Optionen, Text-Editor, XML, Sonstiges

Verwenden Sie die Optionsseite **Sonstiges**, um die Einstellungen für die automatische Vervollständigung und das Schema für den XML-Editor zu ändern. Wählen Sie für den Zugriff auf sonstige XML-Optionen **Extras** > **Optionen** > **Text-Editor** > **XML** und dann **Sonstiges** aus.

## <a name="auto-insert"></a>Automatisch einfügen

**Tags schließen**

Der Text-Editor fügt beim Erstellen von XML-Elementen Endtags hinzu. Wenn das Anfangstag eines Elements ausgewählt ist, fügt der Editor das passende Endtag mit dem entsprechenden Namespacepräfix hinzu. Dieses Kontrollkästchen ist standardmäßig aktiviert.

**Attributanführungszeichen**

Beim Erstellen von XML-Attributen fügt der Editor die Zeichen `="` und `"` ein und platziert das Caretzeichen ( **^** ) innerhalb der Anführungszeichen. Dieses Kontrollkästchen ist standardmäßig aktiviert.

**Namespacedeklarationen**

Der Editor fügt die benötigten Namespacedeklarationen automatisch an den entsprechenden Stellen ein. Dieses Kontrollkästchen ist standardmäßig aktiviert.

**Sonstige Markups (Kommentare, CDATA)**

Kommentare, CDATA, DOCTYPE, Verarbeitungsanweisungen sowie sonstige Markupelemente werden automatisch vervollständigt. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## <a name="network"></a>Netzwerk

**DTDs und Schemata automatisch herunterzuladen**

Schemata und Dokumenttypdefinitionen (DTDs) werden automatisch von den HTTP-Adressen heruntergeladen. Diese Funktion verwendet System.Net mit aktivierter automatischer Proxyservererkennung. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## <a name="outlining"></a>Gliedern

**Beim Öffnen von Dateien in Gliederungsmodus wechseln**

Aktiviert die Gliederungsfunktion beim Öffnen von Dateien. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## <a name="caching"></a>Caching

**Schemas**

Gibt den Speicherort des Schemacaches an. Die Schaltfläche **Durchsuchen** öffnet den aktuellen Speicherort des Schemacaches in einem neuen Fenster. Der Standardspeicherort ist *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Siehe auch

- [XML-Optionen – Formatierung](options-text-editor-xml-formatting.md)
- [XML-Tools in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
