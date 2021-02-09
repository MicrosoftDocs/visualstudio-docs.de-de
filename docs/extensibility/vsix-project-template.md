---
title: VSIX-Projektvorlage | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die VSIX-Projektvorlage verwenden, um Visual Studio-Erweiterungen in ein VSIX-Projekt einzubinden, und veröffentlichen Sie das Paket dann auf dem Visual Studio Marketplace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d346826c97bfa0ed885579d4816c452dbed9a2d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905718"
---
# <a name="vsix-project-template"></a>VSIX-Projektvorlage

Sie können die VSIX-Projektvorlage verwenden, um eine oder mehrere Visual Studio-Erweiterungen in ein VSIX-Projekt einzubinden und das Paket dann auf der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website zu veröffentlichen.

 VSIX-Bereitstellung unterstützt VSPackages, Assemblys, MEF-Komponenten, Projektvorlagen, Element Vorlagen, Toolbox-Steuerelemente und benutzerdefinierte Erweiterungs Typen.

> [!NOTE]
> Um VSIX-Projekte verwenden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen zum Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Suchen der VSIX-Projektvorlage

Die VSIX-Projektvorlage steht im Dialogfeld **Neues Projekt** zur Verfügung, indem Sie nach "VSIX" suchen.  Es gibt sowohl eine c#-als auch eine Visual Basic-Version.

> [!TIP]
> Stellen Sie sicher, dass .NET Framework 4,5 oder höher im Dropdown-Listenfeld oben im Dialogfeld " **Neues Projekt** " angegeben ist.

## <a name="uses-of-the-vsix-project-template"></a>Verwendung der VSIX-Projektvorlage

Die VSIX-Projektvorlage hat zwei Haupt Verwendungsmöglichkeiten:

- Zum Bereitstellen von Projektvorlagen, Element Vorlagen und Erweiterungen.

- Zum Einschließen der Ausgaben mehrerer Erweiterungen in ein Bereitstellungs Paket.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Verpacken einer Erweiterung in einem leeren VSIX-Projekt

Sie können eine vorhandene Erweiterung oder eine Erweiterung, die noch nicht über VSIX-Unterstützung verfügt, packen, indem Sie Sie in ein leeres VSIX-Projekt umschließt. Die zu umschließende Erweiterung muss von einem Typ sein, der vom [VSIX-Schema](../extensibility/vsix-extension-schema-2-0-reference.md)unterstützt wird.

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>So packen Sie eine Erweiterung mithilfe eines VSIX-Projekts

1. Erstellen Sie die Projekte, die ihre Erweiterung bilden.

2. Erstellen Sie ein VSIX-Projekt mithilfe der **VSIX-Projekt** Vorlage.

    " *Source. Extension. vsixmanifest* " wird im **Manifest-Designer** geöffnet.

3. Wählen Sie auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.

    Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

4. Wählen Sie in der Liste **Typ** den Typ der Erweiterung aus, die Sie hinzufügen möchten.

5. Führen Sie die folgenden Schritte aus, um eine Erweiterung oder ein Inhalts Element hinzuzufügen, das in der aktuellen Projekt Mappe enthalten ist (z. b. eine Element Vorlage oder eine kompilierte Assembly):

   1. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

   2. Wählen Sie in der Liste **Projekt** den Namen der Erweiterung aus.

   3. Geben Sie im Feld **in diesen Ordner einbetten** den Namen eines Ordners ein, in den das Medienobjekt eingebettet werden soll, und klicken Sie dann auf die Schaltfläche **OK** .

6. Führen Sie die folgenden Schritte aus, um eine Erweiterung oder ein Inhalts Element hinzuzufügen, die nicht in der aktuellen Projekt Mappe enthalten ist:

   1. Wählen Sie im Listenfeld **Quelle** die Option **Datei im Dateisystem** aus.

   2. Geben Sie im Feld **Pfad** den vollständigen Pfad zur kompilierten oder komprimierten Erweiterungs Datei ein, oder verwenden Sie die Schaltfläche **Durchsuchen** , um zu der Datei zu navigieren.

   3. Geben Sie im Feld **in diesen Ordner einbetten** den Namen eines Ordners ein, in den das Medienobjekt eingebettet werden soll, und klicken Sie dann auf die Schaltfläche **OK** .

7. Wenn Sie möchten, dass das Paket zusätzliche Erweiterungen enthält, fügen Sie diese auf die gleiche Weise hinzu.

8. Erstellen Sie die Projektmappe.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt eine *vsix-Datei,* die eine VSIX-Manifest-Datei, eine [Content_Types]*. XML* -Datei und alle Erweiterungs Ressourcen enthält, die Sie dem Projekt hinzugefügt haben.

## <a name="see-also"></a>Weitere Informationen

- [VSIX-Erweiterungs Schema 2,0-Referenz](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)
