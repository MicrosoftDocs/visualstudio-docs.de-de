---
title: Bearbeiten von Visual Studio-Abonnements im Verwaltungsportal | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 09/21/2020
ms.topic: how-to
description: Erfahren Sie, wie Administratoren Abonnementzuweisungen bearbeiten können.
ms.openlocfilehash: d10e9ee779c6fc37c886bb1b5e00e15913bab7e2
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904158"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Bearbeiten von Visual Studio-Abonnementzuweisungen
Als Abonnementadministrator können Sie Änderungen an den Abonnements vornehmen, die Personen innerhalb Ihrer Organisation zugewiesen sind.  Dieser Artikel beschreibt die Arten von Änderungen, die Sie vornehmen können, und enthält die notwendigen Schritte.

   > [!NOTE]
   > Wenn Sie Abonnementdetails für Abonnenten ändern müssen, der über eine Azure Active Directory-Gruppe zugewiesen wurde, müssen Sie diese aus der Gruppe entfernen und im Verwaltungsportal einzeln hinzufügen.  

## <a name="change-subscriber-information"></a>Eingeben der Abonnenteninformationen
Sie können die Informationen eines Abonnenten bearbeiten, um Fehler zu beheben und Informationen zu aktualisieren.

Klicken Sie für das Bearbeiten eines Abonnenten auf die Auslassungspunkte (...), die neben der E-Mail-Adresse des Abonnenten angezeigt werden, wenn Sie mit der Maus darauf zeigen. Eine Dropdownliste wird angezeigt.  Klicken Sie auf **Bearbeiten** , um die Details des Abonnenten zu ändern. 
> [!div class="mx-imgBorder"]
> ![Auswählen des zu bearbeitenden Abonnenten](_img/edit-license/select-subscriber.png "Klicken Sie auf die Auslassungspunkte, und wählen Sie „Bearbeiten“ aus.")

Sie können Vornamen, Nachnamen, Abonnementebene, E-Mail-Adresse, Land/Region, Sprache, Downloads und Referenz für den Abonnenten aktualisieren. Bearbeiten Sie die Informationen zum Abonnenten, und klicken Sie dann auf **Speichern**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Bearbeiten mehrerer Abonnenten mithilfe der Massenbearbeitung


Sie können mehrere Abonnenten gleichzeitig bearbeiten, wenn Sie die Massenbearbeitung verwenden. Diese Funktion wird in erster Linie für Organisationen verwendet, wenn die geschäftlichen E-Mail-Adressen geändert werden, oder wenn eine Organisation sich dafür entschieden hat, den Zugriff auf Downloads zu beschränken.

Sehen Sie sich dieses Video an, oder lesen Sie weiter, um zu erfahren, wie Sie mehrere Abonnenten mithilfe der Massenbearbeitung bearbeiten. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

   > [!IMPORTANT]
   > Abonnementebenen (d. h. Enterprise, Professional usw.) und Abonnement-GUIDs können nicht über eine Massenbearbeitung geändert werden.  Wenn Sie Ihren Benutzern bestimmte Abonnement-GUIDs zuweisen müssen, verwenden Sie den Prozess zum Hinzufügen von Benutzern, indem Sie die Abonnement-ID auswählen. Wenn Sie versuchen, einen Upload auszuführen, bei dem diese Elemente in der Massenbearbeitungsvorlage geändert wurden, kommt es beim Upload zu einem Fehler.

1. Navigieren Sie zur Registerkarte „Abonnenten“, um mehrere Abonnenten gleichzeitig zu bearbeiten. Klicken Sie im oberen Bereich des Menübands auf **Massenbearbeitung**.

2. Die Massenbearbeitung verwendet eine Excel-Vorlage, um Änderungen an Abonnenteninformationen vorzunehmen. Klicken Sie im Feld „Massenbearbeitung“ auf **Export this Excel** (Diese Excel-Datei exportieren), um die aktuelle Liste der Abonnenten einschließlich aller Informationen herunterzuladen.
   > [!div class="mx-imgBorder"]
   > ![Bearbeiten einer Lizenz: Exportieren der Massenbearbeitungsliste](_img/edit-license/edit-license-bulk-edit-export.png "Klicken Sie auf „Diese Excel-Datei exportieren“, um eine Liste Ihrer aktuellen Abonnements zu erstellen.")

3. Speichern Sie die Datei lokal, damit Sie diese einfach finden und vor dem Upload erforderliche Änderungen vornehmen können. Für einen erfolgreichen Upload darf die **Abonnementebene oder Abonnement-GUID nicht in der Massenbearbeitungsdatei bearbeitet werden** , da dies zu einem Fehler beim Upload führt.

4. Wechseln Sie zum Administratorportal für Visual Studio-Abonnements, und klicken Sie im Dialogfeld „Massenbearbeitung“ auf **Durchsuchen**. Wählen Sie die Excel-Datei aus, die Sie gespeichert haben, und klicken Sie auf **OK**. Der Fortschritt des Uploads wird auf dem Bildschirm angezeigt.
   > [!div class="mx-imgBorder"]
   > ![Bearbeiten einer Lizenz: Massenbearbeitungen – Dateiupload](_img/edit-license/edit-license-bulk-file-upload1.png "Navigieren Sie zum Speicherort Ihrer fertig gestellten Excel-Datei, wählen Sie die Datei aus, und klicken Sie auf OK.")

5. Sobald Sie die Datei hochgeladen haben, wird Ihnen eine Benachrichtigung angezeigt, dass der Upload erfolgreich war. Jetzt sind Ihre Änderungen in den Abonnenteninformationen zu enthalten.

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
- Sie müssen eine bestimmte Abonnement-ID zuweisen? Lesen Sie „Zuweisen einer Abonnement-ID“. 
- Um ein bestimmtes Abonnement zu finden, informieren Sie sich unter [Suchen nach einem Abonnement](search-license.md).
- Müssen Sie eine Liste all Ihrer Abonnements erstellen?  Informieren Sie sich unter [Exportieren von Abonnements](exporting-subscriptions.md).