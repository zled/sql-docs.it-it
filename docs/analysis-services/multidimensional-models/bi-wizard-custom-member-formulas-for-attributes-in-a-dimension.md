---
title: Impostare formule personalizzate membro per gli attributi in una dimensione | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], custom member formulas
- member formulas [Analysis Services]
- dimensions [Analysis Services], Business Intelligence enhancements
- custom member formulas [Analysis Services]
- CustomRollupColumn property
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e9f2afe453c4321ec9767a3cb8a97215d55c877
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="bi-wizard---custom-member-formulas-for-attributes-in-a-dimension"></a>Creazione guidata BI - formule personalizzate membro per gli attributi in una dimensione
  L'aggiunta della funzionalità avanzata delle formule personalizzate membro a un cubo o a una dimensione consente di sostituire la funzione di aggregazione predefinita associata a un membro della dimensione con i risultati di un'espressione MDX (Multidimensional Expressions). Questa funzionalità avanzata imposta la proprietà **CustomRollupColumn** di un attributo specifico in una dimensione.  
  
> [!NOTE]  
>  Una formula personalizzata membro è disponibile solo per le dimensioni basate su origini dei dati esistenti. Per le dimensioni create senza l'utilizzo di un'origine dei dati è necessario eseguire Generazione guidata schema per creare una vista origine dati prima di aggiungere una formula personalizzata membro.  
  
 Per aggiungere una formula personalizzata membro, usare Configurazione guidata funzionalità di Business Intelligence e selezionare l'opzione **Creazione formula personalizzata membro** nella pagina **Scelta funzionalità avanzata** . Questa procedura guidata consente di eseguire in modo semplificato i passaggi relativi alla selezione di una dimensione alla quale si desidera applicare una formula personalizzata membro e all'abilitazione della formula personalizzata membro specifica.  
  
## <a name="selecting-a-dimension"></a>Selezione di una dimensione  
 Nella prima pagina **Creazione formula personalizzata membro** della procedura guidata specificare la dimensione alla quale applicare una formula personalizzata membro. L'aggiunta della funzionalità avanzata della formula personalizzata membro alla dimensione selezionata implica modifiche alla dimensione. Tali modifiche verranno ereditate da tutti i cubi che includono la dimensione selezionata.  
  
## <a name="enabling-a-custom-member-formula"></a>Abilitazione di una formula personalizzata membro  
 Nella seconda pagina **Creazione formula personalizzata membro** associare la colonna di origine contenente la formula personalizzata membro a uno o più attributi nella dimensione. Nella colonna **Attributo** selezionare la casella di controllo accanto all'attributo da associare alla colonna della formula personalizzata membro. Dopo aver selezionato ogni attributo, viene visualizzata la finestra di dialogo **Seleziona colonna** . In questa finestra di dialogo fare clic nella colonna della tabella della dimensione contenente la formula. Se dopo aver chiuso la finestra di dialogo **Seleziona colonna** si desidera modificare una selezione, fare clic nella cella **Colonna di origine** da modificare e quindi sui puntini di sospensione (**...**) per visualizzare nuovamente la finestra di dialogo **Seleziona colonna** .  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la Configurazione guidata funzionalità di Business Intelligence per migliorare le dimensioni](http://msdn.microsoft.com/library/12d995d1-75ca-4890-bf4b-a2656910b8d0)  
  
  

