---
title: Concedere autorizzazioni di lettura definizione per i metadati degli oggetti (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 55c4e6d43ffedd933e968e8fc2355871c698d290
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>Concedere le autorizzazioni di lettura definizione per i metadati degli oggetti (Analysis Services)
  L'autorizzazione per la lettura di una definizione dell'oggetto o dei metadati negli oggetti selezionati consente a un amministratore di concedere l'autorizzazione per la visualizzazione delle informazioni sull'oggetto, senza tuttavia concedere l'autorizzazione per la modifica della definizione dell'oggetto, per la modifica della struttura dell'oggetto o per la visualizzazione dei dati effettivi dell'oggetto. Le autorizzazioni**Lettura definizione** possono essere concesse a livello di database, origine dati, dimensione, struttura di data mining e modello di data mining. Se sono necessarie le autorizzazioni **Lettura definizione** per un cubo, abilitare l'opzione **Lettura definizione** per il database. Tenere presente che le autorizzazioni si sommano tra loro. Si supponga, ad esempio, uno scenario in cui un ruolo concede l'autorizzazione per la lettura dei metadati per un cubo, mentre un secondo ruolo concede allo stesso utente l'autorizzazione per la lettura dei metadati per una dimensione. Le autorizzazioni concesse dai due diversi ruoli si sommano, assegnando all'utente l'autorizzazione per la lettura sia dei metadati per il cubo che dei metadati per la dimensione inclusa nel database.  
  
> [!NOTE]  
>  La lettura dei metadati di un database rappresenta l'autorizzazione minima necessaria per la connessione a un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tramite [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] o [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Un utente che dispone dell'autorizzazione per la lettura dei metadati può inoltre usare il set di righe dello schema DISCOVER_XML_METADATA per eseguire una query sull'oggetto e visualizzarne i metadati. Per altre informazioni, vedere [Set di righe DISCOVER_XML_METADATA](../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md).  
  
## <a name="set-read-definition-permissions-on-a-database"></a>Impostare le autorizzazioni di lettura definizione per un database  
 Quando si concede l'autorizzazione per la lettura dei metadati del database, si concede anche l'autorizzazione per la lettura dei metadati di tutti gli oggetti all'interno del database.  
  
 È consigliabile includere l'autorizzazione **Lettura definizione** a livello di database quando si configurano i ruoli per un'elaborazione dedicata. L'autorizzazione **Lettura definizione** consente agli utenti non amministratori di visualizzare la gerarchia degli oggetti di un modello in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e di visualizzare i singoli oggetti per l'elaborazione successiva.  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], espandere il nodo **Ruoli** relativo al database appropriato in Esplora oggetti, quindi fare clic su un ruolo del database o creare un nuovo ruolo del database.  
  
2.  Nella scheda **Generale** selezionare l'opzione **Lettura definizione** .  
  
3.  Nel riquadro **Appartenenza** immettere gli account utente e di gruppo di Windows che si connettono ad Analysis Services con questo ruolo.  
  
4.  Fare clic su **OK** per completare la creazione del ruolo.  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>Impostare le autorizzazioni di lettura definizione per singoli oggetti  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], aprire la cartella **Database** , selezionare un database, espandere il nodo **Ruoli** relativo al database appropriato in Esplora oggetti, quindi fare clic su un ruolo del database o creare un nuovo ruolo del database.  
  
2.  Nel riquadro **Generale** deselezionare l'autorizzazione del database per **Lettura definizione**. Questo passaggio rimuove l'ereditarietà delle autorizzazioni in modo tale da potere impostare le autorizzazioni per i singoli oggetti.  
  
3.  Selezionare l'oggetto per il quale specificare le proprietà **Lettura definizione** :  
  
    -   Nel riquadro **Origini dati** fare clic sulla casella di controllo **Lettura definizione** per l'origine dati. I membri del ruolo possono visualizzare la stringa di connessione all'origine dati, compresi il nome del server ed eventualmente il nome utente. Questa autorizzazione è disponibile nel caso in cui si desideri fornire le informazioni sulla stringa di connessione, senza tuttavia concedere l'autorizzazione per la modifica della stringa di connessione o per la visualizzazione delle definizioni di altri oggetti.  
  
    -   Nel riquadro **Dimensioni** fare clic sulla casella di controllo **Lettura definizione** per la dimensione. Gli analisti e sviluppatori esperti potrebbero avere l'esigenza di visualizzare la definizione senza l'autorizzazione a modificarla o di visualizzare le definizione di altri oggetti, quali dimensioni, oggetti del cubo o strutture e modelli di data mining.  
  
    -   Nel riquadro Strutture di data mining fare clic sulla casella di controllo **Lettura definizione** per le strutture o i modelli di data mining. L'autorizzazione **Lettura definizione** è obbligatoria per l'esplorazione del modello di dati. Per informazioni dettagliate, vedere [Concedere le autorizzazioni per le strutture e i modelli di data mining &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md).  
  
4.  Nel riquadro **Appartenenza** immettere gli account utente e di gruppo di Windows che si connettono ad Analysis Services con questo ruolo.  
  
5.  Fare clic su **OK** per completare la creazione del ruolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Concedere le autorizzazioni per il database &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)   
 [Concedere le autorizzazioni di elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
  
