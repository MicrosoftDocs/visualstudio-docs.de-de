---
title: 'Vorgehensweise: Verwenden des Aktivitäts Protokolls | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 824feee64f928dc837a379aeb539daaa5ba0d1db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905578"
---
# <a name="how-to-use-the-activity-log"></a>Vorgehensweise: Verwenden des Aktivitäts Protokolls
VSPackages können Nachrichten in das Aktivitätsprotokoll schreiben. Diese Funktion ist besonders nützlich für das Debuggen von VSPackages in Einzelhandelsumgebungen.

> [!TIP]
> Das Aktivitätsprotokoll ist immer aktiviert. Visual Studio speichert einen parallelen Puffer der letzten 100 Einträge sowie die ersten 10 Einträge, die allgemeine Konfigurationsinformationen aufweisen.

## <a name="to-write-an-entry-to-the-activity-log"></a>So schreiben Sie einen Eintrag in das Aktivitätsprotokoll

1. Fügen Sie diesen Code in die- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode oder in eine beliebige andere Methode ein, mit Ausnahme des VSPackage-Konstruktors:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Mit diesem Code wird der <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Dienst abgerufen und in eine- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle umgewandelt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> schreibt einen Informations Eintrag mit dem aktuellen Kultur Kontext in das Aktivitätsprotokoll.

2. Wenn das VSPackage geladen wird (in der Regel, wenn ein Befehl aufgerufen oder ein Fenster geöffnet wird), wird der Text in das Aktivitätsprotokoll geschrieben.

## <a name="to-examine-the-activity-log"></a>So überprüfen Sie das Aktivitätsprotokoll

1. Führen Sie Visual Studio mit der Befehlszeilenoption [/Log](../ide/reference/log-devenv-exe.md) aus, um während der Sitzung ActivityLog.xml auf den Datenträger zu schreiben.

2. Suchen Sie nach dem Schließen von Visual Studio das Aktivitätsprotokoll im Unterordner für Visual Studio-Daten:

   <em> *% AppData%</em>\microsoft\visualstudio \\ \<version>\ActivityLog.xml*.

3. Öffnen Sie das Aktivitätsprotokoll mit einem beliebigen Text-Editor. Dies ist ein typischer Eintrag:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Stabile Programmierung

Da es sich bei dem Aktivitätsprotokoll um einen Dienst handelt, ist das Aktivitätsprotokoll im VSPackage-Konstruktor nicht verfügbar.

Sie sollten das Aktivitätsprotokoll direkt vor dem Schreiben in das Aktivitätsprotokoll abrufen. Speichern oder speichern Sie das Aktivitätsprotokoll nicht für die zukünftige Verwendung.

## <a name="see-also"></a>Weitere Informationen

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
