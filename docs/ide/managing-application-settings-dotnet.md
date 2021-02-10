---
title: Verwalten von Anwendungseinstellungen (.NET)
description: Erfahren Sie, wie Sie Anwendungseinstellungen (früher als dynamische Eigenschaften bezeichnet) verwalten können, die nicht im Anwendungscode enthalten sind, aber zur Laufzeit benötigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: acfaf1f74f856bb90bfc16cacef20579abdcf8c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886560"
---
# <a name="manage-application-settings-net"></a>Verwalten von Anwendungseinstellungen (.NET)

Anwendungseinstellungen ermöglichen ein dynamisches Speichern von Anwendungsinformationen. Mit Einstellungen können Sie Informationen über den Clientcomputer speichern, die nicht im Anwendungscode enthalten sein sollen (beispielsweise eine Verbindungszeichenfolge). Außerdem können Benutzereinstellungen und andere zur Laufzeit benötigte Informationen gespeichert werden.

Durch Anwendungseinstellungen werden die dynamischen Eigenschaften ersetzt, die in früheren Versionen von Visual Studio verwendet wurden.

Jede Anwendungseinstellung muss einen eindeutigen Namen haben. Dieser Name kann aus einer beliebigen Kombination aus Buchstaben, Zahlen und Unterstrichen bestehen. Er darf jedoch nicht mit einer Zahl beginnen, und er darf keine Leerzeichen enthalten. Der Name wird über die `Name`-Eigenschaft geändert.

Anwendungseinstellungen können als ein beliebiger Datentyp gespeichert werden, der in XML serialisierbar ist oder über einen `TypeConverter` mit einer Implementierung von `ToString`/`FromString` verfügt. Die geläufigsten Typen lauten `String`, `Integer`und `Boolean`. Sie können Werte jedoch auch als <xref:System.Drawing.Color>, <xref:System.Object>oder als Verbindungszeichenfolge speichern.

Anwendungseinstellungen enthalten auch einen Wert. Der Wert wird über die Eigenschaft **Wert** festgelegt und muss mit dem Datentyp der Einstellung übereinstimmen.

Außerdem können Anwendungseinstellungen zur Entwurfszeit an die Eigenschaft eines Formulars oder Steuerelements gebunden werden.

Es gibt zwei Typen von Anwendungseinstellungen, die sich hinsichtlich ihres Gültigkeitsbereichs unterscheiden:

- Anwendungsspezifische Einstellungen können für Informationen wie die URL eines Webdiensts oder eine Datenbankverbindungszeichenfolge verwendet werden. Diese Werte werden der Anwendung zugeordnet. Deshalb können Benutzer sie zur Laufzeit nicht ändern.

- Benutzerspezifische Einstellungen können für Informationen, z. B. die Beibehaltung der letzten Position eines Formulars oder eine Schriftarteinstellung, verwendet werden. Die Benutzer können diese Werte zur Laufzeit ändern.

Sie können den Typ einer Einstellung mit der Eigenschaft **Bereich** ändern.

Anwendungseinstellungen werden im Projektsystem in zwei XML-Dateien gespeichert:

- In einer *app.config*-Datei, die zur Entwurfszeit bei der Erstellung der ersten Anwendungseinstellung erstellt wird

- In einer *user.config*-Datei, die zur Laufzeit erstellt wird, wenn der Benutzer, der die Anwendung ausführt, den Wert einer Benutzereinstellung ändert.

Beachten Sie, dass Änderungen in den Benutzereinstellungen nicht auf die Festplatte geschrieben werden, es sei denn, die Anwendung ruft ausdrücklich eine Methode auf, die dies veranlasst.

## <a name="create-application-settings-at-design-time"></a>Erstellen von Anwendungseinstellungen zur Entwurfszeit

Zur Entwurfszeit können Anwendungseinstellungen auf zwei Arten erstellt werden: im **Projekt-Designer** über die Seite **Einstellungen** oder für ein Formular oder ein Steuerelement über das **Eigenschaftenfenster** , in dem Sie eine Einstellung an eine Eigenschaft binden können.

Beim Erstellen einer anwendungsspezifischen Einstellung (z.B. einer Datenbankverbindungszeichenfolge oder eines Verweises auf Serverressourcen) speichert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] diese Einstellung in *app.config* mit dem `<applicationSettings>`-Tag. (Verbindungszeichenfolgen werden unter dem `<connectionStrings>` -Tag gespeichert.)

Beim Erstellen einer benutzerspezifischen Einstellung (z.B. einer Standardschriftart, Startseite oder Fenstergröße) speichert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] diese Einstellung in *app.config* mit dem `<userSettings>`-Tag.

> [!IMPORTANT]
> Beim Speichern von Verbindungszeichenfolgen in *app.config* sollten Sie Vorsichtsmaßnahmen ergreifen, damit keine vertraulichen Informationen, etwa Kennwörter oder Serverpfade, in der Verbindungszeichenfolge preisgegeben werden.
>
> Wenn Sie Informationen für Verbindungszeichenfolgen aus einer externen Quelle übernehmen (z. B. bei Eingabe einer Benutzer-ID und eines Kennworts durch einen Benutzer), müssen Sie sicherstellen, dass die Werte zum Aufbau der Verbindungszeichenfolge keine zusätzlichen Parameter für Verbindungszeichenfolgen enthalten, die das Verhalten der Verbindung ändern oder ihre Sicherheit gefährden.
>
> Verwenden Sie am besten die geschützte Konfiguration, um vertrauliche Informationen in der Konfigurationsdatei zu verschlüsseln. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Da für Klassenbibliotheken das Modell der Konfigurationsdateien nicht verwendet wird, gelten Anwendungseinstellungen nicht für Klassenbibliotheksprojekte. Ausgenommen hiervon sind DLL-Projekte in Visual Studio Tools for Office, die über Konfigurationsdateien verfügen können.

## <a name="use-customized-settings-files"></a>Verwenden von Dateien mit benutzerdefinierten Einstellungen

Sie können dem Projekt zur einfachen Verwaltung von Einstellungsgruppen benutzerdefinierte Einstellungsdateien hinzufügen. Einstellungen, die in einer Datei enthalten sind, werden als Einheit geladen und gespeichert. Durch das Speichern von Einstellungen für häufig und weniger häufig verwendete Gruppen in separaten Dateien können Sie beim Laden und Speichern von Einstellungen Zeit sparen.

Beispielsweise können Sie dem Projekt eine Datei namens *SpecialSettings.settings* hinzufügen. Die `SpecialSettings` -Klasse wird zwar im `My` -Namespace nicht verfügbar gemacht, mit **Code anzeigen** kann jedoch die benutzerdefinierte Einstellungsdatei, die `Partial Class SpecialSettings`enthält, gelesen werden.

Zunächst sucht der **Einstellungs-Designer** nach der vom Projektsystem erstellten Datei *Settings.settings*. Dies ist die Standarddatei, die im **Projekt-Designer** auf der Registerkarte **Einstellungen** angezeigt wird. *Settings.settings* befindet sich bei [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekten im Ordner *My Project* (Mein Projekt) und bei [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekten im Ordner *Eigenschaften*. Der **Projekt-Designer** sucht dann nach anderen Einstellungsdateien im Stammordner des Projekts. Deshalb sollten Sie die benutzerdefinierte Einstellungsdatei dort ablegen. Wenn Sie die *SETTINGS*-Datei einem anderen Projektordner hinzufügen, findet der **Projekt-Designer** sie nicht.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Zugreifen auf oder Ändern von Anwendungseinstellungen in Visual Basic zur Laufzeit

In Visual Studio-Projekten können Sie mit dem `My.Settings`-Objekt zur Laufzeit auf Anwendungseinstellungen zugreifen. Klicken Sie auf der Seite **Einstellungen** auf die Schaltfläche **Code anzeigen**, um die Datei *Settings.vb* anzuzeigen. *Settings.vb* definiert die `Settings`-Klasse, sodass Sie die folgenden Ereignisse für die Settings-Klasse verarbeiten können: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> und <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Beachten Sie, dass die `Settings`-Klasse in der Datei *Settings.vb* eine partielle Klasse ist, die nur den im Besitz des Benutzers befindlichen Code anzeigt und nicht die gesamte generierte Klasse. Weitere Informationen über den Zugriff auf Anwendungseinstellungen über das `My.Settings`-Objekt finden Sie unter [Zugreifen auf Anwendungseinstellungen (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Die Werte aller benutzerspezifischen Einstellungen, die der Benutzer zur Laufzeit ändert (z.B. die Position eines Formulars), werden in der Datei *user.config* gespeichert. Beachten Sie, dass die Standardwerte weiterhin in *app.config* gespeichert sind.

Wenn benutzerspezifische Einstellungen zur Laufzeit geändert wurden, z.B. beim Testen der Anwendung, und Sie diese Einstellungen auf die Standardwerte zurücksetzen möchten, klicken Sie auf die Schaltfläche **Synchronisieren**.

Es wird dringend empfohlen, dass Sie mit dem `My.Settings`-Objekt und der *SETTINGS*-Standarddatei auf Einstellungen zugreifen. Dies ist deshalb wichtig, da Sie mithilfe des **Einstellungs-Designers** den Einstellungen Eigenschaften zuweisen können und Benutzereinstellungen vor dem Beenden der Anwendung automatisch gespeichert werden. Die Visual Basic-Anwendung kann jedoch direkt auf Einstellungen zugreifen. In diesem Fall müssen Sie die `MySettings`-Klasse aufrufen und eine benutzerdefinierte *SETTINGS*-Datei im Stammordner des Projekts verwenden. Sie müssen die Benutzereinstellungen wie bei einer C#-Anwendung vor dem Beenden der Anwendung speichern. Informationen hierzu finden Sie im folgenden Abschnitt.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Zugreifen auf oder Ändern von Anwendungseinstellungen in C# zur Laufzeit
<!-- markdownlint-enable MD003 MD020 -->

In Programmiersprachen außer Visual Basic, z.B. in C#, müssen Sie direkt auf die `Settings`-Klasse zugreifen. Dies wird im folgenden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Beispiel veranschaulicht.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Sie müssen die `Save`-Methode dieser Wrapperklasse explizit aufrufen, damit die Benutzereinstellungen erhalten bleiben. Hierfür verwenden Sie normalerweise den `Closing` -Ereignishandler des Hauptformulars. Im folgenden C#-Beispiel wird einen Aufruf der `Save`-Methode gezeigt.

```csharp
Properties.Settings.Default.Save();
```

Allgemeine Informationen zum Zugriff auf Anwendungseinstellungen über die `Settings`-Klasse finden Sie unter [Übersicht über Anwendungseinstellungen (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Informationen über das Durchlaufen der Einstellungen finden Sie in diesem [Forumsbeitrag](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf Anwendungseinstellungen (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
