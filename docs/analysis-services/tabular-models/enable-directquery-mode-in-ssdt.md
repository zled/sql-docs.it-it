---
title: "Abilitare la modalità DirectQuery in SSDT | Documenti Microsoft"
ms.custom: 
ms.date: 02/22/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cc16e4c1e4c34e9e37d20a747e8ea2acac6bea01
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="enable-directquery-mode-in-ssdt"></a>Abilitare la modalità DirectQuery in SSDT
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In questo argomento verrà descritto come abilitare la modalità DirectQuery per un progetto di modello tabulare in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
Quando si attiva la modalità DirectQuery per un modello tabulare che si sta realizzando in SSDT:
-   le funzionalità che non sono compatibili con la modalità DirectQuery vengono disabilitate.  
-   il modello esistente viene convalidato. gli avvisi vengono visualizzati se le funzionalità non sono compatibili con la modalità DirectQuery.  
-   Se i dati sono stati importati prima di abilitare la modalità DirectQuery, la cache del modello di lavoro viene svuotata.  
  
### <a name="enable-directquery"></a>Abilitare DirectQuery  
  
In SSDT, nel riquadro **Proprietà** per il file **Model.bim** , impostare la proprietà **Modalità DirectQuery**su **On**.  

![Abilitare la modalità DirectQuery in SSDT](../../analysis-services/tabular-models/media/enable-directquery-mode-in-ssdt.png)
  
Se il modello presenta già una connessione a un'origine dati e a dati esistenti, verrà richiesto di immettere le credenziali di database usate per connettersi al database relazionale. I dati già esistenti all'interno del modello verranno rimossi dalla cache in memoria.  
  
Se il modello è parzialmente o completamente completo prima dell'attivazione della modalità DirectQuery, è possibile ottenere errori relativi a funzionalità non compatibili. In Visual Studio aprire l' **Elenco errori** e risolvere eventuali problemi che impedirebbero di impostare la modalità DirectQuery per il modello.  


### <a name="whats-next"></a>Quali sono le operazioni successive? 
È ora possibile importare dati usando l'Importazione guidata tabella per ottenere i metadati per il modello. Non si otterranno righe di dati, ma tabelle, colonne e relazioni da usare come base per il modello. 

È possibile creare una partizione di esempio per ogni tabella e aggiungere dati di esempio in modo da poter verificare il comportamento del modello mentre viene creato. Eventuali dati di esempio aggiunti verranno usati **Analizza in Excel** o in altri strumenti client che possono connettersi al database dell'area di lavoro. Per informazioni più dettagliate, vedere [Aggiungere dati di esempio a un modello DirectQuery in modalità progettazione](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) .  
  
> [!TIP]  
    >  Anche in modalità DirectQuery in un modello vuoto è sempre possibile visualizzare un piccolo set di righe predefinito per ogni tabella. In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic su **Tabella** > **Proprietà tabella** per visualizzare il set di dati di 50 righe.  
  
  
## <a name="see-also"></a>Vedere anche  
[Abilitare la modalità DirectQuery in SSMS](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[Aggiungere dati di esempio a un modello DirectQuery in modalità progettazione](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  
