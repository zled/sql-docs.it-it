---
title: "Aggiungere o modificare un'espressione di proprietà | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Integration Services], creating
- expressions [Integration Services], property expressions
ms.assetid: cb5da499-065f-4fa6-9f6d-5bc5f385241e
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e9f115f318366e743e0a933239b55ccda16b5171
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="add-or-change-a-property-expression"></a>Aggiunta o modifica di un'espressione di proprietà
  È possibile creare espressioni di proprietà per pacchetti, attività, contenitori Ciclo Foreach, contenitori Ciclo For, contenitori Sequenza, gestori di eventi, gestioni connessioni a livello di pacchetto e progetto e provider di log.  
  
 Per creare o modificare espressioni di proprietà, è possibile usare l' **Editor espressioni di proprietà** o il **Generatore di espressioni**. È possibile accedere all' **Editor espressioni di proprietà** dagli editor personalizzati disponibili per attività e contenitori o dalla finestra **Proprietà** . È possibile accedere al**Generatore di espressioni** dall' **Editor espressioni di proprietà**. È possibile scrivere espressioni sia nell'**Editor espressioni di proprietà** che nel **Generatore di espressioni**, ****tuttavia quest'ultimo offre un set di strumenti dell'interfaccia grafica che semplificano la compilazione di espressioni complesse.  
  
 Per sapere di più sulla sintassi, gli operatori e le funzioni offerti da [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vedere [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md) e [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md). Gli argomenti relativi a ogni operatore e funzione includono esempi di utilizzo dell'operatore o della funzione in un'espressione. Per esempi di espressioni più complesse, vedere [Utilizzo delle espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
### <a name="to-create-or-change-a-property-expression"></a>Per creare o modificare un'espressione di proprietà  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto che contiene il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo e quindi eseguire una delle operazioni seguenti.  
  
    -   Nel caso di un'attività o di un contenitore, fare doppio clic sull'elemento e quindi su **Espressioni** nell'editor.  
  
    -   Fare clic con il pulsante destro del mouse sull'elemento e scegliere **Proprietà**.  
  
3.  Fare clic nella casella **Espressioni** e quindi sui puntini di sospensione (…).  
  
4.  Nell' **Editor espressioni di proprietà**selezionare una proprietà nell'elenco **Proprietà** ed eseguire una delle operazioni seguenti:  
  
    -   Digitare o modificare direttamente l'espressione di proprietà nella colonna **Espressione** , quindi fare clic su **OK**.  
  
         -oppure-  
  
    -   Fare clic sui puntini di sospensione (...) nella riga dell'espressione della proprietà per aprire il **Generatore di espressioni**.  
  
5.  (Facoltativo) Nel **Generatore di espressioni**, eseguire una delle attività seguenti:  
  
    -   Per accedere a variabili definite dal sistema e dall'utente, espandere **Variabili**.  
  
    -   Per accedere alle funzioni, ai cast e agli operatori del linguaggio delle espressioni di [!INCLUDE[ssIS](../../includes/ssis-md.md)] , espandere i nodi **Funzioni matematiche**, **Funzioni per i valori stringa**, **Funzioni di data/ora**, **Funzioni NULL**, **Cast di tipo**e **Operatori**.  
  
    -   Per compilare o modificare un'espressione nel **Generatore di espressioni**, trascinare le variabili, le colonne, le funzioni, gli operatori e i cast nella casella **Espressione** oppure digitare direttamente l'espressione nella casella.  
  
    -   Per visualizzare il risultato della valutazione dell'espressione, fare clic su **Valuta espressione** nel **Generatore di espressioni**.  
  
         Se l'espressione non è valida, viene visualizzato un avviso che evidenzia gli errori di sintassi.  
  
        > [!NOTE]  
        >  Quando si valuta un'espressione, il risultato della valutazione non viene assegnato alla proprietà.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Espressioni](../../integration-services/expressions/integration-services-ssis-expressions.md)   
 [Utilizzare le espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md)   
 [Integration Services &#40; SSIS &#41; Pacchetti](../../integration-services/integration-services-ssis-packages.md)   
 [Contenitori in Integration Services](../../integration-services/control-flow/integration-services-containers.md)   
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Integration Services &#40; SSIS &#41; Gestori eventi](../../integration-services/integration-services-ssis-event-handlers.md)   
 [Integration Services &#40; SSIS &#41; Connessioni](../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Integration Services &#40; SSIS &#41; Registrazione](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
