---
title: Dateieigenschaften, JavaScript | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719a956558141684c7d755aafb6929f4368482f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657724"
---
# <a name="file-properties-javascript"></a>Dateieigenschaften, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können Dateieigenschaften verwenden, um anzugeben, welche Aktionen das Projektsystem für die Dateien ausführen soll. Sie können Dateieigenschaften z.B. festlegen, um anzugeben, ob eine Datei als Ressourcendatei zum Paket hinzugefügt werden soll.

 Sie können eine beliebige Datei im Projektmappen-Explorer auswählen und deren Eigenschaften im Eigenschaftenfenster überprüfen. JavaScript-Dateien haben vier Eigenschaften: **In Ausgabeverzeichnis kopieren**, **Package Action**, **Dateiname** und **Dateipfad**.

## <a name="file-properties"></a>Dateieigenschaften
 Dieser Abschnitt beschreibt die Eigenschaften, die JavaScript-Dateien gemeinsam haben.

### <a name="copy-to-output-directory-property"></a>In Ausgabeverzeichnis kopieren
 Diese Eigenschaft gibt die Bedingungen an, unter denen die ausgewählte Quelldatei in das Ausgabeverzeichnis kopiert wird. Wählen Sie **Nicht kopieren** aus, wenn die Datei zu keinem Zeitpunkt in das Ausgabeverzeichnis kopiert werden soll. Wählen Sie **Immer kopieren** aus, wenn die Datei immer in das Ausgabeverzeichnis kopiert werden soll. Wählen Sie **Kopieren, wenn neuer** aus, wenn die Datei nur kopiert werden soll, wenn Sie neuer ist als eine vorhandene Datei mit demselben Namen im Ausgabeverzeichnis.

### <a name="package-action"></a>Paketaktion
 Die Eigenschaft **Paketaktion** gibt an, welche Aktionen Visual Studio für eine Datei durchführt, wenn ein Build ausgeführt wird. **Paketaktion** kann einen der folgenden Werte haben:

- **Keine**: Die Datei ist nicht im Paketmanifest enthalten. Ein Beispiel ist eine Textdatei, die Dokumentation enthält, z.B. eine Readme-Datei.

- **Inhalt**: Die Datei ist im Paketmanifest enthalten. Dies ist z.B. der Standardwert für eine HTM-, JS, CSS, Image, Audio- oder Video-Datei.

- **Manifest** – die Datei ist nicht im Paket Manifest enthalten. Stattdessen wird die Datei für die Eingabe verwendet, während das Paketmanifest generiert wird. Dies ist der Standardwert für die Datei „package.appxmanifest“.

- **Ressource**: Die Datei ist nicht im Paketmanifest enthalten. Stattdessen wird der Inhalt der Datei in der Indexdatei der Paketressource (Package Resource Index, PRI) indiziert, die in das Paketmanifest aufgenommen wird. Sie wird normalerweise für Ressourcendateien verwendet.

  Der Standardwert für **Paketaktion** richtet sich nach der Erweiterung der Datei, die Sie der Projektmappe hinzufügen.

### <a name="file-name-property"></a>Eigenschaft „Dateiname“
 Zeigt den Dateinamen als schreibgeschützten Wert an. Um die Datei umzubenennen,müssen Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Datei klicken, und **Umbenennen** auswählen.

### <a name="full-path-property"></a>Eigenschaft „Vollständiger Pfad“
 Zeigt den vollständigen Pfad als schreibgeschützten Wert an. Ziehen Sie den Pfad der Datei zum Ändern der Datei per Drag & Drop in den Projektmappen-Explorer.

## <a name="reference-file-properties"></a>Eigenschaft „Verweisdatei“
 Dieser Abschnitt beschreibt die Eigenschaften, die Dateien gemeinsam haben, auf die aus [!INCLUDE[win8_app_js](../../includes/win8-app-js-md.md)] verwiesen wird. Wenn Sie im Projektmappen-Explorer einen Verweis auswählen, z.B. eine WINMD-Datei, einen SDK-Verweis, einen Interprojektverweis oder einen Assemblyverweis, werden möglicherweise andere Eigenschaften entsprechend des Dateityps im Eigenschaftenfenster angezeigt.

### <a name="culture"></a>culture
 Zeigt die Sprache an, die dem Verweis zugeordnet ist.

### <a name="file-type"></a>Dateityp
 Zeigt den Dateityp des Verweises an.

### <a name="file-version"></a>Dateiversion
 Zeigt die Dateiversion des Verweises an.

### <a name="identity"></a>Identität
 Zeigt die Identität des Verweises an, der im Projekt verwendet wird, die in der Projektdatei gespeichert wird.

### <a name="package"></a>Package
 Zeigt den Namen des Paketmanifests an, das dem Verweis zugeordnet ist.

### <a name="resolved-path"></a>Aufgelöster Pfad
 Zeigt den Pfad zum Verweis an, der im Projekt verwendet wird.

### <a name="sdk-path"></a>SDK-Pfad
 Zeigt den Pfad zur SDK-Datei an, auf die verwiesen wird.

### <a name="uri"></a>URI
 Zeigt den URI an, der in den HTML- oder JavaScript-Dateien enthalten sein muss, um die Datei als Quelldatei zu einzufügen.

### <a name="version"></a>Version
 Zeigt die Version des Verweises an.

## <a name="see-also"></a>Weitere Informationen
 [NIB: Projekteigenschaften (Visual Studio)](https://msdn.microsoft.com/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)
