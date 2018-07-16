---
title: MSSQL_ENG021331 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021331 error
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4bab3ee3277554b3e3846e95c17f44e1cc937a17
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298081"
---
# <a name="mssqleng021331"></a>MSSQL_ENG021331
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21331|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile copiare il file script utente nel server di distribuzione.(%ls)|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore può verificarsi quando viene inizializzata manualmente una sottoscrizione e gli script generati dalla replica o specificati in un comando di replica non possono essere salvati nella directory specificata. L'errore può essere causato da un problema relativo alle autorizzazioni: quando una sottoscrizione viene inizializzata senza utilizzare uno snapshot, l'account con cui il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito nel server di pubblicazione deve disporre di autorizzazioni di scrittura per la cartella snapshot nel server di distribuzione.  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare che sia stato specificato il percorso corretto della cartella snapshot e che l'account con cui il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito nel server di pubblicazione disponga di autorizzazioni sufficienti.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare la posizione predefinita degli snapshot &#40;SQL Server Management Studio&#41;](specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)   
 [Inizializzare una sottoscrizione transazionale senza uno snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
