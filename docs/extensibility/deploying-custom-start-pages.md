---
title: Bereitstellen von benutzerdefinierten Start Seiten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie benutzerdefinierte Start Seiten mithilfe der VSIX-Bereitstellung oder durch Kopieren der Dateien an die richtigen Speicherorte auf dem Zielcomputer bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 76c2fc23a2b76b48152a4d3d44d687f165abf106
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993886"
---
# <a name="deploy-custom-start-pages"></a>Bereitstellen von benutzerdefinierten Start Seiten

Sie können benutzerdefinierte Start Seiten mithilfe der VSIX-Bereitstellung oder durch Kopieren der Dateien an die richtigen Speicherorte auf dem Zielcomputer bereitstellen.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX-Bereitstellung mithilfe der Projektvorlage für Start Seiten

Wenn Sie eine Startseite mithilfe der Projektvorlage für Startseiten erstellen und dann das Projekt erstellen, erstellt Visual Studio eine *VSIX* -Datei, die Sie verteilen können. Wenn Sie eine Start Seite in einer *VSIX* -Datei packen, stehen Ihnen je nach Zielgruppe die folgenden Optionen für die Bereitstellung zur Verfügung:

- Sie können die *VSIX* -Datei auf einer Netzwerkfreigabe oder auf einer öffentlichen Website ablegen. Wenn jemand die Datei öffnet, wird die Start Seite automatisch installiert.

- Sie können die *VSIX* -Datei auf die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website hochladen, damit Benutzer Sie mithilfe des Erweiterungs- **Managers** installieren können.

Die Projektvorlage für Start Seiten erstellt eine Kopie der standardmäßigen Visual Studio-Startseite, sodass Sie die Kopie ändern und die ursprüngliche beibehalten können.

Sie können die Projektvorlage für Start Seiten mit dem **Erweiterungs-Manager** abrufen oder von der Website herunterladen.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX-Bereitstellung ohne Verwendung der Projektvorlage für Start Seiten
 Eine erfolgreiche VSIX-Bereitstellung erfordert die Installation einer Erweiterung in Ordnern, die vom VSIX-Registrierungsprozess und vom **Erweiterungs-Manager** erkannt werden. Da die Projektvorlage für die Start Seite bereits die richtigen Ordner angibt, empfiehlt es sich, Sie immer dann zu verwenden, wenn Sie eine Erweiterung für die VSIX-Bereitstellung verpacken möchten. Wenn Sie jedoch einen Fall haben, in dem Sie die Vorlage nicht verwenden können, können Sie eine VSIX-Bereitstellung erstellen, ohne Sie zu verwenden.

 Wenn Sie eine VSIX-Bereitstellung ohne die Startseiten-Projektvorlage erstellen möchten, erstellen Sie zunächst eine *VSIX* -Datei für die Startseite auf eine der beiden folgenden Weisen:

- Durch Hinzufügen von benutzerdefinierten Start Seiten Dateien zu einem leeren VSIX-Projekt. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

- Durch manuelles Erstellen einer *VSIX* -Datei. So erstellen Sie eine *VSIX* -Datei manuell:

   1. Erstellen Sie die Datei " *Extension. vsixmanifest* " und die Datei " *[Content_Types]. XML* " in einem neuen Ordner. Weitere Informationen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).

   2. Klicken Sie in Windows Explorer mit der rechten Maustaste auf den Ordner, der die beiden XML-Dateien enthält, klicken Sie auf **Senden an**, und klicken Sie dann auf ZIP-komprimierter Ordner. Benennen Sie die resultierende *ZIP* -Datei in *filename. vsix* um, wobei filename für den Namen der weitervertreibbaren Datei steht, mit der das Paket installiert wird.

Damit Visual Studio eine Start Seite erkennt, muss der `Content Element` des VSIX-Manifests einen enthalten, bei `CustomExtension Element` dem das- `Type` Attribut auf festgelegt ist `"StartPage"` . Eine Startseiten Erweiterung, die mithilfe der VSIX-Bereitstellung installiert wurde, wird in der Liste **Startseite anpassen** auf der Seite **Start** Optionen als **[installierte Erweiterung]** *Erweiterungsname* angezeigt.

Wenn das Start Seiten Paket Assemblys enthält, müssen Sie die Bindungs Pfad Registrierung hinzufügen, damit diese beim Start von Visual Studio verfügbar sind. Stellen Sie zu diesem Zweck sicher, dass das Paket eine *pkgdef* -Datei mit den folgenden Informationen enthält.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>VSIX-Bereitstellung für alle Benutzer
 Erweiterungen, die in VSIX-Paketen bereitgestellt werden, werden standardmäßig nur für den aktuellen Benutzer installiert. Sie können eine Start Seite für alle Benutzer des Ziel Computers installieren, indem Sie eine All-Users-Bereitstellung erstellen.

### <a name="to-create-an-all-users-deployment"></a>So erstellen Sie eine All-Users-Bereitstellung

1. Öffnen Sie die Datei " *Extension. vsixmanifest* " in der Code Ansicht.

2. `Identifier`Fügen Sie im-Element des VSIX-Manifests ein `AllUsers` Element mit dem Wert hinzu `true` .

    ```
    <AllUsers>true</AllUsers>
    ```

     Dies bewirkt, dass der VSIX-Installer Administrator Berechtigungen auffordert und die Dateien dann in " *\common7\ide\Extensions*" installiert.

3. Öffnen Sie die *pkgdef* -Datei.

4. Ändern Sie die *pkgdef* -Datei, um die Standard Startseite unter HKLM festzulegen, indem Sie Folgendes hinzufügen, wobei *mystartpage. XAML* der Name der *XAML* -Datei ist, die Ihre Startseite enthält.

     [$RootKey $ \startpage\standard]

     "URI" = "$PackageFolder $ \\ *mystartpage. XAML*"

     Dies weist Visual Studio an, am neuen Speicherort der Start Seite zu suchen.

## <a name="file-copy-deployment"></a>Datei Kopier Bereitstellung
 Zum Bereitstellen einer benutzerdefinierten Start Seite müssen Sie keine *VSIX* -Datei erstellen. Stattdessen können Sie das Markup und die unterstützenden Dateien direkt in den Ordner " <em>\StartPages" des Benutzers kopieren \* . Auf der Seite *Startseite anpassen</em>* auf der Seite **Start** Optionen werden alle *XAML* -Dateien in diesem Ordner sowie der Pfad angezeigt – beispielsweise *%UserProfile%\My Documents\Visual Studio {Version} \startpages \\ {Dateiname}. XAML*. Wenn die Start Seite Verweise auf private Assemblys enthält, müssen Sie Sie kopieren und in den Ordner * \privateassemblys einfügen \* .

 Zum Verteilen einer Start Seite, die Sie erstellt haben, ohne Sie in einer *VSIX* -Datei zu packen, empfiehlt es sich, eine grundlegende Datei Kopier Strategie zu verwenden, z. b. ein Batch Skript oder eine beliebige andere Bereitstellungs Technologie, mit der Sie die Dateien in die erforderlichen Verzeichnisse einfügen können.

### <a name="to-manually-install-a-custom-start-page"></a>So installieren Sie eine benutzerdefinierte Start Seite manuell

1. Kopieren Sie die *XAML* -Datei, die das Markup der Start Seite enthält, sowie alle unterstützenden Dateien, die keine Assemblys sind, und fügen Sie Sie in den Ordner "* \StartPages" des Benutzers ein \* .

2. Wenn die Start Seite Assemblys erfordert, kopieren Sie Sie, und fügen Sie Sie in ein *. \\ {Visual Studio- \\ Installationsordner} \common7\ide\privateassemblys*.

3. Wählen Sie in der Liste **Startseite anpassen** auf der Seite **Start** Optionen die neue Startseite aus. Weitere Informationen finden Sie unter [Anpassen der Start Seite](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen

- [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)
- [Hinzufügen eines Benutzer Steuer Elements zur Start Seite](../extensibility/adding-user-control-to-the-start-page.md)
