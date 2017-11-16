---
title: Generazione guidata schema (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
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
- relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 789106378805f50a4a27dbb02ace2e8e0943daed
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="schema-generation-wizard-analysis-services"></a>Generazione guidata schema (Analysis Services)
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] supporta due metodi di utilizzo degli schemi relazionali quando si definiscono oggetti OLAP in un progetto o un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Gli oggetti OLAP vengono in genere definiti in base a un modello di dati logico costruito in una vista origine dati all'interno di un progetto o un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Tale vista origine dati viene definita in base a elementi dello schema di una o più origini dati relazionali, come personalizzate nella vista origine dati.  
  
 In alternativa, è possibile definire prima gli oggetti OLAP e successivamente generare una vista origine dati, un'origine dati e lo schema del database relazionale sottostante che supporta questi oggetti OLAP. Tale database relazionale viene denominato "database dell'area di interesse".  
  
 Questo approccio, talvolta chiamato progettazione dall'alto verso il basso, viene in genere utilizzato per prototipi e modelli di analisi. Con tale approccio, viene utilizzata la Generazione guidata schema per creare la vista origine dati sottostante e gli oggetti origine dati in base agli oggetti OLAP definiti in un progetto o un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Si tratta di un approccio iterativo. È molto probabile che la procedura guidata venga rieseguita più volte quando si modifica la progettazione delle dimensioni e dei cubi. Ogni volta che si esegue la procedura guidata, in essa vengono incorporate le modifiche negli oggetti sottostanti mantenendo, per quanto possibile, i dati contenuti nei database sottostanti.  
  
 Lo schema generato è uno schema del motore del database relazionale di SQL Server. La procedura guidata non consente di generare schemi per altri prodotti del database relazionale.  
  
 I dati popolati nel database dell'area di interesse vengono aggiunti separatamente, tramite qualsiasi strumento e tecnica utilizzata per popolare un database relazionale di SQL Server. Nella maggior parte dei casi, i dati vengono mantenuti quando si riesegue la procedura guidata, ma con delle eccezioni. Se si elimina una dimensione o un attributo contenente dati, ad esempio, alcuni dati devono essere eliminati. Se la Generazione guidata schema deve eliminare alcuni dati a causa di una modifica dello schema, prima dell'eliminazione dei dati viene visualizzato un avviso ed è possibile annullare la rigenerazione.  
  
 Come regola generale, qualsiasi modifica apportata a un oggetto originariamente generato mediante la Generazione guidata schema viene sovrascritta quando tale oggetto viene rigenerato mediante la Generazione guidata schema. La principale eccezione a questa regola è rappresentata dall'aggiunta di colonne a una tabella generata dalla Generazione guidata schema. In questo caso, la Generazione guidata schema consente di mantenere sia le colonne aggiunte alla tabella sia i dati in esse contenuti.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Nella tabella seguente sono elencati argomenti aggiuntivi in cui viene illustrato l'utilizzo della Generazione guidata schema.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Usare la Generazione guidata schema &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/use-the-schema-generation-wizard-analysis-services.md)|Viene descritto come generare lo schema per i database dell'area di interesse e dell'area di gestione temporanea.|  
|[Informazioni sugli schemi di database](../../analysis-services/multidimensional-models/understanding-the-database-schemas.md)|Descrive lo schema generato per i database dell'area di interesse e dell'area di gestione temporanea.|  
|[Informazioni sulla generazione incrementale](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)|Descrive le funzionalità di generazione incrementale della Generazione guidata schema.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Origini dati nei modelli multidimensionali](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Origini dati supportate &#40;SSAS - multidimensionale&#41;](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  

