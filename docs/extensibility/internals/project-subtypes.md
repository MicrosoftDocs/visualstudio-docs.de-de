---
title: Projekt Untertypen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Projekt Untertypen das Verhalten der Projektsysteme von Visual Studio anpassen können. VSPackages implementieren Projekt Untertypen mithilfe von com-Aggregationen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00d44014ced9253328890c34d877beb68120c0c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896794"
---
# <a name="project-subtypes"></a>Projektuntertypen
Mit Projekt Untertypen können Sie das Verhalten der Projektsysteme von anpassen oder anpassen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Zu den Anpassungen gehören das Speichern zusätzlicher Daten in der Projektdatei, das Hinzufügen oder Filtern von Elementen im Dialogfeld **Neues Element hinzufügen** , das Steuern der Deserialisierung und Bereitstellung von Assemblys und das Erweitern des Dialog Felds **Eigenschaften Seiten** für Projekt VSPackages implementieren Projekt Untertypen mithilfe von com-Aggregationen.

> [!NOTE]
> Projekt Untertypen werden vom Visual C++-Projekt System nicht unterstützt. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] selbst verwendet Projekt Untertypen, um SQL Server-und Smart Device-Projekte zu implementieren.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)

  Beschreibt das Konzept von Projekt Untertypen.

- [Initialisierungssequenz von Projektuntertypen](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Beschreibt die Initialisierungs Sequenz des programmatischen Projekt unter Typs nach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung.

- [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Stellt ausführliche Beschreibungen der Features und Methoden bereit, die am häufigsten mithilfe von Projekt Untertypen erweitert werden.

- [Beibehalten von Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Beschreibt, wie Daten in einer Projektdatei persistent gespeichert werden und wie verwendet wird, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> um die Daten in der Projektdatei über die Aggregations Ebenen des Projekt unter Typs hinweg beizubehalten.

- [Benutzeroberfläche für Projekteigenschaften](../../extensibility/internals/project-property-user-interface.md)

  Beschreibt, wie Projekt Untertypen das Dialogfeld **Eigenschaften Seiten** des Projekts ändern können.

- [Erweitern des Objektmodells des Basisprojekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Stellt Informationen dazu bereit, wie Projekt Untertypen automatisierungsexextender zum Erweitern des Automatisierungs Objektmodells verwenden können.

- [Mitwirken am Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Beschreibt das Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen** .

- [Speichern von Daten in Projektdateien](../../extensibility/saving-data-in-project-files.md)

  Erläutert, wie ein Projekt Untertyp unter typspezifische Daten in der Projektdatei mithilfe des Managed Package Framework (MPF) speichern und abrufen kann.

- [Behandlung einer speziellen Bereitstellung](../../extensibility/internals/handling-specialized-deployment.md)

  Erläutert, wie Projekt Untertypen ein spezielles Bereitstellungs Verhalten durch Implementieren der-Schnittstelle bereitstellen können <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .

- [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)

  Beschreibt das Hinzufügen und Entfernen von Eigenschaften Seiten im Projekt-Designer.

## <a name="related-sections"></a>Verwandte Abschnitte

- [Projekttypen](../../extensibility/internals/project-types.md)

  Enthält Links zu Themen, in denen-Projekte erläutert werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
