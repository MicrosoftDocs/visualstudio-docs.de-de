---
title: Optionen und Options Seiten | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Unterstützung von Options Seiten, mit denen Sie die Werte der Optionen ändern können, die den Status eines VSPackage bestimmen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4699063d753539c72c373266b3fce9a0fdf8f00
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877870"
---
# <a name="options-and-options-pages"></a>Optionen und Optionsseiten
Wenn Sie **im Menü Extras** auf **Optionen** klicken, wird das Dialogfeld **Optionen** geöffnet. Die Optionen in diesem Dialogfeld werden zusammengefasst als Options Seiten bezeichnet. Das Struktur Steuerelement im Navigationsbereich enthält Optionen Kategorien, und jede Kategorie verfügt über Options Seiten. Wenn Sie eine Seite auswählen, werden die zugehörigen Optionen im rechten Bereich angezeigt. Auf diesen Seiten können Sie die Werte der Optionen ändern, die den Status eines VSPackage bestimmen.

## <a name="support-for-options-pages"></a>Unterstützung für options Seiten
 Die <xref:Microsoft.VisualStudio.Shell.Package> -Klasse bietet Unterstützung für das Erstellen von Options Seiten und Options Kategorien. Die- <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse implementiert eine Optionsseite.

 Die Standard Implementierung von <xref:Microsoft.VisualStudio.Shell.DialogPage> bietet einem Benutzer in einem generischen Raster mit Eigenschaften seine öffentlichen Eigenschaften. Sie können dieses Verhalten anpassen, indem Sie verschiedene Methoden auf der Seite überschreiben, um eine benutzerdefinierte Optionsseite zu erstellen, die über eine eigene Benutzeroberfläche verfügt. Weitere Informationen finden Sie unter [Erstellen einer Options Seite](../../extensibility/creating-an-options-page.md).

 Die <xref:Microsoft.VisualStudio.Shell.DialogPage> -Klasse implementiert <xref:Microsoft.VisualStudio.Shell.IProfileManager> , die Persistenz für options Seiten und auch für Benutzereinstellungen bereitstellt. Die Standard Implementierungen der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> -Methode und der- <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> Methode bewahren Eigenschafts Änderungen in einen Benutzer Abschnitt der Registrierung auf, wenn die-Eigenschaft in eine und aus einer Zeichenfolge konvertiert werden kann.

## <a name="options-page-registry-path"></a>Registrierungs Pfad der Options Seite
 Standardmäßig wird der Registrierungs Pfad der Eigenschaften, die von einer Optionsseite verwaltet werden, durch kombinieren <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , das Wort DialogPage und den Typnamen der Options Seiten Klasse bestimmt. Beispielsweise könnte eine Options Seiten Klasse wie folgt definiert werden.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Wenn <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp ist, sind die Eigenschaftsnamen-und-Wert-Paare Unterschlüssel von HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Der Registrierungs Pfad der Optionsseite selbst wird durch kombinieren <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , das Wort, den toolsoptionspages und die Kategorie und den Namen der Optionsseite bestimmt. Wenn z. b. auf der Seite benutzerdefinierte Optionen die Kategorie, die Options Seiten und die <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp ist, enthält die Seite Optionen den Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Extras/Optionen Seite Attribute und Layout
 Das- <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut bestimmt die Gruppierung von benutzerdefinierten Options Seiten in Kategorien in der Navigationsstruktur des Dialog Felds **Optionen** . Das- <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut ordnet eine Optionsseite dem VSPackage zu, das die-Schnittstelle bereitstellt. Betrachten Sie das folgende Codefragment:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Dadurch wird deklariert, dass myPackage zwei Options Seiten bereitstellt: optionspagegeneral und optionspagecustom. Im Dialogfeld **Optionen** werden beide Options Seiten in der Kategorie " **meine Options Seiten** " als " **Allgemein** " bzw. " **Benutzer** definiert" angezeigt.

## <a name="option-attributes-and-layout"></a>Options Attribute und Layout
 Die Benutzeroberfläche (UI), die die Seite bereitstellt, bestimmt die Darstellung von Optionen auf einer benutzerdefinierten Optionsseite. Layout, Bezeichnung und Beschreibung der Optionen auf einer Seite mit generischen Optionen werden durch die folgenden Attribute bestimmt:

- <xref:System.ComponentModel.CategoryAttribute> bestimmt die Kategorie der Option.

- <xref:System.ComponentModel.DisplayNameAttribute> bestimmt den anzeigen amen der Option.

- <xref:System.ComponentModel.DescriptionAttribute> bestimmt die Beschreibung der Option.

  > [!NOTE]
  > Äquivalente Attribute, SRCategory, LocDisplayName und SRDescription, verwenden Zeichen folgen Ressourcen für die Lokalisierung und sind im [Beispiel für ein verwaltetes Projekt](/azure/devops/integrate/index)definiert.

  Betrachten Sie das folgende Codefragment:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Die Option OptionInteger wird in der Kategorie **meine Optionen** auf der Optionsseite als **Integer-Option** angezeigt. Wenn die Option ausgewählt ist, wird die Option Beschreibung, **meine Ganzzahl** im Feld Beschreibung angezeigt.

## <a name="accessing-options-pages-from-another-vspackage"></a>Zugreifen auf Options Seiten aus einem anderen VSPackage
 Ein VSPackage, das eine Optionsseite hostet und verwaltet, kann mithilfe des Automatisierungs Modells Programm gesteuert von einem anderen VSPackage aus aufgerufen werden. Im folgenden Code wird ein VSPackage beispielsweise als Hosting einer Optionsseite registriert.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Mit dem folgenden Code Fragment wird der Wert von "OptionInteger" aus "myoptionpage" abgerufen:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Wenn das <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut eine Optionsseite registriert, wird die Seite unter dem Schlüssel AutomationProperties registriert, wenn das- `SupportsAutomation` Argument des-Attributs ist `true` . Automation überprüft diesen Registrierungs Eintrag, um das zugeordnete VSPackage zu finden, und dann greift Automation über die Seite gehostete Optionen auf die Eigenschaft zu, in diesem Fall auf meine Raster Seite.

 Der Registrierungs Pfad der Automatisierungs Eigenschaft wird durch kombinieren <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , das Wort, die AutomationProperties und die Kategorie und den Namen der Optionsseite bestimmt. Wenn die Optionsseite z. b. die Kategorie meine Kategorie, den Namen meiner Raster Seite und die HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp enthält, <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> hat die Automation-Eigenschaft den Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> Der kanonische Name, My Category.My Grid Page, ist der Wert des Namens unter Schlüssels dieses Schlüssels.
