---
title: Opzioni di configurazione del server access check cache | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8efe371a915906e6f4f23df9cbd1f853ec20eb7c
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="access-check-cache-server-configuration-options"></a>Opzioni di configurazione del server access check cache
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]accede agli oggetti di database, il controllo dell'accesso viene memorizzato nella cache in una struttura interna denominata **cache dei risultati del controllo dell'accesso**. Le opzioni **access check cache quota** e **access check cache bucket count** determinano il numero di voci e di hash bucket utilizzati per la cache dei risultati del controllo dell' ****accesso. Raramente la modifica di tali opzioni consente di ottenere prestazioni migliori.  
  
 Il valore predefinito 0 indica che le opzioni vengono gestite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . È consigliabile modificare le opzioni solo se suggerito dal Servizio Supporto Tecnico Clienti Microsoft.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

