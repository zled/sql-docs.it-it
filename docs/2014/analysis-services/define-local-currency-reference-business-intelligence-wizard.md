---
title: Definizione associazioni valute locali (configurazione guidata Business Intelligence) | Documenti Microsoft
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
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 10810e19ec00aa77a14cb5a21789dfee1f9ae09a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055117"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a>Definizione associazioni valute locali (Configurazione guidata funzionalità di Business Intelligence)
  Usare la pagina **Definizione associazioni valute locali** per definire le valute locali per la funzionalità di conversione valuta che riguarda il tipo di conversione molti-a-molti o molti-a-uno specificato nella pagina **Selezione tipo di conversione** . Una valuta locale è la valuta in cui vengono archiviate le transazioni per le misure selezionate nella pagina **Selezione misure** .  
  
> [!NOTE]  
>  Questa pagina non viene visualizzata se la Configurazione guidata funzionalità di Business Intelligence viene avviata da Progettazione dimensioni o facendo clic con il pulsante destro del mouse su una dimensione in Esplora soluzioni in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Questa pagina non viene inoltre visualizzata se è stata selezionata l'opzione **One-to-Many** (Uno-a-molti) nella pagina **Selezione tipo di conversione** .  
  
## <a name="options"></a>Opzioni  
 **Identificatori nella tabella dei fatti**  
 Selezionare questa opzione per specificare un attributo che fornisce gli identificatori di valuta per le valute locali in una dimensione di tipo Valuta a cui fa riferimento la tabella dei fatti contenente le misure selezionate nella pagina **Selezione misure** . (Dimensione di una valuta in uno cui `Type` è impostata su *valuta*.)  
  
 Utilizzare questa opzione quando è la transazione stessa a determinare la valuta corrente per la transazione. Ad esempio, nel database di esempio [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] di[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]nel gruppo di misure Internet Sales è inclusa una relazione tra dimensioni di tipo Regolare con la dimensione di tipo Valuta. La tabella dei fatti per tale gruppo di misure include una colonna chiave esterna che fa riferimento agli identificatori di valuta della tabella della dimensione.  
  
 **Dimensione di tipo valuta e attributo a cui fanno riferimento i dati delle tabelle dei fatti**  
 Consente di selezionare l'attributo di valuta nella dimensione di tipo Valuta i cui membri rappresentano gli identificatori di valuta per le valute locali. (Un attributo di valuta è un attributo il cui `Type` è impostata su *valuta*.)  
  
> [!NOTE]  
>  Questa opzione non è disponibile se non è stata selezionata l'opzione **Identificatori nella tabella dei fatti** .  
  
 **Attributi nella tabella delle dimensioni**  
 Consente di specificare un attributo da una dimensione correlata al gruppo di misure che contiene gli identificatori di valuta per le valute locali.  
  
 Utilizzare questa opzione quando è la relazione tra una transazione e un'altra entità commerciale, ad esempio un percorso, a determinare la valuta locale per la transazione. Ad esempio, nel database di esempio [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] di[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], nel gruppo di misure Financial Reporting è disponibile una relazione con dimensioni di tipo Riferimento alla dimensione di tipo Valuta tramite la dimensione Organization. Cioè, la tabella dei fatti per il gruppo di misure Financial Reporting contiene una colonna chiave esterna che fa riferimento a membri nella tabella della dimensione per la dimensione Organization. Questa tabella della dimensione include a sua volta una colonna chiave esterna che fa riferimento agli identificatori di valuta nella tabella della dimensione per la dimensione di tipo Valuta.  
  
 **Attributo della dimensione che fa riferimento alla valuta**  
 Consente di selezionare l'attributo all'interno di una dimensione i cui membri fanno riferimento agli identificatori di valuta per la valuta locale.  
  
> [!NOTE]  
>  Questa opzione non è disponibile se non è stata selezionata l'opzione **Attributi nella tabella delle dimensioni** .  
  
## <a name="see-also"></a>Vedere anche  
 [Business Intelligence guidata F1 Help](business-intelligence-wizard-f1-help.md)   
 [Finestra di progettazione del cubo &#40;Analysis Services - dati multidimensionali&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Finestra di progettazione della dimensione &#40;Analysis Services - dati multidimensionali&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  