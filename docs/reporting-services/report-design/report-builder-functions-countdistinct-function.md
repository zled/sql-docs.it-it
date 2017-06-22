---
title: Funzione CountDistinct (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: 902c251e-e1e8-41d2-ac20-5bb6138ac410
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e776103071948932319097633210603bc9b9dcc3
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="report-builder-functions---countdistinct-function"></a>Report Builder funzioni - funzione CountDistinct
  Restituisce un conteggio di tutti i distinti valori non Null specificati dall'espressione, valutato nel contesto dell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CountDistinct(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parametri  
 *espressione*  
 (**Variant**) Espressione su cui eseguire l'aggregazione.  
  
 *ambito*  
 (**String**) Facoltativo. Nome di un set di dati, gruppo o area dati che contiene gli elementi del report a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
 *ricorsivi*  
 (**Enumerated Type**) Facoltativo. **Simple** (impostazione predefinita) o **RdlRecursive**. Specifica se eseguire l'aggregazione in modo ricorsivo.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un valore **Integer**.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di *scope* deve essere una costante di tipo stringa e non può essere un'espressione. Per aggregazioni o aggregazioni esterne che non specificano altre aggregazioni, *scope* deve fare riferimento all'ambito corrente o a un ambito contenitore. Per le aggregazioni di aggregazioni, le aggregazioni nidificate possono specificare un ambito figlio.  
  
 *Expression* può contenere chiamate alle funzioni di aggregazione nidificate con le eccezioni e le condizioni seguenti:  
  
-   *Scope* per le aggregazioni nidificate deve corrispondere o essere contenuto nell'ambito dell'aggregazione esterna. Per tutti gli ambiti distinti nell'espressione, un ambito deve essere in una relazione figlio con tutti gli altri ambiti.  
  
-   *Scope* per le aggregazioni nidificate non può essere il nome di un set di dati.  
  
-   *Expression* non deve contenere funzioni **First**, **Last**, **Previous**o **RunningValue** .  
  
-   *Expression* non deve contenere aggregazioni nidificate che specificano *recursive*.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un'espressione che calcola il numero di valori non Null univoci di `Size` per l'ambito predefinito e per un ambito di gruppo padre. L'espressione viene aggiunta in una riga di una cella che appartiene al gruppo figlio `GroupbySubcategory`. Il gruppo padre è `GroupbyCategory`. L'espressione visualizza i risultati per `GroupbySubcategory` (ambito predefinito) e quindi per `GroupbyCategory` (ambito del gruppo padre).  
  
> [!NOTE]  
>  Le espressioni non devono contenere ritorni a capo e interruzioni di riga, che sono inclusi nell'esempio di codice per supportare i renderer della documentazione. Se si copia l'esempio seguente, rimuovere i ritorni a capo da ogni riga.  
  
```  
="Distinct count (Subcategory): " & CountDistinct(Fields!Size.Value) &   
"Distinct count (Category): " & CountDistinct(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
