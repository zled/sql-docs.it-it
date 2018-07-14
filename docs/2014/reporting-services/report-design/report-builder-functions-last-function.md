---
title: Funzione Last (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 123b78a0-d6c9-4f78-b0e7-73b21854a250
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b241374ed21e3e0ab004c5c29c4442f1dc4dcb88
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166242"
---
# <a name="last-function-report-builder-and-ssrs"></a>Funzione Last (Generatore report e SSRS)
  Restituisce l'ultimo valore nell'ambito specificato dell'espressione specificata.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Last(expression, scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *expression*  
 (`Variant` oppure `Binary`) espressione su cui eseguire l'aggregazione, ad esempio, `=Fields!Fieldname.Value`.  
  
 *ambito*  
 (`String`) (Facoltativo) Nome di un set di dati, area dati o gruppo che contiene gli elementi del report a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
## <a name="return-type"></a>Tipo restituito  
 Determinato dal tipo di espressione.  
  
## <a name="remarks"></a>Note  
 La funzione `Last` restituisce il valore finale di un set di dati dopo l'applicazione di tutti i criteri di ordinamento e di filtro all'ambito specificato.  
  
 Il `Last` funzione non può essere utilizzata nelle espressioni di filtro di gruppo con altri ambiti ad eccezione dell'ambito corrente (predefinito).  
  
 È anche possibile usare `Last` in un'intestazione di pagina per restituire l'ultimo valore di `ReportItems` raccolta per una pagina in modo da creare intestazioni in formato dizionario che visualizzano la voce e il cognome in una pagina.  
  
 Il valore di *scope* deve essere una costante di tipo stringa e non può essere un'espressione. Per aggregazioni o aggregazioni esterne che non specificano altre aggregazioni, *scope* deve fare riferimento all'ambito corrente o a un ambito contenitore. Per le aggregazioni di aggregazioni, le aggregazioni nidificate possono specificare un ambito figlio.  
  
 *Expression* può contenere chiamate alle funzioni di aggregazione nidificate con le eccezioni e le condizioni seguenti:  
  
-   *Scope* per le aggregazioni nidificate deve corrispondere o essere contenuto nell'ambito dell'aggregazione esterna. Per tutti gli ambiti distinti nell'espressione, un ambito deve essere in una relazione figlio con tutti gli altri ambiti.  
  
-   *Scope* per le aggregazioni nidificate non può essere il nome di un set di dati.  
  
-   *Espressione* non deve contenere `First`, `Last`, `Previous`, o `RunningValue` funzioni.  
  
-   *Expression* non deve contenere aggregazioni nidificate che specificano *recursive*.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente restituisce l'ultimo numero di prodotto nel gruppo o nell'area dati `Category` .  
  
```  
=Last(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle espressioni nei report di &#40;Report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
