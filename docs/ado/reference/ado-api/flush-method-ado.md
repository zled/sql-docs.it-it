---
title: Flush (metodo) (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 94a5e1ced6f0b302253298dcbfb9cd345b9f5bfe
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="flush-method-ado"></a>Flush (metodo) (ADO)
Forza il contenuto del [flusso](../../../ado/reference/ado-api/stream-object-ado.md) rimanenti nel buffer di ADO per l'oggetto sottostante a cui il **flusso** associata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo può essere utilizzato per inviare il contenuto del buffer del flusso all'oggetto sottostante: ad esempio, il nodo o il file rappresentato dall'URL che rappresenta l'origine del **flusso** oggetto. Questo metodo deve essere chiamato quando si desidera garantire che tutte le modifiche che sono state apportate al contenuto di un **flusso** sono state scritte. Tuttavia, con ADO non è in genere necessario chiamare **scaricamento**, in quanto ADO svuota continuamente il proprio buffer per quanto possibile in background. Modifiche al contenuto di un **flusso** vengono eseguite automaticamente e non memorizzato nella cache fino a **scaricamento** viene chiamato.  
  
 La chiusura di un **flusso** con il [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodo cancella il contenuto di un **flusso** automaticamente; non esiste, è necessario chiamare in modo esplicito **scaricamento**immediatamente prima **Chiudi**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
