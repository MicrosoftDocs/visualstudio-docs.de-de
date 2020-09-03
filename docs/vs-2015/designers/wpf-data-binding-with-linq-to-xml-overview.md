---
title: Übersicht über WPF-Datenbindung mit LINQ to XML | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0cbd93f2d32c06ba52b2c47c1af8f326948609a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843927"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>Übersicht über WPF-Datenbindung mit LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Thema enthält eine Einführung in die Funktionen zur dynamischen Datenbindung im <xref:System.Xml.Linq>-Namespace. Diese Funktionen können als Datenquelle für Benutzeroberflächenelemente in WPF (Windows Presentation Foundation) verwendet werden.

## <a name="xaml-and-linq-to-xml"></a>XAML und LINQ to XML
 XAML (Extensible Application Markup Language) ist ein von Microsoft eingeführter XML-Dialekt zur Unterstützung von .NET Framework 3.0-Technologien. XAML wird in WPF zur Darstellung von Benutzeroberflächenelementen und verwandten Funktionen, wie Ereignissen und Datenbindung, verwendet. In Windows Workflow Foundation wird XAML zur Darstellung der Programmstruktur, z.B. der Programmsteuerung (*Workflows*), verwendet. Mit XAML können deklarative Aspekte einer Technologie vom zugehörigen prozeduralen Code getrennt werden, der eher das individualisierte Verhalten eines Programms definiert.

 Für die Interaktion von XAML und LINQ to XML gibt es zwei generelle Möglichkeiten:

- Da XAML-Dateien wohlgeformtes XML sind, können sie mit XML-Technologien, wie LINQ to XML, abgefragt und bearbeitet werden.

- Da LINQ to XML-Abfragen eine Datenquelle darstellen, können diese Abfragen als Datenquelle für die Datenbindung bei WPF-Benutzeroberflächenelementen verwendet werden.

  In dieser Dokumentation wird das zweite Szenario beschrieben.

## <a name="data-binding-in-the-windows-presentation-foundation"></a>Datenbindung in Windows Presentation Foundation
 Die WPF-Datenbindung ermöglicht es einem Benutzeroberflächenelement, eine seiner Eigenschaften einer Datenquelle zuzuordnen. Ein einfaches Beispiel dafür ist ein <xref:System.Windows.Controls.Label>, dessen Text den Wert einer öffentlichen Eigenschaft in einem benutzerdefinierten Objekt angibt. Die WPF-Datenbindung basiert auf den folgenden Komponenten:

|Komponente|Beschreibung|
|---------------|-----------------|
|Bindungsziel|Das Benutzeroberflächenelement, das der Datenquelle zugeordnet werden soll. Visuelle Elemente in WPF werden von der <xref:System.Windows.UIElement>-Klasse abgeleitet.|
|Zieleigenschaft|Die *Abhängigkeitseigenschaft* des Bindungsziels, das den Wert der Datenbindungsquelle wiedergibt. Abhängigkeitseigenschaften werden direkt von der <xref:System.Windows.DependencyObject>-Klasse unterstützt, von der sich <xref:System.Windows.UIElement> herleitet.|
|Bindungsquelle|Das Quellobjekt für die Werte, die dem Benutzeroberflächenelement für die Präsentation bereitgestellt werden. WPF unterstützt automatisch die folgenden Typen als Bindungsquellen: CLR-Objekte, ADO.NET-Datenobjekte, XML-Daten (aus XPath- oder LINQ to XML-Abfragen) oder ein anderes <xref:System.Windows.DependencyObject>.|
|Quellpfad|Die Eigenschaft der Bindungsquelle, aus der sich der Wert oder der Satz von Werten herleitet, der bzw. die gebunden werden sollen.|

 Die Abhängigkeitseigenschaft ist ein WPF-spezifisches Konzept, das eine dynamisch berechnete Eigenschaft eines Benutzeroberflächenelements darstellt. So besitzen Abhängigkeitseigenschaften z. B. häufig Standardwerte oder Werte, die von einem übergeordneten Element bereitgestellt werden. Diese speziellen Eigenschaften werden von Instanzen der <xref:System.Windows.DependencyProperty>-Klasse (und nicht wie bei Standardeigenschaften von Feldern) gestützt. Weitere Informationen finden Sie unter [Übersicht über Abhängigkeitseigenschaften](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).

### <a name="dynamic-data-binding-in-wpf"></a>Dynamische Datenbindung in WPF
 Standardmäßig erfolgt die Datenbindung nur, wenn das Zielbenutzeroberflächenelement initialisiert wird. Dieser Prozess wird als *einmalige* Bindung bezeichnet. Für die meisten Zwecke reicht dies nicht aus. In der Regel erfordert eine Datenbindungslösung, dass die Änderungen zur Laufzeit mit einer der folgenden Bindungen dynamisch weitergegeben werden:

- *Unidirektionale* Bindung: Diese Form der Bindung bewirkt, dass einseitige Änderungen automatisch weitergegeben werden. In den allermeisten Fällen werden so Änderungen an der Quelle im Ziel wiedergegeben, mitunter ist aber auch der umgekehrte Weg hilfreich.

- *Bidirektionale Bindung*: Änderungen an der Quelle werden automatisch an das Ziel weitergegeben, und Änderungen am Ziel werden automatisch an die Quelle weitergegeben.

  Sowohl für die unidirektionale als auch für die bidirektionale Bindung muss die Quelle einen Änderungsbenachrichtigungsmechanismus implementieren. Dies kann z.B. durch die Implementierung der <xref:System.ComponentModel.INotifyPropertyChanged>-Schnittstelle oder durch die Verwendung eines *PropertyNameChanged*-Musters für jede unterstützte Eigenschaft erfolgen.

  Weitere Informationen zur Datenbindung in WPF finden Sie unter Übersicht über [Datenbindung (WPF)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e).

## <a name="dynamic-properties-in-linq-to-xml-classes"></a>Dynamische Eigenschaften in LINQ to XML-Klassen
 Die meisten LINQ to XML-Klassen eignen sich nicht als richtige dynamische WPF-Datenquellen: Einige der nützlichsten Informationen sind nur über Methoden (und nicht über Eigenschaften) verfügbar, und Eigenschaften in diesen Klassen implementieren keine Änderungsbenachrichtigungen. Zur Unterstützung der WPF-Datenbindung macht LINQ to XML einen Satz *dynamischer Eigenschaften* verfügbar.

 Diese dynamischen Eigenschaften sind spezielle Laufzeiteigenschaften, die die Funktionalität vorhandener Methoden und Eigenschaften in den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement> duplizieren. Sie wurden diesen Klassen einzig und allein mit dem Ziel hinzufügt, sie als dynamische Datenquellen für WPF verwenden zu können. Aus diesem Grund implementieren alle diese dynamischen Eigenschaften Änderungsbenachrichtigungen. Eine ausführliche Erläuterung dieser dynamischen Eigenschaften finden Sie im nächsten Abschnitt, [Dynamische Eigenschaften in LINQ to XML](../designers/linq-to-xml-dynamic-properties.md).

> [!NOTE]
> Viele der öffentlichen Standardeigenschaften in den verschiedenen Klassen im <xref:System.Xml.Linq>-Namespace können für die einmalige Bindung verwendet werden. Bedenken Sie dabei aber, dass bei diesem Schema weder die Quelle noch das Ziel dynamisch aktualisiert werden.

### <a name="accessing-dynamic-properties"></a>Zugreifen auf dynamische Eigenschaften
 Auf die dynamischen Eigenschaften in den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement> kann nicht wie auf Standardeigenschaften zugegriffen werden. So gilt z. B. für CLR-kompatible Sprachen wie C# Folgendes:

- Auf die Eigenschaften kann zur Kompilierzeit nicht direkt zugegriffen werden. Dynamische Eigenschaften sind für den Compiler und Visual Studio IntelliSense nicht sichtbar.

- Die Eigenschaften können zur Laufzeit mit .NET-Reflektion weder gefunden noch verwendet werden. Selbst zur Laufzeit handelt es sich bei ihnen nicht um Eigenschaften im eigentlichen CLR-Sinn.

  In C# ist der Zugriff auf dynamische Eigenschaften zur Laufzeit nur über die vom <xref:System.ComponentModel>-Namespace bereitgestellten Funktionen möglich.

  Im Unterschied dazu kann auf die dynamischen Eigenschaften in einer XML-Quelle über eine unkomplizierte Notation in der folgenden Form zugegriffen werden:

```
<object>.<dynamic-property>
```

 Die dynamischen Eigenschaften für diese beiden Klassen ergeben entweder einen Wert, der direkt verwendet werden kann, oder einen Indexer, der mit einem Index bereitgestellt werden muss, damit der resultierende Wert oder die resultierende Auflistung von Werten abgerufen werden kann. Für den letzteren Fall gilt folgende Syntax:

```
<object>.<dynamic-property>[<index-value>]
```

 Weitere Informationen finden Sie unter [Dynamische Eigenschaften in LINQ to XML](../designers/linq-to-xml-dynamic-properties.md).

 Zur Implementierung der dynamischen WPF-Bindung werden die dynamischen Eigenschaften zusammen mit den vom <xref:System.Windows.Data>-Namespace bereitgestellten Funktionen, insbesondere der <xref:System.Windows.Data.Binding>-Klasse, verwendet.

## <a name="see-also"></a>Weitere Informationen
 [WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md) [LINQ to XML dynamischen Eigenschaften](../designers/linq-to-xml-dynamic-properties.md) [XAML in WPF](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) - [Datenbindung (WPF)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e) [mithilfe von Workflow Markup](https://msdn2.microsoft.com/library/ms735921(vs.90).aspx)
