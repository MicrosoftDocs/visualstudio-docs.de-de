---
title: Bearbeitbare Änderungen ohne Commit
description: Commit für Prozess interne Änderungen an Daten gebundenen Windows Forms Steuerelementen vor dem Speichern von Daten ausführen. Aufrufen von EndEdit für alle BindingSource-Komponenten in einem Formular.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 98f75769a8002fd960da74dc5f9bd9a6b046a604
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867242"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten

Beim Bearbeiten von Werten in Daten gebundenen Steuerelementen müssen Benutzer aus dem aktuellen Datensatz navigieren, um den aktualisierten Wert auf die zugrunde liegende Datenquelle zu übertragen, an die das Steuerelement gebunden ist. Wenn Sie Elemente aus dem [Datenquellen Fenster](add-new-data-sources.md) auf ein Formular ziehen, generiert das erste Element, das Sie ablegen, Code im Click-Ereignis der Schaltfläche " **Speichern** " von <xref:System.Windows.Forms.BindingNavigator> . Dieser Code Ruft die- <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode von auf <xref:System.Windows.Forms.BindingSource> . Daher wird der-Methodenaufrufe <xref:System.Windows.Forms.BindingSource.EndEdit%2A> nur für das erste generiert, <xref:System.Windows.Forms.BindingSource> das dem Formular hinzugefügt wird.

Der Aufruf <xref:System.Windows.Forms.BindingSource.EndEdit%2A> führt ein Commit aller Änderungen durch, die in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Wenn also ein datengebundenes Steuerelement den Fokus noch besitzt und Sie auf **Speichern** klicken, werden alle ausstehenden Bearbeitungen in diesem Steuerelement committet, bevor der eigentliche Speichervorgang durchgeführt wird (die `TableAdapterManager.UpdateAll`-Methode).

Sie können Ihre Anwendung so konfigurieren, dass Änderungen automatisch committet werden, auch wenn ein Benutzer versucht, Daten zu speichern, ohne die Änderungen im Rahmen des Speicher Vorgangs zu übernehmen.

> [!NOTE]
> Der Designer fügt den `BindingSource.EndEdit` Code nur für das erste Element hinzu, das auf einem Formular abgelegt wurde. Daher müssen Sie eine Codezeile hinzufügen, um die- <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für jede <xref:System.Windows.Forms.BindingSource> im Formular aufzurufen. Sie können manuell eine Codezeile hinzufügen, um die- <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für jede Methode aufzurufen <xref:System.Windows.Forms.BindingSource> . Alternativ können Sie die Methode dem `EndEditOnAllBindingSources` Formular hinzufügen und Sie vor dem Durchführen einer Speicherung anrufen.

Im folgenden Code wird eine [LINQ (Language-Integrated Query)-](/dotnet/csharp/linq/) Abfrage verwendet, um alle-Komponenten zu durchlaufen <xref:System.Windows.Forms.BindingSource> und die- <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für jedes <xref:System.Windows.Forms.BindingSource> in einem Formular aufzurufen.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>So wenden Sie EndEdit für alle BindingSource-Komponenten in einem Formular an

1. Fügen Sie dem Formular den folgenden Code hinzu, der die <xref:System.Windows.Forms.BindingSource> Komponenten enthält.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Fügen Sie die folgende Codezeile direkt vor den Aufrufen von ein, um die Daten des Formulars zu speichern (die- `TableAdapterManager.UpdateAll()` Methode):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Weitere Informationen

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
