---
title: Scelta funzionalità avanzata (configurazione guidata Business Intelligence) | Documenti Microsoft
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
- sql12.asvs.biwizard.bienhancement.f1
ms.assetid: 39e2f36c-2c02-4a71-af8f-5dbd373190dc
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1377e93214ff5d9e459698946551ffaed6723390
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169786"
---
# <a name="choose-enhancement-business-intelligence-wizard"></a>Scelta funzionalità avanzata (Configurazione guidata funzionalità di Business Intelligence)
  Usare la pagina **Scelta funzionalità avanzata** per scegliere la funzionalità avanzata di Business Intelligence da aggiungere al cubo o alla dimensione.  
  
## <a name="options"></a>Opzioni  
 **Funzionalità avanzate disponibili**  
 Consente di selezionare la funzionalità avanzata di Business Intelligence da aggiungere. Nella tabella seguente vengono elencate le funzionalità avanzate disponibili.  
  
|Funzionalità avanzata|Description|  
|-----------------|-----------------|  
|**Definizione funzionalità di tempo**|Consente di aggiungere viste temporali supplementari per una gerarchia selezionata. Sono disponibili viste per il calcolo dei dati di un periodo rispetto alla data corrente, di un periodo specifico o della media mobile dei dati in un periodo.<br /><br /> Nota: questa opzione è disponibile solo per i cubi.|  
|**Definizione funzionalità di business intelligence**|Consente di assegnare classificazioni contabili standard, ad esempio entrate e uscite, ai membri di un attributo di tipo Conto.<br /><br /> Se la funzione di aggregazione per la misura è impostata su *ByAccount*, l'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] usa le classificazioni contabili per aggregare nel tempo una misura sui membri di un attributo di tipo Conto.|  
|**Definizione funzionalità di business intelligence**|Utilizzare la funzionalità di Business Intelligence per le dimensioni per specificare un tipo aziendale standard per una dimensione e i tipi validi per i relativi attributi. Queste specifiche del tipo possono essere utilizzate dalle applicazioni client per l'analisi dei dati.|  
|**Specificare un operatore unario**|Consente di specificare un operatore unario per sostituire l'aggregazione predefinita associata ai membri di una gerarchia padre-figlio inclusa in un cubo.<br /><br /> Nota: questa opzione è disponibile solo per i cubi.|  
|**Creare una formula personalizzata membro**|Consente di creare una formula personalizzata membro per sostituire l'aggregazione predefinita associata al membro di una dimensione con un operatore diverso.|  
|**Impostazione ordinamento attributi**|Consente di specificare il tipo di ordinamento dei membri di un attributo selezionato. I membri possono essere ordinati in base al nome o alla chiave di un attributo selezionato, oppure in base al nome o alla chiave di un attributo correlato all'attributo selezionato. Per impostazione predefinita, i membri vengono ordinati in base al nome dell'attributo selezionato.|  
|**Abilitazione writeback della dimensione**|Consente di attivare la modifica manuale della struttura della dimensione. Gli aggiornamenti di una dimensione abilitata per la scrittura vengono registrati direttamente nella tabella della dimensione.|  
|**Definisci funzioni semiadditive**|Consente di definire manualmente il metodo di aggregazione per le singole misure o i membri di un attributo di tipo Conto. Se il cubo contiene una dimensione di tipo Conti, è possibile usare l'opzione **Funzionalità di Business Intelligence per la contabilità** per impostare automaticamente le funzioni semiadditive in base al tipo di conto.<br /><br /> Nota: questa opzione è disponibile solo per i cubi.|  
|**Definizione conversione valuta**|Consente di definire le regole per la conversione e l'analisi dei dati multinazionali nel cubo. Le regole per la conversione vengono applicate a livello del cubo utilizzando uno script MDX (Multidimensional Expressions) generato dalla Configurazione guidata funzionalità di Business Intelligence.<br /><br /> Nota: questa opzione è disponibile solo per i cubi.|  
  
 **Descrizione**  
 Consente di visualizzare una breve descrizione della funzionalità avanzata di Business Intelligence selezionata.  
  
## <a name="see-also"></a>Vedere anche  
 [Business Intelligence guidata F1 Help](business-intelligence-wizard-f1-help.md)   
 [Finestra di progettazione del cubo &#40;Analysis Services - dati multidimensionali&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Finestra di progettazione della dimensione &#40;Analysis Services - dati multidimensionali&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  