---
title: Angeben der Abtastrate für eine Auslastungstestlaufeinstellung
description: Hier erfahren Sie, wie Sie im Eigenschaftenfenster die Abtastrate für den Wert einer Laufzeiteinstellung mithilfe des Auslastungstest-Editors bearbeiten.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 7d591ad7cc97543f9167b698b0a5f0664e59b5c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962651"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Vorgehensweise: Angeben der Abtastrate für eine Auslastungstestlaufeinstellung

Nach dem Erstellen des Auslastungstests mit dem **Assistenten für neuen Auslastungstest** können Sie mit dem **Auslastungstest-Editor** die Eigenschaften ändern, um die Testanforderungen und -ziele zu erreichen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Mit dem **Auslastungstest-Editor** können Sie den Eigenschaftswert **Samplingrate** einer Laufzeiteinstellung im Fenster **Eigenschaften** bearbeiten. Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

Wählen Sie basierend auf der Länge des Auslastungstests einen entsprechenden Wert für die Eigenschaft **Samplingrate** für die Laufzeiteinstellung des Auslastungstests aus. Eine kleinere Samplingrate (z. B. der Standardwert von fünf Sekunden) erfordert mehr Speicherplatz in der Datenbank für die Auslastungstestergebnisse. Bei längeren Auslastungstests wird durch eine höhere Samplingrate die gesammelte Datenmenge reduziert. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Abtastrate für eine Auslastungstestlaufeinstellung](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Die folgende Tabelle enthält Richtlinien für die Samplingraten:

|Dauer des Auslastungstests|Empfohlene Samplingrate|
|-|-----------------------------|
|\< 1 Stunde|5 Sekunden|
|1 – 8 Stunden|15 Sekunden|
|8 – 24 Stunden|30 Sekunden|
|> 24 Stunden|60 Sekunden|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>So geben Sie die Leistungsindikator-Samplingrate in einer Testlaufeinstellung an

1. Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Klicken Sie in der Auslastungsteststruktur im Ordner **Laufzeiteinstellungen** auf die Laufzeiteinstellung, für die Sie die Samplingrate angeben möchten.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Kategorien und Eigenschaften der Testlaufeinstellung werden im **Eigenschaftenfenster** angezeigt.

4. Geben Sie in der Eigenschaft **Samplingrate** einen Zeitwert ein, der die Häufigkeit angibt, mit der Leistungsindikatordaten beim Auslastungstest gesammelt werden.

5. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Anschließend können Sie den Auslastungstest mit dem neuen Wert für **Samplingrate** ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
