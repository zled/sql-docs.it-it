---
title: CursorTypeEnum | Documenti Microsoft
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
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6875e6b2b967cf73511c73bf4ca7cdafed21557b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cursortypeenum"></a>CursorTypeEnum
Specifica il tipo di cursore utilizzato in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**Impostare**|2|Utilizza un cursore dinamico. Aggiunte, modifiche ed eliminazioni da altri utenti sono visibili e tutti i tipi di spostamento all'interno di **Recordset** sono consentiti, ad eccezione dei segnalibri, se il provider non li supporta.|  
|**adOpenForwardOnly**|0|Valore predefinito. Utilizza un cursore forward-only. Identico a un cursore statico, ad eccezione del fatto che può solo lo scorrimento in avanti di record. Ciò migliora le prestazioni quando è necessario apportare solo una passano attraverso un **Recordset**.|  
|**adOpenKeyset**|1|Utilizza un cursore keyset. Ad esempio un cursore dinamico, ad eccezione del fatto che non è possibile visualizzare i record aggiunti da altri utenti, anche se i record eliminati dagli altri utenti non sono accessibili dal **Recordset**. Le modifiche dei dati da altri utenti sono ancora visibili.|  
|**adOpenStatic**|3|Utilizza un cursore statico, ovvero una copia statica di un set di record che è possibile utilizzare per trovare i dati o di generare report. Le aggiunte, modifiche o le eliminazioni eseguite da altri utenti non sono visibili.|  
|**adOpenUnspecified**|-1|Non specifica il tipo di cursore.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)

