---
title: Distribuire soluzioni di modelli tramite la distribuzione guidata | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services Deployment Wizard
- deploying [Analysis Services], Analysis Services Deployment Wizard
- Analysis Services deployments, Analysis Services Deployment Wizard
- Analysis Services Deployment Wizard, about Analysis Services Deployment Wizard
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 904ca80fe95b73813d9932496563ffdfb400a66a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Deploy Model Solutions Using the Deployment Wizard
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata utilizza i file di output JSON generati da un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto come file di input. Questi file di input possono essere facilmente modificati per personalizzare la distribuzione di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Lo script di distribuzione generato può quindi essere eseguito subito oppure salvato per essere distribuito in una fase successiva.  
  
 È possibile effettuare la distribuzione utilizzando la procedura guidata come indicato in questa sezione. È anche possibile automatizzare la distribuzione o utilizzare la funzionalità di sincronizzazione. Se il database distribuito è di grandi dimensioni, è consigliabile utilizzare partizioni sui sistemi di destinazione. È inoltre possibile automatizzare il popolamento e la creazione delle partizioni utilizzando la libreria AMO (Analysis Management Objects).  
  
> [!IMPORTANT]  
>  I file di output né lo script di distribuzione conterrà l'id utente o la password se tali opzioni vengono specificate nella stringa di connessione per un'origine dati o per gli scopi della rappresentazione. Poiché in questo scenario sono necessarie per l'elaborazione, è necessario aggiungere tali informazioni manualmente. Se la distribuzione non include l'elaborazione, è possibile aggiungere le informazioni di connessione e le impostazioni di rappresentazione in base alle esigenze dopo la distribuzione. Se la distribuzione include l'elaborazione, si possono aggiungere tali informazioni e impostazioni nella procedura guidata oppure nello script di distribuzione dopo il relativo salvataggio.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Gli argomenti seguenti descrivono come utilizzare Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , i file di input e lo script di distribuzione:  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|Descrive i vari modi in cui si può eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Informazioni sui file di input utilizzati per creare uno script di distribuzione](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|Descrive quali file vengono utilizzati da Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] come valori di input e il contenuto di ciascuno di questi file. Contiene inoltre collegamenti a vari argomenti che descrivono come modificare i valori contenuti in ciascun file di input.|  
|[Informazioni sullo script di distribuzione di Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|Descrive il contenuto dello script di distribuzione e come viene eseguito lo script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire soluzioni di modelli utilizzando XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Sincronizzare database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [Informazioni sui file di Input utilizzati per creare lo Script di distribuzione](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [Distribuire soluzioni di modelli con l'utilità di distribuzione](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
