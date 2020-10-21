---
title: 'Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c47b16bbb9fe5eb352171e6e1cf4c13890890265
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "92298655"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung
Eine domänenspezifische Sprache (DSL) wird mithilfe einer spezialisierten Visual Studio-Projekt Mappe erstellt.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie dieses Verfahren starten können, installieren Sie die folgenden Komponenten:

- Visual Studio
- Visual Studio SDK (installiert als Teil der **Visual Studio-Erweiterungs Entwicklung** )
- Modellierungs-SDK (installiert als Visual Studio-Komponente)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer Domain-Specific-Sprachlösung

1. Starten Sie den DSL-Assistenten, indem Sie ein neues **Domänen spezifisches sprach-Designer** -Projekt erstellen.

   > [!NOTE]
   > Vorzugsweise sollte der Name, den Sie für das Projekt auswählen, ein gültiger Visual c#-Bezeichner sein, da er zum Generieren von Code verwendet werden kann.

   ::: moniker range="vs-2017"

   ![Dialogfeld "DSL erstellen"](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Wählen Sie eine DSL-Vorlage aus.

    Wählen Sie auf der Seite Optionen für die **Domain-Specific Sprache auswählen** eine der Lösungs Vorlagen aus, z. b. **minimale Sprache**. Wählen Sie eine Vorlage aus, die der zu erstellenden DSL ähnelt.

    Weitere Informationen zu Lösungs Vorlagen finden Sie unter [Auswählen einer Domain-Specific-sprach Lösungs Vorlage](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Geben Sie auf der Seite **Dateierweiterung** eine Dateierweiterung ein. Sie muss auf Ihrem Computer und auf allen Computern, auf denen Sie die DSL installieren möchten, eindeutig sein. Die Meldung " **keine Anwendungen oder Visual Studio-Editoren" sollte diese Erweiterung verwenden**.

   - Wenn Sie die Dateinamenerweiterung in früheren experimentellen DSLs verwendet haben, die noch nicht vollständig installiert wurden, können Sie Sie mit dem Tool " **experimentelle Instanz zurücksetzen** " löschen, das sich im Visual Studio SDK-Menü befindet.

   - Wenn eine andere Visual Studio-Erweiterung, die diese Dateierweiterung verwendet, vollständig auf dem Computer installiert wurde, sollten Sie diese deinstallieren. Klicken Sie **im Menü Extras** auf **Erweiterungs-Manager**.

4. Überprüfen Sie die Felder auf den verbleibenden Seiten des Assistenten, und passen Sie Sie ggf. an. Wenn Sie mit den Einstellungen zufrieden sind, klicken Sie auf **Fertig**stellen. Weitere Informationen zu den Einstellungen finden Sie unter [DSL-Designer-Assistenten Seiten](#settings).

    Der Assistent erstellt eine Projekt Mappe mit zwei Projekten namens **DSL** und **dslpackage**.

   > [!NOTE]
   > Wenn eine Meldung angezeigt wird, dass keine Textvorlagen aus nicht vertrauenswürdigen Quellen ausgeführt werden sollen, klicken Sie auf **OK**. Diese Meldung kann so festgelegt werden, dass Sie nicht erneut angezeigt wird.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> Die Seiten des DSL-Designer-Assistenten
 Sie können einige der Felder unverändert lassen, um die Standardwerte zu ändern. Stellen Sie jedoch sicher, dass Sie das Feld Dateierweiterung festgelegt haben.

### <a name="solution-settings-page"></a>Seite "Lösungs Einstellungen"
 **Auf welcher Vorlage möchten Sie Ihre domänenspezifische Sprache aufbauen?**
Wählen Sie eine Vorlage aus, die der zu erstellenden DSL ähnelt. Die verschiedenen Vorlagen bieten praktische Ausgangspunkte. Wenn Sie eine Projektmappenvorlage auswählen, zeigt der Assistent eine Beschreibung an. Weitere Informationen zu Lösungs Vorlagen finden Sie unter [Auswählen einer Domain-Specific-sprach Lösungs Vorlage](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Wie möchten Sie Ihre domänenspezifische Sprache benennen?**
Der Standardwert ist der Projektmappenname. Der Code wird aus diesem Wert generiert. Er muss als c#-Klassenname gültig sein.

### <a name="file-extension-page"></a>Datei Erweiterungs Seite
 **Welche Erweiterung sollen Modelldateien verwenden?**
Geben Sie eine neue Dateierweiterung ein.

 Vergewissern Sie sich, dass diese Dateierweiterung nicht bereits für die Verwendung auf diesem Computer registriert wurde. gehen Sie hierzu wie folgt vor:

 Sehen **Sie sich die anderen Tools und Anwendungen an, die für diese Erweiterung registriert**sind. Wenn die Meldung " **keine Anwendungen oder Visual Studio-Editoren verwenden diese Erweiterung**" angezeigt wird, können Sie diese Dateierweiterung verwenden.

 Wenn eine Liste der Tools oder Pakete angezeigt wird, sollten Sie eine der folgenden Aktionen ausführen:

- Geben Sie eine andere Dateierweiterung ein.

     \- oder -

- Setzen Sie die experimentelle Instanz von Visual Studio zurück. Dadurch wird die Registrierung aller zuvor erstellten DSLs aufgehoben. Klicken Sie im **Startmenü** auf **Alle Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und setzen Sie dann **die experimentelle Microsoft Visual Studio 2010-Instanz zurück**. Sie können alle anderen DSLs neu erstellen, die Sie wieder verwenden möchten.

     \- oder -

- Wenn eine Visual Studio-Erweiterung, die diese Dateierweiterung verwendet, vollständig auf dem Computer installiert wurde, deinstallieren Sie Sie. Klicken Sie **im Menü Extras** auf **Erweiterungs-Manager**.

### <a name="product-settings-page"></a>Seite "Produkt Einstellungen"
 **Wie lautet der Name des Produkts, zu dem die neue domänenspezifische Sprache gehört?**
Der Standardwert ist der DSL-Name.

 Dieser Wert wird im Windows-Explorer (oder Datei-Explorer) verwendet, um Dateien zu beschreiben, die diese Dateierweiterung aufweisen.

 **Wie lautet der Name des Unternehmens, zu dem das Produkt gehört?**
Der Name Ihres Unternehmens.

 Dieser Wert ist in die AssemblyInfo-Eigenschaften Ihres DSL-Pakets integriert.

 **Was ist der Stamm Namespace für Projekte in dieser Projekt Mappe?**
Standardmäßig wird ein Name verwendet, der aus Ihrem Unternehmen und ihren Produktnamen besteht.

### <a name="signing-page"></a>Signierungs Seite
 **Erstellen einer Schlüsseldatei mit starkem Namen** Die Standardoption besteht darin, einen neuen Schlüssel zum Signieren Ihrer DSL-Assembly zu erstellen.

 **Vorhandenen Schlüssel mit starkem Namen verwenden** Verwenden Sie diese Option, wenn Sie Ihre DSL in eine andere Assembly integrieren möchten.

 Weitere Informationen zu starken Namen finden Sie unter [Erstellen und Verwenden von Strong-Named](/dotnet/standard/assembly/create-use-strong-named)Assemblys.

## <a name="see-also"></a>Weitere Informationen

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))