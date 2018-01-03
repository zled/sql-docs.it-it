---
title: Posizionamento di recordset | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28dcc44f38c763056a7a7f78979eee4f6de7df48
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-positioning"></a>Posizionamento di recordset
Utilizzare il **AbsolutePosition** proprietà per passare a un record, in base alla posizione ordinale di **Recordset** oggetto, o per determinare la posizione ordinale del record corrente. Il provider deve supportare le funzionalità appropriate per questa proprietà sia disponibile.  
  
 **AbsolutePosition** è basata su 1 ed è uguale a 1 quando il record corrente è il primo record di **Recordset**. Come accennato in precedenza, è possibile ottenere il numero totale di record nel **Recordset** dall'oggetto di **RecordCount** proprietà.  
  
 Quando si imposta la **AbsolutePosition** proprietà, anche se a un record nella cache corrente, ADO ricarica la cache con un nuovo gruppo di record che iniziano con il record specificato. Il **CacheSize** proprietà determina le dimensioni di questo gruppo.  
  
> [!NOTE]
>  Non è consigliabile utilizzare il **AbsolutePosition** proprietà come numero di record sostitutivo. La posizione di un determinato record cambia quando si elimina un record precedente. Non vi è alcuna garanzia che un determinato record avrà lo stesso **AbsolutePosition** se il **Recordset** oggetto viene rieseguito o riaperto. I segnalibri rappresentano il modo consigliato per mantenere e tornare a una posizione specifica e sono l'unico modo il posizionamento in tutti i tipi di **Recordset** oggetti.
