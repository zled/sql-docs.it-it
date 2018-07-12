---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: acf61c82e7ca67172843c33d5ec5cef3165ccffa
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419911"
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
  
  
