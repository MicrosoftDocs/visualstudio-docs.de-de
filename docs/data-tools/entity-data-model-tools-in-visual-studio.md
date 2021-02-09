---
title: Entity Framework-Tools
description: Verstehen Sie Entity Framework Tools in Visual Studio. Entity Framework Tools wurden entwickelt, um Sie beim Erstellen von Entity Framework (EF)-Anwendungen zu unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ee4bb5e56c5ae9ffb5f5266c8ef80804c8e96597
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866982"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools in Visual Studio

Entity Framework ist eine Objekt relationale Mapping-Technologie, die es .NET-Entwicklern ermöglicht, mithilfe von domänenspezifischen Objekten mit relationalen Daten zu arbeiten. Es entfällt die Notwendigkeit für den Großteil des Datenzugriffs-Codes, den Entwickler normalerweise schreiben müssen. Entity Framework ist die empfohlene ORM-Modellierungstechnologie (Object-Relational Mapping) für neue .NET-Anwendungen.

Entity Framework Tools wurden entwickelt, um Sie beim Erstellen von Entity Framework (EF)-Anwendungen zu unterstützen. Die komplette Dokumentation für Entity Framework finden Sie hier: [Übersicht-EF 6](/ef/ef6/).

  > [!NOTE]
  > Die auf dieser Seite beschriebenen Entity Framework Tools werden zum Generieren von *edmx* -Dateien verwendet, die in EF Core nicht unterstützt werden. Informationen zum Generieren eines EF Core Modells aus einer vorhandenen Datenbank finden Sie unter [Reverse Engineering-EF Core](/ef/core/managing-schemas/scaffolding). Weitere Informationen zu den Unterschieden zwischen EF 6 und EF Core finden Sie unter [Vergleichen von EF 6 und EF Core](/ef/efcore-and-ef6/).

Mit Entity Framework Tools können Sie ein *konzeptionelles Modell* aus einer vorhandenen Datenbank erstellen und dann das konzeptionelle Modell grafisch visualisieren und bearbeiten. Oder Sie können zuerst ein konzeptionelles Modell grafisch erstellen und anschließend eine Datenbank generieren, die das Modell unterstützt. In beiden Fällen können Sie das Modell automatisch aktualisieren, sobald sich die zugrunde liegende Datenbank ändert, und Sie können automatisch Code auf Objektebene für die Anwendung erstellen. Datenbank- und Codegenerierung auf Objektebene sind vom Benutzer anpassbar.

Die Entity Framework Tools werden im Rahmen der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert. Sie können Sie auch als einzelne Komponente unter der Kategorie **SDK, Bibliotheken und Frameworks** installieren.

Dabei handelt es sich um die spezifischen Tools, die Entity Framework Tools in Visual Studio bilden:

- Mit dem [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Designer** (**Entity Designer**) können Sie Entitäten, Zuordnungen, Zuordnungen und Vererbungs Beziehungen visuell erstellen und ändern. Der- **Entity Designer** generiert auch [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] objektebenencode.

- Sie können den **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Assistenten** verwenden, um ein konzeptionelles Modell aus einer vorhandenen Datenbank zu generieren und der Anwendung Daten bankverbindungs Informationen hinzuzufügen.

- Mit dem Assistenten zum **Erstellen einer Datenbank** können Sie zuerst ein konzeptionelles Modell erstellen und dann eine Datenbank erstellen, die das Modell unterstützt.

- Mit dem **Modellaktualisierungs-Assistenten** können Sie das konzeptionelle Modell, das Speichermodell und die Zuordnungen aktualisieren, wenn Änderungen an der zugrunde liegenden Datenbank vorgenommen wurden.

  > [!NOTE]
  > Ab Visual Studio 2010 werden von Entity Framework Tools nicht unterstützt [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)] .

Die-Tools generieren oder ändern eine *edmx* -Datei. Diese *edmx* -Datei enthält Informationen, in denen das konzeptionelle Modell, das Speichermodell und die Zuordnungen zwischen Ihnen beschrieben werden. Weitere Informationen finden Sie unter [edmx](/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) helfen Ihnen beim Erstellen von Anwendungen, die die Entity Data Model verwenden. Mit den Power Tools können Sie ein konzeptionelles Modell generieren, ein vorhandenes Modell überprüfen, Quell Code Dateien erstellen, die auf dem konzeptionellen Modell basierende Objektklassen enthalten, und Quell Code Dateien erstellen, die vom Modell generierte Sichten enthalten. Ausführliche Informationen finden Sie unter [vorab generierte Mapping-Sichten](/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Verwandte Themen

| Titel | Beschreibung |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Beschreibt [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] die Verwendung von Tools, die [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] bereitstellt, um-Anwendungen zu erstellen. |
| [Entity Data Model](/dotnet/framework/data/adonet/entity-data-model) | Enthält Links und Informationen zum Arbeiten mit Daten, die von Anwendungen verwendet werden, die auf basieren [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] . |
| [Entity Framework (EF)-Dokumentation)](/ef/ef6/get-started) | Bietet einen Index mit Videos, Tutorials und erweiterter Dokumentation, mit deren Hilfe Sie Entity Framework optimal nutzen können. |
| [ASP.net 5 Anwendung in neue Datenbank](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Hier wird beschrieben, wie Sie eine neue ASP.net 5-Anwendung mit Entity Framework 7 erstellen. |

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
