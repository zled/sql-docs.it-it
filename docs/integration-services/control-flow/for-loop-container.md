---
title: "Contenitore Ciclo For | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.forloopcontainerdetails.f1"
  - "sql13.dts.designer.forloopcontainer.f1"
helpviewer_keywords: 
  - "repeating control flow"
  - "contenitori [Integration Services], Ciclo For"
  - "Ciclo For - contenitori"
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
caps.latest.revision: 55
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 54
---
# Contenitore Ciclo For
  Il contenitore Ciclo For definisce un flusso di controllo ripetuto all'interno di un pacchetto. L'implementazione del ciclo è simile alla struttura del ciclo **For** nei linguaggi di programmazione. A ogni ripetizione del ciclo il contenitore Ciclo For valuta un'espressione e ne ripete il flusso di lavoro finché tale espressione non restituisce **False**.  
  
 Per definire il ciclo, il contenitore Ciclo For usa gli elementi seguenti:  
  
-   Un'espressione di inizializzazione facoltativa che assegna valori ai contatori del ciclo.  
  
-   Un'espressione di valutazione che contiene l'espressione utilizzata per stabilire se il ciclo deve essere arrestato o continuare.  
  
-   Un'espressione di iterazione facoltativa che incrementa o decrementa il contatore del ciclo.  
  
 Nella figura seguente viene illustrato un contenitore Ciclo For con un'attività Invia messaggi. Se l'espressione di inizializzazione è `@Counter = 0`, l'espressione di valutazione è `@Counter < 4` e l'espressione di iterazione è `@Counter = @Counter + 1`, il ciclo si ripeterà quattro volte e verranno inviati quattro messaggi di posta elettronica.  
  
 ![Un contenitore Ciclo For ripete un'attività quattro volte](../../integration-services/control-flow/media/ssis-forloop.gif "Un contenitore Ciclo For ripete un'attività quattro volte")  
  
 Le espressioni devono essere espressioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] valide.  
  
 Per creare le espressioni di inizializzazione e assegnazione, è possibile utilizzare l'operatore di assegnazione (=). In altre circostanze questo operatore non è supportato dalla grammatica delle espressioni di Integration Services, ma può essere utilizzato solo dai tipi di espressione di inizializzazione e assegnazione nel contenitore Ciclo For. Tutte le espressioni che usano l'operatore di assegnazione devono presentare la sintassi `@Var = <expression>`, dove **Var** è una variabile di run-time ed \<expression> è un'espressione che segue le regole della sintassi delle espressioni di [!INCLUDE[ssIS](../../includes/ssis-md.md)]. L'espressione può includere le variabili, i valori letterali e tutti gli operatori e le funzioni supportati dalla grammatica delle espressioni di SSIS. L'espressione deve restituire un tipo di dati di cui è possibile eseguire il cast al tipo di dati della variabile.  
  
 Un contenitore Ciclo For può includere una sola espressione di valutazione, pertanto esegue tutti gli elementi del flusso di controllo per lo stesso numero di volte. Poiché un contenitore Ciclo For può includere altri contenitori Ciclo For, nei pacchetti è possibile compilare cicli nidificati e implementare loop complessi.  
  
 È possibile impostare una proprietà di transazione sul contenitore Ciclo For per definire una transazione per un subset del flusso di controllo del pacchetto. In questo modo è possibile gestire le transazioni con un livello di granularità superiore. Se ad esempio un contenitore Ciclo For ripete un flusso di controllo che aggiorna più volte i dati di una tabella, sarà possibile configurare il ciclo For e il relativo flusso di controllo per l'utilizzo di una transazione, in modo da assicurare che se non è possibile aggiornare correttamente tutti i dati, non ne verrà aggiornato alcuno. Per altre informazioni, vedere [Transazioni di Integration Services](../../integration-services/integration-services-transactions.md).  
  
## Configurazione del contenitore Ciclo For  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Editor ciclo For](../Topic/For%20Loop%20Editor.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per altre informazioni sull'impostazione a livello di codice di queste proprietà, vedere la documentazione per la classe **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** nella Guida per gli sviluppatori.  
  
## Attività correlate  
 Per informazioni sulla configurazione di un contenitore Ciclo For, vedere gli argomenti seguenti.  
  
-   [Configurazione di un contenitore Ciclo For](../Topic/Configure%20a%20For%20Loop%20Container.md)  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Vedere anche  
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)   
 [Espressioni di Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  