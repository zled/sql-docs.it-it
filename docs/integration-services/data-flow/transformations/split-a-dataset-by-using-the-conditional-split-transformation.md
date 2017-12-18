---
title: Dividere un set di dati tramite la trasformazione Suddivisione condizionale | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
caps.latest.revision: "40"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 04462fe588d783d9a4c8fbde3487866084d7d8e5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a>Dividere un set di dati tramite la trasformazione Suddivisione condizionale
  È possibile aggiungere e configurare una trasformazione Suddivisione condizionale solo se il pacchetto include già almeno un'attività Flusso di dati e un'origine.  
  
### <a name="to-conditionally-split-a-dataset"></a>Per eseguire la suddivisione condizionale di un set di dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi, dalla **casella degli strumenti**, trascinare la trasformazione Suddivisione condizionale sull'area di progettazione.  
  
4.  Connettere la trasformazione Suddivisione condizionale al flusso di dati trascinando il connettore dall'origine dati o dalla trasformazione precedente alla trasformazione Suddivisione condizionale.  
  
5.  Fare doppio clic sulla trasformazione Suddivisione condizionale.  
  
6.  Nella finestra di dialogo **Editor trasformazione Suddivisione condizionale**compilare le espressioni da usare come condizioni trascinando variabili, colonne, funzioni e operatori nella colonna **Condizione** della griglia. In alternativa, digitare l'espressione nella colonna **Condizione** .  
  
    > [!NOTE]  
    >  È possibile utilizzare una stessa variabile o colonna in più espressioni.  
  
    > [!NOTE]  
    >  Se l'espressione non è valida, il testo dell'espressione viene evidenziato e tramite una descrizione comando nella colonna vengono descritti gli errori.  
  
7.  Facoltativamente, modificare i valori nella colonna **Nome output** . I nomi predefiniti sono Case 1, Case 2 e così via.  
  
8.  Per modificare la sequenza in cui vengono valutate le condizioni, fare clic sulla freccia in su o sulla freccia in giù.  
  
    > [!NOTE]  
    >  Collocare le condizioni più probabili all'inizio dell'elenco.  
  
9. Facoltativamente, modificare il nome dell'output predefinito per le righe di dati che non soddisfano alcuna condizione.  
  
10. Per configurare un output degli errori, fare clic su **Configura output errori**. Per altre informazioni, vedere [Debug di un flusso di dati](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
11. Scegliere **OK**.  
  
12. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Tipi di dati di Integration Services](../../../integration-services/data-flow/integration-services-data-types.md)   
 [Attività Flusso di dati](../../../integration-services/control-flow/data-flow-task.md)   
 [Espressioni di Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  
