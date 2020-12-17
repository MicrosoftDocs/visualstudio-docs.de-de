---
title: Debuggen einer .NET Framework-Quelle | Microsoft-Dokumentation
Description: Informationen zum Debuggen einer .NET Framework-Quelle. Sie müssen eine entsprechende Konfiguration vornehmen und Debugsymbole herunterladen.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 13a575ec2e77f1b715ec5f17324a6933d8cf0805
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398622"
---
# <a name="how-to-debug-net-framework-source"></a>Vorgehensweise: Debuggen einer .NET Framework-Quelle

Zum Debuggen einer .NET Framework-Quelle müssen die folgenden Bedingungen erfüllt sein:

- Sie müssen das Durchlaufen des .NET Framework-Quellcodes aktivieren.

- Sie müssen Zugriff auf Debugsymbole für den Code haben.

  Sie können die Debugsymbole sofort herunterladen oder Optionen für einen späteren Download festlegen. Wenn Sie die Symbole nicht sofort herunterladen, werden sie beim nächsten Starten des Debuggens Ihrer App heruntergeladen. Während des Debuggens können Sie auch das Fenster **Module** oder **Aufrufliste** verwenden, um Symbole herunterzuladen und zu laden.

### <a name="to-enable-stepping-into-net-framework-source"></a>So aktivieren Sie das Durchlaufen des .NET Framework-Quellcodes

1. Wählen Sie unter **Extras** (oder **Debuggen**) > **Optionen** > **Debugging** > **Allgemein** die Option **Durchlaufen des .NET Framework-Quellcodes aktivieren** aus.

   - Wenn Sie Nur Mein Code aktiviert haben, wird Ihnen in einem Warndialogfeld mitgeteilt, dass Nur mein Code jetzt deaktiviert wird. Klicken Sie auf **OK**.

   - Wenn Sie keinen lokalen Symbolcache festgelegt haben, wird in einem Warnungsdialogfeld angezeigt, dass ein Standardsymbolcache festgelegt wurde. Klicken Sie auf **OK**.

1. Wählen Sie **OK** aus, um das Dialogfeld **Optionen** zu schließen.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>So legen Sie Symbolquellspeicherorte und das Ladeverhalten fest oder ändern diese(s)

1. Wählen Sie unter **Extras** (oder **Debuggen**) > **Optionen** > **Debugging** die Kategorie **Symbole** aus.

1. Wählen Sie auf der Seite **Symbole** unter **Speicherorte für Symboldateien (.pdb)** die Option **Microsoft-Symbolserver** aus, um auf Symbole von öffentlichen Microsoft-Symbolservern zuzugreifen. Wählen Sie die Symbolleistenschaltflächen aus, um weitere Symbolspeicherorte hinzuzufügen und die Ladereihenfolge zu ändern.

1. Um Ihren lokalen Symbolcache zu ändern, bearbeiten Sie den Speicherort, oder navigieren Sie zu einem anderen Speicherort unter **Symbole in diesem Verzeichnis zwischenspeichern**.

1. Wählen Sie **Alle Symbole laden** aus, um Symbole sofort herunterzuladen. Diese Schaltfläche ist nur während des Debuggens verfügbar.

   Wenn Sie jetzt keine Symbole herunterladen, werden die Symbole beim nächsten Starten des Debuggens heruntergeladen.

1. Wählen Sie **OK** aus, um das Dialogfeld **Optionen** zu schließen.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>So laden Sie Symbole aus dem Fenster „Module“ oder „Aufrufliste“

1. Öffnen Sie während des Debuggens das Fenster, indem Sie **Debuggen** > **Fenster** > **Module** auswählen (oder drücken Sie **STRG+ALT+U**). Oder wählen Sie **Debuggen** > **Fenster** > **Aufrufliste** aus (**STRG+ALT+C**).

1. Klicken Sie mit der rechten Maustaste auf ein Modul, für das keine Symbole geladen wurden. Im Fenster **Module** wird der Symbolladestatus in der Spalte **Symbolstatus** angezeigt. Im Fenster **Aufrufliste** wird der Status in der Spalte **Framestatus** angezeigt, und der Frame ist abgeblendet.

   - Wählen Sie im Menü die Option **Symbole laden** aus, um Symboldateien in einem Ordner auf Ihrem Computer zu suchen und zu laden.

   - Wählen Sie **Symbolladeinformationen** aus, um die Speicherorte anzuzeigen, in denen der Debugger nach Symbolen gesucht hat.

   - Wählen Sie **Symboleinstellungen** aus, um die Seite **Symbole** zu öffnen. Wählen Sie auf der Seite **Symbole** unter **Speicherorte für Symboldateien (.pdb)** die Option **Microsoft-Symbolserver** aus, um auf Symbole von öffentlichen Microsoft-Symbolservern zuzugreifen. Wählen Sie die Symbolleistenschaltflächen aus, um weitere Symbolspeicherorte hinzuzufügen und die Ladereihenfolge zu ändern. Wählen Sie **OK** aus, um das Dialogfeld zu schließen.

### <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)