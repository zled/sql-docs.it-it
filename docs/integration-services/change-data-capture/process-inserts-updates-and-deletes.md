---
title: "Elaborazione di inserimenti, aggiornamenti ed eliminazioni | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "caricamento incrementale [Integration Services], elaborazione dati"
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Elaborazione di inserimenti, aggiornamenti ed eliminazioni
  Nel flusso di dati di un pacchetto Integration Services che esegue un caricamento incrementale dei dati delle modifiche la seconda attività consiste nel separare inserimenti, aggiornamenti ed eliminazioni. Sarà quindi possibile utilizzare i comandi appropriati per applicarli alla destinazione.  
  
> [!NOTE]  
>  La prima attività nella progettazione del flusso di dati di un pacchetto che esegue un caricamento incrementale dei dati delle modifiche consiste nel configurare il componente di origine che esegue la query per il recupero dei dati delle modifiche. Per altre informazioni su questo componente, vedere [Recupero e comprensione dei dati delle modifiche](../../integration-services/change-data-capture/retrieve-and-understand-the-change-data.md). Per una descrizione del processo complessivo di creazione di un pacchetto in cui viene eseguito un caricamento incrementale dei dati delle modifiche, vedere [Change Data Capture &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## Associazione di valori descrittivi per separare inserimenti, aggiornamenti ed eliminazioni  
 Nella query di esempio che recupera i dati delle modifiche la funzione **cdc.fn_cdc_get_net_changes_<capture_instance>**restituisce solo la colonna di metadati denominata **__$operation**. Questa colonna di metadati contiene un valore ordinale che indica l'operazione che ha provocato la modifica.  
  
> [!NOTE]  
>  Per altre informazioni sulla query che usa chiamate alla funzione **cdc.fn_cdc_get_net_changes_<capture_instance>**, vedere [Creazione della funzione per il recupero dei dati delle modifiche](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md).  
  
 La creazione di una corrispondenza tra un valore ordinale e la relativa operazione non è altrettanto semplice quanto l'utilizzo di un tasto di scelta per l'operazione. "D" e "I", ad esempio, possono rappresentare in modo semplice rispettivamente un'operazione di eliminazione e un'operazione di inserimento. La query di esempio creata nell'argomento [Creazione della funzione per il recupero dei dati delle modifiche](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md) esegue questa conversione da un valore ordinale a un valore stringa descrittivo restituito in una nuova colonna. Nel segmento di codice seguente viene illustrata tale conversione:  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## Configurazione di una trasformazione Suddivisione condizionale per indirizzare inserimenti, aggiornamenti ed eliminazioni  
 Per indirizzare righe di dati delle modifiche a uno tra tre output diversi, la trasformazione Suddivisione condizionale rappresenta la soluzione ideale. La trasformazione controlla semplicemente il valore della colonna **CDC_OPERATION** in ogni riga e determina se la modifica è un inserimento, un aggiornamento o un'eliminazione.  
  
> [!NOTE]  
>  La colonna CDC_OPERATION contiene un valore stringa descrittivo derivato dal valore numerico presente nella colonna **__$operation**.  
  
#### Per suddividere inserimenti, aggiornamenti ed eliminazioni per l'elaborazione tramite una trasformazione Suddivisione condizionale  
  
1.  Nella scheda **Flusso di dati** aggiungere una trasformazione Suddivisione condizionale.  
  
2.  Connettere l'output dell'origine OLE DB alla trasformazione Suddivisione condizionale.  
  
3.  In **Editor trasformazione Suddivisione condizionale** immettere le tre righe seguenti nel riquadro inferiore per designare i tre output:  
  
    1.  Immettere una riga con la condizione `CDC_OPERATION == "I"` per indirizzare le righe inserite all'output per gli inserimenti.  
  
    2.  Immettere una riga con la condizione `CDC_OPERATION == "U"` per indirizzare le righe aggiornate all'output per gli aggiornamenti.  
  
    3.  Immettere una riga con la condizione `CDC_OPERATION == "D"` per indirizzare le righe eliminate all'output per le eliminazioni.  
  
## Passaggio successivo  
 Dopo avere suddiviso le righe per l'elaborazione, il passaggio successivo consiste nell'applicare le modifiche alla destinazione.  
  
 **Argomento successivo:** [Applicazione delle modifiche alla destinazione](../../integration-services/change-data-capture/apply-the-changes-to-the-destination.md)  
  
## Vedere anche  
 [Trasformazione Suddivisione condizionale](../../integration-services/data-flow/transformations/conditional-split-transformation.md)   
 [Divisione di un set di dati tramite la trasformazione Suddivisione condizionale](../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  