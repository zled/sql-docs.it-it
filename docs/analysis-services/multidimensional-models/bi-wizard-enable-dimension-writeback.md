---
title: Abilitazione writeback della dimensione | Documenti Microsoft
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
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e5ca1ff1e48da8fb464ffe9d2e8c7a4427980030
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="bi-wizard---enable-dimension-writeback"></a>Creazione guidata BI - Abilita il Writeback delle dimensioni
  Aggiungere a un cubo o a una dimensione la funzionalità avanzata di writeback della dimensione per consentire agli utenti di modificare manualmente la struttura e i membri della dimensione. Gli aggiornamenti di una dimensione abilitata per la scrittura vengono registrati direttamente nella tabella della dimensione. Questa funzionalità avanzata modifica l'impostazione della proprietà **WriteEnabled** per una dimensione.  
  
 Per aggiungere il writeback della dimensione, usare Configurazione guidata funzionalità di Business Intelligence e selezionare l'opzione **Abilitazione writeback della dimensione** nella pagina **Scelta funzionalità avanzata** . Questa procedura guidata consente di eseguire in modo semplificato i passaggi per la selezione di una dimensione alla quale si desidera applicare il writeback della dimensione e per l'impostazione di questa opzione per la dimensione selezionata.  
  
> [!NOTE]  
>  Il writeback è supportato solo per i database relazionali e i data mart di SQL Server.  
  
## <a name="selecting-a-dimension"></a>Selezione di una dimensione  
 Nella prima pagina della procedura guidata **Abilitazione writeback della dimensione** specificare la dimensione alla quale si desidera applicare il writeback della dimensione. La funzionalità avanzata di writeback della dimensione aggiunta alla dimensione selezionata risulterà tra le modifiche apportate alla dimensione. Tali modifiche verranno ereditate da tutti i cubi che includono la dimensione selezionata.  
  
## <a name="setting-dimension-writeback-capability"></a>Impostazione della funzionalità di writeback della dimensione  
 Nella seconda pagina della procedura guidata **Abilitazione writeback della dimensione** è possibile effettivamente impostare l'opzione **Consenti writeback della dimensione** . Selezionando questa opzione, la proprietà **WriteEnabled** della dimensione viene impostata automaticamente su **True**. Deselezionando questa opzione la proprietà viene impostata automaticamente su **False**.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si crea un nuovo membro, è necessario includere ogni attributo di una dimensione. Non è possibile inserire un membro senza specificare un valore per l'attributo chiave della dimensione. La creazione di membri è pertanto soggetta a tutti i vincoli, ad esempio valori di chiave non Null, definiti nella tabella della dimensione. È consigliabile inoltre considerare le colonne che possono essere specificate dalle proprietà della dimensione, ad esempio quelle specificate nella proprietà della dimensione **CustomRollupColumn**, **CustomRollupPropertiesColumn** o **UnaryOperatorColumn** .  
  
> [!WARNING]  
>  Se si utilizza SQL Azure come origine dati per eseguire il writeback in un database di Analysis Services, l'operazione non viene completata. Questo si verifica per motivi strutturali, dal momento che l'opzione provider che abilita il servizio MARS (Multiple Active Result Sets) non è abilitata per impostazione predefinita.  
>   
>  La soluzione alternativa consiste nell'aggiungere l'impostazione seguente nella stringa di connessione, per supportare il servizio MARS e abilitare il writeback:  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Per altre informazioni vedere [Utilizzo di MARS &#40;Multiple Active Result Set&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dimensioni abilitate per la scrittura](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
