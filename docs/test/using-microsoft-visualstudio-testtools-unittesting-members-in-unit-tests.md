---
title: Verwenden von MSTest für Unittests
description: Erfahren Sie mehr über das MSTest-Framework, das Komponententests in Visual Studio unterstützt. Verwenden Sie diese Klassen und Member, um Komponententests zu codieren.
ms.custom: SEO-VS-2020
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 21e78263e848a501d83414630de734368f90a179
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598574"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Verwenden des MSTest-Frameworks in Komponententests

Das [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>)-Framework unterstützt Komponententests in Visual Studio. Verwenden Sie die Klassen und Member im <xref:Microsoft.VisualStudio.TestTools.UnitTesting>-Namespace, wenn Sie Code für Komponententests schreiben. Sie können sie auch verwenden, wenn Sie einen Komponententest verfeinern, der aus Code generiert wurde.

## <a name="framework-members"></a>Framework-Member

Für einen besseren Überblick über das Framework für Komponententests werden die Member des <xref:Microsoft.VisualStudio.TestTools.UnitTesting>-Namespaces in diesem Abschnitt in Gruppen verwandter Funktionen aufgeführt.

> [!NOTE]
> Attributelemente, deren Namen mit der Zeichenfolge „Attribute“ enden, können mit oder ohne „Attribute“ am Ende verwendet werden. So wird beispielsweise mit den folgenden beiden Codebeispiele das gleiche Ergebnis erzielt:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Für datengesteuerte Tests verwendete Member

Verwenden Sie die folgenden Elemente zum Einrichten eines datengesteuerten Komponententests. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines datengesteuerten Komponententests](../test/how-to-create-a-data-driven-unit-test.md) und [Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Zum Einrichten einer Aufrufreihenfolge verwendete Attribute

Ein mit einem der folgenden Attribute versehenes Codeelement wird zum angegebenen Zeitpunkt aufgerufen. Weitere Informationen finden Sie unter [Aufbau eines Komponententests](/previous-versions/ms182517(v=vs.110)).

### <a name="attributes-for-assemblies"></a>Attribute für Assemblys

AssemblyInitialize und AssemblyCleanup werden direkt nach dem Laden und direkt vor dem Entladen der Assembly aufgerufen.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Attribute für Klassen

ClassInitialize und ClassCleanup werden direkt nach dem Laden und direkt vor dem Entladen der Klasse aufgerufen.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Attribute für Testmethoden

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Zum Angeben von Testklassen und Testmethoden verwendete Attribute

Jede Testklasse muss das `TestClass`-Attribut aufweisen und jede Testmethode das `TestMethod`-Attribut. Weitere Informationen finden Sie unter [Aufbau eines Komponententests](/previous-versions/ms182517(v=vs.110)).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert-Klassen und zugehörige Ausnahmen

Im Rahmen von Komponententests kann mit verschiedenen Arten von Assertions, Ausnahmen und Attributen überprüft werden, ob sich eine Anwendung auf eine bestimmte Weise verhält. Weitere Informationen finden Sie unter [Verwenden der Assert-Klassen](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>Die TestContext-Klasse

Die folgenden Attribute und die diesen zugewiesenen Werte werden im Visual Studio-Eigenschaftenfenster für eine bestimmte Testmethode angezeigt. Diese Attribute dienen nicht dem Zugriff über den Code des Komponententests. Stattdessen beeinflussen sie, in welcher Weise der Komponententest ausgeführt wird – entweder von Ihnen über die IDE von Visual Studio oder von der Visual Studio-Test-Engine. Einige dieser Attribute werden beispielsweise im Fenster **Test Manager** und im Fenster **Testergebnisse** in Spalten angezeigt. Das bedeutet, dass Sie sie zum Gruppieren und Sortieren von Tests und Testergebnissen verwenden können. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> ist ein Attribut dieser Art. Mit ihm können beliebige Metadaten Komponententests hinzugefügt werden. Sie können es beispielsweise verwenden, um den Namen eines Testdurchlauf zu speichern, der von diesem Test abgedeckt wird, indem Sie den Komponententest mit `[TestProperty("TestPass", "Accessibility")]` kennzeichnen. Alternativ können Sie es verwenden, um einen Indikator zu speichern, der die Art des Tests angibt: `[TestProperty("TestKind", "Localization")]`. Die Eigenschaft, die durch die Verwendung dieses Attributs erstellt wird, und der zugewiesene Eigenschaftswert werden im Visual Studio-**Eigenschaftenfenster** unter der Überschrift **Testspezifisch** angezeigt.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Testkonfigurationsklassen

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Attribute, die zum Generieren von Berichten verwendet werden

Die in diesem Abschnitt beschriebenen Attribute verknüpfen die Testmethode, in der sie enthalten sind, mit Entitäten in der Projekthierarchie eines Team Foundation Server-Teamprojekts.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Mit privaten Accessoren verwendete Klassen

Sie können einen Komponententest für eine private Methode generieren. Dabei wird eine private Accessor-Klasse erstellt, die ein Objekt der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>-Klasse instanziiert. Bei der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>-Klasse handelt es sich um eine Wrapperklasse, die im Rahmen des Prozesses für den privaten Accessor Reflektionen verwendet. Die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>-Klasse ist ähnlich, unterscheidet sich jedoch insofern, als sie zum Aufrufen von privaten statischen Methoden statt von privaten Instanzmethoden verwendet wird.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Referenzdokumentation