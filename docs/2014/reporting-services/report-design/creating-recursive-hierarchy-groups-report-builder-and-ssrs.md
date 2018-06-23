---
title: Creazione di gruppi di gerarchie ricorsive (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 52410faf7827c6692575aff641070565d0ef6243
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169163"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Creazione di gruppi di gerarchie ricorsive (Generatore report e SSRS)
  Per visualizzare dati ricorsivi dove la relazione tra padre e figlio viene rappresentata dai campi nel set di dati, è possibile impostare l'espressione di raggruppamento di area dati in base al campo figlio e impostare la proprietà padre in base al campo padre.  
  
 La visualizzazione di dati gerarchici è in genere utilizzata per gruppi di gerarchie ricorsive, ad esempio i dipendenti in un organigramma. Il set di dati include un elenco di dipendenti e responsabili, in cui i nomi dei responsabili sono visualizzati anche nell'elenco dei dipendenti.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Creazione di gerarchie ricorsive  
 Per compilare una gerarchia ricorsiva in un'area dati Tablix è necessario impostare l'espressione di raggruppamento sul campo che specifica i dati figlio e la proprietà Parent del gruppo sul campo che specifica i dati padre. Ad esempio, per un set di dati che include campi ID dipendente e ID responsabile in cui i dipendenti sono subordinati ai responsabili, impostare l'espressione di raggruppamento su ID dipendente e la proprietà Parent su ID responsabile.  
  
 Un gruppo definito come gerarchia ricorsiva, ovvero un gruppo che usa la proprietà Parent, può includere una sola espressione di raggruppamento. È possibile utilizzare la funzione `Level` nella spaziatura interna della casella di testo per applicare un rientro ai nomi dei dipendenti in base al relativo livello nella gerarchia.  
  
 Per altre informazioni, vedere [Aggiungere o eliminare un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) e [Creare un gruppo di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Funzioni di aggregazione che supportano la ricorsione  
 È possibile usare funzioni di aggregazione di Reporting Services che accettano il parametro *Recursive* per calcolare dati riepilogativi per una gerarchia ricorsiva. The following functions accept `Recursive` as a parameter: [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), and [VarP](report-builder-functions-varp-function.md). Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Area dati Tablix &#40;Generatore report e SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Riferimento a funzioni di aggregazione &#40;SSRS e Generatore Report&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Tabelle &#40;Generatore report e SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrici &#40;Generatore report e SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Elenchi &#40;Generatore report e SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  