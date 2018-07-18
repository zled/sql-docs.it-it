---
title: Distribuire soluzioni di modelli tramite la distribuzione guidata | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cde312f2bfad67c6cfe61a9b8379973c1f59a56c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Deploy Model Solutions Using the Deployment Wizard
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata utilizza i file di output JSON generati da un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto come file di input. Questi file di input possono essere facilmente modificati per personalizzare la distribuzione di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Lo script di distribuzione generato può quindi essere eseguito subito oppure salvato per essere distribuito in una fase successiva.  

> [!NOTE]
> Il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] guidata/Utilità di distribuzione viene installato con [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) (SSMS). Verificare se che si sta utilizzando la versione più recente. Se in esecuzione dal prompt dei comandi, per impostazione predefinita, C:\Program Files (x86) \Microsoft SQL Server\140\Tools\Binn\ManagementStudio installata la versione più recente della procedura guidata distribuzione. 
  
 È possibile effettuare la distribuzione utilizzando la procedura guidata come indicato in questa sezione. È anche possibile automatizzare la distribuzione o utilizzare la funzionalità di sincronizzazione. Se il database distribuito è di grandi dimensioni, è consigliabile utilizzare partizioni sui sistemi di destinazione. È possibile automatizzare la creazione della partizione e popolamento utilizzando tabulare oggetto modello TOM (), Scriting linguaggio TMSL (Tabular Model) e gli oggetti AMO (Analysis Management).  
  
> [!IMPORTANT]  
>  I file di output né lo script di distribuzione conterrà l'id utente o la password se tali opzioni vengono specificate nella stringa di connessione per un'origine dati o per gli scopi della rappresentazione. Poiché in questo scenario sono necessarie per l'elaborazione, è necessario aggiungere tali informazioni manualmente. Se la distribuzione non include l'elaborazione, è possibile aggiungere le informazioni di connessione e le impostazioni di rappresentazione in base alle esigenze dopo la distribuzione. Se la distribuzione include l'elaborazione, si possono aggiungere tali informazioni e impostazioni nella procedura guidata oppure nello script di distribuzione dopo il relativo salvataggio.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Gli argomenti seguenti descrivono come utilizzare Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , i file di input e lo script di distribuzione:  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Esegue la distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|Descrive i vari modi in cui si può eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Informazioni sui file di Input utilizzati per creare lo Script di distribuzione](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|Descrive quali file vengono utilizzati da Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] come valori di input e il contenuto di ciascuno di questi file. Contiene inoltre collegamenti a vari argomenti che descrivono come modificare i valori contenuti in ciascun file di input.|  
|[Comprendere lo Script di distribuzione di Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|Descrive il contenuto dello script di distribuzione e come viene eseguito lo script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire soluzioni di modelli utilizzando XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Sincronizzare i database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [Informazioni sui file di Input utilizzati per creare lo Script di distribuzione](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [Distribuire soluzioni di modelli con l'utilità di distribuzione](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
