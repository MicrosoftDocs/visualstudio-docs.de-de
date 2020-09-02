---
title: Kulturspezifische Klassen für globale Windows Forms und Web Forms | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c2d048387e4e81763a63b5bf010c36c87beeacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665906"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Kulturspezifische Klassen für globale Windows Forms und Web Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jede Kultur verfügt über unterschiedliche Konventionen für die Anzeige von Datumsangaben, Uhrzeiten, Zahlen, Währungen und sonstigen Informationen. Der Namespace <xref:System.Globalization> enthält Klassen, die zum Ändern der Anzeige kulturspezifischer Werte verwendet werden können, z.B. <xref:System.Globalization.DateTimeFormatInfo>, **Calendar** und <xref:System.Globalization.NumberFormatInfo>.

## <a name="using-the-culture-setting"></a>Verwenden der Kultureinstellung
 In den meisten Fällen werden Sie jedoch die Kultureinstellung verwenden, die entweder in der Anwendung oder in der Systemsteuerung unter **Regionale Einstellungen** gespeichert ist, um die Konventionen zur Laufzeit automatisch zu ermitteln und die Informationen entsprechend zu formatieren. Weitere Informationen zum Festlegen der Kultur finden Sie unter [Gewusst wie: Festlegen der Kultur und Benutzeroberflächenkultur für die Windows Forms-Globalisierung](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) oder [Gewusst wie: Festlegen der Kultur und Benutzeroberflächenkultur für die Globalisierung von ASP.NET-Webseiten](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). Klassen, die die Informationen automatisch entsprechend der Kultureinstellung formatieren, werden als kulturspezifisch bezeichnet. Einige kulturspezifische Methoden sind <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName> und <xref:System.String.Format%2A?displayProperty=fullName>. Einige kulturspezifische Funktionen (in Visual Basic) sind `MonthName` und `WeekDayName`.

 Zum Beispiel zeigt der folgende Code, wie Sie die Methode <xref:System.IFormattable.ToString%2A> zum Formatieren von Währungen für die aktuelle Kultur verwenden können:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))

```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

 Wenn die Kultur „fr-FR“ festgelegt ist, wird Folgendes im Ausgabefenster angezeigt:

 `100,00`

 Wenn die Kultur „en-US“ festgelegt ist, wird Folgendes im Ausgabefenster angezeigt:

 `$100.00`

## <a name="see-also"></a>Weitere Informationen
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName> <xref:System.Globalization.DateTimeFormatInfo>
 <xref:System.Globalization.NumberFormatInfo>
 <xref:System.Globalization.Calendar>
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>
 <xref:System.String.Format%2A?displayProperty=fullName>
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
