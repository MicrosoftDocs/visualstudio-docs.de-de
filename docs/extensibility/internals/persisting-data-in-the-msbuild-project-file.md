---
title: Beibehalten von Daten in der MSBuild-Projektdatei | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Daten in einer Projektdatei beibehalten und ipersistxmlfragment verwenden, um die Daten in der Projektdatei über Projekt Untertyp-Aggregations Ebenen hinweg beizubehalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d2011cd8686f3210ee534fdaefaa26d2f3b4ad5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954448"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Beibehalten von Daten in der MSBuild-Projektdatei
Ein Projekt Untertyp muss möglicherweise Untertyp spezifische Daten für die spätere Verwendung in der Projektdatei beibehalten. Ein Projekt Untertyp verwendet die Persistenz von Projektdateien, um die folgenden Anforderungen zu erfüllen:

1. Beibehalten von Daten, die beim Projekt Aufbau verwendet werden. (Weitere Informationen zum Microsoft-Build-Engine finden Sie unter [MSBuild](../../msbuild/msbuild.md).) Buildbezogene Informationen können folgende Aktionen ausführen:

    1. Konfigurations unabhängige Daten. Das heißt, Daten, die in MSBuild-Elementen mit leeren oder fehlenden Bedingungen gespeichert werden.

    2. Konfigurations abhängige Daten. Das heißt, dass Daten in MSBuild-Elementen gespeichert werden, die für eine bestimmte Projekt Konfiguration bedingt sind. Beispiel:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Speichert Daten, die für die Erstellung nicht relevant sind. Diese Daten können in frei Form-XML ausgedrückt werden, das nicht anhand eines XML-Schemas überprüft wird.

    1. Konfigurations unabhängige Daten.

    2. Konfigurations abhängige Daten.

## <a name="persisting-build-related-information"></a>Persistente Build-Related Informationen
 Die Persistenz von Daten, die zum Erstellen eines Projekts hilfreich sind, wird über MSBuild behandelt. Das MSBuild-System verwaltet eine Master Tabelle mit Build-bezogenen Informationen. Projekt Untertypen sind für den Zugriff auf diese Daten verantwortlich, um Eigenschaftswerte zu erhalten und festzulegen. Projekt Untertypen können die Build-bezogene Datentabelle auch erweitern, indem Sie zusätzliche Eigenschaften hinzufügen, die persistent gespeichert werden sollen, und indem Sie Eigenschaften entfernen, sodass Sie nicht persistent sind.

 Zum Ändern der MSBuild-Daten ist ein Projekt Untertyp für das Abrufen des MSBuild-Eigenschaften Objekts aus dem Basisprojekt System über verantwortlich <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> ist eine Schnittstelle, die auf dem Kernprojekt System implementiert ist, und die aggregierten Projekt Untertypen Abfragen dafür durch Ausführen von `QueryInterface` .

 Im folgenden Verfahren werden die Schritte zum Entfernen einer Eigenschaft mithilfe von beschrieben <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>So entfernen Sie eine Eigenschaft aus einer MSBuild-Projektdatei

1. Ruft `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> den Projekt Untertyp auf.

2. Wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> aufgerufen `pszPropName` , wenn auf die Eigenschaft festgelegt ist, die Sie entfernen möchten.

### <a name="persisting-non-build-related-information"></a>Beibehalten von nicht Build bezogenen Informationen
 Die Persistenz von Daten in Projektdateien, die nicht für den Build wichtig sind, wird durch behandelt <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> .

 Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> für das Haupt `project subtype aggregator` Objekt, das- `project subtype project configuration` Objekt oder beides implementieren.

 Die folgenden Punkte beschreiben die Hauptkonzepte bezüglich der Persistenz von Informationen, die nicht im Build zusammenhängen.

- Das Basisprojekt Ruft für den Hauptprojekt Untertyp (d. h. das äußerste Projekt Untertyp) Aggregator-Objekt auf, um die Konfigurations unabhängigen Daten zu laden und zu speichern, und ruft die Projekt Konfigurationsobjekte des Projekt unter Typs auf, um Konfigurations abhängige Daten zu laden oder zu speichern.

- Das Basisprojekt Ruft die Methoden von mehrmals <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> für jede Ebene der Projekt Untertypen Aggregation auf und übergibt die GUID für jede Ebene.

- Das Basisprojekt übergibt oder empfängt ein XML-Fragment, das einem bestimmten Projekt Untertyp zugeordnet ist, und verwendet diesen Mechanismus als Möglichkeit zum Beibehalten des Zustands zwischen den Aggregations Ebenen.

- Das Basisprojekt Ruft die Implementierung des äußersten Projekt unter Typs auf, wobei <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> eine GUID übergeben wird. Wenn die GUID zum äußersten Projekt Untertyp gehört, wird der eigentliche Rückruf behandelt. Andernfalls wird der-Aufrufe an einen inneren Projekt Untertyp delegiert usw., bis der Projekt Untertyp gefunden wird, dem die GUID entspricht.

- Ein Projekt Untertyp kann das XML-Fragment auch vor oder nach dem Delegaten des Aufrufes an einen inneren Projekt Untertyp ändern. Das folgende Beispiel zeigt einen Auszug aus einer Projektdatei, bei der der Name einer Datei, die Eigenschaften enthält, die für einen Projekt Untertyp spezifisch sind, an diesen Projekt Untertyp übermittelt wird.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Weitere Informationen
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)
