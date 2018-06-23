---
title: Analysis Services deprecate in SQL Server 2014 | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- deprecated features [Analysis Services]
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 49a65a9ca1684a7bcec7b5f7f1d19d38b01f13d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065246"
---
# <a name="deprecated-analysis-services-features-in-sql-server-2014"></a>Funzionalità di Analysis Services deprecate in SQL Server 2014
  In questo argomento verranno descritte le funzionalità deprecate di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ancora disponibili in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Tali funzionalità verranno rimosse a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È consigliabile non usare le funzionalità deprecate nelle nuove applicazioni.  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Funzionalità non supportate nella prossima versione di SQL Server  
 Le funzionalità riportate di seguito di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] non saranno supportate nella prossima versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Non usare queste funzionalità in un nuovo progetto di sviluppo e modificare non appena possibile le applicazioni in cui sono attualmente implementate.  
  
|Category|Funzionalità deprecata|Sostituzione|  
|--------------|------------------------|-----------------|  
|Funzione MDX|Funzione CalculationPassValue|Nessuna. Il motore OLAP gestisce la sessione di calcolo. Questa funzione non è più necessaria.|  
|Funzione MDX|CalculationCurrentPass - funzione|Nessuna. Il motore OLAP gestisce la sessione di calcolo. Questa funzione non è più necessaria.|  
|Espressioni MDX (MDX)|L'hint di Query Optimizer NON_EMPTY_BEHAVIOR è abilitato per impostazione predefinita.|L'hint di Query Optimizer NON_EMPTY_BEHAVIOR sarà disabilitato per impostazione predefinita in una versione successiva. Si tratta di un hint dell'ottimizzazione di MDX che può produrre risultati non corretti quando non viene utilizzato in modo appropriato.|  
|Altro|Proprietà intrinseca di cella CELL_EVALUATION_LIST|Inizialmente veniva fornito un elenco di formule valutate applicabili a una cella. In questa versione di Analysis Services è vuota.  Adesso l'ordine di valutazione è specificato in script MDX. Per altre informazioni, vedere [comprensione e l'ordine di valutazione &#40;MDX&#41;](multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|  
|Oggetti|Assembly COM|È possibile che gli assembly COM creino un rischio per la sicurezza. Il supporto per assembly COM verrà rimossa in una versione successiva.|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Funzionalità non supportate in una futura versione di SQL Server  
 Le funzionalità seguenti del [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sono supportate nella versione successiva di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ma in seguito verranno rimosse. La versione specifica di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non è stata determinata.  
  
|Category|Funzionalità deprecata|Sostituzione|  
|--------------|------------------------|-----------------|  
|Modelli multidimensionali|Partizioni remote|Nessuna. Utilizzare, in alternativa, le partizioni locali. Vedere [creare e gestire una partizione locale &#40;Analysis Services&#41; ](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md) per altre informazioni.|  
|Modelli multidimensionali|Gruppi di misure collegati remoti|Un gruppo di misure collegato remoto è un gruppo di misure collegato tramite un'origine dati in un server remoto. La possibilità di usare un'origine dati remota per un gruppo di misure collegato è ora pianificata per l'eliminazione.<br /><br /> Non sono disponibili sostituzioni per questa funzionalità. È consigliabile usare, in alternativa, gruppi di misure collegati locali. Vedere [Linked Measure Groups](multidimensional-models/linked-measure-groups.md) per altre informazioni.|  
|Modelli multidimensionali|Writeback dimensionale|Nessuna. Utilizzare il writeback di partizione se è richiesta la funzionalità di writeback. Vedere [Set Partition Writeback](multidimensional-models/set-partition-writeback.md) per altre informazioni.|  
|Modelli multidimensionali|Dimensioni collegate|Nessuna. Si consideri la copia delle dimensioni in modelli aggiuntivi anziché il collegamento a una dimensione in un altro modello.|  
|MDX|Proprietà Non_Empty_Behavior|Nessuna. L'impostazione non corretta di questa proprietà durante la creazione di un membro calcolato aumenta le probabilità che vengano restituiti risultati non validi. Le recenti ottimizzazioni apportate al motore OLAP hanno migliorato le operazioni sui set di dati di tipo sparse, rendendo meno rilevante questa proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Compatibilità con le versioni precedenti di Analysis Services](analysis-services-backward-compatibility.md)   
 [Caratteristiche non più disponibili di Analysis Services in SQL Server 2014](discontinued-analysis-services-functionality-in-sql-server-2014.md)  
  
  