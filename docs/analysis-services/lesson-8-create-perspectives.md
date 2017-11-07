---
title: Lezione 9 creare prospettive | Documenti Microsoft
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 993cf02a47240c0a74667f6220c6b2dd5d6df86c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-8-create-perspectives"></a>Lezione 8: Creare prospettive
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione verrà creata una prospettiva Internet Sales. Una prospettiva consente di definire un subset visualizzabile di un modello in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione del modello. Quando un utente si connette a un modello utilizzando una prospettiva, vengono visualizzati solo gli oggetti modello (tabelle, colonne, misure, gerarchie e indicatori KPI) come campi definiti in tale prospettiva.  
  
La prospettiva Internet Sales che è stato creato in questa lezione escluderà l'oggetto tabella DimCustomer. Quando si crea una prospettiva che esclude determinati oggetti dalla visualizzazione, tali oggetti sono ancora presenti nel modello; tuttavia non sono visibili in un elenco di campi di un client di creazione di report. Le colonne e le misure calcolate incluse o meno in una prospettiva consentono ancora eseguire calcoli da dati di oggetto esclusi.  
  
Lo scopo di questa lezione è quello di descrivere come creare prospettive e di consentire di acquisire familiarità con gli strumenti di creazione di modelli tabulari. Se successivamente si espande questo modello per includere tabelle aggiuntive, è possibile creare ulteriori prospettive per definire diversi punti di vista del modello, ad esempio, vendite e inventario. Per altre informazioni, vedere [Prospettive](../analysis-services/tabular-models/perspectives-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 7: creare indicatori di prestazioni chiave](../analysis-services/lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Creare prospettive  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Per creare una prospettiva Internet Sales  
  
1.  Fare clic su di **modello** menu > **prospettive** > **crea e Gestisci**.  
  
2.  Nella finestra di dialogo **Prospettive** fare clic su **Nuova prospettiva**.  
  
3.  Fare doppio clic su di **nuova prospettiva** intestazione di colonna e quindi rinominare **Internet Sales**.  
  
4.  Selezionare tutte le tabelle *tranne* **DimCustomer**.  
  
    ![come-tabulare-lesson8-prospettive](../analysis-services/media/as-tabular-lesson8-perspectives.png)
  
    In una lezione successiva si utilizzerà l'analizza nella funzionalità di Excel per testare questa prospettiva. Nell'elenco campi tabella pivot di Excel includerà ogni tabella, tranne la tabella DimCustomer.  

## <a name="whats-next"></a>Operazioni successive
Passare alla lezione successiva: [lezione 9: creare gerarchie](../analysis-services/lesson-9-create-hierarchies.md).
  
  
  
  

