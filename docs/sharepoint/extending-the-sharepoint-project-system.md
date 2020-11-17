---
title: Erweitern des SharePoint-Projekt Systems | Microsoft-Dokumentation
description: Erweitern Sie das SharePoint-Projekt System. Erfahren Sie, wie Sie das SharePoint-Projekt System erweitern. Erfahren Sie mehr über allgemeine Entwicklungsaufgaben.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c017217f66e38eed6248b90efaeabce0efaa9c70
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672547"
---
# <a name="extend-the-sharepoint-project-system"></a>Erweitern des SharePoint-Projektsystems
  Sie können SharePoint-Lösungen erstellen, indem Sie eine Reihe von Projektvorlagen und Element Vorlagen in Visual Studio verwenden. Diese Vorlagen erfüllen die Anforderungen vieler Entwicklungsszenarien, Sie können jedoch einige Fälle ermitteln, in denen Sie keine erforderliche Funktionalität bereitstellen. In diesen Fällen können Sie das SharePoint-Projekt System erweitern.

## <a name="overview-of-the-sharepoint-project-system"></a>Übersicht über das SharePoint-Projekt System
 Das SharePoint-Projekt System basiert auf der grundlegenden Komponente von *SharePoint-Projekt Elementen*. Ein SharePoint-Projekt Element stellt eine einzelne SharePoint-Anpassung dar, z. b. eine Listen Definition, ein Webpart oder einen Inhaltstyp.

 Ein SharePoint-Projekt ist ein Visual Studio-Projekt, das ein oder mehrere SharePoint-Projekt Elemente enthält. SharePoint-Projekte enthalten außerdem zusätzliche Komponenten, die definieren, wie Projekt Elemente in Funktionen und Paketen für die Bereitstellung gruppiert werden.

 Weitere Informationen zum Inhalt von SharePoint-Projekt Elementen und SharePoint-Projekten finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Erweitern des SharePoint-Projekt Systems
 Es gibt folgende Möglichkeiten, um das SharePoint-Projekt System zu erweitern:

- Definieren Sie Ihre eigenen SharePoint-Projekt Elementtypen, und ordnen Sie Sie neuen Element Vorlagen oder Projektvorlagen in Visual Studio zu. Beispielsweise können Sie einen SharePoint-Projekt Elementtyp zum Erstellen einer benutzerdefinierten Aktion oder eines Felds definieren. Weitere Informationen finden Sie unter [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Erweitern Sie SharePoint-Projekt Elementtypen, die bereits in Visual Studio installiert sind. Beispielsweise können Sie einem Projekt Element in **Projektmappen-Explorer** ein Kontextmenü Element hinzufügen und das Projekt Element anpassen, wenn ein Entwickler das Menü Element auswählt. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md).

- Erweitern von SharePoint-Projekten. Beispielsweise können Sie Ereignishandler hinzufügen, um bestimmte Aufgaben auszuführen, wenn Elemente zu SharePoint-Projekten hinzugefügt oder daraus entfernt werden. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md).

- Erweitern Sie das Verpackungs-und Bereitstellungs Verhalten von SharePoint-Projekt Elementen und SharePoint-Projekten. Beispielsweise können Sie eigene Bereitstellungs Schritte erstellen, die beim Bereitstellen oder zurückziehen eines Projekts ausgeführt werden, oder Sie können zusätzliche benutzerdefinierte Aufgaben ausführen, wenn Visual Studio bestimmte Bereitstellungs Schritte ausführt. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Allgemeine Entwicklungsaufgaben
 Die folgenden allgemeinen Aufgaben können in Erweiterungen des SharePoint-Projekt Systems ausgeführt werden:

- Speichern Sie benutzerdefinierte Zeichen folgen Daten mit Projekt Elementen und in verschiedenen Typen von Projektdateien. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Konvertieren Sie ein Objekt im SharePoint-Projekt System in ein entsprechendes Objekt im Visual Studio-Automatisierungs Objektmodell oder im Integrations Objektmodell (oder umgekehrt). Weitere Informationen finden Sie unter " [KONVER" zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Siehe auch
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md)
- [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md)
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Programmier Konzepte und Funktionen für Erweiterungen für SharePoint-Tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
