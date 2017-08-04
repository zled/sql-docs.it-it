---
title: Editor trasformazione Suddivisione condizionale | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 769f9562af7bac75a488854319ba87ff8088329c
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="conditional-split-transformation-editor"></a>Editor trasformazione Suddivisione condizionale
  Utilizzare la finestra di dialogo **Editor trasformazione Suddivisione condizionale** per creare espressioni e impostare l'ordine in cui vengono valutate, nonché per assegnare un nome agli output di una suddivisione condizionale. In questa finestra di dialogo sono inclusi funzioni e operatori matematici, di data/ora e per i valori stringa che possono essere utilizzati per la compilazione di espressioni. La prima condizione che restituisce true determina l'output a cui è indirizzata una riga.  
  
> [!NOTE]  
>  La trasformazione Suddivisione condizionale indirizza ogni riga di input a un unico output. Se si immettono più condizioni, la trasformazione invierà ogni riga al primo output per cui la condizione è verificata e ignorerà le successive condizioni per tale riga. Per valutare più condizioni consecutivamente, potrebbe essere necessario concatenare più trasformazioni Suddivisione condizionale nel flusso di dati.  
  
 Per altre informazioni sulla trasformazione Suddivisione condizionale, vedere [Trasformazione Suddivisione condizionale](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
## <a name="options"></a>Opzioni  
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
 Consente di indicare come gestire gli errori tramite la finestra di dialogo [Configura output errori](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) .  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Dividere un set di dati tramite la trasformazione Suddivisione condizionale](../../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
