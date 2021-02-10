---
title: MT-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Parameter und Befehlszeilenoptionen der MSBuild-Aufgabe „MT“, die das Microsoft-Manifesttool (mt.exe) umschließt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a023c58e528b2cda74fa42fcce46fd9c39059459
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905436"
---
# <a name="mt-task"></a>MT-Aufgabe

Umschließt das Microsoft-Manifesttool *mt.exe*. Weitere Informationen finden Sie unter [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **MT**-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige andere Parameter entsprechen einer Befehlszeilenoption.

> [!NOTE]
> In der *mt.exe*-Dokumentation wird als Präfix für Befehlszeilenoptionen ein Bindestrich ( **-** ) verwendet, in diesem Artikel jedoch ein Schrägstrich ( **/** ). Beide Präfixe sind zulässig.

|Parameter|Beschreibung|
|---------------|-----------------|
|**AdditionalManifestFiles**|Optionaler **String[]** -Parameter.<br /><br /> Gibt den Namen von mindestens einer Manifestdatei an.<br /><br /> Weitere Informationen finden Sie unter der **/manifest**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AdditionalOptions**|Optionaler **String** -Parameter.<br /><br /> Eine Liste der Befehlszeilenoptionen. Beispiel: /\<option1> /\<option2> /\<option#>. Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht durch einen anderen **MT**-Aufgabenparameter dargestellt werden.<br /><br /> Weitere Informationen finden Sie unter [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Optionaler **String** -Parameter.<br /><br /> Gibt die Attributwerte des **assemblyIdentity**-Elements des Manifests an. Geben Sie eine durch Trennzeichen getrennte Liste an, in der zuerst der Wert des `name`-Attributs erscheint und anschließend mindestens ein Name/Wert-Paar des Formats *\<attribute name>=<attribute_value>* .<br /><br /> Weitere Informationen finden Sie unter der **/identity**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ComponentFileName**|Optionaler **String** -Parameter.<br /><br /> Gibt den Namen der Dynamic Link Library an, die Sie aus den *RGS*- oder *TLB*-Dateien erstellen möchten. Dieser Parameter ist erforderlich, wenn Sie die **RegistrarScriptFile**- oder **TypeLibraryFile**-MT-Aufgabenparameter angeben.<br /><br /> Weitere Informationen finden Sie unter der **/dll**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Optionaler **String** -Parameter.<br /><br /> Gibt die Abhängigkeitsinformationen-Datei an, die von Visual Studio verwendet wird, um Informationen zur Build-Abhängigkeit für das Manifesttool zu verwalten.|
|**EmbedManifest**|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird die Manifestdatei in die Assembly eingebettet. Wenn `false`, wird eine eigenständige Manifestdatei erstellt.|
|**EnableDPIAwareness**|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden die Manifestinformationen erweitert, die die Anwendung als „mit DPI kompatibel“ markieren. Wenn eine Anwendung so geschrieben wird, dass sie mit DPI kompatibel ist, sieht ihre Benutzeroberfläche bei verschiedensten High-DPI-Anzeigeeinstellungen ansprechend aus.<br /><br /> Weitere Informationen finden Sie unter [Hoher DPI-Wert](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden Dateien zur Katalogdefinition (*CDF*) generiert.<br /><br /> Weitere Informationen finden Sie unter der **/makecdfs**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird bewirkt, dass Kategorietags generiert werden. Wenn dieser Parameter `true` ist, muss der **ManifestFromManagedAssemblyMT**-Aufgabenparameter ebenfalls angegeben werden.<br /><br /> Weitere Informationen finden Sie unter der **/category**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Optionaler **String** -Parameter.<br /><br /> Geben Sie das Manifest aus einer Ressource vom Typ RT_MANIFEST ein, die über den angegebenen Bezeichner verfügt. Geben Sie eine Ressource im Format \<file>[;[#]\<resource_id>] an, bei der der optionale \<resource_id>-Parameter eine positive 16-Bit-Zahl ist.<br /><br /> Wenn keine `resource_id` angegeben wird, wird der CREATEPROCESS_MANIFEST_RESOURCE-Standardwert (1) verwendet.<br /><br /> Weitere Informationen finden Sie unter der [Mt.exe](/windows/desktop/SbsCs/mt-exe)-Option **/inputresource**.|
|**ManifestFromManagedAssembly**|Optionaler **String** -Parameter.<br /><br /> Generiert ein Manifest aus der angegebenen verwalteten Assembly.<br /><br /> Weitere Informationen finden Sie unter der [Mt.exe](/windows/desktop/SbsCs/mt-exe)-Option **/managedassemblyname**.|
|**ManifestToIgnore**|Optionaler **String** -Parameter.<br /><br /> (Nicht verwendet.)|
|**OutputManifestFile**|Optionaler **String** -Parameter.<br /><br /> Gibt den Namen des Ausgabemanifests an. Wenn dieser Parameter nicht angegeben wird und gerade nur an einem Manifest gearbeitet wird, wird dieses stattdessen geändert.<br /><br /> Weitere Informationen finden Sie unter der **/out**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Optionaler **String** -Parameter.<br /><br /> Geben Sie das Manifest an eine Ressource vom Typ RT_MANIFEST aus, die über den angegebenen Bezeichner verfügt. Die Ressource besitzt das Format \<file>[;[#]\<resource_id>], wobei der optionale \<resource_id>-Parameter eine positive 16-Bit-Zahl ist.<br /><br /> Wenn keine `resource_id` angegeben wird, wird der CREATEPROCESS_MANIFEST_RESOURCE-Standardwert (1) verwendet.<br /><br /> Weitere Informationen finden Sie unter der [Mt.exe](/windows/desktop/SbsCs/mt-exe)-Option **/outputresource**.|
|**RegistrarScriptFile**|Optionaler **String** -Parameter.<br /><br /> Gibt den Namen der Registrierungsskriptdatei (*RGS*) zum Verwenden bei der COM-Manifest-Unterstützung ohne Registrierung an.<br /><br /> Weitere Informationen finden Sie unter der **/rgs**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Optionaler **String** -Parameter.<br /><br /> Gibt die Datei an, die Werte für die ersetzbaren Zeichenfolgen in der Registrierungsskriptdatei (*RGS*) enthält.<br /><br /> Weitere Informationen finden Sie unter der [Mt.exe](/windows/desktop/SbsCs/mt-exe)-Option **/replacements**.|
|**ResourceOutputFileName**|Optionaler **String** -Parameter.<br /><br /> Gibt die Ausgaberessourcen-Datei an, die verwendet wird, um das Manifest in die Projektausgabe einzubetten.|
|**Sources**|Optionaler `ITaskItem[]`-Parameter.<br /><br /> Definiert eine Liste von durch Leerräume getrennten Manifestquelldateien.<br /><br /> Weitere Informationen finden Sie unter der **/manifest**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressDependencyElement**|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird ein Manifest ohne Abhängigkeitselemente generiert. Wenn dieser Parameter `true` ist, müssen Sie auch den **ManifestFromManagedAssemblyMT**-Aufgabenparameter angeben.<br /><br /> Weitere Informationen finden Sie unter der [Mt.exe](/windows/desktop/SbsCs/mt-exe)-Option **/nodependency**.|
|**SuppressStartupBanner**|Optionaler `Boolean`-Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Weitere Informationen finden Sie unter der [Mt.exe](/windows/desktop/SbsCs/mt-exe)-Option **/nologo**.|
|**TrackerLogDirectory**|Optionaler `String`-Parameter.<br /><br /> Gibt das Zwischenverzeichnis an, in dem die Nachverfolgungsprotokolle für diese Aufgabe gespeichert sind.|
|**TypeLibraryFile**|Optionaler **String** -Parameter.<br /><br /> Gibt den Namen der Typbibliotheksdatei (*TLB*) an. Wenn Sie diesen Parameter angeben, müssen Sie ebenfalls den **ComponentFileNameMT**-Aufgabenparameter angeben.<br /><br /> Weitere Informationen finden Sie unter der **/tlb**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird der Hashwert der Dateien an dem Pfad berechnet, der vom **UpdateFileHashesSearchPathMT**-Aufgabenparameter angegeben wird. Anschließend wird beim Manifest der Wert des **hash**-Attributs des **file**-Elements mithilfe des berechneten Werts aktualisiert.<br /><br /> Weitere Informationen finden Sie unter der **/hashupdate**-Option in [Mt.exe](/windows/desktop/SbsCs/mt-exe). Siehe auch den Parameter **UpdateFileHashesSearchPath** in dieser Tabelle|
|**UpdateFileHashesSearchPath**|Optionaler `String`-Parameter.<br /><br /> Gibt den Suchpfad an, der verwendet werden soll, wenn die Dateihashwerte aktualisiert werden. Verwenden Sie diesen Parameter mit dem **UpdateFileHashesMT**-Aufgabenparameter.<br /><br /> Weitere Informationen finden Sie unter dem **UpdateFileHashes**-Parameter in dieser Tabelle.|
|**VerboseOutput**|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden ausführliche Debuginformationen angezeigt.<br /><br /> Weitere Informationen finden Sie unter der Option **/verbose** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
