---
title: Aggiungere un'aggregazione personalizzata a una dimensione | Documenti Microsoft
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
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63ad6f1d9e72fae70997c87aca194f7437c62d07
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="bi-wizard---add-a-custom-aggregation-to-a-dimension"></a>Creazione guidata BI - aggiungere un'aggregazione personalizzata a una dimensione
  È possibile aggiungere una funzionalità avanzata di aggregazione personalizzata a un cubo o una dimensione per sostituire le aggregazioni predefinite associate a un membro di una dimensione con un operatore unario diverso. Questa funzionalità consente di specificare nella tabella della dimensione una colonna dell'operatore unario che definisce il rollup per i membri di una gerarchia padre-figlio. L'operatore unario funge da attributo padre nella gerarchia padre-figlio.  
  
> [!NOTE]  
>  Un'aggregazione personalizzata è disponibile solo per le dimensioni basate su origini dei dati esistenti. Per le dimensioni create senza utilizzare un'origine dei dati, prima di aggiungere l'aggregazione personalizzata è necessario eseguire la Generazione guidata schema per creare una vista origine dati.  
  
 Per aggiungere un'aggregazione personalizzata, usare la Configurazione guidata funzionalità di Business Intelligence e selezionare l'opzione **Impostazione operatore unario** nella pagina **Scelta funzionalità avanzata** . Questa procedura guidata consente di eseguire in modo semplificato i passaggi necessari per selezionare una dimensione a cui si desidera applicare un'aggregazione personalizzata e identificare l'aggregazione personalizzata.  
  
> [!NOTE]  
>  Prima di eseguire la Configurazione guidata funzionalità di Business Intelligence per aggiungere un'aggregazione personalizzata, verificare che la dimensione a cui deve essere applicata la funzionalità avanzata contenga una gerarchia dell'attributo padre-figlio. Per altre informazioni, vedere [Dimensioni padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension.md).  
  
## <a name="selecting-a-dimension"></a>Selezione di una dimensione  
 Nella prima pagina di **Impostazione operatore unario** della procedura guidata specificare la dimensione a cui si vuole applicare un'aggregazione personalizzata. L'aggiunta dell'aggregazione personalizzata alla dimensione selezionata comporterà modifiche della dimensione. Tali modifiche verranno ereditate da tutti i cubi che includono la dimensione selezionata.  
  
## <a name="adding-custom-aggregation-unary-operator"></a>Aggiunta di un'aggregazione personalizzata (operatore unario)  
 Nella seconda pagina di **Impostazione operatore unario** specificare l'attributo padre desiderato per l'aggregazione personalizzata e la colonna di origine nella tabella della dimensione per l'operatore unario. **Attributo padre** elenca gli attributi per cui la proprietà **Utilizzo** è impostata su **Padre**. Se gli attributi padre sono più di uno, scegliere quello corrispondente alla relazione padre-figlio che si desidera utilizzare. Se non è indicato alcun attributo padre, significa che la dimensione non include una gerarchia padre-figlio valida.  
  
 In **Colonna di origine** selezionare la colonna stringa che contiene gli operatori unari. Questa selezione imposta la proprietà **UnaryOperatorColumn** dell'attributo padre. La tabella della dimensione dovrebbe inoltre contenere una colonna stringa che specifica l'operatore di rollup unario. I valori stringa di questa colonna devono contenere operatori di aggregazione validi. Se una riga è vuota, il membro corrispondente viene calcolato normalmente. Se la formula in una colonna non è valida, si verifica un errore di run-time ogni volta che viene recuperato il valore di una cella che utilizza il membro. Per altre informazioni, vedere [Operatori unari nelle dimensioni padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md).  
  
  
