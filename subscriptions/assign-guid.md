---
title: Zuweisen spezifischer GUIDs zu Visual Studio-Abonnenten | Microsoft-Dokumentation
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 10/22/2020
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren Abonnenten spezifische Abonnement-GUIDs zuweisen können.
ms.openlocfilehash: 1097743d1640fbadba550f3c2ee6908ac694436d
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467478"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Zuweisen spezifischer Abonnements im Portal für die Verwaltung von Visual Studio-Abonnements

Administratoren können über das Verwaltungsportal für Visual Studio-Abonnements ab sofort einzelnen Abonnenten spezifische Abonnements zuweisen.  Dies kann in Situationen sinnvoll sein, in denen Organisationen über temporäre Mitarbeiter oder Lieferanten verfügen, die für einen kurzen Zeitraum auf ein Abonnement zugreifen müssen.  Administratoren können ein Abonnement zuweisen, das bereits teilweise verwendet wurde, sodass sich die Nutzungsdauer neuer Abonnements nicht verringert.  

Sehen Sie sich das Video an, oder lesen Sie den Artikel, um zu erfahren, wie Sie Benutzern bestimmte Abonnement-GUIDs zuweisen. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Zuweisen spezifischer Abonnement-GUIDs für Benutzer

Der Vorgang zum Zuweisen spezifischer Abonnements für Einzelpersonen umfasst zwei vorhandene Verwaltungsprozesse, mit denen einzelnen Benutzern spezifische Abonnement-GUIDs (Globally Unique Identifier) zugewiesen werden.  Der dreistufige Prozess beginnt zunächst mit dem Exportieren einer Liste Ihrer aktuellen Abonnements und Zuweisungen. Anhand dieser Liste werden dann die spezifischen GUIDs ermittelt, die zugewiesen werden sollen. Anschließend werden die neuen Zuweisungen mit dem Vorgang zum Massenhinzufügen hochgeladen.

### <a name="export-your-subscriptions-information"></a>Exportieren Ihrer Abonnementinformationen

So führen Sie den Export aus:
1. Melden Sie sich beim [Verwaltungsportal](https://manage.visualstudio.com) an.
2. Wählen Sie die Registerkarte **Exportieren** aus, und die Datei wird auf Ihren lokalen Computer heruntergeladen. Die Datei enthält den Namen der Vereinbarung, die Ihre Benutzerabonnements enthält, sowie das Datum des Exports.
> [!div class="mx-imgBorder"]
> ![Abonnenten exportieren](_img/exporting-subscriptions/exporting-subscriptions.png "Klicken Sie auf „Exportieren“, um die Liste Ihrer zugewiesenen Abonnement mit Abonnenteninformationen zu speichern.")

### <a name="identify-the-guids-you-want-to-assign"></a>Ermitteln der GUIDs, die Sie zuweisen möchten

Wenn Sie das Exporttool zuvor bereits verwendet haben, werden Sie feststellen, dass die erzeugte Tabellenkalkulation über neue Felder verfügt.  Anhand dieser Felder können Sie den Status der einzelnen Abonnements ermitteln und festlegen, welche Abonnements Benutzern zugewiesen werden sollen.  

- **Abonnementstatus** : In diesem Feld wird angezeigt, ob ein Abonnement zugewiesen ist oder nicht.  Wenn ein Abonnement den Status „Zugewiesen“ aufweist, sind auch Benutzerinformationen wie Name, E-Mail-Adresse usw. zugeordnet. 
- **Verwendungsstatus** : Der Verwendungsstatus lautet entweder „Neu“, was bedeutet, dass das Abonnement noch nie einem Benutzer zugewiesen wurde, oder „Verwendet“, was bedeutet, dass das Abonnement schon einmal einem Benutzer zugewiesen wurde.  

Anhand der Werte in diesen Feldern und weiteren Informationen innerhalb der Tabellenkalkulation können Sie bestimmen, welche Abonnements einzelnen Benutzern zugewiesen werden sollen. Sie können einen Filter in Excel anwenden, um die Liste basierend auf dem Status, der Abonnementebene, dem Ablaufdatum usw. einzuschränken. 

### <a name="upload-your-new-assignments"></a>Hochladen Ihrer neuen Zuweisungen

Im letzten Schritt laden Sie die Vorlage zum **Massenhinzufügen** herunter, tragen die erforderlichen Informationen für die Abonnements ein, die Sie zuweisen möchten, und laden die Vorlage hoch.  Eine ausführliche Beschreibung dieses Vorgangs finden Sie unter [Hinzufügen mehrerer Benutzer](assign-license-bulk.md).  

> [!IMPORTANT]
> Um einen erfolgreichen Upload sicherzustellen, sorgen Sie für Folgendes:
> - Sie verwenden die im Dialogfeld verknüpfte Vorlage, wenn Sie **Massenhinzufügen** auswählen.  Verwenden Sie keine lokal gespeicherte Kopie der Vorlage, da diese möglicherweise nicht alle erforderlichen Felder enthält.  Wenn Sie eine alte Vorlage verwenden, tritt beim Hochladen ein Fehler auf. 
> - Alle Felder, die in der Vorlage als **Pflichtfeld** gekennzeichnet sind, sind ausgefüllt.
> - In der Spalte **Fehlermeldung** sind keine Fehler aufgeführt.
> - Jede GUID wird in der Vorlage nur einmal verwendet. 
> - Die Abonnementebene in der Vorlage entspricht dem Abonnement der GUID in der exportierten Liste. 
> - Die GUID wurde noch keinem anderen Benutzer in der exportieren Liste zugewiesen. 

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Frage: Wie kann ich ändern, welches Abonnement einem einzelnen Benutzer aktuell zugewiesen ist?
Antwort: Wenn Sie die GUID ändern möchten, die einem Benutzer zugewiesen ist, müssen Sie zunächst das Abonnement für diesen Benutzer löschen.  Weitere Informationen finden Sie unter [Löschen von Abonnements](delete-license.md).  Nachdem das Abonnement für den Benutzer gelöscht wurde, führen Sie die oben beschriebenen Schritte zum Exportieren der Liste und Hochladen der neuen Abonnementinformationen aus.  

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie Abonnements für Benutzer zugewiesen haben, können Sie sich mit weiteren Verwaltungsaufgaben vertraut machen.
- [Zuweisen von Lizenzen im Verwaltungsportal für Visual Studio-Abonnements](assign-license.md)
- [Zuweisen von Abonnements zu mehreren Benutzern](assign-license-bulk.md)
- [Bearbeiten von Abonnements](edit-license.md)
- [Löschen von Abonnements](delete-license.md)
- [Verwenden des Features „Maximum Usage“ (Maximale Auslastung) zur Übersicht der Anzahl zugewiesener Abonnements](maximum-usage.md)


