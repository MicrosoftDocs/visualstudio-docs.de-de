---
title: 'Gewusst wie: Definieren des Typdeskriptors eines Parameters | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie den Typdeskriptor eines Parameters für eine Methode in Ihrem Business Data Connectivity-Modell (BDC) definieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9dac5aa82b03887a11ba9ed3c76fe03fd85174cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913720"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Gewusst wie: Definieren des Typdeskriptors für einen Parameter
  Ein Typdeskriptor enthält Eigenschaften, mit denen der Datentyp eines Parameters beschrieben wird. Von einem Typdeskriptor kann ein Feld, eine Entität oder eine Auflistung von Entitäten definiert werden. Weitere Informationen finden Sie unter [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>So definieren Sie den Typdeskriptor für einen Parameter

1. Wählen Sie im Fenster **BDC-Methoden Details** den Typdeskriptor des Parameters aus.

2. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaften Fenster** aus.

3. Legen Sie im **Eigenschaften** Fenster die Eigenschaften des Typdeskriptors fest.

     In den folgenden Prozeduren wird beschrieben, wie ein Typdeskriptor als Feld, Entität oder Entitätsauflistung definiert wird.

### <a name="to-define-a-field"></a>So definieren Sie ein Feld

1. Legen Sie im Fenster **Eigenschaften** die **Name** -Eigenschaft des Typdeskriptors auf den Namen eines Felds in dem Typ fest, der die Entität darstellt (z. b. **FirstName**).

2. Wählen Sie in der Liste neben der **tykame** -Eigenschaft den entsprechenden Datentyp aus (z. b. **Int32**).

     Weitere Informationen zu anderen optionalen Parametern finden Sie unter [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>So definieren Sie eine Entität

1. Legen Sie im Fenster **Eigenschaften** die **Name** -Eigenschaft auf einen Namen fest, der die Entität beschreibt (z. b. **Contact**).

2. Legen Sie die Eigenschaft **tykame** auf den voll qualifizierten Namen des Typs fest, der die Entität darstellt. Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.

    - Wählen Sie für eine Klasse im Projekt den Pfeil nach unten neben der Eigenschaft **tykame** aus, wählen Sie im angezeigten Dialogfeld die Registerkarte **Aktuelles Projekt** aus, und wählen Sie dann die Klasse in Ihrem Projekt aus.

         Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB-Systems. Im folgenden Beispiel wird der Wert der Eigenschaft **tykame** auf eine Klasse im Projekt festgelegt.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.

         Im folgenden Beispiel wird der Wert der **tykame** -Eigenschaft auf einen Typ festgelegt, der in einer Assembly definiert ist, auf die Sie in der Projekt Mappe verweisen.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - Bei Verwendung eines im BDC-Objektmodell definierten Typs enthält der vollqualifizierte Name den Namespace und den Namen des Typs.

         Im folgenden Beispiel wird der Wert der **tykame** -Eigenschaft auf einen Typ im BDC-Objektmodell festgelegt.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. Öffnen Sie im Fenster **BDC-Methoden Details** die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie dann **Bearbeiten** aus.

     Das **BDC-Explorer** -Fenster wird geöffnet.

4. Öffnen Sie im **BDC-Explorer** das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen** aus.

     Dem Entitätstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt. Konfigurieren Sie diesen Typdeskriptor als Feld.

5. Wiederholen Sie Schritt 4, um für jedes Feld der Entität einen untergeordneten Typdeskriptor hinzuzufügen.

### <a name="to-define-a-collection-of-entities"></a>So definieren Sie eine Auflistung von Entitäten

1. Wählen Sie im Fenster **BDC-Methoden Details** den Typdeskriptor des gewünschten Parameters aus.

2. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaften Fenster** aus.

3. Legen Sie im Fenster **Eigenschaften** die **Name** -Eigenschaft auf einen Namen fest, der die Entität beschreibt (z. b. **Kontakte**).

4. Legen Sie die **IsCollection** -Eigenschaft auf **true** fest. Dadurch wird angegeben, dass es sich bei diesem Typdeskriptor um eine Auflistung von Entitäten handelt.

5. Legen Sie die Eigenschaft **tykame** auf eine Zeichenfolge fest, die einen Verweis auf die <xref:System.Collections.Generic.IEnumerable%601> -Schnittstelle enthält, und auf den voll qualifizierten Namen des Typs, der die Entität darstellt. Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.

   - Wählen Sie für eine Klasse im Projekt den Pfeil nach unten neben der Eigenschaft **tykame** aus, wählen Sie im angezeigten Dialogfeld die Registerkarte **Aktuelles Projekt** aus, und wählen Sie dann die Klasse in Ihrem Projekt aus.

      Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB-Systems.

      Im folgenden Beispiel wird der Wert der Eigenschaft **tykame** auf eine Auflistung von Klassen in Ihrem Projekt festgelegt.

      `System.Collections.Generic.IEnumerable`1 [mybdcnamespace. BdcModel1. Contact, BdcModel1] '

   - Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.

      Im folgenden Beispiel wird der Wert der Eigenschaft **tykame** auf eine Auflistung von Typen in einer Assembly festgelegt, auf die Sie in der Projekt Mappe verweisen.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace. Contact, myAssemblyName, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089] '

   - Bei Verwendung eines im BDC-Objektmodell definierten Typs enthält der vollqualifizierte Name lediglich den Namespace und den Namen des Typs.

      Im folgenden Beispiel wird der Wert der **tykame** -Eigenschaft auf eine Auflistung von Typen festgelegt, die im BDC-Objektmodell definiert sind.

      `System.Collections.Generic.IEnumerable`1 [Microsoft. businessdata. Runtime. dynamictype] '

6. Öffnen Sie im Fenster **BDC-Methoden Details** die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie dann **Bearbeiten** aus.

    Das **BDC-Explorer** -Fenster wird geöffnet.

7. Öffnen Sie im **BDC-Explorer** das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen** aus.

    Dem Auflistungstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt. Konfigurieren Sie diesen Typdeskriptor als Entität.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
