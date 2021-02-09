---
title: Aktualisieren von Projekten | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Schnittstellen, die das Visual Studio SDK zum Implementieren der upgradeunterstützung in Ihren Projekten bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b399feb80da56ef70b18a1b11b05c7f6cc3795f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883154"
---
# <a name="upgrading-projects"></a>Aktualisieren von Projekten

Änderungen am Projekt Modell von einer Version von Visual Studio zur nächsten erfordern möglicherweise, dass Projekte und Projektmappen aktualisiert werden, damit Sie auf der neueren Version ausgeführt werden können. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Stellt Schnittstellen bereit, die zum Implementieren von upgradeunterstützung in ihren eigenen Projekten verwendet werden können.

## <a name="upgrade-strategies"></a>Upgradestrategien

Um ein Upgrade zu unterstützen, muss die Implementierung des Projekt Systems eine Upgradestrategie definieren und implementieren. Zum Ermitteln ihrer Strategie können Sie eine parallele (SxS) Sicherung, Kopiesicherung oder beides unterstützen.

- SxS Backup bedeutet, dass in einem Projekt nur die Dateien kopiert werden, für die ein Upgrade durchgeführt werden muss. dabei wird ein geeigneter Dateinamen Suffix hinzugefügt, z. b. ". old".

- Kopiesicherung bedeutet, dass ein Projekt alle Projekt Elemente an einen vom Benutzer bereitgestellten Sicherungs Speicherort kopiert. Die relevanten Dateien am ursprünglichen Projekt Speicherort werden dann aktualisiert.

## <a name="how-upgrade-works"></a>Funktionsweise des Upgrades

Wenn eine Projekt Mappe, die in einer früheren Version von Visual Studio erstellt wurde, in einer neueren Version geöffnet wird, überprüft die IDE die Projektmappendatei, um zu ermitteln, ob Sie aktualisiert werden muss. Wenn ein Upgrade erforderlich ist, wird der **Upgrade-Assistent** automatisch gestartet, um den Benutzer durch den Upgradeprozess zu durchlaufen.

Wenn eine Projekt Mappe aktualisiert werden muss, fragt Sie jede projektfactory nach ihrer Upgradestrategie ab. Die Strategie bestimmt, ob die projektfactory Kopiesicherung oder SxS-Sicherung unterstützt. Die Informationen werden an den **Upgrade-Assistenten** gesendet, der die für die Sicherung erforderlichen Informationen sammelt und dem Benutzer die entsprechenden Optionen präsentiert.

### <a name="multi-project-solutions"></a>Projektmappen mit mehreren Projekten

Wenn eine Projekt Mappe mehrere Projekte enthält und die Upgradestrategien unterschiedlich sind, z. b. Wenn ein C++-Projekt, das nur die SxS-Sicherung unterstützt, und ein Webprojekt, das nur die Kopiesicherung unterstützt, die Projekt-Factorys

Die Projekt Mappe fragt jede projektfactory nach ab <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Anschließend wird aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> , um zu prüfen, ob globale Projektdateien aktualisiert werden müssen, und um die unterstützten Upgradestrategien zu ermitteln. Anschließend wird der **Upgrade-Assistent** aufgerufen.

Nachdem der Benutzer den Assistenten abgeschlossen hat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> wird für jede projektfactory aufgerufen, um das tatsächliche Upgrade auszuführen. Um die Sicherung zu vereinfachen, stellen ivsprojectupgradeviafactory-Methoden den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Dienst bereit, um die Details des Upgradevorgangs zu protokollieren. Dieser Dienst kann nicht zwischengespeichert werden.

Nachdem alle relevanten globalen Dateien aktualisiert wurden, kann jede projektfactory auswählen, ein Projekt zu instanziieren. Die Projekt Implementierung muss unterstützen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird dann aufgerufen, um alle relevanten Projekt Elemente zu aktualisieren.

> [!NOTE]
> Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode stellt keinen SVsUpgradeLogger-Dienst bereit. Dieser Dienst kann durch Aufrufen von abgerufen werden <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

## <a name="best-practices"></a>Empfehlungen

Verwenden <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Sie den Dienst, um zu prüfen, ob Sie eine Datei bearbeiten können, bevor Sie Sie bearbeiten, und Sie können Sie speichern, bevor Sie gespeichert wird. Dies hilft Ihren Sicherungs-und upgradeimplementierungen bei der Behandlung von Projektdateien in der Quell Code Verwaltung, Dateien mit unzureichenden Berechtigungen usw.

Verwenden <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Sie den Dienst in allen Phasen der Sicherung und des Upgrades, um Informationen über den Erfolg oder Misserfolg des Upgradevorgangs bereitzustellen.

Weitere Informationen zum Sichern und Upgraden von Projekten finden Sie in den Kommentaren für ivsprojectupgrade in vsshell2. idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> Aktualisieren von benutzerdefinierten Projekten

Wenn Sie die in der Projektdatei dauerhaft gespeicherten Informationen zwischen verschiedenen Visual Studio-Versionen Ihres Produkts ändern, müssen Sie das Durchführen eines Upgrades der Projektdatei von der alten auf die neue Version unterstützen. Implementieren Sie die-Schnittstelle, um ein Upgrade zu unterstützen, das die Teilnahme am **Visual Studio-Konvertierungs-Assistenten** ermöglicht <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Diese Schnittstelle stellt das einzige verfügbare Verfahren zum Durchführen von Kopierupgrades dar. Das Upgrade des Projekts erfolgt im Rahmen des Öffnens der Projektmappe. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>-Schnittstelle wird von der Projektfactory implementiert oder sollte zumindest über diese verfügbar sein.

Der alte Mechanismus, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Schnittstelle verwendet, wird noch unterstützt, doch wird dabei das abweichende Konzept verfolgt, das Upgrade des Projektsystems beim Öffnen des Projekts vorzunehmen. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle wird daher von der Visual Studio-Umgebung aufgerufen, auch wenn die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle aufgerufen oder implementiert wird. Aufgrund dieses Ansatzes können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> verwenden, um die Kopie zu implementieren und nur Teile des Upgrades zu projizieren, wobei der Rest der Arbeit für die Ausführung an Ort und Stelle (also möglichst dem neuen Speicherort) durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Schnittstelle delegiert wird.

Eine Beispiel Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> finden Sie unter [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Im Rahmen von Projektupgrades stellen sich die folgenden Szenarien dar:

- Wenn die Datei ein neueres Format aufweist, als es vom Projekt unterstützt werden kann, muss eine Fehlermeldung zurückgegeben werden, aus der dieser Umstand hervorgeht. Dabei wird davon ausgegangen, dass die ältere Version Ihres Produkts Code zum Überprüfen der Version enthält.

- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>-Flag in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Methode angegeben ist, wird das Upgrade vor dem Öffnen des Projekts als Upgrade an Ort und Stelle ausgeführt.

- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP>-Flag in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Methode angegeben ist, wird das Upgrade als Kopierupgrade implementiert.

- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>-Flag im <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Aufruf angegeben ist, wurde der Benutzer von der Umgebung aufgefordert, nach dem Öffnen des Projekts ein Upgrade der Projektdatei an Ort und Stelle auszuführen. Beispielsweise fordert die Umgebung den Benutzer zum Upgrade auf, wenn der Benutzer eine ältere Version der Lösung öffnet.

- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>-Flag nicht im <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Aufruf angegeben ist, müssen Sie den Benutzer auffordern, ein Upgrade der Projektdatei auszuführen.

     Die folgende Aufforderungsnachricht stellt ein Beispiel dar:

     "Das Projekt '%1' wurde in einer älteren Version von Visual Studio erstellt. Wenn Sie es mit dieser Version von Visual Studio öffnen, können Sie es möglicherweise nicht mehr mit älteren Versionen von Visual Studio öffnen. Möchten Sie fortfahren und dieses Projekt öffnen?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>So implementieren Sie IVsProjectUpgradeViaFactory

1. Implementieren Sie die Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>-Schnittstelle, insbesondere die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Methode in Ihrer Projektfactoryimplementierung, oder machen Sie die Implementierungen von Ihrer Projektfactoryimplementierung aus aufrufbar.

2. Wenn Sie ein Upgrade an Ort und Stelle als Teil des Öffnens der Projektmappe ausführen möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> als Parameter von `VSPUVF_FLAGS` in Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Implementierung an.

3. Wenn Sie ein Upgrade an Ort und Stelle als Teil des Öffnens der Projektmappe ausführen möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> als Parameter von `VSPUVF_FLAGS` in Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Implementierung an.

4. Für die Schritte 2 und 3, die eigentlichen Dateiupgradeschritte, kann die Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> wie im Abschnitt "Implementierung von `IVsProjectUpgade`" im Abschnitt unten beschrieben implementiert werden; alternativ können Sie das eigentliche Dateiupgrade an <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> delegieren.

5. Verwenden Sie die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>, um mit Upgrades zusammenhängende Nachrichten für Benutzer mithilfe des Visual Studio-Migrations-Assistenten zu veröffentlichen.

6. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>-Schnittstelle wird verwendet, um jede Art von Dateiupgrade zu implementieren, die im Rahmen eines Projektupgrades erfolgen muss. Diese Schnittstelle wird nicht von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> aufgerufen, sondern als Mechanismus für das Upgrade von Dateien bereitgestellt, die zum Projektsystem gehören, von denen das Projekthauptsystem jedoch möglicherweise keine unmittelbare Kenntnis hat. Diese Situation kann beispielsweise eintreten, wenn die compilerbezogenen Dateien und Eigenschaften nicht vom gleichen Entwicklungsteam wie der Rest des Projektsystems betreut werden.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade-Implementierung

Wenn das Projekt System <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> nur implementiert, kann es nicht an dem **Visual Studio-Konvertierungs-Assistenten** teilnehmen. Aber selbst wenn Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>-Schnittstelle implementieren, können Sie das Dateiupgrade trotzdem an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Implementierung delegieren.

#### <a name="to-implement-ivsprojectupgrade"></a>So implementieren Sie IVsProjectUpgrade

1. Wenn ein Benutzer versucht, ein Projekt zu öffnen, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Methode von der Umgebung aufgerufen, nachdem das Projekt geöffnet wurde und bevor andere Benutzeraktionen für das Projekt ausgeführt werden können. Wenn der Benutzer bereits aufgefordert wurde, ein Upgrade der Projektmappe auszuführen, wird im `grfUpgradeFlags`-Parameter das <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>-Flag übergeben. Wenn der Benutzer ein Projekt direkt öffnet, z. b. mit dem Befehl **vorhandenes Projekt hinzufügen** , <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> wird das Flag nicht weitergegeben, und das Projekt muss den Benutzer auffordern, das Upgrade durchzuführen.

2. In Reaktion auf den <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Aufruf muss das Projekt bewerten, ob für die Projektdatei ein Upgrade ausgeführt werden muss. Wenn das Projekt für den Projekttyp kein Upgrade auf eine neue Version ausführen muss, kann es einfach das <xref:Microsoft.VisualStudio.VSConstants.S_OK>-Flag zurückgeben.

3. Wenn das Projekt ein Upgrade des Projekttyps auf eine neue Version vornehmen muss, muss es bestimmen, ob die Projektdatei durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>-Methode und Übergeben des Werts <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für den `rgfQueryEdit`-Parameter geändert werden kann. In diesem Fall muss das Projekt folgendes ausführen:

    - Wenn der im `pfEditCanceled`-Parameter zurückgegebene `VSQueryEditResult`-Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> ist, kann das Upgrade fortgesetzt werden, weil die Projektdatei geschrieben werden kann.

    - Wenn der im `pfEditCanceled`-Parameter zurückgegebene `VSQueryEditResult`-Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ist und für den `VSQueryEditResult`-Wert das <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc>-Bit festgelegt ist, muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> einen Fehler zurückgeben, da der Benutzer das Berechtigungsproblem selbst lösen muss. Das Projekt sollte dann Folgendes ausführen:

         Melden Sie den Fehler an den Benutzer, indem Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> und den <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> Fehlercode an zurückgeben <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

    - Wenn der `VSQueryEditResult`-Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ist und für den `VSQueryEditResultFlags`-Wert das <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>-Bit festgelegt ist, sollte die Projektdatei durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...) ausgecheckt werden.

4. Wenn der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>-Aufruf der Projektdateien zum Auschecken der Datei und zum Abrufen der letzten Version führt, wird das Projekt entladen und erneut geladen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Methode wird erneut aufgerufen, sobald eine weitere Instanz des Projekts erstellt wird. Bei diesem zweiten Aufruf kann die Projektdatei auf den Datenträger geschrieben werden; es wird empfohlen, dass das Projekt eine Kopie der Projektdatei im vorherigen Format mit einer OLD-Erweiterung speichert, die für das Upgrade erforderlichen Änderungen vornimmt und die Projektdatei anschließend im neuen Format speichert. Wenn bei irgendeinem Teil des Upgradevorgangs ein Fehler auftritt muss auch hier die Methode den Fehler durch Zurückgeben von <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> anzeigen. Dadurch wird das Projekt aus dem Projektmappen-Explorer entladen.

     Für den Fall, dass der Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>-Methode (mit dem Wert „ReportOnly“) die Flags <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> und <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> zurückgibt, ist es wichtig, den gesamten Prozess zu verstehen, der in der Umgebung geschieht.

5. Der Benutzer versucht, die Projektdatei zu öffnen.

6. Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>-Implementierung auf.

7. Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>`true` zurückgibt, ruft die Umgebung Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>-Implementierung auf.

8. Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>-Implementierung auf, um die Datei zu öffnen und das Projektobjekt zu initialisieren z. B. „Projekt1“.

9. Die Umgebung ruft Ihre `IVsProjectUpgrade::UpgradeProject` -Implementierung auf, um zu bestimmen, ob ein Upgrade der Projektdatei erforderlich ist.

10. Sie rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> auf und übergeben den Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> für den `rgfQueryEdit`-Parameter.

11. Die Umgebung gibt für `VSQueryEditResult` den Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> zurück, und in `VSQueryEditResultFlags` wird das <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>-Bit festgelegt.

12. Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Implementierung ruft `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>) auf.

Dieser Aufruf kann dazu führen, dass eine neue Kopie Ihrer Projektdatei ausgecheckt und die neueste Version abgerufen wird, wodurch es erforderlich wird, die Projektdatei neu zu laden. An diesem Punkt geschieht eins von zwei Dingen:

- Wenn Sie das erneute Laden des Projekts selbst vornehmen, ruft die Umgebung Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>-Implementierung (VSITEMID_ROOT) auf. Wenn Sie diesen Aufruf empfangen, laden Sie die erste Instanz des Projekts (Projekt1) erneut, und fahren Sie mit dem Upgrade Ihrer Projektdatei fort. Die Umgebung weiß, dass Sie das erneute Laden des Projekts selbst übernehmen, wenn Sie für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) `true` zurückgeben.

- Wenn Sie das erneute Laden des Projekts nicht selbst ausführen, geben Sie für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) `false` zurück. In diesem Fall <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> erstellt die Umgebung vor der Rückgabe von (QEF_ForceEdit_NoPrompting QEF_DisallowInMemoryEdits) eine neue Instanz des Projekts, z. b. "Projekt2", wie folgt:

    1. Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> für Ihr erstes Projektobjekt „Project1“ auf und versetzt dieses Objekt dadurch in den inaktiven Zustand.

    2. Die Umgebung ruft Ihre `IVsProjectFactory::CreateProject` -Implementierung auf, um eine zweite Instanz Ihres Projekts zu erstellen, „Project2“.

    3. Die Umgebung ruft Ihre `IPersistFileFormat::Load` -Implementierung auf, um die Datei zu öffnen und das zweite Projektobjekt, „Projekt2“, zu initialisieren.

    4. Die Umgebung ruft `IVsProjectUpgrade::UpgradeProject` ein zweites Mal auf, um zu bestimmen, ob für das Projektobjekt ein Upgrade ausgeführt werden soll. Dieser Aufruf erfolgt jedoch für eine neue, zweite Instanz des Projekts, „Projekt2“. Dies ist das Projekt, das in der Projektmappe geöffnet ist.

        > [!NOTE]
        > Wenn die Instanz Ihres ersten Projekts, „Projekt1“, in den inaktiven Status versetzt wurde, müssen Sie vom ersten Aufruf <xref:Microsoft.VisualStudio.VSConstants.S_OK> an Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Implementierung zurückgeben.

    5. Sie rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> auf und übergeben den Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> für den `rgfQueryEdit`-Parameter.

    6. Die Umgebung gibt <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> zurück, und das Upgrade kann fortgesetzt werden, weil die Projektdatei geschrieben werden kann.

Wenn Sie das Upgrade versäumen, geben Sie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> aus `IVsProjectUpgrade::UpgradeProject` zurück. Wenn für Sie kein Upgrade erforderlich ist oder Sie sich gegen das Upgrade entscheiden, behandeln Sie den `IVsProjectUpgrade::UpgradeProject` -Aufruf als nicht erfolgten Vorgang (No-Op). Wenn Sie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> zurückgeben, wird dem Projektmappe für Ihr Projekt ein Platzhalterknoten hinzugefügt.

## <a name="upgrading-project-items"></a>Aktualisieren von Projektelementen

Wenn Sie Elemente in Projekt Systemen hinzufügen oder verwalten, die Sie nicht implementieren, müssen Sie möglicherweise am Projekt Upgradeprozess teilnehmen. Crystal Reports ist ein Beispiel für ein Element, das dem Projekt System hinzugefügt werden kann.

In der Regel möchten Projekt Element Implementierungen ein bereits vollständig instanzialisiertes und aktualisiertes Projekt nutzen, da Sie wissen müssen, was die Projekt Verweise sind und welche anderen Projekteigenschaften vorhanden sind, um eine Aktualisierungs Entscheidung zu treffen.

### <a name="to-get-the-project-upgrade-notification"></a>So erhalten Sie die Upgradebenachrichtigung für das Projekt

1. Legen Sie das- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> Flag (definiert in vsshell80. idl) in der Projekt Element Implementierung fest. Dies bewirkt, dass das Projekt Element VSPackage automatisch geladen wird, wenn die Visual Studio-Shell bestimmt, dass ein Projekt System gerade aktualisiert wird.

2. Informieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle über die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> Methode.

3. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> -Schnittstelle wird ausgelöst, nachdem die Projekt System Implementierung die Upgradevorgänge abgeschlossen hat und das neue aktualisierte Projekt erstellt wurde. Abhängig vom Szenario wird die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle nach den- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> ,- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> ,-oder- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Methoden ausgelöst.

### <a name="to-upgrade-the-project-item-files"></a>So aktualisieren Sie die Projekt Element Dateien

1. Sie müssen den Datei Sicherungsprozess in der Projekt Element Implementierung sorgfältig verwalten. Dies gilt insbesondere für eine parallele Sicherung, bei der der- `fUpgradeFlag` Parameter der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode auf festgelegt ist <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> , wobei Dateien, die gesichert wurden, neben Dateien platziert werden, die als ". old" bezeichnet werden. Die gesicherten Dateien, die älter als die Systemzeit waren, als das Projekt aktualisiert wurde, können als veraltet eingestuft werden. Außerdem können Sie überschrieben werden, es sei denn, Sie führen bestimmte Schritte aus, um dies zu verhindern.

2. Wenn das Projekt Element eine Benachrichtigung über das Projekt Upgrade erhält, wird der **Visual Studio-Konvertierungs-Assistent** weiterhin angezeigt. Daher sollten Sie die Methoden der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Schnittstelle verwenden, um upgrademeldungen für die Benutzeroberfläche des Assistenten bereitzustellen.

## <a name="see-also"></a>Weitere Informationen

- [Projekte](../../extensibility/internals/projects.md)
