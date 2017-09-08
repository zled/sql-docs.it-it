---
title: "Abilitare la modalità DirectQuery in SSDT | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f3a5cfe3f2b39f35d2b2e70dd44ec11adeebcd0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="enable-directquery-mode-in-ssdt"></a>Abilitare la modalità DirectQuery in SSDT

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

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


### <a name="whats-next"></a>Operazioni successive 
È ora possibile importare dati usando l'Importazione guidata tabella per ottenere i metadati per il modello. Non si otterranno righe di dati, ma tabelle, colonne e relazioni da usare come base per il modello. 

È possibile creare una partizione di esempio per ogni tabella e aggiungere dati di esempio in modo da poter verificare il comportamento del modello mentre viene creato. Eventuali dati di esempio aggiunti verranno usati **Analizza in Excel** o in altri strumenti client che possono connettersi al database dell'area di lavoro. Per informazioni più dettagliate, vedere [Aggiungere dati di esempio a un modello DirectQuery in modalità progettazione](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) .  
  
> [!TIP]  
    >  Anche in modalità DirectQuery in un modello vuoto è sempre possibile visualizzare un piccolo set di righe predefinito per ogni tabella. In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic su **Tabella** > **Proprietà tabella** per visualizzare il set di dati di 50 righe.  
  
  
## <a name="see-also"></a>Vedere anche  
[Abilitare la modalità DirectQuery in SSMS](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[Aggiungere dati di esempio a un modello DirectQuery in modalità progettazione](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  
