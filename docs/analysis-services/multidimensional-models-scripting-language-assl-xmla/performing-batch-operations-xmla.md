---
title: Esecuzione di operazioni Batch (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 509554d21fc56088d5be341cd828b8b8ed8e3d60
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="performing-batch-operations-xmla"></a>Esecuzione di operazioni batch (XMLA)
  È possibile utilizzare il [Batch](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) in XML for Analysis (XMLA) per eseguire più comandi XMLA utilizzando un unico comando [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) metodo. È possibile eseguire più comandi contenuti nel **Batch** comando come una singola transazione o in transazioni separate per ogni comando, in serie o in parallelo. È inoltre possibile specificare associazioni out-of-line e altre proprietà di **Batch** comando per l'elaborazione di più [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oggetti.  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>Esecuzione di comandi Batch transazionali e non transazionali  
 Il **Batch** comando esegue comandi in uno dei due modi:  
  
 **Transazionale**  
 Se il **transazione** attributo del **Batch** comando è impostato su true, il **Batch** comandi eseguito tutti i comandi contenuti dal comando di **Batch** comando in una singola transazione, ovvero un *transazionale* batch.  
  
 Se un comando non riesce in un batch transazionale, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rollback di qualsiasi comando nel **Batch** comando eseguito prima del comando non riuscito e **Batch** comando termina immediatamente. In tutti i comandi di **Batch** non vengono eseguiti i comandi che non hanno ancora eseguito. Dopo il **Batch** comando termina, il **Batch** comando segnala gli errori che si sono verificati per il comando non riuscito.  
  
 **Non transazionale**  
 Se il **transazione** attributo è impostato su false, il **Batch** comando viene eseguito ogni comando contenuto il **Batch** comando in una transazione separata, ovvero un  *non transazionale* batch. Se un comando non riesce in un batch non transazionale, il **Batch** comando continua a eseguire i comandi successivi al comando non riuscito. Dopo il **Batch** comando tenta di eseguire tutti i comandi che il **Batch** comando contiene, il **Batch** comando segnala gli errori che si è verificato.  
  
 Tutti i risultati restituiti dai comandi contenuti in un **Batch** comando vengono restituiti nello stesso ordine in cui sono contenuti i comandi nel **Batch** comando. I risultati restituiti da una **Batch** comando variano a seconda che il **Batch** comando è transazionale o non transazionale.  
  
> [!NOTE]  
>  Se un **Batch** comando contiene un comando che non restituisce output, ad esempio il [blocco](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) comando e comando viene eseguito correttamente, il **Batch** comando restituisce un oggetto vuoto [radice](../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento all'interno dell'elemento di risultati. Vuoto **radice** elemento garantisce che ogni comando contenuto un **Batch** comando è possibile associare appropriata **radice** elemento per i risultati del comando.  
  
### <a name="returning-results-from-transactional-batch-results"></a>Restituzione di risultati di un batch transazionale  
 Risultati di comandi eseguiti all'interno di un batch transazionale non vengono restituiti fino a quando l'intero **Batch** comando viene completato. I risultati non vengono restituiti dopo ogni comando viene eseguito poiché qualsiasi comando che non riesce in un batch transazionale provocherebbe l'intero **Batch** comando e tutti i comandi che contiene il rollback. Se tutti i comandi avviare ed eseguire correttamente, il [restituire](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md) elemento del [ExecuteResponse](../../analysis-services/xmla/xml-elements-objects-executeresponse.md) elemento restituito dal **Execute** metodo per il **Batch**  comando contiene uno [risultati](../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md) elemento, che a sua volta contiene un **radice** elemento per ogni comando eseguito correttamente contenuto nel **Batch** comando. Se un comando nel **Batch** comando non può essere avviato o non riesce, il **Execute** il metodo restituisce un errore SOAP per il **Batch** comando che contiene l'errore il comando non riuscito.  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>Restituzione di risultati di un batch non transazionale  
 Risultati di comandi eseguiti all'interno di un batch non transazionale vengono restituiti nell'ordine in cui i comandi sono contenuti all'interno di **Batch** comando e come vengono restituiti da ogni comando. Se nessun comando contenuto nel **Batch** comando può essere avviato correttamente, il **Execute** il metodo restituisce un errore SOAP che contiene un errore per il **Batch** comando. Se almeno un comando è stato avviato correttamente, il **restituire** elemento del **ExecuteResponse** elemento restituito dal **Execute** metodo per il **Batch**  comando contiene uno **risultati** elemento, che a sua volta contiene un **radice** elemento per ogni comando contenuto nel **Batch** comando . Se uno o più comandi in un batch non transazionale non può essere avviati o non riesce, il **radice** elemento per tale comando non riuscito contiene un [errore](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) elemento che descrive l'errore.  
  
> [!NOTE]  
>  Come è possibile avviare almeno un comando in un batch non transazionale, il batch non transazionale viene considerato hanno eseguito correttamente, anche se ogni comando contenuto nel batch non transazionale restituisce un errore nei risultati del **Batch**  comando.  
  
## <a name="using-serial-and-parallel-execution"></a>Esecuzione in serie e parallela  
 È possibile utilizzare il **Batch** comando da eseguire inclusi i comandi in serie o in parallelo. Quando i comandi vengono eseguiti in serie, il comando successivo incluso nel **Batch** comando non è possibile avviare fino a quando il comando attualmente in esecuzione nel **Batch** comando viene completato. Quando i comandi vengono eseguiti in parallelo, possono essere eseguiti simultaneamente da più comandi di **Batch** comando.  
  
 Per eseguire comandi in parallelo, aggiungere i comandi da eseguire in parallelo per il [parallela](../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md) proprietà del **Batch** comando. Attualmente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] può eseguire solo contigui e sequenziali [processo](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) comandi in parallelo. Qualsiasi altro comando XMLA, ad esempio [crea](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) o [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), incluso nel **parallela** proprietà viene eseguita in serie.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]tenta di eseguire tutti **processo** comandi inclusi nel **parallela** proprietà in parallelo, ma non garantisce che tutti inclusi **processo** comandi possono essere eseguiti in parallelo. L'istanza analizza ogni **processo** comando e, se l'istanza determina che il comando non può essere eseguito in parallelo, la **processo** comando viene eseguito in serie.  
  
> [!NOTE]  
>  Per eseguire i comandi in parallelo, la **transazione** attributo del **Batch** comando deve essere impostato su true perché [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta solo una transazione attiva per connessione e non transazionale batch eseguono ogni comando in una transazione separata. Se si include il **parallela** si verifica un errore di proprietà in un batch non transazionale.  
  
### <a name="limiting-parallel-execution"></a>Impostazioni di limiti all'esecuzione parallela  
 Un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza tenta di eseguire tante **processo** comandi in parallelo possibili, fino ai limiti del computer in cui viene eseguita l'istanza. È possibile limitare il numero di simultaneamente **processo** comandi impostando il **maxParallel** attributo del **parallela** proprietà su un valore che indica il numero massimo di **processo** i comandi che possono essere eseguiti in parallelo.  
  
 Ad esempio, un **parallela** proprietà contiene i comandi seguenti nella sequenza elencata:  
  
1.  **Creare**  
  
2.  **Process**  
  
3.  **Alter**  
  
4.  **Process**  
  
5.  **Process**  
  
6.  **Process**  
  
7.  **Elimina**  
  
8.  **Process**  
  
9. **Process**  
  
 Il **maxParalle**attributo l di questo **parallela** proprietà è impostata su 2. Di conseguenza l'istanza esegue gli elenchi precedenti di comandi nel modo descritto nell'elenco seguente:  
  
-   Comando 1 viene eseguito in serie poiché comando 1 è un **crea** comando e solo **processo** comandi possono essere eseguiti in parallelo.  
  
-   Comando 2 viene eseguito in serie dopo il completamento del comando 1.  
  
-   Comando 3 viene eseguito in serie dopo il completamento del comando 2.  
  
-   Comandi 4 e 5 vengono eseguiti in parallelo dopo il completamento del comando 3. Sebbene il comando 6 sia anche un **processo** comando comando 6 non è possibile eseguire in parallelo con comandi 4 e 5 poiché la **maxParallel** è impostata su 2.  
  
-   Il comando 6 viene eseguito in serie dopo il completamento dei comandi 4 e 5.  
  
-   Il comando 7 viene eseguito in serie dopo il completamento del comando 6.  
  
-   I comandi 8 e 9 vengono eseguiti in parallelo dopo il completamento del comando 7.  
  
## <a name="using-the-batch-command-to-process-objects"></a>Utilizzo del comando Batch per l'elaborazione di oggetti  
 Il **Batch** comando contiene diverse proprietà facoltative e gli attributi inclusi in modo specifico per supportare l'elaborazione di più [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetti:  
  
-   Il **ProcessAffectedObjects** attributo del **Batch** comando indica se l'istanza deve elaborare anche qualsiasi oggetto che richiede la rielaborazione in seguito a un **processo** incluso nel comando di **Batch** comando elabora un oggetto specificato.  
  
-   Il [associazioni](../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md) proprietà contiene una raccolta di associazioni out-of-line utilizzate da tutti i **processo** comandi nel **Batch** comando.  
  
-   Il [DataSource](../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md) proprietà contiene un'associazione out-of-line per un'origine dati utilizzata da tutti i **processo** comandi nel **Batch** comando.  
  
-   Il [DataSourceView](../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md) proprietà contiene un'associazione out-of-line per una vista origine dati utilizzata da tutti i **processo** comandi nel **Batch** comando.  
  
-   Il [ErrorConfiguration](../../analysis-services/xmla/xml-elements-properties/errorconfiguration-element-xmla.md) proprietà specifica il modo in cui il **Batch** comando gestisce gli errori rilevati da tutti i **processo** comandi contenuti nel **Batch** comando.  
  
    > [!IMPORTANT]  
    >  Oggetto **processo** comando non può includere il **associazioni**, **DataSource**, **DataSourceView**, o **ErrorConfiguration**  proprietà, se il **processo** comando è contenuto in un **Batch** comando. Se è necessario specificare queste proprietà per un **processo** comando, specificare le informazioni necessarie nelle proprietà corrispondenti del **Batch** comando che contiene il **processo** comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento batch &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Elemento Process &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)   
 [Elaborazione di un modello multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
