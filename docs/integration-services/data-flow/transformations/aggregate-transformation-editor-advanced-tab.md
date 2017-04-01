---
title: "Editor trasformazione Aggregazione (scheda Avanzate) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.aggregationtransformation.advanced.f1"
helpviewer_keywords: 
  - "Editor trasformazione Aggregazione"
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Editor trasformazione Aggregazione (scheda Avanzate)
  Usare la scheda **Avanzate** della finestra di dialogo **Editor trasformazione Aggregazione** per impostare le proprietà dei componenti, specificare le aggregazioni, nonché impostare le proprietà delle colonne di input e output.  
  
> [!NOTE]  
>  Le opzioni per il conteggio delle chiavi, la scala delle chiavi, il conteggio delle chiavi distinct e la scala delle chiavi distinct vengono applicate a livello di componente quando vengono specificate nella scheda **Avanzate**, a livello di output quando vengono specificate nella sezione delle opzioni avanzate della scheda **Aggregazioni** e a livello di colonna quando vengono specificate nell'elenco delle colonne nella parte inferiore della scheda **Aggregazioni**.  
>   
>  Nella trasformazione Aggregazione **Chiavi** e **Scala chiavi** fanno riferimento al numero di gruppi che dovrebbero risultare da un'operazione **Group by**. **Chiavi conteggio valori distinct** e **Scala conteggio valori distinct** fanno riferimento al numero di valori distinct che dovrebbero risultare da un'operazione **Distinct count**.  
  
 Per altre informazioni sulla trasformazione Aggregazione, vedere [Trasformazione Aggregazione](../../../integration-services/data-flow/transformations/aggregate-transformation.md).  
  
## Opzioni  
 **Scala chiavi**  
 Consente di specificare facoltativamente il numero approssimativo di chiavi previste dall'aggregazione. La trasformazione utilizza tale informazione per ottimizzare la dimensione iniziale della cache. Per impostazione predefinita, il valore di questa opzione è **Non specificata**. Se vengono specificate sia **Scala chiavi** sia **Numero di chiavi**, quest'ultima** ** ha priorità.  
  
|Valore|Description|  
|-----------|-----------------|  
|Non specificato|La proprietà **Scala chiavi** non viene usata.|  
|Basso|L'aggregazione può scrivere circa 500.000 chiavi.|  
|Media|L'aggregazione può scrivere circa 5.000.000 di chiavi.|  
|Alto|L'aggregazione può scrivere oltre 25.000.000 di chiavi.|  
  
 **Numero di chiavi**  
 Consente di specificare facoltativamente il numero esatto di chiavi previste dall'aggregazione. La trasformazione utilizza tale informazione per ottimizzare la dimensione iniziale della cache. Se vengono specificate sia **Scala chiavi** sia **Numero di chiavi**, quest'ultima** **ha priorità.  
  
 **Scala conteggio valori distinct**  
 È possibile specificare il numero approssimativo di valori distinct che l'aggregazione può scrivere. Per impostazione predefinita, il valore di questa opzione è **Non specificata**. Se vengono specificate sia **Scala conteggio valori distinct** sia **Chiavi conteggio valori distinct**, quest'ultima** **ha priorità.  
  
|Valore|Description|  
|-----------|-----------------|  
|Non specificato|La proprietà CountDistinctScale non viene utilizzata.|  
|Basso|L'aggregazione può scrivere circa 500.000 valori distinct.|  
|Media|L'aggregazione può scrivere circa 5.000.000 di valori distinct.|  
|Alto|L'aggregazione può scrivere oltre 25.000.000 di valori distinct.|  
  
 **Chiavi conteggio valori distinct**  
 È possibile specificare il numero esatto di valori distinct che l'aggregazione può scrivere. Se vengono specificate sia **Scala conteggio valori distinct** sia **Chiavi conteggio valori distinct**, quest'ultima** **ha priorità.  
  
 **Fattore di estensione automatica**  
 Consente di utilizzare un valore compreso tra 1 e 100 per specificare la percentuale di estensione possibile della memoria durante l'aggregazione. Il valore predefinito di questa opzione è **25%**.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Aggregazione &#40;scheda Aggregazioni&#41;](../../../integration-services/data-flow/transformations/aggregate-transformation-editor-aggregations-tab.md)   
 [Aggregazione di valori in un set di dati utilizzando la trasformazione Aggregazione](../../../integration-services/data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  