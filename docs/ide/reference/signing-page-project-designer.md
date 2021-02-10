---
title: Seite "Signierung", Projekt-Designer
description: In diesem Artikel verwenden Sie die Seite „Signierung“ des Projekt-Designers, um das Anwendungs- und das Bereitstellungsmanifest sowie die Assembly zu signieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52d02407316fbc8f9a7b5e3db1c02a3566cda87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957581"
---
# <a name="signing-page-project-designer"></a>Seite "Signierung", Projekt-Designer

Verwenden Sie die Seite **Signierung** des **Projekt-Designers**, um die Anwendungs- und Bereitstellungsmanifeste zu signieren. Außerdem können sie damit die Assembly signieren (Signierung mit starkem Namen).

Bitte beachten Sie, dass das Signieren von Anwendungs- und Bereitstellungsmanifesten sich vom Signieren von Assemblys unterscheidet, obwohl beide Aufgaben von der Seite **Signierung** aus durchgeführt werden.

Außerdem unterscheidet sich das Speichern von Schlüsseldateiinformationen für das Signieren von Manifesten von dem von Assemblys. Bei der Signierung von Manifesten werden Schlüsselinformationen in der kryptografischen Speicherdatenbank ihres Computers und dem Windows-Zertifikat des aktuellen Benutzers gespeichert. Bei der Signierung von Assemblys werden Schlüsselinformationen hingegen nur in der kryptografischen Speicherdatenbank Ihres Computers gespeichert.

Wählen Sie zum Aufrufen der Seite **Signierung** im **Projektmappenexplorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Signierung**.

## <a name="application-and-deployment-manifest-signing"></a>Signierung von Anwendungs- und Bereitstellungsmanifesten

Kontrollkästchen **ClickOnce-Manifeste signieren**

Setzen Sie in diesem Kontrollkästchen ein Häkchen, wenn Sie Anwendungs- und Bereitstellungsmanifeste mit einem öffentlichen bzw. privaten Schlüsselpaar signieren möchten. Weitere Informationen hierzu finden Sie unter [Vorgehensweise: Signieren von Anwendungs- und Bereitstellungsmanifesten](../../ide/how-to-sign-application-and-deployment-manifests.md).

Schaltfläche **Aus Speicher auswählen**

Gibt Ihnen die Möglichkeit, ein vorhandenes Zertifikat aus dem persönlichen Zertifikatspeicher des aktuellen Benutzers auszuwählen. Eines dieser Zertifikate können Sie für die Signierung Ihrer Anwendungs- und Bereitstellungsmanifeste benutzen.

Wenn Sie auf **Aus Speicher auswählen** klicken, wird das Dialogfeld **Zertifikat auswählen** geöffnet, in dem die Zertifikate in Ihrem persönlichen Zertifikatspeicher aufgelistet werden, die aktuell gültig – d.h. nicht abgelaufen – sind, und die private Schlüssel aufweisen. Der Zweck des von Ihnen ausgewählten Zertifikats sollte eine Codesignatur enthalten.

Wenn Sie auf **Zertifikateigenschaften anzeigen** klicken, wird das Dialogfeld **Zertifikatdetails** geöffnet. Dieses Dialogfeld enthält ausführliche Informationen zu dem Zertifikat sowie zusätzliche Optionen. Sie können auf **Learn more about certificates (Weitere Informationen zu Zertifikaten)** klicken, um weitere Hilfeinformationen anzuzeigen.

Schaltfläche **Aus Datei auswählen**

Gibt Ihnen die Möglichkeit, ein Zertifikat aus einer vorhandenen Schlüsseldatei auszuwählen.

Wenn Sie auf **Aus Datei auswählen** klicken, öffnet sich das Dialogfeld **Datei auswählen**, über das Sie eine Zertifikatschlüsseldatei (.pfx) auswählen können. Die Datei muss kennwortgeschützt sein und darf sich nicht bereits in Ihrem persönlichen Zertifikatspeicher befinden.

Geben Sie im Dialogfeld **Kennwort zum Öffnen der Datei eingeben** ein Kennwort ein, um die Zertifikatschlüsseldatei (.pfx) zu öffnen. Informationen zum Kennwort sind in Ihrer persönlichen Schlüsselcontainerliste und Ihrem persönlichen Zertifikatspeicher gespeichert.

Schaltfläche **Testzertifikat erstellen**

Gibt Ihnen die Möglichkeit, ein Testzertifikat zu erstellen. Das Testzertifikat wird für die Signierung Ihrer ClickOnce-Anwendungs- und Bereitstellungsmanifesten verwendet.

Wenn Sie auf **Testzertifikat erstellen** klicken, wird das Dialogfeld **Testzertifikat erstellen** aufgerufen, wo Sie ein Kennwort für die Schlüsseldatei mit starkem Namen für das Testzertifikat eingeben können. Die Datei heißt *Projektname* _TemporaryKey.pfx. Wenn Sie auf **OK** klicken, ohne ein Kennwort einzugeben, ist die .pfx-Datei nicht kennwortverschlüsselt.

Feld **Timestampserver-URL**

Gibt die Adresse des Servers an, der Ihre Signatur mit einem Zeitstempel versieht. Wenn Sie ein Zertifikat bereitstellen, überprüft diese externe Seite den Zeitpunkt, zu dem die Anwendung signiert wurde.

## <a name="assembly-signing"></a>Signieren von Assemblys

Kontrollkästchen **Assembly signieren**

Setzen Sie ein Häkchen in diesem Kontrollkästchen, um die Assembly zu signieren und eine Schlüsseldatei mit starkem Namen zu erstellen. Weitere Informationen zum Signieren von Assemblys mithilfe von **Projekt-Designer** finden Sie unter [Vorgehensweise: Signieren von Assemblys (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio).

Diese Option verwendet das Tool „AI.exe“, das vom Windows Software Development Kit (SDK) zum Signieren der Assembly bereitgestellt wird. Weitere Informationen zu diesem Tool erhalten Sie im Artikel [Vorgehensweise: Signieren einer Assembly mit einem starken Namen](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

Liste **Schlüsseldatei mit starkem Namen auswählen**

Gibt Ihnen die Möglichkeit, eine neue oder bereits vorhandene Schlüsseldatei mit starkem Namen festzulegen, die verwendet wird, um die Assembly zu signieren. Klicken Sie auf **\<Browse...>** , um eine vorhandene Schlüsseldatei auszuwählen.

Klicken Sie auf **\<New...>** , um eine neue Schlüsseldatei zu erstellen, mit der die Assembly signiert werden soll. Das Dialogfeld **Schlüssel für einen starken Namen erstellen** wird geöffnet, in dem Sie einen Namen für die Schlüsseldatei angeben und die Schlüsseldatei durch ein Kennwort schützen können. Das Kennwort muss mindestens eine Länge von 6 Zeichen aufweisen. Wenn Sie ein Kennwort angeben, wird eine Personal Information Exchange-Datei (.pfx) erstellt; wenn Sie kein Kennwort angeben, wird eine Schlüsseldatei mit starkem Namen (.snk) erstellt.

Schaltfläche **Kennwort ändern**

Ändert das Kennwort der Personal Information Exchange-Datei (.pfx), mit der Sie die Assembly signieren.

Wenn Sie auf **Kennwort ändern** klicken, wird das Dialogfeld **Schlüsselkenntwort ändern** geöffnet. In diesem Dialogfeld ist das **alte Kennwort** das aktuelle Kennwort der Schlüsseldatei. Das **neue Kennwort** muss mindestens eine Länge von 6 Zeichen aufweisen. Informationen zum Kennwort werden im Windows-Zertifikatspeicher des aktuellen Benutzers gespeichert.

Kontrollkästchen **Nur verzögerte Signierung**

Setzen Sie ein Häkchen in diesem Kontrollkästchen, um die verzögerte Signierung zu aktivieren.

Bitte beachten Sie, dass ein verzögert signiertes Projekt nicht ausgeführt wird und auch nicht debuggt werden kann. Allerdings können Sie das [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool) mit der Option `-Vr` verwenden, um das Überprüfen während der Entwicklung zu überspringen.

> [!NOTE]
> Beim Signieren einer Assembly haben Sie möglicherweise nicht immer Zugriff auf einen privaten Schlüssel. Eine Organisation kann z.B. ein streng geheim gehaltenes Schlüsselpaar verwenden, auf das Entwickler nicht täglich zugreifen können. Möglicherweise steht der öffentliche Schlüssel zur Verfügung, während der Zugriff auf den privaten Schlüssel nur einigen Wenigen erlaubt ist. In einem solchen Fall können Sie die *verzögerte* oder *Teilsignierung* verwenden, um den öffentlichen Schlüssel bereitzustellen. Dadurch wird das Hinzufügen des privaten Schlüssels solange verzögert, bis die Assembly übergeben wird.

## <a name="see-also"></a>Siehe auch

- [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)
- [Verwalten der Signierung von Assemblys und Manifesten](../../ide/managing-assembly-and-manifest-signing.md)
- [How to: Signieren von Anwendungs- und Bereitstellungsmanifesten](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [How to: Signieren einer Assembly (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [How to: Signieren einer Assembly mit einem starken Namen](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Assemblys mit starkem Namen](/dotnet/framework/app-domains/strong-named-assemblies)
