---
title: Anzeigen von Arbeitsspeicher für Variablen im Debugger | Microsoft-Dokumentation
description: Es wird beschrieben, wie Sie das Fenster „Arbeitsspeicher“ beim Debuggen verwenden, um den von Ihrer App genutzten Platz im Arbeitsspeicher anzuzeigen. In anderen Fenstern werden Variablen und der zugehörige Ort im Arbeitsspeicher angezeigt.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c39024e32c899310b88c1b0583d5b292b063937
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903108"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Verwenden des Fensters „Arbeitsspeicher“ im Visual Studio-Debugger (C#, C++, Visual Basic, F#)

Beim Debuggen wird im Fenster **Arbeitsspeicher** der Speicherplatz des Arbeitsspeichers angezeigt, der von Ihrer App genutzt wird.

Im Debugger werden in Fenstern wie **Überwachung**, **Auto**, **Lokal** und im Dialogfeld **Schnellüberwachung** Variablen angezeigt, die an bestimmten Orten im Arbeitsspeicher gespeichert sind. Das Fenster **Arbeitsspeicher** enthält die Gesamtübersicht. Die Arbeitsspeicheransicht ist besonders hilfreich beim Untersuchen von großen Datenmengen (z. B. Puffer oder umfangreiche Zeichenfolgen), die in den anderen Fenstern nicht gut dargestellt werden.

Das Fenster **Arbeitsspeicher** ist nicht allein auf die Anzeige von Daten beschränkt. In diesem Fenster wird der gesamte Inhalt des Arbeitsspeichers angezeigt, z. B. Daten, Code oder zufällig verteilte Objekte im nicht zugewiesenen Arbeitsspeicher.

Für das Skript- oder SQL-Debuggen ist das Fenster **Arbeitsspeicher** nicht verfügbar. Das Konzept eines Arbeitsspeichers wird bei diesen Sprachen nicht erkannt.

## <a name="open-a-memory-window"></a>Öffnen des Fensters „Arbeitsspeicher“

Wie bei anderen Debuggerfenstern auch, ist das Fenster **Arbeitsspeicher** nur während einer Debugsitzung verfügbar.

>[!IMPORTANT]
>Zum Aktivieren des Fensters **Arbeitsspeicher** muss unter **Tools** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debuggen** > **Allgemein** die Option **Debugging auf Adressebene aktivieren** ausgewählt sein.

**So öffnen Sie ein Arbeitsspeicherfenster**

1. Stellen Sie sicher, dass unter **Tools** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debuggen** > **Allgemein** die Option **Debugging auf Adressebene aktivieren** aktiviert ist.

1. Starten Sie das Debuggen, indem Sie den grünen Pfeil auswählen, **F5** drücken oder **Debuggen** > **Debuggen starten** auswählen.

2. Wählen Sie unter **Debuggen** > **Windows** > **Arbeitsspeicher** die Option **Arbeitsspeicher 1**, **Arbeitsspeicher 2**, **Arbeitsspeicher 3** oder **Arbeitsspeicher 4** aus. (Bei einigen Editionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist nur ein Fenster vom Typ **Arbeitsspeicher** verfügbar.)

## <a name="move-around-in-the-memory-window"></a>Navigieren im Fenster „Arbeitsspeicher“

Da der Adressraum eines Computers sehr umfangreich ist, kann es leicht passieren, dass Sie sich beim Scrollen im Fenster **Arbeitsspeicher** verirren.

Höhere Speicheradressen werden unten im Fenster angezeigt. Scrollen Sie nach unten, um eine höhere Adresse anzuzeigen. Scrollen Sie nach oben, um eine niedrigere Adresse anzuzeigen.

Sie können im Fenster **Arbeitsspeicher** direkt auf eine angegebene Adresse zugreifen, indem Sie Drag & Drop verwenden oder die Adresse im Feld **Adresse** eingeben. Im Feld **Adresse** werden alphanumerische Adressen sowie Ausdrücke akzeptiert, die als Adressen ausgewertet werden können, z. B. `e.User.NonroamableId`.

Wählen Sie das Symbol **Automatisch neu auswerten** mit dem abgerundeten Pfeil aus, um eine sofortige erneute Auswertung eines Ausdrucks im Feld **Adresse** zu erzwingen.

Im Fenster **Arbeitsspeicher** werden Ausdrücke vom Typ **Adresse** standardmäßig als Live-Ausdrücke behandelt, die während der Ausführung der App neu ausgewertet werden. Live-Ausdrücke können beispielsweise hilfreich sein, um den Arbeitsspeicher anzuzeigen, der von einer Zeigervariablen belegt wird.

**Verwenden Sie Drag & Drop wie folgt zum Zugreifen auf einen Ort im Arbeitsspeicher:**

1. Wählen Sie in einem beliebigen Debuggerfenster eine Speicheradresse oder eine Zeigervariable aus, die eine Speicheradresse enthält.

2. Ziehen Sie die Adresse oder den Zeiger in das Fenster **Arbeitsspeicher**. Diese Adresse wird dann im Feld **Adresse** angezeigt, und das Fenster **Arbeitsspeicher** wird angepasst, um die Adresse oben anzuzeigen.

**Greifen Sie auf einen Ort des Arbeitsspeichers zu, indem Sie diesen im Feld „Adresse“ eingeben:**

- Geben oder fügen Sie die Adresse oder den Ausdruck im Feld **Adresse** ein, und drücken Sie die **EINGABETASTE**, oder wählen Sie in der Dropdownliste des Felds **Adresse** den entsprechenden Eintrag aus. Das Fenster **Arbeitsspeicher** wird angepasst, um die Adresse oben anzuzeigen.

## <a name="customize-the-memory-window"></a>Anpassen des Fensters „Arbeitsspeicher“

Standardmäßig wird der Inhalt des Arbeitsspeichers in Form einer 1-Byte-Ganzzahl im Hexadezimalformat angezeigt, und die Anzahl angezeigter Spalten richtet sich nach der Fensterbreite. Die Art und Weise der Anzeige des Speicherinhalts im Fenster **Arbeitsspeicher** kann angepasst werden.

**So ändern Sie das Format des Speicherinhalts:**

- Klicken Sie mit der rechten Maustaste in das Fenster **Arbeitsspeicher**, und wählen Sie im Kontextmenü die gewünschten Formate aus.

**So ändern Sie die Anzahl der Spalten im Fenster „Arbeitsspeicher“:**

- Wählen Sie den Dropdownpfeil neben dem Feld **Spalten** und dann die Anzahl von anzuzeigenden Spalten aus. Sie können auch **Auto** auswählen, um die automatische Anpassung anhand der Fensterbreite zu aktivieren.

Wenn sich der Inhalt des Fensters **Arbeitsspeicher** während der Ausführung der App nicht ändern soll, können Sie die Live-Auswertung von Ausdrücken deaktivieren.

**So schalten Sie die Liveauswertung um:**

- Klicken Sie mit der rechten Maustaste in das Fenster **Arbeitsspeicher**, und wählen Sie im Kontextmenü die Option **Automatisch neu auswerten** aus.

  >[!NOTE]
  >Die Live-Auswertung von Ausdrücken ist ein Umschalter, der standardmäßig aktiviert ist. Wenn Sie die Option **Automatisch neu auswerten** auswählen, wird sie also deaktiviert. Wenn Sie **Automatisch neu auswerten** erneut auswählen, wird die Option wieder aktiviert.

Die Symbolleiste am oberen Rand des Fensters **Arbeitsspeicher** kann angezeigt oder ausgeblendet werden. Bei ausgeblendeter Symbolleiste haben Sie keinen Zugriff auf das Feld **Adresse** oder andere Tools.

**Blenden Sie die Symbolleiste wie folgt ein oder aus:**

- Klicken Sie mit der rechten Maustaste in das Fenster **Arbeitsspeicher**, und wählen Sie im Kontextmenü die Option **Symbolleiste anzeigen** aus. Je nach ihrem vorherigen Zustand wird die Symbolleiste ein- bzw. ausgeblendet.

## <a name="follow-a-pointer-through-memory"></a>Verfolgen eines Zeigers im Arbeitsspeicher

In Apps, die im nativen Code geschrieben wurden, können Sie als Live-Ausdrücke Registernamen verwenden. Zur Verfolgung des Stapels können Sie z. B. den Stapelzeiger verwenden.

**So verfolgen Sie einen Zeiger im Arbeitsspeicher:**

1. Geben Sie im Fenster **Arbeitsspeicher** im Feld **Adresse** einen Zeigerausdruck ein, der im aktuellen Bereich enthalten ist. Je nach verwendeter Sprache müssen Sie u. U. den entsprechenden Verweis aufheben.

2. Drücken Sie die **EINGABETASTE**.

   Wenn Sie einen Debugbefehl verwenden, z. B. **Einzelschritt**, ändert sich die Arbeitsspeicheradresse, die im Feld **Adresse** und oben im Fenster **Arbeitsspeicher** angezeigt wird, bei einer Änderung des Zeigers automatisch.

## <a name="see-also"></a>Siehe auch
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)