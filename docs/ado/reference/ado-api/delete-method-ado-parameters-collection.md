---
title: Metodo Delete (insieme Parameters ADO) | Documenti Microsoft
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
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 770271da0c0b2b378adf2be5611428e05f7f5148
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-ado-parameters-collection"></a>Metodo Delete (insieme Parameters ADO)
Elimina un oggetto di [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Parametri  
 *Indice*  
 Oggetto **stringa** valore contenente il nome dell'oggetto a cui si desidera eliminare, o la posizione ordinale dell'oggetto (indice) nella raccolta.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzo di **eliminare** metodo in una raccolta consente di rimuovere uno degli oggetti nella raccolta. Questo metodo è disponibile solo per il **parametri** raccolta di un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto. È necessario utilizzare il [parametro](../../../ado/reference/ado-api/parameter-object.md) dell'oggetto [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà o l'indice di raccolta quando si chiama il **eliminare** metodo, una variabile oggetto non è un argomento valido.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Delete (insieme Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete (metodo) (Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Metodo DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)

