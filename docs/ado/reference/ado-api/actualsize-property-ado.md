---
title: "Proprietà ActualSize (ADO) | Documenti Microsoft"
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
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d66019d7a71dd480f1a88a28fe94d72a176497c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="actualsize-property-ado"></a>Proprietà ActualSize (ADO)
Indica la lunghezza effettiva di un campo??? valore s in byte.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce un **lungo** valore.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **ActualSize** proprietà per restituire la lunghezza effettiva di un [campo](../../../ado/reference/ado-api/field-object.md) valore dell'oggetto. Per tutti i campi, il **ActualSize** proprietà è di sola lettura. Se ADO non è possibile determinare la lunghezza del **campo** il valore dell'oggetto, il **ActualSize** restituisce proprietà **adUnknown**.  
  
 Il **ActualSize** e [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) le proprietà sono diverse, come illustrato nell'esempio seguente. Oggetto **campo** oggetto con un tipo dichiarato di **adVarChar** e una lunghezza massima di 50 caratteri restituisce un **DefinedSize** valore della proprietà di 50, ma la  **ActualSize** valore restituito della proprietà è la lunghezza dei dati archiviati nel campo del record corrente. **Campi** con un **DefinedSize** maggiori di 255 byte vengono considerati come colonne di lunghezza variabile.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio ActualSize e DefinedSize proprietà (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Esempio ActualSize e DefinedSize proprietà (VC + +)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Proprietà DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)

