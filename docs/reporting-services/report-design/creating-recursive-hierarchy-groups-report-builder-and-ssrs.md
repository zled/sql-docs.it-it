---
title: "Creazione di gruppi di gerarchie ricorsive (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Creazione di gruppi di gerarchie ricorsive (Generatore report e SSRS)
Per visualizzare dati ricorsivi in report impaginati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], dove la relazione tra padre e figlio è rappresentata mediante i campi del set di dati, impostare l'espressione di raggruppamento nell'area dati in base al campo figlio e la proprietà Parent in base al campo padre.  
  
 La visualizzazione di dati gerarchici è in genere utilizzata per gruppi di gerarchie ricorsive, ad esempio i dipendenti in un organigramma. Il set di dati include un elenco di dipendenti e responsabili, in cui i nomi dei responsabili sono visualizzati anche nell'elenco dei dipendenti.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Creazione di gerarchie ricorsive  
 Per compilare una gerarchia ricorsiva in un'area dati Tablix è necessario impostare l'espressione di raggruppamento sul campo che specifica i dati figlio e la proprietà Parent del gruppo sul campo che specifica i dati padre. Ad esempio, per un set di dati che include campi ID dipendente e ID responsabile in cui i dipendenti sono subordinati ai responsabili, impostare l'espressione di raggruppamento su ID dipendente e la proprietà Parent su ID responsabile.  
  
 Un gruppo definito come gerarchia ricorsiva, ovvero un gruppo che usa la proprietà Parent, può includere una sola espressione di raggruppamento. È possibile usare la funzione **Level** nella spaziatura interna della casella di testo per applicare un rientro ai nomi dei dipendenti in base al relativo livello nella gerarchia.  
  
 Per altre informazioni, vedere [Aggiunta o eliminazione di un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) e [Creare un gruppo di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### Funzioni di aggregazione che supportano la ricorsione  
 È possibile usare funzioni di aggregazione di Reporting Services che accettano il parametro *Recursive* per calcolare dati riepilogativi per una gerarchia ricorsiva. Le funzioni seguenti accettano **Recursive** come parametro: [Sum](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md), [Avg](../../reporting-services/report-design/avg-function-report-builder-and-ssrs.md), [Count](../../reporting-services/report-design/count-function-report-builder-and-ssrs.md), [CountDistinct](../../reporting-services/report-design/countdistinct-function-report-builder-and-ssrs.md), [CountRows](../../reporting-services/report-design/countrows-function-report-builder-and-ssrs.md), [Max](../../reporting-services/report-design/max-function-report-builder-and-ssrs.md), [Min](../../reporting-services/report-design/min-function-report-builder-and-ssrs.md), [StDev](../../reporting-services/report-design/stdev-function-report-builder-and-ssrs.md), [StDevP](../../reporting-services/report-design/stdevp-function-report-builder-and-ssrs.md), [Sum](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md), [Var](../../reporting-services/report-design/var-function-report-builder-and-ssrs.md) e [VarP](../../reporting-services/report-design/varp-function-report-builder-and-ssrs.md). Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md).  
  
## Vedere anche  
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Area dati Tablix &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)   
 [Tabelle &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)    
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  