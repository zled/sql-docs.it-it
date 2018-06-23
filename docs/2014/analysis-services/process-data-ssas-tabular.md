---
title: Elaborare dati (SSAS tabulare) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 605c0b0171eadbab3e2fb7265ed5059ae521d011
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158339"
---
# <a name="process-data-ssas-tabular"></a>Elaborare dati (SSAS tabulare)
  Quando si importano dati in un modello tabulare, nella modalità cache si acquisisce uno snapshot di tali dati al momento dell'importazione. In alcuni casi, tali dati potrebbero non cambiare mai, pertanto non devono essere aggiornati nel modello. Tuttavia, è più probabile che i dati che si importano cambino regolarmente, pertanto affinché il modello rifletta i dati più recenti delle origini dati, è necessario elaborarli (aggiornarli) e calcolare nuovamente i dati calcolati. Per aggiornare i dati nel modello, è necessario eseguire un'azione di elaborazione in tutte le tabelle, in una singola tabella, in base a una partizione o a una connessione all'origine dati.  
  
 Durante la creazione del progetto di modello, tutte le azioni di elaborazione devono essere avviate manualmente in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Dopo la distribuzione di un modello, le operazioni di elaborazione possono essere eseguite tramite [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oppure pianificate utilizzando uno script. Tutte le attività descritte di seguito riguardano le azioni di elaborazione che è possibile eseguire durante la creazione di modelli in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Per ulteriori informazioni sulle azioni di elaborazione per un modello distribuito, vedere [elaborare Database, tabella o partizione](tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Elaborare manualmente i dati &#40;tabulare di SSAS&#41;](manually-process-data-ssas-tabular.md)|Viene descritto come elaborare manualmente i dati dell'area di lavoro modello.|  
|[Risolvere i problemi di elaborazione dei dati &#40;tabulare di SSAS&#41;](troubleshoot-process-data-ssas-tabular.md)|Viene descritto come risolvere i problemi relativi alle operazioni di elaborazione.|  
  
  