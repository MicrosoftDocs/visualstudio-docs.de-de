---
title: Erstellen von Projekt Instanzen mithilfe von projektfactorys | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Projektklassen Instanzen mithilfe von projektfactorys in der integrierten Entwicklungsumgebung (IDE) von Visual Studio erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ad41bda80337fd0adc65d4792adbbbb1cf38f1
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328599"
---
# <a name="create-project-instances-by-using-project-factories"></a>Erstellen von Projekt Instanzen mithilfe von projektfactorys
Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden eine *projektfactory* , um Instanzen von Project-Objekten zu erstellen. Eine projektfactory ähnelt einer Standardklassenfactory für coerstell Bare com-Objekte. Projekt Objekte sind jedoch nicht codierbar. Sie können nur mit einer projektfactory erstellt werden.

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Ruft die projektfactory auf, die in Ihrem VSPackage implementiert ist, wenn ein Benutzer ein vorhandenes Projekt lädt oder in ein neues Projekt erstellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Das neue Project-Objekt stellt der IDE ausreichend Informationen zur Verfügung, um **Projektmappen-Explorer** aufzufüllen. Das neue Project-Objekt stellt außerdem die erforderlichen Schnittstellen zur Unterstützung aller relevanten UI-Aktionen bereit, die von der IDE initiiert werden.

 Sie können die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Schnittstelle in einer Klasse im Projekt implementieren. In der Regel befindet Sie sich in einem eigenen Modul.

 Projekte, die die aggregierte durch einen Besitzer unterstützen, müssen einen Besitzer Schlüssel in der Projektdatei beibehalten. Wenn die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> Methode für ein Projekt mit einem Besitzer Schlüssel aufgerufen wird, konvertiert das eigene Projekt seinen Besitzer Schlüssel in eine projektfactoryguid und ruft dann die- `CreateProject` Methode für diese projektfactory auf, um die tatsächliche Erstellung durchzuführen.

## <a name="create-an-owned-project"></a>Erstellen eines eigenen Projekts
 Ein Besitzer erstellt in zwei Phasen ein eigenes Projekt:

1. Durch Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> Methode. Dadurch erhält das eigene Projekt die Möglichkeit, ein aggregiertes Projekt Objekt basierend auf der Eingabe zu erstellen, die steuert `IUnknown` . Das Projekt im Besitz übergibt die inneren `IUnknown` und das aggregierte Objekt zurück an das Besitzer Projekt. Dadurch erhält das eigene Projekt die Möglichkeit, das Innere zu speichern `IUnknown` .

2. Durch Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> Methode. Das besitzende Projekt übernimmt die gesamte Instanziierung, wenn diese Methode aufgerufen wird `IVsProjectFactory::CreateProject` , anstatt wie bei Projekten, die nicht im Besitz von sind, nicht aufzurufen. Die `VSOWNEDPROJECTOBJECT` eingabeenumeration ist in der Regel das aggregierte besitzende Projekt. Das eigene Projekt kann diese Variable verwenden, um zu bestimmen, ob das Projekt Objekt bereits erstellt wurde (Cookie ist nicht gleich null) oder erstellt werden muss (Cookie ist gleich null).

   Projekttypen werden durch eine eindeutige Projekt-GUID identifiziert, ähnlich der CLSID eines coerbaren com-Objekts. In der Regel verarbeitet eine projektfactory das Erstellen von Instanzen eines einzelnen Projekt Typs, obwohl es möglich ist, dass eine projektfactory mehrere Projekttyp-GUID behandelt.

   Projekttypen sind einer bestimmten Dateinamenerweiterung zugeordnet. Wenn ein Benutzer versucht, eine vorhandene Projektdatei zu öffnen, oder versucht, ein neues Projekt zu erstellen, indem er eine Vorlage Klonen, verwendet die IDE die-Erweiterung für die Datei, um die entsprechende Projekt-GUID zu ermitteln.

   Sobald die IDE bestimmt, ob ein neues Projekt erstellt oder ein vorhandenes Projekt eines bestimmten Typs geöffnet werden muss, verwendet die IDE die Informationen in der Systemregistrierung unter **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** , um zu ermitteln, welches VSPackage die erforderliche projektfactory implementiert. Die IDE lädt dieses VSPackage. In der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode muss das VSPackage seine projektfactory bei der IDE registrieren, indem die-Methode aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> .

   Die primäre Methode der- `IVsProjectFactory` Schnittstelle ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , die zwei Szenarien behandeln sollte: das Öffnen eines vorhandenen Projekts und das Erstellen eines neuen Projekts. In den meisten Projekten wird der Projektzustand in einer Projektdatei gespeichert. In der Regel werden neue Projekte erstellt, indem eine Kopie der Vorlagen Datei an die Methode weitergegeben `CreateProject` und dann die Kopie geöffnet wird. Vorhandene Projekte werden instanziiert, indem die an die-Methode übergebenen Projektdateien direkt geöffnet werden `CreateProject` . Die- `CreateProject` Methode kann dem Benutzer je nach Bedarf zusätzliche Benutzeroberflächen Features anzeigen.

   Ein Projekt kann auch keine Dateien verwenden und stattdessen seinen Projektzustand in einem anderen Speichermechanismus als dem Dateisystem speichern, z. b. einer Datenbank oder einem Webserver. In diesem Fall handelt es sich bei dem an die Methode übergebenen Dateinamen Parameter `CreateProject` nicht tatsächlich um einen Dateisystempfad, sondern um eine eindeutige Zeichenfolge – eine URL –, um die Projektdaten zu identifizieren. Sie müssen nicht die Vorlagen Dateien kopieren, die an übermittelt werden, `CreateProject` um die Ausführung der entsprechenden Konstruktions Sequenz zu initiieren.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
