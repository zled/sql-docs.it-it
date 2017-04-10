---
title: "Impostare formule personalizzate membro per gli attributi in una dimensione | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "miglioramenti di Business Intelligence [Analysis Services], formule personalizzate membri"
  - "formule membri [Analysis Services]"
  - "dimensioni [Analysis Services], miglioramenti di Business Intelligence"
  - "formule personalizzate membri [Analysis Services]"
  - "CustomRollupColumn - proprietà"
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Impostare formule personalizzate membro per gli attributi in una dimensione
  L'aggiunta della funzionalità avanzata delle formule personalizzate membro a un cubo o a una dimensione consente di sostituire la funzione di aggregazione predefinita associata a un membro della dimensione con i risultati di un'espressione MDX (Multidimensional Expressions). Questa funzionalità avanzata imposta la proprietà **CustomRollupColumn** di un attributo specifico in una dimensione.  
  
> [!NOTE]  
>  Una formula personalizzata membro è disponibile solo per le dimensioni basate su origini dei dati esistenti. Per le dimensioni create senza l'utilizzo di un'origine dei dati è necessario eseguire Generazione guidata schema per creare una vista origine dati prima di aggiungere una formula personalizzata membro.  
  
 Per aggiungere una formula personalizzata membro, usare Configurazione guidata funzionalità di Business Intelligence e selezionare l'opzione **Creazione formula personalizzata membro** nella pagina **Scelta funzionalità avanzata**. Questa procedura guidata consente di eseguire in modo semplificato i passaggi relativi alla selezione di una dimensione alla quale si desidera applicare una formula personalizzata membro e all'abilitazione della formula personalizzata membro specifica.  
  
## Selezione di una dimensione  
 Nella prima pagina **Creazione formula personalizzata membro** della procedura guidata specificare la dimensione alla quale applicare una formula personalizzata membro. L'aggiunta della funzionalità avanzata della formula personalizzata membro alla dimensione selezionata implica modifiche alla dimensione. Tali modifiche verranno ereditate da tutti i cubi che includono la dimensione selezionata.  
  
## Abilitazione di una formula personalizzata membro  
 Nella seconda pagina **Creazione formula personalizzata membro** associare la colonna di origine contenente la formula personalizzata membro a uno o più attributi nella dimensione. Nella colonna **Attributo** selezionare la casella di controllo accanto all'attributo da associare alla colonna della formula personalizzata membro. Dopo aver selezionato ogni attributo, viene visualizzata la finestra di dialogo **Seleziona colonna**. In questa finestra di dialogo fare clic nella colonna della tabella della dimensione contenente la formula. Se dopo aver chiuso la finestra di dialogo **Seleziona colonna** si desidera modificare una selezione, fare clic nella cella **Colonna di origine** da modificare e quindi sui puntini di sospensione (**...**) per visualizzare nuovamente la finestra di dialogo **Seleziona colonna**.  
  
## Vedere anche  
 [Utilizzare la Configurazione guidata funzionalità di Business Intelligence per migliorare le dimensioni](../Topic/Use%20the%20Business%20Intelligence%20Wizard%20to%20Enhance%20Dimensions.md)  
  
  