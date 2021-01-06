---
title: Parameter Informationen in einer Legacy Sprache Service1 | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die QuickInfo für IntelliSense-Parameter Info implementieren, die Benutzern Tipps in einem Legacy Sprachdienst bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cd49644e670df42f4630af987a5e9152b4f6c95
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876804"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Parameter Informationen in einem Legacy Sprachdienst 1
Der IntelliSense-Parameter Info QuickInfo bietet Benutzern Hinweise dazu, wo Sie sich in einem Sprachkonstrukt befinden.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="how-parameter-info-tooltips-work"></a>Funktionsweise von Parameter Info-Quick Infos
 Wenn Sie eine Anweisung im Editor eingeben, zeigt das VSPackage ein kleines QuickInfo-Fenster an, das die Definition der typisierten Anweisung enthält. Wenn Sie z. b. eine Microsoft Foundation Classes (MFC)-Anweisung eingeben (z. b. `pMainFrame ->UpdateWindow` ) und die öffnende Klammer Taste drücken, um mit der Auflistung von Parametern zu beginnen, wird ein Methoden Tipp mit der Definition der `UpdateWindow` Methode angezeigt.

 Quick Infos für die Parameter Info werden normalerweise in Verbindung mit der Anweisungs Vervollständigung verwendet. Sie sind besonders nützlich für Sprachen mit Parametern oder anderen formatierten Informationen nach dem Methodennamen oder-Schlüsselwort.

 Die Quick Infos für die Parameter Info werden vom Sprachdienst durch die Befehls Abfang Funktion initiiert. Zum Abfangen von Benutzer Zeichen muss das Sprachdienst Objekt die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle implementieren und der Textansicht einen Zeiger auf die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung übergeben, indem die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode in der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle aufgerufen wird. Der Befehls Filter fängt die Befehle ab, die Sie in das Code Fenster eingeben. Überwachen Sie die Befehls Informationen, um zu erfahren, wann dem Benutzerparameter Informationen angezeigt werden. Sie können denselben Befehls Filter für Anweisungs Vervollständigung, Fehler Marker usw. verwenden.

 Wenn Sie ein Schlüsselwort eingeben, für das der Sprachdienst Hinweise bereitstellen kann, erstellt der Sprachdienst ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Objekt und ruft die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Methode in der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle auf, um die IDE zum Anzeigen eines Hinweises zu benachrichtigen. Erstellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Sie das Objekt mit, und geben Sie `VSLocalCreateInstance` die Co-Klasse an `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` ist eine Funktion, die in der Header Datei vsdoc. h definiert ist, die `QueryService` für die lokale Registrierung aufruft und für `CreateInstance` dieses Objekt für den aufruft `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Bereitstellen eines Methoden Tipps
 Um einen Methoden Tipp anzugeben, müssen Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> Methode in der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Schnittstelle aufzurufen und ihr die Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle übergeben.

 Wenn Ihre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Klasse aufgerufen wird, werden die zugehörigen Methoden in der folgenden Reihenfolge aufgerufen:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Gibt die Position und Länge der relevanten Daten im aktuellen Text Puffer zurück. Dadurch wird die IDE angewiesen, diese Daten nicht mit dem QuickInfo-Fenster zu verbergen.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Gibt die Methoden Nummer (null basierter Index) zurück, die anfänglich angezeigt werden soll. Wenn Sie z. b. 0 (null) zurückgeben, wird zunächst die erste überladene Methode angezeigt.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Gibt die Anzahl der überladenen Methoden zurück, die im aktuellen Kontext anwendbar sind. Wenn Sie für diese Methode einen Wert größer als 1 zurückgeben, werden in der Textansicht für Sie die Pfeile nach oben und nach unten angezeigt. Wenn Sie auf den Pfeil nach unten klicken, ruft die IDE die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> Methode auf. Wenn Sie auf den Pfeil nach oben klicken, ruft die IDE die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> Methode auf.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Der Text der QuickInfo für die Parameter Info wird bei mehreren Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> -und- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> Methoden erstellt.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Gibt die Anzahl von Parametern zurück, die in der Methode angezeigt werden sollen.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Wenn Sie eine Methoden Nummer zurückgeben, die der Überladung entspricht, die Sie anzeigen möchten, wird diese Methode aufgerufen, gefolgt von einem Aufruf der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> Methode.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informiert ihren Sprachdienst über das Aktualisieren des Editors, wenn ein Methoden Tipp angezeigt wird. Nennen Sie in der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> Methode Folgendes:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Sie erhalten einen aufzurufenden Befehl an die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Methode, wenn Sie das Methoden Tipp Fenster schließen.
