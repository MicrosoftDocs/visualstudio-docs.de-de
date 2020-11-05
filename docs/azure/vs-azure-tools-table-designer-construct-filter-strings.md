---
title: Erstellen von Filterzeichenfolgen für den Tabellen-Designer | Microsoft Docs
description: Erstellen von Filterzeichenfolgen für den Tabellen-Designer
author: ghogen
manager: jillfra
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 30e9a347be1a3b35e69d2c72d141873c62dcdeb3
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398604"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Erstellen von Filterzeichenfolgen für den Tabellen-Designer
## <a name="overview"></a>Übersicht
Wenn Sie Daten in einer Azure-Tabelle filtern möchten, die im **Tabellen-Designer** von Visual Studio angezeigt wird, müssen Sie eine Filterzeichenfolge erstellen und in das Filterfeld eingeben. Die Syntax der Filterzeichenfolge wird von den WCF Data Services definiert und ist mit einer SQL WHERE-Klausel vergleichbar. Sie wird jedoch über eine HTTP-Anforderung an den Tabellenspeicherdienst gesendet. Der **Tabellen-Designer** nimmt die erforderliche Codierung vor, sodass Sie zum Filtern nach einem gewünschten Eigenschaftswert nur den Eigenschaftennamen, den Vergleichsoperator, den Kriterienwert und optional einen booleschen Operator im Filterfeld eingeben müssen. Die $filter-Abfrageoption muss nicht eingeschlossen werden, wie es beim Erstellen einer URL zur Tabellenabfrage über die [Referenz zur REST-API der Speicherdienste](/rest/api/storageservices/) notwendig wäre.

Die WCF Data Services basieren auf dem [Open Data Protocol](https://www.odata.org/) (OData). Einzelheiten zur Filtersystemabfrage-Option ( **$filter** ) finden Sie in der [Spezifikation zu OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).

## <a name="comparison-operators"></a>Vergleichsoperatoren
Die folgenden logischen Operatoren werden für alle Eigenschaftentypen unterstützt:

| Logischer Operator | Beschreibung | Filterzeichenfolge (Beispiel) |
| --- | --- | --- |
| eq |Gleich |Ort eq 'Redmond' |
| gt |Größer als |Preis gt 20 |
| ge |Größer als oder gleich |Preis ge 10 |
| lt |Kleiner als |Preis lt 20 |
| le |Kleiner als oder gleich |Preis le 100 |
| ne |Ungleich |Ort ne 'London' |
| und |Und |Preis le 200 and Preis gt 3,5 |
| oder |oder |Preis le 3,5 or Preis gt 200 |
| not |Not |not isAvailable |

Wenn Sie eine Filterzeichenfolge erstellen, sind die folgenden Regeln wichtig:

* Verwenden Sie die logischen Operatoren, um eine Eigenschaft mit einem Wert zu vergleichen. Es ist nicht möglich, eine Eigenschaft mit einem dynamischen Wert zu vergleichen; eine Seite des Ausdrucks muss eine Konstante sein.
* Bei allen Teilen der Filterzeichenfolge ist die Groß-/Kleinschreibung zu beachten.
* Der konstante Wert muss den gleichen Datentyp besitzen wie die Eigenschaft, damit vom Filter gültige Ergebnisse zurückgegeben werden. Weitere Informationen zu unterstützten Eigenschaftentypen finden Sie unter [Grundlegendes zum Tabellenspeicherdienst-Datenmodell](/rest/api/storageservices/Understanding-the-Table-Service-Data-Model).

## <a name="filtering-on-string-properties"></a>Filtern nach Zeichenfolgeneigenschaften
Wenn Sie nach Zeichenfolgeneigenschaften filtern, schließen Sie die Zeichenfolgenkonstante in einfache Anführungszeichen ein.

Im folgenden Beispiel wird nach der **PartitionKey** -Eigenschaft und der **RowKey** -Eigenschaft gefiltert. Zusätzliche nicht schlüsselbezogene Eigenschaften können auch der Filterzeichenfolge hinzugefügt werden:

```
PartitionKey eq 'Partition1' and RowKey eq '00001'
```

Sie können jeden Filterausdruck in Klammern einschließen, obwohl dies nicht erforderlich ist:

```
(PartitionKey eq 'Partition1') and (RowKey eq '00001')
```

Der Tabellenspeicherdienst unterstützt keine Platzhalterabfragen, und sie werden auch nicht im Tabellen-Designer unterstützt. Sie können jedoch den Präfixabgleich ausführen, indem Sie für das gewünschte Präfix Vergleichsoperatoren verwenden. Im folgenden Beispiel werden Entitäten mit einer LastName-Eigenschaft zurückgegeben, die mit dem Buchstaben 'A' beginnt:

```
LastName ge 'A' and LastName lt 'B'
```

## <a name="filtering-on-numeric-properties"></a>Filtern nach numerischen Eigenschaften
Wenn Sie nach einer ganzen Zahl oder einer Gleitkommazahl filtern möchten, geben Sie die Zahl ohne Anführungszeichen an.

In diesem Beispiel werden alle Entitäten mit einer Alterseigenschaft zurückgegeben, deren Wert größer als 30 ist:

```
Age gt 30
```

In diesem Beispiel werden alle Entitäten mit einer AmountDue-Eigenschaft zurückgegeben, deren Wert kleiner oder gleich 100,25 ist:

```
AmountDue le 100.25
```

## <a name="filtering-on-boolean-properties"></a>Filtern nach booleschen Eigenschaften
Geben Sie zum Filtern nach einem booleschen Wert **true** oder **false** ohne Anführungszeichen ein.

Im folgenden Beispiel werden alle Entitäten zurückgegeben, bei denen die IsActive-Eigenschaft auf **true** festgelegt ist:

```
IsActive eq true
```

Sie können auch diesen Filterausdruck ohne den logischen Operator schreiben. Im folgenden Beispiel gibt der Tabellenspeicherdienst ebenfalls alle Entitäten zurück, in denen IsActive **true** ist:

```
IsActive
```

Mit dem not-Operator können alle Entitäten zurückgegeben werden, bei denen IsActive "false" ergibt:

```
not IsActive
```

## <a name="filtering-on-datetime-properties"></a>Filtern nach DateTime-Eigenschaften
Um nach einem DateTime-Wert zu filtern, geben Sie das Schlüsselwort **datetime** an, auf das die Datums-/Uhrzeitkonstante in einfachen Anführungszeichen folgt. Die Datum-/Uhrzeitkonstante muss im kombiniertem UTC-Format vorliegen, wie in [Formatieren von DateTime-Eigenschaftswerten](/rest/api/storageservices/Formatting-DateTime-Property-Values)beschrieben.

Im folgenden Beispiel werden Entitäten zurückgegeben, bei denen die CustomerSince-Eigenschaft gleich dem 10. Juli 2008 ist:

```
CustomerSince eq datetime'2008-07-10T00:00:00Z'
```
