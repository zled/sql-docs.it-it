---
title: Origini dati da oggetti esistenti (guidata origine dati) (Analysis Services) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.datasourcewizard.specifyobject.f1
ms.assetid: e6ef6dea-9db8-45c4-8959-f9febd7caf7b
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 60f07885aff1d323cb2627e933330af3f35b8d45
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064822"
---
# <a name="data-sources-from-existing-objects-data-source-wizard-analysis-services"></a>Origini dati da oggetti esistenti (Creazione guidata origine dati) (Analysis Services)
  La pagina **Origini dati da oggetti esistenti** consente di specificare un'origine dei dati o un progetto esistente su cui basare la nuova origine dei dati.  
  
## <a name="options"></a>Opzioni  
 **Creare un'origine dati basata su un'origine dati esistente nella soluzione**  
 Selezionare questa opzione per basare la nuova origine dei dati su un'origine dei dati esistente nella soluzione. Quando un progetto che utilizza la nuova origine dei dati viene compilato, aggiornato o distribuito, la nuova origine dei dati acquisisce le impostazioni dall'origine dei dati specificata quando si seleziona questa opzione.  
  
 **Origine dati**  
 Consente di selezionare un'origine dei dati su cui basare la nuova origine dei dati dall'elenco delle origini dei dati, raggruppate per progetto.  
  
 **Creare un'origine dati basata su un progetto di Analysis Services**  
 Selezionare questa opzione per creare una nuova origine dati che fa riferimento a un altro progetto di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nella soluzione corrente. La nuova origine dei dati acquisisce le impostazioni dalle proprietà `TargetServer` e `TargetDatabase` del progetto selezionato. Quando un progetto che utilizza la nuova origine dei dati viene compilato, aggiornato o distribuito, la nuova origine dei dati acquisisce le impostazioni dall'origine dei dati specificata quando si seleziona questa opzione.  
  
 **Progetto**  
 Consente di selezionare il progetto a cui fare riferimento nella nuova origine dei dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida F1 guidata origine dati &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md)   
 [Origini dati nei modelli multidimensionali](multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Origini dati supportate &#40;multidimensionale di SSAS&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  