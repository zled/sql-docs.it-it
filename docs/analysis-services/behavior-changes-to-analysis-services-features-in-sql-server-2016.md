---
title: "Modifiche del comportamento delle funzionalit&#224; di Analysis Services in SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# Modifiche del comportamento delle funzionalit&#224; di Analysis Services in SQL Server 2016
  Una *modifica del comportamento* influisce sulle modalità d'uso o di interazione delle funzionalità nella versione corrente rispetto alle versioni precedenti di SQL Server.  
  
 Modifiche dei valori predefiniti, configurazione manuale necessaria per completare un aggiornamento o un ripristino di funzionalità o una nuova implementazione di una funzionalità esistente sono tutti esempi di modifiche del comportamento nel prodotto.  
  
 Di seguito sono elencati i comportamenti delle funzionalità cambiati in questa versione, che comunque non interrompono un codice o un modello esistente dopo l'aggiornamento.  
  
> [!NOTE]  
>  Al contrario di una *modifica del comportamento*, una *modifica di rilievo* impedisce l'esecuzione di un modello di dati o di un'applicazione integrata con [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dopo l'aggiornamento di un server, di uno strumento client o di un modello. Per vedere l'elenco, visitare [Modifiche di rilievo nelle funzionalità di Analysis Services in SQL Server 2016](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
## Analysis Services in modalità SharePoint  
 L'esecuzione della configurazione guidata di PowerPivot non è più necessaria come attività di post-installazione. Questo vale per tutte le versioni supportate di SharePoint che caricano i dalla versione corrente di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## Modalità DirectQuery per modelli tabulari  
 *DirectQuery* è una modalità di accesso ai dati per modelli tabulari, in cui l'esecuzione di query avviene in un database relazionale di back-end, recuperando un set di risultati in tempo reale. Viene usata spesso per set di dati di grandi dimensioni per i quali la memoria non è sufficiente o quando i dati sono volatili e si vuole che i dati più recenti vengano restituiti in query in un modello tabulare.  
  
 DirectQuery è disponibile come modalità di accesso ai dati nelle ultime versioni rilasciate. In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]l'implementazione è stata leggermente modificata, presupponendo che il modello tabulare sia impostato a un livello di compatibilità pari a 1200. DirectQuery ha meno restrizioni rispetto a prima. Include inoltre diverse proprietà di database.  
  
 Se si usa DirectQuery in un modello tabulare esistente, è possibile mantenere il modello al livello di compatibilità attuale pari a 1100 o 1103 e continuare a usare DirectQuery come implementato per tali livelli. In alternativa, è possibile aggiornare il modello a 1200 per usufruire dei miglioramenti apportati a DirectQuery in questa versione di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Non esiste alcun aggiornamento sul posto di un modello DirectQuery, in quanto le impostazioni dei livelli di compatibilità precedenti non hanno controparti esatte nel recente livello di compatibilità a 1200. Se si dispone di un modello tabulare esistente eseguito in modalità DirectQuery, aprire il modello in SQL Server Data Tools, disattivare DirectQuery, impostare la proprietà **Livello di compatibilità** su 1200 e quindi riconfigurare le proprietà di DirectQuery come definite per i modelli tabulari a 1200. Per altri dettagli, vedere [Modalità DirectQuery &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md).  
  
## Vedere anche  
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)   
 [Modifiche di rilievo nelle funzionalità di Analysis Services in SQL Server 2016](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Download di SQL Server Data Tools](https://msdn.microsoft.com/en-us/library/mt204009.aspx)  
  
  