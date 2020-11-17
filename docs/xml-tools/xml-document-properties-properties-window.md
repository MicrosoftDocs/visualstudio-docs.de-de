---
title: XML-Dokumenteigenschaften, Eigenschaftenfenster
description: Hier erfahren Sie mehr über die XML-Dokumenteigenschaften im Eigenschaftenfenster, die grundlegende Informationen über das aktive Dokument im XML-Editor enthalten.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31098083383b1669e0fe79423c212f1f38208acc
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350230"
---
# <a name="xml-document-properties-properties-window"></a>XML-Dokumenteigenschaften, Eigenschaftenfenster

Das **Eigenschaften** fenster liefert grundlegende Informationen zu dem im XML-Editor aktiven Dokument. Die verfügbaren Eigenschaften sind vom Typ des gerade aktiven XML-Dokuments abhängig.

> [!NOTE]
> Alle XML-Dokumenteigenschaften werden in der Projektmappe gespeichert. Dadurch müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.

**Codieren**

Die Zeichencodierung für die Datei. Wenn diese Eigenschaft geändert wird, wird auch das Codierungsattribut für die XML-Deklaration geändert und umgekehrt. Die neue Codierung wird beim Speichern der Datei zum Codieren der Datei verwendet.

**Eingabe**

Das dem XSLT-Stylesheet zugeordnete Eingabedokument. Sie wird von den **XSLT starten**-Befehlen verwendet, z. B. **XML** > **XSLT ohne Debuggen starten**. Mit der Schaltfläche zum Durchsuchen ( **...** ) kann ein Dokument ausgewählt werden.

Diese Eigenschaft ist nur sichtbar, wenn eine XSLT-Datei im Editor geöffnet ist.

**Ausgabe**

Die bei der Transformation eines XML-Dokuments generierte Datei.

Wenn keine Datei angegeben wurde, wird aufgrund des `method`-Attributs für das `xsl:output`-Element, das die Dateierweiterung festlegt, ein Standarddateiname generiert. Die Standarddatei befindet sich im temporären Verzeichnis des aktuellen Benutzers.

**Schemas**

Die für die Validierung verwendeten Schemata. Die Schaltfläche öffnet das Dialogfeld **XSD-Schemata**, in dem die zu verwendenden Schemata ausgewählt werden können.

Sie können den Pfad zu den Schemata auch eingeben. Wenn mehrere Schemata angegeben sind, muss jeder Schemapfad in doppelte Anführungszeichen eingeschlossen werden.

**Stylesheet**

Die XSLT-Datei, die verwendet wird, um das Dokument zu transformieren, wenn die Befehle **XSLT-Debuggen starten** und **XSLT ohne Debuggen starten** verwendet werden. Wenn dieses Feld leer ist, verwendet der Editor den in der `xml-stylesheet`-Verarbeitungsanweisung des Dokuments angegebenen Wert, oder Sie werden zur Eingabe eines Dateinamens aufgefordert.

Beim Bearbeiten einer XSLT-Datei kann mithilfe dieser Eigenschaft angegeben werden, dass ein anderes Stylesheet verwendet werden soll, wenn der Befehl **XSLT-Debuggen starten** oder **XSLT ohne Debuggen starten** ausgewählt ist. Dies kann z. B. beim Bearbeiten eines Stylesheets der Fall sein, das in einem übergeordneten Stylesheet enthalten ist.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
