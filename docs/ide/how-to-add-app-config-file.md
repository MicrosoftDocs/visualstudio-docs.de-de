---
title: So fügen Sie einem Projekt die Datei „app.config“ hinzu
description: Lernen Sie, einem C#-Projekt eine app.config-Datei hinzuzufügen, um anzupassen, wie die Common Language Runtime-Assemblydateien sucht und lädt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e9280451d7841755cb3085726843bf6fc1443f8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948282"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Vorgehensweise: Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt

Durch Hinzufügen einer Anwendungskonfigurationsdatei (*app.config*) zu einem C#-Projekt können Sie anpassen, wie die Common Language Runtime Assemblydateien sucht und lädt. Weitere Informationen zu Anwendungskonfigurationsdateien finden Sie unter [So sucht die Common Language Runtime nach Assemblys (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> UWP-Apps enthalten keine Datei namens *app.config*.

Bei der Projekterstellung kopiert die Entwicklungsumgebung automatisch die Datei *app.config*, ändert den Dateinamen der Kopie entsprechend Ihrer ausführbaren Datei und verschiebt die Kopie dann in das **bin**-Verzeichnis.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt

1. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Erweitern Sie **Installiert** > **Visual C#-Elemente**, und wählen Sie dann die Vorlage **Anwendungskonfigurationsdatei**.

1. Geben Sie im Textfeld **Name** einen Namen ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.

     Eine Datei namens *app.config* wird Ihrem Projekt hinzugefügt.

## <a name="see-also"></a>Weitere Informationen

- [Verwalten von Anwendungseinstellungen (.NET)](../ide/managing-application-settings-dotnet.md)
- [Konfigurationsdateischema (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurieren von Apps (.NET Framework)](/dotnet/framework/configure-apps/index)
