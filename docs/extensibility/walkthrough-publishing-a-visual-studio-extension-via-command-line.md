---
title: Erweiterung mit Befehlszeile veröffentlichen
description: Erfahren Sie, wie Sie die Befehlszeile verwenden, um eine Erweiterung für den Visual Studio Marketplace zu veröffentlichen, sodass Entwickler nach neuen und aktualisierten Erweiterungen suchen können.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4132d878ff1ec7689be890446a1849577fafd30
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877922"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung über die Befehlszeile

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie eine Visual Studio-Erweiterung mithilfe der Befehlszeile in der Visual Studio Marketplace veröffentlichen. Wenn Sie Ihre Erweiterung zum Marketplace hinzufügen, können Entwickler das Dialogfeld [**Erweiterungen und Updates**](../ide/finding-and-using-visual-studio-extensions.md) verwenden, um dort nach neuen und aktualisierten Erweiterungen zu suchen.

VsixPublisher.exe ist das Befehlszeilen Tool zum Veröffentlichen von Visual Studio-Erweiterungen im Marketplace. Der Zugriff ist über "$ {VSInstallDir}" \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe möglich. Für dieses Tool sind folgende Befehle verfügbar: **Publish**, up **Publisher**, **deletepublisher**, **deleteextension**, **Login**, **Abmelde**.

## <a name="commands"></a>Befehle

### <a name="publish"></a>Veröffentlichen

Veröffentlicht eine Erweiterung im Marketplace. Bei der Erweiterung kann es sich um eine VSIX, eine exe/MSI-Datei oder einen Link handeln. Wenn die Erweiterung bereits mit derselben Version vorhanden ist, wird die Erweiterung überschrieben. Wenn die Erweiterung nicht bereits vorhanden ist, wird eine neue Erweiterung erstellt.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|Nutzlast (erforderlich) | Entweder ein Pfad zur zu veröffentlichenden Nutzlast oder ein Link, der als "Weitere Info-URL" verwendet werden soll. |
|publishmanifest (erforderlich) | Pfad zur zu verwendenden Veröffentlichungs Manifest-Datei. |
|ignorewarning | Liste der Warnungen, die beim Veröffentlichen einer Erweiterung ignoriert werden sollen. Diese Warnungen werden beim Veröffentlichen einer Erweiterung als Befehlszeilen Meldungen angezeigt. (z. b. "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalaccesstoken | Persönliches Zugriffs Token (Pat), das zum Authentifizieren des Verlegers verwendet wird. Wenn keine Angabe erfolgt, wird Pat von den angemeldeten Benutzern abgerufen. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>"kreatepublisher"

Erstellt einen Verleger im Marketplace. Protokolliert auch den Verleger bei zukünftigen Aktionen (z. b. beim Löschen/Veröffentlichen einer Erweiterung) auf dem Computer.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|Display Name (erforderlich) | Anzeige Name des Verlegers. |
|PublisherName (erforderlich) | Der Name des Verlegers (z. b. der Bezeichner). |
|Personal Access Token (erforderlich) | Persönliches Zugriffs Token, das verwendet wird, um den Verleger zu authentifizieren. |
|Kurzbeschreibung | Eine kurze Beschreibung des Verlegers (keine Datei). |
|LongDescription | Eine lange Beschreibung des Verlegers (keine Datei). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletepublisher

Löscht einen Verleger im Marketplace.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|PublisherName (erforderlich) | Der Name des Verlegers (z. b. der Bezeichner). |
|Personal Access Token (erforderlich) | Persönliches Zugriffs Token, das verwendet wird, um den Verleger zu authentifizieren. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteextension

Löscht eine Erweiterung aus dem Marketplace.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|ExtensionName (erforderlich) | Der Name der zu löschenden Erweiterung. |
|PublisherName (erforderlich) | Der Name des Verlegers (z. b. der Bezeichner). |
|personalaccesstoken | Persönliches Zugriffs Token, das verwendet wird, um den Verleger zu authentifizieren. Wenn keine Angabe erfolgt, wird Pat von den angemeldeten Benutzern abgerufen. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Protokolliert einen Verleger auf dem Computer.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|personalaccesstoken (erforderlich | Persönliches Zugriffs Token, das verwendet wird, um den Verleger zu authentifizieren. |
|PublisherName (erforderlich) | Der Name des Verlegers (z. b. der Bezeichner). |
|overwrite | Gibt an, dass jeder vorhandene Verleger mit dem neuen persönlichen Zugriffs Token überschrieben werden soll. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Protokolliert einen Verleger von dem Computer.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|PublisherName (erforderlich) | Der Name des Verlegers (z. b. der Bezeichner). |
|ignoremissingpublisher | Gibt an, dass das Tool nicht fehlerhaft sein sollte, wenn der angegebene Verleger nicht bereits angemeldet ist. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishmanifest-Datei

Eine publishmanifest-Datei wird vom **Publish** -Befehl verwendet. Sie stellt alle Metadaten zu der Erweiterung dar, die der Marketplace kennen muss. Wenn die hoch zuladende Erweiterung aus einer VSIX-Erweiterung besteht, muss für die Identity-Eigenschaft nur der "InternalName"-Wert festgelegt sein. Dies liegt daran, dass der Rest der "Identity"-Eigenschaften aus der vsixmanifest-Datei generiert werden kann. Wenn es sich bei der Erweiterung um eine MSI/exe-oder Link Erweiterung handelt, muss der Benutzer die erforderlichen Felder in der Identity-Eigenschaft angeben. Der Rest des Manifests enthält spezifische Informationen zum Marketplace (z. b. Kategorien, ob Q&A aktiviert ist usw.).

VSIX-Erweiterung publishmanifest-Datei Beispiel:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

Beispiel für MSI/exe oder Link publishmanifest-Datei:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Medienobjekt Dateien

Medienobjekt Dateien können zum Einbetten von Bildern in der Infodatei bereitgestellt werden. Wenn eine Erweiterung z. b. das folgende markdown-Dokument "Übersicht" enthält:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Um "Images/testlogo.png" im vorherigen Beispiel aufzulösen, kann ein Benutzer wie folgt "assetfiles" im Veröffentlichungs Manifest bereitstellen:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Exemplarische Vorgehensweise

### <a name="prerequisites"></a>Voraussetzungen

Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Erstellen einer Visual Studio-Erweiterung

In diesem Fall wird eine standardmäßige VSPackage-Erweiterung verwendet, aber die gleichen Schritte sind für jede Art von Erweiterung gültig.

1. Erstellen Sie ein VSPackage in c# mit dem Namen "testpublish", das über einen Menübefehl verfügt. Weitere Informationen finden Sie unter [Erstellen der ersten Erweiterung: Hallo Welt](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Packen der Erweiterung

1. Aktualisieren Sie das vsixmanifest-Erweiterungs Manifest mit den korrekten Informationen zu Produktname, Autor und Version.

   ![Erweiterungs-vsixmanifest aktualisieren](media/update-extension-vsixmanifest.png)

2. Erstellen Sie die Erweiterung im **Releasemodus** . Nun wird Ihre Erweiterung als VSIX im Ordner "\bin\release" verpackt.

3. Sie können auf die VSIX doppelklicken, um die Installation zu überprüfen.

### <a name="test-the-extension"></a>Testen der Erweiterung

 Bevor Sie die Erweiterung verteilen, erstellen und testen, um sicherzustellen, dass Sie ordnungsgemäß in der experimentellen Instanz von Visual Studio installiert ist.

1. Starten Sie in Visual Studio das Debuggen. , um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie **in der experimentellen Instanz zum Menü Extras** , und klicken Sie dann auf **Erweiterungen und Updates...**. Die Erweiterung testpublish sollte im mittleren Bereich angezeigt und aktiviert werden.

3. Vergewissern Sie sich, dass **im Menü Extras der Befehl** Test angezeigt wird.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Veröffentlichen der Erweiterung im Marketplace über die Befehlszeile

1. Stellen Sie sicher, dass Sie die Releaseversion ihrer Erweiterung erstellt haben und auf dem neuesten Stand sind.

2. Stellen Sie sicher, dass Sie publishmanifest.json-und Overview.MD-Dateien erstellt haben.

3. Öffnen Sie die Befehlszeile, und navigieren Sie zu "$ {VSInstallDir} \vssdk\visualstudiointegration\tools\bin\".

4. Verwenden Sie den folgenden Befehl, um einen neuen Verleger zu erstellen:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Bei erfolgreicher Erstellung des Verlegers wird die folgende Befehlszeilen Meldung angezeigt:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Sie können den erstellten neuen Verleger überprüfen, indem Sie zu [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Verwenden Sie den folgenden Befehl, um eine neue Erweiterung zu veröffentlichen:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Bei erfolgreicher Erstellung des Verlegers wird die folgende Befehlszeilen Meldung angezeigt:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Sie können die neue Erweiterung, die Sie veröffentlicht haben, überprüfen, indem Sie zu [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installieren Sie die Erweiterung aus der Visual Studio Marketplace

Nachdem die Erweiterung veröffentlicht wurde, installieren Sie Sie in Visual Studio und testen Sie dort.

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates...**.

2. Klicken Sie auf **Online** , und suchen Sie nach testpublish.

3. Klicken Sie auf **Download**. Die Erweiterung wird dann für die Installation geplant.

4. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

Sie können die Erweiterung aus dem Visual Studio Marketplace und von Ihrem Computer entfernen.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>So entfernen Sie die Erweiterung über die Befehlszeile aus dem Marketplace

1. Wenn Sie eine Erweiterung entfernen möchten, verwenden Sie den folgenden Befehl:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Nach erfolgreicher Löschung der Erweiterung wird die folgende Befehlszeilen Meldung angezeigt:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung auf dem Computer

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

2. Wählen Sie "myvsixextension" aus, und klicken Sie dann auf **deinstallieren**. Die Erweiterung wird dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.
