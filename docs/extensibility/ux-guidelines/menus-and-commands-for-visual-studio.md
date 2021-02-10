---
title: Menüs und Befehle für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Befehls leisten bei der Erstellung neuer Features für Visual Studio Flexibilität in der Benutzeroberfläche ermöglichen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d28242b70c0c9808cc7eb066341cd2973d2372a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971582"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menüs und Befehle für Visual Studio
## <a name="command-usage"></a>Befehls Verwendung

### <a name="overview"></a>Übersicht
 Anders als bei Microsoft Office, bei der es sich um eine Sammlung handelt, die viele separate Produkte umfasst, enthält Visual Studio viele Produkte, die jeweils ihre Befehls Sätze an die globale Visual Studio-IDE einbringen. Die IDE verwaltet die Komplexität von Tausenden von Befehlen, indem die Funktionen gefiltert werden, die für den Benutzer basierend auf dem Kontext verfügbar sind.

 Wenn sich der Kontext eines Benutzers ändert, z. b. beim Wechseln von einem Entwurfs Fenster zu einem Code Bearbeitungsfenster, wird die Funktionalität nicht mehr mit dem neuen Kontext angezeigt. Gleichzeitig werden neue Funktionen zusammen mit verwandten dynamischen Informationen, z. b. Eigenschaften und Toolbox Optionen, angezeigt. Der Benutzer sollte das Austauschen des verfügbaren Befehlssatzes nicht bemerken. Wenn der Benutzer durch Befehle, die angezeigt oder verschwindet, abgelenkt oder verwirrt wird, muss der Benutzeroberflächen Entwurf angepasst werden. Der aktuelle Kontext des Benutzers wird immer auf eine oder mehrere Arten angegeben, z. b. in der IDE-Titelleiste, im Eigenschaftenfenster oder im Dialogfeld Eigenschaften Seiten.

 Befehls leisten ermöglichen Flexibilität in der Benutzeroberfläche. Die einzigen Befehlsstrukturen in der Visual Studio-Umgebung sind das Hauptmenü und die Haupt Befehlsleiste, die beide angepasst und sogar ausgeblendet werden können. Andere Befehls leisten werden basierend auf dem Zustand der Anwendung angezeigt und verschwinden. Tool Fenster und Dokument-Editoren können auch eingebettete Symbolleisten innerhalb ihrer Fensterkanten enthalten.

#### <a name="basic-guidelines"></a>Grundlegende Richtlinien

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Verwenden Sie nach Möglichkeit vorhandene freigegebene Befehle, Befehls Gruppen und Menüs.
 Da Befehle in der Regel auf der Grundlage des Kontexts angezeigt werden, stellt die Verwendung vorhandener frei gegebener Menüs und Befehls Gruppen sicher, dass die Befehlsstruktur zwischen den Änderungen im Kontext relativ stabil bleibt. Durch die Wiederverwendung frei gegebener Befehle und die Platzierung neuer Befehle in der Nähe der zugehörigen freigegebenen Befehle wird auch die IDE-Komplexität reduziert, und die Benutzerfreundlichkeit wird verbessert Wenn ein neuer Befehl definiert werden muss, versuchen Sie, ihn in einer vorhandenen freigegebenen Befehlsgruppe zu platzieren. Wenn eine neue Gruppe definiert werden muss, platzieren Sie Sie in einem vorhandenen freigegebenen Menü in der Nähe einer zugehörigen Befehlsgruppe, bevor Sie ein neues Menü der obersten Ebene erstellen.

##### <a name="do-not-create-icons-for-every-command"></a>Erstellen Sie für jeden Befehl keine Symbole.
 Vor dem Erstellen eines Befehls Symbols sollten Sie sorgfältig überlegen. Symbole sollten nur für Befehle erstellt werden, für die Folgendes gilt:

- wird auf einer Standard Symbolleiste angezeigt.

- werden von Benutzern wahrscheinlich über das Dialogfeld " **anpassen...** " einer Symbolleiste hinzugefügt.

- ein Symbol, das derselben Aktion in einem anderen Microsoft-Produkt zugeordnet ist.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Hinzufügen von Tastenkombinationen begrenzen
 Die große Mehrheit der Benutzer nutzt einen kleinen Bruchteil aller verfügbaren Tastenkombinationen. Binden Sie Ihre Funktion im Zweifelsfall nicht an eine Tastenkombination. Arbeiten Sie mit Ihrem benutzerfreundlichen Team, bevor Sie neue Verknüpfungen hinzufügen.

##### <a name="give-commands-a-default-menu-placement"></a>Übergeben von Befehlen eine Standardmenü Platzierung
 Beachten Sie, dass Ihre Befehle von anderen Personen angepasst und entsprechend entworfen werden. Es gibt keinen ausgeblendeten Befehl. Alle Visual Studio-Befehle werden im Dialogfeld Extras **> anpassen** , Befehlsfenster, Auto vervollständigen, **Tools > Optionen > Tastatur** Dialogfeld und Entwicklungs Tools-Umgebung (DTE) angezeigt. Stellen Sie sicher, dass Sie Ihren Befehlen einen Namen und eine QuickInfo in der CTC-Datei geben, damit Benutzer Sie leicht finden können.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Duplizieren Sie keine freigegebenen Befehle auf einer eingebetteten Symbolleiste.
 Es ist hilfreich, Befehle in unmittelbarer Nähe zum Bereich des Benutzer Fokus zu platzieren. Eine Möglichkeit hierfür ist das Erstellen einer eingebetteten Symbolleiste am oberen Rand des Tool Fensters oder des Dokument-Editors. Die auf der Symbolleiste platzierten Befehle sollten für den Inhalts Bereich innerhalb des Fensters spezifisch sein. Duplizieren Sie keine freigegebenen Befehle auf diesen Symbolleisten. Platzieren Sie z. b. niemals das Symbol "Speichern" in einer eingebetteten Symbolleiste.

### <a name="content-and-command-visibility"></a>Sichtbarkeit von Inhalten und Befehlen
 In den folgenden Bereichen sind Befehle vorhanden: **Umgebung**, **Hierarchie** und **Dokument**. Informieren Sie sich über jeden Bereich, um Vertrauen in die Befehls Platzierung zu erhalten.

 Befehle im **Umgebungs** Bereich richten den primär Kontext ein und werden von mehreren Kontexten gemeinsam genutzt. Sie ändern die Sichtbarkeit oder Anordnung von Dokumenten und Tool Fenstern. Zu den Befehlen im Umgebungs Bereich zählen **Neues Projekt**, **Verbindung mit Server herstellen**, **Prozess anfügen**, **Ausschneiden**, **Kopieren**, **Einfügen**, **Suchen**, **Optionen**, **Anpassen**, **Neues Fenster** und **Hilfe anzeigen**.

 Befehle im **Hierarchie** Bereich verwalten Hierarchien in Visual Studio, **einschließlich Projekt**, **Team** und **Daten**. Sie beziehen sich auf den unter Kontext eines Projekts, z. b. **Debuggen**, **Erstellen**, **Testen**, **Architektur** oder **analysieren**. Zu den Befehlen im Bereich Hierarchie gehören **Add New Item**, **New Query**, **Project Settings**, **Add New Data Source**, **Launch Performance Wizard** und **New Diagram**.

 Befehle im **Dokument** Bereich agieren auf den Inhalt eines Dokuments, z. b. Code, Design oder eine Arbeitsaufgaben Abfrage (Work Item Query, WIQ). Sie wirken sich auch auf die Ansicht eines Tool Fensters aus oder sind für dieses Tool Fenster anderweitig spezifisch. Dokument Bereichs Befehle wirken sich auch auf die Datei Objekte aus, die selbst Hierarchie spezifisch sind, z. b. **aus Projekt entfernen**. Die Befehle im Dokumentbereich sind **Umgestalten > umbenennen**, **Erstellen einer Kopie des Arbeits Elements**, **erweitern alle**, **alle** reduzieren und **Benutzer erstellen**.

### <a name="command-placement-decisions"></a>Entscheidungen hinsichtlich der Befehls Platzierung
 Wenn Sie sich entschieden haben, einen Befehl zu erstellen, müssen Sie die entsprechende Platzierung bestimmen und angeben, ob eine Tastenkombination erstellt werden soll. Gehen Sie folgendermaßen vor, um festzulegen, wo der Befehl platziert werden soll:

 ![Entscheidungsdiagramm zur Befehlspositionierung](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Entscheidungs Pfad für Befehls Platzierung in Visual Studio**

### <a name="command-placement-in-menus"></a>Befehls Platzierung in Menüs

#### <a name="main-menu-bar"></a>Hauptmenüleiste
 Die Hauptmenüleiste sollte der Standard Speicherort für Befehle von kontextspezifischen Menü Paketen sein, die zur Benutzeroberfläche beitragen. Die Hauptmenüleiste unterscheidet sich von anderen Befehlsstrukturen darin, dass Sie von der Umgebung verwendet wird, um zu steuern, welche Befehle sichtbar sind. Alle anderen Befehls leisten deaktivieren einfach Befehle, die nicht im Kontext sind, und zwar unabhängig davon, ob Sie in einem Menü oder auf einer Symbolleiste abgelegt werden.

 Die Umgebung definiert eine Reihe von Befehlen, die in die Hauptmenüleiste integriert sind und in der gesamten IDE und mehreren Aufgaben Domänen gemeinsam sind. Diese Befehle sind immer sichtbar, unabhängig davon, welche VSPackages in die Umgebung geladen werden. Obwohl VSPackages diese Befehls Reihe erweitern können, liegt der Befehlssatz jedes Produkts und die Platzierung der Befehle in der Verantwortung der einzelnen Teams.

 Die Struktur des Visual Studio-Hauptmenüs kann in die folgenden Menü Kategorien aufgeteilt werden:

##### <a name="core-menus"></a>Core-Menüs

- Datei

- Bearbeiten

- Sicht

- Tools

- Fenster

- Hilfe

##### <a name="project-specific-menus"></a>Projektspezifische Menüs

- Project

- Entwickeln

- Debuggen

##### <a name="context-specific-menus"></a>Kontextspezifische Menüs

- Team

- Daten

- Test

- Aufbau

- Analysieren

##### <a name="document-specific-menus"></a>Dokument spezifische Menüs

- Format

- Tabelle

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Beachten Sie beim Entwerfen von Hauptmenüs die folgenden Regeln:

- Höchstens 25 Elemente der obersten Ebene in einem bestimmten Kontext überschreiten

- Menüs sollten nie die Höhe von 600 Pixel überschreiten.

- Wertet ein Hauptmenü in mehreren Kontexten aus, z. b. in der Ultimate-SKU und im allgemeinen Profil.

- Flyout-Menüs sind zulässig.

- Flyout-Menüs sollten mindestens drei Elemente und höchstens sieben Elemente enthalten.

- Flyout-Menüs sollten nur eine Ebene tief gehen: einige Visual Studio-Menü Elemente haben kaskadierende Untermenüs, aber dieses Muster wird nicht empfohlen.

- Verwenden Sie höchstens sechs Trennzeichen. Gruppierungen sollten der folgenden Abbildung entsprechen:

     ![Richtlinien für die Gruppierung des Hauptmenüs](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Obwohl es nicht erforderlich ist, dass jede Gruppierung in der Abbildung vorhanden ist, ist das Hinzufügen zusätzlicher Gruppierungen eingeschränkt.

- Jede Gruppierung sollte zwischen zwei und sieben Menü Elemente aufweisen.

#### <a name="main-menu-ordering"></a>Hauptmenü-Reihenfolge
 Bevor Sie ein neues Element der obersten Ebene hinzufügen, sollten Sie den Befehl in einem vorhandenen Menü der obersten Ebene platzieren. Wenn Sie ein neues Menü der obersten Ebene hinzufügen, stellen Sie sicher, dass Sie es an der richtigen Stelle platzieren. Entscheiden Sie, ob das Menü für das Projekt, den Kontext oder das Dokument spezifisch ist. Behalten Sie den Namen des Menüs der obersten Ebene bei, und verwenden Sie nur ein Wort.

 Die Hauptmenüs sollten den Rest der Befehle als Lesezeichen markieren. Datei, bearbeiten und Ansicht sollten immer links sein, und Tools, Fenster und Hilfe sollten immer auf der rechten Seite stehen.

#### <a name="context-menus"></a>Kontextmenüs
 Das Platzieren einer zu großen Funktionalität in den Kontextmenüs führt zu einer schwer zu ermittelenden Schnittstelle. Alle wichtigen Funktionen sollten über die Hauptmenüleiste verfügbar sein. Die Platzierung von Befehlen sollte mit vorhandenen Befehlen abgestimmt werden, um doppelte Befehle zu vermeiden. Bei Kontextmenüs definiert die Shell Standardmenü Gruppen, die abhängig davon, ob das Kontextmenü für die Projekt Mappe, einen Projekt Knoten oder ein Projekt Element vorgesehen ist, eingeschlossen werden sollen.

 Beachten Sie beim Entwerfen von Kontextmenüs dieselben Regeln wie für das Hauptmenü, und fügen Sie außerdem Folgendes hinzu:

- Überschreiten 25 Menü Elemente der obersten Ebene.

- Flyout-Menüs sind akzeptabel, dürfen aber nicht mehr als eine Ebene verwenden, die keine kaskadierenden Flyouts verwenden darf.

- Verwenden Sie höchstens sechs Trennzeichen.

### <a name="command-placement-in-toolbars"></a>Befehls Platzierung in Symbolleisten

#### <a name="general-toolbars"></a>Allgemeine Symbolleisten
 Beachten Sie beim Entwerfen und Anordnen von Symbolleisten folgende Standards:

- Verwenden Sie nicht mehr als ein Verb pro Schaltfläche. Eine Schaltfläche = eine Aktion.

- Verwenden Sie Text neben dem Symbol nur, wenn er mit der Bezeichnung verstärkt werden muss.

- Verwenden Sie ein Kombinations Feld exklusiv für Eigenschaften, die in einer Sitzung mehrmals gewechselt werden. Andernfalls können Sie die Eigenschaft an anderer Stelle verfügbar machen.

- Die Breite eines Kombinations Felds sollte gleich der Breite des längsten Elements im Feld + 30% sein. Wenn das längste Element beispielsweise 200 Pixel beträgt, sollte das Kombinations Feld 260 Pixel breit sein.

- Beschränken Sie die Verwendung von Trennzeichen. Die Verwendung eines Trenn Zeichens neben einer Dropdown Liste ist ein Antimuster, da die Form der Dropdown Liste selbst als visuelles Trennzeichen fungiert.

- Symbolgruppen sollten zwischen drei und sechs Symbolen enthalten.

- Wenn Qualifizierer mehrere nützliche Befehle ergeben, verwenden Sie eine unterteilte Schaltfläche, in der die letzte Einstellung gespeichert wird:

     ![Unterteilte Schaltflächen in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Beispiel für eine Trenn Schaltfläche. Die sechs Befehle auf der linken Seite können stattdessen in eine einzelne Schaltfläche eingefügt werden.**

#### <a name="product-specific-toolbars"></a>Produktspezifische Symbolleisten
 Jedes Produkt kann eine Standard Symbolleiste bereitstellen, die häufig verwendete und wichtige Befehle enthält, und die Standard Symbolleiste jedes Produkts sollte angezeigt werden, wenn Visual Studio zum ersten Mal nach der Installation des Produkts gestartet wird.

 Produkte sollten auch freigegebene Befehls Gruppen und Menüs nutzen, die von der IDE bereitgestellt werden. Alle freigegebenen Befehls Gruppen werden in ein frei gegebenes Menü eingefügt, um verwandte Befehle auf sinnvolle Weise für den Benutzer zu organisieren. Es ist wichtig, diese freigegebene Befehlsstruktur zu nutzen, um die Komplexität zu verringern.

#### <a name="global-toolbars"></a>Globale Symbolleisten
 Globale Symbolleisten müssen direkt in eine Zeile passen. Wenn Sie eine neue globale Symbolleiste erstellen, befolgen Sie die Richtlinien für diesen Symbolleisten-Typ.

 **Allgemeine Richtlinien für Symbolleisten:**

- Jede Symbolleiste verfügt über 24 Pixel in allgemeinen Steuerelementen (Greifer, Überlauf).

- Jede Symbolleisten Schaltfläche ist 22 Pixel breit, einschließlich Padding. Durch das Symbol einer unterteilten Schaltfläche werden weitere 11 Pixel Breite hinzugefügt.

- Die Duplizierung von Befehlen über Symbolleisten hinweg ist zulässig.

  **Dokument spezifische Symbolleisten** werden angezeigt, wenn ein bestimmter Dateityp aktiv ist und ausgeblendet wird, wenn ein anderer Dateityp aktiv wird.

- Dokument spezifische Symbolleisten dürfen nicht mehr als 12 Schaltflächen enthalten.

- Die Gesamtbreite der Symbolleiste darf 300 Pixel nicht überschreiten.

- Jeder Dateityp kann entweder eine eingebettete Symbolleiste oder eine Dokument spezifische globale Symbolleiste aufweisen, aber nicht beides.

  **Kontextspezifische Symbolleisten** werden angezeigt, wenn ein bestimmter Kontext festgelegt ist und in der Regel für erweiterte Zeiträume aktiv bleibt.

- Das Schaltflächen Limit für alle kontextspezifischen Symbolleisten ist 18.

- Wenn die meisten Benutzer diese Symbolleisten Befehle nicht konsistent verwenden, wenn der Kontext aktiv ist, ordnen Sie diese Symbolleiste nicht einem Kontext zu.

- Stellen Sie sicher, dass die Symbolleiste beim Beenden des Kontexts verschwindet Keine dieser Symbolleisten sollte beim Start angezeigt werden.

  **Symbolleisten ohne Kontext** werden nie automatisch angezeigt. Diese werden nur angezeigt, wenn Sie vom Benutzer aktiviert werden. Behalten Sie die maximale Breite unter 200 Pixel.

### <a name="general-organization-and-shell-defined-groups"></a>Allgemeine Organisations-und Shell-definierte Gruppen
 Verwenden Sie vorhandene freigegebene Befehle, Befehls Gruppen und Menüs. Wenn ein neuer Befehl definiert werden muss, versuchen Sie, ihn in einer vorhandenen freigegebenen Befehlsgruppe zu platzieren. Wenn eine neue Gruppe definiert werden muss, versuchen Sie, Sie in einem vorhandenen freigegebenen Menü zu platzieren, das sich in der Nähe einer zugehörigen Befehlsgruppe befinden, bevor Sie ein neues Menü der obersten Ebene erstellen. Dadurch wird die Befehls Komplexität reduziert und gleichzeitig eine konsistente Befehls Platzierung in der IDE sichergestellt.

 Das Menü mit den freigegebenen **Formaten** , das in der Regel im Kontext von Dokument Fenstern im Designer angezeigt wird, ist in der folgenden Abbildung dargestellt:

 ![Visual Studio-Menü "Format" mit Beschriftungen](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Menü Gruppen in Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Reduzieren und wieder verwenden von Befehlen
 Befehle werden in der Regel auf der Grundlage des Kontexts angezeigt, um die Anzahl der Befehle zu verringern, die dem Benutzer zu einem beliebigen Zeitpunkt angezeigt werden. Sie sollten jedoch auch vorhandene freigegebene Menüs und Befehls Gruppen wieder verwenden, um sicherzustellen, dass die Befehlsstruktur zwischen den Änderungen im Kontext relativ stabil bleibt.

 Durch die Wiederverwendung frei gegebener Befehle und die Platzierung neuer Befehle in der Nähe verwandter frei gegebener Befehle wird die IDE-Komplexität reduziert, und es wird eine benutzerfreundlichere Benutzerfreundlichkeit

## <a name="naming-commands"></a>Benennungs Befehle

### <a name="naming-conventions"></a>Benennungskonventionen
 Eine konsistente Befehls Benennung ist wichtig, damit Benutzer Befehle suchen und ausführen können, indem Sie entweder über die Befehlszeile oder über die Bindung an eine Tastenkombination eine Tastenkombination verwenden. Befehlsnamen unterstützen den Benutzer außerdem dabei, den Zweck eines Befehls zu verstehen, wenn er auf einer Symbolleiste oder in einem kaskadierenden oder Kontextmenü angezeigt wird.

#### <a name="when-naming-commands"></a>Beim Benennen von Befehlen:

- Erstellen Sie Text, sodass er problemlos lokalisiert werden kann. Weitere Informationen zum Lokalisieren von Text finden Sie unter [bewährte Methoden](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)für die Lokalisierung.

- Seien Sie präzise. Befehle sollten nicht mehr als drei Wörter verwenden.

- Groß-/Kleinschreibung für Groß-/Kleinschreibung verwenden: der erste Buchstabe jedes Worts sollte groß geschrieben werden. Weitere Informationen zur Textformatierung in Visual Studio finden Sie unter [Textart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Berücksichtigen Sie, wo der Befehl platziert wird. Handelt es sich um ein Menü der obersten Ebene oder um ein Flyout? Wenn Sie z. b. Ausrichtungs Befehle in einem Flyout gruppieren, sollte der Befehl auf oberster Ebene "ausrichten" lauten, und die Flyout-Befehle sollten "Left", "Right", "Center", "rechtfertigen" usw. lauten. Es wäre redundant, die Flyout-Befehle "linksbündig" oder "Rechtsbündig ausrichten" zu benennen.

     ![Visual Studio-Menü "Format"](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Verwenden von Symbolen mit Befehlen
 Die Verwendung von Symbol Kopplung mit Befehlen ist sparsam. Obwohl das Zuordnen eines eindeutigen Bilds zu einem Befehl die Fähigkeit des Benutzers, diesen Befehl zu identifizieren, beschleunigt, treten visuelle Übersichtlichkeit und Ineffizienz bei der Bild überverwendung auf. Die folgenden Regeln helfen bei der Entscheidung, ob ein Befehls Symbol erstellt werden soll.

#### <a name="use-an-icon-with-a-command-only-if"></a>Verwenden Sie ein Symbol nur mit einem Befehl, wenn Folgendes verwendet wird:

- Dem gleichen Befehl ist ein Symbol in einem anderen prominenten Microsoft-Produkt zugeordnet, z. b. einer der Microsoft Office Anwendungen.

- Der Befehl wird in einer Standard Symbolleiste abgelegt.

- Der Befehl ist ein Spezial Befehl, den Benutzer wahrscheinlich mithilfe des Dialog Felds **"anpassen..."** zu einer Symbolleiste hinzufügen.

## <a name="access-and-shortcut-keys"></a>Zugriffs-und Tastenkombinationen

### <a name="overview"></a>Übersicht
 Es gibt zwei Arten von Tastaturtasten Zuweisungen:

- **Zugriffsschlüssel** (auch als Accelerators bezeichnet) ermöglichen den Tastatur Zugriff über die Menüs für die Befehls Ansicht und jede Bezeichnung in der Benutzeroberfläche des Dialog Felds. Zugriffsschlüssel dienen hauptsächlich zu Barrierefreiheits Zwecken, werden allen Menüs und den meisten Dialogfeld-Steuerelementen zugewiesen, sind nicht für die Speicherung vorgesehen, wirken sich nur auf das aktuelle Fenster aus und sind lokalisiert.

- Tasten **Kombinationen** verwenden hauptsächlich Steuerungs-(STRG) und Funktionstasten Sequenzen (FN). Sie sind für fortgeschrittene Benutzer und höhere Produktivität konzipiert. Sie werden nur den am häufigsten verwendeten Befehlen zugewiesen und ermöglichen den schnellen Zugriff, während das Hauptmenü umgangen wird. Tastenkombinationen müssen gespeichert werden, und aus diesem Grund muss das Profil Schema konsistent zugewiesen werden. Tastenkombinationen können von Profil zu Profil abweichen. Benutzer können Tastenkombinationen mithilfe von **Tools > Optionen > Tastatur** anpassen.

### <a name="assigning-access-keys"></a>Zuweisen von Zugriffs Schlüsseln
 Zugriffsschlüssel bestehen aus alt Plus alphanumerischen Schlüsseln. Weisen Sie jedem Menü Element ohne Ausnahme einen Zugriffsschlüssel zu. Befolgen Sie Windows und allgemeine Konventionen zum Zuweisen von Zugriffs Schlüsseln. Beispielsweise sollte der Zugriffsschlüssel für **File > New** immer **alt, F, N** sein.

 Verwenden Sie keine Buchstaben mit nur einer Pixel Breite, wie z. b. "i" (in groß-oder Kleinbuchstaben) oder den Kleinbuchstaben "l", und vermeiden Sie die Verwendung von Zeichen mit untergeordneten Zeichen (g, j, p, q und y), da diese schwierig zu unterscheiden sind.

 Vermeiden Sie, wenn möglich, doppelte Schlüssel zu verwenden. In Fällen, in denen die Duplizierung unvermeidlich ist, verarbeitet das Menüsystem Konflikte, indem alle Befehle durchlaufen werden, die den Schlüssel verwenden. Beispielsweise würde für einen hypothetischen "Number"-Befehl im Menü "file", der den Zugriffsschlüssel "N" dupliziert, **alt, f, n** eine neue Datei erstellen, und **alt, f, n, n** führt den Befehl "Number" aus.

### <a name="assigning-shortcut-keys"></a>Zuweisen von Tastenkombinationen
 Vermeiden Sie das Zuweisen neuer Tastenkombinationen, da diese für jeden Befehl nicht erforderlich sind, und Steuern Sie das System (und den Benutzer Arbeitsspeicher), wenn dies überlastet ist. Daten aus dem Programm zur Verbesserung der Benutzerfreundlichkeit (CEIP) zeigen an, dass Visual Studio-Benutzer nur eine kleine Teilmenge der integrierten Tastenkombinationen verwenden.

 Beachten Sie beim Definieren von Verknüpfungen die folgenden Regeln:

- **Verwenden Sie die Tastenkombinationen Control (STRG) und Function (FN).**

- **Häufig verwendete Verknüpfungen beibehalten.** Behalten Sie die beliebtesten Tastenkombinationen bei.

- **Vereinfachen Sie die Verknüpfung von Editor-Verknüpfungen.** Binden Sie einfache Verknüpfungen an Befehle, die Entwickler beim Schreiben von Code am meisten benötigen. Beispielsweise muss **Edit. invokesmarttag** über eine kurze Tastenkombination wie STRG +/und nicht ALT + UMSCHALT + F10 verfügen.

- **Bemühen Sie sich um konsistente Tastenkombinationen.**

- **Verwenden Sie die Windows-Richtlinien, um zu bestimmen, welche Modifizierertasten Sie** Verwenden Sie STRG-Tastenkombinationen für Befehle mit umfangreichen Effekten, z. b. Befehle, die für ein gesamtes Dokument gelten. Verwenden Sie UMSCHALT Tastenkombinationen für Befehle, mit denen die Aktionen der Standard-Tastenkombination erweitert oder ergänzt werden. Verwenden Sie die Tastenkombination STRG + ALT nicht.

- **Entfernen Sie überflüssige Verknüpfungen.** Wenn Sie über eine Legacy Funktion verfügen, sollten Sie die Verknüpfungen, die mit extremer Häufigkeit verwendet werden (weniger als zehnmal aus den CEIP-Daten), oder eine moderate infrequenz (weniger als 100-Mal aus den CEIP-Daten) entfernen, wenn eine Zugriffstaste einen schnellen Zugriff auf denselben Befehl ermöglicht. Beispiel: alt, H, C öffnet Hilfe/Inhalt.

  Es gibt keine einfache Möglichkeit, die Verknüpfungs Verfügbarkeit zu überprüfen. Wenn Sie eine Verknüpfung hinzufügen möchten, führen Sie die folgenden Schritte aus:

1. Überprüfen Sie die Liste der [Visual Studio 2013](http://visualstudioshortcuts.com/2013/) Verknüpfungen, um zu bestimmen, ob ähnliche Befehle vorhanden sind, mit denen Sie Ihre Gruppierung

2. Wechseln Sie zu Extras **> Optionen > Umgebung > Tastatur** , und testen Sie die Verknüpfung. Überprüfen Sie jedes Tastatur Zuordnungs Schema, das unter "das folgende zusätzliche Tastatur Zuordnungs Schema anwenden" aufgeführt ist. Überprüfen Sie die Profile General, c#, VB und C++, da diese eindeutige Verknüpfungen gemeinsam verwenden. Die Verknüpfung ist verfügbar, wenn Sie an keinem dieser Orte zugeordnet ist.
