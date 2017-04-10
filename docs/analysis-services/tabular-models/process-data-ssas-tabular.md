---
title: "Elaborare dati (SSAS tabulare) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Elaborare dati (SSAS tabulare)
  Quando si importano dati in un modello tabulare, nella modalità cache si acquisisce uno snapshot di tali dati al momento dell'importazione. In alcuni casi, tali dati potrebbero non cambiare mai, pertanto non devono essere aggiornati nel modello. Tuttavia, è più probabile che i dati che si importano cambino regolarmente, pertanto affinché il modello rifletta i dati più recenti delle origini dati, è necessario elaborarli (aggiornarli) e calcolare nuovamente i dati calcolati. Per aggiornare i dati nel modello, è necessario eseguire un'azione di elaborazione in tutte le tabelle, in una singola tabella, in base a una partizione o a una connessione all'origine dati.  
  
 Durante la creazione del progetto di modello, tutte le azioni di elaborazione devono essere avviate manualmente in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Dopo la distribuzione di un modello, le operazioni di elaborazione possono essere eseguite tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oppure pianificate utilizzando uno script. Tutte le attività descritte di seguito riguardano le azioni di elaborazione che è possibile eseguire durante la creazione di modelli in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni sulle azioni di elaborazione per un modello distribuito, vedere [Elaborare database, tabelle o partizioni &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## Attività correlate  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Elaborare manualmente i dati &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/manually-process-data-ssas-tabular.md)|Viene descritto come elaborare manualmente i dati dell'area di lavoro modello.|  
|[Risolvere i problemi relativi all'elaborazione dei dati &#40;SSAS tabulare&#41;](../../analysis-services/troubleshoot-process-data-ssas-tabular.md)|Viene descritto come risolvere i problemi relativi alle operazioni di elaborazione.|  
  
  