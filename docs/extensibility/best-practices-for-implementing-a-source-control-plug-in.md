---
title: 'Implementieren eines Quellcodeverwaltungs-Plug-ins: bewährte Methoden'
description: Überprüfen Sie diese technischen Details, damit Sie ein Quellcodeverwaltungs-Plug-in in Visual Studio zuverlässig implementieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80a944c077d520d6d9ecac9557179311ecf20281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893073"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Bewährte Methoden für die Implementierung eines Quellcodeverwaltungs-Plug-ins
Die folgenden technischen Details helfen Ihnen bei der zuverlässigen Implementierung eines Quellcodeverwaltungs-Plug-ins in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Probleme mit der Speicherverwaltung
 In den meisten Fällen gibt die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE), bei der es sich um den Aufrufer handelt, den Arbeitsspeicher frei Das Quellcodeverwaltungs-Plug-in gibt Zeichen folgen und andere Elemente in der vom Aufrufer zugewiesenen Puffer zurück. Ausnahmen werden in Beschreibungen spezifischer Funktionen aufgeführt, in denen Sie auftreten.

## <a name="arrays-of-file-names"></a>Arrays von Dateinamen
 Wenn ein Array von Dateien übermittelt wird, wird es nicht als zusammenhängendes Array von Dateinamen übermittelt. Sie wird als Array von Zeigern auf Dateinamen übermittelt. Beispielsweise werden in [sccget](../extensibility/sccget-function.md)die Dateinamen durch den- `lpFileNames` Parameter übergeben, wobei `lpFileNames` tatsächlich ein Zeiger auf eine ist `char **` . `lpFileNames`[0] ist ein Zeiger auf den Vornamen, `lpFileNames` [1] ist ein Zeiger auf den zweiten Namen usw.

## <a name="large-model"></a>Großes Modell
 Alle Zeiger sind auch bei 16-Bit-Betriebssystemen 32 Bits.

## <a name="fully-qualified-paths"></a>Voll qualifizierte Pfade
 Wenn Dateinamen oder Verzeichnisse als Argumente angegeben werden, müssen Sie voll qualifizierte Pfade oder UNC-Pfade ohne die abschließenden umgekehrten Schrägstriche sein. Das Quellcodeverwaltungs-Plug-in ist dafür verantwortlich, diese in relative Pfade zu übersetzen, wenn dies eine Anforderung des zugrunde liegenden Quell Code Verwaltungssystems ist.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Geben Sie einen voll qualifizierten Pfad für die registrierte DLL an.
 Die IDE lädt keine DLLs mehr aus relativen Pfaden (z. b. *.\NewProvider.dll*). Es muss ein vollständiger Pfad der DLL angegeben werden (z. b. *C:\Providers\NewProvider.dll*). Diese Anforderung erhöht die Sicherheit der IDE, indem verhindert wird, dass nicht autorisierte oder nicht autorisierte Quell Code Verwaltungs-DLLs geladen werden.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Bei der Installation des Quellcodeverwaltungs-Plug-Ins auf ein vorhandenes vssci-Plug-in überprüfen
 Für einen Benutzer, der das Quellcodeverwaltungs-Plug-in installieren möchte, ist möglicherweise bereits ein Quellcodeverwaltungs-Plug-in auf dem Computer installiert. Das Installationsprogramm (Setup) für das Plug-in, das Sie erstellen, sollte ermitteln, ob vorhandene Werte für die relevanten Registrierungsschlüssel vorhanden sind. Wenn diese Schlüssel bereits festgelegt sind, sollte das Installationsprogramm den Benutzer bitten, das Plug-in als Standard-Quellcodeverwaltungs-Plug-in zu registrieren und das bereits installierte zu ersetzen.

## <a name="error-result-codes-and-reporting"></a>Fehler Ergebnis Codes und Berichterstellung
 Der `SCC_OK` Rückgabecode für eine Quell Code Verwaltungsfunktion gibt an, dass der Vorgang für alle Dateien erfolgreich war. Wenn der Vorgang fehlschlägt, wird erwartet, dass der zuletzt aufgetretene Fehlercode zurückgegeben wird.

 Die Regel für die Berichterstellung besteht darin, dass die IDE bei Auftreten eines Fehlers in der IDE für die Berichterstellung zuständig ist. Wenn im Quell Code Verwaltungssystem ein Fehler auftritt, ist das Quellcodeverwaltungs-Plug-in für die Berichterstellung verantwortlich. Beispielsweise werden **derzeit keine Dateien ausgewählt** , die von der IDE gemeldet werden, während **Diese Datei bereits ausgecheckt ist** .

## <a name="the-context-structure"></a>Die Kontext Struktur
 Während des Aufrufers [sccinitialize](../extensibility/sccinitialize-function.md)übergibt der Aufrufer den- `ppvContext` Parameter, bei dem es sich um ein nicht initialisiertes Handle für einen void handelt. Das Quellcodeverwaltungs-Plug-in kann diesen Parameter ignorieren, oder er kann eine Struktur beliebiger Art zuordnen und einen Zeiger auf diese Struktur in den übergebenen Zeiger einfügen. Die IDE versteht diese Struktur nicht, sondern übergibt einen Zeiger auf diese Struktur an jeden anderen-Befehl im Plug-in. Dadurch erhalten Sie wertvolle Kontext Cache Informationen für das Plug-in, mit denen Sie globale Zustandsinformationen verwalten können, die über Funktionsaufrufe hinweg beibehalten werden, ohne dass globale Variablen verwendet werden. Das Plug-in ist dafür verantwortlich, die Struktur für einen aufzurufenden [sccuninitialize](../extensibility/sccuninitialize-function.md)-Befehl freizugeben.

 Wenn das Plug-in das `SCC_CAP_REENTRANT` Bit in [sccinitialize](../extensibility/sccinitialize-function.md) festlegt (insbesondere im- `lpSccCaps` Parameter), werden mehrere Kontext Strukturen verwendet, um alle geöffneten Projekte zu verfolgen.

## <a name="bitflags-and-other-command-options"></a>Bitflags und andere Befehlsoptionen
 Für jeden Befehl, wie z. b. [sccget](../extensibility/sccget-function.md), kann die IDE viele Optionen angeben, die das Verhalten des Befehls ändern.

 Die API unterstützt die Einstellung bestimmter Optionen durch die IDE mithilfe des- `fOptions` Parameters. Diese Optionen werden in Bitflags beschrieben, die [von bestimmten Befehlen](../extensibility/bitflags-used-by-specific-commands.md) in Verbindung mit den Befehlen verwendet werden, die Sie betreffen. Im Allgemeinen handelt es sich hierbei um Optionen, für die der Benutzer nicht aufgefordert wird.

 Die meisten vom benutzerkonfigurierbaren Einstellungsoptionen werden nicht auf diese Weise definiert, da Sie sich in den Quellcodeverwaltungs-Plug-ins stark unterscheiden. Daher ist der empfohlene Mechanismus eine Schaltfläche **erweitert** . Beispielsweise zeigt die IDE im Dialogfeld **Get** nur Informationen an, die Sie versteht. Sie zeigt jedoch auch eine Schaltfläche **erweitert** an, wenn das Plug-in über Optionen für diesen Befehl verfügt. Wenn der Benutzer auf die Schaltfläche **erweitert** klickt, ruft die IDE [sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md) auf, damit das Quellcodeverwaltungs-Plug-in den Benutzer zur Eingabe von Informationen auffordern kann, z. b. Bitflags oder Datum/Uhrzeit. Das Plug-in gibt diese Informationen in einer-Struktur zurück, die während des-Befehls zurückgegeben wird `SccGet` .

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-ins](../extensibility/internals/creating-a-source-control-plug-in.md)
