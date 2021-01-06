---
title: Migrieren eines Legacy sprach Dienstanbieter | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einen Sprachdienst auf die neueste Version von Visual Studio aktualisieren, indem Sie das Projekt aktualisieren und eine "Source. Extension. vsixmanifest"-Datei hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ced200ff24b17f312e63642c8083f038a6fc6a4d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877831"
---
# <a name="migrating-a-legacy-language-service"></a>Migrieren eines Legacysprachdiensts
Sie können einen Legacy Sprachdienst zu einer späteren Version von Visual Studio migrieren, indem Sie das Projekt aktualisieren und dem Projekt eine Datei vom Typ "Source. Extension. vsixmanifest" hinzufügen. Der Sprachdienst selbst funktioniert weiterhin wie zuvor, da er vom Visual Studio-Editor angepasst wird.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren eines sprach Dienstanbieter finden Sie unter [Editor-und Sprachdienst Erweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrieren einer Visual Studio 2008-Sprachdienst Lösung zu einer späteren Version
 In den folgenden Schritten wird gezeigt, wie ein Visual Studio 2008-Beispiel mit dem Namen regexlanguageservice angepasst wird. Sie finden dieses Beispiel in einer Visual Studio 2008 SDK-Installation im Ordner " *Visual Studio SDK-Installationspfad*\visualstudiointegration\samples\ide\csharp\example.regexlanguageservice\".

> [!IMPORTANT]
> Wenn Ihr Sprachdienst keine Farben definiert, müssen Sie für <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` das VSPackage explizit auf festlegen:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>So migrieren Sie einen Visual Studio 2008-Sprachdienst zu einer späteren Version

1. Installieren Sie die neueren Versionen von Visual Studio und dem Visual Studio SDK. Weitere Informationen zu den Möglichkeiten, das SDK zu installieren, finden Sie unter [Installieren des Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Bearbeiten Sie die Datei regexlangserv. csproj (ohne Sie in Visual Studio zu laden.

     Ersetzen Sie in dem Knoten, der `Import` auf die Datei Microsoft. VSSDK. targets verweist, den Wert durch den folgenden Text.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Speichern Sie die Datei, und schließen Sie Sie.

4. Öffnen Sie die Projekt Mappe "regexlangserv. sln".

5. Das Fenster für das unidirektionale **Upgrade** wird angezeigt. Klicken Sie auf **OK**.

6. Aktualisieren Sie die Projekteigenschaften. Öffnen Sie das **Projekteigenschaften** Fenster, indem Sie den Projekt Knoten im **Projektmappen-Explorer** auswählen, mit der rechten Maustaste klicken und **Eigenschaften** auswählen.

    - Ändern Sie auf der Registerkarte **Anwendung** das **Ziel Framework** in **4.6.1**.

    - Geben Sie auf der Registerkarte **Debuggen** im Feld **externes Programm starten** **\<Visual Studio installation path>\Common7\IDE\devenv.exe. ein.**

         Geben Sie im Feld **Befehlszeilenargumente** den Text/**rootsuffix Exp** ein.

7. Aktualisieren Sie die folgenden Verweise:

    - Entfernen Sie den Verweis auf Microsoft.VisualStudio.Shell.9.0.dll, und fügen Sie dann Verweise auf Microsoft.VisualStudio.Shell.14.0.dll und Microsoft.VisualStudio.Shell.Immutable.11.0.dll hinzu.

    - Entfernen Sie den Verweis auf Microsoft.VisualStudio.Package.LanguageService.9.0.dll, und fügen Sie dann einen Verweis auf Microsoft.VisualStudio.Package.LanguageService.14.0.dll hinzu.

    - Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.10.0.dll hinzu.

8. Öffnen Sie die Datei vspkg.cs, und ändern Sie den Wert des `DefaultRegistryRoot` Attributs in.

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Das ursprüngliche Beispiel registriert nicht seinen Sprachdienst. Daher müssen Sie das folgende Attribut zu vspkg.cs hinzufügen.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Sie müssen eine "Source. Extension. vsixmanifest"-Datei hinzufügen.

    - Kopieren Sie diese Datei aus einer vorhandenen Erweiterung in Ihr Projektverzeichnis. (Eine Möglichkeit, diese Datei zu erstellen, besteht darin, ein VSIX-Projekt zu erstellen (unter **Datei**, auf **neu** und dann auf **Projekt**. Klicken Sie unter Visual Basic oder c# auf **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt** aus.)

    - Fügen Sie Ihrem Projekt die Datei hinzu.

    - Legen Sie in den **Eigenschaften** der Datei den Wert für **Build Action** auf **None** fest.

    - Öffnen Sie die Datei mit dem **VSIX-Manifest-Editor**.

    - Ändern Sie die folgenden Felder:

    - **ID**: regexlangserv

    - **Produkt Name**: regexlangserv

    - **Beschreibung**: ein Sprachdienst für reguläre Ausdrücke.

    - Klicken Sie unter **Assets** auf **New**, wählen Sie den **Typ** **Microsoft. VisualStudio. VSPackage** aus, legen Sie die **Quelle** auf **ein Projekt in der aktuellen Projekt** Mappe fest, und legen Sie dann das **Projekt** auf **regexlangserv** fest.

    - Speichern und schließen Sie die Datei.

11. Erstellen Sie die Projektmappe. Die erstellten Dateien werden unter **%UserProfile%\appdata\local\microsoft\visualstudio\14.0exp\extensions\msit\ regexlangserv \\** bereitgestellt.

12. Beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio wurde geöffnet.

## <a name="see-also"></a>Weitere Informationen
- [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)
