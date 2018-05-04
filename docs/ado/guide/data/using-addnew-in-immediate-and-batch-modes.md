---
title: Utilizzo di AddNew nell'immediato e la modalità Batch | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c66b250780e3b12ae9590796a062426f89920de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>Utilizzo di AddNew nell'immediato e la modalità Batch
Il comportamento del **AddNew** metodo dipende dalla modalità di aggiornamento del **Recordset** oggetto e se si passa il *elenco campi* e *valori*argomenti.  
  
 In modalità di aggiornamento immediato (in cui il provider scrive le modifiche all'origine dati sottostante dopo aver chiamato il **aggiornare** metodo), la chiamata il **AddNew** metodo senza argomenti imposta il  **EditMode** proprietà **adEditAdd.** Il provider memorizza nella cache qualsiasi valore di campo modificato in locale. Chiamata di **aggiornamento** metodo invia il nuovo record nel database e reimposta il **EditMode** proprietà **adEditNone.** Se si passa il *elenco campi* e *valori* argomenti, ADO invia immediatamente il nuovo record per il database (non **aggiornamento** è necessario chiamare); il **EditMode**  valore proprietà non viene modificato (**adEditNone**).  
  
 In modalità di aggiornamento batch, la chiamata di **AddNew** metodo senza argomenti imposta la **EditMode** proprietà **adEditAdd**. Il provider memorizza nella cache qualsiasi valore di campo modificato in locale. La chiamata di **aggiornamento** metodo aggiunge il nuovo record corrente **Recordset** e reimposta il **EditMode** proprietà **adEditNone**, ma il provider invia le modifiche al database sottostante fino a quando non si chiama il **UpdateBatch** metodo. Se si passa il *elenco campi* e *valori* argomenti, ADO invia il nuovo record per il provider di archiviazione in una cache, è necessario chiamare il **UpdateBatch** per registrare il nuovo (metodo) registrare il database sottostante. Per ulteriori informazioni su **aggiornamento** e **UpdateBatch**, vedere [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).
