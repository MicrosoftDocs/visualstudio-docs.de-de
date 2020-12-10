---
title: Erweitern von Projekten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eigene benutzerdefinierte Projekttypen im Visual Studio SDK erstellen und unterschiedliche Typen von Visual Studio-Projektmappen verwalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181acea9a5188ba28a4ef109b5bec0e7c040b5da
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994614"
---
# <a name="extend-projects"></a>Erweitern von Projekten
Projekte und Projektmappen sind die Möglichkeiten, wie Visual Studio Code-und Ressourcen Dateien in Kompilierungs-und Bereitstellungs Einheiten organisiert. Weitere Informationen zu Projekten in [Projekten (Visual Studio SDK)](../extensibility/extending-projects.md)finden Sie hier.

 Sie können eigene Projekttypen mit dem Visual Studio SDK und dem Managed Package Framework für Projekte erstellen, die Sie unter [Managed Package Framework for Projects](https://github.com/tunnelvisionlabs/MPFProj10)herunterladen können. Informationen dazu, wie benutzerdefinierte Projekte implementiert werden, finden Sie unter [New Project Generation: at the Hood, Part One](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) and [New Project Generation: at the Hood, Part Two](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 In den Themen in diesem Abschnitt wird beschrieben, wie benutzerdefinierte Projekte erstellt werden und wie unterschiedliche Typen von Visual Studio-Projektmappen verwaltet werden.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erstellen eines grundlegenden Projekt Systems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) Beschreibt, wie ein benutzerdefiniertes Projekt System erstellt wird.

- [Erstellen eines grundlegenden Projekt Systems, Teil 2](../extensibility/creating-a-basic-project-system-part-2.md) Beschreibt, wie ein benutzerdefiniertes Projekt System erstellt wird.

- [Speichern von Daten in Projektdateien](../extensibility/saving-data-in-project-files.md) Erläutert, wie dem Projekt hinzugefügt wird (<em>.</em> proj *)-Dateien.

- [Überprüfen der Untertypen eines Projekts zur Laufzeit](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Erläutert, wie der Untertyp eines Projekts zur Laufzeit überprüft wird.

- [Hinzufügen und Entfernen von Eigenschaften Seiten](../extensibility/adding-and-removing-property-pages.md) Erläutert, wie die Eigenschaften Seiten für Ihr benutzerdefiniertes Projekt angepasst werden.

- [Hinzufügen eines Attributs zu einem Projekt Element](../extensibility/adding-an-attribute-to-a-project-item.md) Erläutert, wie einem benutzerdefinierten Projekt Element ein Attribut hinzugefügt wird.

- Persistente [Eigenschaft eines Projekt Elements](../extensibility/persisting-the-property-of-a-project-item.md) Erläutert, wie die Eigenschaften eines benutzerdefinierten Projekt Elements persistent gespeichert werden.

- [Universelle Windows-Projekte verwalten](../extensibility/managing-universal-windows-projects.md) Erläutert, wie universelle Projekte verwaltet werden.
