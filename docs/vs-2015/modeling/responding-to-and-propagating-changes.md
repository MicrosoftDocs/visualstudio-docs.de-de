---
title: Reagieren auf und propagieren von Änderungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b216e89e6a04fb38537f9c45336d07cf6df4abdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671268"
---
# <a name="responding-to-and-propagating-changes"></a>Reagieren auf und Propagieren von Änderungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn ein Element erstellt, gelöscht oder aktualisiert wird, können Sie Code schreiben, der die Änderung an andere Teile des Modells oder an externe Ressourcen wie z. b. Dateien, Datenbanken oder andere Komponenten weitergibt.

## <a name="in-this-section"></a>In diesem Abschnitt
 Beachten Sie als Richtlinie diese Verfahren in der folgenden Reihenfolge:

|Verfahren|Szenarien|Weitere Informationen finden Sie unter|
|---------------|---------------|--------------------------|
|Definieren Sie eine berechnete Domänen Eigenschaft.|Eine Domänen Eigenschaft, deren Wert aus anderen Eigenschaften im Modell berechnet wird. Beispielsweise ein Preis, der die Summe der Preise für verwandte Elemente ist.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|
|Definieren Sie eine benutzerdefinierte Speicher Domänen Eigenschaft.|Eine Domänen Eigenschaft, die in anderen Teilen des Modells oder extern gespeichert ist. Beispielsweise können Sie eine Ausdrucks Zeichenfolge in eine Struktur im Modell analysieren.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|
|Überschreiben von Änderungs Handlern, z. b. onvaluechanging und onlösch|Behalten Sie die Synchronisierung verschiedener Elemente bei, und behalten Sie die Synchronisierung externer Werte mit dem Modell bei.<br /><br /> Schränkt Werte auf definierte Bereiche ein.<br /><br /> Wird unmittelbar vor und nach dem-Eigenschafts Wert und anderen Änderungen aufgerufen. Sie können die Änderung beenden, indem Sie eine Ausnahme auslösen.|[Handler für Wertänderungen von Domäneneigenschaften](../modeling/domain-property-value-change-handlers.md)|
|Regeln|Sie können Regeln definieren, die unmittelbar vor dem Ende einer Transaktion, in der eine Änderung vorgenommen wurde, zur Ausführung in die Warteschlange eingereiht werden. Sie werden bei Rückgängigmachen oder wiederholen nicht ausgeführt. Verwenden Sie diese, um einen Teil des Stores synchron mit einem anderen zu verwenden.|[Regeln propagieren Änderungen im Modell](../modeling/rules-propagate-changes-within-the-model.md)|
|Speichern von Ereignissen|Der Modellierungs Speicher bietet Benachrichtigungen zu Ereignissen, z. b. zum Hinzufügen oder Löschen eines Elements oder Links oder zum Ändern des Werts einer Eigenschaft. Das Ereignis wird auch bei Rückgängigmachen und wiederholen ausgeführt. Verwenden Sie Store-Ereignisse, um Werte zu aktualisieren, die sich nicht im Speicher befinden.|[Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.Net-Ereignisse|Formen verfügen über Ereignishandler, die auf Mausklicks und andere Gesten reagieren. Sie müssen für jedes Objekt eine Registrierung für diese Ereignisse durchsuchen. Die Registrierung erfolgt in der Regel in einer außer Kraft Setzung von initializeingestanceresources und muss für jedes Element ausgeführt werden.<br /><br /> Diese Ereignisse treten in der Regel außerhalb einer Transaktion auf.|[Gewusst wie: Abfangen eines Klicks auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Begrenzungs Regeln|Eine Begrenzungs Regel wird speziell verwendet, um die Grenzen einer Form einzuschränken.|[BoundsRules schränken Position und Größe von Formen ein](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|Auswahlregeln|Auswahlregeln beschränken speziell das, was der Benutzer auswählen kann.|[Gewusst wie: Zugreifen auf die und Einschränken der aktuellen Auswahl](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|Onassoalisiedpropertychanged|Geben Sie die Zustände der Modellelemente mithilfe von Merkmalen von Formen und Connectors wie Schatten, Pfeilspitzen, Farbe, Linienbreite und Stil an.|[Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**Vergleichen von Regeln und Speichern von Ereignissen**
 Änderungs Benachrichtigungen, Regeln und Ereignisse werden ausgeführt, wenn Änderungen in einem Modell auftreten.

 Regeln werden normalerweise bei der End-Transaktion angewendet, in der die Änderung aufgetreten ist, und Ereignisse werden angewendet, nachdem die Änderungen in einer Transaktion übernommen wurden.

 Verwenden Sie Store-Ereignisse, um das Modell mit Objekten außerhalb des Stores zu synchronisieren, und Regeln, um die Konsistenz innerhalb des Stores aufrechtzuerhalten.

- **Erstellen von benutzerdefinierten Regeln** Sie erstellen eine benutzerdefinierte Regel als abgeleitete Klasse aus einer abstrakten Regel. Außerdem müssen Sie das Framework über die benutzerdefinierte Regel informieren. Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

- **Abonnieren von Ereignissen** Bevor Sie ein Ereignis abonnieren können, erstellen Sie einen Ereignishandler und einen Delegaten. Verwenden Sie dann die- <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> Eigenschaft, um das-Ereignis zu abonnieren. Weitere Informationen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Änderungen werden nicht mehr** ausgeführt Wenn Sie eine Transaktion rückgängig machen, werden Ereignisse ausgelöst, aber Regeln werden nicht angewendet. Wenn eine Regel einen Wert ändert und Sie diese Änderung rückgängig machen, wird der Wert während der Rückgängig-Aktion auf den ursprünglichen Wert zurückgesetzt. Wenn ein Ereignis ausgelöst wird, müssen Sie den Wert manuell auf seinen ursprünglichen Wert zurücksetzen. Weitere Informationen zu transactons und zum Rückgängigmachen finden Sie unter Gewusst [wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Übergeben von Ereignis Argumenten an Regeln und Ereignisse** An Ereignisse und Regeln wird ein `EventArgs` Parameter übergeben, der Informationen über die Änderung des Modells enthält.

## <a name="see-also"></a>Weitere Informationen
 Gewusst [wie: Abfangen eines Klick auf eine Form oder einen Decorator, der](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md) [Code zum Anpassen einer domänenspezifischen Sprache schreibt](../modeling/writing-code-to-customise-a-domain-specific-language.md)
