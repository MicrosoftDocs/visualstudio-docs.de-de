---
title: Informationen zu domänenspezifischen Sprachen
description: Erfahren Sie, wie eine domänenspezifische Sprache (Domain-Specific Language, DSL) zum Ausdrücken von Anweisungen in einem bestimmten Problembereich oder einer Domäne entworfen wurde.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 144e8f965a456c4763a74daa2cedeb8c571e518f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908965"
---
# <a name="about-domain-specific-languages"></a>Informationen zu domänenspezifischen Sprachen

Anders als bei einer allgemeinen Sprache (z. b. c# oder UML) ist eine domänenspezifische Sprache (DSL) so konzipiert, dass Anweisungen in einem bestimmten Problembereich oder einer Domäne ausgedrückt werden.

Bekannte DSLs enthalten reguläre Ausdrücke und SQL. Jede DSL ist viel besser als eine allgemeine Sprache zum Beschreiben von Vorgängen für Text Zeichenfolgen oder eine Datenbank, aber viel schlimmer beim Beschreiben von Ideen, die außerhalb Ihres eigenen Bereichs liegen. Einzelne Branchen verfügen auch über eigene DSLs. In der Telekommunikationsbranche werden z. b. sprach Beschreibungs Sprachen häufig verwendet, um die Reihenfolge der Zustände in einem Telefonanruf anzugeben, und in der Luft Reisebranche wird eine Standard-DSL verwendet, um Flugbuchungen zu beschreiben.

Ihr Unternehmen und Ihr Projekt befassen sich auch mit speziellen Sätzen von Konzepten, die mit einer DSL beschrieben werden könnten. Sie können z. b. eine DSL für eine dieser Anwendungen definieren:

- Planen der Navigationspfade auf einer Website.

- Verkabelung von Diagrammen für elektronische Komponenten.

- Netzwerke mit Transport Bändern und Gepäck Behandlungsgeräten für einen Flughafen.

Beim Entwerfen einer DSL definieren Sie eine *Domänen Klasse* für jedes der wichtigen Konzepte in der Domäne, z. b. eine Webseite, eine Lamp oder ein Check-in-Desk für den Flughafen. Sie definieren *Domänen Beziehungen* , wie z. b. Hyperlink, Wire oder ein Fließband, um die Konzepte miteinander zu verknüpfen.

Benutzer Ihrer DSL erstellen *Modelle.* Modelle sind *Instanzen* der DSL. Sie beschreiben z. b. eine bestimmte Website oder die Verkabelung eines bestimmten Geräts oder das Gepäck Behandlungssystem an einem bestimmten Flughafen.

Die Benutzer können ein Modell als Diagramm oder als Windows Form anzeigen. Modelle können auch als XML angezeigt werden, d. h., wie Sie gespeichert werden. Wenn Sie eine DSL definieren, definieren Sie, wie die Instanzen der einzelnen Domänen Klassen und Beziehungen auf dem Bildschirm des Benutzers angezeigt werden. Eine typische DSL wird als Auflistung von Symbolen oder Rechtecke angezeigt, die mit Pfeilen verbunden sind.

Die folgende Abbildung zeigt ein kleines Modell in einer diagrammatischen DSL:

![Tudor-Stammbaummodell](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Was Sie mit DSLs tun können

Eine typische Anwendung einer DSL besteht darin, Programmcode oder andere Artefakte zu generieren. Wenn Sie die DSL definieren, können Sie *Textvorlagen* definieren, die ein Modell der DSL lesen und Textdateien generieren.

Beispielsweise könnten Sie Vorlagen schreiben, die einen Flughafen Plan akzeptieren und einen Teil der Software für die Gepäck Behandlung generieren, sowie einige der Benutzer Dokumente, in denen der Plan beschrieben wird.

Wenn Sie eine DSL definiert haben, können Sie Sie an andere Benutzer verteilen, die Sie auf Ihren eigenen Computern installieren können. Benutzer Ihrer DSL können Modelle in Visual Studio erstellen und bearbeiten.

Sie können auch Menübefehle und andere Tools definieren, die Benutzern helfen, die DSL zu bearbeiten, Validierungs Einschränkungen, um sicherzustellen, dass die DSL ordnungsgemäß verwendet wird, und Element Vorlagen, die Benutzer beim Erstellen neuer Instanzen unterstützen. Sie können eine oder mehrere DSLs mit ihren Tools und anderen Visual Studio-Erweiterungen als integriertes Paket einschließen.

In der Regel wird eine domänenspezifische Sprache erstellt, wenn ein Entwicklungsteam ähnlichen Code für mehrere Produkte schreiben muss. Beispielsweise kann ein Unternehmen, das sich auf Gepäck Behandlungssysteme spezialisiert hat, eine gepäcktrack-DSL definieren, aus der der Code für jede Installation generiert werden kann. Der Vorteil der DSL besteht darin, dass Sie von ihren Kunden verstanden werden kann, dass der Code, der aus ihr generiert wurde, zuverlässig ist und dass das System schnell aktualisiert werden kann, wenn sich die Anforderungen der Kunden ändern.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ermöglicht es Ihnen, eine domänenspezifische Sprache zu erstellen, die über einen eigenen grafischen Designer und eine eigene Diagramm Notation verfügt, und dann die Sprache zu verwenden, um für jedes Projekt den entsprechenden Quellcode zu generieren.

## <a name="domain-specific-development"></a>Domain-Specific Entwicklung

Die domänenspezifische Entwicklung ist der Prozess, bei dem die Teile Ihrer Anwendungen identifiziert werden, die mithilfe einer domänenspezifischen Sprache modelliert werden können. Anschließend wird die Sprache erstellt und für die Anwendungsentwickler bereitgestellt. Die Entwickler verwenden die domänenspezifische Sprache zum Erstellen von Modellen, die für Ihre Anwendungen spezifisch sind, verwenden die Modelle, um Quellcode zu generieren, und verwenden dann den Quellcode, um die Anwendungen zu entwickeln.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekte der grafischen Domain-Specific Entwicklung

Eine grafische domänenspezifische Sprache muss die folgenden Features enthalten:

- Notation

- Domänenmodell

- Artefaktgenerierung

- Serialisierung

- Integration in Visual Studio

### <a name="notation"></a>Notation

Eine domänenspezifische Sprache muss über einen relativ kleinen Satz von Elementen verfügen, der leicht definiert und erweitert werden kann, um domänenspezifische Konstrukte darzustellen. Eine Notation besteht aus Formen, die die Elemente und Connectors darstellen, die die Beziehungen zwischen Elementen auf einer grafischen Diagramm Oberfläche darstellen. In [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] können die Formen erweitert und verfeinert werden, um die Elemente der domänenspezifischen Sprache darzustellen.

### <a name="domain-model"></a>Domänen Modell

Eine domänenspezifische Sprache muss den Satz von Elementen und die Beziehungen zwischen Ihnen in eine kohärente Grammatik kombinieren. Außerdem muss definiert werden, ob Kombinationen aus Elementen und Beziehungen gültig sind. Programmiersprachen verhindern z. b. in der Regel die zirkuläre Vererbung, bei der eine Klasse von einer zweiten Klasse abgeleitet und die zweite Klasse von der ersten Klasse abgeleitet wird. Einschränkungen können auch verwendet werden, um Geschäftslogik auszudrücken, z. b. kann eine Person nicht von sich selbst abhängig sein. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] verwendet Einschränkungen, um die Arten von Einschränkungen auszudrücken, die für die meisten domänenspezifischen Sprachen erforderlich sind.

### <a name="artifact-generation"></a>Artefaktgenerierung

Einer der Hauptzwecke einer domänenspezifischen Sprache besteht darin, ein Element zu generieren, z. b. Quellcode, eine XML-Datei oder andere verwendbare Daten. In der Regel bedeutet eine Änderung im Modell eine Änderung des Artefakts. Sie können [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] zum Generieren von Artefakten und zum erneuten Generieren von Artefakten verwenden, wenn Sie das Modell ändern.

### <a name="serialization"></a>Serialisierung

Eine domänenspezifische Sprache muss in einer Form beibehalten werden, die bearbeitet, gespeichert, geschlossen und erneut geladen werden kann. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] verwendet ein XML-Format, mit dem Sie definieren und anpassen können, wie Ihre domänenspezifische Sprache serialisiert oder beibehalten wird.

### <a name="integration-with-visual-studio"></a>Integration in Visual Studio

Da [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] in Visual Studio gehostet wird, werden viele Visual Studio-Fenster und-Steuerelemente erweitert. Außerdem können Sie das Verhalten von Menübefehlen, Toolbox Elementen und anderen Elementen der Benutzeroberfläche anpassen.

Sie können auch einen modellbus Adapter für Ihre domänenspezifische Sprache erstellen. Mit diesem Adapter können Sie auf ein Modell und Elemente innerhalb eines Modells verweisen, und Sie können Code schreiben, der auf eine Instanz der DSL zugreifen und diese aktualisieren kann. Mit dem leistungsfähigen modellbus Mechanismus können Sie Visual Studio-Erweiterungen schreiben, die mit mehreren Modellen funktionieren. Sie können auch eigenständige Anwendungen schreiben, die mit Modellen arbeiten. Weitere Informationen finden Sie unter [integrieren von Modellen mit Visual Studio-ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Vorteile der Domain-Specific Entwicklung

Eine domänenspezifische Sprache kann die folgenden Vorteile bieten:

- Enthält Konstrukte, die exakt an den Problembereich angepasst sind.

     Anders als allgemeine Sprachen besteht eine domänenspezifische Sprache aus Elementen und Beziehungen, die die Logik des Problem Raums direkt darstellen. Beispielsweise muss eine Versicherungsrichtlinien Anwendung Elemente für Richtlinien und Ansprüche enthalten. Eine domänenspezifische Sprache erleichtert das Entwerfen der Anwendung und das Auffinden und Beheben von Logik Fehlern.

- Ermöglicht nicht-Entwicklern und Personen, die die Domäne nicht kennen, den Gesamtentwurf zu verstehen.

     Wenn Sie eine grafische domänenspezifische Sprache verwenden, können Sie eine visuelle Darstellung der Domäne erstellen, damit nicht--Entwickler das Design der Anwendung leicht nachvollziehen können.

- Erleichtert das Erstellen eines Prototyps der abschließenden Anwendung.

     Entwickler können den Code, den Ihr Modell generiert, verwenden, um eine Prototypanwendung zu erstellen, die Sie Clients anzeigen können.

## <a name="the-process-of-domain-specific-development"></a>Der Prozess der Domain-Specific Entwicklung

Die meisten Softwareentwicklungsteams, die domänenspezifische Sprachen verwenden, führen die folgenden Schritte aus, um Ihre Modelle zu erstellen und zu verwenden:

- Das Team unterscheidet die Variablen Teile der Domäne von den Teilen, die sich nie ändern.

- Die Entwickler schreiben Code für die fixierten Teile und belassen Erweiterungs Punkte für die Variablen Teile.

- Der Lead Softwareentwickler oder der Architekt erstellt eine domänenspezifische Sprache, die die Entwurfsmuster der fixierten Teile der Domäne und die Erweiterungs Punkte für die Variablen Teile enthält.

- Der Lead Softwareentwickler oder der Architekt stellt die domänenspezifische Sprache für die Entwickler der verschiedenen vom Team erstellten Anwendungen bereit.

- Jeder Entwickler erstellt ein Modell, das für die jeweilige Anwendung gilt.
