---
title: Funzione Level (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 0ae9006603a9c76e9e7cbd308275c4f8a8c7594b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109513"
---
# <a name="level-function-report-builder-and-ssrs"></a>Funzione Level (Generatore report e SSRS)
  Restituisce il livello di nidificazione corrente in una gerarchia ricorsiva.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ambito*  
 (`String`) (Facoltativo). Nome di un set di dati, gruppo o area dati che contiene gli elementi del report a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un `Integer`. Se *ambito* specifica una set di dati o un'area dati oppure un raggruppamento non ricorsivo (vale a dire un raggruppamento con nessun `Parent` elemento), `Level` restituisce 0. Se *scope* viene omesso, restituisce il livello dell'ambito corrente.  
  
## <a name="remarks"></a>Note  
 Il valore restituito dalla funzione `Level` è a base zero, ovvero il primo livello di una gerarchia viene indicato con 0.  
  
 È possibile utilizzare la funzione `Level` per consentire l'applicazione dei rientri in una gerarchia ricorsiva, ad esempio un elenco di dipendenti.  
  
 Per altre informazioni sulle gerarchie ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente consente di ottenere il livello di riga nel gruppo Employees:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle espressioni nei report di &#40;Report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
