---
title: Formatspezifizierer in c# | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6085ba95d3880417e517530069734052741113e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682484"
---
# <a name="format-specifiers-in-c"></a>Formatspezifizierer in C\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das Format ändern, in dem ein Wert im Fenster **Überwachen** mithilfe von Formatbezeichnern angezeigt wird. Formatbezeichner können im Fenster **Direkt** , im Fenster **Befehl** und sogar in den Quellcodefenstern verwendet werden. Wenn Sie in einen Ausdruck in diesen Fenstern anhalten, wird das Ergebnis in einem DataTip angezeigt. DataTips geben den Formatbezeichner in der DataTip-Anzeige wieder.

Zum Verwenden eines Formatbezeichners geben Sie den von einem Komma gefolgten Ausdruck ein. Fügen Sie nach dem Komma den entsprechenden Bezeichner hinzu.

## <a name="using-format-specifiers"></a>Verwenden von Formatbezeichnern

Wenn Ihr Code folgendermaßen lautet:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Fügen Sie die Variable `my_var1` dem Fenster "Überwachen" hinzu (beim Debugging, **Debuggen/Fenster/Überwachen/Überwachen 1**), und legen Sie die Anzeige auf hexadezimal fest (klicken Sie im Fenster **Überwachen** mit der rechten Maustaste auf die Variable, und wählen Sie **Hexadezimale Anzeige**aus). Das Fenster über **Wachen** zeigt nun an, dass es den Wert 0x0065 enthält. Um diesen Wert als ganze Dezimalzahl und nicht als ganze Hexadezimalzahl auszudrücken, geben Sie in der Spalte "Name" nach dem Variablennamen den Dezimalformatbezeichner **, d**ein. In der Spalte "Wert" wird nun der Dezimalwert 101 angezeigt.

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

## <a name="format-specifiers"></a>Formatbezeichner

In der folgenden Tabelle wird der C#-Formatbezeichner angezeigt, die vom Debugger erkannt werden.

|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Anzeige|
|---------------|------------|--------------------------|--------------|
|ac|Erzwingen der Auswertung eines Ausdrucks. Dies kann nützlich sein, wenn die implizite Auswertung von Eigenschaften sowie implizite Funktionsaufrufe deaktiviert sind. Siehe [Side Effects and Expressions](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Meldung "Implizite Funktionsevaluierung durch den Benutzer deaktiviert"|\<value>|
|T|Ganze Dezimalzahl|0x0065|101|
|dynamic|Zeigt das angegebene Objekt mit einer dynamischen Ansicht an.|Zeigt alle Member des Objekts einschließlich der dynamischen Ansicht an.|Zeigt nur die dynamische Ansicht an.|
|h|Ganze Hexadezimalzahl|61541|0x0000F065|
|nq|Zeichenfolge ohne Anführungszeichen|"Meine Zeichenfolge"|Meine Zeichenfolge|
|hidden|Zeigt alle öffentlichen und nicht öffentlichen Member an.|Zeigt öffentliche Member an.|Zeigt alle Member an.|
|raw|Zeigt ein Element so an, wie es im Knoten für Rohdatenelemente dargestellt wird. Nur für Proxyobjekte gültig.|Wörterbuch\<T>|Unformatierte Ansicht des Wörterbuchs\<T>|
|results|Wird mit einer Variablen eines Typs verwendet, der IEnumerable oder IEnumerable implementiert \<T> , normalerweise das Ergebnis eines Abfrage Ausdrucks. Zeigt nur die das Abfrageergebnis enthaltenden Member an.|Zeigt alle Member an.|Zeigt die Elemente an, die die Bedingungen der Abfrage erfüllen.|

## <a name="see-also"></a>Weitere Informationen

- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Variablenfenster](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
