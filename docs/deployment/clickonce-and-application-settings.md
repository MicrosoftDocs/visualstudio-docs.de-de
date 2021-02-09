---
title: ClickOnce und Anwendungseinstellungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Anwendungs Einstellungsdateien in einer ClickOnce-Anwendung funktionieren und wie ClickOnce Einstellungen migriert, wenn der Benutzer auf die nächste Version aktualisiert wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96491dc192b6578abd725d5d69b7c9093e92b20c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896389"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce und Anwendungseinstellungen
Anwendungseinstellungen für Windows Forms erleichtern das Erstellen, speichern und Verwalten von benutzerdefinierten Einstellungen für Anwendungen und Benutzer auf dem Client. Im folgenden Dokument wird beschrieben, wie Anwendungs Einstellungsdateien in einer ClickOnce-Anwendung funktionieren und wie ClickOnce Einstellungen migriert, wenn der Benutzer auf die nächste Version aktualisiert wird.

 Die folgenden Informationen gelten nur für den Standardanbieter für Anwendungseinstellungen, die- <xref:System.Configuration.LocalFileSettingsProvider> Klasse. Wenn Sie einen benutzerdefinierten Anbieter angeben, legt dieser Anbieter fest, wie seine Daten gespeichert werden und wie seine Einstellungen zwischen den Versionen aktualisiert werden. Weitere Informationen zu Anwendungs Einstellungs Anbietern finden Sie unter [Architektur der Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Dateien für Anwendungseinstellungen
 Die Anwendungseinstellungen verbrauchen zwei Dateien: *\<app>.exe.config* und *user.config*, wobei *App* der Name Ihrer Windows Forms Anwendung ist. *user.config* wird auf dem Client erstellt, wenn die Anwendung zum ersten Mal benutzerspezifische Einstellungen speichert. *\<app>.exe.config* hingegen vor der Bereitstellung vorhanden ist, wenn Sie Standardwerte für Einstellungen definieren. Diese Datei wird von Visual Studio automatisch angezeigt, wenn Sie den **Veröffentlichungs** Befehl verwenden. Wenn Sie die ClickOnce-Anwendung mit *Mage.exe* oder *MageUI.exe* erstellen, müssen Sie sicherstellen, dass diese Datei in den anderen Dateien Ihrer Anwendung enthalten ist, wenn Sie das Anwendungs Manifest auffüllen.

 In einer Windows Forms Anwendung, die nicht mit ClickOnce bereitgestellt wird, wird die *\<app>.exe.config* Datei einer Anwendung im Anwendungsverzeichnis gespeichert, während die *user.config* Datei im Ordner " **Dokumente und Einstellungen** " des Benutzers gespeichert wird. In einer ClickOnce-Anwendung befindet sich *\<app>.exe.config* im Anwendungsverzeichnis innerhalb des ClickOnce-Anwendungs Caches, und *user.config* im ClickOnce-Datenverzeichnis für diese Anwendung.

 Unabhängig davon, wie Sie Ihre Anwendung bereitstellen, gewährleisten Anwendungseinstellungen den sicheren Lesezugriff auf *\<app>.exe.config* und den sicheren Lese-/Schreibzugriff auf *user.config*.

 In einer ClickOnce-Anwendung wird die Größe der von Anwendungseinstellungen verwendeten Konfigurationsdateien durch die Größe des ClickOnce-Caches eingeschränkt. Weitere Informationen finden Sie unter [Übersicht über den ClickOnce-Cache](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Versionsupgrades
 Ebenso wie jede Version einer ClickOnce-Anwendung von allen anderen Versionen isoliert ist, werden die Anwendungseinstellungen für eine ClickOnce-Anwendung auch von den Einstellungen für andere Versionen isoliert. Wenn der Benutzer auf eine höhere Version der Anwendung aktualisiert wird, vergleicht die Anwendungseinstellungen die neuesten Versionen (mit der höchsten Nummerierung) mit den Einstellungen, die mit der aktualisierten Version bereitgestellt werden, und führt die Einstellungen in einem neuen Satz von Einstellungsdateien zusammen.

 In der folgenden Tabelle wird beschrieben, wie Anwendungseinstellungen entscheiden, welche Einstellungen kopiert werden sollen.

|Art der Änderung|Upgradeaktion|
|--------------------|--------------------|
|Der *\<app>.exe.config* hinzugefügte Einstellung|Die neue Einstellung wird mit dem *\<app>.exe.config* der aktuellen Version zusammengeführt.|
|Die Einstellung wurde aus *\<app>.exe.config* entfernt.|Die alte Einstellung wird aus der aktuellen Version entfernt *\<app>.exe.config*|
|Der Standardwert der Einstellung wurde geändert. die lokale Einstellung ist in *user.config* weiterhin auf ursprünglicher Standard festgelegt.|Die Einstellung wird mit dem neuen Standardwert in die *user.config* der aktuellen Version zusammengeführt.|
|Der Standardwert der Einstellung wurde geändert. Einstellung ist in *user.config* auf nicht Standard festgelegt.|Die Einstellung wird mit dem *user.config* der aktuellen Version zusammengeführt, wobei der nicht standardmäßige Wert beibehalten wird.|

Wenn Sie Ihre eigene Wrapper Klasse für Anwendungseinstellungen erstellt haben und die Aktualisierungs Logik anpassen möchten, können Sie die-Methode überschreiben <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> .

## <a name="clickonce-and-roaming-settings"></a>ClickOnce-und Roamingeinstellungen
 ClickOnce funktioniert nicht mit den Roamingeinstellungen, mit denen Ihre Einstellungsdatei auf die Computer in einem Netzwerk folgen kann. Wenn Sie Roamingeinstellungen benötigen, müssen Sie entweder einen Anwendungs Einstellungs Anbieter implementieren, der Einstellungen über das Netzwerk speichert, oder eigene benutzerdefinierte Einstellungs Klassen zum Speichern von Einstellungen auf einem Remote Computer entwickeln. Weitere Informationen zu Einstellungs Anbietern finden Sie unter [Architektur der Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)
- [Übersicht über Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Übersicht über den ClickOnce-Cache](../deployment/clickonce-cache-overview.md)
- [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)