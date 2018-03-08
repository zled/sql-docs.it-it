---
title: "Proprietà OriginalValue (ADO) | Documenti Microsoft"
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
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8cc3597b6f3b476a889f836ae899f558b38eff20
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="originalvalue-property-ado"></a>Proprietà OriginalValue (ADO)
Indica il valore di un [campo](../../../ado/reference/ado-api/field-object.md) che era presente nel record prima che eventuali modifiche apportate.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Variant** valore che rappresenta il valore di un campo prima di qualsiasi modifica.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **OriginalValue** proprietà per restituire il valore originale per un campo del record corrente.  
  
 In *modalità di aggiornamento immediato* (in cui il provider scrive le modifiche all'origine dati sottostante dopo la chiamata di [aggiornare](../../../ado/reference/ado-api/update-method.md) metodo), il **OriginalValue** restituisce proprietà il valore di campo esistente prima di tutte le modifiche (ovvero, dopo l'ultimo **aggiornamento** chiamata al metodo). Questo è lo stesso valore che il [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) metodo utilizzato per sostituire il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà.  
  
 In *modalità di aggiornamento batch* (in cui il provider memorizza nella cache più modifiche e li scrive all'origine dati sottostante solo quando si chiama il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo), il **OriginalValue** proprietà restituisce il valore di campo esistente prima di tutte le modifiche (ovvero, dopo l'ultimo **UpdateBatch** chiamata al metodo). Questo è lo stesso valore che il [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodo utilizzato per sostituire il **valore** proprietà. Quando si utilizza questa proprietà con il [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) proprietà, è possibile risolvere i conflitti generati dagli aggiornamenti in batch.  
  
## <a name="record"></a>Record  
 Per [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetti, il **OriginalValue** proprietà sarà vuota per i campi aggiunti prima [aggiornamento](../../../ado/reference/ado-api/update-method.md) viene chiamato.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio OriginalValue e UnderlyingValue proprietà (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Esempio OriginalValue e UnderlyingValue proprietà (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Proprietà UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
