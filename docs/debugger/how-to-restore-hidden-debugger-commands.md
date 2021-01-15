---
title: Wiederherstellen von ausgeblendeten Debuggerbefehlen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie ausgeblendete Debuggerbefehle in Visual Studio wiederherstellen. Möglicherweise blenden die IDE-Standardeinstellungen für einige Sprachen bestimmte Debuggerbefehle aus.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e761a9bcbbf2f35555ae30065cd239f4d7587ff4
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148597"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Vorgehensweise: Wiederherstellen von ausgeblendeten Debuggerbefehlen
Beim Einrichten von Visual Studio werden Sie aufgefordert, die IDE-Standardeinstellungen für Ihre bevorzugte Programmiersprache festzulegen. Möglicherweise blenden die IDE-Standardeinstellungen für einige Sprachen bestimmte Debuggerbefehle aus.

 Falls Sie ein Debuggerfeature verwenden möchten, das durch Ihre IDE-Standardeinstellungen ausgeblendet ist, können Sie dem Menü den Befehl durch folgende Prozedur wieder hinzufügen.

### <a name="to-restore-hidden-debugger-commands"></a>So stellen Sie ausgeblendete Debuggerbefehle wieder her

1. Klicken Sie in einem geöffneten Projekt im Menü **Extras** auf **Anpassen**.

2. Klicken Sie im Dialogfeld **Anpassen** auf die Registerkarte **Befehle**.

3. Wählen Sie im Dropdownfeld **Menüleiste:** das Menü **Debuggen** aus, dass den wiederhergestellten Befehl enthalten soll.

4. Klicken Sie auf die Schaltfläche **Befehl hinzufügen**.

5. Wählen Sie im Feld **Befehl hinzufügen** den Befehl aus, den Sie hinzufügen möchten, und klicken Sie auf **OK**.

6. Wiederholen Sie den vorigen Schritt, um einen weiteren Befehl hinzuzufügen.

7. Klicken Sie auf **Schließen**, wenn Sie dem Menü keine weiteren Befehle hinzufügen möchten.

    > [!WARNING]
    > Einige Menüelemente sind nur in bestimmten Debuggermodi sichtbar, etwa im Ausführmodus oder im Unterbrechungsmodus. Deshalb ist ein Element, das Sie hinzugefügt haben, nicht notwendigerweise sofort nach Ausführung dieser Schritte sichtbar.

## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Wiederherstellen von Befehlen, die im Dialogfeld Anpassen nicht verfügbar sind
 Einige Befehle, besonders solche in hierarchischen Menüs, können nicht im Dialogfeld **Anpassen** wiederhergestellt werden. Um diese Befehle wiederherzustellen, müssen Sie eine neue Auflistung von IDE-Einstellungen importieren.

#### <a name="to-import-new-ide-settings"></a>So importieren Sie neue IDE-Einstellungen

1. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**.

2. Klicken Sie auf der Seite **Willkommen beim Assistenten zum Importieren und Exportieren von Einstellungen** auf **Ausgewählte Umgebungseinstellungen importieren** und dann auf **Weiter**.

3. Auf der Seite **Aktuelle Einstellungen speichern** können Sie entscheiden, ob Sie die bestehenden Einstellungen speichern möchten. Klicken Sie anschließend auf **Weiter**.

4. Wählen Sie auf der Seite **Auflistung von Einstellungen für den Import auswählen** aus dem Ordner **Standardeinstellungen** eine Auflistung von Entwicklungseinstellungen, in der die gewünschten Befehle enthalten sind. Wenn Sie nicht wissen, für welche Auflistung Sie sich entscheiden sollen, wählen Sie **Allgemeine Entwicklungseinstellungen** oder **Visual C++-Entwicklungseinstellungen**. Darin sind die meisten Debuggerbefehle enthalten.

5. Klicken Sie auf **Weiter**.

6. Stellen Sie auf der Seite **Einstellungen für den Import auswählen** unter **Optionen** sicher, dass **Debuggen** ausgewählt ist. Deaktivieren Sie die anderen Kontrollkästchen, sofern Sie nicht noch weitere Einstellungen importieren möchten.

7. Klicken Sie auf **Fertig stellen**.

8. Überprüfen Sie auf der Seite **Importvorgang abgeschlossen** den Bereich **Details** auf Fehler, die beim Wiederherstellen der Einstellungen aufgetreten sein könnten.

9. Klicken Sie auf **Schließen**.

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)