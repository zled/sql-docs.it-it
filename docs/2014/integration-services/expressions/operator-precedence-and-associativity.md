---
title: Precedenza e associatività degli operatori | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a0e20795ecf10dbfb1bcf2daa8b4808221fa2ba7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063138"
---
# <a name="operator-precedence-and-associativity"></a>Precedenza e associatività degli operatori
  Ogni operatore nel set di operatori supportato dall'analizzatore di espressioni ha una precedenza specifica nella gerarchia delle precedenze e prevede una direzione di valutazione. La direzione di valutazione di un operatore è l'associatività dell'operatore. Gli operatori con precedenza superiore vengono valutati prima di quelli con precedenza inferiore. Se un'espressione complessa include più operatori, l'ordine di esecuzione è determinato dalla precedenza degli operatori. L'ordine di esecuzione può modificare in modo significativo il valore restituito. Alcuni operatori hanno la stessa precedenza. Se un'espressione contiene più operatori con la stessa precedenza, gli operatori verranno valutati nell'ordine in cui compaiono, procedendo da sinistra a destra o da destra a sinistra.  
  
 Nella tabella seguente vengono elencate le precedenze degli operatori, dalla più alta alla più bassa. Gli operatori indicati sullo stesso livello hanno la stessa precedenza.  
  
|Simbolo operatore|Tipo di operazione|Associatività|  
|---------------------|-----------------------|-------------------|  
|( )|Espressione|Da sinistra a destra|  
|–, !, ~|Unaria|Da destra a sinistra|  
|cast|Unaria|Da destra a sinistra|  
|*, / ,%|Moltiplicazione|Da sinistra a destra|  
|+, –|Additive|Da sinistra a destra|  
|\<, >, \<=, >=|Relazionale|Da sinistra a destra|  
|==, !=|Uguaglianza|Da sinistra a destra|  
|&|AND bit per bit|Da sinistra a destra|  
|^|OR esclusivo bit per bit|Da sinistra a destra|  
|&#124;|OR inclusivo bit per bit|Da sinistra a destra|  
|&&|AND logico|Da sinistra a destra|  
|&#124;&#124;|OR logico|Da sinistra a destra|  
|? :|Espressione condizionale|Da destra a sinistra|  
  
## <a name="see-also"></a>Vedere anche  
 [Gli operatori &#40;espressione SSIS&#41;](operators-ssis-expression.md)  
  
  