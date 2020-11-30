---
title: Erstellen von übergeordneten Container Ordnern für Projektmappen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die API-Version 1,2 der Quellcodeverwaltungs-Plug-in verwenden, um ein einzelnes Quell Code Verwaltungs Ziel für alle Webprojekte in einer Projekt Mappe anzugeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e65da2b50984b0259079a1693dd31d400e1e12e3
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329938"
---
# <a name="create-parent-container-folders-for-solutions"></a>Erstellen von übergeordneten Container Ordnern für Projektmappen
In der Quellcodeverwaltungs-Plug-in-API-Version 1,2 kann ein Benutzer ein einzelnes Quell Code Verwaltungs Ziel für alle Webprojekte in der Projekt Mappe angeben. Dieser einzelne Stamm wird als Super Unified root (sur) bezeichnet.

 Wenn der Benutzer in der Quellcodeverwaltungs-Plug-in-API Version 1,1 eine Projekt Mappe mit mehreren Projekten zur Quell Code Verwaltung hinzugefügt hat, wurde der Benutzer aufgefordert, ein Quell Code Verwaltungs Ziel für jedes Webprojekt anzugeben.

## <a name="new-capability-flags"></a>Neue funktionsflags
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Neue Funktionen
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE erstellt beim Hinzufügen einer Projekt Mappe zur Quell Code Verwaltung fast immer einen sur-Ordner. Dies geschieht insbesondere in den folgenden Fällen:

- Das Projekt ist ein Dateifreigabe-Webprojekt.

- Es gibt verschiedene Laufwerke für das Projekt und die Projektmappendatei.

- Es gibt verschiedene Freigaben für das Projekt und die Projektmappendatei.

- Projekte wurden separat hinzugefügt (in einer Lösung für die Quell Code Verwaltung).

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird empfohlen, dass der Name des Ordners "sur" mit dem Projektmappennamen ohne Erweiterung identisch ist. In der folgenden Tabelle wird das Verhalten in den beiden Versionen zusammengefasst.

|Funktion|Quellcodeverwaltungs-Plug-in-API, Version 1,1|Quellcodeverwaltungs-Plug-in-API, Version 1,2|
|-------------| - | - |
|Lösung zu SCC hinzufügen|Sccinitialize ()<br /><br /> Sccgetprojpath ()<br /><br /> Sccgetprojpath ()<br /><br /> Sccopumproject ()|Sccinitialize ()<br /><br /> Sccgetprojpath ()<br /><br /> Scckreatesubproject ()<br /><br /> Scckreatesubproject ()<br /><br /> Sccopumproject ()|
|Projekt der Projekt Mappe zur Quell Code Verwaltung hinzufügen|Sccgetprojpath ()<br /><br /> OpenProject ()|Sccgetparametprojectpath ()<br /><br /> Sccopumproject ()<br /><br />  **Hinweis:**  Visual Studio geht davon aus, dass eine Projekt Mappe ein direktes untergeordnetes Element der sur ist.|

## <a name="examples"></a>Beispiele
 In der folgenden Tabelle sind zwei Beispiele aufgeführt. In beiden Fällen wird der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzer zur Eingabe eines Zielspeicher Orts für die Lösung unter Quell Code Verwaltung aufgefordert, bis die  *user_choice* als Ziel angegeben wird. Wenn die user_choice angegeben wird, werden die Projekt Mappe und zwei Projekte hinzugefügt, ohne dass der Benutzer zur Eingabe von Quell Code Verwaltungs Zielen aufgefordert wird.

|Projekt Mappe enthält|Auf Speicherorten|Daten Bank Standardstruktur|
|-----------------------|-----------------------|--------------------------------|
|*sln1. sln*<br /><br /> Web1<br /><br /> Web2|*C:\solutions\sln1*<br /><br /> *C:\inetpub\wwwroot\web1*<br /><br /> \\\server\wwwroot $ \web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/web1<br /><br /> $/<user_choice>/web2|
|*sln1. sln*<br /><br /> Web1<br /><br /> Win1|*C:\solutions\sln1*<br /><br /> *D:\inetpub\wwwroot\web1*<br /><br /> *C:\solutions\sln1\win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 Der Ordner "sur" und die Unterordner werden unabhängig davon erstellt, ob der Vorgang aufgrund eines Fehlers abgebrochen wurde oder fehlschlägt. Sie werden nicht automatisch in Abbruch-oder Fehlerzuständen entfernt.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hat standardmäßig das Verhalten von Version 1,1, wenn das Quellcodeverwaltungs-Plug-in keine `SCC_CAP_CREATESUBPROJECT` -und-funktionsflags zurückgibt `SCC_CAP_GETPARENTPROJECT` Außerdem können Benutzer von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auswählen, das Verhalten von Version 1,1 wiederherzustellen, indem Sie den Wert des folgenden Schlüssels auf *DWORD festlegen: 00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] donotkreatesolutionrootfolderinsourcecontrol**  =  *DWORD: 00000001*

## <a name="see-also"></a>Siehe auch
- [Neuerungen in der Quellcodeverwaltungs-Plug-in-API, Version 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
