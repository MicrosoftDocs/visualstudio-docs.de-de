---
title: 'Integration der Quell Code Verwaltung: Übersicht | Microsoft-Dokumentation'
description: 'Erfahren Sie mehr über die Unterschiede zwischen den beiden Möglichkeiten zum Integrieren der Quell Code Verwaltung in Visual Studio: ein Quellcodeverwaltungs-Plug-in und ein VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6bbd385c7089504949d2437091b0a2ea002fafdd
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876011"
---
# <a name="source-control-integration-overview"></a>Übersicht über die Integration der Quellcodeverwaltung
In diesem Abschnitt werden die beiden Möglichkeiten zur Integration in die Visual Studio-Quell Code Verwaltung verglichen. ein Quellcodeverwaltungs-Plug-in und ein VSPackage, das eine Quell Code Verwaltungs Lösung bereitstellt und die neuen Funktionen der Quell Code Verwaltung hervorhebt. Visual Studio ermöglicht einen manuellen Wechsel zwischen VSPackages der Quell Code Verwaltung und Quellcodeverwaltungs-Plug-ins sowie automatischen lösungsbasierten wechseln.

## <a name="source-control-integration"></a>Integration der Quellcodeverwaltung
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Typen von Integrationsoptionen für die Quell Code Verwaltung. In allen Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können Sie weiterhin ein Plug-in auf der Grundlage der Quellcodeverwaltungs-Plug-in-API integrieren (zuvor auch als MSSCCI-API bezeichnet), die grundlegende Funktionen der Quell Code Verwaltung bei Verwendung der Benutzeroberfläche der Visual Studio-Quell Code Verwaltung (UI) bereitstellt. Ein Quellcodeverwaltungs-VSPackage hingegen stellt einen neuen Deep-Integration-Pfad bereit, der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] für die Integration der Quell Code Verwaltung geeignet ist und ein hohes Maß an Komplexität und Autonomie in seinem Quell Code Verwaltungsmodell erfordert.

 ![Übersicht über die Quellcodeverwaltung](../../extensibility/internals/media/sourcectnrloverview.gif "Sourcectnrloverview")

## <a name="source-control-plug-in"></a>Quellcodeverwaltungs-Plug-in
 Alle Versionen von Visual Studio unterstützen die API-Spezifikation der Quellcodeverwaltungs-Plug-in, Version 1,2, als Integrations Pfad. Ein Quellcodeverwaltungs-Plug-in implementiert eine DLL, die die Quellcodeverwaltungs-Plug-in-API-Funktionen für die Integration und Registrierung der Quell Code Verwaltung implementiert, wie unter [Erstellen eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/creating-a-source-control-plug-in.md)beschrieben. Bei diesem Ansatz verwendet die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche für Dialogfelder, wie z. b. Einchecken, Auschecken, Extras/Optionen (Eigenschaften Seiten, Symbolleisten und Symbole der Quell Code Verwaltung). Strikte Einhaltung der Quellcodeverwaltungs-Plug-in-API sichert eine einfache Integration in Visual Studio und eine problemlose Benutzer Benutzerin. Dies bedeutet, dass das Quellcodeverwaltungs-Plug-in die meisten Funktionen und Rückrufe implementieren muss, die in der API ausführlich beschrieben werden.

 Gehen Sie folgendermaßen vor, um ein Quellcodeverwaltungs-Plug-in mithilfe der Quellcodeverwaltungs-Plug-in-API zu implementieren:

1. Erstellen Sie eine DLL, die die in [Quellcodeverwaltungs-Plug-ins](../../extensibility/source-control-plug-ins.md)angegebenen Funktionen implementiert.

2. Registrieren Sie die dll, indem Sie die entsprechenden Registrierungseinträge erstellen (siehe Vorgehens [Weise: Installieren eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Erstellen Sie eine hilfsprogrammbenutzer Oberfläche, und zeigen Sie diese an, wenn Sie vom Quellcodeverwaltungs-Adapter Paket (der Visual Studio-Komponente, die die Quell Code Verwaltung über Quellcodeverwaltungs-Plug

   Als Antwort auf einen Quell Code Verwaltungs Befehl stellt die Visual Studio-IDE eine Standardbenutzer Oberfläche für die grundlegenden Vorgänge dar und übergibt die Informationen dann an das Quellcodeverwaltungs-Plug-in über die Funktionen, die in der Quellcodeverwaltungs-Plug-in-API definiert sind. Für erweiterte Optionen kann das Quellcodeverwaltungs-Plug-in für eine eigene Benutzeroberfläche aufgerufen werden, z. b. Durchsuchen nach einem Projekt mit Quell Code Verwaltung. Dies bedeutet, dass dem Benutzer beim Umgang mit der Quell Code Verwaltung möglicherweise zwei unterschiedliche Arten von Benutzeroberflächen angezeigt werden: die von Visual Studio vorgestellte Benutzeroberfläche und die Benutzeroberfläche, die das Quellcodeverwaltungs-Plug-in darstellt. Dies ist mit erweiterten Quell Code Verwaltungs Vorgängen besonders bemerkbar.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Nachteile der Implementierung eines Quellcodeverwaltungs-Plug-ins

- Für erweiterte Features werden dem Benutzer möglicherweise zwei verschiedene Schnittstellen angezeigt, was zu Verwechslungen führt.

- Das Quellcodeverwaltungs-Plug-in ist auf das Quell Code Verwaltungsmodell beschränkt, das von der Quellcodeverwaltungs-Plug-in-API impliziert wird.

- Die Quellcodeverwaltungs-Plug-in-API ist möglicherweise für einige Quell Code Verwaltungs Szenarien zu restriktiv.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vorteile der Implementierung eines Quellcodeverwaltungs-Plug-ins

- Visual Studio stellt die gesamte Benutzeroberfläche für alle grundlegenden Quell Code Verwaltungsvorgänge bereit, sodass das Quellcodeverwaltungs-Plug-in keine potenziell komplexe Benutzeroberfläche implementieren muss.

- Aufgrund der strikten API kann das Quellcodeverwaltungs-Plug-in problemlos mit externen Quell Code Verwaltungsprogrammen interagieren, um umfangreichere Funktionen bereitzustellen. Visual Studio kümmert sich nicht darum, wie die Funktionen der Quell Code Verwaltung erreicht werden, sondern nur, dass Sie gemäß der Quellcodeverwaltungs-Plug-in-API durchgeführt werden.

- Es ist einfacher, ein Quellcodeverwaltungs-Plug-in als ein Quellcodeverwaltungs-VSPackage zu implementieren.

## <a name="source-control-vspackage"></a>Quellcodeverwaltungs-VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ermöglicht die umfassende Integration in Visual Studio mit vollständiger Kontrolle über die Funktionen der Quell Code Verwaltung und die vollständige Ersetzung der von Visual Studio bereitgestellten Benutzeroberfläche für die Quell Code Verwaltung. Ein Quellcodeverwaltungs-VSPackage ist in Visual Studio registriert und bietet Funktionen für die Quell Code Verwaltung. Obwohl mehrere Quellcodeverwaltungs-VSPackages bei Visual Studio registriert werden können, kann jeweils nur eine von Ihnen gleichzeitig aktiv sein. Ein Quellcodeverwaltungs-VSPackage verfügt über vollständige Kontrolle über die Funktionen und Darstellung der Quell Code Verwaltung in Visual Studio, während es aktiv ist. Alle anderen VSPackages der Quell Code Verwaltung, die möglicherweise im System registriert sind, sind inaktiv und zeigen überhaupt keine Benutzeroberfläche an.

 Zum Implementieren eines VSPackage für die Quell Code Verwaltung ist eine all-oder Nothing-Strategie erforderlich. Der Ersteller eines Quellcodeverwaltungs-VSPackages muss einen beträchtlichen Aufwand bei der Implementierung einer Reihe von Quell Code Verwaltungs Schnittstellen und neuen Benutzeroberflächen Elementen (Dialogfelder, Menüs und Symbolleisten) investieren, um die gesamte Funktionalität der Quell Code Verwaltung abzudecken. Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackages](../../extensibility/internals/creating-a-source-control-vspackage.md) .

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Nachteile der Implementierung eines Quellcodeverwaltungs-VSPackages

- Das VSPackage muss eine Reihe komplexer Schnittstellen implementieren, damit es in Visual Studio erfolgreich integriert werden konnte.

- Das VSPackage muss die gesamte Benutzeroberfläche bereitstellen, die für die Quell Code Verwaltung erforderlich ist. Visual Studio bietet keine Unterstützung in diesem Bereich.

- Ein Quellcodeverwaltungs-VSPackage ist eng an Visual Studio gebunden und kann nicht mit eigenständigen Programmen verwendet werden, sodass die Funktionalität nicht so einfach für eine externe Version des Quell Code Verwaltungs Programms freigegeben werden kann.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vorteile der Implementierung eines Quellcodeverwaltungs-VSPackages

- Da das VSPackage über die vollständige Kontrolle über die Benutzeroberfläche und die Funktionalität der Quell Code Verwaltung verfügt, wird dem Benutzer eine nahtlose Oberfläche für die Quell Code Verwaltung angezeigt.

- Das VSPackage ist nicht auf ein bestimmtes Quell Code Verwaltungsmodell beschränkt.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltung](../../extensibility/internals/source-control.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Neuigkeiten in der Quellcodeverwaltung](../../extensibility/internals/what-s-new-in-source-control.md)
