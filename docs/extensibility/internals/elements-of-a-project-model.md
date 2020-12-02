---
title: Elemente eines Projekt Modells | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Elemente eines Projekt Modells und darüber, wie die Schnittstellen und Implementierungen aller Projekte in Visual Studio eine grundlegende Struktur gemeinsam verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e366b2923d5903f00241db0a6b71017dc25f3dee
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480043"
---
# <a name="elements-of-a-project-model"></a>Elemente eines Projekt Modells
Die Schnittstellen und Implementierungen aller Projekte in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] haben eine grundlegende Struktur gemeinsam: das Projekt Modell für den Projekttyp. In Ihrem Projekt Modell, bei dem es sich um das VSPackage handelt, das Sie entwickeln, erstellen Sie Objekte, die ihren Entwurfsentscheidungen entsprechen und zusammen mit der von der IDE bereitgestellten globalen Funktionalität funktionieren. Obwohl Sie steuern, wie ein Projekt Element beibehalten wird, Steuern Sie z. b. die Benachrichtigung, dass eine Datei beibehalten werden muss. Wenn ein Benutzer den Fokus auf ein geöffnetes Projekt Element setzt und im Menü **Datei** in der Menüleiste die Option **Speichern** auswählt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , muss der Projekttyp Code den Befehl aus der IDE abfangen, die Datei persistent speichern und die Benachrichtigung an die IDE zurücksenden, dass die Datei nicht mehr geändert wird.

 Das VSPackage interagiert mit der IDE über Dienste, die Zugriff auf die IDE-Schnittstellen bereitstellen. Beispielsweise können Sie über bestimmte Dienste Befehle überwachen und weiterleiten und Kontextinformationen für die im Projekt vorgenommenen Auswahl bereitstellen. Alle globalen IDE-Funktionen, die für Ihr VSPackage benötigt werden, werden von-Diensten bereitgestellt. Weitere Informationen zu Diensten finden Sie unter Gewusst [wie: erhalten eines Diensts](../../extensibility/how-to-get-a-service.md).

 Weitere Überlegungen zur Implementierung:

- Ein einzelnes Projekt Modell kann mehr als einen Projekttyp enthalten.

- Projekttypen und die entsprechenden projektfactorys werden unabhängig von GUIDs registriert.

- Jedes Projekt muss über eine Vorlagen Datei oder einen Assistenten verfügen, um die neue Projektdatei zu initialisieren, wenn ein Benutzer über die Benutzeroberfläche ein neues Projekt erstellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Die [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Vorlagen initialisieren z. b., was schließlich zu VCPROJ-Dateien wird.

  Die folgende Abbildung zeigt die primären Schnittstellen, Dienste und Objekte, die eine typische Projekt Implementierung bilden. Sie können das Anwendungs Hilfsprogramm, `HierUtil7` , verwenden, um die zugrunde liegenden Objekte und andere Programmier Bausteine zu erstellen. Weitere Informationen zum Anwendungs Hilfsprogramm `HierUtil7` finden Sie unter [Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekt Typs (C++)](/previous-versions/bb166212(v=vs.100)).

  ![Grafik zum Visual Studio-Projekt Modell](../../extensibility/internals/media/vsprojectmodel.gif "vsprojectmodel") Projekt Modell

  Weitere Informationen zu den im vorherigen Diagramm aufgelisteten Schnittstellen und Diensten sowie zu anderen optionalen Schnittstellen, die nicht im Diagramm enthalten sind, finden Sie unter [Projekt Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md).

  Projekte können Befehle unterstützen und müssen daher die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementieren, um am Befehls Routing über die Befehls Kontext-GUIDs teilnehmen zu können.

## <a name="see-also"></a>Siehe auch
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekt Typs (C++)](/previous-versions/bb166212(v=vs.100))
- [Projekt Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)
- [Erstellen von Projekt Instanzen mithilfe von projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Vorgehensweise: erhalten eines Dienstanbieter](../../extensibility/how-to-get-a-service.md)
- [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)