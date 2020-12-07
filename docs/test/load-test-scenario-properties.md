---
title: Load Test Scenario Properties
description: Hier erfahren Sie, wie Sie die Eigenschafteneinstellungen Ihres Auslastungstestszenarios in Visual Studio in eine der verschiedenen in diesem Artikel aufgeführten Eigenschaften für Auslastungstestszenarios ändern.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 263a3a1f928fe42d1f5b910f82d0d4a6ea24412e
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328807"
---
# <a name="load-test-scenario-properties"></a>Eigenschaften von Auslastungstestszenarios

Ändern Sie die Eigenschafteneinstellungen für Auslastungstestszenarios in Visual Studio, um Ihre Auslastungstestanforderungen zu erfüllen. Dieser Artikel listet die verschiedenen Eigenschaften von Auslastungstestszenarios nach Kategorie auf.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Allgemein

|Eigenschaft|Definition|
|-|----------------|
|**Name**|Der Name des Szenarios.|

## <a name="mix"></a>Mischung

|Eigenschaft|Definition|
|-|----------------|
|**Browsermischung**|Gibt den Webbrowsermix für den Auslastungstest an. Sie können verschiedene Webbrowsertypen und ihre Auslastungsverteilung angeben.<br /><br />Klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, um das Dialogfeld **Browsermischung bearbeiten** zu öffnen, und wählen Sie mithilfe von **Hinzufügen** und **Entfernen** die Webbrowsertypen im Auslastungstest aus.<br /><br />Weitere Informationen finden Sie unter [Angeben von Webbrowsertypen](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Netzwerkmischung**|Gibt die Netzwerkmischung für den Auslastungstest an. Sie können angeben, welche Netzwerktypen eingeschlossen werden sollen, und ihre Auslastungsverteilung festlegen.<br /><br />Klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, um das Dialogfeld **Netzwerkmischung bearbeiten** zu öffnen, und wählen Sie mithilfe von **Hinzufügen** und **Entfernen** die Netzwerktypen im Auslastungstest aus.<br /><br />Weitere Informationen finden Sie unter [Angeben von virtuellen Netzwerktypen](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Testmischung**|Gibt die Mischung der Webleistungs- und Komponententests für den Auslastungstest an. Sie können angeben, welche Tests eingeschlossen werden sollen, und ihre Auslastungsverteilung festlegen.<br /><br />Klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, um das Dialogfeld **Testmischung bearbeiten** zu öffnen, und wählen Sie mithilfe von **Hinzufügen** und **Entfernen** die Tests im Auslastungstest aus.<br /><br />Weitere Informationen finden Sie unter [Editing the Test Mix for a Load Test Scenario (Bearbeiten der Testmischung für ein Auslastungstestszenario)](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Testmischungstyp**|Gibt das Testmischungsmodell für den Auslastungstest an.<br /><br />Klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, um das Dialogfeld **Testmischung bearbeiten** zu öffnen, und wählen Sie aus dem Dropdownmenü unter **Testmischungsmodell** das Testmischungsmodell aus, das im Auslastungstest verwendet werden soll.<br /><br />Weitere Informationen finden Sie unter [Editing Test Mix Models (Bearbeiten von Testmischungsmodellen)](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Optionen

|Eigenschaft|Definition|
|-|----------------|
|**Zu verwendende Agents**|Gibt die Agents an, die für das zu verwendende Szenario verwendet werden sollen, wenn Sie den Auslastungstest remote ausführen. Sie möchten z. B. einen bestimmten Satz von Agents angeben, damit Sie die Konsistenz beim Analysieren von Leistungstrends aufrechterhalten. Zudem sind Agents möglicherweise geografisch verteilt, sodass bezüglich der ausgeführten Skripts und des Standorts des Agents eine Affinität besteht.<br /><br />Agents müssen durch Kommas getrennt sein, z.B. „**Agent1, Agent2, Agent3**“. Wenn Sie keine Eigenschaft angeben, verwendet das Szenario alle verfügbaren Agents.<br /><br />Weitere Informationen finden Sie unter [How to: Specify Test Agents to Use (Vorgehensweise: Angeben der zu verwendenden Test-Agents)](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Verteilung auf Geschwindigkeitsverzögerung anwenden**|Boolescher Wert, mit dem angegeben wird, wenn Sie typische Verteilungsverzögerungen im Testmischungsmodell mit Geschwindigkeitsangabe anwenden möchten. Diese Eigenschaft ist nur gültig, wenn die Eigenschaft **Testmischungstyp** auf **Auf Grundlage der Benutzergeschwindigkeit** festgelegt wird.<br /><br />Weitere Informationen finden Sie unter [How to: Apply Distribution to Pacing Delay (Vorgehensweise: Anwenden der Verteilung auf Geschwindigkeitsverzögerungen)](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).|
|**IP-Wechsel**|Boolescher Wert, der angibt, ob ein IP-Wechsel verwendet wird.<br /><br />Durch IP-Wechsel kann ein Test-Agent für Anfragen an einen Server einen Bereich von IP-Adressen verwenden. Auf diese Weise werden Aufrufe von anderen Clientcomputern simuliert. Der IP-Wechsel ist wichtig, wenn Sie den Test mit einer Webfarm ausführen, deren Last ausgeglichen ist. Die meisten Lastenausgleichsmodule etablieren die Zugehörigkeit zwischen einem Client und einem bestimmten Webserver durch die Verwendung der IP-Adresse des Clients. Wenn alle Anfragen von einem einzigen Client zu kommen scheinen, wird die Auslastung vom Lastenausgleichsmodul nicht ausgeglichen. Um innerhalb der Webfarm einen guten Lastenausgleich zu erhalten, ist es wichtig, dass die Anfragen von mehreren IP-Adressen stammen.<br /><br />Der IP-Wechsel ist nur für den Test-Agent verfügbar.|
|**Maximale Anzahl von Testiterationen**|Numerischer Wert, mit dem die maximale Anzahl der Tests angegeben wird, die im Szenario ausgeführt werden sollen. Der Wert "0" gibt kein Maximum an.<br /><br />Weitere Informationen finden Sie unter [Configuring Test Iterations for Scenarios (Konfigurieren von Testiterationen für Szenarios)](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Prozentsatz neuer Benutzer**|Numerischer Wert, mit dem der Prozentsatz neuer Benutzer oder erstmaliger Besucher im Szenario angegeben wird.<br /><br />Weitere Informationen finden Sie unter [How to: Specify the Percentage of Virtual Users that Use Web Cache Data (Vorgehensweise: Angeben des Prozentanteils virtueller Benutzer, die auf Webcachedaten zugreifen)](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Reaktionsprofil**|Gibt an, ob vom Szenario **Normalverteilung** verwendet wird, oder ob das Reaktionsprofil **Aktiviert** oder **Deaktiviert** ist.<br /><br />Weitere Informationen finden Sie unter [Editing Think Times to Simulate Website Human Interaction Delays (Bearbeiten von Reaktionszeiten zum Simulieren von Website-Interaktionsverzögerungen des Benutzers)](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Zeitliche Steuerung

|Eigenschaft|Definition|
|-|----------------|
|**Startzeit verzögern**|Ein Zeitwert, der angibt, um wie viele Stunden, Minuten und Sekunden das Starten des Szenarios nach dem Beginn des Auslastungstest verzögert wird. Wenn die Eigenschaft **Während Aufwärmdauer deaktivieren** auf **TRUE** festgelegt wird, wird die Wartezeit erst nach dem Abschluss der Aufwärmphase angewendet.<br /><br />Weitere Informationen finden Sie unter [Konfigurieren von Szenariostartverzögerungen](../test/configure-scenario-start-delays.md).|
|**Während Aufwärmdauer deaktivieren**|Boolescher Wert, mit dem angegeben wird, ob das Szenario während der Zeitangabe der Eigenschaft **Aufwärmdauer** ausgeführt werden soll, die in den Laufzeiteinstellungen des Auslastungstests festgelegt wurde.<br /><br />Weitere Informationen zu den Einstellungseigenschaften für die Auslastungstestausführung finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).<br /><br />Weitere Informationen finden Sie unter [Konfigurieren von Szenariostartverzögerungen](../test/configure-scenario-start-delays.md).|
|**Reaktionszeiten zwischen Testiterationen**|Numerischer Wert, mit dem die Wartezeit in Sekunden zwischen Testiterationen angegeben wird.<br /><br />Weitere Informationen finden Sie unter [Editing Think Times to Simulate Website Human Interaction Delays (Bearbeiten von Reaktionszeiten zum Simulieren von Website-Interaktionsverzögerungen des Benutzers)](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
