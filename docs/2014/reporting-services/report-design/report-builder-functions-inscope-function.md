---
title: Funzione InScope (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ebf90710587c73206408dfda1429a90b58f39621
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228841"
---
# <a name="inscope-function-report-builder-and-ssrs"></a>Funzione InScope (Generatore report e SSRS)
  Indica se l'istanza corrente di un elemento è inclusa nell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ambito*  
 (`String`) Il nome di un set di dati, area dati o gruppo che specifica un ambito.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un `Boolean`.  
  
## <a name="remarks"></a>Note  
 Il `InScope` funzione testa l'ambito dell'istanza corrente di un elemento del report per l'appartenenza nell'ambito specificato per il *ambito*parametro.  
  
 *Scope* non può essere un'espressione.  
  
 Un utilizzo tipico di `InScope` funzione sia nelle aree dati sono dinamici dell'ambito. Ad esempio, `InScope` può essere utilizzato in un collegamento drill-through nelle celle di un'area dati per fornire nome e diversi set di parametri a seconda della cella sulla quale viene fatto clic su un altro report. Di seguito viene riportato un esempio:  
  
-   L'espressione seguente, usata come nome del report in un collegamento drill-through, apre il report `ProductDetail` se la cella su cui si fa clic si trova nel gruppo `Month` e il report `ProductSummary` in caso contrario.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   L'espressione seguente, usato nel `Omit` proprietà di un parametro di report drill-through, passerà il parametro al report di destinazione solo se la cella selezionata è nel `Product` gruppo.  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Esempio  
 Il codice di esempio seguente indica se l'istanza corrente dell'elemento si trova nell'ambito del set di dati, area dati o gruppo `Product` .  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle espressioni nei report di &#40;Report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
