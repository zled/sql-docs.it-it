---
title: 'Esempi di SQL Server: pacchetti di distribuzione di modelli (MDS) | Microsoft Docs'
ms.custom: 
ms.date: 07/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- Master Data Services
- campione
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
caps.latest.revision: "21"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7317bf544574e2314e4d830e672a3aa65650042
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-examples-model-deployment-packages-mds"></a>Esempi di SQL Server: pacchetti di distribuzione di modelli (MDS)
  Quando viene installato [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]vengono inclusi anche pacchetti di modelli di esempio. Il percorso predefinito dei pacchetti di modelli di esempio è unità\<>\Programmi\Microsoft SQL Server\130\Master Data Services\Samples\Packages.  
  
 Per istruzioni su come distribuire i pacchetti di modelli di esempio, vedere [Distribuzione di modelli di esempio e dati](../master-data-services/master-data-services-installation-and-configuration.md#deploySample). I pacchetti di modelli di esempio vengono distribuiti con lo [strumento MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]  
>  **Aggiornamenti di esempio in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**  
>   
>  I pacchetti di esempio sono stati aggiornati per supportare le nuove funzionalità seguenti.  
>   
>  -   Visualizzare le relazione molti-a-molti.  
>   
>      Per altre informazioni, vedere [Relazione M2M nel modello di esempio](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md#M2MSample).  

> -   Valori consentiti dai vincoli per attributi basati su dominio.  
>   
>      Per altre informazioni, vedere [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md).  
> -   Richiedere l'approvazione delle modifiche delle entità.  
>   
>      Per altre informazioni, vedere [Approvazione necessaria &#40;Master Data Services&#41;](../master-data-services/approval-required-master-data-services.md).  
> -   Usare gli operatori Not ed Else nelle regole di business  
>   
>      Per altre informazioni, vedere [Esempi di regole di business](../master-data-services/business-rule-examples-master-data-services.md).  
> -   Implementare l'indice personalizzato  
>   
>      Per altre informazioni, vedere [Indice personalizzato &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md).  
 

 
 In Master Data Services, un pacchetto è un file XML contenente una struttura di modello distribuibile e, facoltativamente, i dati del modello. Usare i pacchetti di modelli per spostare copie dei modelli da un ambiente MDS a un altro o per creare nuovi modelli nell'ambiente [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
