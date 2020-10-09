---
title: Ungültiges Replacer-Argument | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6a77675a1cb618210d9c44104cf6397dda03c11
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862560"
---
# <a name="invalid-replacer-argument"></a>Ungültiges replacer-Argument
Es wurde versucht, mit einem ungültigen Argument aufzurufen `JSON.stringify` . Das `replacer` Argument muss eine Funktion oder ein Array sein.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Ändern Sie das- `replacer` Argument in eine Funktion oder ein Array.  
  
## <a name="example"></a>Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, da `memberfilter` ein Objekt anstelle einer Funktion oder eines Arrays ist.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [JSON-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Analyse-Funktion](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript-Laufzeitfehler](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)