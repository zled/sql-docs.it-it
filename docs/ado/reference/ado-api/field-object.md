---
title: Oggetto Field | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 27956d93b6c27b44758281043a1742eed7ce5d79
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="field-object"></a>Oggetto Field
Rappresenta una colonna di dati con un tipo di dati.  
  
## <a name="remarks"></a>Osservazioni  
 Ogni **campo** oggetto corrisponde a una colonna di [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Utilizzare il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà di **campo** oggetti per impostare o restituire dati per il record corrente. A seconda della funzionalità espone il provider, alcuni insiemi, metodi o proprietà di un **campo** oggetto potrebbe non essere disponibile.  
  
 Con le raccolte, i metodi e proprietà di un **campo** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Restituire il nome di un campo con il [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà.  
  
-   Consente di visualizzare o modificare i dati nel campo con il **valore** proprietà. **Valore** è la proprietà predefinita di **campo** oggetto.  
  
-   Restituire le caratteristiche di base di un campo con il [tipo](../../../ado/reference/ado-api/type-property-ado.md), [precisione](../../../ado/reference/ado-api/precision-property-ado.md), e [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) proprietà.  
  
-   Restituire le dimensioni dichiarate di un campo con il [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) proprietà.  
  
-   Restituire la dimensione effettiva dei dati in un determinato campo con il [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) proprietà.  
  
-   Determinare i tipi di funzionalità sono supportati per un determinato campo con il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà e [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
-   Modificare i valori dei campi che contengono dati binari lungo o long character con il [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) e [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) metodi.  
  
-   Se il provider supporta gli aggiornamenti in batch, è possibile risolvere le differenze tra i valori dei campi durante l'aggiornamento in batch con il [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) e [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) proprietà.  
  
 Tutte le proprietà dei metadati (**nome**, **tipo**, **DefinedSize**, **precisione**, e **NumericScale**) sono disponibili prima dell'apertura di **campo** dell'oggetto **Recordset**. Impostarli in quel momento è utile per la creazione dinamica di form.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà dell'oggetto campo, metodi ed eventi](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
