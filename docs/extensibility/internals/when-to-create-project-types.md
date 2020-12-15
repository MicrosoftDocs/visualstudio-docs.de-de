---
title: Zeitpunkt der Erstellung von Projekttypen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie bestimmen können, ob ein neuer Projekttyp erforderlich ist, um Visual Studio für Ihre Benutzer anzupassen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 458ca77ebcd8017b9834a8925edec255ca04cc13
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487828"
---
# <a name="when-to-create-project-types"></a>Gründe für das Erstellen von Projekttypen
Wenn Sie einen neuen Projekttyp erstellen, finden Sie eine Grundlage für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Anpassung für Ihre Benutzer. Es ist jedoch nicht erforderlich, einen neuen Projekttyp für alle Anpassungen zu erstellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Die folgenden Richtlinien sollen Ihnen dabei helfen zu bestimmen, ob ein neuer Projekttyp für Ihr Szenario erforderlich ist.

## <a name="create-a-new-project-type"></a>Neuen Projekttyp erstellen
 Sie müssen einen Projekttyp erstellen, wenn Sie eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oder mehrere der folgenden Methoden anpassen möchten:

- Nehmen Sie an Build, Bereitstellung, Konfigurationen und Quell Code Verwaltung Teil.

- Bietet Debugunterstützung.

- Zeigen Sie Projekt Elemente in **Projektmappen-Explorer** an.

- Verwenden Sie das Dialogfeld **Projekt öffnen** oder **Neues Projekt** .

- Unterstützung der Projekt Schachtelung

## <a name="extend-an-existing-project-type"></a>Erweitern eines vorhandenen Projekt Typs
 Möglicherweise möchten Sie einen neuen Projekttyp erstellen, der auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die folgenden Arten verwenden kann, um das Verhalten eines vorhandenen Projekt Typs zu ändern oder zu erweitern, z. b. zum Ändern des Buildprozesses für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte:

- Arbeiten Sie mit mehreren Dateien als einzelne Einheit.

- Zeigt eine einzelne Datei als Hierarchie von unter Elementen an.

- Anzeigen eines Befehls Kontexts um Editoren.

- Zeigen Sie einen Dienst Kontext für Editoren an.

## <a name="use-an-existing-project-type"></a>Vorhandenen Projekttyp verwenden
 Das Erstellen eines neuen Projekts ist manchmal nicht erforderlich. In der folgenden Tabelle sind die Tasks aufgeführt, für die Sie keinen Projekttyp erstellen müssen.

|Aufgabe|Beschreibung|
|----------|-----------------|
|Verarbeiten von Befehlen|Alle VSPackage können Befehle verarbeiten.|
|Aufbauen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument Fenster und Editoren](/previous-versions/bb165691(v=vs.100)).|
|Besitzende Fenster|Sie können sowohl Tool-als auch Dokument Fenster erstellen, ohne einen neuen Projekttyp hinzuzufügen.|
|Verfügbar machen von Eigenschaften im Eigenschaftenfenster|Alle-Objekte können Eigenschaften verfügbar machen.|

## <a name="create-a-project-subtype"></a>Erstellen eines Projekt unter Typs
 Mithilfe von Projekt Untertypen können Sie einen verwalteten Projekttyp erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projekt Untertypen verwenden com-Aggregation, um verwaltete Projekte zu erweitern, die in Microsoft oder geschrieben wurden [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Mit com-Aggregation können Sie einen Großteil der Implementierung des verwalteten Projekt Systems wieder verwenden und dennoch für ein bestimmtes Szenario durch Aggregation und die Verwendung von unterstützenden Schnittstellen anpassen. Weitere Informationen zu Projekt Untertypen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Weitere Informationen
- [Dokument Fenster und-Editoren](/previous-versions/bb165691(v=vs.100))
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)