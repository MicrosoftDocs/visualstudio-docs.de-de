---
title: Auswählen des Installationsverzeichnisses für ein VSPackage | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das Installationsverzeichnis für ein VSPackage und seine unterstützenden Dateien mithilfe von Faktoren auswählen, z. b. ob es verwaltet oder nicht verwaltet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfb7f339ca9832db8fdfea47a5bc1aa940534823
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189978"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Auswählen des Installationsverzeichnisses für ein VSPackage
Ein VSPackage und seine unterstützenden Dateien müssen sich im Dateisystem eines Benutzers befinden. Der Speicherort hängt davon ab, ob das VSPackage verwaltet oder nicht verwaltet ist, ob es sich um ein paralleles Versions Schema und eine Benutzer Auswahl handelt.

## <a name="unmanaged-vspackages"></a>Nicht verwaltete VSPackages
 Ein nicht verwaltetes VSPackage ist ein com-Server, der an einem beliebigen Speicherort installiert werden kann. Die Registrierungsinformationen müssen den Speicherort exakt widerspiegeln. Die Benutzeroberfläche des Installers sollte einen Standard Speicherort als Unterverzeichnis des `ProgramFilesFolder` Windows Installer Eigenschafts Werts bereitstellen. Beispiel:

*&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; myvspackageproduct &gt; \v1.0\\*

 Der Benutzer sollte das Standardverzeichnis ändern können, um Benutzer zu unterstützen, die eine kleine Start Partition aufbewahren und die Installation von Anwendungen und Tools auf einem anderen Volume bevorzugen.

 Wenn das parallele Schema ein VSPackage mit Versions Angabe verwendet, können Sie Unterverzeichnisse zum Speichern verschiedener Versionen verwenden. Beispiel:

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; myvspackageproduct &gt; \\ v 1.0 \\ 2002\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; myvspackageproduct &gt; \\ v 1.0 \\ 2003\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; myvspackageproduct &gt; \\ v 1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>Verwaltete VSPackages
 Verwaltete VSPackages können auch an einem beliebigen Speicherort installiert werden. Sie sollten jedoch die Installation im globalen Assemblycache (GAC) immer in Erwägung gezogen, um die Ladezeiten der Assembly zu verringern. Da verwaltete VSPackages immer Assemblys mit starkem Namen sind, bedeutet die Installation im GAC, dass die Signatur Überprüfung mit starkem Namen nur zur Installationszeit erfolgt. Assemblys mit starkem Namen, die an anderer Stelle im Dateisystem installiert sind, müssen bei jedem Laden überprüft werden. Wenn Sie verwaltete VSPackages im GAC installieren, verwenden Sie den **/Assembly** -Schalter des regpkg-Tools, um Registrierungseinträge zu schreiben, die auf den starken Namen der Assembly verweisen.

 Wenn Sie verwaltete VSPackages an einem anderen Speicherort als dem globalen Assemblycache installieren, befolgen Sie die vorherigen Ratschläge für nicht verwaltete VSPackages zum Auswählen von Verzeichnishierarchien. Verwenden Sie den **/CodeBase** -Schalter des regpkg-Tools, um Registrierungseinträge zu schreiben, die auf den Pfad der VSPackage-Assembly verweisen.

 Weitere Informationen finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Satelliten-DLLs
 Gemäß der Konvention befinden sich VSPackage-Satelliten-DLLs, die Ressourcen für ein bestimmtes Gebiets Schema enthalten, in Unterverzeichnissen des *VSPackage* -Verzeichnisses. Die Unterverzeichnisse entsprechen den LCID-Werten (Locale ID).

 Der Artikel [Verwalten von VSPackages](../../extensibility/managing-vspackages.md) gibt an, dass Registrierungseinträge steuern, wo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tatsächlich nach der Satelliten-DLL eines VSPackages sucht. Allerdings [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht, eine Satelliten-DLL in einem Unterverzeichnis mit dem Namen für einen LCID-Wert in der folgenden Reihenfolge zu laden:

1. Standard-LCID (Visual Studio LCID, z. b. *\ 1033* für Englisch)

2. Standard-LCID mit der Standard unter Sprache.

3. System Standard-LCID.

4. System Standard-LCID mit der Standard unter Sprache.

5. US-Englisch (*. \ 1033* oder *.\0x409*).

Wenn die VSPackage-dll Ressourcen enthält und der Registrierungs Eintrag **satellitedll\dllname** darauf verweist, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht, Sie in der obigen Reihenfolge zu laden.

## <a name="see-also"></a>Weitere Informationen
- [Auswählen zwischen freigegebenen und versionierten VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
- [Verwalten der Paket Registrierung](/previous-versions/bb166783(v=vs.100))