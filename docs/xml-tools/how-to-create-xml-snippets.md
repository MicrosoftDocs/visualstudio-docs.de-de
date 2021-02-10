---
title: 'Vorgehensweise: Erstellen von XML-Ausschnitten'
description: In diesem Artikel erfahren Sie, wie Sie den XML-Editor in Visual Studio verwenden, um XML-Ausschnitte zu erstellen, mit denen Sie XML-Dateien schneller erstellen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad907175f0826a5dd040f77c03517e00d4e1391c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959778"
---
# <a name="how-to-create-xml-snippets"></a>Vorgehensweise: Erstellen von XML-Ausschnitten

Mithilfe des XML-Editors können neue XML-Ausschnitte erstellt werden. Der Editor enthält einen XML-Ausschnitt mit dem Namen "Snippet". Dies ist ein vorformulierter Ausschnitt zum Erstellen neuer XML-Ausschnitte.

## <a name="to-create-a-new-xml-snippet"></a>So erstellen Sie einen neuen XML-Ausschnitt

Zum Erstellen eines neuen XML-Ausschnitts erstellen Sie eine neue XML-Datei, und verwenden Sie die Funktion **Ausschnitt einfügen**.

1. Klicken Sie im Menü **Datei** auf **Neu**, und klicken Sie anschließend auf **Datei**.

2. Klicken Sie auf **XML-Datei** und danach auf **Öffnen**.

3. Klicken Sie mit der rechten Maustaste in den Editorbereich, und wählen Sie **Ausschnitt einfügen** aus.

4. Wählen Sie in der Liste **Ausschnitt** aus, und drücken Sie die **EINGABETASTE**.

5. Nehmen Sie die gewünschten Änderungen an dem neuen Ausschnitt vor.

6. Wählen Sie im Menü **Datei** die Option **XMLFile.xml speichern** aus.

     Das Dialogfeld **Datei speichern unter** wird angezeigt.

7. Geben Sie den Namen für den neuen Ausschnitt an, und wählen Sie im Dropdownfenster **Datei speichern unter** die Option **Ausschnittdateien** aus.

8. Ändern Sie mithilfe der Dropdownliste von **Speichern in** den Speicherort der Datei in den Ordner *Eigene Dateien\Visual Studio 2005\Codeausschnitte \XML\My XML Snippets*, und klicken Sie anschließend auf **Speichern**.

## <a name="snippet-description"></a>Ausschnittbeschreibung

In diesem Abschnitt werden einige Schlüsselelemente im vorformulierten Ausschnitt beschrieben. Weitere Informationen zu Schemaelementen, die von XML-Ausschnitten verwendet werden, finden Sie unter [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType-Element

Vom Editor werden zwei Ausschnitttypen unterstützt:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

Der `Expansion`-Typ bestimmt, ob der Ausschnitt beim Aufrufen des Befehls **Ausschnitt einfügen** angezeigt wird. Der `SurroundsWith`-Typ bestimmt, ob der Ausschnitt beim Aufrufen des Befehls **Umgeben mit** angezeigt wird.

### <a name="code-element"></a>Codeelement

Das `Code`-Element definiert den XML-Text, der beim Aufrufen des Ausschnitts eingefügt wird.

> [!NOTE]
> Der XML-Ausschnitttext muss in einem `<![CDATA[...]]>`-Abschnitt eingeschlossen werden.

Es folgt das `Code`-Element, das von einem vorformulierten Ausschnitt erstellt wurde.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

Das `Code`-Element enthält drei Variablen.

- $name$ ist eine benutzerdefinierte Variable. Sie erstellt ein `name`-Element mit einem editierbaren Wert, dessen Standardwert "name" ist. Benutzerdefinierte Variablen werden mithilfe des `Literal`-Elements definiert.

- $selected$ ist eine vordefinierte Variable. Sie stellt den Text dar, der im XML-Editor vor dem Aufrufen des Ausschnitts ausgewählt wurde. Die Positionierung dieser Variablen bestimmt, an welcher Position der ausgewählte Text im Codeausschnitt angezeigt wird, der die Auswahl umgibt.

- $end$ ist eine vordefinierte Variable. Wenn der Benutzer die **EINGABETASTE** drückt, um die Bearbeitung der Codeausschnittfelder zu beenden, bestimmt diese Variable, an welche Position das Caretzeichen (^) verschoben wird.

  Das obige `Code`-Element fügt den folgenden XML-Text ein:

```xml
<test>
  <name>name</name>
</test>
```

Der Wert des name-Elements wird als editierbarer Bereich gekennzeichnet.

### <a name="literal-element"></a>Literalelement

Mithilfe des `Literal`-Elements wird der Ersetzungstext angegeben, der nach dem Einfügen in die Datei angepasst werden kann. Literalzeichenfolgen, numerische Werte und einige Variablennamen können beispielsweise als Literale deklariert werden. Sie können in einem XML-Ausschnitt beliebig viele Literale definieren, und Sie können darauf mehrfach aus dem Ausschnitt verweisen. Es folgt ein Beispiel für ein `Literal`-Element, das eine $name$-Variable definiert, deren Standardwert "name" ist.

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Literale können auch auf Funktionen verweisen. Der XML-Editor weist eine Funktion mit dem Namen **LookupPrefix** auf. Die **LookupPrefix**-Funktion sucht nach dem angegebenen Namespace-URI im Speicherort im XML-Dokument, von dem aus dieser Ausschnitt aufgerufen wurde, und gibt das Namespacepräfix zurück, das für diesen Namespace definiert wurde (falls zutreffend), und fügt den Doppelpunkt (:) in den Namen ein. Es folgt ein Beispiel für ein `Literal`-Element, das die **LookupPrefix**-Funktion verwendet.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

Die $prefix$-Variable kann anschließend an beliebiger Stelle im XML-Ausschnitt verwendet werden.

## <a name="see-also"></a>Siehe auch

- [XML-Ausschnitte](../xml-tools/xml-snippets.md)
- [How to: Verwenden von XML-Ausschnitten](../xml-tools/how-to-use-xml-snippets.md)
- [How to: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
