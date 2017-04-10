---
title: "Editor trasformazione Suddivisione condizionale | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.conditionalsplittransformation.f1"
helpviewer_keywords: 
  - "Editor trasformazione Suddivisione condizionale"
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Editor trasformazione Suddivisione condizionale
  Utilizzare la finestra di dialogo **Editor trasformazione Suddivisione condizionale** per creare espressioni e impostare l'ordine in cui vengono valutate, nonché per assegnare un nome agli output di una suddivisione condizionale. In questa finestra di dialogo sono inclusi funzioni e operatori matematici, di data/ora e per i valori stringa che possono essere utilizzati per la compilazione di espressioni. La prima condizione che restituisce true determina l'output a cui è indirizzata una riga.  
  
> [!NOTE]  
>  La trasformazione Suddivisione condizionale indirizza ogni riga di input a un unico output. Se si immettono più condizioni, la trasformazione invierà ogni riga al primo output per cui la condizione è verificata e ignorerà le successive condizioni per tale riga. Per valutare più condizioni consecutivamente, potrebbe essere necessario concatenare più trasformazioni Suddivisione condizionale nel flusso di dati.  
  
 Per altre informazioni sulla trasformazione Suddivisione condizionale, vedere [Trasformazione Suddivisione condizionale](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
## Opzioni  
 **JSON**  
 Selezionare una riga e utilizzare i tasti di direzione a destra per modificare l'ordine in base a cui valutare le espressioni.  
  
 **Nome output**  
 Consente di specificare un nome per l'output. Per impostazione predefinita viene suggerito un elenco numerato di casi. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Condizione**  
 Consente di digitare un'espressione o di compilarne una eseguendo un'operazione di trascinamento dall'elenco di operatori, funzioni, variabili e colonne disponibili.  
  
 È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.  
  
 **Argomenti correlati:**  [Espressioni di Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Operatori &#40;espressione SSIS&#41;](../../../integration-services/expressions/operators-ssis-expression.md) e [Funzioni &#40;espressione SSIS&#41;](../../../integration-services/expressions/functions-ssis-expression.md)  
  
 **Nome output predefinito**  
 Consente di immettere un nome per la trasformazione. In alternativa, utilizzare quello predefinito.  
  
 **Configura output errori**  
 Consente di indicare come gestire gli errori tramite la finestra di dialogo [Configura output errori](../Topic/Configure%20Error%20Output.md).  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Divisione di un set di dati tramite la trasformazione Suddivisione condizionale](../../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  