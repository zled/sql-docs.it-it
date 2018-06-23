---
title: Editor trasformazione Suddivisione condizionale | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: be0e756eaaf0a97dd041d94f254fd7bf80854b23
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067429"
---
# <a name="conditional-split-transformation-editor"></a>Editor trasformazione Suddivisione condizionale
  Utilizzare la finestra di dialogo **Editor trasformazione Suddivisione condizionale** per creare espressioni e impostare l'ordine in cui vengono valutate, nonché per assegnare un nome agli output di una suddivisione condizionale. In questa finestra di dialogo sono inclusi funzioni e operatori matematici, di data/ora e per i valori stringa che possono essere utilizzati per la compilazione di espressioni. La prima condizione che restituisce true determina l'output a cui è indirizzata una riga.  
  
> [!NOTE]  
>  La trasformazione Suddivisione condizionale indirizza ogni riga di input a un unico output. Se si immettono più condizioni, la trasformazione invierà ogni riga al primo output per cui la condizione è verificata e ignorerà le successive condizioni per tale riga. Per valutare più condizioni consecutivamente, potrebbe essere necessario concatenare più trasformazioni Suddivisione condizionale nel flusso di dati.  
  
 Per altre informazioni sulla trasformazione Suddivisione condizionale, vedere [Trasformazione Suddivisione condizionale](data-flow/transformations/conditional-split-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **JSON**  
 Selezionare una riga e utilizzare i tasti di direzione a destra per modificare l'ordine in base a cui valutare le espressioni.  
  
 **Nome output**  
 Consente di specificare un nome per l'output. Per impostazione predefinita viene suggerito un elenco numerato di casi. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Condizione**  
 Consente di digitare un'espressione o di compilarne una eseguendo un'operazione di trascinamento dall'elenco di operatori, funzioni, variabili e colonne disponibili.  
  
 È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.  
  
 **Argomenti correlati:**  [Espressioni di Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md), [Operatori &#40;espressione SSIS&#41;](expressions/operators-ssis-expression.md) e [Funzioni &#40;espressione SSIS&#41;](expressions/functions-ssis-expression.md)  
  
 **Nome output predefinito**  
 Consente di immettere un nome per la trasformazione. In alternativa, utilizzare quello predefinito.  
  
 **Configura output errori**  
 Consente di indicare come gestire gli errori tramite la finestra di dialogo [Configura output errori](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Dividere un set di dati tramite la trasformazione Suddivisione condizionale](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  