---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mithilfe der VSPackage-Projektvorlage einen einfachen benutzerdefinierten Editor in C++ erstellen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 188c02471e8921e66faefe9668ec3f54c935b50b
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863124"
---
# <a name="walkthrough-create-a-custom-editor"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors
Die VSPackage-Projektvorlage kann einen einfachen benutzerdefinierten Editor in C++ erstellen. Die VSPackage-Projektvorlage unterstützt nicht mehr c#-oder Visual Basic-Projekte. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Die Projektvorlage für das Visual Studio-Paket
 Sie finden die Projektvorlage für das Visual Studio-Paket im Dialogfeld " **Neues Projekt** " unter dem Ordner " **C++ Extensibility** ".

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>So erstellen Sie ein VSPackage mithilfe der Visual Studio-Paket Vorlage

1. Erstellen Sie ein Projekt mit der Visual Studio-Paket Vorlage.

2. Wählen Sie die Option **benutzerdefinierter Editor** , und klicken Sie auf **weiter**. Die Seite **Editor-Optionen** wird angezeigt.

3. Geben Sie den Namen des Editors in das Feld **Editor Name** ein. Geben Sie im Feld **Dateierweiterung** die Dateierweiterung ein, die dem Editor zugeordnet werden soll. Der Editor ist für Dateien mit dieser Erweiterung verfügbar. Die Dateierweiterung ist nur für Visual Studio registriert, nicht für Windows. Geben Sie im Feld **Standard Dateiname** den Standard Dateinamen für neue Dokumente ein, die mit Ihrem Editor erstellt wurden.

4. Klicken Sie auf **Fertig stellen** , um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.

### <a name="to-test-your-custom-editor"></a>So testen Sie den benutzerdefinierten Editor

1. Zeigen Sie im Menü **Datei** auf **neu** , und klicken Sie dann auf **Datei**.

2. Wählen Sie im Bereich **installierte Vorlagen** des Dialog Felds **neue Datei** die Datei Vorlage aus, und wählen Sie dann den Dateityp aus, den Sie registriert haben.

3. Klicken Sie auf **Öffnen** , um das Dokument anzuzeigen und zu bearbeiten.

     Der Editor unterstützt Ausschneide-und Einfügevorgänge, Find-and-Replace-und Open-and-Load-Vorgänge.

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
