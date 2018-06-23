---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 984a675db470f66941b1d1a9292b76cb18f07f4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158905"
---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41333|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Testo del messaggio|Le seguenti transazioni devono accedere a tabelle con ottimizzazione per la memoria e stored procedure compilate in modo nativo con isolamento SNAPSHOT: transazioni REPEATABLEREAD, SERIALIZABLE e transazioni che accedono a tabelle senza ottimizzazione per la memoria con isolamento REPEATABLEREAD o SERIALIZABLE.|  
  
## <a name="explanation"></a>Spiegazione  
 Sono presenti restrizioni relative all'uso di livelli di isolamento più elevati tra le transazioni basate su disco e le transazioni di XTP.  
  
## <a name="user-action"></a>Azione dell'utente  
 Non tentare operazioni con un livello di isolamento alto nelle tabelle ottimizzate per la memoria (e procedure compilate in modo nativo) e nelle tabelle basate su disco.  
  
 Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  