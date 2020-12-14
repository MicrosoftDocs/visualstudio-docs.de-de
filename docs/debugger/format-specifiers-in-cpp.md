---
title: Formatbezeichner im Debugger (C++) | Microsoft-Dokumentation
description: Verwenden Sie einen Formatbezeichner, um das Format zu ändern, in dem ein Wert im Fenster „Überwachen“, „Auto“ oder „Lokal“ angezeigt wird. Dieser Artikel bietet Details zur Verwendung.
ms.custom: SEO-VS-2020
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 64166768dea1da015c223a74c74440ae09a0d106
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863035"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Formatbezeichner für C++ im Visual Studio-Debugger
Mit Formatbezeichnern können Sie das Format ändern, in dem ein Wert in den Fenstern **Überwachung**, **Auto** und **Lokal** angezeigt wird.

Formatbezeichner können auch im Fenster **Direkt**, im Fenster **Befehl**, in [Ablaufverfolgungspunkten](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) und sogar in Quellcodefenstern verwendet werden. Wenn Sie einen Ausdruck in diesen Fenstern anhalten, wird das Ergebnis in einem [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) angezeigt. Die DataTip-Anzeige entspricht dem Formatbezeichner.

> [!NOTE]
> Wenn der native Debugger von Visual Studio in eine neue Debug-Engine geändert wurde, wurden einige neue Formatbezeichner hinzugefügt, während einige alte Bezeichner entfernt wurden. Der ältere Debugger wird weiterhin verwendet, wenn Sie das Interop-Debuggen (systemeigen und verwaltet) mit C++/CLI durchführen.

## <a name="set-format-specifiers"></a>Festlegen von Formatbezeichnern
Wir verwenden den folgenden Beispielcode:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Fügen Sie beim Debuggen dem Fenster **Überwachung** die Variable `my_var1` hinzu, **Debuggen** > **Fenster** > **Überwachung** > **Überwachen 1**. Klicken Sie dann mit der rechten Maustaste auf die Variable, und wählen Sie **Hexadezimale Anzeige** aus. Im Fenster **Überwachung** wird jetzt der Wert 0x0065 angezeigt. Um diesen Wert als ein Zeichen und nicht als Integer auszudrücken, klicken Sie zunächst mit der rechten Maustaste, und deaktivieren Sie **Hexadezimale Anzeige**. Fügen Sie dann den Zeichenformatbezeichner **, c** in der Spalte **Name** nach dem Variablennamen hinzu. In der Spalte **Wert** wird jetzt **101 'e'** angezeigt.

![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")

::: moniker range=">= vs-2019" 
Sie können eine Liste der verfügbaren Formatbezeichner anzeigen und Formatbezeichner darin auswählen, indem Sie an den Wert im Fenster **Überwachung** ein Komma (,) anfügen. 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Formatbezeichner
Die folgenden Tabellen beschreiben die Formatbezeichner, die Sie in Visual Studio verwenden können. Fett formatierte Bezeichner werden nur für den neuen Debugger unterstützt und nicht für das Interop-Debuggen mit C++/CLI.

::: moniker range=">= vs-2019" 

|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|
|---------------|------------|--------------------------|---------------------|
|T|Ganze Dezimalzahl|0x00000066|102|
|o|Oktale ganze Zahl ohne Vorzeichen|0x00000066|000000000146|
|w<br /><br /> **h**|Ganze Hexadezimalzahl|102|0xcccccccc|
|X<br /><br /> **H**|Ganze Hexadezimalzahl|102|0xcccccccc|
|xb<br /><br /> **hb**|Ganze Hexadezimalzahl (ohne vorangestelltes 0x)|102|cccccccc|
|Xb<br /><br /> **Hb**|Ganze Hexadezimalzahl (ohne vorangestelltes 0x)|102|CCCCCCCC|
|k|Binäre ganze Zahl ohne Vorzeichen|25|0b00000000000000000000000000011001|
|bb|Binäre ganze Zahl ohne Vorzeichen (ohne vorangestelltes 0b)|25|00000000000000000000000000011001|
|e|Wissenschaftliche Schreibweise|25000000|2.500000e+07|
|g|Kürzere Variante aus wissenschaftlicher oder Gleitkommaschreibweise|25000000|2.5e+07|
|c|Einzelnes Zeichen|0x0065|101 'e'|
|s|const char*-Zeichenfolge (mit Anführungszeichen)|\<location> "hello world"|"hello world"|
|**sb**|const char*-Zeichenfolge (ohne Anführungszeichen)|\<location> "hello world"|hello world|
|s8|UTF-8-Zeichenfolge|\<location> "This is a UTF-8 coffee cup â˜•"|"This is a UTF-8 coffee cup ☕"|
|**s8b**|UTF-8-Zeichenfolge (ohne Anführungszeichen)|\<location> "hello world"|hello world|
|su|Unicode-Zeichenfolge (UTF-16-Codierung mit Anführungszeichen)|\<location> L"hello world"|L"hello world"<br /><br /> u"hello world"|
|sub|Unicode-Zeichenfolge (UTF-16-Codierung ohne Anführungszeichen)|\<location> L"hello world"|hello world|
|bstr|BSTR-Binärzeichenfolge (mit Anführungszeichen)|\<location> L"hello world"|L"hello world"|
|env|Umgebungsblock (doppelt nullterminierte Zeichenfolge)|\<location> L"=::=::\\\\"|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|UTF-32-Zeichenfolge (mit Anführungszeichen)|\<location> U"hello world"|u"hello world"|
|**s32b**|UTF-32-Zeichenfolge (ohne Anführungszeichen)|\<location> U"hello world"|hello world|
|**en**|enum|Samstag(6)|Samstag|
|**hv**|Zeigertyp - gibt an, dass der überprüfte Zeigerwert das Ergebnis der Heapzuweisung eines Arrays ist, z. B. `new int[3]`.|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|Unterdrückt die Speicheradresse eines Zeigers auf ein Objekt.|\<location>, {member=value...}|{member=value...}|
|**nd**|Es werden nur die Basisklasseninformationen angezeigt, die abgeleiteten Klassen werden ignoriert.|`(Shape*) square` enthält die Basisklassen- und abgeleitete Klasseninformationen|Zeigt nur Basisklasseninformationen an|
|hr|HRESULT oder Win32-Fehlercode. Dieser Bezeichner wird nicht mehr für HRESULTs benötigt, da er vom Debugger automatisch decodiert wird.|S_OK|S_OK|
|wc|Fensterklassenflag|0x0010|WC_DEFAULTCHAR|
|wm|Windows-Meldungsnummern|16|WM_CLOSE|
|nr|"Raw View"-Element unterdrücken|
|nvo|"Raw View"-Element nur für numerische Werte anzeigen|
|!|Rohdatenformat, jegliche Ansichtsanpassungen für den Datentyp werden ignoriert.|\<customized representation>|4|

::: moniker-end

::: moniker range="vs-2017" 

|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|
|---------------|------------|--------------------------|---------------------|
|T|Ganze Dezimalzahl|0x00000066|102|
|o|Oktale ganze Zahl ohne Vorzeichen|0x00000066|000000000146|
|w<br /><br /> **h**|Ganze Hexadezimalzahl|102|0xcccccccc|
|X<br /><br /> **H**|Ganze Hexadezimalzahl|102|0xcccccccc|
|c|Einzelnes Zeichen|0x0065, c|101 'e'|
|s|const char*-Zeichenfolge (mit Anführungszeichen)|\<location> "hello world"|"hello world"|
|**sb**|const char*-Zeichenfolge (ohne Anführungszeichen)|\<location> "hello world"|hello world|
|s8|UTF-8-Zeichenfolge|\<location> "This is a UTF-8 coffee cup â˜•"|"This is a UTF-8 coffee cup ☕"|
|**s8b**|UTF-8-Zeichenfolge (ohne Anführungszeichen)|\<location> "hello world"|hello world|
|su|Unicode-Zeichenfolge (UTF-16-Codierung mit Anführungszeichen)|\<location> L"hello world"|L"hello world"<br /><br /> u"hello world"|
|sub|Unicode-Zeichenfolge (UTF-16-Codierung ohne Anführungszeichen)|\<location> L"hello world"|hello world|
|bstr|BSTR-Binärzeichenfolge (mit Anführungszeichen)|\<location> L"hello world"|L"hello world"|
|env|Umgebungsblock (doppelt nullterminierte Zeichenfolge)|\<location> L"=::=::\\\\"|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|UTF-32-Zeichenfolge (mit Anführungszeichen)|\<location> U"hello world"|u"hello world"|
|**s32b**|UTF-32-Zeichenfolge (ohne Anführungszeichen)|\<location> U"hello world"|hello world|
|**en**|enum|Samstag(6)|Samstag|
|**hv**|Zeigertyp - gibt an, dass der überprüfte Zeigerwert das Ergebnis der Heapzuweisung eines Arrays ist, z. B. `new int[3]`.|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|Unterdrückt die Speicheradresse eines Zeigers auf ein Objekt.|\<location>, {member=value...}|{member=value...}|
|**nd**|Es werden nur die Basisklasseninformationen angezeigt, die abgeleiteten Klassen werden ignoriert.|`(Shape*) square` enthält die Basisklassen- und abgeleitete Klasseninformationen|Zeigt nur Basisklasseninformationen an|
|hr|HRESULT oder Win32-Fehlercode. Dieser Bezeichner wird nicht mehr für HRESULTs benötigt, da er vom Debugger automatisch decodiert wird.|S_OK|S_OK|
|wc|Fensterklassenflag|0x0010|WC_DEFAULTCHAR|
|wm|Windows-Meldungsnummern|16|WM_CLOSE|
|!|Rohdatenformat, jegliche Ansichtsanpassungen für den Datentyp werden ignoriert.|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> Wenn der Formatbezeichner **hv** vorhanden ist, versucht der Debugger, die Länge des Puffers zu bestimmen, und zeigt die betreffende Anzahl von Elementen an. Da der Debugger nicht immer die exakte Puffergröße eines Arrays finden kann, sollten Sie möglichst immer einen Größenbezeichner `(pBuffer,[bufferSize])` verwenden. Der Formatbezeichner **hv** ist nützlich, wenn die Puffergröße nicht unmittelbar verfügbar ist.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Größenbezeichner für Zeiger als Arrays
Wenn Sie über einen Zeiger für ein Objekt verfügen, das Sie als Array anzeigen möchten, können Sie eine ganze Zahl oder einen Ausdruck verwenden, um die Anzahl von Arrayelementen zu bestimmen.

|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|
|---------------|------------|---------------------------|---------------------|
|n|Dezimalzahl oder ganze **Hexadezimalzahl**|pBuffer,[32]<br /><br /> pBuffer, **[0x20]**|Zeigt `pBuffer` als Array mit 32 Elementen an.|
|**[exp]**|Ein gültiger C++-Ausdruck, der für eine ganze Zahl ausgewertet wird.|pBuffer,[bufferSize]|Zeigt pBuffer als Array von `bufferSize` Elementen an.|
|**expand(n)**|Ein gültiger C++-Ausdruck, der für eine ganze Zahl ausgewertet wird|pBuffer, expand(2)|Zeigt das dritte Element von  `pBuffer`an|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Formatbezeichner für das Interop-Debuggen mit C++/CLI
**Fett formatierte** Bezeichner werden nur zum Debuggen von systemeigenem und C++/CLI-Code unterstützt.

|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|Ganze Dezimalzahl mit Vorzeichen|0xF000F065|-268373915|
|**n**|Ganze Dezimalzahl ohne Vorzeichen|0x0065|101|
|o|Oktale ganze Zahl ohne Vorzeichen|0xF065|0170145|
|w<br /><br />X|Ganze Hexadezimalzahl|61541|0x0000f065|
|**l**<br /><br />**h**|Langes oder kurzes Präfix für: d, i, u, o, x, X|00406042|0x0c22|
|**f**|Gleitkommazahl mit Vorzeichen|(3./2.), f|1.500000|
|**e**|Wissenschaftliche Notation mit Vorzeichen|(3.0/2.0)|1.500000e+000|
|**g**|Gleitkommazahl oder wissenschaftliche Schreibweise mit Vorzeichen,<br/> je nachdem, was kürzer ist|(3.0/2.0)|1.5|
|c|Einzelnes Zeichen|\<location>|101 'e'|
|s|const char* (mit Anführungszeichen)|\<location>|"hello world"|
|su|const wchar_t*<br /><br /> const char16_t\* (mit Anführungszeichen)|\<location>|L"hello world"|
|sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|hello world|
|s8|const char* (mit Anführungszeichen)|\<location>|"hello world"|
|hr|HRESULT oder Win32-Fehlercode.<br/>Dieser Bezeichner wird nicht mehr für HRESULTs benötigt, da er vom Debugger automatisch decodiert wird.|S_OK|S_OK|
|wc|Fensterklassenflag|0x00000040,|WC_DEFAULTCHAR|
|wm|Windows-Meldungsnummern|0x0010|WM_CLOSE|
|!|Rohdatenformat, jegliche Ansichtsanpassungen für den Datentyp werden ignoriert|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Formatbezeichner für Speicherbereiche beim Interop-Debuggen mit C++/CLI
Die folgende Tabelle beschreibt Formatierungssymbole, die für Speicherbereiche verwendet werden. Bezeichner für Speicherbereiche können mit beliebigen Werten oder Ausdrücken verwendet werden, die als Speicherbereiche ausgewertet werden.

|Symbol|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|
|------------|------------|--------------------------|---------------------|
|**ma**|64 ASCII-Zeichen|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|
|**m**|16 Bytes im Hexadezimalformat, gefolgt von 16 ASCII-Zeichen|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mb**|16 Bytes im Hexadezimalformat, gefolgt von 16 ASCII-Zeichen|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mw**|8 Wörter|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**md**|4 Doppelwörter|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**mq**|2 Vierfachwörter|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**mu**|2-Byte-Zeichen (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Größenbezeichner für Zeiger als Arrays beim Interop-Debuggen mit C++/CLI
Wenn Sie einen Zeiger für ein Objekt haben, das Sie als Array anzeigen möchten, können Sie eine ganze Zahl verwenden, um die Anzahl von Arrayelementen zu bestimmen.

|Bezeichner|Format|expression|Angezeigter Wert|
|---------------|------------|----------------|---------------------|
|n|Ganze Dezimalzahl|pBuffer[32]|Zeigt `pBuffer` als Array mit 32 Elementen an.|