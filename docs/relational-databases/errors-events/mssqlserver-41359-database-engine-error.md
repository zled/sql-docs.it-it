---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 448f425c45fa183b1f9ce54376e3a0a455beebfe
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41359"></a>MSSQLSERVER_41359
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41359|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Testo del messaggio|Una query che accede a tabelle con ottimizzazione per la memoria utilizzando il livello di isolamento READ COMMITTED non può accedere alle tabelle basate su disco quando l'opzione di database READ_COMMITTED_SNAPSHOT è impostata su ON. Specificare un livello di isolamento supportato per la tabella con ottimizzazione per la memoria utilizzando un hint di tabella, ad esempio WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Spiegazione  
Il database con READ_COMMITTED_SNAPSHOT=ON non supporta le transazioni che accedono sia alle tabelle con ottimizzazione per la memoria che a tabelle basate su disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Impostare READ_COMMITTED_SNAPSHOT su OFF o specificare un livello di isolamento supportato per la tabella con ottimizzazione per la memoria utilizzando un hint a livello di tabella, ad esempio WITH (SNAPSHOT). Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

