---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 076c9a6d93a3ffba45ae741a4724d7f6561fe688
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21871|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum21871|  
|Testo del messaggio|Il server di pubblicazione %s del database %s non è stato reindirizzato.|  
  
## <a name="explanation"></a>Spiegazione  
**sp_validate_replica_hosts_as_publishers** controlla la tabella MSredirected_publishers nel database di distribuzione per cercare una voce per il server di pubblicazione identificato e il database del server di pubblicazione.  **sp_validate_replica_hosts_as_publishers** restituisce l'errore 21871 quando non viene trovata alcuna voce.  
  
## <a name="user-action"></a>Azione dell'utente  
**sp_validate_replica_hosts_as_publishers** è attinente solo per i server di pubblicazione reindirizzati. Se un database del server di pubblicazione è membro di un gruppo di disponibilità, usare la stored procedure **sp_redirect_publisher** per associare il server di pubblicazione e il database del server di pubblicazione al nome del listener del gruppo di disponibilità.  
  
