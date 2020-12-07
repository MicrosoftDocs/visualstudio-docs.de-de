---
title: Angeben der Anzahl von Iterationen in einer Testlaufeinstellung für Auslastungstests
description: Hier erfahren Sie, wie Sie die Anzahl der Iterationen angeben, die in allen Webleistungs- und Komponententests in allen Szenarios eines Auslastungstests mit dem Auslastungstest-Editor durchlaufen werden sollen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 754a5ad7612f6abbea52ea9d4bb4cb1d159f6dac
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328300"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Vorgehensweise: Angeben der Anzahl von Testiterationen in einer Testlaufeinstellung für Auslastungstests

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern. Weitere Informationen finden Sie unter [ Vorgehensweise: Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md).

Sie können mit dem **Auslastungstest-Editor** die Eigenschaft **Testiterationen** eines Laufzeiteinstellungswerts im Fenster **Eigenschaften** bearbeiten. Die Eigenschaft **Testiterationen** gibt die Anzahl der Iterationen an, die in allen Webleistungs- und Komponententests in allen Szenarios eines Auslastungstests mit dem **Auslastungstest-Editor** verwendet werden sollen.

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>So geben Sie die Anzahl der Testiterationen in einer Testlaufeinstellung an

1. Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird geöffnet und zeigt die Auslastungsteststruktur an.

2. Klicken Sie in der Auslastungsteststruktur im Ordner **Laufzeiteinstellungen** auf eine Testlaufeinstellung.

3. Wählen Sie im Menü **Ansicht** die Option **Eigenschaftenfenster** aus, um die Kategorien und Eigenschaften der Testlaufeinstellung für Auslastungstests anzuzeigen.

4. Legen Sie die Eigenschaft **Testiterationen verwenden** auf **TRUE** fest.

5. Geben Sie in der Eigenschaft **Testiterationen** eine Zahl ein, die die Anzahl der während des Auslastungstests ausgeführten Testiterationen angibt.

6. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Sie können anschließend den Auslastungstest mithilfe des neuen Werts für **Testiterationen** ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
