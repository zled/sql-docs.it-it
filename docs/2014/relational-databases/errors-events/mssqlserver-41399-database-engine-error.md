---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18f6619ed33640a0659e4260a8c40dedcb225727
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425120"
---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41399|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|Testo del messaggio|L'operazione di ordinamento è troppo complessa. Per ulteriori informazioni, vedere la documentazione online di SQL Server.|  
  
## <a name="explanation"></a>Spiegazione  
 L'ordinamento del risultato di operazioni di join e di aggregazione aumenta la complessità dell'operazione di ordinamento incrementando le dimensioni della riga nel buffer di ordinamento. Questo errore indica che le dimensioni della riga sono maggiori delle dimensioni massime supportate dall'operatore di ordinamento nelle stored procedure compilate in modo nativo. Notare che le dimensioni di una riga nel buffer di ordinamento sono determinate unicamente dal numero di join e dal numero e dal tipo di funzioni di aggregazione. Le dimensioni delle righe nelle tabelle di base non influisce sulle dimensioni della riga nel buffer.  
  
## <a name="user-action"></a>Azione dell'utente  
 Ridurre la complessità della query rimuovendo le funzioni di aggregazione o i join.  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
