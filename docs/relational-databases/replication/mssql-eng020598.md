---
title: MSSQL_ENG020598 | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd821635130f3b631cfb08f29b66af13de82b3d3
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng020598"></a>MSSQL_ENG020598
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20598|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile trovare la riga nel Sottoscrittore durante l'applicazione del comando replicato.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore viene generato nella replica transazionale se l'agente di distribuzione tenta di aggiornare una riga nel Sottoscrittore mentre la riga è stata eliminata o la chiave primaria della riga è stata modificata. Per impostazione predefinita, i Sottoscrittori di pubblicazioni transazionali devono essere considerati di sola lettura poiché le modifiche non vengono trasferite al server di pubblicazione. Nella replica transazionale, gli utenti possono eseguire modifiche nel Sottoscrittore solo se utilizzano sottoscrizioni aggiornabili o la replica peer-to-peer. Per informazioni sulle opzioni menzionate, vedere [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md) e [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 **Per risolvere il problema:**  
  
1.  Se si desidera che la replica continui mentre si identifica l'origine dell'errore, specificare il parametro **-SkipErrors 20598** per l'agente di distribuzione. In questo modo l'agente ignorerà le modifiche che generano l'errore 20598 e consentirà la replica delle altre modifiche.  
  
2.  Identificare le righe eliminate o che presentano una chiave primaria diversa nel Sottoscrittore rispetto alle righe corrispondenti nel server di pubblicazione. È possibile utilizzare la [tablediff Utility](../../tools/tablediff-utility.md) per determinare quali righe risultano diverse nei database di pubblicazione e di sottoscrizione. Per informazioni sull'uso di questa utilità con database di replica, vedere [Confrontare tabelle replicate al fine di individuare le differenze &#40;programmazione della replica&#41;](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
3.  Correggere le righe nel Sottoscrittore utilizzando l'utilità **tablediff** o un altro metodo.  
  
4.  (Facoltativo) Rimuovere il parametro **-SkipErrors** .  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
