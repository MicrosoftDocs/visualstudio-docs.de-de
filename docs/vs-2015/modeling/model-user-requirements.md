---
title: Modell Benutzer Anforderungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a94a4bd479c3ad48efe44d3a92e91dc3a050efcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918269"
---
# <a name="model-user-requirements"></a>Modellieren von Benutzeranforderungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hilft Ihnen dabei, die Anforderungen der Benutzer zu verstehen, zu besprechen und zu kommunizieren, indem Diagramme über ihre Aktivitäten und die Rolle Ihres System bei der Erreichung ihrer Ziele gezeichnet werden. Ein Anforderungsmodell ist ein Satz dieser Diagramme, von denen sich jedes auf einen anderen Aspekt der Benutzeranforderungen konzentriert. Eine Videodemo finden Sie unter: [Modeling the Business Domain](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)(Modellieren der Geschäftsdomäne) .

 Informationen dazu, welche Versionen von Visual Studio die einzelnen Modelltypen unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Ein Anforderungsmodell hilft Ihnen bei Folgendem:

- Konzentration auf das externe Verhalten des Systems, unabhängig von seinem internen Entwurf.

- Beschreiben der Anforderungen von Benutzern und Projektbeteiligten mit deutlich weniger Mehrdeutigkeiten als in der natürlichen Sprache.

- Definieren eines konsistenten Glossars von Begriffen, das von Benutzern, Entwicklern und Testern verwendet werden kann.

- Reduzieren von Lücken und Inkonsistenzen hinsichtlich der Anforderungen.

- Reduzieren der für die Reaktion auf Anforderungsänderungen notwendigen Arbeit.

- Planen der Reihenfolge, in der Funktionen entwickelt werden.

- Verwenden der Modelle als Grundlage für Systemtests, um eine klare Beziehung zwischen den Tests und den Anforderungen herzustellen. Wenn sich die Anforderungen ändern, hilft Ihnen diese Beziehung beim ordnungsgemäßen Aktualisieren der Tests. Dadurch wird sichergestellt, dass das System die neuen Anforderungen erfüllt.

  Ein Anforderungsmodell bietet den größten Vorteil, wenn Sie es für die Ausrichtung von Besprechungen mit den Benutzern oder ihren Vertretern einsetzen und es am Anfang jeder Iteration überdenken. Sie müssen es nicht im Detail fertigstellen, bevor Sie Code schreiben. Eine teilweise funktionierende Anwendung bildet in der Regel, auch wenn sie sehr vereinfacht ist, die anregendste Grundlage für die Besprechung der Anforderungen mit den Benutzern. Das Modell ist eine effektive Methode, um die Ergebnisse solcher Diskussionen zusammenzufassen. Weitere Informationen finden Sie unter [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> In diesen Themen meint „System“ das System oder die Anwendung, das bzw. die Sie entwickeln. Es kann sich um eine umfangreiche Sammlung von vielen Software- und Hardwarekomponenten, eine einzelne Anwendung oder eine Softwarekomponente in einem größeren System handeln. In jedem Fall beschreibt das Anforderungsmodell das Verhalten, das über eine Benutzeroberfläche oder eine API von außerhalb Ihres Systems sichtbar ist.

## <a name="common-tasks"></a>Allgemeine Aufgaben
 Sie können verschiedene Ansichten der Benutzeranforderungen erstellen.  Jede Ansicht bietet eine bestimmte Art von Informationen.  Wenn Sie diese Ansichten erstellen, empfiehlt es sich, häufig zwischen ihnen zu wechseln. Sie können bei jeder Ansicht starten.

|Diagramm oder Dokument|Was es in einem Anforderungsmodell beschreibt|`Section`|
|-------------------------|-----------------------------------------------|-------------|
|Anwendungsfalldiagramm|Wer das System verwendet und was sie damit tun|[Beschreiben, wie das System verwendet wird](#UseCases)|
|Konzeptionelles Klassendiagramm|Glossar von Typen, die zum Beschreiben der Anforderungen verwendet werden; die auf der Benutzeroberfläche des Systems sichtbaren Typen.|[Definieren von Begriffen, die zum Beschreiben der Anforderungen verwendet wurden](#RequirementsClasses)|
|Aktivitätsdiagramm|Arbeitsablauf und Informationsfluss zwischen den Aktivitäten, die von Benutzern und dem System oder seinen Teilen durchgeführt werden.|[Darstellen des Arbeitsablaufs zwischen Benutzern und dem System](#Workflow)|
|Sequenzdiagramm|Die Sequenz der Interaktionen zwischen Benutzern und dem System oder seinen Teilen. Eine alternative Ansicht zum Aktivitätsdiagramm.|[Darstellen der Interaktionen zwischen Benutzern und dem System](#Sequences)|
|Zusätzliche Dokumente oder Arbeitselemente|Kriterien für die Leistung, Sicherheit, Nutzbarkeit und Zuverlässigkeit|[Beschreiben von Servicequalitätsanforderungen](#QoSRequirements)|
|Zusätzliche Dokumente oder Arbeitselemente|Einschränkungen und Regeln, die nicht spezifisch für einen bestimmten Anwendungsfall sind|[Anzeigen von Geschäftsregeln](#BusinessRules)|

 Beachten Sie, dass die meisten Diagrammtypen für andere Zwecke verwendet werden können. Eine Übersicht über die Diagrammtypen finden [Sie unter Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md). Grundlegende Informationen zum Zeichnen von Diagrammen finden Sie unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md).

## <a name="describing-how-your-system-is-used"></a><a name="UseCases"></a> Beschreiben, wie das System verwendet wird
 Erstellen Sie Anwendungsfalldiagramme, um zu beschreiben, wer das System verwendet und wofür es verwendet wird. Ein Anwendungsfall stellt ein Ziel von Benutzern des Systems dar und das Verfahren, das sie ausführen, um das Ziel zu erreichen.

 Ein Onlinesystem für den Verkauf von Mahlzeiten beispielsweise muss es Kunden ermöglichen, Gerichte aus einer Speisekarte auszuwählen, und die liefernden Restaurants müssen die Speisekarte aktualisieren können. Sie können dies in einem Anwendungsfalldiagramm zusammenfassen:

 ![Anwendungsfälle für Kunden und Restaurant](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")

 Sie können auch anzeigen, wie ein Anwendungsfall aus kleineren Fällen zusammengesetzt ist. Beispielsweise ist das Bestellen einer Mahlzeit Teil des Kaufs einer Mahlzeit, der auch Zahlung und Lieferung umfasst:

 ![System nimmt an Zahlung teil, aber nicht an Übermittlung.](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")

 Sie können auch zeigen, welche Anwendungsfälle im Systems enthalten sind, das Sie entwickeln. Beispielsweise ist das System in der Abbildung nicht am Anwendungsfall zum Liefern der Mahlzeit beteiligt. Dadurch kann der Kontext für die Entwicklungsarbeit festgelegt werden. (In einem Anwendungsfalldiagramm können Subsystem-Containern verwendet werden, um das System oder seine Komponenten darzustellen.)

 Darüber hinaus kann Ihr Team besprechen, was in nachfolgende Versionen einbezogen werden soll. Sie könnten beispielsweise besprechen, ob in der ersten Version des Systems die Bezahlung der Mahlzeit direkt zwischen dem Restaurant und dem Kunden anstatt über das System geregelt werden soll. In diesem Fall könnten Sie die Bezahlung für die Mahlzeit für die erste Version außerhalb des Rechteck des Dinner Now-Systems platzieren.

 Ein Anwendungsfalldiagramm bietet nur eine Zusammenfassung der Anwendungsfälle. Um ausführlichere Beschreibungen bereitzustellen, können Sie die Anwendungsfälle im Diagramm mit separaten Dokumenten und anderen Diagrammen verknüpfen. Weitere Informationen hierzu finden Sie unter [Verknüpfen eines Anwendungsfalls mit Dokumenten und Diagrammen](../modeling/link-a-use-case-to-documents-and-diagrams.md).

 Das Zeichnen eines Anwendungsfalldiagramms unterstützt Ihr Team bei Folgendem:

- Konzentration darauf, was der Benutzer mit dem System tun möchte, ohne von Details der Implementierung abgelenkt zu werden

- Besprechen des Umfangs des Systems oder bestimmter Versionen des Systems

  Die folgenden Themen stellen weitere Informationen bereit:

|Thema|Lesen|
|--------------------|----------|
|Ausführlichere Informationen zum Erstellen von Anwendungsfällen|[UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)|
|Elemente in einem Anwendungsfalldiagramm|[UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)|
|Entwickeln von Code aus Anwendungsfällen|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|

## <a name="defining-terms-used-to-describe-requirements"></a><a name="RequirementsClasses"></a> Definieren von Begriffen zum Beschreiben von Anforderungen
 Sie können anhand von UML-Klassendiagrammen ein einheitliches Vokabular der Business-Konzepte entwickeln, das für folgende Zwecke verwendet werden kann:

- Von den Benutzern selbst, zur Besprechung des Geschäfts, in dem das System eingesetzt wird

- Zum Beschreiben der Anforderungen der Benutzer, z.B. bei der Beschreibung von Anwendungsfällen, Geschäftsregeln und User Storys

- Die Typen von Informationen, die an der API des Systems oder über die Benutzeroberfläche ausgetauscht werden

- Beschreibungen von System-oder Akzeptanztests

  Wenn sie für diesen Zweck verwendet werden, wird der Inhalt eines UML-Klassendiagramms als konzeptionelles Klassendiagramm bezeichnet. (Es wird auch als *Domänenmodell* oder *Analyseklassenmodell*bezeichnet.)

  In einem konzeptionellen Klassendiagramm zeigen Sie nur die Klassen an, die in der Beschreibung der Anforderungen erforderlich sind, ohne Details des internen Entwurfs des Systems. Das Diagramm zeigt keine Details des internen Entwurfs des Systems. Sie zeigen in der Regel keine Vorgänge oder Schnittstellen in konzeptionellen Klassen an.

  Sie könnten beispielsweise die folgenden konzeptionellen Klassen für das Dinner Now-System zeichnen:

  ![Klassenmenü, Bestellung, Menüelement, Order-Element.](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")

  Ein konzeptionelles Klassendiagramm bietet das Vokabular, das Sie im gesamten Anforderungsmodell verwenden. Beispielsweise könnten Sie in der detaillierten Beschreibung des Anwendungsfalls zum Bestellen einer Mahlzeit Folgendes schreiben:

  Der Kunde wählt eine *Speisekarte* , aus der er eine *Bestellung*vornehmen möchte, und erstellt dann *Bestellpositionen* in der *Bestellung* , indem er *Gerichte* aus der *Speisekarte*auswählt.

  Beachten Sie, dass die in dieser Beschreibung verwendeten Begriffe den Namen der Klassen im Modell entsprechen. Das Diagramm entfernt Mehrdeutigkeiten aus Beziehungen zwischen solchen Klassen. Beispielsweise zeigt es deutlich, dass jede Bestellung mit nur einer Speisekarte verknüpft ist.

  Missverständnisse im Hinblick auf die Benutzeranforderungen sind häufig auf Missverständnisse hinsichtlich der genauen Bedeutungen von Worten zurückzuführen. Beispielsweise werden die meisten Restaurants die Begriffe Speisekarte und Bestellung auf gleiche Weise verstehen, jedoch ist der Unterschied zwischen einer Position auf einer Bestellung und einem Gericht auf einer Speisekarte weniger klar. Wenn die Anforderungen mit den Projektbeteiligten besprochen werden, müssen solche Unterschiede geklärt werden. Das Klassendiagramm ist ein nützliches Tool für das Klären von Begriffen und ihren Beziehungen.

  Das konzeptionelle Klassenmodell kann das Grundvokabular bilden, mit dem die Geschäftslogik Ihres Systems beschrieben werden kann. Doch die Klassen in der Software sind in der Regel viel komplexer als das konzeptionelle Modell, da bei der Implementierung Aspekte wie die Leistung, Verteilung, Flexibilität und andere Faktoren berücksichtigt werden müssen. Häufig umfasst ein System mehrere unterschiedliche Implementierungen einer konzeptionellen Klasse.

  Beispielsweise können Bestellungen in XML, SQL, HTML und C# in unterschiedlichen Teilen des Systems und an unterschiedlichen Schnittstellen zwischen den Teilen dargestellt werden. Die Zuordnung zwischen einer Bestellung und einer Speisekarte könnte auf viele verschiedene Arten dargestellt werden, etwa als Verweise in C#-Code, Beziehungen in einer Datenbank oder übergreifende IDs in XML. Doch trotz dieser Abweichungen bietet das konzeptionelle Model wichtige Informationen, die für jeden Teil der Software gelten. Das Klassendiagramm im Beispiel gibt an, dass in jeder Implementierung nur eine Speisekarte mit jeder Bestellung verknüpft ist.

  Durch das Zeichnen eines Klassendiagramms wird Ihr Team bei Folgendem unterstützt:

- Definieren und Standardisieren der grundlegenden Begriffe, die in Besprechungen der Benutzeranforderungen verwendet werden

- Klären der Beziehungen zwischen diesen Begriffen

  Die folgenden Themen stellen weitere Informationen bereit:

|Thema|Lesen|
|--------------------|----------|
|Genauere Informationen zum Finden von Anforderungsklassen|[UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|
|Elemente in einem konzeptionellen Klassendiagramm|[UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)|
|Entwickeln von Code aus konzeptionellen Klassen|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|

 In einem konzeptionellen Klassendiagramm ist es in der Regel nicht hilfreich, Pfeile auf den Zuordnungen zu platzieren, um die Navigationsfreundlichkeit darzustellen. Das liegt daran, dass das Diagramm keine Implementierung darstellt. Die Zuordnungen stellen Beziehungen zwischen realen Objekten dar.

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Anzeige von Geschäftsregeln
 Eine Geschäftsregel ist eine Anforderung, die mit keinem speziellen Anwendungsfall verknüpft ist und im ganzen System zu beachten ist.

 Viele Geschäftsregeln sind Einschränkungen der Beziehungen zwischen den konzeptionellen Klassen. Sie können diese *statischen Geschäftsregeln* als Kommentare schreiben, die mit den entsprechenden Klassen in einem konzeptionellen Klassendiagramm verknüpft sind. Beispiel:

 ![Regel in an Order-Klasse angefügtem Kommentar.](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")

 *Dynamische Geschäftsregeln* schränken die zulässigen Sequenzen von Ereignissen ein. Beispielsweise verwenden Sie ein Sequenz- oder Aktivitätsdiagramm, um zu zeigen, dass sich ein Benutzer anmelden muss, bevor er andere Vorgänge im System durchführen kann.

 Allerdings können viele dynamische Regeln effektiver und allgemeiner durch Ersetzung durch statische Regeln angegeben werden. Beispielsweise können Sie einer Klasse im konzeptionellen Klassenmodell ein boolesches Attribut „Angemeldet“ hinzufügen. Sie würden „Angemeldet“ als Nachbedingung des Anwendungsfalls für das Anmelden hinzufügen und als Vorbedingung für die meisten der anderen Anwendungsfälle. Mit diesem Ansatz können Sie vermeiden, alle möglichen Kombinationen von Ereignissequenzen definieren zu müssen. Zudem ist dieses Vorgehen flexibler, wenn Sie dem Model neue Anwendungsfälle hinzufügen müssen.

 Beachten Sie, dass hier zu entscheiden ist, wie Sie die Anforderungen definieren, und dass dies unabhängig von der Implementierung der Anforderungen im Programmcode ist.

 Die folgenden Themen stellen weitere Informationen bereit:

|Thema|Lesen|
|--------------------|----------|
|Genauere Informationen zum Finden und Aufzeichnen statischer Geschäftsregeln|[UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|
|Elemente in einem konzeptionellen Klassendiagramm|[UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)|
|Entwickeln von Code, der Geschäftsregeln entspricht|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Beschreiben von Quality of Service Anforderungen
 Es gibt mehrere Kategorien von Servicequalitätsanforderungen. Dazu gehören:

- Leistung

- Sicherheit

- Benutzerfreundlichkeit

- Zuverlässigkeit

- Stabilität

  Sie können einige dieser Anforderungen in die Beschreibungen bestimmter Anwendungsfälle einschließen. Andere Anforderungen sind nicht spezifisch für Anwendungsfälle und werden am effektivsten in ein separates Dokument geschrieben. Es ist nützlich, nach Möglichkeit das von den Anforderungsmodellen definierte Vokabular einzuhalten. Beachten Sie im nächsten Beispiel, dass die in der Anforderung verwendeten Hauptwörter den Titeln von Akteuren, Anwendungsfällen und Klassen in den vorangehenden Abbildungen entsprechen:

  Wenn ein Restaurant ein Gericht löscht, während ein Kunde eine Mahlzeit bestellt, werden Bestellpositionen, die sich auf dieses Gericht beziehen, rot angezeigt.

  Die folgenden Themen stellen weitere Informationen bereit:

|Thema|Lesen|
|--------------------|----------|
|Anfügen zusätzlicher Dokumente an Anwendungsfälle|[Verknüpfen eines Anwendungsfalls mit Dokumenten und Diagrammen](../modeling/link-a-use-case-to-documents-and-diagrams.md)|
|Entwickeln von Code, der Servicequalitätsanforderungen entspricht|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|

## <a name="showing-work-flow-between-users-and-your-system"></a><a name="Workflow"></a> Der Workflow zwischen Benutzern und Ihrem System wird angezeigt.
 Sie können ein Aktivitätsdiagramm verwenden, um den Arbeitsablauf zwischen verschiedenen Anwendungsfällen zu zeigen. Es ist häufig nützlich, ein Anforderungsmodell durch Zeichnen eines Aktivitätsdiagramms zu beginnen, das die vom Benutzer ausgeführten Hauptaufgaben zeigt, sowohl im System als auch außerhalb.

 Beispiel:

 ![Aktivität mit drei Aktionen und einer Schleife.](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")

 Sie können Anwendungsfalldiagramme und Aktivitätsdiagramme zeichnen, um unterschiedliche Ansichten derselben Informationen zu zeigen.  Das Anwendungsfalldiagramm ist effektiver, wenn es darum geht, die Schachtelung der kleineren Aktionen innerhalb der größeren Aktivität zu zeigen, jedoch zeigt es nicht den Arbeitsablauf. Beispiel:

 ![Anwendungsfälle für vorherige Aktionen](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")

 Beachten Sie, dass Sie Aktivitätsdiagramme auch zum Abbilden von Algorithmen in der Software einsetzen können, doch wenn Sie die Diagramme für den Geschäftsprozess nutzen, konzentrieren Sie sich auf die Aktionen, die außerhalb des Systems sichtbar sind.

 Die folgenden Themen stellen weitere Informationen bereit:

|Thema|Lesen|
|--------------------|----------|
|Weitere Informationen zum Definieren von Geschäftsarbeitsabläufen|[UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)|
|Elemente in einem Aktivitätsdiagramm|[UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)|
|Entwickeln von Code aus Aktivitätsdiagrammen|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|

## <a name="showing-interactions-between-users-and-your-system"></a><a name="Sequences"></a> Darstellung von Interaktionen zwischen Benutzern und Ihrem System
 Sie können ein Sequenzdiagramm verwenden, um den Austausch von Meldungen zwischen Ihrem System und externen Akteuren oder zwischen Teilen des Systems darzustellen. Dadurch ergibt sich eine Ansicht der Schritte in einem Anwendungsfall, die sehr deutlich die Sequenz der Interaktionen zeigt. Sequenzdiagramme sind besonders nützlich, wenn es mehrere interagierende Parteien in einem Anwendungsfall gibt und wenn Ihr System eine API aufweist.

 Beispiel:

 ![Sequenzdiagramm mit System und Akteuren.](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")

 Ein Vorteil von Sequenzdiagrammen besteht darin, dass Sie einfach sehen können, welche Meldungen bei dem System eingehen, das Sie konstruieren. Um das System zu entwerfen, können Sie die einfache Systemlebenslinie durch eine separate Lebenslinie für jede Komponente ersetzen und dann die Interaktionen zwischen ihnen in Reaktion auf die einzelnen eingehenden Meldungen zeigen.

 Die folgenden Themen stellen weitere Informationen bereit:

|Thema|Lesen|
|--------------------|----------|
|Weitere Informationen zum Definieren von Interaktionen|[UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)|
|Elemente in einem Sequenzdiagramm|[UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)|
|Entwickeln von Code aus Sequenzdiagrammen|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|

## <a name="using-a-model-to-reduce-inconsistencies"></a>Verwenden eines Modells zum Reduzieren von Inkonsistenzen
 Die Erstellung eines Modells führt in der Regel zu einer deutlichen Verringerung von Inkonsistenzen und Mehrdeutigkeiten hinsichtlich der Benutzeranforderungen. Verschiedene Projektbeteiligte haben häufig ein unterschiedliches Verständnis von der Geschäftswelt, in der das System eingesetzt wird. Daher besteht Ihre erste Aufgabe darin, diese Unterschiede zwischen Ihren Kunden auszugleichen.

 Sie werden merken, dass viele Fragen zur Geschäftsdomäne auf natürliche Weise aufkommen, während Sie ein Modell erstellen. Indem Sie diese Fragen den Benutzern stellen, reduzieren Sie die Notwendigkeit von Änderungen in späteren Projektphasen. Nachfolgend finden Sie einige spezifische Fragen, die Sie sich zunächst selbst und anschließend den Projektbeteiligten stellen können, wenn die Antwort nicht klar ist:

- Fragen Sie für jede Klasse im Anforderungsmodell: „Welcher Anwendungsfall erstellt Instanzen dieser Klasse?“. Bei einem Onlinebestelldienst für Mahlzeiten beispielsweise könnten Sie fragen: „Welcher Anwendungsfall erstellt Instanzen der Klasse der Restaurantspeisekarten?“. Dies würde zu einer Diskussion darüber führen, wie ein neues Restaurants für den Dienst registriert wird und seine Speisekarte beisteuert. Sie können ähnliche Fragen darüber stellen, was Attribute und Zuordnungen erstellt oder ändert.

- Versuchen Sie für jeden Anwendungsfall im Anforderungsmodell, das Endergebnis oder die Nachbedingung der einzelnen Anwendungsfälle in Worten zu beschreiben, die Sie in den Klassendiagrammen finden. Es ist häufig nützlich, die Wirkung eines Anwendungsfalls zu zeigen, indem Sie Instanzen der Klassen vor und nach einem Auftreten des Anwendungsfalls skizzieren. Wenn die Nachbedingung des Anwendungsfalls beispielsweise „Ein Gericht wird der Kundenbestellung hinzugefügt“ lautet, skizzieren Sie Instanzen der Klassen „Bestellung“ und „Gericht“. Zeigen Sie die Wirkungen des Anwendungsfalls, etwa eine neue Verknüpfung oder ein neues Objekt, in einer anderen Farbe oder in einer neuen Zeichnung an. Dies führt häufig zu Diskussionen darüber, welche Informationen im Modell notwendig sind. Obwohl Anforderungsklassen nicht direkt mit der Implementierung zu tun haben, beschreiben sie die Informationen, die das System zum Speichern und Übertragen benötigt.

- Fragen Sie nach den Einschränkungen bei Attributen und Zuordnungen, insbesondere nach Einschränkungen, die mehr als ein Attribut oder eine Zuordnung betreffen.

- Fragen Sie nach gültigen und ungültigen Sequenzen von Anwendungsfällen, und zeichnen Sie Sequenz- oder Aktivitätsdiagramme, um sie darzustellen.

  Durch Untersuchen der Beziehungen zwischen den Ansichten, die von verschiedenen Diagrammen bereitstellt werden, können Sie schnell die wichtigsten Konzepte verstehen, mit denen die Benutzer arbeiten, und ihnen helfen, zu verstehen, was sie aus dem System benötigen. Sie können auch besser verstehen, bei welchen Anforderungen sich die Projektbeteiligten am unsichersten sind. Sie können planen, diese Features zumindest in vereinfachter Form in einem frühen Stadium des Projekts zu entwickeln, damit Benutzer mit ihnen experimentieren können.

## <a name="see-also"></a>Weitere Informationen
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [entwickeln von Tests aus einem Modell verwenden von](../modeling/develop-tests-from-a-model.md) [Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md) [Modell des Architektur Videos ihrer App](../modeling/model-your-app-s-architecture.md) [: Modellieren der Geschäftsdomäne](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)
