---
title: Überlegungen zu Sandkasten Lösungen | Microsoft-Dokumentation
description: Erkunden Sie Sandbox-Lösungen, bei denen es sich um ein Feature in Microsoft SharePoint handelt, mit dem Website Sammlungs Benutzer ihre eigenen benutzerdefinierten Code Lösungen hochladen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17b310a3f992f80b04ad14bb6e038e05b009a4af
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970464"
---
# <a name="sandboxed-solution-considerations"></a>Überlegungen zu Sandkastenlösungen
  *Sandkasten Lösungen* sind eine Funktion in Microsoft SharePoint 2010, mit der Website Sammlungs Benutzer ihre eigenen benutzerdefinierten Code Lösungen hochladen können. Eine gängige Sandkasten Lösung ist, dass Benutzer ihre eigenen Webparts hochladen.

 Eine Sandkasten-SharePoint-Anwendung wird in einem sicheren, überwachten Prozess ausgeführt, der Zugriff auf einen begrenzten Teil der Webfarm hat. Microsoft SharePoint 2010 verwendet eine Kombination aus Features, projektmappenkatalogen, Lösungs Überwachung und einem Validierungs Framework, um Sandbox-Lösungen zu ermöglichen.

## <a name="specify-project-trust-level"></a>Projekt Vertrauens Ebene angeben
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unterstützt Sandkasten Lösungen über eine boolesche Projekt Eigenschaft namens *Sandbox-Lösung*. Diese Eigenschaft kann jederzeit im Projekt festgelegt werden, oder Sie kann angegeben werden, wenn Sie das Projekt im Assistenten zum Anpassen von **SharePoint** erstellen.

> [!NOTE]
> Das Ändern der *Sandkasten* -Projektmappeneigenschaft eines Projekts nach der Erstellung kann Validierungs Fehler verursachen.

 Die Lösung wird als Projekt Mappe mit Farmebene betrachtet, wenn die Eigenschaft für die *Sandbox-Lösung* auf **false** festgelegt ist, oder Sie wählen die Option **als Farm Lösung** bereitstellen aus. Die Projekt Mappe wird jedoch anders behandelt als eine Farm Lösung, wenn die Eigenschaft für die *Sandbox-Lösung* auf **true** festgelegt ist, oder Sie wählen die Option **als Sandkasten Lösung** bereitstellen im Assistenten aus.

## <a name="sharepoint-site-hierarchy"></a>SharePoint-Website Hierarchie
 Um zu verstehen, wie Sandkasten Lösungen funktionieren, ist es hilfreich zu wissen, dass SharePoint-Sites im Gültigkeitsbereich hierarchisch sind. Das oberste Element wird als Webfarm bezeichnet, und andere Elemente sind dieser untergeordnet:

 Webfarm

 Webanwendung A

 Website Sammlung a1

 Standort A1A

 Webanwendung B

 Website Sammlung B1

 Standort B1a

 Standort B1b

 Website Sammlung B2

 Standort B2A

 Wie Sie sehen können, können Webfarmen eine oder mehrere Webanwendungen enthalten, die wiederum eine oder mehrere Website Sammlungen enthalten können, die untergeordnete Sites aufweisen können usw. Änderungen, die an einer Website Sammlung vorgenommen werden, wirken sich nur auf diese Website Sammlung und keine andere aus. Änderungen, die auf der Webfarm Ebene vorgenommen werden, wirken sich jedoch auf alle Website Sammlungen in der Farm aus.

 Windows SharePoint Services (WSS) 3,0 ermöglicht Ihnen die Bereitstellung von Lösungen nur auf Farmebene, ermöglicht aber die Bereitstellung [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] auf Farmebene (Farm Lösung) oder auf der Website Sammlungs Ebene (Sandbox-Lösung).

## <a name="why-sandboxed-solutions"></a>Warum Sandbox-Lösungen?
 In WSS 3,0 konnten Lösungen nur auf der Farm Ebene bereitgestellt werden. Dies bedeutete, dass potenziell schädliche oder destabilisierende Lösungen bereitgestellt werden konnten, die sich auf die gesamte Webfarm und alle anderen Website Sammlungen und-Anwendungen ausgewirkt haben, die darunter ausgeführt werden. Mithilfe von Sandkasten Lösungen können Sie Ihre Lösungen jedoch für ein untergeordnetes Element der Farm bereitstellen, eine bestimmte Website Sammlung. Um zusätzlichen Schutz zu bieten, wird die Assembly der Lösung nicht in den Haupt [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] Prozess geladen (*w3wp.exe*). Stattdessen wird Sie in einen separaten Prozess geladen (*SPUCWorkerProcess.exe*). Dieser Prozess wird überwacht und implementiert Kontingente und Drosselung, um die Farm vor Sandbox-Lösungen zu schützen, die schädliche Aktivitäten ausführen, z. b. das Ausführen von engen Schleifen, die CPU-Zyklen beanspruchen.

## <a name="site-collection-solution-gallery"></a>Lösungskatalog für Website Sammlungen
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 verfügt über eine Funktion, die als "Site Collection Solution Gallery" bezeichnet wird. Sie können auf diese Funktion über die Seite SharePoint 2010-zentral Administration zugreifen oder indem Sie das Menü **Website Aktionen** öffnen, **Site Einstellungen** auswählen und dann auf der SharePoint-Website unter **Galerien** den Link **Lösungen** auswählen. Lösungs Kataloge sind Repository von Lösungen, mit denen Website Sammlungs Administratoren Lösungen in Ihren Website Sammlungen verwalten können.

 Der Lösungskatalog ist eine Dokumentbibliothek, die im Stamm Web der SharePoint-Website gespeichert ist. Der Lösungskatalog ersetzt Website Vorlagen und unterstützt Projektmappenpakete. Wenn eine SharePoint-Lösungspaket Datei (*. wsp*) hochgeladen wird, wird Sie als Sandkasten Lösung verarbeitet.

## <a name="sandboxed-solution-limitations"></a>Einschränkungen der Sandkasten Lösung
 Wenn eine Sandkasten Lösung bereitgestellt wird, ist das für Sie verfügbare Array von SharePoint-Funktionen so eingeschränkt, dass Sicherheitsrisiken, die möglicherweise auftreten, verringert werden. Zu diesen Einschränkungen gehören die folgenden:

- Sandkasten Lösungen verfügen über eine eingeschränkte Teilmenge der bereitstell baren Lösungs Elemente, die Ihnen zur Verfügung stehen. Potenziell anfällige SharePoint-Projektvorlagen, z. b. Website Definitionen und Workflows, sind nicht verfügbar.

- SharePoint führt einen Sandkasten Lösungs Code in einem Prozess (*SPUCWorkerProcess.exe*) aus, der vom Haupt [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] Prozess des Anwendungs Pools (*w3wp.exe*) getrennt ist.

- Zugeordnete Ordner können dem Projekt nicht hinzugefügt werden.

- Typen in der [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] Assembly "Microsoft. Office. Server" können nicht in Sandbox-Lösungen verwendet werden. Außerdem können nur Typen in der [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] Assembly "Microsoft. SharePoint" in Sandbox-Lösungen verwendet werden.

  Beachten Sie unbedingt, dass die Angabe einer SharePoint-Lösung als Sandkasten Lösung keine Auswirkung auf SharePoint Server hat. Es bestimmt nur, wie das SharePoint-Projekt in SharePoint bereitgestellt wird und welche Assemblys [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] es bindet. Sie hat keine Auswirkung auf die generierte *wsp* -Datei, und die *wsp* -Datei enthält keine Daten, die direkt mit der *Sandbox* -Projektmappeneigenschaft korrelieren.

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funktionen und Elemente in Sandkasten Lösungen
 Sandkasten Lösungen unterstützen die folgenden Funktionen und Elemente:

- Inhaltstypen/Felder

- Benutzerdefinierte Aktionen

- Deklarative Workflows

- Ereignisempfänger

- Funktionsaufrufe

- Definitionen auflisten

- Auflisten von Instanzen

- Module/Dateien

- Navigation

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- Spwebeventreceiver

- Unterstützung für alle Webparts, die von abgeleitet sind `System.Web.UI.WebControls.WebParts.WebPart`

- Webparts

- WebTemplate-Funktionselemente (anstelle von *Webtemp.xml*)

- Visual Webparts

  Sandkasten Lösungen unterstützen nicht die folgenden Funktionen und Elemente:

- Anwendungsseiten

- Benutzerdefinierte Aktionsgruppe

- Funktionen mit Farm Bereich

- `HideCustomAction`-Element

- Features von Webanwendungs Bereich

- Workflows mit Code

## <a name="see-also"></a>Weitere Informationen
- [Unterschiede zwischen Sandkasten-und Farm Lösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
