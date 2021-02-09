---
title: Übersicht über domänenspezifische Sprachtools
description: Erfahren Sie, wie Sie mit DSL-Tools (Domain-Specific Language Tools) eine domänenspezifische Sprache entwerfen und sämtliche Bestandteile generieren, die Benutzer zum Erstellen von Modellen benötigen, die auf dieser Sprache basieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dbae3a1b36e6a948766c7dc31d4a8ea8af6d70c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897771"
---
# <a name="overview-of-domain-specific-language-tools"></a>Übersicht über domänenspezifische Sprachtools
DSL-Tools (Domain-Specific Language Tools, domänenspezifische Sprachtools), die in Visual Studio gehostet werden, ermöglichen Ihnen das Entwerfen einer domänenspezifischen Sprache. Anschließend können Sie sämtliche Komponenten generieren, die Benutzer zum Erstellen von Modellen basierend auf der Sprache benötigen.

 Die folgenden Tools gehören zu den DSL-Tools:

- Ein Projekt-Assistent, der verschiedene Projektmappenvorlagen verwendet, um Ihnen die Entwicklung von domänenspezifischen Sprachen zu erleichtern.

- Ein grafischer Designer zum Erstellen und Bearbeiten der domänenspezifischen Sprachdefinition.

- Eine Validierungs-Engine, die sicherstellt, dass die domänenspezifische Sprachdefinition richtig formatiert ist, und bei Problemen Fehler- und Warnmeldungen anzeigt.

- Ein Codegenerator, der eine domänenspezifische Sprachdefinition als Eingabe behandelt und anschließend Quellcode ausgibt.

## <a name="the-dsl-tools-solution"></a>Die Projektmappe für DSL-Tools
 Der DSL-Designer-Assistent stellt die folgenden Projektmappenvorlagen zur Verfügung:

- Aufgabenfluss

- Klassendiagramme

- Minimal Language (Einfache Version der Sprache)

- Komponentenmodelle

- Minimal WPF (Einfache Version von WPF)

- Minimal Windows.Forms (Einfache Version von Windows.Forms)

- DSL-Bibliothek

  Weitere Informationen finden Sie unter [Choosing a Domain-Specific Language Solution Template (Auswählen einer Projektmappenvorlage für eine domänenspezifische Sprache)](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Der Assistent erstellt eine Visual Studio-Projektmappe, die die folgenden Projekte enthält:

- DSL

   Das DSL-Projekt definiert die domänenspezifische Sprache sowie Tools zum Bearbeiten und für die Verarbeitung.

- **DslPackage**

   Das DslPackage-Projekt bestimmt, wie die Sprachtools mit Visual Studio integriert werden.

## <a name="the-dsl-tools-graphical-interface"></a>Die grafische Benutzeroberfläche der DSL-Tools
 Sie können die grafische Benutzeroberfläche der DSL-Tools verwenden, um Elemente und Beziehungen zu Ihrer domänenspezifischen Sprache hinzuzufügen. Wenn Sie die Elemente hinzugefügt haben, können Sie deren Darstellung definieren, indem Sie ihnen Formen zuordnen, Farben anpassen und Decorator-Elemente hinzufügen. Sie können die Elemente auch der Toolbox hinzufügen.

## <a name="validation-in-dsl-tools"></a>Validierung in DSL-Tools
 Die DSL-Tools umfassen eine Validierungsebene, die sicherstellt, dass das Domänenmodell die allgemeinen Anforderungen für die Codegenerierung erfüllt. Wenn Sie Ihre eigene domänenspezifische Sprache erstellen, sollten Sie Ihre eigene Validierung hinzufügen, um die Regeln Ihrer Geschäftslogik auszudrücken. Weitere Informationen zur benutzerdefinierten Validierung finden Sie unter [Validation in a Domain-Specific Language (Validierung in einer domänenspezifischen Sprache)](../modeling/validation-in-a-domain-specific-language.md).

 Es wird empfohlen, eigene domänenspezifische Sprachen während des Entwurfvorgangs häufig zu überprüfen. Wenn Ihre domänenspezifische Sprache Validierungsfehler aufweist, können Sie keinen Quellcode erstellen. Sie können anhand der Vorlagen Quellcode erstellen, indem Sie in der Symbolleiste des Projektmappen-Explorers auf **Alle Vorlagen transformieren** klicken. Auch wenn Sie die Sprachdefinition ändern, sollten Sie anschließend immer **alle Vorlagen transformieren**. Weitere Informationen finden Sie unter [Vorgehensweise: Create a Domain-Specific Language Solution (Vorgehensweise: Erstellen einer Projektmappe für die domänenspezifische Sprache)](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Anpassen von DSL-Tools
 Sie können zusätzlichen Code zur Verfügung stellen, um das Verhalten des Modells zu verfeinern und Einschränkungen für Ihre Sprache zu definieren. Wenn nötig können Sie auch wichtige Änderungen vornehmen, indem Sie die Textvorlagen ändern.

## <a name="distributing-your-dsl-solution"></a>Verteilen Ihrer DSL-Projektmappe
 DSL-Tools generieren ein Paket, das in Visual Studio gehostet wird. Das Paket zeigt eine Toolbox, einen DSL-Explorer und andere Benutzeroberflächenelemente an, über die Benutzer mithilfe Ihrer domänenspezifischen Sprache Modelle erstellen können.

 Wenn Sie die Projektmappe für die DSL-Tools in Visual Studio erstellen und ausführen, zeigt Ihnen eine zweite Instanz von Visual Studio, wie Ihre domänenspezifische Sprache für den Benutzer aussieht. Wenn Sie überprüft haben, dass alles einwandfrei funktioniert, können Sie die `.vsix`-Datei verteilen, die um Buildordner des DslPackage-Projekts enthalten ist. Diese Datei kann auf anderen Computern als Visual Studio-Erweiterung für die Installation der DSL-Tools verwendet werden.  Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Weitere Informationen

- [Die experimentelle Instanz](../extensibility/the-experimental-instance.md)
- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))