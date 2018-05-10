---
title: Distribuire soluzioni di modelli utilizzando XMLA | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 70dbd820e0ef1936d60dc1dca3508897c4b6764a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deploy-model-solutions-using-xmla"></a>Distribuire soluzioni di modelli utilizzando XMLA
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] l'opzione **Genera codice per istruzione CREATE in** del comando **Crea script per database** consente di creare uno script XML per un intero database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o uno dei relativi oggetti che lo costituiscono. Lo script risultante può quindi essere eseguito in un altro computer per ricreare lo schema (metadati) del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Lo script genera l'intero database e non è disponibile alcun meccanismo per eseguire l'aggiornamento incrementale di oggetti già distribuiti durante l'utilizzo dello script. In seguito all'esecuzione dello script e alla distribuzione del database, il nuovo database creato deve essere elaborato prima che gli utenti possano visualizzarlo.  
  
 Per altre informazioni sul comando **Crea script per database** , vedere [Documentazione e script per un database di Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md).  
  
## <a name="modifying-object-properties-in-the-xml-script"></a>Modifica delle proprietà degli oggetti nello script XML  
 Quando si usa il comando **Crea script per database** , non è possibile modificare proprietà specifiche, ad esempio il nome del database, le stringhe di connessione dell'origine dei dati e le impostazioni di sicurezza, degli oggetti del database. Tali proprietà devono essere modificate manualmente nello script in seguito alla generazione dello script oppure nel database distribuito in seguito all'esecuzione dello script.  
  
> [!IMPORTANT]  
>  La password eventualmente specificata nella stringa di connessione per un'origine dati o ai fini della rappresentazione non è contenuta nello script XML. Poiché in tale scenario la password è necessaria per l'elaborazione, è necessario aggiungerla manualmente allo script XML prima che questo venga eseguito oppure aggiungerla dopo l'esecuzione dello script XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire soluzioni di modelli tramite la distribuzione guidata](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)   
 [Sincronizzare i database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
  
