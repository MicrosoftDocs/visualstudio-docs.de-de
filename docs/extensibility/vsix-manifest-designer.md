---
title: VSIX-Manifest-Designer | Microsoft-Dokumentation
description: Erfahren Sie, wie der VSIX-Manifest-Designer eine VSIX-Paket Manifest-Datei ändert, mit der das Installations Verhalten für eine Visual Studio-Erweiterung festgelegt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6323b4330279848bc0453bdc7413904e2582d13a
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863973"
---
# <a name="vsix-manifest-designer"></a>VSIX-Manifest-Designer
Ändert eine VSIX-Paket Manifest-Datei, mit der das Installations Verhalten für eine Visual Studio-Erweiterung festgelegt wird.

 Der **VSIX-Manifest-Designer** wird dem zugrunde liegenden VSIX-Schema zugeordnet. Jedes Element im Schema kann mit einem entsprechenden Steuerelement im Designer festgelegt werden. Weitere Informationen zum Schema finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

 Um den **VSIX-Manifest-Designer** zu öffnen, suchen Sie in **Projektmappen-Explorer** eine Datei vom Typ " *Source. Extension. vsixmanifest* ", und öffnen Sie die Datei. Wenn die Datei keine gültige XML-Datei enthält, wird der Manifest-Designer nicht geöffnet.

> [!NOTE]
> Die Datei " *Source. Extension. vsixmanifest* " wird beim Erstellen des Pakets an die *Erweiterung ". vsixmanifest* " ausgegeben.

## <a name="uielement-list"></a>UIElement-Liste
 Der **VSIX-Manifest-Designer** enthält vier Abschnitte, die diesen Elementen der obersten Ebene des Schemas entsprechen:

- Metadaten

- Installations Ziele

- Objekte

- Abhängigkeiten

  Der Überschriften Bereich enthält die folgenden Steuerelemente.

  **Produkt Name** Beschreibt den Erweiterungs Namen.

  **Produkt-ID** Gibt die eindeutigen Identifikationsinformationen für dieses Paket an.

  **Autor** Gibt den Namen des Autors der Erweiterung an.

  **Version** Gibt die Versionsnummer der Erweiterung an.

  Die Registerkarte **Metadaten** enthält die folgenden Steuerelemente.

  **Beschreibung** Stellt eine Textbeschreibung der Erweiterung bereit, die im Erweiterungs- **Manager** angezeigt werden soll.

  **Sprache** Gibt die Standardsprache für das Paket an, die den Textdaten im Manifest entspricht. Das- `Language` Attribut folgt der Common Language Runtime (CLR)-Gebiets Schema-Code Konvention für Ressourcenassemblys, z. b. en-US, en, fr-fr. Standardmäßig ist der wertneutral, was bedeutet, dass das Paket in jeder Sprachversion von Visual Studio ausgeführt wird.

  **Lizenz** Gibt die Textdatei an, die die Benutzerlizenz enthält (sofern vorhanden).

  **Symbol** Gibt die Grafikdatei (*. png*, *. bmp*, *. JPEG*, *. ico*) an, die das Symbol enthält, das im **Erweiterungs-Manager** angezeigt werden soll, wenn ein Symbol vorhanden ist. Das Symbolbild muss eine Größe von 32 x 32 Pixel aufweisen, oder die Größe wird auf diese Dimensionen angepasst. Wenn kein Symbol angegeben wird, verwendet der **Erweiterungs-Manager** ein Standard Symbol.

  **Vorschaubild** Gibt die Grafikdatei (*PNG*, *BMP*, *. JPEG*, *. ico*) an, die das Vorschaubild enthält, das im **Erweiterungs-Manager** angezeigt werden soll, wenn ein Vorschaubild vorhanden ist. Das Vorschaubild muss 200 x 200 Pixel betragen. Wenn kein Vorschaubild angegeben wird, verwendet der **Erweiterungs-Manager** ein Standard Image.

  **Tags** Fügt texttags hinzu, die für Such Hinweise verwendet werden sollen.

  **Anmerkungen** zu dieser Version Gibt eine Datei (*txt*, *RTF*) an, die Anmerkungen zu dieser Version enthält. Es kann sich dabei auch um die URL einer Website handeln, auf der die Anmerkungen zu diesem Release enthalten sind.

  **Leitfaden zu** den ersten Schritten Gibt eine Datei (*txt*, *RTF*) an, die Informationen zur Verwendung der Erweiterung oder des Inhalts im VSIX-Paket enthält. Diese Anleitung wird angezeigt, wenn die Erweiterungs Installation fertiggestellt wurde. Außerdem übernimmt die URL einer Website, auf der das Handbuch angezeigt wird.

  **Weitere Informationen-URL** Gibt die URL einer Website an, die zusätzliche Informationen über das Produkt enthält.

  Die Registerkarte **Ziele installieren** enthält die folgenden Steuerelemente.

  **Installationstyp** Listet die **Visual Studio-Erweiterung** und das **Erweiterungs-SDK** als Ziel Installationstypen auf. Die Optionen unterscheiden sich je nach ausgewähltem Typ.

  **Visual Studio-Erweiterung** Listet die **installationtarget** -Elemente auf, die beschreiben, wie das Paket installiert werden kann und in welche Visual Studio-Produkte diese Erweiterung installiert werden kann. Jedes Produkt wird separat anhand des Namens und eines Versions-oder Versions Bereichs identifiziert. Produkte können zur Liste hinzugefügt, geändert und gelöscht werden. Der Name und die Version eines Produkts entsprechen den Attributen **ID** und **Version** des zugeordneten **installationtarget** -Elements.

  Der **Versions Bereich** ist [12,0, 14,0] und verwendet die folgende Notation:

- [-Minimale inklusive Version

- ]-maximale Version einschließlich

- (-Mindestversion exklusiv

- )-maximale Version exklusiv

- Einzelne Version #-nur die angegebene Version

  **Erweiterungs-SDK** Gibt eine globale Installation an, die nicht für ein bestimmtes Produkt und eine bestimmte Version festgelegt ist. Der **Bezeichner der Zielplattform** ist die Plattform, z. b. "Windows", die Sie als Zielplattform verwenden. Die Version der **Zielplattform** ist die Version (z. b. 8,0) Ihrer Zielplattform. **SDK-Name** und **SDK-Version** sind der Name und die Versionsnummer des SDK.

  **Diese VSIX wird für alle Benutzer installiert (erfordert eine Erhöhung der Rechte bei der Installation)** . Wenn Sie dieses Kontrollkästchen aktivieren, wird die Erweiterung für alle Benutzer installiert. Andernfalls wird Sie nur für den aktuellen Benutzer installiert.

  **Diese VSIX wird von Windows Installer** Wenn Sie dieses Kontrollkästchen aktivieren, wird die Erweiterung vom Windows Installer (*MSI* -Datei) installiert. Andernfalls wird Sie als typisches VSIX-Paket (*VSIX* -Datei) installiert.

  Die Registerkarte **Assets** enthält die folgenden Steuerelemente.

  **Liste der Assets** Listet die Asset-Elemente auf, die die Erweiterungs-oder Inhaltselemente beschreiben, die dieses Paket auflistet. Jede Erweiterung bzw. jedes Inhalts Element wird separat nach Quelle, Typ und Pfad aufgelistet. Erweiterungen und Inhaltselemente können der Liste hinzugefügt, geändert und gelöscht werden. Der Typ und der Pfad einer Erweiterung oder eines Inhalts Elements entsprechen den `Type` `Path` Attributen und des zugeordneten `Asset` Elements. Die folgenden Typen werden unterstützt:

- Microsoft. VisualStudio. Package

- Microsoft.VisualStudio.MefComponent

- Microsoft. VisualStudio. ToolboxControl

- Microsoft. VisualStudio. Samples

- Microsoft. VisualStudio. ProjectTemplate

- Microsoft. VisualStudio. ItemTemplate

- Microsoft. VisualStudio. Assembly

- Microsoft. extensionsdk

  Wenn Sie ein Medienobjekt hinzufügen oder bearbeiten möchten, müssen Sie den Assettyp angeben, unabhängig davon, ob es sich um ein Projekt in der aktuellen Projekt Mappe oder eine Datei im Dateisystem handelt, und den Namen des Projekts. Sie können auch den Namen des Ordners angeben, in den eingebettet werden soll.

  Sie können auch eigene Typen erstellen und Ihnen eindeutige Namen zuordnen.

  Die Registerkarte **Abhängigkeiten** enthält die folgenden Steuerelemente.

  **Name, Quelle und Versions Bereich** Listet die Abhängigkeits Elemente dieses Pakets auf, bei denen es sich um andere Pakete handelt, von denen dieses Paket abhängt. Wenn ein Abhängigkeits Paket angegeben wird, muss es vor der Installation dieses Pakets installiert werden. Andernfalls muss dieses Paket es installieren.

  Abhängigkeits Pakete werden durch den Bezeichner, den Namen, den Versions Bereich, die Quelle und die Art der Auflösung der Abhängigkeit angegeben. Jedes Abhängigkeits Paket wird separat nach Name, Version und Quelle aufgelistet. Abhängigkeits Pakete können zur Liste hinzugefügt, geändert und gelöscht werden.

  Der Bezeichner muss mit dem- `ID` Attribut der Metadaten für das Abhängigkeits Paket identisch sein. Bei der Quelle kann es sich um ein Projekt in der aktuellen Projekt Mappe, eine zurzeit installierte Erweiterung oder eine Datei handeln. Die Einstellung für die **Abhängigkeits** Auflösung kann der relative Pfad eines geschposteten Pakets oder die URL des Download Speicher Orts für die Abhängigkeit sein. Die ID, die Version und die Auflösung des Abhängigkeits Pakets entsprechen den `Id` `Version` Attributen, und `Location` des zugeordneten `Dependency` Elements.

## <a name="see-also"></a>Weitere Informationen
- [VSIX-Erweiterungs Schema 2,0-Referenz](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
