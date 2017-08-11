---
title: Funzione CountRows (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 0d15d79a57e1a08a251fc7e46b615fec7e94730d
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---countrows-function"></a>Report Builder funzioni - funzione CountRows
  Restituisce il numero di righe nell'ambito specificato, incluse le righe con valori Null.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ambito*  
 (**String**) Nome di un set di dati, area dati o gruppo che contiene gli elementi del report da conteggiare.  
  
 *ricorsivi*  
 (**Enumerated Type**) Facoltativo. **Simple** (impostazione predefinita) o **RdlRecursive**. Specifica se eseguire l'aggregazione in modo ricorsivo.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un valore **Integer**.  
  
## <a name="remarks"></a>Osservazioni  
 **CountRows** conteggia tutte le righe nell'ambito specificato, incluse le righe con valori Null.  
  
 Il valore di *scope* non può essere un'espressione e deve fare riferimento all'ambito corrente o a un ambito di contenuto.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente è illustrata un'espressione che calcola il numero di righe in un gruppo di righe denominato `GroupbyCategory` (in base all'espressione `[Category]`).  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati in espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
