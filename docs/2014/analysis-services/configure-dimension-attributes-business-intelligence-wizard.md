---
title: Configurazione attributi dimensione (configurazione guidata Business Intelligence) | Documenti Microsoft
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
- sql12.asvs.biwizard.acctintelligence.selectattributes.f1
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e9ce0f7535f111d5c9152304a4e27315f73e5087
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077689"
---
# <a name="configure-dimension-attributes-business-intelligence-wizard"></a>Configurazione attributi dimensione (Configurazione guidata funzionalità di Business Intelligence)
  Utilizzare la pagina **Configurazione attributi dimensione** per eseguire il mapping tra gli attributi di dimensione e i tipi di attributo utilizzati da [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per identificare gli attributi per le dimensioni di tipo Conto.  
  
## <a name="options"></a>Opzioni  
 **Tipo di dimensione**  
 Consente di visualizzare il tipo di dimensione selezionato.  
  
> [!NOTE]  
>  Questa opzione non è disponibile perché il `Type` proprietà della dimensione non può essere impostata su un valore diverso da *Account* per le dimensioni dell'account.  
  
 **Attributi della dimensione**  
 Consente di visualizzare i tipi di attributo validi di cui è possibile eseguire il mapping agli attributi della dimensione esistenti.  
  
 **Includere**  
 Selezionare una casella di controllo per includere nella dimensione il tipo di attributo corrispondente.  
  
 **Tipo di attributo**  
 Consente di visualizzare i tipi di attributo di cui è possibile eseguire il mapping agli attributi della dimensione esistenti.  
  
 **Attributo della dimensione**  
 Consente di selezionare l'attributo della dimensione di cui è necessario eseguire il mapping al tipo di attributo corrispondente.  
  
 **Imposta misure semiadditive in base al tipo di account**  
 Selezionare questa opzione per modificare ogni misura associata alla dimensione corrente da aggregare in base al tipo di conto.  
  
> [!NOTE]  
>  Questa opzione non viene visualizzata se la Configurazione guidata funzionalità di Business Intelligence è stata avviata da Progettazione dimensioni oppure facendo clic con il pulsante destro del mouse su una dimensione in Esplora soluzioni in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Business Intelligence guidata F1 Help](business-intelligence-wizard-f1-help.md)   
 [Finestra di progettazione del cubo &#40;Analysis Services - dati multidimensionali&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Finestra di progettazione della dimensione &#40;Analysis Services - dati multidimensionali&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  