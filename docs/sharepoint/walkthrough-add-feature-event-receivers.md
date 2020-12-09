---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Funktions Ereignis Empfängern | Microsoft-Dokumentation'
description: Fügen Sie in dieser exemplarischen Vorgehensweise Funktions Ereignis Empfänger hinzu, bei denen es sich um Methoden handelt, die ausgeführt werden, wenn eine SharePoint-Funktion installiert, aktiviert, deaktiviert oder entfernt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 98b85222fca4da6dfca653ad74e1315801798d83
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915595"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Exemplarische Vorgehensweise: Hinzufügen von Funktions Ereignis Empfängern
Funktions Ereignis Empfänger sind Methoden, die ausgeführt werden, wenn eines der folgenden Funktions bezogenen Ereignisse in SharePoint auftritt:

- Eine Funktion ist installiert.

- Eine Funktion ist aktiviert.

- Eine Funktion ist deaktiviert.

- Eine Funktion wird entfernt.

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein Ereignis Empfänger zu einer Funktion in einem SharePoint-Projekt hinzugefügt wird. Es werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines leeren Projekts mit einem Funktions Ereignis Empfänger.

- Verarbeiten der **featuredeaktivierungs** -Methode.

- Verwenden Sie das SharePoint-Projekt Objektmodell, um der Ankündigungsliste eine Ankündigung hinzuzufügen.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Erstellen eines Features-Ereignis Empfänger Projekts
 Erstellen Sie zunächst ein Projekt, das den Funktions Ereignis Empfänger enthalten soll.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>So erstellen Sie ein Projekt mit einem Funktions Ereignis Empfänger

1. Wählen Sie in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.

2. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie im Bereich **Vorlagen** die **SharePoint 2010-Projekt** Vorlage aus.

     Sie verwenden diesen Projekttyp für Funktions Ereignis Empfänger, da Sie keine Projektvorlage haben.

4. Geben Sie im Feld **Name den Namen** **FeatureEvtTest** ein, und klicken Sie dann auf die Schaltfläche **OK** , um den Assistenten zum Anpassen von **SharePoint** anzuzeigen.

5. Geben Sie auf der Seite **Site und Sicherheitsebene für Debugging angeben** die URL für die SharePoint-Serversite ein, der Sie das neue benutzerdefinierte Feld Element hinzufügen möchten, oder verwenden Sie den Standard Speicherort (http:// \<*system name*> /).

6. Wählen Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** das Optionsfeld **als Farm Lösung** bereitstellen aus.

     Weitere Informationen zu Sandkasten Lösungen im Vergleich zu Farm Lösungen finden Sie unter [Überlegungen zu Sandkasten](../sharepoint/sandboxed-solution-considerations.md)Lösungen.

7. Wählen Sie die Schaltfläche **Fertig** stellen aus, und beachten Sie, dass unter dem Knoten **Features** eine Funktion mit dem Namen Feature1 angezeigt wird.

## <a name="add-an-event-receiver-to-the-feature"></a>Hinzufügen eines Ereignis Empfängers zum Feature
 Fügen Sie als nächstes der Funktion einen Ereignis Empfänger hinzu, und fügen Sie Code hinzu, der ausgeführt wird, wenn die Funktion deaktiviert wird.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>So fügen Sie der Funktion einen Ereignis Empfänger hinzu

1. Öffnen Sie das Kontextmenü für den Knoten Features, und wählen Sie dann **Feature hinzufügen** aus, um ein Feature zu erstellen.

2. Öffnen Sie unter dem Knoten **Features** das Kontextmenü für **Feature1**, und wählen Sie dann **Ereignis Empfänger hinzufügen** aus, um der Funktion einen Ereignis Empfänger hinzuzufügen.

     Dadurch wird eine Codedatei unter Feature1 hinzugefügt. In diesem Fall wird Sie abhängig von der Entwicklungssprache Ihres Projekts entweder *Feature1.EventReceiver.cs* oder *Feature1. EventReceiver. vb* benannt.

3. Wenn Ihr Projekt in geschrieben ist [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , fügen Sie den folgenden Code am Anfang des Ereignis Empfängers hinzu, wenn er nicht bereits vorhanden ist:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. Die Ereignis Empfängerklasse enthält mehrere auskommentierten Methoden, die als Ereignisse fungieren. Ersetzen Sie die **featuredeaktivierungs** -Methode durch Folgendes:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Testen des Funktions Ereignis Empfängers
 Deaktivieren Sie als nächstes das Feature, um zu testen, ob die **featueinlösen** -Methode eine Ankündigung an die SharePoint-Ankündigungsliste ausgibt.

#### <a name="to-test-the-feature-event-receiver"></a>So testen Sie den Funktions Ereignis Empfänger

1. Legen Sie den Wert der Eigenschaft **aktive Bereitstellungs Konfiguration** des Projekts auf **keine Aktivierung** fest.

     Durch Festlegen dieser Eigenschaft wird verhindert, dass das Feature in SharePoint aktiviert wird, und Sie können Funktions Ereignis Empfänger Debuggen. Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).

2. Drücken Sie die Taste **F5** , um das Projekt auszuführen und in SharePoint bereitzustellen.

3. Öffnen Sie oben auf der SharePoint-Webseite das Menü **Website Aktionen** , und wählen Sie dann **Website Einstellungen** aus.

4. Wählen Sie auf der Seite **Standorteinstellungen** im Abschnitt **Website Aktionen** den Link **Website Features verwalten** aus.

5. Wählen Sie auf der Seite **Features** neben dem Feature **FeatureEvtTest Feature1** die Schaltfläche **aktivieren** aus.

6. Wählen Sie auf der Seite **Features** neben dem Feature **FeatureEvtTest Feature1** die Schaltfläche **Deaktivieren** aus, und wählen Sie dann den Link diese featurebestätigung **Deaktivieren** aus, um die Funktion zu deaktivieren.

7. Wählen Sie die Schaltfläche **Start** aus.

     Beachten Sie, dass eine Ankündigung in der **Ankündigungs** Liste angezeigt wird, nachdem die Funktion deaktiviert wurde.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)