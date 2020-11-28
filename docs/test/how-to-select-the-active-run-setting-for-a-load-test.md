---
title: Auswählen der Laufzeiteinstellung für einen Auslastungstest
description: Ein Auslastungstest kann mehrere Laufzeiteinstellungen umfassen. Laufzeiteinstellungen sind Eigenschaften, die die Art der Ausführung eines Auslastungstests beeinflussen. Lernen Sie, die aktive Ausführungseinstellung auszuwählen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87a67cb90ed48993e75dc248f23d10e982c64c43
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439861"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Vorgehensweise: Auswählen der aktiven Laufzeiteinstellungen für einen Auslastungstest

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ein Auslastungstest kann mehrere *Laufzeiteinstellungen* enthalten. Laufzeiteinstellungen sind eine Gruppe von Eigenschaften, die die Art der Ausführung eines Auslastungstests beeinflussen. Laufzeiteinstellungen werden nach Kategorien im **Eigenschaftenfenster** strukturiert. Bei der Ausführung eines Auslastungstests wird die Testlaufeinstellung verwendet, die derzeit als aktiv festgelegt ist.

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

Wenn Ihr Auslastungstest im Ordner **Laufzeiteinstellungen** nur einen Laufzeiteinstellungsknoten enthält, handelt es sich bei diesem Knoten immer um den aktiven Knoten. Wenn der Auslastungstest mehrere Testlaufeinstellungsknoten enthält, können Sie den Knoten auswählen, der bei der Ausführung des Auslastungstests verwendet werden soll. Weitere Informationen finden Sie unter [How to: Hinzufügen von weiteren Laufzeiteinstellungen zu einem Auslastungstest](../test/how-to-add-additional-run-settings-to-a-load-test.md).

Im **Auslastungstest-Editor** wird die aktive Testlaufeinstellung durch das Suffix "[Aktiv]" gekennzeichnet.

## <a name="select-the-active-run-setting"></a>Auswählen der aktiven Testlaufeinstellung

1. Öffnen Sie einen Auslastungstest.

2. Erweitern Sie den Ordner **Laufzeiteinstellungen**.

3. Klicken Sie mit der rechten Maustaste auf den Laufzeiteinstellungsknoten, der der aktive Knoten sein soll, und klicken Sie anschließend auf **Als aktiv festlegen**.

     Im **Auslastungstest-Editor** wird der betroffene Laufzeiteinstellungsknoten mit dem Suffix „[Aktiv]“ gekennzeichnet.

     Die ausgewählte Testlaufeinstellung wird und bleibt aktiv, bis Sie eine andere Testlaufeinstellung als aktiv festlegen.

> [!NOTE]
> Sie können die aktive Testlaufeinstellung überschreiben, indem Sie eine Umgebungsvariable mit dem Namen `Test.UseRunSetting=<run setting name>` festlegen. Dies ist sinnvoll, wenn Sie einen Auslastungstest von der Befehlszeile oder von einer Batchdatei aus ausführen. Sie können hierdurch verschiedene Testlaufeinstellungen auswählen, ohne den Auslastungstest zu öffnen.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Angeben der zu verwendenden Testlaufeinstellung über die Befehlszeile

Sie können die Standardtestlaufeinstellungen im Auslastungstest überschreiben, indem Sie eine Umgebungsvariable über die Befehlszeile festlegen:

**Set Test.UseRunSetting=PreProdEnvironment**

Führen Sie anschließend den Test aus:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Vorgehensweise: Hinzufügen von weiteren Laufzeiteinstellungen zu einem Auslastungstest](../test/how-to-add-additional-run-settings-to-a-load-test.md)
