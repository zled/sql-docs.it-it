---
title: Livello di funzione (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 171842909a300d0c98fca2a26bbf4567810e8e95
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---level-function"></a>Funzioni di Generatore report - funzione Level
  Restituisce il livello di nidificazione corrente in una gerarchia ricorsiva.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ambito*  
 (**String**) Facoltativo. Nome di un set di dati, gruppo o area dati che contiene gli elementi del report a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un valore **Integer**. Se il parametro *scope* specifica un set di dati o un'area dati oppure un raggruppamento non ricorsivo, ovvero un raggruppamento privo dell'elemento **Parent** , **Level** restituirà 0. Se *scope* viene omesso, restituisce il livello dell'ambito corrente.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore restituito dalla funzione **Level** è a base zero, ovvero il primo livello di una gerarchia viene indicato con 0.  
  
 È possibile utilizzare la funzione **Level** per consentire l'applicazione dei rientri in una gerarchia ricorsiva, ad esempio un elenco di dipendenti.  
  
 Per altre informazioni sulle gerarchie ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente consente di ottenere il livello di riga nel gruppo Employees:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati in espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
