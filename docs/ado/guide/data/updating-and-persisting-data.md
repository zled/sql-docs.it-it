---
title: L'aggiornamento e salvataggio di dati | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ADO]
- data updates [ADO]
- ADO, updating data
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5331ee16d67159c67c40fcca328b011dfd9a0462
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="updating-and-persisting-data"></a>L'aggiornamento e il mantenimento dei dati
Capitoli precedenti hanno illustrato come utilizzare ADO per recuperare i dati in un'origine dati, come spostarsi all'interno dei dati e anche come modificare i dati. Naturalmente, se l'obiettivo dell'applicazione è consentire agli utenti di apportare modifiche ai dati, è necessario conoscere le modalità salvare le modifiche. È possibile mantenere sia il **Recordset** cambia in un file utilizzando il **salvare** metodo oppure è possibile inviare di nuovo le modifiche all'origine dati per l'utilizzo di archiviazione il **aggiornamento** o  **UpdateBatch** metodi.  
  
 Nei capitoli precedenti, è stato modificato in diverse righe di dati di **Recordset**. ADO supporta due approcci di base in riguardanti l'aggiunta, eliminazione e la modifica di righe di dati.  
  
 Il primo approccio si apportare le modifiche non sono immediatamente al **Recordset**; invece, sono state apportate a un interno *buffer di copia*. Se si decide di non creare le modifiche, le modifiche nel buffer di copia vengono rimosse. Se si decide di mantenere le modifiche, le modifiche nel buffer di copia vengono applicate per il **Recordset**.  
  
 Il secondo approccio è che le modifiche vengono propagate sia all'origine dati non appena si dichiara il lavoro in una riga completa (vale a dire *immediato* modalità), o tutte le modifiche a un set di righe vengono raccolti fino a quando non si dichiara il lavoro per il set completa (vale a dire *batch* modalità). Il **LockType** proprietà determina quando vengono apportate all'origine dati sottostante. **adLockOptimistic** oppure **adLockPessimistic** specifica la modalità immediata, mentre **adLockBatchOptimistic** specifica la modalità batch. Il **CursorLocation** proprietà può influire sulle cui **LockType** sono disponibili le impostazioni. Ad esempio, il **adLockPessimistic** impostazione non è supportata se il **CursorLocation** è impostata su **adUseClient**.  
  
 In modalità immediata, ogni chiamata del **aggiornamento** metodo propaga le modifiche all'origine dati. In modalità batch, ogni chiamata di **aggiornamento** o lo spostamento della posizione di riga corrente Salva le modifiche apportate al buffer di copia, ma solo il **UpdateBatch** metodo propaga le modifiche all'origine dati.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Aggiornamento dei dati](../../../ado/guide/data/updating-data.md)  
  
-   [Persistenza dei dati](../../../ado/guide/data/persisting-data.md)
