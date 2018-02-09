---
title: "Proprietà DefinedSize | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Field20::DefinedSize
helpviewer_keywords:
- DefinedSize property [ADO]
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 44c44b0dd7528634cc6db88b3d5bb04a8a1237e3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="definedsize-property"></a>Proprietà DefinedSize
Indica la capacità di dati di un [campo](../../../ado/reference/ado-api/field-object.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **lungo** valore che corrisponde alle dimensioni definite di un campo, che dipende dal tipo di dati dell'oggetto campo, vedere [tipo](../../../ado/reference/ado-api/type-property-ado.md) per ulteriori informazioni. Per un campo che utilizza un tipo di dati a lunghezza fissa, il valore restituito è la dimensione del tipo di dati in byte. Per un campo che utilizza un tipo di dati a lunghezza variabile, questa è una delle operazioni seguenti:  
  
1.  La lunghezza massima del campo in caratteri (per **adVarChar** e **adVarWChar**) o in byte (per **adVarBinary**, e **adVarNumeric**) se il campo ha una lunghezza definita. Ad esempio, **adVarChar(5)** campo ha una lunghezza massima di 5.  
  
2.  La lunghezza massima del tipo di dati in caratteri (per **famiglia** e **adWChar**) o in byte (per **adBinary** e **adNumeric**) se il campo non dispone di una lunghezza definita.  
  
3.  ~ 0 (OR bit per bit, il valore non è 0; tutti i bit sono impostati su 1) se il campo né il tipo di dati ha una lunghezza massima definita.  
  
4.  Per tipi di dati che non hanno una lunghezza è impostato su ~ 0 (OR bit per bit, il valore non è 0; tutti i bit sono impostati su 1).  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **DefinedSize** proprietà per determinare la capacità di dati di un **campo** oggetto.  
  
 Il **DefinedSize** e [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) le proprietà sono diverse. Si consideri ad esempio un **campo** oggetto con un tipo dichiarato di **adVarChar** e **DefinedSize** valore della proprietà di 50, contenente un singolo carattere. Il **ActualSize** valore restituito della proprietà è la lunghezza in byte del carattere singolo.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio ActualSize e DefinedSize proprietà (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Esempio ActualSize e DefinedSize proprietà (VC + +)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Proprietà ActualSize (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)
