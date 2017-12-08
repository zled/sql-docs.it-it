---
title: Azioni nei modelli multidimensionali | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- actions [Analysis Services], creating
- report actions [Analysis Services]
- drillthrough actions [Analysis Services]
- cubes [Analysis Services], actions
ms.assetid: b9fee2b9-05a5-4077-848d-d8457326dc27
caps.latest.revision: "20"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ce19f2ad400f0a3e01efae5fea89235905025414
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="actions-in-multidimensional-models"></a>Azioni nei modelli multidimensionali
  Un'azione è un'operazione inizializzata dall'utente finale su un cubo o una parte di un cubo selezionati. L'operazione consente di avviare un'applicazione con l'elemento selezionato come parametro oppure di recuperare informazioni sull'elemento selezionato. Per altre informazioni sulle azioni, vedere [Azioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
 Usare la scheda **Azioni** di Progettazione cubi per compilare azioni per un cubo. Specificare le opzioni seguenti:  
  
 **Nome**  
 Selezionare un nome che identifichi l'azione.  
  
 **Destinazione azione**  
 Selezionare l'oggetto a cui è associata l'azione. Nelle applicazioni client l'azione viene in genere visualizzata quando gli utenti finali selezionano l'oggetto di destinazione. Tuttavia, è l'applicazione client che determina quale operazione dell'utente finale attiva la visualizzazione delle azioni. In **Tipo di destinazione**scegliere tra gli oggetti seguenti:  
  
-   Membri dell'attributo  
  
-   Celle  
  
-   Cube  
  
-   Membri della dimensione  
  
-   Gerarchia  
  
-   Membri della gerarchia  
  
-   Level  
  
-   Membri del livello  
  
 Dopo aver selezionato il tipo di oggetto di destinazione, in **Oggetto di destinazione**selezionare l'oggetto del cubo del tipo definito.  
  
 **Condizione (facoltativa)**  
 Specificare un'espressione MDX (Multidimensional Expressions) facoltativa che restituisca un valore booleano. Se il valore è **True**, l'azione viene eseguita sulla destinazione specificata. Se invece il valore è **False**, l'azione non viene eseguita.  
  
 **Contenuto azione**  
 Selezionare il tipo di azione. Nella tabella seguente vengono riepilogati i tipi disponibili.  
  
|Tipo|Description|  
|----------|-----------------|  
|Set di dati|Consente di recuperare un set di dati.|  
|Proprietario|Esegue un'operazione utilizzando un'interfaccia diversa da quelle elencate in questa tabella.|  
|Set di righe|Consente di recuperare un set di righe.|  
|Istruzione|Esegue un comando OLE DB.|  
|URL|Visualizza una pagina variabile in un browser Internet.|  
  
 In **Espressione azione**specificare i parametri passati durante l'esecuzione dell'azione. Il risultato della valutazione della sintassi deve essere una stringa ed è necessario includere un'espressione MDX. Ad esempio, l'espressione MDX può indicare una parte del cubo inclusa nella sintassi. Le espressioni MDX vengono valutate prima del passaggio dei parametri. È inoltre disponibile Generatore MDX, che consente di compilare espressioni MDX in modo semplificato.  
  
 **Proprietà aggiuntive**  
 Selezionare la proprietà. Nella tabella seguente vengono riepilogate le proprietà disponibili.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Chiamata**|Specifica la modalità di esecuzione dell'azione. L'impostazione predefinita Interattiva specifica che l'azione viene eseguita quando un utente accede a un oggetto. Le impostazioni possibili sono:<br /><br /> Batch<br /><br /> Interattiva<br /><br /> Su apertura|  
|**Applicazione**|Descrive l'applicazione dell'azione.|  
|**Description**|Descrive l'azione.|  
|**Caption**|Visualizza una didascalia da associare all'azione. Se la didascalia è MDX, specificare **True** in **Didascalia MDX**.|  
|**Didascalia MDX**|Specificare **True** se la didascalia è MDX, in caso contrario specificare **False** .|  
  
> [!NOTE]  
>  Per definire i tipi di azione HTML e Riga di comando, è necessario utilizzare Analysis Services Scripting Language (ASSL) o la libreria AMO (Analysis Management Objects). Per altre informazioni, vedere [Elemento Action &#40;ASSL&#41;](../../analysis-services/scripting/objects/action-element-assl.md), [Elemento Type &#40;Action&#41; &#40;ASSL&#41;](../../analysis-services/scripting/properties/type-element-action-assl.md) e [Programmazione di oggetti avanzati OLAP in AMO](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-advanced-objects.md).  
  
## <a name="creating-a-reporting-action"></a>Creazione di un'azione report  
 Il server di report risponde alle richieste basate su URL relative ai report. Per creare un'azione report scegliere **Nuova azione report** dal menu **Cubo**. Le opzioni seguenti sono specifiche di un'azione report.  
  
 **Server di report**  
 Le proprietà descritte nella tabella seguente sono specifiche del server di report.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Nome server**|Nome del computer in cui il server di report è in esecuzione.|  
|**Percorso server**|Percorso esposto dal server di report.|  
|**Formato report**|HTML5, HTML3, Excel o PDF.|  
  
> [!NOTE]  
>  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]è possibile specificare Transport Layer Security (https:) nella proprietà nome server.  
  
 **Parametri (facoltativi)**  
 I parametri vengono inviati al server come parte della stringa dell'URL quando viene creata l'azione. Includono **Nome parametro** e **Valore parametro**, che è un'espressione MDX.  
  
 L'URL del server di report viene creato nel modo seguente:  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 Esempio:  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a>Creazione di un'azione drill-through  
 Un'azione drill-through viene definita da un'azione set di righe, che a sua volta viene restituita all'applicazione client come istruzione drill-through. La destinazione dell'azione è membro di un gruppo di misure. Per creare una nuova azione drill-through, scegliere **Nuova azione drill-through** dal menu **Cubo**. Le opzioni seguenti sono specifiche di un'azione drill-through.  
  
 **Colonne drill-through**  
 Selezionare una o più dimensioni e per ogni dimensione selezionare le colonne drill-through restituite all'applicazione client dall'azione.  
  
## <a name="see-also"></a>Vedere anche  
 [Cubi nei modelli multidimensionali](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
