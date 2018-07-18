---
title: MSSQL_ENG014120 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb15b59a86b60d12d65716341062d6c670ad4a5f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299901"
---
# <a name="mssqleng014120"></a>MSSQL_ENG014120
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14120|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Il database di distribuzione '%s' è associato a un server di pubblicazione. Impossibile eliminarlo.|  
  
## <a name="explanation"></a>Spiegazione  
 Nel database di distribuzione vengono memorizzati metadati e dati di cronologia relativi a tutti i tipi di replica e alle transazioni per la replica transazionale. Questo errore si verifica se si tenta di eliminare un database di distribuzione associato a uno o più server di pubblicazione.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per eliminare un database di distribuzione, è innanzitutto necessario eliminare l'associazione tra il server di distribuzione e il server di pubblicazione. Per altre informazioni, vedere [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)   
 [Configurare la distribuzione](configure-distribution.md)  
  
  
