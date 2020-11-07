---
title: Herunterladen der Satellitenassembly bei Bedarf mithilfe des ClickOnce-Designers
description: Erfahren Sie, wie Sie Satellitenassemblys mit dem-Designer als optional markieren und nur die Assembly herunterladen, die ein Client Computer für die aktuellen Kultur Einstellungen benötigt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b6b57faf01878dc5aff708f0aca47707bf6e48c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350334"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der ClickOnce-Bereitstellungs-API
Mit Windows Forms-Anwendungen können mehrere Kulturen mithilfe von Satellitenassemblys konfiguriert werden. Eine *Satellitenassembly* ist eine Assembly, die Anwendungsressourcen für eine andere Kultur als die Standardkultur der Anwendung enthält.

 Wie unter [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md)erläutert, können Sie mehrere Satellitenassemblys für mehrere Kulturen innerhalb derselben [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung einschließen. In der Standardeinstellung lädt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alle Satellitenassemblys in Ihrer Bereitstellung auf den Clientcomputer herunter, obwohl ein einzelner Client wahrscheinlich nur eine Satellitenassembly benötigt.

 Diese exemplarische Vorgehensweise beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt.

> [!NOTE]
> Zu Testzwecken legen die folgenden Codebeispiele die Kultur programmgesteuert auf `ja-JP` fest. Im Abschnitt "Nächste Schritte" weiter unten in diesem Thema finden Sie Informationen zum Anpassen dieses Codes für eine Produktionsumgebung.

### <a name="to-mark-satellite-assemblies-as-optional"></a>So markieren Sie Satellitenassemblys als optional

1. Erstellen Sie Ihr Projekt. Dadurch werden Satellitenassemblys für alle Kulturen generiert, die Sie lokalisieren.

2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Eigenschaften**.

3. Klicken Sie auf die Registerkarte **Veröffentlichen** , und klicken Sie dann auf die **Anwendungsdateien**.

4. Aktivieren Sie das Kontrollkästchen **Alle Dateien anzeigen** , um Satellitenassemblys anzuzeigen. Standardmäßig werden alle Satellitenassemblys in Ihre Bereitstellung aufgenommen und in diesem Dialogfeld angezeigt.

     Eine Satellitenassembly weist einen Namen in der Form *\<isoCode>\ApplicationName.resources.dll* auf, wobei \<isoCode> eine sprach Kennung im RFC 1766-Format ist.

5. Klicken Sie in der Liste **Downloadgruppe** für jede Sprachen-ID auf **Neu**. Wenn Sie zur Eingabe eines Downloadgruppennamens aufgefordert werden, geben Sie die Sprach-ID ein. Für eine japanische Satellitenassembly würden Sie z. b. den Download Gruppennamen angeben `ja-JP` .

6. Schließen Sie das Dialogfeld **Anwendungsdateien**.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>So laden Sie Satellitenassemblys bei Bedarf in C\# herunter

1. Öffnen Sie die Datei *Program.cs*. Wenn diese Datei nicht im Projektmappen-Explorer angezeigt wird, wählen Sie das Projekt aus, und klicken Sie im Menü **Projekt** auf **Alle Dateien anzeigen**.

2. Verwenden Sie den folgenden Code, um die entsprechende Satellitenassembly herunterzuladen und die Anwendung zu starten.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>So laden Sie Satellitenassemblys bei Bedarf in Visual Basic herunter

1. Klicken Sie im Fenster **Eigenschaften** der Anwendung auf die Registerkarte **Anwendung**.

2. Klicken Sie unten auf der Registerkarte auf **Anwendungsereignisse anzeigen**.

3. Fügen Sie folgenden Importanweisungen am Anfang der Datei *ApplicationEvents.VB* hinzu.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

4. Fügen Sie der `MyApplication` -Klasse den folgenden Code hinzu.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

## <a name="next-steps"></a>Nächste Schritte
 In einer Produktionsumgebung müssen Sie wahrscheinlich die Zeile in den Codebeispielen entfernen, die <xref:System.Threading.Thread.CurrentUICulture%2A> auf einen bestimmten Wert festlegt, da auf Clientcomputern der richtige Wert standardmäßig festgelegt ist. Beim Ausführen der Anwendung auf einem japanischen Clientcomputer ist <xref:System.Threading.Thread.CurrentUICulture%2A> z. B. standardmäßig `ja-JP` . Das programmgesteuerte Festlegen ist eine gute Möglichkeit, die Satellitenassemblys zu testen, bevor Sie die Anwendung bereitstellen.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Bedarfs gesteuertes herunterladen von Satellitenassemblys mit der ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md)
