---
title: Ruoli e autorizzazioni (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 77a8043d96f99543428121c3b98a58a7704ec0b2
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="roles-and-permissions-analysis-services"></a>Ruoli e autorizzazioni (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]fornisce un modello di autorizzazione basata sui ruoli che concede l'accesso a operazioni, oggetti e dati. È necessario che tutti gli utenti che accedono a un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] si attengano a questa procedura all'interno del contesto di un ruolo.  
  
 L'amministratore di sistema di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] può concedere l'appartenenza al **ruolo di amministratore del server** che fornisce l'accesso illimitato alle operazioni sul server. Le autorizzazioni di questo ruolo sono fisse e non possono essere personalizzate. Per impostazione predefinita, i membri del gruppo Administrators locale sono automaticamente amministratori di sistema di Analysis Services.  
  
 Agli utenti non amministratori che elaborano o eseguono query sui dati, l'accesso viene concesso tramite i **ruoli di database**. Gli amministratori di sistema e di database possono creare i ruoli che descrivono i diversi livelli di accesso all'interno di un database e quindi assegnare l'appartenenza a ogni utente che richiede l'accesso. Ogni ruolo dispone di un set di autorizzazioni personalizzato per l'accesso a oggetti e operazioni all'interno di un database specifico. È possibile assegnare le autorizzazioni a livello di database, di oggetti interni quali cubi e dimensioni (ma non prospettive) e di righe.  
  
 È pratica comune creare i ruoli e assegnare l'appartenenza con operazioni separate. Spesso, Progettazione modelli aggiunge i ruoli durante la fase di progettazione. In questo modo, tutte le definizioni di ruolo vengono riflesse nei file di progetto che definiscono il modello. L'appartenenza al ruolo viene in genere implementata in un secondo momento quando il database passa in produzione, generalmente dagli amministratori del database che creano script che possono essere sviluppati, testati ed eseguiti come un'operazione indipendente.  
  
 Ogni autorizzazione viene concessa su un'identità utente di Windows valida. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizza l'autenticazione di Windows esclusivamente per autenticare le identità utente. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]non fornisce alcun metodo di autenticazione proprietario. Vedere [le metodologie di autenticazione supportate da Analysis Services](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md).  
  
> [!IMPORTANT]  
>  Le autorizzazioni si sommano tra loro per ogni utente o gruppo di Windows in tutti i ruoli del database. Se un ruolo nega a un utente o a un gruppo le autorizzazioni per eseguire determinate attività o per visualizzare determinati dati, mentre un altro ruolo concede a tale utente o gruppo queste autorizzazioni, l'utente o il gruppo disporrà delle autorizzazioni per eseguire l'attività o visualizzare i dati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Per l'autorizzazione di accesso per gli oggetti e operazioni &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [Concedere autorizzazioni per database &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)  
  
-   [Concedere al cubo o modello autorizzazioni &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)  
  
-   [Concedere le autorizzazioni di elaborazione &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
-   [Concedere autorizzazioni di lettura definizione per i metadati degli oggetti &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [Concedere le autorizzazioni per un oggetto origine dati &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [Concedere le autorizzazioni per strutture di data mining e modelli &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [Concedere le autorizzazioni per una dimensione &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [Concedere l'accesso personalizzato alla dimensione dei dati &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [Concedere l'accesso personalizzato a una cella di dati &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare e gestire ruoli &#40; SSAS tabulare &#41;](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)  
  
  
