---
title: 'Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen'
description: Erfahren Sie, wie Sie Verbindungs Zeichenfolgen in Visual Studio-Anwendungen speichern und bearbeiten. Speichern oder bearbeiten Sie eine Verbindungs Zeichenfolge direkt in den Anwendungseinstellungen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 18d1da27faed67b90658ea4479f1e2e9a11ead4a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436288"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Vorgehensweise: Speichern und Bearbeiten von Verbindungszeichenfolgen
Verbindungs Zeichenfolgen in Visual Studio-Anwendungen werden in der Anwendungs Konfigurationsdatei (auch als Anwendungseinstellungen bezeichnet) oder direkt in der Anwendung gespeichert. Das Speichern von Verbindungszeichenfolgen in der Anwendungskonfigurationsdatei vereinfacht das Verwalten der Anwendung. Wenn die Verbindungszeichenfolge geändert werden muss, können Sie dies in der Datei mit den Anwendungseinstellungen durchführen (und müssen nicht den Quellcode ändern und die Anwendung dann neu kompilieren).

Das Speichern vertraulicher Informationen (z. B. das Kennwort) in der Verbindungszeichenfolge kann sich auf die Sicherheit der Anwendung auswirken. In der Anwendungskonfigurationsdatei gespeicherte Verbindungszeichenfolgen sind nicht verschlüsselt oder verborgen, sodass es möglich ist, dass jemand auf die Datei zugreift und ihre Inhalte liest. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.

Wenn Sie nicht die integrierte Sicherheit von Windows wählen und die Datenbank einen Benutzernamen und ein Kennwort erfordert, können Sie diese aus der Verbindungszeichenfolge weglassen. Die Anwendung muss diese Informationen aber für eine Verbindung zur Datenbank liefern. Sie können beispielsweise ein Dialogfeld erstellen, dass den Benutzer zur Eingabe dieser Informationen auffordert und dynamisch während der Laufzeit die Verbindungszeichenfolge erstellt. Die Sicherheit kann immer noch ein Problem darstellen, wenn die Informationen auf dem Weg zur Datenbank abgefangen werden.
Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>So speichern Sie eine Verbindungs Zeichenfolge innerhalb des Assistenten zum Konfigurieren von Datenquellen
Wählen Sie im **Assistenten zum Konfigurieren von Datenquellen** die Option zum Speichern der Verbindung auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** aus.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>So speichern Sie eine Verbindungszeichenfolge direkt in den Anwendungseinstellungen
1. Doppelklicken Sie im **Projektmappen-Explorer** auf das Symbol **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), um den **Projekt-Designer** zu öffnen.
1. Wählen Sie die Registerkarte **Einstellungen** aus.
1. Geben Sie einen **Namen** für die Verbindungszeichenfolge ein. Verweisen Sie beim Zugriff auf die Verbindungszeichenfolge im Code auf diesen Namen.
1. Legen Sie den **Typ** auf ( **Verbindungszeichenfolge** ) fest.
1. Lassen Sie den **Bereich** auf **Anwendung** eingestellt.
1. Geben Sie im **Feld Wert die** Verbindungs Zeichenfolge ein, oder klicken Sie im Feld **Wert** auf die Schaltfläche mit den Auslassungs Punkten (...), um das Dialogfeld **Verbindungs Eigenschaften** zu öffnen **und die Verbindungs** Zeichenfolge zu erstellen

## <a name="edit-connection-strings-stored-in-application-settings"></a>In Anwendungseinstellungen gespeicherte Verbindungs Zeichenfolgen bearbeiten
Sie können mithilfe des **Projekt-Designers** die Verbindungsinformationen ändern, die in den Anwendungseinstellungen geändert sind.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>So bearbeiten Sie eine Verbindungszeichenfolge, die in den Anwendungseinstellungen gespeichert ist
1. Doppelklicken Sie im **Projektmappen-Explorer** auf das Symbol **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), um den **Projekt-Designer** zu öffnen.
1. Wählen Sie die Registerkarte **Einstellungen** aus.
1. Suchen Sie die Verbindung, die Sie bearbeiten möchten, und wählen Sie den Text im Feld **Wert** aus.
1. Bearbeiten Sie die Verbindungs Zeichenfolge im Feld **Wert** , oder klicken Sie im Feld **Wert** auf die Schaltfläche mit den Auslassungs **Punkten (.** ..), um die Verbindung mit dem Dialogfeld **Verbindungs Eigenschaften** zu bearbeiten.

## <a name="edit-connection-strings-for-datasets"></a>Verbindungs Zeichenfolgen für Datasets bearbeiten
Sie können die Verbindungsinformationen für jeden TableAdapter in einem Dataset ändern.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>So bearbeiten Sie eine Verbindungs Zeichenfolge für einen TableAdapter in einem DataSet
1. Doppelklicken Sie in **Projektmappen-Explorer** auf das Dataset ( **XSD** -Datei), das die zu bearbeitende Verbindung aufweist.
1. Wählen Sie den **TableAdapter** oder die Abfrage aus, der die zu bearbeitende Verbindung aufweist.
1. Erweitern Sie im Fenster **Eigenschaften** den **Knoten Verbindung**.
1. Um die Verbindungs Zeichenfolge schnell zu ändern, bearbeiten Sie die **ConnectionString** -Eigenschaft, oder klicken Sie auf den Pfeil nach unten in der **Verbindungs** Eigenschaft, und wählen Sie **neue Verbindung**.

## <a name="security"></a>Sicherheit
Das Speichern vertraulicher Informationen (z. B. ein Kennwort) in der Verbindungszeichenfolge kann sich auf die Sicherheit der Anwendung auswirken. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.
Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Verbindungen](../data-tools/add-new-connections.md)
