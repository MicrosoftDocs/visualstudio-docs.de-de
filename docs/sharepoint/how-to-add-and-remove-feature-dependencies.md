---
title: 'Vorgehensweise: Hinzufügen und Entfernen von Featureabhängigkeiten | Microsoft-Dokumentation'
description: Informieren Sie sich über das Hinzufügen und Entfernen von Featureabhängigkeiten zu Ihrer SharePoint-Lösung mithilfe des Funktions-Designers in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ebec7f6b1f6d777ce7b3b914ac5c1d5629190fcc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923576"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Vorgehensweise: Hinzufügen und Entfernen von Featureabhängigkeiten
  Die SharePoint-Funktion kann von anderen Features für Funktionen oder Daten abhängen. In diesen Fällen können Sie diese anderen Features als Abhängigkeiten für ihre Funktion markieren. Auf diese Weise wird vom SharePoint-Server sichergestellt, dass abhängige Features aktiviert werden, bevor das Feature aktiviert wird.

## <a name="add-dependencies"></a>Hinzufügen von Abhängigkeiten
 Sie können weitere Funktionen in der Projekt Mappe als Abhängigkeiten hinzufügen. Auf diese Weise können Sie sicherstellen, dass erforderliche Funktionen installiert und aktiviert sind, bevor die Funktion installiert ist.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>So fügen Sie eine Abhängigkeit zu einer Funktion in der Projekt Mappe hinzu

1. Öffnen Sie den Funktions-Designer, erweitern Sie den Knoten **Funktions Aktivierungs Abhängigkeiten** , und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Abhängigkeiten von Featureaktivierung hinzu** fügen die Option **Abhängigkeit von Features in der Projekt Mappe hinzufügen** aus, wählen Sie den Titel der Funktion aus, die Sie als Abhängigkeit hinzufügen möchten, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Sie können mehr als eine Funktion hinzufügen, indem Sie beim Auswählen der **STRG** -Taste mehrere Titel auswählen.

## <a name="addi-custom-dependencies"></a>Benutzerdefinierte ADDI-Abhängigkeiten
 Sie können Funktionen hinzufügen, die bereits auf einem SharePoint-Server als Abhängigkeit bereitgestellt wurden. Auf diese Weise prüft der SharePoint-Aktivierungsprozess, ob alle abhängigen Features aktiviert sind, bevor das Feature installiert wird.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>So fügen Sie eine Abhängigkeit mithilfe der Funktions-ID hinzu

1. Öffnen Sie den Funktions-Designer, erweitern Sie den Knoten **Funktions Aktivierungs Abhängigkeiten** , und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Abhängigkeiten von Featureaktivierung hinzu** fügen die Options Schaltfläche **benutzerdefinierte Abhängigkeit hinzufügen** aus.

3. Geben Sie im Textfeld **Funktions-ID** die GUID für die Funktion ein, die Sie als Aktivierungs Abhängigkeit markieren möchten, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

## <a name="edit-custom-dependencies"></a>Benutzerdefinierte Abhängigkeiten bearbeiten
 Sie können benutzerdefinierte Abhängigkeiten bearbeiten, die Sie zuvor hinzugefügt haben. Abhängige Features, die in der Projekt Mappe enthalten sind, können jedoch nur entfernt, nicht bearbeitet werden.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>So ändern Sie eine Abhängigkeit von einer Funktion in der Projekt Mappe

1. Öffnen Sie den Funktions-Designer, und erweitern Sie dann den Knoten **Funktions Aktivierungs Abhängigkeiten** .

2. Wählen Sie den Namen der Funktion aus, die Sie bearbeiten möchten, und klicken Sie dann auf die Schaltfläche **Bearbeiten** .

3. Ändern Sie im Dialogfeld **benutzerdefinierte Funktions Aktivierungs Abhängigkeit bearbeiten** den Titel, die Funktions-ID oder die Beschreibung, und wählen Sie dann die Schaltfläche **senden** aus.

## <a name="remove-dependencies"></a>Abhängigkeiten entfernen

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>So entfernen Sie eine Abhängigkeit von einer Funktion in der Projekt Mappe

1. Erweitern Sie im Funktions-Designer den Knoten **Funktions Aktivierungs Abhängigkeiten** , wählen Sie den Namen des zu entfernenden Features aus, und klicken Sie dann auf die Schaltfläche **Entfernen** .

## <a name="see-also"></a>Weitere Informationen
- [SharePoint-Features erstellen](../sharepoint/creating-sharepoint-features.md)
- [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Gewusst wie: Hinzufügen und Entfernen von Elementen zu SharePoint-Features](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
