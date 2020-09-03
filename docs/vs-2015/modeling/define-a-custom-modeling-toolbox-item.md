---
title: Definieren eines benutzerdefinierten Modellierungs Toolbox Elements | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a038150519ea7a40a52fb1be16ed93045c09eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851523"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Für die einfache Erstellung eines Elements oder einer Gruppe von Elementen gemäß eines Musters, das Sie häufig verwenden, können Sie der Toolbox mit Modellierungsdiagrammen in Visual Studio neue Tools hinzufügen. Sie können diese Toolboxelemente an andere Visual Studio-Benutzer verteilen.

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Ein benutzerdefiniertes Tool erstellt ein oder mehrere neue Elemente in einem Diagramm. Sie können z. B. ein benutzerdefiniertes Tool zum Erstellen von Elementen, wie beispielsweise die folgenden, erstellen:

- Ein Paket, das mit dem .NET-Profil verknüpft ist, und eine Klasse mit dem .NET-Stereotyp.

- Ein Paar von Klassen, das durch eine Zuordnung verknüpft ist, um das Observer-Muster darzustellen.

> [!NOTE]
> Sie können diese Methode verwenden, um Elementtools zu erstellen. Das heißt, Sie können Tools erstellen, die Sie aus der Toolbox in ein Diagramm ziehen. Sie können keine Connector-Tools erstellen.

## <a name="defining-a-custom-modeling-tool"></a><a name="DefineTool"></a> Definieren eines benutzerdefinierten Modellierungstools

#### <a name="to-define-a-custom-modeling-tool"></a>So definieren Sie ein benutzerdefiniertes Modellierungstool

1. Erstellen Sie ein UML-Diagramm, das ein Element oder eine Gruppe von Elementen enthält.

    - Diese Elemente können Beziehungen untereinander haben und untergeordnete Elemente wie Ports, Attribute, Vorgänge oder Pins aufweisen.

2. Speichern Sie das Diagramm mit dem Namen, den das neue Tool erhalten soll. Verwenden Sie im Menü **Datei** die Option **speichern... Als**.

3. Kopieren Sie mithilfe von Windows-Explorer die zwei Diagrammdateien in den folgenden Ordner oder einen beliebigen Unterordner:

     *Yourdocuments* **\Visual studio\architecture tools\custom Toolbox Items**

    - Erstellen Sie diesen Ordner, wenn er nicht bereits vorhanden ist. Möglicherweise müssen Sie sowohl **Architektur Tools** als auch **benutzerdefinierte Toolbox Elemente**erstellen.

    - Kopieren Sie beide Diagramm Dateien, eine mit einem Namen, der endet. **Diagramm**"und das andere mit einem Namen, der endet... **Diagram. Layout**"

    - Sie können beliebig viele benutzerdefinierte Tools erstellen. Verwenden Sie ein Diagramm für jedes Tool.

4. Optionale Erstellen Sie eine **tbxinfo** -Datei, wie in [Definieren der Eigenschaften von benutzerdefinierten Tools](#tbxinfo)beschrieben, und fügen Sie Sie demselben Verzeichnis hinzu. Auf diese Weise können Sie ein Toolboxsymbol, eine QuickInfo usw. definieren.

    - Eine einzelne **tbxinfo** -Datei kann verwendet werden, um mehrere Tools zu definieren. Diese kann auf Diagrammdateien verweisen, die sich in Unterordnern befinden.

5. Starten Sie Visual Studio neu. Das zusätzliche Tool wird in der Toolbox für den entsprechenden Diagrammtyp angezeigt.

### <a name="what-the-custom-tool-will-replicate"></a>Was vom benutzerdefinierten Tool repliziert wird
 Ein benutzerdefiniertes Tool repliziert die meisten Funktionen des Quelldiagramms:

- Namen Wenn ein Element aus der Toolbox erstellt wird, wird bei Bedarf eine Zahl am Ende des Namens hinzugefügt, um doppelte Namen im selben Namespace zu verhindern.

- Farben, Größen und Formen

- Stereotype und Paketprofile

- Eigenschaftswerte wie z. B. Is Abstract

- Verknüpfte Arbeitselemente

- Multiplizitäten und andere Eigenschaften von Beziehungen

- Die relativen Positionen von Formen

  Die folgenden Funktionen werden in einem benutzerdefinierten Tool nicht beibehalten:

- Einfache Formen Hierbei handelt es sich um Formen, die nicht im Zusammenhang mit Modellelementen stehen, die Sie in einigen Arten von Diagrammen zeichnen können.

- Connector-Routing Wenn Sie Connectors manuell weiterleiten, wird das Routing nicht beibehalten, wenn das Tool verwendet wird. Die Positionen einiger geschachtelter Formen, wie z. B. Ports, werden in Bezug auf ihre Besitzer nicht beibehalten.

## <a name="how-to-define-the-properties-of-custom-tools"></a><a name="tbxinfo"></a> Definieren der Eigenschaften von benutzerdefinierten Tools
 Mithilfe einer Toolbox-Informationsdatei (**. tbxinfo**) können Sie einen Toolbox Namen, ein Symbol, eine QuickInfo, eine Registerkarte und ein Hilfe Schlüsselwort für ein oder mehrere benutzerdefinierte Tools angeben. Nennen Sie einen beliebigen Namen, z. b. **mytools. tbxinfo**.

 Die allgemeine Form der Datei ist wie folgt:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 Der Wert jedes Elements kann Folgendes sein:

- `<bmp fileName="…"/>` für das Toolboxsymbol und `<value>string</value>` für die anderen Elemente, wie in dem Beispiel dargestellt.

  \- oder -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   In diesem Fall geben Sie eine kompilierte Assembly an, in der die Zeichenfolgenwerte als Ressourcen kompiliert wurden.

  Fügen Sie einen `<customToolboxItem>`-Knoten für jedes Toolboxelement hinzu, das Sie definieren möchten.

  Die Knoten in der **tbxinfo** -Datei sind wie folgt. Es gibt einen Standardwert für jeden Knoten.

|Knotenname|Definiert|
|---------------|-------------|
|displayName|Der Name des Toolboxelements.|
|tabName|Die Toolboxregisterkarte, in der das Element angezeigt werden soll. Sie können entweder den Namen der normalen Registerkarte für diesen Typ von Diagramm oder einen anderen Namen angeben.|
|image|Der Speicherort der Bitmapdatei (**. bmp**), die die Höhe und Breite von 16 und eine Farbtiefe von 24 Bits aufweisen muss.|
|f1Keyword|Das Schlüsselwort, mit dem ein Hilfethema gesucht wird.|
|QuickInfo|Eine QuickInfo für dieses Tool.|

 Sie können die Bitmapdatei in Visual Studio bearbeiten und ihre Höhe und Breite im Eigenschaftenfenster auf 16 festlegen.

> [!NOTE]
> Wenn Sie beginnen, eine TBXINFO-Datei zu verwenden, nachdem Sie mit der alleinigen Verwendung von Diagrammdateien experimentiert haben, stellen sie möglicherweise fest, dass die Toolbox sowohl die alten als auch die neuen Versionen eines Toolboxelements enthält. Dies kann auch auftreten, wenn der Name der Diagrammdatei in der TBXINFO-Datei falsch eingegeben wurde. Wenn dies der Fall ist, wählen Sie im Kontextmenü der Toolbox **Toolbox zurücksetzen**aus. Die benutzerdefinierten Toolboxelemente werden ausgeblendet. Starten Sie Visual Studio neu; daraufhin werden die richtigen benutzerdefinierten Elemente angezeigt.

## <a name="how-to-distribute-toolbox-items-in-a-visual-studio-extension"></a><a name="Extension"></a> Verteilen von Toolbox Elementen in einer Visual Studio-Erweiterung
 Sie können Toolbox Elemente an andere Benutzer verteilen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] indem Sie Sie in eine Visual Studio-Erweiterung (VSIX) verpacken. Sie können Befehle, Profile und andere Erweiterungen in der gleichen VSIX-Datei verpacken. Weitere Informationen finden Sie unter Bereitstellen von [Visual Studio-Erweiterungen](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

 Die übliche Vorgehensweise zum Erstellen einer Visual Studio-Erweiterung besteht darin, die VSIX-Projektvorlage zu verwenden. Zu diesem Zweck muss [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installiert sein.

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>So fügen Sie ein Toolboxelement zu einer Visual Studio-Erweiterung hinzu

1. [Erstellen und testen Sie ein oder mehrere benutzerdefinierte Tools](#DefineTool).

2. [Erstellen Sie eine tbxinfo-Datei](#tbxinfo) , die auf die Tools verweist.

3. Öffnen Sie ein vorhandenes Visual Studio-Erweiterungsprojekt.

     \- oder -

     Definieren Sie ein neues Visual Studio-Erweiterungsprojekt.

    1. Wählen Sie im Menü **Datei** die Befehle **Neu** und **Projekt** aus.

    2. Wählen Sie im Dialogfeld **Neues Projekt** unter **installierte Vorlagen**die Option **Visual c#**, **Erweiterbarkeit**, **VSIX-Projekt**aus.

4. Fügen Sie die Toolboxdefinitionen dem Projekt hinzu. Fügen Sie die **tbxinfo** -Datei, die Diagramm Dateien, die Bitmapdateien und alle Ressourcen Dateien ein, und stellen Sie sicher, dass Sie in der VSIX enthalten sind.

    - Wählen Sie in Projektmappen-Explorer im Kontextmenü des VSIX-Projekts die Option **Hinzufügen**, **Vorhandenes Element**aus. Legen Sie im Dialogfeld **Objekte vom Typ: alle Dateien**fest. Suchen Sie die Dateien, wählen Sie alle aus, und klicken Sie dann auf **Hinzufügen**.

        > [!NOTE]
        > In diesem Projekt können die Diagrammdateien nicht im Modell-Editor geöffnet werden.

5. Legen Sie die folgenden Eigenschaften aller Dateien fest, die Sie gerade hinzugefügt haben. Sie können ihre Eigenschaften gleichzeitig festlegen, indem Sie alle im Projektmappen-Explorer auswählen. Achten Sie darauf, dass Sie keine Änderungen an den Eigenschaften der anderen Dateien im Projekt vornehmen.

     **In Ausgabeverzeichnis kopieren**  =  **Immer kopieren**

     **Buildvorgang** = **Inhalt**

     **In VSIX einschließen**  =  **true**

6. Öffnen Sie **source.extension.vsixmanifest**. Die Datei wird im Erweiterungsmanifest-Editor geöffnet.

7. Fügen Sie unter **Metadaten**eine Beschreibung für die benutzerdefinierten Tools hinzu.

     Wählen Sie unter **Assets**die Option **neu** aus, und legen Sie dann die Felder im Dialogfeld wie folgt fest:

    - **Typ**  =  **Benutzerdefinierter Erweiterungstyp**

    - Typ = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Dies ist keine der Optionen in der Dropdownliste. Sie müssen sie über die Tastatur eingeben.

    - **Quelle**  =  **Datei im Dateisystem**.

    - **Path** = your **tbxinfo** -Datei, z. b. **mytools. tbxinfo**

8. Erstellen Sie das Projekt.

9. Drücken Sie F5, **um zu überprüfen, ob die Erweiterung funktioniert**. Die experimentelle Instanz von Visual Studio wird geöffnet.

     Erstellen oder öffnen Sie in der experimentellen Instanz ein UML-Diagramm des relevanten Typs. Stellen Sie sicher, dass das neue Tool in der Toolbox angezeigt wird und dass Elemente ordnungsgemäß erstellt werden.

10. **So erhalten Sie eine VSIX-Datei für die Bereitstellung:** Öffnen Sie in Windows-Explorer den Ordner " **.\bin\debug** " oder " **.\bin\release** ", um die **VSIX** -Datei zu suchen. Dies ist eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterungsdatei. Sie kann auf dem Computer installiert und an andere Visual Studio-Benutzer gesendet werden.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>So installieren Sie benutzerdefinierte Tools aus einer Visual Studio-Erweiterung

1. Öffnen Sie im Windows-Explorer oder in Visual Studio die `.vsix`-Datei.

2. Wählen Sie im angezeigten Dialogfeld die Option **Installieren** aus.

3. Um die Erweiterung zu deinstallieren oder vorübergehend zu deaktivieren, öffnen Sie im **Menü Extras die Option** **Erweiterungen und Updates** .

## <a name="localization"></a>Lokalisierung
 Sie können eine Erweiterung erstellen, die bei der Installation auf einem anderen Computer Toolnamen und QuickInfos in der Sprache des Zielcomputers anzeigt.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>So stellen Sie Versionen des Tools in mehreren Sprachen bereit

1. Erstellen Sie ein Visual Studio-Erweiterungsprojekt, das ein oder mehrere benutzerdefinierte Tools enthält.

    Verwenden Sie in der **tbxinfo** -Datei die Ressourcen Datei Methode, um die Tools `displayName` , die Toolbox und die QuickInfo zu definieren `tabName` . Erstellen Sie eine Ressourcendatei, in der diese Zeichenfolgen definiert sind, kompilieren Sie diese in eine Assembly, und verweisen Sie dann aus der TBXINFO-Datei darauf.

2. Erstellen Sie zusätzliche Assemblys, die Ressourcendateien mit Zeichenfolgen in anderen Sprachen enthalten.

3. Legen Sie jede zusätzliche Assembly in einen Ordner, dessen Name der Kulturcode für die Sprache ist. Platzieren Sie z. b. eine französische Version der Assembly in einem Ordner mit dem Namen " **fr**".

4. Sie sollten einen neutralen Kulturcode verwenden, also in der Regel zwei Buchstaben. Verwenden Sie keine speziellen Kulturcodes wie `fr-CA`. Weitere Informationen zu Kultur Codes finden Sie unter [CultureInfo. GetCultures-Methode](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx), die eine komplette Liste der Kultur Codes enthält.

5. Erstellen Sie die Visual Studio-Erweiterung, und verteilen Sie sie.

6. Wenn die Erweiterung auf einem anderen Computer installiert ist, wird die Version der Ressourcendatei für die lokale Kultur des Benutzers automatisch geladen. Wenn Sie keine Version für die Kultur des Benutzers angegeben haben, werden die Standardressourcen verwendet.

   Sie können diese Methode verwenden, um verschiedene Versionen des Prototypdiagramms zu installieren. Die Namen von Elementen und Connectors sind in jeder Installation identisch.

## <a name="other-toolbox-operations"></a>Andere Toolboxvorgänge
 In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] können Sie normalerweise die Toolbox anpassen, indem Sie Tools umbenennen, diese in andere Toolboxregisterkarten verschieben und löschen. Aber diese Änderungen werden für benutzerdefinierte Modellierungstools, die mit den in diesem Thema beschriebenen Verfahren erstellt wurden, nicht beibehalten. Beim Neustart von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] werden benutzerdefinierte Tools wieder mit ihren definierten Namen und Toolboxspeicherorten angezeigt.

 Außerdem werden die benutzerdefinierten Tools ausgeblendet, wenn Sie den Befehl **Toolbox zurücksetzen** ausführen. Sie werden jedoch wieder angezeigt, wenn Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] neu starten.

## <a name="see-also"></a>Weitere Informationen
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md) [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md) [Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definieren von Validierungs Einschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)
