---
title: Webbrowser, Umgebung, Dialogfeld "Optionen"
description: Hier erfahren Sie, wie Sie über die Seite „Webbrowser“ im Abschnitt „Umgebung“ Optionen für den internen Webbrowser und Internet Explorer festlegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Environment.Web Browser
- VS.ToolsOptionsPages.Environment.WebBrowser
- VS.ToolsOptionsPages.Environment.Web_Browser
helpviewer_keywords:
- browsers, customizing
- searching, search page for Web browser
- Web browsers, customizing
- searches, default Web browser search page
- URLs, specifying VS home page
- home page
- Options dialog box, Web settings
- Internet Explorer, setting options
ms.assetid: 586db4eb-032d-4cb5-93a6-a7c14de1ae49
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2898984896ef96f9e7767e0c56ad58c92be42f54
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560927"
---
# <a name="options-dialog-box-environment--web-browser"></a>Dialogfeld „Optionen“: Umgebung \> Webbrowser

Legt Optionen sowohl für den internen Webbrowser als auch für Internet Explorer fest. Klicken Sie zum Öffnen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Umgebung**, und klicken Sie dann auf **Webbrowser**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../environment-settings.md#reset-settings).

> [!IMPORTANT]
> Durch Öffnen bestimmter Webdateien oder -komponenten kann auf Ihrem Computer Code ausgeführt werden.

## <a name="home-page"></a>Startseite

Legt die Seite fest, die beim Öffnen des IDE-Webbrowsers angezeigt wird.

## <a name="search-page"></a>Seite „Search“

Hier können Sie eine Suchseite für den internen Webbrowser festlegen. Diese Adresse kann sich von der Suchseite unterscheiden, die von Internet Explorer-Instanzen verwendet wird, die außerhalb der integrierten Entwicklungsumgebung (IDE) gestartet wurden.

## <a name="view-source-in"></a>Quelltext anzeigen in

Legt den Editor fest, der zum Öffnen einer Website verwendet wird, wenn Sie den Befehl **Quelltext anzeigen** auf der im internen Webbrowser angezeigten Seite wählen.

- **Quellcode-Editor** Wählen Sie diese Option zum Anzeigen von Quellcode im [Editor](../../ide/writing-code-in-the-code-and-text-editor.md) aus.

- **HTML-Editor** Wählen Sie diese Option zum Anzeigen von Quellcode im [HTML-Designer](/previous-versions/ex0hkwbx(v=vs.140)) aus. Verwenden Sie diese Option, wenn Sie die Website in einer von zwei Ansichten bearbeiten möchten: In der Entwurfsansicht oder in der Standardtext-Quellansicht.

- **Externer Editor** Wählen Sie diese Option zum Anzeigen von Quellcode in einem anderen Editor aus. Geben Sie den Pfad eines beliebigen Editors an, z.B. Notepad.exe.

## <a name="internet-explorer-options"></a>Internet Explorer-Optionen

Klicken Sie hier, um im Dialogfeld **Interneteigenschaften** Optionen für Internet Explorer zu ändern. Änderungen, die in diesem Dialogfeld vorgenommen werden, wirken sich sowohl auf den internen Webbrowser als auch auf die Internet Explorer-Instanzen aus, die außerhalb der Visual Studio-IDE (z.B. über das Startmenü) gestartet wurden.

> [!NOTE]
> Im Dialogfeld **Browse with** (Durchsuchen mit) können Sie den internen Webbrowser von Visual Studio durch einen Browser Ihrer Wahl ersetzen. Für das Öffnen des Dialogfelds „“ haben Sie zwei Optionen: Klicken Sie entweder mit der rechten Maustaste auf z.B. eine HTML-Datei in Ihrem Projekt, oder öffnen Sie deren Kontextmenü.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
- [HTML-Designer](/previous-versions/ex0hkwbx(v=vs.140))