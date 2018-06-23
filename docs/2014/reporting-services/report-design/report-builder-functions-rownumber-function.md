---
title: Funzione RowNumber (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 150a46a736a9c6ddd2f8c394f3f173906cd07132
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065044"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a>Funzione RowNumber (Generatore report e SSRS)
  Restituisce il conteggio parziale del numero di righe per l'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ambito*  
 (`String`) Il nome di un set di dati, area dati, gruppo o null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), che specifica il contesto in cui valutare il numero di righe. `Nothing` Specifica il contesto più esterno, generalmente il set di dati di report.  
  
## <a name="remarks"></a>Remarks  
 `RowNumber` Restituisce il valore corrente del conteggio delle righe all'interno dell'ambito specificato, così come [RunningValue](report-builder-functions-runningvalue-function.md) restituisce il valore corrente di una funzione di aggregazione. Durante la definizione di un ambito, si specifica quando reimpostare il conteggio delle righe su 1.  
  
 *scope* non può essere un'espressione. Il parametro*scope* deve essere un ambito contenitore. I tipici ambiti, dal contenuto più esterno fino al più interno, sono set di dati di report, aree dati, gruppi di righe o di colonne.  
  
 Per incrementare i valori nelle colonne, specificare un ambito che corrisponde al nome di un gruppo di colonne. Per incrementare i numeri verso il basso delle righe, specificare un ambito che corrisponde al nome di un gruppo di righe.  
  
> [!NOTE]  
>  Non è possibile includere aggregazioni che specificano sia un gruppo di righe che un gruppo di colonne in un'unica espressione.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="code-example"></a>Esempio di codice  
 È riportata un'espressione che è possibile utilizzare per il `BackgroundColor` proprietà di una riga di dettaglio area dati Tablix per alternare il colore delle righe di dettaglio per ogni gruppo, sempre partire dal bianco.  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressione viene utilizzata nei report di &#40;SSRS e Generatore Report&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;SSRS e Generatore Report&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  