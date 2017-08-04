---
title: Editor trasformazione (scheda Avanzate) di aggregazione | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 770920407115e5c8b7fa434ad8499bc801371e5f
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="aggregate-transformation-editor-advanced-tab"></a>Editor trasformazione Aggregazione (scheda Avanzate)
  Usare la scheda **Avanzate** della finestra di dialogo **Editor trasformazione Aggregazione** per impostare le proprietà dei componenti, specificare le aggregazioni, nonché impostare le proprietà delle colonne di input e output.  
  
> [!NOTE]  
>  Le opzioni per il conteggio delle chiavi, la scala delle chiavi, il conteggio delle chiavi distinct e la scala delle chiavi distinct vengono applicate a livello di componente quando vengono specificate nella scheda **Avanzate** , a livello di output quando vengono specificate nella sezione delle opzioni avanzate della scheda **Aggregazioni** e a livello di colonna quando vengono specificate nell'elenco delle colonne nella parte inferiore della scheda **Aggregazioni** .  
>   
>  Nella trasformazione Aggregazione, **Chiavi** e **Scala chiavi** fanno riferimento al numero di gruppi che dovrebbero risultare da un'operazione **Group by** . **Chiavi conteggio valori distinct** e **Scala conteggio valori distinct** fanno riferimento al numero di valori distinct che dovrebbero risultare da un'operazione **Distinct count** .  
  
 Per altre informazioni sulla trasformazione Aggregazione, vedere [Trasformazione Aggregazione](../../../integration-services/data-flow/transformations/aggregate-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Scala chiavi**  
 Consente di specificare facoltativamente il numero approssimativo di chiavi previste dall'aggregazione. La trasformazione utilizza tale informazione per ottimizzare la dimensione iniziale della cache. Per impostazione predefinita, il valore di questa opzione è **Non specificata**. Se vengono specificate sia **Scala chiavi** sia **Numero di chiavi** , quest'ultima ****  ha priorità.  
  
|Valore|Description|  
|-----------|-----------------|  
|Non specificata|La proprietà **Scala chiavi** non viene usata.|  
|Basso|L'aggregazione può scrivere circa 500.000 chiavi.|  
|Media|L'aggregazione può scrivere circa 5.000.000 di chiavi.|  
|Alto|L'aggregazione può scrivere oltre 25.000.000 di chiavi.|  
  
 **Numero di chiavi**  
 Consente di specificare facoltativamente il numero esatto di chiavi previste dall'aggregazione. La trasformazione utilizza tale informazione per ottimizzare la dimensione iniziale della cache. Se vengono specificate sia **Scala chiavi** sia **Numero di chiavi** , quest'ultima ****  ha priorità.  
  
 **Scala conteggio valori distinct**  
 È possibile specificare il numero approssimativo di valori distinct che l'aggregazione può scrivere. Per impostazione predefinita, il valore di questa opzione è **Non specificata**. Se vengono specificate sia **Scala conteggio valori distinct** sia **Chiavi conteggio valori distinct** , quest'ultima ****  ha priorità.  
  
|Valore|Description|  
|-----------|-----------------|  
|Non specificata|La proprietà CountDistinctScale non viene utilizzata.|  
|Basso|L'aggregazione può scrivere circa 500.000 valori distinct.|  
|Media|L'aggregazione può scrivere circa 5.000.000 di valori distinct.|  
|Alto|L'aggregazione può scrivere oltre 25.000.000 di valori distinct.|  
  
 **Chiavi conteggio valori distinct**  
 È possibile specificare il numero esatto di valori distinct che l'aggregazione può scrivere. Se vengono specificate sia **Scala conteggio valori distinct** sia **Chiavi conteggio valori distinct** , quest'ultima ****  ha priorità.  
  
 **Fattore di estensione automatica**  
 Consente di utilizzare un valore compreso tra 1 e 100 per specificare la percentuale di estensione possibile della memoria durante l'aggregazione. Il valore predefinito di questa opzione è **25%**.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione aggregazione &#40; Scheda aggregazioni &#41;](../../../integration-services/data-flow/transformations/aggregate-transformation-editor-aggregations-tab.md)   
 [Aggregazione di valori in un set di dati tramite la trasformazione aggregazione](../../../integration-services/data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
