---
title: 'Bewährte Methoden für die Entwicklung: com, VSTO, & VBA-Add-Ins in Office'
description: Informieren Sie sich über die empfohlenen bewährten Methoden bei der Entwicklung von com-, VSTO-und VBA-Add-Ins für Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d5470c138d4339356ca9f8c79cb5ab274dd99019
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897559"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Bewährte Methoden für die Entwicklung von com-, VSTO-und VBA-Add-Ins in Office
  Wenn Sie com-, VSTO-oder VBA-Add-Ins für Office entwickeln, befolgen Sie die in diesem Artikel beschriebenen bewährten Methoden für die Entwicklung.   Vorteile:

- Kompatibilität von Add-Ins über verschiedene Versionen und bereit Stellungen von Office hinweg.
- Geringere Komplexität der Add-in-Bereitstellung für Ihre Benutzer und IT-Administratoren.
- Unbeabsichtigte Installation oder Laufzeitfehler des Add-ins treten nicht auf.

>Hinweis: das Verwenden der [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) zum Vorbereiten des com-, VSTO-oder VBA-Add-Ins für den Windows Store wird nicht unterstützt. COM-, VSTO-und VBA-Add-Ins können nicht im Windows Store oder im Office Store verteilt werden.

## <a name="do-not-check-for-office-during-installation"></a>Nicht während der Installation für Office prüfen
 Es wird nicht empfohlen, dass Sie mit dem Add-in erkennen, ob Office während des Add-in-Installationsvorgangs installiert wird. Wenn Office nicht installiert ist, können Sie das Add-in installieren, und der Benutzer kann nach der Installation von Office darauf zugreifen.

## <a name="use-embedded-interop-types-nopia"></a>Eingebettete Interop-Typen (nopia) verwenden
Wenn Ihre Lösung .NET 4,0 oder höher verwendet, verwenden Sie eingebettete Interop-Typen (nopia) anstelle von der verteilbaren Office Primary Interopassemblys (PIA). Durch die Verwendung von Einbettungs Typen wird die Installations Größe Ihrer Lösung reduziert, und die zukünftige Kompatibilität wird sichergestellt. Office 2010 war die letzte Version von Office, die die PIA Redistributable ausgeliefert hat. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Einbetten von Typinformationen aus Microsoft Office](/previous-versions/ee317478(v=vs.140)) Assemblys und [typäquivalenz und eingebetteten Interop-Typen](/windows/uwp/porting/desktop-to-uwp-root).

Wenn Ihre Lösung eine frühere Version von .NET verwendet, empfiehlt es sich, die Lösung für die Verwendung von .NET 4,0 oder höher zu aktualisieren. Die Verwendung von .NET 4,0 oder höher reduziert die Lauf Zeit Voraussetzungen für neuere Versionen von Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Vermeiden Sie die Abhängigkeit von bestimmten Office-Versionen.
Wenn Ihre Lösung Funktionen verwendet, die nur in neueren Versionen von Office verfügbar sind, überprüfen Sie, ob die Funktion (sofern möglich) zur Laufzeit vorhanden ist (z. b. durch die Verwendung der Ausnahmebehandlung oder durch Überprüfen der Version). Überprüfen Sie die minimalen Versionen und keine bestimmten Versionen, indem Sie unterstützte APIs im Objektmodell verwenden, z. b. die [Application. Version-Eigenschaft](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Es wird nicht empfohlen, dass Sie sich auf binäre Office-Metadaten, Installations Pfade oder Registrierungsschlüssel verlassen, da sich diese zwischen Installationen, Umgebungen und Versionen ändern können.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Aktivieren von 32-Bit-und 64-Bit-Office-Verwendung
Das standardbuildziel sollte sowohl 32-Bit (x86) als auch 64-Bit (x64) unterstützen, es sei denn, die Projekt Mappe ist von Bibliotheken abhängig, die nur für eine bestimmte Bitness verfügbar sind. Die 64-Bit-Version von Office wird bei der Übernahme gesteigert, insbesondere in Big Data Umgebungen. Wenn Sie sowohl 32-Bit als auch 64-Bit unterstützen, ist es für Benutzer einfacher, zwischen 32-Bit-und 64-Bit-Versionen von Office zu wechseln.

Verwenden Sie beim Schreiben von VBA-Code 64-Bit-sichere Declare-Anweisungen, und konvertieren Sie Variablen nach Bedarf. Außerdem sollten Sie sicherstellen, dass Dokumente von Benutzern gemeinsam genutzt werden können, die entweder 32-Bit-oder 64-Bit-Versionen von Office ausführen, indem Sie Code für jede Bitness bereitstellen Weitere Informationen finden Sie unter [Übersicht über 64-Bit-Visual Basic für Anwendungen](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Unterstützen eingeschränkter Umgebungen
Für Ihre Lösung sollten keine Rechte für das Benutzerkonto oder Administrator Rechte erforderlich sein. Außerdem sollte die Lösung nicht von der Einstellung oder Änderung abhängen:

- Das aktuelle Arbeitsverzeichnis
- DLL-Lade Verzeichnisse.
- Die Pfad Variable.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Speicherort für freigegebene Daten und Einstellungen ändern
Wenn die Lösung aus einem Add-in und einem externen Prozess für Office besteht, verwenden Sie nicht den Anwendungsdatenordner des Benutzers oder die Registrierung, um Daten oder Einstellungen zwischen dem Add-in und dem externen Prozess auszutauschen. Verwenden Sie stattdessen den temporären Ordner, den Ordner "Dokumente" oder das Installationsverzeichnis Ihrer Lösung.

## <a name="increment-the-version-number-with-each-update"></a>Erhöhen Sie die Versionsnummer jedes Updates.
Legen Sie die Versionsnummer der Binärdateien in der Projekt Mappe fest, und erhöhen Sie Sie mit jedem Update. Dadurch wird es für Benutzer einfacher, Änderungen Zwischenversionen zu erkennen und die Kompatibilität zu bewerten.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Bereitstellen von Support Anweisungen für die neuesten Versionen von Office
Kunden bitten Sie ISVs, Support Anweisungen für Ihre com-, VSTO-und VBA-Add-Ins bereitzustellen, die in Office ausgeführt werden. Durch das Auflisten ihrer expliziten Support Anweisungen können Kunden, die Microsoft 365-Apps für Unternehmens Bereitschafts Tools verwenden, Ihren Support verstehen.

Zum Bereitstellen von Support Anweisungen für Office-Client Anwendungen (z. b. Word oder Excel) überprüfen Sie zunächst, ob Ihre Add-Ins in der aktuellen Office-Version ausgeführt werden, und führen Sie dann die Bereitstellung von Updates durch, wenn das Add-in in einer zukünftigen Version unterbrochen wird. Sie müssen Ihre Add-Ins nicht testen, wenn Microsoft einen neuen Build oder ein Update für Office freigibt. Microsoft ändert die Erweiterbarkeits Plattform für com, VSTO und VBA in Office selten, und diese Änderungen werden gut dokumentiert.

>Wichtig: Microsoft verwaltet eine Liste der unterstützten Add-Ins für Bereitschafts Berichte und ISV-Kontaktinformationen. Informationen zum Auflisten des Add-Ins finden Sie unter [/ConfigMgr/Desktop-Analytics/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Verwenden des Prozess Monitors zum Debuggen oder Laden von Problemen
Wenn das Add-in während der Installation oder Auslastung Kompatibilitätsprobleme aufweist, sind Sie möglicherweise mit Problemen mit dem Datei-oder Registrierungs Zugriff verknüpft. Verwenden Sie den [Prozess Monitor](/sysinternals/downloads/procmon) oder ein ähnliches Debugtool, um das Verhalten einer funktionierenden Umgebung zu protokollieren und zu vergleichen, um das Problem zu identifizieren.