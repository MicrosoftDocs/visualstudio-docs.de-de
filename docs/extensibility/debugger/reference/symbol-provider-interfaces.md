---
title: Symbol Anbieter Schnittstellen | Microsoft-Dokumentation
description: Dieser Artikel verknüpft Sie mit Beschreibungen der Schnittstellen für die Symbol Behandlung für das Visual Studio SDK, die Variablen in einer aufrufsstapel während des Break-Modus auswerten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a24baec6738382f93dee5d8b7843d624eea80890
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845790"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
Im folgenden sind die Schnittstellen für die Symbol Behandlung für das aufgeführt [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Diskussion
 Diese Schnittstellen werden verwendet, um Variablen in einer-Rückruf Stapel während des Break-Modus auszuwerten. Sie werden nur für Common Language Runtime Symbol Anbieter (SP) implementiert.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Stellt die Adresse eines Elements dar.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Stellt die Adresse eines Elements dar und bietet Zugriff auf die Prozess-ID.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Stellt ein Array Symbol oder einen Arraytyp dar.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Stellt ein Klassen Symbol oder einen Klassentyp dar.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Stellt einen com+-Symbol Anbieter mit Methoden dar, die für verwalteten Code spezifisch sind.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Stellt einen com+-Symbol Anbieter mit spezifischen Methoden für verwalteten Code dar und erweitert den **idebugcomplussymbolprovider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Stellt ein Symbol oder einen Typ dar, bei dem es sich um einen Container für andere Symbole oder Typen handelt.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Stellt ein benutzerdefiniertes Attribut dar, das an ein Symbol angefügt werden kann.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Stellt eine Abfrage für benutzerdefinierte Attribute für eine Methode oder einen Typ dar.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Ermöglicht den Zugriff auf benutzerdefinierte Attribute für ein Symbol.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Die Basisschnittstelle für jeden Typ, der zur Laufzeit bestimmt werden kann.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Stellt ein dynamisches Feld für ein [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt dar.|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Stellt einen Enumerationstyp dar.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|El|Erweitert die Typen verfügbarer Felder, um verwaltete Code Generika zu unterstützen.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Die Basisklasse für alle Felder. stellt eine Beschreibung eines Symbols oder Typs dar.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Stellt die Definition eines Felds für einen generischen verwalteten Codetyp dar.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Stellt eine Instanz eines Felds für einen generischen verwalteten Codetyp dar.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Stellt einen Parameter für einen generischen Typ mit verwaltetem Code dar.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Stellt eine Methode dar.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Stellt einen optionalen Debug-Modifizierer dar.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Stellt einen Zeiger dar.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Stellt einen primitiven typenumerationswert aus einer [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle dar.|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Stellt eine Eigenschaft einer verwalteten Code Klasse dar, die erhalten oder festgelegt werden kann.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Stellt einen Symbol Anbieter dar, der Symbole und Typen bereitstellt.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Stellt einen Symbol Anbieter mit direktem Zugriff auf Metadaten und Kern Symbol Schnittstellen dar.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Stellt die Fähigkeit dar, ein Feld zu erstellen, das einen Typ darstellt.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Erweitert den **idebugtypefieldbuilder** , damit Array Typen erstellt werden können.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Stellt eine Auflistung von [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekten dar.|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Stellt eine Auflistung von [idebugcustomattribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) -Objekten dar.|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Stellt eine Auflistung von [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekten dar.|

## <a name="see-also"></a>Siehe auch
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
