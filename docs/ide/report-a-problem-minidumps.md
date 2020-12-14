---
title: Erstellen von Minidumps mit allen Aufruflisten
description: Hier erfahren Sie, wie Sie Minidumps für einen Visual Studio-Prozess erstellen, die Informationen für alle Aufruflisten enthalten.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: d5cf6add1a20a0ee45ec69ade0d5f2839483bb9f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560875"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Erstellen von Minidumps für einen Visual Studio-Prozess mit allen Aufruflisten

In einigen Fällen kann Microsoft einen Minidump eines laufenden Visual Studio-Prozesses mit Informationen für alle Aufruflisten anfordern. Um diese Informationen zu erfassen, gehen Sie wie folgt vor:

## <a name="create-the-minidump-file"></a>Erstellen der Minidumpdatei

1. Starten Sie eine neue Instanz von Visual Studio.
1. Wählen Sie im Hauptmenü die Optionen **Debuggen** > **An den Prozess anhängen** aus.
1. Aktivieren Sie die relevanten Kontrollkästchen **Verwaltet** und **Nativ**, und klicken Sie auf **Anfügen**.

   ![Anhängen an den Prozess](../ide/media/attach-to-process.png)

1. Wählen Sie aus der Liste der ausgeführten Prozesse die andere Visual Studio-Instanz für den Anfügevorgang aus.
1. Klicken Sie im Hauptmenü auf **Debuggen** > **Alle unterbrechen**.
1. Klicken Sie im Hauptmenü auf **Debuggen** > **Speicherabbild speichern unter**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Abrufen der Aufruflisten aus dem Minidump

1. Öffnen Sie die Speicherabbilddatei in Visual Studio.
1. Navigieren Sie zu **Extras**  >  **Optionen**  >  **Debuggen**  >  **Symbole**, und stellen Sie sicher, dass **Microsoft-Symbolserver** unter **Speicherorte für Symboldateien (.pdb)** aktiviert ist.
1. Öffnen Sie das **Befehlsfenster** (**Ansicht** > **Weitere Fenster** > **Befehlsfenster**).
1. Geben Sie „~*k“ ein. Im Fenster werden die Aufruflisten aller Threads angezeigt.
1. Kopieren Sie den gesamten Text aus dem Befehlsfenster, und speichern Sie ihn in einer Textdatei.
1. Fügen Sie die TXT-Datei an den Fehler an.
