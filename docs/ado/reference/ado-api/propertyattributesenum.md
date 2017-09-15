---
title: PropertyAttributesEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6614f74546fab23a1e1ce453ac12c10082011a25
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Specifica gli attributi di un [proprietà](../../../ado/reference/ado-api/property-object-ado.md) oggetto.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|Indica che la proprietà non è supportata dal provider.|  
|**adPropRequired**|1|Indica che l'utente deve specificare un valore per questa proprietà prima di inizializzata l'origine dati.|  
|**adPropOptional**|2|Indica che l'utente non devono specificare un valore per questa proprietà prima di inizializzata l'origine dati.|  
|**adPropRead**|512|Indica che l'utente può leggere la proprietà.|  
|**adPropWrite**|1024|Indica che l'utente può impostare la proprietà.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.PropertyAttributes.NOTSUPPORTED|  
|AdoEnums.PropertyAttributes.REQUIRED|  
|AdoEnums.PropertyAttributes.OPTIONAL|  
|AdoEnums.PropertyAttributes.READ|  
|AdoEnums.PropertyAttributes.WRITE|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
