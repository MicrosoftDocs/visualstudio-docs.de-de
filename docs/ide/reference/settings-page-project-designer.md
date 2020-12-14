---
title: Seite „Einstellungen“, Projekt-Designer
description: Hier erfahren Sie, wie Sie über die Seite „Einstellungen“ des Projekt-Designers die Anwendungseinstellungen eines Projekts angeben.
ms.custom: SEO-VS-2020
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b5aa077043b16c01a05e8730bcd2b42719edaf0
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560316"
---
# <a name="settings-page-project-designer"></a>Seite „Einstellungen“, Projekt-Designer

Legen Sie auf der Seite **Einstellungen** des Projekt-Designers die Anwendungseinstellungen eines Projekts fest. Mit den Anwendungseinstellungen können Sie Eigenschafteneinstellungen und andere Informationen für Ihre Anwendung dynamisch speichern und abrufen. Außerdem können Sie benutzerdefinierte Anwendungs- und Benutzereinstellungen auf einem Clientcomputer verwalten. Weitere Informationen finden Sie unter [Verwalten von Anwendungseinstellungen](../managing-application-settings-dotnet.md).

Wählen Sie zum Aufrufen der Seite **Einstellungen** im **Projektmappen-Explorer** einen Projektknoten und anschließend **Projekt** > **Eigenschaften** aus. Wenn der Projekt-Designer angezeigt wird, klicken Sie auf die Registerkarte **Einstellungen**.

## <a name="header-bar"></a>Headerleiste

Die Headerleiste am oberen Rand der Seite **Einstellungen** enthält verschiedene Steuerelemente:

**Synchronize**

Mit **Synchronisieren** werden für die von der Anwendung zur Laufzeit oder beim Debuggen verwendeten Einstellungen im Gültigkeitsbereich des Benutzers die zur Entwurfszeit festgelegten Standardwerte wiederhergestellt. Zum Wiederherstellen der Daten entfernen Sie die zur Laufzeit generierten anwendungsspezifischen Dateien vom Datenträger, nicht aus den Projektdaten.

**Webeinstellungen laden**

Mit **Webeinstellungen laden** wird das Dialogfeld **Anmelden** angezeigt, über das Sie Einstellungen für einen authentifizierten Benutzer oder für anonyme Benutzer laden können. Diese Schaltfläche ist nur aktiviert, wenn Sie auf der Seite **Dienste** Clientanwendungsdienste aktiviert und einen **Speicherort des Webeinstellungsdiensts** festgelegt haben.

**Code anzeigen**

Bei C#-Projekten können Sie mithilfe der Schaltfläche **Code anzeigen** den Code in der Datei *Settings.cs* anzeigen. Mit dieser Datei wird die `Settings`-Klasse definiert, sodass bestimmte Ereignisse für das `Settings`-Objekt verarbeitet werden können. In allen Sprachen außer Visual Basic müssen Sie die `Save`-Methode dieser Wrapperklasse explizit aufrufen, damit die Benutzereinstellungen erhalten bleiben. Hierfür verwenden Sie normalerweise den **Closing**-Ereignishandler des Hauptformulars. Nachfolgend finden Sie ein Beispiel für eine `Save`-Methode:

```csharp
Properties.Settings.Default.Save();
```

Bei Visual Basic-Projekten können Sie mithilfe der Schaltfläche **Code anzeigen** den Code in der Datei *Settings.vb* anzeigen. Mit dieser Datei wird die `MySettings`-Klasse definiert, sodass bestimmte Ereignisse für das `My.Settings`-Objekt verarbeitet werden können. Weitere Informationen über den Zugriff auf Anwendungseinstellungen über das `My.Settings`-Objekt finden Sie unter [Zugreifen auf Anwendungseinstellungen](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings) verfügt.

Weitere Informationen über den Zugriff auf Anwendungseinstellungen finden Sie unter [Anwendungseinstellungen für Windows Forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Zugriffsmodifizierer**

Mithilfe der Schaltfläche **Zugriffsmodifizierer** können Sie die Zugriffsebene der Hilfsprogrammklassen `Properties.Settings` (in C#) oder `My.Settings` (in Visual Basic) festlegen, die von Visual Studio in *Settings.Designer.cs* oder *Settings.Designer.vb* generiert werden.

Bei Visual C#-Projekten kann der Zugriffsmodifizierer **Internal** oder **Public** verwendet werden.

Bei Visual Basic-Projekten kann der Zugriffsmodifizierer **Friend** oder **Public** verwendet werden.

Standardmäßig wird in C# **Internal** und in Visual Basic **Friend** verwendet. Wenn von Visual Studio Hilfsprogrammklassen als **Internal** oder **Friend** generiert werden, haben ausführbare Anwendungen (*EXE*) keinen Zugriff auf die Ressourcen und Einstellungen, die Sie den Klassenbibliotheken (*DLL*-Dateien) hinzugefügt haben. Legen Sie für den Zugriffsmodifizierer **Public** fest, wenn Sie Ressourcen und Einstellungen aus einer Klassenbibliothek freigeben müssen.

Weitere Informationen zu den Hilfsprogrammklassen für Einstellungen finden Sie unter [Verwalten von Anwendungseinstellungen](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Settings grid (Einstellungsraster)

**Settings Grid** (Einstellungsraster) wird zum Konfigurieren von Anwendungseinstellungen verwendet. Dieses Raster enthält die folgenden Spalten:

**Name**

Geben Sie den Namen der Anwendungseinstellung in dieses Feld ein.

**Typ**

Wählen Sie über die Dropdownliste einen Typ für die Einstellung aus. In der Dropdownliste werden die am häufigsten verwendeten Typen angezeigt, wie etwa **String****(Verbindungszeichenfolge)** und **System.Drawing.Font**. Sie können einen anderen Typ auswählen, indem Sie am Ende der Liste **Durchsuchen** und anschließend im Dialogfeld **Typ auswählen** einen Typ auswählen. Nachdem Sie einen Typ ausgewählt haben, wird er den häufig verwendeten Typen in der Dropdownliste hinzugefügt (nur für die aktuelle Projektmappe).

**Bereich**

Wählen Sie **Anwendung** oder **Benutzer** aus.

Einstellungen im Gültigkeitsbereich der Anwendung wie Verbindungszeichenfolgen werden mit der Anwendung verknüpft. Sie können vom Benutzer zur Laufzeit nicht geändert werden.

Einstellungen im Gültigkeitsbereich des Benutzers wie Systemschriftarten sind zur Verwendung für Benutzereinstellungen vorgesehen. Sie können vom Benutzer zur Laufzeit geändert werden.

**Wert**

Die mit der Anwendungseinstellung verknüpften Daten oder Werte. Wenn es sich bei der Einstellung beispielsweise um eine Schriftart handelt, könnte der Wert **Verdana, 9.75pt, style=Bold** lauten.

## <a name="see-also"></a>Weitere Informationen

- [Verwalten von Anwendungseinstellungen](../managing-application-settings-dotnet.md)
- [Zugreifen auf Anwendungseinstellungen (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
