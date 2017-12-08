---
title: Partizioni (SSAS tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 708b9bdf-8c0b-4476-809a-8f616be23a58
caps.latest.revision: "20"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: ceaff43e4f0f5d2b1901c98b026d37af9ba89383
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="partitions"></a>Partizioni
  Le partizioni consentono di dividere una tabella in parti logiche. Ogni partizione può quindi essere elaborata (aggiornata) indipendentemente dalle altre. Le nuove partizioni create utilizzando la finestra di dialogo partizioni in SSDT durante la creazione di modelli si applicano al database dell'area di lavoro modello. Quando il modello viene distribuito, le partizioni definite per il database dell'area di lavoro modello vengono duplicate nel database modello distribuito. È inoltre possibile creare e gestire partizioni per un database modello distribuito tramite la finestra di dialogo partizioni in SQL Server Management Studio.  In questo argomento vengono descritte le nuove partizioni create durante la creazione di modelli tramite la finestra di dialogo Gestione partizioni in SSDT. Per informazioni sulla creazione e la gestione delle partizioni per un modello distribuito, vedere [creare e gestire partizioni di modelli tabulari](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_benefits"></a> Vantaggi  
 Le partizioni, nei modelli tabulari, consentono di dividere una tabella in oggetti partizione logici. Ogni partizione può quindi essere elaborata indipendentemente dalle altre. Ad esempio, è possibile che in una tabella siano inclusi determinati set di righe contenenti dati che raramente vengono modificati, a differenza di altri set i cui dati vengono invece modificati spesso. In questi casi, non è necessario elaborare tutti i dati quando in realtà si desidera effettuare tale operazione solo per una parte. Le partizioni consentono di dividere parti di dati che devono essere elaborati di frequente dai dati che possono invece essere elaborati meno frequentemente.  
  
 Un modello di progetto efficace consente di utilizzare le partizioni per eliminare elaborazioni e successivi carichi del processore non necessari nei server Analysis Services assicurando, nel contempo, che i dati vengano elaborati e aggiornati con una frequenza tale da riflettere i dati più recenti dalle origini dati. La modalità con cui le partizioni vengono implementate e utilizzate durante la creazione di modelli può essere molto diversa se riguarda modelli distribuiti. Tenere presente che, durante la fase di creazione dei modelli, è possibile che si utilizzi solo un subset dei dati che alla fine si troveranno nel modello distribuito.  
  
### <a name="processing-partitions"></a>Elaborazione di partizioni  
 Modelli distribuiti, l'elaborazione viene eseguita utilizzando SQL Server Management Studio oppure eseguendo uno script che include il comando di processo e specifica le impostazioni e opzioni di elaborazione. Quando si creano modelli utilizzando SSDT, è possibile eseguire operazioni di elaborazione tramite un comando elabora nel menu modello o sulla barra degli strumenti. Un'operazione di elaborazione può essere specificata per una partizione, una tabella o per qualsiasi altro elemento.  
  
 Quando viene eseguita un'operazione di elaborazione, viene effettuata una connessione all'origine dati utilizzando la connessione dati. I nuovi dati importati in tabelle, relazioni e gerarchie del modello vengono ricompilati per ogni tabella, mentre i calcoli nelle colonne calcolate e nelle misure calcolate vengono calcolati nuovamente.  
  
 Dividendo ulteriormente una tabella in partizioni logiche, è possibile determinare in modo selettivo quali dati in ogni partizione vengono elaborati, nonché quando e come eseguire tale operazione Quando si distribuisce un modello, l'elaborazione delle partizioni può essere completata manualmente tramite la finestra di dialogo partizioni in SQL Server Management Studio o tramite uno script che esegue un comando di elaborazione.  
  
### <a name="partitions-in-the-model-workspace-database"></a>Partizioni nel database dell'area di lavoro modello  
 È possibile creare nuove partizioni, modificare, unire o eliminare partizioni tramite Gestione partizioni in SSDT. A seconda del livello di compatibilità del modello di creazione, gestione partizioni sono disponibili due modalità per la selezione di tabelle, righe e colonne per una partizione: per i modelli tabulari 1400, le partizioni sono definite tramite una query M oppure è possibile utilizzare la modalità di progettazione per aprire Editor di query. Per tabulari 1100, 1103, i modelli 1200, usare la modalità anteprima tabella e la modalità query SQL. 
  
### <a name="partitions-in-a-deployed-model-database"></a>Partizioni in un database modello distribuito  
 Quando si distribuisce un modello, le partizioni per il database modello distribuito verranno visualizzate come oggetti di database in SQL Server Management Studio. È possibile creare, modificare, merge ed eliminare partizioni per un modello distribuito tramite la finestra di dialogo partizioni in SQL Server Management Studio. La gestione delle partizioni per un modello distribuito in SSMS non rientra nell'ambito di questo argomento. Per ulteriori informazioni sulla gestione delle partizioni in SQL Server Management Studio, vedere [creare e gestire partizioni di modelli tabulari](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Attività correlate  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Creare e gestire partizioni nel database dell'area di lavoro](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)|Viene descritto come creare e gestire partizioni nel database dell'area di lavoro modello tramite Gestione partizioni in SSDT.|  
|[Elaborare partizioni nel database dell'area di lavoro](../../analysis-services/tabular-models/process-partitions-in-the-workspace-databse-ssas-tabular.md)|Viene descritto come elaborare (aggiornare) le partizioni nel database dell'area di lavoro modello.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Elaborare dati](../../analysis-services/tabular-models/process-data-ssas-tabular.md)  
  
  
