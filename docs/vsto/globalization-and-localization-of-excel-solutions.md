---
title: Globalisierung und Lokalisierung von Excel-Lösungen
description: Informieren Sie sich über besondere Überlegungen für Microsoft Office Excel-Lösungen, die auf Computern mit nicht englischen Einstellungen für Windows ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51e4a2cc4fb74309c44b8068152253de92eed0df
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847753"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalisierung und Lokalisierung von Excel-Lösungen
  Dieser Abschnitt enthält besondere Überlegungen zu Microsoft Office Excel-Projektmappen, die auf Computern ausgeführt werden, die über nicht englische Einstellungen für Windows verfügen. Die meisten Aspekte bei der Globalisierung und Lokalisierung von Microsoft Office-Projektmappen sind mit denen identisch, die beim Erstellen von anderen Arten von Projektmappen mit Visual Studio auftreten. Allgemeine Informationen finden Sie unter [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md).

 Die Hoststeuerelemente in Microsoft Office Excel funktionieren standardmäßig in allen regionalen Windows-Einstellungen ordnungsgemäß, solange alle mithilfe von verwaltetem Code übergebenen oder geänderten Daten als „Englisch (USA)“ formatiert werden. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]ausgerichtet sind, wird dieses Verhalten von der Common Language Runtime (CLR) gesteuert.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Formatieren von Daten in Excel mit verschiedenen regionalen Einstellungen
 Sie müssen sämtliche Daten, die gebietsschemaabhängige Formatierungen aufweisen, z. B. Datumsangaben und Währungen, mit dem Datenformat „Englisch (USA)“ (Gebietsschema-ID 1033) formatieren, bevor Sie sie an Microsoft Office Excel übergeben oder die Daten in Ihrem Office-Projekt aus Code lesen.

 Standardmäßig erwartet das Excel-Objektmodell bei der Entwicklung einer Office-Projektmappe in Visual Studio die Datenformatierung mit Gebietsschema-ID 1033 (dies wird auch als Sperren des Objektmodells für Gebietsschema-ID 1033 bezeichnet). Dieses Verhalten entspricht der von Visual Basic for Applications verwendeten Vorgehensweise. Allerdings können Sie dieses Verhalten in Ihren Office-Projektmappen ändern.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Verstehen, wie das Excel-Objektmodell immer die Gebiets Schema-ID 1033 erwartet
 Standardmäßig sind von Ihnen mit Visual Studio erstellte Office-Projektmappen nicht von den Gebietsschemaeinstellungen des Endbenutzers betroffen, und sie verhalten sich immer so, als ob das Gebietsschema „Englisch (USA)“ verwendet würde. Wenn Sie z. B. die <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> -Eigenschaft in Excel abrufen oder festlegen, müssen die Daten so formatiert sein, wie es die Gebietsschema-ID 1033 erwartet. Wenn Sie ein anderes Datenformat verwenden, erhalten Sie möglicherweise unerwartete Ergebnisse.

 Auch wenn Sie das Format „Englisch (USA)“ für Daten verwenden, die von verwaltetem Code übergeben oder geändert werden, interpretiert Excel die Daten gemäß der Gebietsschemaeinstellung des Endbenutzers und zeigt die Daten ordnungsgemäß an. Excel kann die Daten ordnungsgemäß formatieren, da der verwaltete Code die Gebietsschema-ID 1033 zusammen mit den Daten übergibt, wodurch angegeben wird, dass die Daten im Format „Englisch (USA)“ vorliegen und daher neu formatiert werden müssen, um mit der Gebietsschemaeinstellung des Benutzers übereinzustimmen.

 Wenn Endbenutzer z. B. ihre regionalen Optionen auf das Gebietsschema Deutsch (Deutschland) festgelegt haben, erwarten sie, dass das Datum „29. Juni 2005“ folgendermaßen formatiert wird: 29.06.2005. Wenn Ihre Projektmappe das Datum jedoch als Zeichenfolge an Excel übergibt, müssen Sie das Datum gemäß dem Format „Englisch (USA)“ formatieren: 6/29/2005. Wenn die Zelle als Datumszelle formatiert ist, zeigt Excel das Datum im Format „Deutsch (Deutschland)“ an.

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Übergeben anderer Gebiets Schema-IDs an das Excel-Objektmodell
 Die Common Language Runtime (CLR) übergibt die Gebietsschema-ID 1033 automatisch an alle Methoden und Eigenschaften im Excel-Objektmodell, die gebietsschemaabhängige Daten akzeptieren. Es gibt keine Möglichkeit, dieses Verhalten automatisch für alle Aufrufe des Objektmodells zu ändern. Sie können jedoch eine andere Gebietsschema-ID an eine bestimmte Methode übergeben, indem Sie <xref:System.Type.InvokeMember%2A> zum Aufrufen der Methode und Übergeben der Gebietsschema-ID an den *culture* -Parameter der Methode verwenden.

## <a name="localize-document-text"></a>Lokalisieren von Dokument Text
 Das Dokument, die Vorlage oder die Arbeitsmappe in Ihrem Projekt umfasst wahrscheinlich statischen Text, der getrennt von der Assembly und anderen verwalteten Ressourcen lokalisiert werden muss. Eine einfache Möglichkeit hierzu stellt das Erstellen einer Kopie des Dokuments und das anschließende Übersetzen des Texts mithilfe von Microsoft Office Word oder Microsoft Office Excel dar. Diese Vorgehensweise funktioniert auch, wenn Sie keine Änderungen am Code vornehmen, da eine beliebige Anzahl von Dokumenten mit derselben Assembly verknüpft werden kann.

 Sie müssen weiterhin sicherstellen, dass jeder Teil des Codes, der mit dem Dokumenttext interagiert, stets mit der Sprache des Texts übereinstimmt, und dass sich Lesezeichen, benannte Bereiche und andere Anzeigefelder allen neuen Formatierungen des Office-Dokuments anpassen, die hinsichtlich einer anderen Grammatik und Textlänge geändert werden mussten. Für Dokumentvorlagen, die relativ wenig Text enthalten, können Sie erwägen, den Text in Ressourcendateien zu speichern und dann zur Laufzeit zu laden.

### <a name="text-direction"></a>Text Richtung
 In Excel können Sie eine Eigenschaft des Arbeitsblatts festlegen, um den Text von rechts nach links zu rendern. Host Steuerelemente oder beliebige Steuerelemente, die `RightToLeft` über eine Eigenschaft verfügen, die im Designer platziert wird, entsprechen diesen Einstellungen zur Laufzeit automatisch. Word verfügt nicht über eine Dokument Einstellung für bidirektionalen Text (Sie ändern einfach die Textausrichtung), sodass die Steuerelemente dieser Einstellung nicht zugeordnet werden können. Stattdessen müssen Sie die Ausrichtung des Texts für jedes Steuerelement festlegen. Es ist möglich, Code zu schreiben, um alle Steuerelemente zu durchlaufen und für diese zu erzwingen, dass sie den Text von rechts nach Links rendern.

### <a name="change-culture"></a>Kultur ändern
 Ihr Anpassungscode auf Dokumentebene teilt in der Regel den primären UI-Thread von Excel. Daher wirken sich alle Änderungen, die Sie an der Threadkultur vornehmen, auf alles andere aus, das in diesem Thread ausgeführt wird. Die Änderung ist nicht auf Ihre Anpassung beschränkt.

 Windows Forms-Steuerelemente werden initialisiert, bevor VSTO-Add-Ins der Anwendungsebene von der Hostanwendung gestartet werden. In diesen Situationen sollte die Kultur vor dem Festlegen der UI-Steuerelemente geändert werden.

## <a name="install-the-language-packs"></a>Installieren der Sprachpakete
 Wenn Sie andere Einstellungen als „Englisch“ für Windows verwenden, können Sie die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Sprachpakete installieren, um [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] -Meldungen in der unter Windows ausgewählten Sprache anzuzeigen. Wenn Benutzer Ihre Projektmappen mit anderen Einstellungen als „Englisch“ für Windows ausführen, müssen sie über das richtige Sprachpaket verfügen, um Laufzeitmeldungen in derselben Sprache wie Windows anzeigen zu können. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Sprachpakete sind im [Microsoft Download Center](https://www.microsoft.com/download)verfügbar.

 Darüber hinaus sind die verteilbaren .NET Framework Language Packs für ClickOnce-Meldungen erforderlich. Die .NET Framework Language Packs sind im [Microsoft Download Center](https://www.microsoft.com/download)verfügbar.

## <a name="regional-settings-and-excel-com-calls"></a>Regionale Einstellungen und com-Aufrufe von Excel
 Sobald ein verwalteter Client eine Methode für ein COM-Objekt aufruft und dabei kulturspezifische Informationen übergeben muss, erfolgt dies über <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (Gebietsschema), das mit dem aktuellen Threadgebietsschema übereinstimmt. Das aktuelle Threadgebietsschema wird standardmäßig von den regionalen Einstellungen des Benutzers geerbt. Wenn Sie jedoch aus einer Excel-Projektmappe, die mithilfe von Office-Entwicklungstools in Visual Studio erstellt wurde, einen Aufruf an das Excel-Objektmodell senden, wird das Datenformat „Englisch (USA)“ (Gebietsschema-ID 1033) automatisch an das Excel-Objektmodell übergeben. Sie müssen sämtliche Daten, die gebietsschemaabhängige Formatierungen aufweisen, z. B. Datumsangaben und Währungen, mit dem Datenformat „Englisch (USA)“ formatieren, bevor Sie sie an Microsoft Office Excel übergeben oder die Daten aus Ihrem Projektcode lesen.

## <a name="considerations-for-storing-data"></a>Überlegungen zum Speichern von Daten
 Um sicherzustellen, dass Ihre Daten ordnungsgemäß interpretiert und angezeigt werden, sollten Sie ebenfalls berücksichtigen, dass Probleme auftreten können, wenn eine Anwendung Daten, z. B. Excel-Arbeitsblattformeln, in Zeichenfolgenliteralen (hartcodiert) anstatt in stark typisierten Objekten speichert. Sie sollten Daten verwenden, die unter Annahme eines kulturinvarianten Formats oder des Formats „Englisch (USA)“ (LCID-Wert 1033) formatiert werden.

### <a name="applications-that-use-string-literals"></a>Anwendungen, die Zeichen folgen Literale verwenden
 Hartcodierte Werte können z. B. Datumsliterale im Format „Englisch (USA)“ und Excel-Arbeitsblattformeln sein, die lokalisierte Funktionsnamen enthalten. Eine weitere Möglichkeit ist z. B. eine hartcodierte Zeichenfolge, die eine Zahl wie „1,000“ enthält. In einigen Kulturen wird dies als eintausend interpretiert, während es in anderen Kulturen als eine „1“ mit drei Nachkommastellen interpretiert wird. Mit dem falschen Format ausgeführte Berechnungen und Vergleiche führen möglicherweise zu falschen Daten.

 Excel interpretiert alle Zeichenfolgen gemäß der LCID, die mit der Zeichenfolge übergeben wird. Dies kann ein Problem darstellen, wenn das Format der Zeichenfolge nicht mit der übergebenen LCID übereinstimmt. Excel-Projektmappen, die mithilfe der Office-Entwicklungstools in Visual Studio erstellt werden, verwenden beim Übergeben sämtlicher Daten die LCID 1033 (en-US). Excel zeigt die Daten gemäß den regionalen Einstellungen und der Sprache der Excel-Benutzeroberfläche an. Visual Basic for Applications (VBA) funktioniert auch auf diese Weise. Zeichenfolgen werden als „en-US“ formatiert und VBA übergibt fast immer den Wert „0“ (sprachneutral) als LCID. Der folgende VBA-Code zeigt z. b. einen ordnungsgemäß formatierten Wert für den 12. Mai 2004 in Übereinstimmung mit der Gebiets Schema Einstellung aktueller Benutzer an:

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 Wenn derselbe Code in einer Projektmappe verwendet wird, die mit den Office-Entwicklungstools in Visual Studio erstellt und über COM-Interop an Excel übergeben wurde, liefert er dieselben Ergebnisse, wenn das Datum mit dem Format „en-US“ formatiert ist.

 Zum Beispiel:

 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]

 Sie sollten anstelle von Zeichenfolgenliteralen nach Möglichkeit stattdessen mit stark typisierten Daten arbeiten. Anstatt ein Datum z. B. in einem Zeichenfolgenliteral zu speichern, speichern Sie es als <xref:System.Double>und konvertieren es dann zur Bearbeitung in ein <xref:System.DateTime> -Objekt.

 Das folgende Codebeispiel übernimmt ein Datum, das von einem Benutzer in Zelle A5 eingegeben wird, speichert es als <xref:System.Double>und konvertiert es zum Anzeigen in ein <xref:System.DateTime> -Objekt in Zelle A7. Zelle A7 muss formatiert werden, damit sie ein Datum anzeigt.

 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]

### <a name="excel-worksheet-functions"></a>Excel-Arbeitsblatt Funktionen
 Die Namen von Arbeitsblattfunktionen werden für die meisten Sprachversionen von Excel intern übersetzt. Aufgrund möglicher sprach-und COM-Interop-Probleme wird jedoch empfohlen, nur englische Funktionsnamen in Ihrem Code zu verwenden.

### <a name="applications-that-use-external-data"></a>Anwendungen, die externe Daten verwenden
 Möglicherweise ist auch jeglicher Code, der externe Daten öffnet oder anderweitig verwendet, betroffen, z. B. Dateien mit durch Trennzeichen getrennten Werten (CSV-Dateien), die aus einem Legacysystem exportiert wurden, wenn diese Dateien in einem anderen Format als „en-US“ exportiert werden. Der Zugriff auf die Datenbank ist möglicherweise nicht beeinträchtigt, da alle Werte im binären Format vorliegen sollten, sofern die Datenbank die Daten nicht als Zeichenfolgen speichert oder Vorgänge ausführt, die kein binäres Format verwenden. Wenn Sie SQL-Abfragen mithilfe von Daten aus Excel erstellen, müssen Sie zudem möglicherweise sicherstellen, dass diese in Abhängigkeit von der verwendeten Funktion im Format „en-US“ vorliegen.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Ausrichten der mehrsprachigen Office-Benutzeroberfläche](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)