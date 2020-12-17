---
title: Verwalten paralleler Dateizuordnungen | Microsoft-Dokumentation
description: Wenn das VSPackage Dateizuordnungen bereitstellt, entscheiden Sie, wie parallele Installationen behandelt werden sollen, bei denen eine bestimmte Version von Visual Studio eine Datei öffnet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 477afbd5bc4586d8c46db11b036364f8058133b0
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616343"
---
# <a name="manage-side-by-side-file-associations"></a>Parallele Dateizuordnungen verwalten

Wenn das VSPackage Dateizuordnungen bereitstellt, müssen Sie entscheiden, wie parallele Installationen behandelt werden sollen, bei denen eine bestimmte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufgerufen werden muss, um eine Datei zu öffnen. Das Problem wurde mit inkompatiblen Dateiformaten zusammengesetzt.

Benutzer erwarten, dass eine neue Version eines Produkts mit früheren Versionen kompatibel ist, damit vorhandene Dateien in eine neue Version geladen werden können, ohne dass Daten verloren gehen. Im Idealfall kann das VSPackage die Dateiformate früherer Versionen laden und speichern. Wenn dies nicht zutrifft, sollten Sie ein Upgrade des Datei Formats auf die neue Version des VSPackage anbieten. Der Nachteil dieses Ansatzes besteht darin, dass die aktualisierte Datei in der früheren Version nicht geöffnet werden kann.

Um dieses Problem zu vermeiden, können Sie Erweiterungen ändern, wenn Dateiformate inkompatibel werden. Beispielsweise könnte Version 1 des VSPackage die Erweiterung, *. mypkg10*, verwenden, und Version 2 kann die Erweiterung *. mypkg20* verwenden. Dieser Unterschied identifiziert das VSPackage, das eine bestimmte Datei öffnet. Wenn Sie der Liste der Programme, die einer alten Erweiterung zugeordnet sind, neuere VSPackages hinzufügen, können Benutzer mit der rechten Maustaste auf die Datei klicken und Sie in einem neueren VSPackage öffnen. Zu diesem Zeitpunkt kann das VSPackage anbieten, die Datei auf das neue Format zu aktualisieren oder die Datei zu öffnen und die Kompatibilität mit früheren Versionen des VSPackage aufrechtzuerhalten.

> [!NOTE]
> Sie können diese Ansätze kombinieren. Sie können z. b. eine Abwärtskompatibilität bereitstellen, indem Sie eine ältere Datei laden und das Dateiformat aktualisieren, wenn der Benutzer Sie speichert.

## <a name="face-the-problem"></a>Dem Problem begegnen

Wenn Sie möchten, dass mehrere parallele VSPackages dieselbe Erweiterung verwenden, müssen Sie die Version von auswählen, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] der Erweiterung zugeordnet ist. Hier sind zwei Alternativen:

- Öffnen Sie die Datei in der neuesten Version von, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf dem Computer des Benutzers installiert ist.

   Bei diesem Ansatz ist das Installationsprogramm für die Bestimmung der aktuellen Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und das Einschließen des Registrierungs Eintrags, der für die Datei Zuordnung geschrieben wurde, verantwortlich. In einem Windows Installer-Paket können Sie benutzerdefinierte Aktionen einschließen, um eine Eigenschaft festzulegen, die die neueste Version von angibt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  > [!NOTE]
  > In diesem Kontext bedeutet "Latest" "Latest" (neueste unterstützte Version). Diese Installer-Einträge erkennen nicht automatisch eine nachfolgende Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Einträge zum [Erkennen von System Anforderungen](../extensibility/internals/detecting-system-requirements.md) und in [Befehlen, die nach der Installation ausgeführt werden müssen](../extensibility/internals/commands-that-must-be-run-after-installation.md) , ähneln den hier vorgestellten und sind für die Unterstützung zusätzlicher Versionen von erforderlich [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   In den folgenden Zeilen in der Tabelle "CustomAction" wird die DEVENV_EXE_LATEST-Eigenschaft auf eine Eigenschaft festgelegt, die von den Tabellen "AppSearch" und "reglocator", die in Befehlen erläutert werden [, die nach der Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) Zeilen in der InstallExecuteSequence-Tabelle planen die benutzerdefinierten Aktionen frühzeitig in der Ausführungssequenz. Werte in der Spalte Bedingung machen die Logik funktionsfähig:

  - Visual Studio .NET 2002 ist die neueste Version, wenn dies die einzige aktuelle Version ist.

  - Visual Studio .NET 2003 ist die neueste Version nur, wenn Sie vorhanden und [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht vorhanden ist.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist die neueste Version, wenn Sie die einzige vorhandene Version ist.

    Das Ergebnis ist, dass DEVENV_EXE_LATEST den Pfad der neuesten Version von devenv.exe enthält.

  **CustomAction-Tabellenzeilen, die die neueste Version von Visual Studio bestimmen**

  |Aktion|type|`Source`|Ziel|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence-Tabellenzeilen, die die neueste Version von Visual Studio bestimmen**

  |Aktion|Bedingung|Sequenz|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 und nicht (DEVENV_EXE_2003 oder DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 und nicht DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Mit der DEVENV_EXE_LATEST-Eigenschaft in der Registrierungs Tabelle des Windows Installer Pakets können Sie den Standardwert des **HKEY_CLASSES_ROOT *ProgID* shellopencommand** , [DEVENV_EXE_LATEST] "%1", schreiben.

- Führen Sie ein frei gegebenes Start Programm Programm aus, das von verfügbaren VSPackage-Versionen die beste Wahl treffen kann.

   Die Entwickler von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] haben diese Herangehensweise gewählt, um die komplexen Anforderungen der verschiedenen Formate von Projektmappen und Projekten zu bewältigen, die aus vielen Versionen von resultieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bei dieser Vorgehensweise registrieren Sie ein Start Programm Programm als Erweiterungs Handler. Das Start Programm untersucht die Datei und entscheidet, welche Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und das VSPackage diese bestimmte Datei verarbeiten kann. Wenn ein Benutzer beispielsweise eine Datei öffnet, die zuletzt von einer bestimmten Version des VSPackages gespeichert wurde, kann das Start Programm dieses VSPackage in der entsprechenden Version von Starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Außerdem kann ein Benutzer das Start Programm so konfigurieren, dass immer die neueste Version gestartet wird. Ein Start Programm könnte auch einen Benutzer auffordern, das Format der Datei zu aktualisieren. Wenn das Format der Datei eine Versionsnummer enthält, könnte das Start Programm einen Benutzer darüber informieren, ob das Dateiformat eine Version ist, die höher als mindestens ein installiertes VSPackages ist.

   Das Start Programm sollte sich in einer Windows Installer Komponente befinden, die für alle Versionen des VSPackage freigegeben ist. Dadurch wird sichergestellt, dass die neueste Version immer installiert ist und erst entfernt wird, wenn alle Versionen des VSPackage deinstalliert wurden. Auf diese Weise werden die Dateizuordnungen und andere Registrierungseinträge der Start Programm Komponente auch dann beibehalten, wenn eine Version des VSPackages deinstalliert wird.

## <a name="uninstall-and-file-associations"></a>Deinstallation und Dateizuordnungen

Wenn Sie ein VSPackage deinstallieren, das Registrierungseinträge für Dateizuordnungen schreibt, werden die Dateizuordnungen entfernt. Daher sind der Erweiterung keine Programme zugeordnet. Die Registrierungseinträge, die beim Installieren des VSPackages hinzugefügt wurden, werden von Windows Installer nicht "wieder hergestellt". Es folgen einige Möglichkeiten, die Dateizuordnungen eines Benutzers zu beheben:

- Verwenden Sie wie zuvor beschrieben eine freigegebene Start Programm Komponente.

- Weisen Sie den Benutzer an, eine Reparatur der Version des VSPackage auszuführen, der der Benutzer die Datei Zuordnung zuordnen möchte.

- Stellen Sie ein separates ausführbares Programm bereit, mit dem die entsprechenden Registrierungseinträge neu geschrieben werden.

- Geben Sie eine Konfigurations Optionsseite oder ein Dialogfeld an, mit dem Benutzerdatei Zuordnungen auswählen und verlorene Zuordnungen freigeben können. Weisen Sie die Benutzer an, Sie nach der deinstalstallation auszuführen.

## <a name="see-also"></a>Weitere Informationen

- [Registrieren von Dateinamen Erweiterungen für parallele bereit Stellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registrieren von Verben für Dateinamen Erweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)
