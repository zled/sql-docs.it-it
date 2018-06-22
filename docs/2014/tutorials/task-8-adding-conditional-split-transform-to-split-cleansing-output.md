---
title: "Attività 8: Aggiunta Conditional Split trasformazione per suddividere l'Output di pulizia | Documenti Microsoft"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6dc3b98e03a7940841bc97012c1a4e4220bb970d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156392"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>Attività 8: Aggiunta della trasformazione Suddivisione condizionale aggiunta dell'output di pulizia della suddivisione
  In questa trasformazione viene aggiunta la trasformazione Suddivisione condizionale al flusso di dati. La trasformazione Suddivisione condizionale consente di indirizzare le righe verso output diversi in base al contenuto dei dati. Per questa esercitazione, si utilizza il **stato Record** colonna di output dalla trasformazione DQS Cleansing. In questa esercitazione verranno caricati solo i record corretti o con correzione nel server MDS. Pertanto, controllare se il **stato Record** viene **corretti** oppure **con correzione**e combinare i record prima di caricarli in MDS.  
  
1.  Trascinare **trasformazione Suddivisione condizionale** da **comuni** sezione il **casella degli strumenti SSIS** per il **del flusso di dati** scheda **Pulisci dati fornitore**.  
  
2.  Fare doppio clic su **suddivisione condizionale**, fare clic su **rinominare**. Tipo di **Seleziona record corretti e** e premere **invio**.  
  
3.  Connettersi **Pulisci dati fornitore** e **Seleziona record corretti e** utilizzando il collegamento blu.  
  
     ![CLEANSE Supplier Data -> scegliere corretti con correzione](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Cleanse Supplier Data -> scegliere corretti con correzione")  
  
4.  Fare doppio clic su **Seleziona record corretti e** nel **del flusso di dati** scheda.  
  
5.  Modifica il **nome Output predefinito** nella parte inferiore della schermata per **corretti**.  
  
6.  Espandere **colonne** nel **riquadro superiore sinistro**.  
  
     ![Editor trasformazione Suddivisione condizionale](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Editor trasformazione Suddivisione condizionale")  
  
7.  Trascinare **stato Record** per il **condizione** colonna.  
  
8.  Tipo di **= = "Corrected"** accanto a **[Record Status]** per il **condizione** colonna.  
  
9. Fare clic su **Case 1** nel **colonna nome Output**e modificare il nome in **con correzione**.  
  
10. Fare clic su **OK** per chiudere la **Editor trasformazione Suddivisione condizionale** finestra di dialogo.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 9: Aggiunta della unione trasformazione multipli per combinare i record corretti e con correzioni](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  