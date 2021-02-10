---
title: ASP.NET Core-Web-App mit Entity Framework und Visual Studio 2019
titleSuffix: ''
description: Informieren Sie sich vor dem Erstellen einer ASP.NET Core-Web-App zuerst anhand dieses Videotutorials und schrittweiser Anleitungen über das Installieren von Visual Studio-2019.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c6cf4429607f8ceb2a3ed4a5a1cb91274a201698
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922797"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Tutorial: Erstellen Ihrer ersten ASP.NET Core-App mithilfe von Entity Framework mit Visual Studio 2019

In diesem Tutorial erstellen Sie eine ASP.NET Core-Web-App, die Daten verwendet, und stellen Sie in Azure bereit. Dieses Tutorial besteht aus den folgenden Schritten:

- [Schritt 1: Installieren von Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Schritt 2: Erstellen Ihrer ersten ASP.NET Core-Web-App](tutorial-aspnet-core-ef-step-02.md)
- [Schritt 3: Arbeiten mit Daten mithilfe von Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Schritt 4: Bereitstellen einer Web-API von Ihrer ASP.NET Core-App aus](tutorial-aspnet-core-ef-step-04.md)
- [Schritt 5: Bereitstellen Ihrer ASP.NET Core-App in Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Schritt 1: Installieren von Visual Studio 2019

Erfahren Sie mit diesem Videotutorial und schrittweisen Anleitungen, wie Sie Visual Studio 2019 installieren. Wenn Sie Visual Studio bereits installiert haben, fahren Sie fort mit [Schritt 2: Erstellen Ihrer ersten ASP.NET Core-Web-App](tutorial-aspnet-core-ef-step-02.md).

_Sehen Sie sich dieses Video an, und gehen Sie zum Installieren von Visual Studio und Erstellen Ihrer ersten ASP.NET Core-App entsprechend vor._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Herunterladen des Installationsprogramms

Unter [visualstudio.com](https://visualstudio.com) finden Sie das Installationsprogramm. Klicken Sie auf den Visual Studio 2019-Link, um den Download zu starten. Um eine kostenlose Version von Visual Studio zu erhalten, wählen Sie „Visual Studio Community“ aus.

## <a name="start-the-installer"></a>Starten des Installationsprogramms

Nachdem der Download abgeschlossen ist, klicken Sie auf **Ausführen**, um das Installationsprogramm zu starten.

![Visual Studio 2019-Installationsprogramm](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Auswählen von Workloads

Visual Studio kann für viele verschiedene Arten der Entwicklung verwendet werden, und Workloads erleichtern Ihnen, alles herunterzuladen, was Sie für die Art von Apps benötigen, die Sie erstellen möchten. Wählen Sie nun die Workloads **ASP.NET und Webentwicklung** und **Plattformübergreifende .NET Core-Entwicklung** aus. Sie können das Installationsprogramm später immer neu starten, um zusätzliche Workloads und Komponenten zu installieren.

![Visual Studio 2019 – Auswählen von Workloads](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Installieren

Klicken Sie auf **Installieren**, lassen Sie das Installationsprogramm herunterladen, und installieren Sie Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Erstmaliges Ausführen von Visual Studio

Visual Studio sollte nach Abschluss des Installationsprogramms automatisch gestartet werden. Sie werden möglicherweise aufgefordert, sich anzumelden, womit einige nützlichen Funktionen verbunden sind, aber im Moment können Sie das auf später verschieben. Als Nächstes können Sie Ihre Einstellungen für Design und Entwicklung auswählen. Nachdem Sie diese Auswahl vorgenommen haben, können Sie mit Ihrem ersten Projekt beginnen. Klicken Sie auf **Neues Projekt erstellen**, und wählen Sie dann **ASP.NET Core-Webanwendung** aus.

![Visual Studio 2019 – Erstellen eines neuen ASP.NET Core-Webanwendungsprojekts](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Untersuchen von ASP.NET Core-Projekttypen

Sie können Ihren Projektnamen und Speicherort und dann **Erstellen** auswählen. Wählen Sie nun die für Ihre ASP.NET Core-Anwendung zu verwendende Vorlage aus. Sie können eine der folgenden Optionen auswählen:

- Leer. Eine leere Projektvorlage, mit der Sie von Grund auf neu starten.
- API. Am besten geeignet für Web-APIs.
- Webanwendung. Eine standardmäßige, mit Razor Pages erstellte ASP.NET Core-Webanwendung.
- Webanwendung (Model View Controller). Eine standardmäßige ASP.NET Core-Webanwendung mit dem Model View Controller-Muster.
- Angular.
- React.js.
- React.js / Redux.
- Razor-Klassenbibliothek. Wird zum Freigeben von Razor-Objekten zwischen Projekten verwendet.

Beachten Sie, dass Sie für die meisten Projektvorlagen auch das Kontrollkästchen zum Aktivieren der Docker-Unterstützung aktivieren können. Sie können auch Authentifizierungsunterstützung hinzufügen, indem Sie auf die Schaltfläche zum Ändern der Authentifizierung klicken. Dort können Sie unter folgenden Optionen wählen:

- Keine Authentifizierung.
- Einzelne Benutzerkonten. Diese werden in einer lokalen oder Azure-basierten Datenbank gespeichert.
- Geschäfts-, Schul- oder Unikonten. Diese Option verwendet Active Directory, Azure AD oder Microsoft 365 für die Authentifizierung.
- Windows-Authentifizierung. Geeignet für Intranetanwendungen.

Wählen Sie die Standardvorlage für Webanwendungen ohne Authentifizierung aus, und klicken Sie auf **Erstellen**.

![Visual Studio 2019 – Auswählen von ASP.NET Core-Projektoptionen](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Nächste Schritte

Im nächsten Video erfahren Sie mehr über Ihr erstes ASP.NET Core-Projekt.

[Tutorial: Erstellen Ihrer ersten ASP.NET Core-Web-App](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Siehe auch

- [Tutorial: Erste Schritte mit C# und ASP.NET Core](tutorial-aspnet-core.md) Ein ausführlicheres Tutorial ohne Video zur exemplarischen Vorgehensweise
