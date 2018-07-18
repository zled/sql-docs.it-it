---
title: Funzione CountRows (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 86b8b79fc5bcac1842a4fae82535afdff06c305e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280267"
---
# <a name="countrows-function-report-builder-and-ssrs"></a>Funzione CountRows (Generatore report e SSRS)
  Restituisce il numero di righe nell'ambito specificato, incluse le righe con valori Null.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ambito*  
 (`String`) Nome di un set di dati, area dati o gruppo che contiene gli elementi del report da conteggiare.  
  
 *ricorsivi*  
 (**Enumerated Type**) Facoltativo. `Simple` (impostazione predefinita) o `RdlRecursive`. Specifica se eseguire l'aggregazione in modo ricorsivo.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un `Integer`.  
  
## <a name="remarks"></a>Note  
 `CountRows` conteggia tutte le righe nell'ambito specificato, incluse le righe con valori null.  
  
 Il valore di *scope* non può essere un'espressione e deve fare riferimento all'ambito corrente o a un ambito di contenuto.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente è illustrata un'espressione che calcola il numero di righe in un gruppo di righe denominato `GroupbyCategory` (in base all'espressione `[Category]`).  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle espressioni nei report di &#40;Report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
