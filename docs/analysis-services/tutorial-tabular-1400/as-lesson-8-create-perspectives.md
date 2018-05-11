---
title: Analysis Services tutorial lezione 8 creare prospettive | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6de14f79ab00f489913153abefa1ae40aa5608e7
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="create-perspectives"></a>Creare prospettive

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione, si crea una prospettiva Internet Sales. Una prospettiva consente di definire un subset visualizzabile di un modello in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione del modello. Quando un utente si connette a un modello utilizzando una prospettiva, vengono visualizzati solo gli oggetti modello (tabelle, colonne, misure, gerarchie e indicatori KPI) come campi definiti in tale prospettiva. Per ulteriori informazioni, vedere [prospettive](../tabular-models/perspectives-ssas-tabular.md).
  
La prospettiva Internet Sales che è stato creato in questa lezione consente di escludere l'oggetto tabella DimCustomer. Quando si crea una prospettiva che esclude determinati oggetti dalla visualizzazione, l'oggetto esiste ancora nel modello. Tuttavia, non è visibile nell'elenco di campi client reporting. Le colonne e le misure calcolate incluse o meno in una prospettiva consentono ancora eseguire calcoli da dati di oggetto esclusi.  
  
Lo scopo di questa lezione è quello di descrivere come creare prospettive e di consentire di acquisire familiarità con gli strumenti di creazione di modelli tabulari. Se successivamente si espande questo modello per includere tabelle aggiuntive, è possibile creare ulteriori prospettive per definire diversi punti di vista del modello, ad esempio, vendite e inventario.  
  
Tempo stimato per completare questa lezione: **cinque minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 7: creare indicatori di prestazioni chiave](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Creare prospettive  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Per creare una prospettiva Internet Sales  
  
1.  Fare clic su di **modello** menu > **prospettive** > **crea e Gestisci**.  
  
2.  Nella finestra di dialogo **Prospettive** fare clic su **Nuova prospettiva**.  
  
3.  Fare doppio clic su di **nuova prospettiva** intestazione di colonna e quindi rinominare **Internet Sales**.  
  
4.  Selezionare tutte le tabelle *tranne* **DimCustomer**.  
  
    ![prospettive come lesson8](../tutorial-tabular-1400/media/as-lesson8-perspectives.png)
  
    In una lezione successiva, si usa analizza nella funzionalità di Excel per testare questa prospettiva. Nell'elenco campi tabella pivot di Excel include ogni tabella, tranne la tabella DimCustomer.  

## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 9: Creare gerarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md).
  
  
  
  
