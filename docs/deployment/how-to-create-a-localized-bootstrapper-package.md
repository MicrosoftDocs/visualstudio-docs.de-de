---
title: Erstellen eines lokalisierten Bootstrapperpakets | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie lokalisierte Versionen des Bootstrapperpakets in ClickOnce erstellen, indem Sie für jedes Gebiets Schema zwei weitere Dateien erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4858a9efdad747293a94563196108d895c40880b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351244"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Vorgehensweise: Erstellen eines lokalisierten Bootstrappakets
Nachdem Sie ein Bootstrapperpaket erstellt haben, können Sie lokalisierte Versionen des Boots Trapper-Pakets erstellen, indem Sie für jedes Gebiets Schema zwei weitere Dateien erstellen: eine Datei mit Software-Lizenzbedingungen (z *. b. "EULA. RTF* ") und ein Paket Manifest ( *package.xml* ).

 Visual Studio 2010 umfasst standardmäßig nur lokalisierte Bootstrapperpakete für .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 und F# Runtime 4.0. Mit den folgenden drei Schritten können Sie lokalisierte Pakete für andere Bootstrapper erstellen.

1. Erstellen Sie einen Ordner, der nach dem Gebiets Schema Namen in *\Programme\Microsoft SDKs\Windows\v7.0a\bootstrapper\packages \\ \<BootstrapperPackageName>* benannt ist.

2. Erstellen Sie eine Datei, die die Softwarelizenzbedingungen für das Bootstrapperpaket enthält, und legen Sie diese in dem neuen Ordner ab.

3. Erstellen Sie ein Paket Manifest mit dem Namen *package.xml* , aktualisieren Sie die Zeichen folgen und die Kultur, und fügen Sie die Datei in den neuen Ordner ein. Wenn Sie bereits ein Bootstrapperpaket von Visual Studio in der Zielsprache erstellt haben, können Sie die Visual Studio-Datei *package.xml* kopieren und in diesem Schritt ändern.

> [!NOTE]
> Wenn Sie ein Setup-Projekt zur Bereitstellung von Anwendungen verwenden, können Sie Ihre Anwendung durch Ändern der **Localization** -Eigenschaft lokalisieren.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>So erstellen Sie ein lokalisiertes Bootstrapperpaket

1. Erstellen Sie einen Ordner mit dem Namen des Gebietsschemas.

     Erstellen Sie auf 32-Bit-Computern den Ordner im Ordner " *\Programme\Microsoft SDKs\Windows\v7.0a\bootstrapper\packages \\ \<BootstrapperPackageName> \\* ".

     Erstellen Sie auf 64-Bit-Computern den Ordner im Ordner *\Program Files (86) \Microsoft SDKs\Windows\v7.0a\bootstrapper\packages \\ \<BootstrapperPackageName> \\* .

     In der folgenden Tabelle sind die Ordnernamen dargestellt, die Sie für die Übereinstimmung mit einem Gebietsschema verwenden können.

    |Gebietsschema|Ordnername|
    |------------|-----------------|
    |Chinesisch (vereinfacht)|zh-Hans|
    |Chinesisch (traditionell)|zh-Hant|
    |Tschechisch|cs|
    |Deutsch|de|
    |Englisch|en|
    |Spanisch|es|
    |Französisch|fr|
    |Italienisch|it|
    |Koreanisch|ko|
    |Japanisch|ja|
    |Polnisch|pl|
    |Portugiesisch (Brasilien)|pt-BR|
    |Russisch|ru|
    |Türkisch|tr|

2. Erstellen Sie eine Datei, die die Softwarelizenzbedingungen für das Bootstrapperpaket enthält, und legen Sie diese in dem neuen Ordner ab.

3. Erstellen Sie ein Paketmanifest mit dem Namen *package.xml* , und legen Sie die Datei in dem neuen Ordner ab. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines Paket Manifests](../deployment/how-to-create-a-package-manifest.md).

4. Aktualisieren Sie den Abschnitt `<Strings>` des Paketmanifests so, dass die Zeichenfolgen die korrekte Sprache für das Gebietsschema aufweisen.

5. Ändern Sie den Wert `<String Name="Culture">` so, dass er mit dem Ordnernamen übereinstimmt.

6. Speichern Sie die *package.xml* Datei.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>So erstellen Sie ein Bootstrapperpaket für .NET Framework 3.5 Service Pack 1 lokalisiert in Französisch

1. Erstellen Sie einen Ordner mit dem Namen " *fr* ". Der Ordnername muss mit dem Gebietsschemanamen übereinstimmen.

     Erstellen Sie auf 32-Bit-Computern den Ordner im Ordner " *\Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\* ".

     Erstellen Sie auf 64-Bit-Computern den Ordner im Ordner *\Program Files (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*.

2. Legen Sie eine lokalisierte Version der Softwarelizenzbedingungen im Ordner *fr* ab.

3. Kopieren Sie die Datei " *\Program Files (x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* " in den Ordner " *fr* ", und öffnen Sie die Datei im XML-Designer.

4. Aktualisieren Sie den Abschnitt `<Strings>` des Paketmanifests so, dass die Fehlerzeichenfolgen auf Französisch sind.

5. Ändern `<String Name="Culture">` Sie den Wert in " *fr* ".

6. Speichern Sie die *package.xml* Datei.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)
- [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)
- [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md)